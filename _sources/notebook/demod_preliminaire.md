---
jupytext:
  encoding: '# -*- coding: utf-8 -*-'
  formats: ipynb,md:myst
  split_at_heading: true
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.10.3
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

Il arrive fréquemment qu'on cherche à obtenir le signal modulant à partir du signal modulé en amplitude (cas en radio AM par exemple). Nous allons voir dans ce TP deux méthodes permettant de le réaliser :
* la détection d'enveloppe
* la détection synchrone

# (Travail) Etude préliminaire

## Détection d'enveloppe
La détection d'enveloppe est basé sur l'utilisation d'un dipôle non linéaire : la diode. Le circuit détecteur d'enveloppe est le [suivant](detecteur).

```{figure} ./images/detecteur_crete.jpg
:name: detecteur
:align: center
Montage détecteur d'enveloppe.
```

```{code-cell}
:tags: [remove-output, remove-input]
from matplotlib.pyplot import *
from numpy import *
from myst_nb import glue

T = 0.01
x = linspace(0, 2 * T, 10000)
y = sin(2 * pi * 1000  * x) + 1 / 2 * sin(2 * pi * 1000  * x) * sin(2 * pi * 100  * x)
y2 = sin(2 * pi * 10000  * x) + 1 / 2 * sin(2 * pi * 10000  * x) * sin(2 * pi * 100  * x)

f, ax = subplots(figsize=(9,6))
f.suptitle('Signal Modulé en amplitude')

ax.set_xlabel('temps(ms)')
ax.set_ylabel('VE(V)')

ax.plot(x * 1000, y, label="m=1/2")

ax.legend()

f2, ax2 = subplots(figsize=(9,6))
f2.suptitle('Signal Modulé en amplitude')

ax2.set_xlabel('temps(ms)')
ax2.set_ylabel('VE(V)')

ax2.plot(x * 1000, y2, label="m=1/2")

ax2.legend()

glue('sig_mod', f)
glue('sig_mod2', f2)
```

Le signal en entrée $V_E(t)$ est le signal modulé en amplitude. On donne son [allure](signal_module)

```{glue:figure} sig_mod
:name: signal_module
:align: center
Allure temporelle de $V_E(t)$ pour $f_p = 10 f_m$
```

````{admonition} Exercice : Etude du circuit
:class: tip
1. L'étude de la caractéristique dynamique de la diode aux différents signaux nous permet-elle d'utiliser la caractéristique statique de la diode pour analyser le circuit précédent ?
2. On prendra pour l'instant $U_D = 0$ sur la modélisation de la diode.
3. On suppose que à $t=0$ la diode est dans un état passant ($u_{diode} = U_D = 0$).
    1. A quoi est équivalente la diode dans ces conditions ?
    2. Comment va évoluer la tension $V_S(t)$ aux bornes du générateur en fonction de $V_E(t)$ ?
    3. A quelle moment $i_C$ s'annule ? _$i_R$ étant relativement faible, on pourra faire comme si c'est aussi le moment où la diode se bloque._
    4. Reproduire le signal $V_E(t)$ et représenter $V_S(t)$ jusqu'au moment où la diode se bloque.
4. La diode est maintenant bloquée ($i=0$). Elle le restera tant que $u_{diode} < U_D = 0$.
    1. Dans quel régime est alors le condensateur ? En déduire sans calcul l'allure temporelle de $V_S(t)$ et le temps caractéristique $\tau$ associé à sa variation.
    2. Donner une première condition sur $\tau$ pour que le détecteur d'enveloppe ne suive pas les variations rapides du signal.
    3. Quand la diode va-t-elle redevenir passante ?
5. Avec la condition suivante, poursuivre le tracé de $V_S(t)$ jusqu'à ce que le signal d'entrée soit au sommet de son enveloppe.
6. Justifier que pour que le signal de sortie suive l'enveloppe du signal à partir de ce point là, il faut imposer une deuxième condition sur $\tau$.
````

__Dans le cas précédente $f_p = 10 f_m$, il est difficile d'imposer les deux conditions de manière acceptable (c'est d'ailleurs difficile de dessiner un signal qui suit bien l'enveloppe). En TP, on aura un rapport 100 entre les fréquences ce qui permettra de réaliser les deux conditions.__

```{glue:figure} sig_mod2
:name: signal_module2
:align: center
Allure temporelle de $V_E(t)$ pour $f_p = 100 f_m$
```


````{admonition} Exercice : Surmodulation
:class: tip
1. Dessiner l'allure de $V_E(t)$ pour $m > 1$.
2. Quelle va être l'allure du signal à la sortie du détecteur d'enveloppe (les deux conditions précédentes ayant été réalisées). Quel problème observe-t-on ?
````

__C'est une des limites de la détection de crête. L'utilisation d'une détection synchrone permet de s'affranchir de cette limite.__


## Détection synchrone
La détection synchrone consiste à :
1. multiplier le signal modulé par un signal sinuoïdal de fréquence $f_p$ accordé avec la porteuse.
2. faire passer ce signal par un filtre passe-bas de fréquence de coupure judicieusement choisie.
3. Si nécessaire couper la composante continue restante avec un filtre passe-haut (pas réalisé en TP).

### Multiplication
On multiplie donc $V_E(t)$ par un signal de fréquence $f_p$. On note le signal obtenu $V_{s1}$

````{admonition} Exercice : Etude spectrale
:class: tip
1. Déterminer le spectre du signal $V_{s1}$.
2. Pourquoi un filtre passe-bas permet (à la composante continue près et à un facteur près) de retrouver le signal modulant ? Comment choisir (approximativement) la fréquence de coupure du filtre.
````

### Filtre passe-bas
Nous allons utiliser un [filtre passe-bas actif](pbas).

```{figure} ./images/pbas_actif.png
:name: pbas
:align: center
Filtre passe-bas actif du second ordre.
```

````{admonition} Exercice : Dimensionnement du filtre.
:class: tip
1. Justifier rapidement que ce filtre est un passe-bas puis exprimer sa fonction de transfert. On montrera que $\omega_0 = \frac{1}{\sqrt{2}RC}$ et $Q = \frac{1}{\sqrt{2}}$.
2. Observe-t-on une résonance ? La fréquence de coupure est ici $\omega_c = \omega_0$ (on pourra s'entraîner à le démontrer).
3. On veut que le gain à $f_p$ soit de $10^{-2}$, en déduire le choix de la fréquence de coupure $f_c$ en fonction de $f_p$.
4. Que vaut alors le gain pour la fréquence $f_m$ sachant que $f_p = 100 f_m$. En déduire que ce filtre devrait remplir sa fonction en choisissant $f_c$ comme décidé précédemment. Quelle sera alors l'allure du signal de sortie ? Quelle est la différence avec la détection d'enveloppe ?
````


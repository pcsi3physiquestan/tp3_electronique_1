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

Le but de cette séance est de produire un signal modulé en amplitude à la manière des signaux produits en radio AM (on n'utilisera une gamme de fréquence différente).

# (Travail) Etude préliminaire

## Position du problème.

### But

On veut réaliser un signal $s(t)$ modulé en amplitude à partir :
* d'un signal porteur $e_p(t)$ sinusoïdal de fréquence rapide $f_p$.
* d'un signal modulant $e_m(t)$ sinusoïdal de fréquence lente $f_m$.

Le signal modulé en amplitude aura pour expression :

$$
s(t) = k e_m(t) e_p(t) + e_p(t)
$$

### Matériel à disposition
On dispose pour ce faire de plusieurs éléments :
* deux générateurs basse fréquences qui vont pouvoir délivrer les tensions $e_p(t)$ et $e_m(t)$. Ils ont tous les deux une impédances de sortie de $50 \Omega$
* un [multiplieur](multiplieur)
	* un circuit permettant, à partir de deux tensions $v_1$ et $v_2$ d'obtenir le produit $v_s = k v_1 v_2$ où $k$ est une grandeur dimensionnée propre au multiplieur.
	* son impédance d'entre pour chaque entre $v_i$ est très grande (de l'ordre du GigaOhm)
	* son impédance de sortie est très faible (quelques Ohms).
* un amplificateur linéaire intégré permettant, grâce à différentes résistances de réaliser les diverses fonctions étudiées lors de l'étude de l'ALI.
* d'une alimentation (symétrique) nécessaire à l'alimentation de l'ALI et du multiplieur.
* plusieurs résistances permettant de former un montage sommateur donné [ci-après](sommateur)
* d'un oscilloscope pour observer les différentes tensions.

````{panels}
```{figure} ./images/multiplieur.png
:name: multiplieur
:align: center
Représentation d'un multiplieur
```
---
```{figure} ./images/sommateur.jpg
:name: sommateur
:align: center
Montage sommateur
```
````

## Etude théorique du sommateur

````{admonition} Analyse du sommateur
:class: tip
1. En utilisant une loi des noeuds en terme de potentiel, montrer que la tension en sortie du sommateur est bien égale à $v_s = \alpha (v_1 + v_2)$
2. Proposer un protocole permettant de mesurer $\alpha$ (les tensions seront sinusoïdales)
2. Si l'on veut au final $v_{s1} = v_1 + v_2$, quel montage faut-il placer après le sommateur ? Préciser la relation entre $R_1, R_2$ et les valeurs des résistances du montage à placer ensuite.
3. On relie $v_2$ à la masse. Justifier alors que $v_1$ semble branché à une résistance équivalente $R_e$ qu'on déterminera. Cette résistance est un ordre de grandeur de la résistance d'entrée du montage sommateur pour $v_1$ et $v_2$.
````

## Montage à réaliser.

### Montage général
````{admonition} Questions
:class: tip
1. Proposer un montage complet utilisant les différents étages proposées pour obtenir en sortie un signal modulé en amplitude (note : les alimentations symétriques nécessaies au fonctionnement de l'ALI et du multiplieur ne sont pas à représenter).
2. Dans le cas signaux sinusoïdaux, préciser l'expression explicite de $s(t)$ sous la forme : $s(t) = A_p (1 + m \cos \omega_m t) \cos \omega_p t$ où $m$ est appelé taux de modulation.
3. Représenter l'allure théorique de $s(t)$ lorsque $m > 1$ puis lorsque $m < 1$. Sur quel paramètre du montage doit-on jouer pour modifier la valeur de m ?
````

_Note : En pratique $k = 0.1$ et $A_s < 10V$ il ne sera donc pas possible d'obtenir une surmodulation de cette manière._

### Association d'impédances.
````{admonition} Question
:class: tip
En utilisant les valeurs des impédances d'entrée et sortie des différents étages du circuit, préciser s'il est nécessaire d'intercaler un montage suiveur à un endroit du montage.
````

## Rédaction du protocole
````{admonition} Protocole
:class: tip
Vous devez maintenant rédiger le protocole général de l'ensemble du TP. Vous devrez :
1. Préciser le but du TP
2. __Dessiner le montage à réaliser.__
3. Expliquer théoriquement (le principe donc) comment ce montage permet de réaliser le but du TP et justifier la nécessité ou la non nécessité des montages suiveur.
4. Expliquer, __schéma de montage à l'appui__, les protocoles à réaliser pour vérifier le bon fonctionnement de chaque étage séparément ainsi que pour régler le gain de l'amplificateur pour avoir $v_{s1} = v_1 + v_2$.
````
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

Avant de commencer le TP, vous aller préparer les protocoles. Vous allez apprendre les spécificités des protocoles en électrocinétique.

# (Travail) Préparation des protocoles

+++

## Dipôle étudié.

### Généralités

On va étudier un dipôle non linéaire : la diode. Un diode classique est composée de matériaux semi-conducteur (de deux types, l’un appelé N et l’autre appelé P). Leur association (on parle de jonction... P-N) permet de créer un dipôle (la diode donc... ) qui ne laisse passer le courant que dans un sens. La diode est un dipôle polarisé.

+++

```{figure} ./images/diode_photos.jpg
:name: diode_photo
:align: center
:width: 50%
Exemples de diodes
````

+++

### Caractéristique et modélisation
La diode possède une caractéristique __statique__ qui a l'allure suivante.
```{margin}
Attention la caractéristique donnée est en convention récepteur __avec i dans le sens donnée sur le symbole ci-dessus__. Dans le cas des dipôles polarisés, le sens de $i$ (et de $u$) a une influence sur l'allure de la caractéristique.
```

````{panels}
:column: col-lg-8 p-2
```{figure} ./images/diode_carac.png
:name: diode_carac
:align: center
Caractéristique d'une diode
```
---
:column: col-lg-4 p-2
```{figure} ./images/diode_symbole.png
:name: diode_symbole
:align: center
:width: 70%
Symbole d'une diode
```
````

On distingue deux modélisations :
* Modélisation précise (en rouge sur le graphique) : la relation $i(u)$ est alors modélisée par une relation exponentielle. On n'utilisera pas cette modélisation en TP.
* Modélisation par deux états (en pointillés - on l'utilisera en TP):
    * __Un état bloqué__ pour lequel le courant ne peut passer. Cet état ne peut exister que si _la tension est inférieur à une tension seuil $U_D$_ : on assimile alors la diode à un __interrupteur ouvert__.
    * __Un état passant__ pour lequel le courant peut passer mais ne _peut qu'être positif_. La tension est alors quasi-constante et vaut la tension seuil $U_D$ : on assimile alors la diode à une __source idéale de tension de f.e.m. $U_D$__.

````{admonition} Exercice : Tension seuil
Utiliser l'[extrait de la fiche technique](diode_extrait_1) de la diode 1N4148 ci-après pour obtenir un ordre de grandeur de la tension $U_D$.

```{figure} ./images/diode_sheet_2.jpg
---
name: diode_extrait_1
---
Extrait n°1 de la fiche technique d'une diode 1N4148
```
````

+++

### Protection d'une diode
La [caractéristique](diode_carac) montre qu'imposer une tension supérieure à $U_D$ aux bornes de la diodes va dramatiquement augmenter l'intensité qui y circule et _risquer de détériorer la diode._ Pour protéger la diode, on utilise __une résistance qu'on place en série avec la diode__ et qui va servir à limiter le courant qui circule dans la diode.

````{admonition} Exercice : Protection d'une diode
1. On considère une diode de tension seuil $U_D$ protégée par une résistance $R_P$, l'ensemble étant soumis à une tension $E$. Estimer l'intensité $I$ qui circule dans la branche (résistance + diode).
2. Utiliser l'extrait suivant pour obtenir l'intensité maximale qu'on peut faire passer dans la diode en régime indépendant du temps. Choisir, avec une marge, la résistance $R_P$ de protection sachant que les tensions ne dépasseront pas 10V en TP.

```{figure} ./images/diode_sheet_1.jpg
---
name: diode_extrait_2
---
Extrait n°2 de la fiche technique d'une diode 1N4148
```
````

```{margin}
Même si ce n'est pas précisé, il __faudra protéger une diode par une résistance de protection__. Bien sûr, si une résistance suffisante est déjà présente en série, il n'est pas nécessaire d'en ajouter une !.
```

## Caractéristiques statiques d'une diode.

Le but est d'obtenir les points $(U,I)$ de fonctionnement d'une diode en régime indépendant du temps. On dispose 
* de la diode d'étude
* d'une résistance variable jouant le rôle de résistance de protection
* d'un générateur basse fréquence (GBF) qui peut créer des signaux variables ET des signaux indépendants du temps.
* de multimètres (2)
* d'un oscilloscope (deux voies de mesure)
* d'une carte d'acquisition

### Montage sans les instruments de mesure.

Le premier montage est donné. On réalise le [montage suivant](montage_diode) (la source de tension sera le GBF).


```{figure} ./images/diode_montage_simple.png
:name: montage_diode
:align: center
Montage à réaliser
```


```{admonition} Exercice.
:class: tip
1. Rappeler la valeur de $R_p$
2. Pour étudier la caractéristiques statiques, quelle forme choisir pour la tension $V(t)$.
3. Représenter sur le graphique de la caractéristique statique de la diode, la caractéristique statique du dipôle $V + R_p$. Où est le point de fonctionnement du circuit ?
4. Expliquer précisément comment faire pour obtenir plusieurs points de fonctionnement du circuit et retracer ainsi la caractéristique de la diode.
5. Préparer _intelligemment_ un tableau de valeurs (10) de $V(t)$ pour lesquelles vous déterminerez le point de fonctionnement.
```

### Utilisation des instruments de mesure.

Puisqu'on réalise des études en régime indépendant du temps, l'utilisation des multimètres peut suffire. On donne la représentation schématique d'un [voltmètre](voltmetre) et d'un [ampèremètre](amperemetre).

````{panels}
```{figure} ./images/voltmetre.png
:name: voltmetre
:align: center
Voltmètre. Le tension est mesurée dans le sens où est représentée Uc.
```
---
```{figure} ./images/amperemetre.png
:name: amperemetre
:align: center
Ampèremètre. L'intensité est mesurée dans le sens entrant par la borne +.
```
````

```{admonition} Exercice.
:class: tip
1. Quel calibre choisir pour les deux multimètre ? AC ou DC ?
2. Reprendre le [schéma de montage précédent](montage_diode) et y faire figurer les deux instruments de mesure en faisant attention à leur orientation.
```

```{important}
Le schéma que vous obtenez est le schéma qui doit apparaître dans la présentation du protocole expérimental.
```

### Rédaction du protocole
```{admonition} Exercice.
:class: tip
A vous de rédiger le protocole. Pour vous aider pour cette première fois, un squelette est donné dans la cellule suivante (cliquez sur la croix).
```

```{dropdown} Squelette de protocole
__But :__ ............

__Principe théorique :__ _...S'aider du raisonnement sur le point de fonctionnement..._

__Mode opératoire :__ 
1. _...Préciser le montage à réaliser..._
2. _...Préciser les valeurs des composants et le type de tension qu'on va envoyer..._
3. _...Préciser les mesures directes réalisées et ce que vous allez en faire..._

```


## Caractéristique dynamique de la diode.

On veut maintenant obtenir le tracé de la caractéristique dynamique $(u(t), i(t))$ de la diode pour les différents signaux ci-dessous.

1. Un signal sinusoïdale de fréquence 1kHz, d’amplitude 10V et de valeur moyenne nulle
2. Un signal sinusoïdale de fréquence 20kHz, d’amplitude 3V et de valeur moyenne 1V
3. Un signal triangulaire de fréquence 3kHz, d’amplitude 3V, de valeur basse -2V
4. Un signal créneau de fréquence 500Hz, d’amplitude 8V et de valeur moyenne nulle
5. Un signal créneau de fréquence 30kHz, de valeur basse 0V et de valeur haute 6V.
6. Un signal modulé en amplitude $s = k v \times e$ avec e$,$ un signal sinusoïdal de fréquence 10kHz modulé et d'amplitude 4V et $v$ un signal sinusoïdal de fréquence 500Hz et d'amplitude 4V. On donne $k = 0.1$.

### Mise en place du protocole expérimental
On va utiliser la carte d'acquisition FOXY déjà utilisée au premier TP. Chaque voie d'acquisition (il y en a 4) peut être représentée par un voltmètre.  __On ne peut mesurer que des tensions à l'aide de FOXY.__

```{admonition} Exercice.
:class: tip
1. Sachant qu'on ne peut mesurer que des tensions, proposer une méthode permettant d'obtenir l'intensité (ou presque) circulant dans le circuit. Proposer un schéma de montage à intégrer dans le protocole expérimental.

2. Rédiger alors le protocole expérimental (on ne détaillera pas les types de signaux à envoyer mais simplement leur caractère variable.
```

### Problème de masse
On voudrait faire la même étude avec un oscilloscope. Le but de cette étude préliminaire est de comprendre pourquoi ce n'est pas possible. Un oscilloscope (ceux des TPs) possède deux voies d'acquisition (Voie 1 et Voie 2). Donc la représentation est donnée [ci-dessous](oscillo) :

```{figure} ./images/oscillo.png
:name: oscillo
:align: center
Schématisation des branchements de l'oscilloscope.
```

````{admonition} Exercice.
:class: tip

1. Que signifie le symbole suivant ?
```{figure} ./images/masse.png
:name: masse
:align: center
```

```{dropdown}
C'est une caractéristique générale des oscilloscopes. Les deux voies ont une borne commune : la Terre !
```

2. Puisque les deux voies ont une borne commune, où faut-il la placer si on veut mesurer les deux tensions aux bornes de la diode et de la résistance sur le [schéma](montage_diode) ? Représenter alors le schéma (GBF+résistance+diode) avec les branchements nécessaires de l'oscilloscope. Sachant que le GBF a aussi __une borne reliée à la Terre__ (visible sur le [schéma](montage_diode)), quelle problème va-t-il se poser ?

````

Nous verrons comment s'affranchir de ce problème en TP en utilisation un transformateur d'isolement.
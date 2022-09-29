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

Vous allez commencer par préparer la séance de familiarisation. L'étude préliminéaire est à réaliser par écrit au début du compte-rendu que vous rendrez à la fin des séances de TPs.

+++

# (Travail) Matériel en électrocinétique

## Position du problème.

On va se concentrer dans cette partie sur l'étude d'un dipôle en régime statique - on cherchera à tracer sa caractéristique statique - puis en régime dynamique - en traçant $(u(t); i(t))$. On pourra ainsi voir si son comportement est le même en régime indépendant du temps et en régime variable avant de l'utiliser dans des montages. Cette étude va amener à se poser plusieurs questions :
* Quel instrument utiliser pour étudier un point de fonctionnement d'un dipôle en régime statique ? Comment le régler et l'utiliser ?
* Quel instrument utiliser pour suivre l'évolution d'un point de fonctionnement d'un dipôle en régime dynamique ? Comment le régler et l'utiliser ?
* Comment créer un signal de tension fixe pour étudier le régime statique d'un dipôle ?
* Comment créer un signal de tension variable pour étudier le régime dynamique ? Comment régler la forme et les caractéristiques voulues pour le signal.
* Quelles sont les contraintes liées à une acquisition numérique d'un signal ?


+++

## Instrumentation électrique

### Instrumentation diverse
Sans être exhaustif, citons :
* les câbles simples qui matérialisent un fil de connection.
* les cables BNC qui contiennent __deux câbles__. A leur extrémité, soit les deux câbles sont séparés en deux branchements simples, soit un reste sur une connectique BNC et un branchement permet le raccordement __des deux bornes du dipôles__. C'est le cas des GBF et oscilloscope. En général, un des bornes est alors reliées à la Terre.
* les plaquettes de montage. Certaines inclus un ALI ou un multiplieur
* les composants R, L, C, Diode de valeur fixe.
* les composants R, L, C, Diode de valeur réglable. On parle de __boite à décades__.

````{attention} 
Les boites à décade ne peuvent être utilisées que comme un seul composant. __Vous ne pouvez utiliser la même boite pour créer deux composants.__
````

### Les câbles BNC
#### Présentation et branchement
````{margin}
C'est le même principe sur les écouteurs et casque (prise Jack): un seul cable contenant 2 ou 3 fils.
````
Les câbles BNC sont des câbles particuliers car contrairement aux câbles simples, assimilables à des fils de connection, les câbles BNC contiennent __2 fils de connection__: un fil au milieu du câble (l'âme) et un tressage autour (la gaine), les deux fils étant isolés l'un de l'autre par un isolant plastique. Ces fils ont ne nombreux avantages en terme de proection du bruit. Leur utilisation est un peu particulière.

````{margin}
Il existe un autre type de BNC-simple où le câble se sépare en deux connections rouge et noire.
````
On distingue deux cas:
* Les câbles dits BNC-BNC où les deux connection sont des entrées/sorties BNC (cas du haut). Elles servent principalement pour nous à relier directement le GBF et l'oscilloscope. __Comme sur la photo, un seul câble suffit brancher les DEUX bornes du GBF aux DEUX bornes de l'oscilloscope.__
* Les câbles BNC-simples qui permettent de brancher un GBF/Oscilloscope sur un instruments ne possédant pas de voie BNC (_Résistance, condensateur, bobine, multimètre..._). Comme sur la figure du bas, le BNC est séparé en deux connectinos simples correspondant aux deux fils (et donc aux deux bornes du GBF/Oscilloscope).
    * Sur le fil présenté, l'embout sortant métallique est relié à l'âme (flèche rouge) et l'orifice dans l'excroissance (flèche verte) est reliée à la gaine. Il faut alors brancher un fil noir sur la gaine et on obtient deux connection à brancher dans le circuit.

```{figure} ./images/branchement_bnc.png
:name: branch_bnc
:align: center
Types de branchement des BNC
```

#### BNC et Terre
__La majorité des GBF et oscilloscopes possèdent une de leur borne reliée à la Terre.__

````{margin}
Ou la connectique noire pour les câbles séparés en rouge et noir.
````
Lorsqu'on branche un BNC-simple, il est important de savoir où elle se trouve car on va imposer un point de Terre dans le circuit. __La borne de Terre est toujours reliée à la gaine du BNC (branché à un GBF ou un oscilloscope) soit en sortie d'un BNC-simple l'excroissance du câble.__

```{attention} Unicité de la Terre
La borne de Terre est une borne physique dont le potentiel est imposé. Il ne peut donc y en avoir qu'une seule dans un circuit. __CELA SIGNIFIE que toutes les bornes de Terre des GBF et oscilloscope doivent être reliés _au même point de potentiel dans un circuit_.__ Cela peut entrainer des contraintes dans la réalisation d'un circuit.
```

### Créer un signal électrique.
On distingue trois types de sources :
* Les alimentations stabilisées. Elles permettent de créer une tension continue et délivrer une puissance assez importante. On les utilisera peu et le cas échéant, leur fonctionnement sera précisé.
```{margin} On remarquera que le constructeur nous impose alors le choix du point de masse```
* Les _alimentations symétriques_. Elles sont constituées de _trois_ branchements correspondant à des potentiels : $-15V, 0V, 15V$. On les utilise surtout pour alimenter les ALI (les 3 bornes sont alors à brancher).
* Les __générateurs basse fréquence__. Ils permettent de générer des signaux de forment varier (possiblement continu mais aussi sinusoïdaux, créneaux ou plus complexe). Ils seront très utilisés et on va s'attarder sur leurs réglages.

+++

#### Le GBF : Etapes de réglage
```{attention}
Avant de commencer à toucher aux boutons du GBF, il est __obligatoire__ de réfléchir aux caractéristiques du signal qu'on veut déliver...
```

La présentation du premier GBF utilisé et le protocole de réglage est présenté [ici](https://github.com/pcsi3physiquestan/donnees_exp/blob/main/poster_gbf.pdf?raw=true). Attention, le protocole est __général__ mais les boutons sont spécifiques au GBF présenté.

+++

### Mesurer une valeur unique : le multimètre

Un multimètre renvoie une valeur correspondant au type de mesure qu'on veut réaliser :
* ampèremètre : pour mesurer un courant
* voltmètre : pour mesurer une tension
* ohmètre : pour mesurer une résistance

+++

#### Ampèremètre et voltmètre
On rappelle :
* qu'un ampèremètre doit être _branché en série_ avec le dipôle dont on veut mesurer l'intensité qui le traverse.
* qu'un voltmètre doit être _branché en parallèle_ du dipôle dont on veut mesurer la tension à ses bornes.
* que dans les deux cas, la mesure est polarisée. La bornes `COM` correspond à la borne `-` des représentations : la queue de la flèche de tension (voltmètre) ou la sortie du dipôle en terme d'intensité (ampèremètre).
* que l'autre branchement est en général différent pour l'ampèremètre et le voltmètre.

+++

#### Calibre AC et DC
```{important}
* Le calibre DC permet de mesurer la valeur moyenne d'un signal.
* Le calibre AC permet de mesurer la valeur efficace d'un signal.
```

Ces calibres sont parfois représentés pas un `~` (AC) ou un `=` (DC, le trait inférieur peut-être en pointillés).

```{admonition} Exercice: quel calibre ?
:class: tip
1. On veut étudier le point de fonctionnement de la diode en régime indépendant du temps.
    1. Pour une tension continue de valeur $U_0$. Que vaut sa valeur moyenne ?
    2. Pour une tension continue de valeur $U_0$. Que vaut sa valeur efficace ?
    3. Vaut-il mieux régler le multimètre en DC ou en AC ?
2. On veut étudier le gain entrée/sortie d'un système électrique en régime sinusoïdal.
    1. Pour une tension sinusoïdal d'amplitude $U_m$. Que vaut sa valeur moyenne ?
    2. Pour une tension sinusoïdal d'amplitude $U_m$. Que vaut sa valeur efficace ?
    3. Vaut-il mieux régler le multimètre sur DC ou AC pour mesurer le rapport des amplitudes de deux tensions sinusoidales ?
```


#### Incertitudes et multimètre
Une présentation des sources d'incertitude avec les multimètre est données [ici](https://stanislas.edunao.com/mod/page/view.php?id=13269).
+++

### Suivre l'évolution d'un signal : la carte d'acquisition

Une carte d'acquisition est un dispositif permettant de mesurer des __tensions__ et envoyer des mesures à intervalles régulières à un ordinateur. Une logiciel récupère alors les données et affiche l'allure des signaux. L'interface graphique du logiciel (ici `Atelier scientifique`) permet de régler les paramètres d'acquisition de la carte pour obtenir les données voulues. L'affichage d'un suivi nécessite en effet un paramétrage adapté :
* l'acquisition doit suivre le signal voulu.
* l'acquisition doit démarrer au bon moment (crucial si le signal n'est pas périodique).
* l'acquisition doit durer un temps suffisant pour observer le phénomène voulu. Elle doit aussi ne pas être trop longue pour ne pas "écraser" l'observation du phénomène par des données inutiles.
* les mesures ne doivent pas "saturer"(en général, la carte est réglée pour mesurer des tensions entre 2 valeurs extrêmes)
* le nombre de points (d'échantillons) doit être suffisant pour pouvoir suivre les variations du signal.

+++

#### Réglage des cartes d'acquisition

_Affichez les étapes de réglages grâce à la croix à droite._


````{toggle}
On se base sur la carte FOXY utilisée au laboratoire.
1. Alimenter la carte et la brancher (USB) à l'ordinateur. Une interface se lance automatiquement. Choisir __Généraliste__.
2. Réaliser les branchements au circuit.
3. Choisir `Acquisition` dans les menus. Une fenêtre s'affiche à gauche pour les réglages.
4. __Choisir la(les) voie(s) à étudier.__ Elles sont représentées par ![Image voie](./images/as_voies.png). Un glisser-déplacer vers l'axe des ordonnées du graphique pour choisir d'acquérir la voie voulue.
5. __Régler les paramètres de chaque voie__ En cliquant sur la voie choisie, un menu avec des onglets s'affiche. Visiter les onglets pour modifier les réglages. Le réglage __indispensable__ est le __calibre__. Le reste correspond à des réglages de forme.
6. __Choisir une abscisse temporelle__ Faire un glisser-déplacer de l'horloge vers l'axe des abscisses.

```{margin}
Même si vous compter plus tard mettre en abscisses une autre grandeur (pour avoir $(u(t), i(t))$ par exemple), choisissez TOUJOURS le temps en abscisses pour pouvoir régler les paramètres d'acquisition.
```

7. __Régler les paramètres temporels.__ Il faut avoir réfléchi au phénomène que vous voulez observer. Il faut circuler dans les onglets généralement.
    1. __Durée d'acquisition__.
    2. __Nombre de points__ On reviendra sur cette notion plus tard. Par défaut, le choisir au maximum (16000 points) _en pensant à sauvegarder régulièrement._
    3. __Acquisition continue__. Il est souvent préférable de l'activer mais vous devrez déciser sur vous voulez une acquisition unique ou rafraichier régulièrement l'acquisition du signal.
    4. __Synchronisation__ Elle est indispensable en acquisition continue et vivement conseillée en acquisition unique. On précisera en TP son utilité.
    5. __Voie (pour la synchronisation), Valeur, Pente__ cf. TP
8. Lancer l'acquisition (bouton vert).
````

+++

#### Choix des paramètres

```{admonition} Exercice : Paramètres d'acquisition
:class: tip

Par la suite, on voudra tester le comportement de la diode pour différents types de signaux :
1. Un signal sinusoïdale de fréquence 1kHz, d’amplitude 10V et de valeur moyenne nulle
2. Un signal sinusoïdale de fréquence 20kHz, d’amplitude 3V et de valeur moyenne 1V
3. Un signal triangulaire de fréquence 3kHz, d’amplitude 3V, de valeur basse -2V
4. Un signal créneau de fréquence 500Hz, d’amplitude 8V et de valeur moyenne nulle
5. Un signal créneau de fréquence 30kHz, de valeur basse 0V et de valeur haute 6V.
6. Un signal modulé en amplitude $s = k v \times e$ avec e$,$ un signal sinusoïdal de fréquence 10kHz et d'amplitude 4V et $v$ un signal sinusoïdal de fréquence 500Hz et d'amplitude 4V. On donne $k = 0.1$.

On veut observer le signal délivré par le GBF dans chaque cas, on a brancher le GBF en parallèle de la voie 1 de la carte FOXY. Par chaque signal, préciser :
* le calibre de la voie 1 choisi
* la durée d'acquisition choisie

Note : Les calibres possibles sont `-0.25V/+0.25V`, `-5V/+5V`, `-15V/+15V`, `-30V/+30V`
```

+++

### Suivre l'évolution d'un signal : l'oscilloscope
Un oscilloscope est un instrument de suivi temporel de tension. Il embarque le système de mesure et l'affichage. Il existe deux types d'oscilloscopes : les oscilloscopes analogiques (la trace est obtenue par déviation d'un faisceau d'électron) et les oscilloscopes numériques (un écran - généralement LCD - affiche les données mesurées après traitement numérique). On travaillera principalement sur le second type d'oscilloscope.

```{margin}
Il existe aussi des oscilloscopes hybride analogique-numérique permettant de passer d'un fonctionnement à l'autre.
```

Le principe de réglage est à peu près le même que pour la carte d'acquisition à ceci près qu'on ne règle pas le nombre de points de mesure. La différence réside dans la position des boutons de réglages.

```{attention}
Un oscilloscope affiche sans s'arrêter ce qu'il est en train d'acquérir. Il peut alors être tentant de régler l'oscilloscope "au visuel" en se basant sur l'allure du signal observé. __Ne le faites pas !__ car c'est souvent une source d'erreur (on croit avoir bien l'oscilloscope alors que non).

Il faut toujours __prévoir la durée d'acquisition nécessaire__ et le __calibre vertical adpaté__ __en fonction du phénomène qu'on veut observer.__

_On ne réglera visuellement le signal que dans un second temps quand on a déjà un signal à peu près propre (affiner la qualité d'affichage)._
```

+++

#### Etapes de réglages.
La vidéo ci-après présente les boutons pour le FI32052 utilisé en TP et un poster regroupant la méthode de mesure est donné [ici](https://github.com/pcsi3physiquestan/donnees_exp/blob/main/poster_oscillo.pdf?raw=true).

Observer la vidéo ci-dessous pour voir les étapes de réglages.

```{code-cell} ipython3
---
tags: [remove-input]
---
from IPython.display import Video
Video("https://github.com/pcsi3physiquestan/videos_physique/blob/main/instrument_oscilloscope.mp4?raw=true", width=640)
```
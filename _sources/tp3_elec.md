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

# Introduction

Le premier TP d'électrocinétique sera divisé en trois séances. Le travail se décompose en :
* __[Familiarisation avec le matériel]__ : Vous allez commencer par apprendre à vous familiariser avec le matériel et les méthodes expérimentales à travers de la caractéristique statique puis dynamique d'un dipôle non linéaire (une diode). Cette étude, utile pour la suite, vous entraînera à réaliser des circuits électriques, faire des mesures avec un multimètre, une carte d'acquisition ou avec un oscilloscope et créer un signal de forme voulu avec un générateur basse-fréquence. Une __[étude préliminaire](./notebook/fam_preliminaire.ipynb)__ devra être réalisée avant le TP.
* __[Création d'un signal modulé]__ : Vous allez ensuite chercher à créer un signal modulé en amplitude. On apprendra ainsi à manipuler différents signaux ainsi qu'à mettre en cascade différents étages de traitement. La question des impédances d'entrée et de sortie seront alors abordées. Une __[étude préliminaire](./notebook/modul_preliminaire.ipynb)__ devra être réalisée avant le TP.
* __[Démodulation ]__ : Une fois le signal modulé créé, vous chercherez à démoduler ce signal de deux manières. La première utilisera la diode étudiée précédemment dans un _détecteur de crête_ et la seconde utilisera un système de filtrage (_démodulation synchrone_). On étudiera ainsi un régime transitoire et une réponse fréquentielle pour l'appliquer à la démodulation. Une __[étude préliminaire](./notebook/demod_preliminaire.ipynb)__ devra être réalisée avant le TP.
* __[Travail supplémentaire]__ : Si le temps le permet, vous essaierez de réinvestir ce que vous avez appris en TP et en cours pour étudier un système d'ordre 2.

Le compte-rendu du TP sera __manuscrit ou tapé (mais imprimé)__ et devra être rendu à la fin de la troisième séance. Un notebook sera utilisé pour l'étude complète et devra être rendu sur le site en plus du compte-rendu.

__Compétences mises en jeu :__

_Familiarisation (Plusieurs compétences mises en jeu seront réutilisées dans les autres TPs)_

| Compétences | Je sais de quoi ça parle | Je peux explier la méthode | Je sais l'appliquer |
|:------------| :-:|:-:|:-:|
|Choisir de façon cohérente la fréquence d’échantillonnage et la durée totale d’acquisition.||||
|Mesurer une tension à l'aide d'un multimètre ou un oscilloscope.||||
|Mesurer une intensité à l'aide d'un multimètre ou indirectement grâce à un oscilloscope.||||
|Visualiser la caractéristique d’un dipôle à l’aide d’un oscilloscope numérique ou d’une carte d’acquisition||||
|Obtenir un signal de valeur moyenne, de forme, d’amplitude et de fréquence données.||||
|Évaluer expérimentalement une résistance d’entrée ou de sortie.||||
|Repérer l’influence des résistances d’entrée ou de sortie sur le signal délivré par un GBF||||

_Modulation_

| Compétences | Je sais de quoi ça parle | Je peux explier la méthode | Je sais l'appliquer |
|:------------| :-:|:-:|:-:|
|Différencier masse et terre.||||
|Utiliser correctement un cable coaxial.||||
|Créer et régler un signal modulé en amplitude à partir d'un GBF.||||
|Gérer, dans un circuit électronique, les contraintes liées à la liaison entre les masses.||||
|Associer les fonctions de base de l'électronique pour réaliser une fonction complexe en gérant les contraintes liées aux impédances d’entrée et/ou de sortie des blocs.||||
|Repérer le caractère non linéaire d'un système grâce aux spectres des signaux entrée/sortie.||||


_Démodulation_

| Compétences | Je sais de quoi ça parle | Je peux explier la méthode | Je sais l'appliquer |
|:------------| :-:|:-:|:-:|
|Réaliser l’acquisition unique d’un régime transitoire pour un circuit linéaire du premier ordre et analyser ses caractéristiques.||||
|Réaliser l’acquisition répétée d’un régime transitoire pour un circuit linéaire du premier ordre et analyser ses caractéristiques.||||
|Mettre en œuvre une méthode directe ou indirecte de mesure de fréquence ou de période.||||
|Reconnaître une avance ou un retard de phase.||||
|Passer d’un décalage temporel à un déphasage et inversement.||||
|Repérer précisément le passage par un déphasage de 0 ou $\pi$en mode XY.||||
|Faire l'étude fréquentielle d'un filtre linéaire.||||
|Réaliser une détection synchrone.||||
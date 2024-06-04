---
title: Linux
description: Tout ce qu'il faut savoir sur linux
published: true
date: 2024-06-04T07:46:35.749Z
tags: 
editor: markdown
dateCreated: 2024-06-04T07:40:31.891Z
---

![logo](https://logos-marques.com/wp-content/uploads/2021/03/Linux-Symbole.png =300x){.align-center}

# Filesystem Hierarchy Standard (FHS)
## Principe

Le Filesystem Hierarchy Standard (FHS) est un document qui décrit l’organisation
du système de fichiers sous UNIX, comment les répertoires sont censés être
organisés et quels types de fichiers ils doivent contenir.

## Répertoires principaux
**/bin** commandes d’intérêt général
**/boot** fichiers nécessaires au démarrage du système
**/dev** fichiers spéciaux permettant l’accès aux périphériques
**/etc** fichiers de configuration du système et des applications
**/home** répertoires personnels des utilisateurs
**/lib** bibliothèques
**/opt** logiciels additionnels
**/proc** liste des processus et informations diverses
**/sbin** commandes pour l’administration du système
**/srv** données des services fonctionnant sur la machine
**/sys** informations sur les périphériques et leurs pilotes
**/usr** données partageables en lecture seule
**/var** données variables

# Linux
## Qu'est-ce que c'est ?
- Linux est uniquement un noyau (kernel).
- C’est important mais, pour construire un système complet et utilisable, il faut
ajouter d’autres composants :
	- un chargeur d’amorçage (bootloader)
	- un programme init
	- des bibliothèques (en particulier libc)
	- un environnement système (daemons)
	- un environnement utilisateur (userland)
	- un environnement graphique
- Beaucoup des composants ci-dessus étant fournis par le projet GNU, on désigne
souvent les systèmes les utilisant sour le nom GNU/Linux.
- C’est le but des distributions que de compléter le noyau pour aboutir à un
système complet.
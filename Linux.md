---
title: Linux
description: Tout ce qu'il faut savoir sur linux
published: true
date: 2024-06-04T13:12:18.040Z
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

## Distributions
Il existe de très nombreuses distributions Linux. Les plus connues sont :
AlmaLinux
Arch Linux
CentOS
Debian
Fedora
Gentoo
Linux Mint
Mageia
openSUSE
Red Hat Enterprise Linux
Rocky Linux
Slackware
SUSE Linux Enterprise
Ubuntu

les liens : 
https://almalinux.org/
https://fr.wikipedia.org/wiki/AlmaLinux
https://www.archlinux.org/
https://fr.wikipedia.org/wiki/Arch_Linux
https://www.centos.org/
https://fr.wikipedia.org/wiki/CentOS
https://www.debian.org/
https://fr.wikipedia.org/wiki/Debian
https://www.fedoraproject.org/
https://fr.wikipedia.org/wiki/Fedora_(Linux)
https://www.gentoo.org/
https://fr.wikipedia.org/wiki/Gentoo_Linux
https://www.linuxmint.com/
https://fr.wikipedia.org/wiki/Linux_Mint

# Une session
## Ouverture de session
Avant de pouvoir utiliser un ordinateur, il est nécessaire d’ouvrir une session, sur
un terminal directement relié à cet ordinateur ou par l’intermédiaire du réseau :

Ouverture de session (mode texte) :
![login-term.png](/images/linux/login-term.png)

Ouverture de session (mode graphique) : 
![login-graph.png](/images/linux/login-graph.png)


## La commande MAN
### Principe 

La commande man affiche le manuel de la commande indiquée en argument :
```bash
$ man bash
```
L’affichage du manuel est réalisé au moyen de la commande **less**.
Les pages de manuel se trouvent dans le répertoire **/usr/share/man**.

### Les sections
Les pages de manuel sont organisées en sections :
1. programmes exécutables ou commandes de l’interpréteur de commandes (shell)
2. appels système (fonctions fournies par le noyau)
3. appels de bibliothèque (fonctions fournies par les bibliothèques des programmes)
4. fichiers spéciaux (situés généralement dans /dev)
5. formats des fichiers et conventions (par exemple /etc/passwd)
6. jeux
7. divers
8. commandes de gestion du système (généralement destinées au super-utilisateur)
9. sous-programmes du noyau

Lorsque des pages de manuel homonymes existent dans plusieurs sections, il
peut être nécessaire d’indiquer la section souhaitée :
```bash
$ man 5 passwd
```

### Recherche dans les pages de manuel

- L'option -k (ou --apropos) permet d'afficher quelles pages de manuel contiennent l'expression indiquée dans leur nom ou leur description :
```bash
$ man -k password
```

- La commande apropos est équivalente :
```bash
$ apropos password
```

### l'option --help

De nombreuses commandes disposent d’une option --help destinée à afficher
une courte documentation :
```bash
$ usleep --help
Usage: usleep [microseconds]
-v, --version Display the version of this program, and exit
-o, --oot oot says hey!
Help options:
-?, --help Show this help message
--usage Display brief usage message
```















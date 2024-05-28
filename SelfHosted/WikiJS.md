---
title: WikiJs
description: Un jolie wiki autohébergé !
published: true
date: 2024-05-28T12:15:40.424Z
tags: 
editor: markdown
dateCreated: 2024-05-28T12:00:20.028Z
---

![](https://cdn-images.threadless.com/threadless-media/artist_shops/shops/wikijs/profile/logo-1531876777-e927870eea78296b4aa681910b70a189.png?v=3&d=eyJvbmx5X21ldGEiOiBmYWxzZSwgImZvcmNlIjogZmFsc2UsICJvcHMiOiBbWyJyZXNpemUiLCBbNjAwLCAyNTBdLCB7fV1dfQ==){.align-center}

# Présentation
Wiki.js est un outils selfhosted développé en javascript qui permet de mettre en place simplement un système de wiki puissant, complet et jolie.
L'un des gros avantages de ce dernier c'est la synchronisation avec git directement pour la sauvegarde et le versionning.
wiki.papamathi.com fonctionne avec Wiki.js depuis ses débuts sous Docker !
La version 3.0 devrais sortir d'ici la fin d'année 2025 avec beaucoup de nouveautés:

Site officiel : https://js.wiki
Documentation : https://docs.requarks.io

# Installation
## Linux

1. Téléchargez la dernière version de Wiki.js:
  ```bash
  wget https://github.com/Requarks/wiki/releases/latest/download/wiki-js.tar.gz
  ```
2. Décompressez l'archive dan s le dossier final de l'application :
  ```bash
  mkdir wiki
  tar xzf wiki-js.tar.gz -C ./wiki
  cd ./wiki
  ```
3. Renommez le fichier `config.sample.yml` en `config.yml` :
  ```bash
  mv config.sample.yml config.yml
  ```
4. Editez le fichier de config et remplissez les informations de votre base de données et de port : ([Configuration Reference](/install/config)):
  ```bash
  nano config.yml
  ```
5. ***Pour l'installation avec SQLite:*** *(ignorez cette etape sinon)* Récupère les liaisons natives pour SQLite3 :
  ```bash
  npm rebuild sqlite3
  ```
6. Lancez Wiki.js
  ```bash
  node server
  ```
7. Attendez que vous soyez invité à ouvrir la page de configuration dans votre navigateur.
8. Complétez l'assistant de configuration pour terminer l'installation.

### Run as service

Il existe plusieurs solutions pour exécuter Wiki.js en tant que service en arrière-plan. Nous allons nous concentrer sur **systemd** dans ce guide car il est disponible dans presque toutes les distributions linux.

1. Créez un nouveau fichier nommé `wiki.service` dans le répertoire `/etc/systemd/system`.
  ```bash
  nano /etc/systemd/system/wiki.service
  ```
2. Collez le contenu suivant (en supposant que votre wiki est installé dans `/var/wiki`) :
  ```ini
  [Unit]
  Description=Wiki.js
  After=network.target

  [Service]
  Type=simple
  ExecStart=/usr/bin/node server
  Restart=always
  # Consider creating a dedicated user for Wiki.js here:
  User=nobody
  Environment=NODE_ENV=production
  WorkingDirectory=/var/wiki

  [Install]
  WantedBy=multi-user.target
  ```
3. Sauvegardez le fichier (<kbd>CTRL</kbd>+<kbd>X</kbd>, suivis de <kbd>Y</kbd>).
4. Redémarrez systemd :
  ```bash
  systemctl daemon-reload
  ```
5. Lancez le service :
  ```bash
  systemctl start wiki
  ```
6. Activez le service au démarrage :
  ```bash
  systemctl enable wiki
  ```

> Vous pouvez consultez les logs du service avec `journalctl -u wiki`
{.is-info}

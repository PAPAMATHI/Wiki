---
title: Guide d'installation Docker
description: 
published: true
date: 2024-05-28T11:39:01.703Z
tags: docker
editor: markdown
dateCreated: 2024-05-27T11:18:25.546Z
---

# Comment installer Docker sur Linux (Almalinux)
**Étapes pour installer Docker sur Linux (AlmaLinux)**
## 1. Assurez-vous que les conditions préalables sont en place
- Système d'exploitation et version : Almalinux 9.0
- Utilisez la commande sudo en tant qu'utilisateur root pour vous connecter au système AlmaLinux 9 ou connectez-vous en tant qu'utilisateur disposant de droits d'administrateur.

## 2. Mettez à jour votre système
Avant d'installer Docker sur Linux (AlmaLinux), vous devrez mettre à jour les référentiels de packages de votre système à l'aide des commandes suivantes pour vous assurer d'obtenir les dernières versions des packages :
```bash 
sudo dnf --refresh update
sudo dnf upgrade
```

## 3. Activer le référentiel Docker
Vous pouvez installer le package yum-utils à l'aide de la commande suivante, qui fournit l'utilitaire yum-config-manager pour configurer les référentiels :
```bash
sudo dnf install yum-utils
```
Maintenant, vous pouvez ajouter le référentiels Docker en utilisant **yum-config-manager**.
```bash
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```
## 4. Installez Docker sur Almalinux avec la commande DNF.
```bash
sudo dnf install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

## 5. Démarrez et Activez le service Docker.
Une fois Docker et ses dépendances installés, démarrez et activez son service à l'aide des commandes suivantes :
```bash
sudo systemctl start docker
sudo systemctl enable docker
```

En utilisant cette commande, vous pouvez voir le service docker tourner.
```bash
sudo systemctl status docker
```

## 6. Vérifier la version de Docker.
Pour continuer, vous pouvez utiliser la commande ci-dessous pour vérifier la version de docker.
```bash
sudo docker version
docker --version
```

## 7. Testez l'installation de Docker.

Pour tester l'installation, démarrez un conteneur Docker avec l'image **hello-world** :

```bash
sudo docker run hello-world
```

la sortie : 
```
~]# sudo docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
719385e32844: Pull complete 
Digest: sha256:dcba6daec718f547568c562956fa47e1b03673dd010fe6ee58ca806767031d1c
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

## 8. Ajouter un utilisateur au groupe d'utilisateurs Docker.
Vous pourrez ajouter votre utilisateur local au groupe docker afin que l'utilisateur puisse utiliser les commandes docker sans sudo.

Remplacez $USER selon vos besoins. Vous pouvez utiliser la commande suivante pour voir si votre utilisateur est membre du groupe Docker :
```bash
id $USER
```

Voici le résultat : 
```bash
~]# sudo usermod -aG docker root
~]# id root
uid=0(root) gid=0(root) groups=0(root),991(docker)
```
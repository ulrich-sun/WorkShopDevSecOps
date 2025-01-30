# Build d'une image avec Kaniko sur Kubernetes (k3s)

## Introduction

Bonjour à tous,

Dans ce projet, nous allons installer Kubernetes via **k3s** et procéder au build de notre image avec **Kaniko**.

- **k3s** : Une version allégée de Kubernetes initiée par Rancher, permettant de déployer rapidement un cluster fonctionnel.
- **Kaniko** : Une solution permettant de builder des images sans nécessiter un démon Docker en cours d'exécution.

## Infrastructure requise

- **Machine virtuelle (VM)** : k3s
- **Système d'exploitation** : Ubuntu 20.04 LTS
- **Configuration minimale** : 1 CPU & 1 Go de RAM
- **Configuration recommandée** : 2 CPU & 4 Go de RAM (utilisée pour ce projet)

## Installation de k3s

Exécutez la commande suivante pour installer k3s :

```sh
curl https://raw.githubusercontent.com/ulrich-sun/help-script/refs/heads/main/k3s.sh | sh -
```

## Récupération des fichiers

Clonez le dépôt contenant les fichiers nécessaires :

```sh
git clone -b kaniko https://github.com/ulrich-sun/WorkShopDevSecOps.git
```

## Création du secret Docker Registry

Avant de builder l'image avec Kaniko, créez un secret Kubernetes pour l'authentification à Docker Hub :

```sh
kubectl create secret docker-registry docker-config-secret \
  --docker-server=https://index.docker.io/v1/ \
  --docker-username=<dockerhub-username> \
  --docker-password=<dockerhub-password> \
  --docker-email=<dockerhub-email> -o yaml --dry-run=client > docker-config-secret.yaml
```

Remplacez `<dockerhub-username>`, `<dockerhub-password>` et `<dockerhub-email>` par vos informations Docker Hub.

---

Vous êtes maintenant prêt à builder votre image avec Kaniko `<lien vidéo you tube>`! 🚀
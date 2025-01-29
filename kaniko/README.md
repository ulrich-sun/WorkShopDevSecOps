Hello a tous

Nous allons realiser l'installation de Kubernetes via k3s puis realiser le build de notre image avec Kaniko

  

k3s est une version legere de kubernetes initie par rancher et qui nous permet d'avoir tres rapidement un cluster de fonctionnel

kaniko est une solution qui nous permet de realiser le build d'image sans toute fois avoir besoin d'un demon docker

  

notre infra:

-   vm: k3s
-   image: ubuntu:20.04-lts
-   4Go de RAM & 2CPU (c'est ma configuration , mais k3s demande au minimum 1 CPU et 1Go de RAM)

Installation de k3s:

-   curl https://raw.githubusercontent.com/ulrich-sun/help-script/refs/heads/main/k3s.sh | sh -

recuperer les fichiers ;

-   git clone -b kaniko https://github.com/ulrich-sun/WorkShopDevSecOps.git
-   creer votre secret docker-registry
    ''' bash 
        kubectl create secret docker-registry docker-config-secret \
        --docker-server=https://index.docker.io/v1/ \
        --docker-username=<dockerhub-username> \
        --docker-password=<dockerhub-password>\
        --docker-email=<dockerhub-email> -oyaml --dry-run=client > docker-config-secret.yaml
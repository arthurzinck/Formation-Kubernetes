# Kubernetes

Kubernetes est un systeme opensource pour gerer le cycle de vie des conteneur. Kubernetes veut dire pilote en Greque. Il a ete [creer a la suite de 15 ans d'utilisation de Borg](https://kubernetes.io/blog/2015/04/borg-predecessor-to-kubernetes/), un autre systeme similaire interne a Google. Il avait certains concept en communs mais avais moins de fonctionnalité que K8s peut avoir. Google a OpenSourcé le projet Kubernetes en 2014. Une grosse comunité de pleins d'entreprise et de developpeur independant ont aidé a structurer et a developper le projet.

Kubernetes a bien evolué est utiliser maintenant par des miliers d'entreprise a travers le monde.

Kubernetes permet d'orchester des centaines de conteneurs en production en assurant une qualité de services et permetant une scalabité horizontal et vertical des differents groupe de conteneurs.

 ## A travers le temps

![image](Container_Evolution.svg)

### Ere Deploiment Traditionnel
Avant on deployait les applications directement sur des serveurs physique. Il n'y avait aucun moyen de definir de limite de ressource, cela posait des soucis d'allocations des resources entre les applications. Par exemple si une applications prends beaucoup de ressource, elle pourrait prendre les ressources des autre applications, la faisant sous performer. Une solutions a ce soucis serait d'avoir des serveurs phyique different pour chacune des applications mais cela engendre des couts important pour les entrerpises.

### Ere du deploiement Virtualiser
Comme solutions, la virtualisation a été introduite. Cela permet de faire tourner plusieur machine virtuel, sur un seul serveur physique. La Virtualisation permet au applications d'etre isolée les unes des autres et ajoute un niveau de securité puisque les informations d'une application ne peut etre acceder par une autre application.

La Virtualisation permet aussi une meilleur utilisation des ressource d'un serveur physique et celaa permet une meilleur scalabité puisque les machine peuvent etre dupliqué mais aussi deplacer sur de nouvelle machine physique. On peut ansi faire des clusters de machine physique avec des machines virtuel a dispositions.

Chaque VM est une machine entiere qui fait tourner l'integralité des composant, soms propre noyeau avec sont systeme d'exploitation pour gere les composant hardware virtualisé.

### Ere du deploiement en Conteneur
Les conteneur sont similaire au VM, mais leur proprieté d'isolation sont un peu moins stricte, elle partage le system d'exploitations avec les autre applications. C'est pour cela qu'ils sont considere comme plus leger. Pareil que les VM les conteneurs ont leur propre filesystem, une fraction de cpu, etc. Vu qu'ils sont detaché de linfrastructure en dessous, ils sont portable a travers les different cloud provider et OS.

Les containeurs ont pris en popularité parce qu'ils ont nombre d'avantages:
* leur capacité a se soustraire de l'infrastructure qui les fait tourné: une image contient tout ce qu'il faut de librairy et de code pour faire tourner son app.
* leur creation et leur deploiement est plus souple : augmentation de la facilité et de l'efficatite de creation d'une image de conteneur en comparaison d'une image de VM.
* le developement au meme moment d'architecture logicielle basé sur des microservice rompant avec le modele domminant du monolith


## Architecture

![Alt text](components-of-kubernetes.svg)

### Control-plane nodes
Communement appelé les Master, son nom change suite au mouvement Black Lives Matter. 
C'est noeuds peuvent etre 1 ou 3 en High Availability.
Ils hebergent les application qui font fonctionner le cluster.

* Kube Api server: API de Kubernetes c'est elle qui permet de comuniquer avec le cluster que ce soit pour creer, modifier ou detruire des ressources, ou meme pour recuperer des infos.

* ETCD: L'Api Server ecrit toutes les infos en Base de donnée, cette base c'est ETCD. C'est une base qui est dite NoSql, une base dans lequels on stock des Clefs=Valeurs.

* Kube Scheduler: C'est un composant qui cherche des pods nouvellement crée sans noeuds attribué. il regarde different paramettre et attribue un noeud au pod.

* Kube Controler manager: C'est un composant de controle qui tourne independamment son travail c'est de reconcilier l'etat actuel avec l'etat désiré. Il plein de boucle de controle differentes
* Cloud Controller manager: Composant qui permet un meilleur integration du cluster kubernetes avec les service managé  du cloud provider
* Konnectivity Server: Permet la comuniquation entre les noeuds et les masters

### Worker
* Kube Proxy: Composant deployer sur chacun des worker nodes, il creer de regle de redirictions et les maintiens a jours pour accedder au different Pod sur chacuns des noeuds.
* Kubelet: Composant deployer sur chacun des worker nodes, il s'assure que les pod attribuer a son noeuds soit demarré et en bonne santé. Mais ce n'est pas lui qui creer les conteneurs.
* Container Runtime: C'est le composant qui fait tourner les conteneurs, cela peut etre Docker, ContainerD, ou Cri-o.
* Konnectivity Agent: creer une connection tcp du noeuds au Konnectivity server et permet ainsi une conexion securisé entre Control Plane et Worker.

### Addons
* CNI : Container Network Interfaces, utiliser pour permetres d'un avoir un reseau inter conteneur qui s'abstrait des noeuds. il en existe plein Calico, Cilium, Weave..
* DNS: Permetre au container de se joindre avec des noms de domaines, pratique quand les applications doivent se parler.
* Ingress: Permet de faire des regle d'association entre une application et un nom de domaines.

## Installation de minikube ou de kind


Pour avoir un cluster sur votre machine, vous pouvez utilisez : 
* miniKube:  
    * [doc d'installation de minikube](https://minikube.sigs.k8s.io/docs/start/)    
* Kind :
    * [Doc d'installation de kind](https://kind.sigs.k8s.io/docs/user/quick-start/#installing-from-release-binaries)
    * [Doc de configuration de kind](https://kind.sigs.k8s.io/docs/user/quick-start/#creating-a-cluster)

Pour pouvoir communiquer avec votre cluster vous aurez besoin de Kubectl
[Doc d'installation de kubectl](https://kubernetes.io/fr/docs/tasks/tools/install-kubectl/#installation-%C3%A0-l-aide-des-gestionnaires-des-paquets-natifs)

## Les Objet Kube

### Pod
#### Execice 1 :
Creer un pod nginx classic y acceder 
### ConfigMap
#### Exercice 1: 
Creer un pod et lui charger une configmap en variable d'environement avec le contenue que vous souhaitez 
### Exercice 2: 
Creer un pod et lui charger une configmap en montage de volume dans `/etc/configmap`

### Secret
#### Exercice 1: 
Creer un pod et lui charger un sercret en variable d'environement
#### Exercice 2: 
Creer un pod et lui charger un sercret en montage de volume dans `/etc/secret`


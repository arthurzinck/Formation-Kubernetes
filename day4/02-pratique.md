# Partie Pratique 

## Exercice 1: 
Déployez un cluster Kubernetes minimaliste (vous pouvez utiliser Minikube ou un environnement similaire). Fournissez les commandes utilisées et capturez les sorties de commande.

## Exercice 2: 
Créez un déploiement simple dans Kubernetes qui lance un serveur web (par exemple, nginx ou httpd). Fournissez le fichier YAML utilisé pour le déploiement.

## Exercice 3: 
Ajouter a ce déploiement une configmap. Cette configmap doit etre chargé dans les variables d'environement. 
Elle doit contenire : 
* NOM
* PRENOM
* JOUEUR_PREF

Fournissez le fichier YAML utilisé pour le déploiement et la configmap.

## Exercice 4: 
Ajouter a ce déploiement un secret. il doit etre monté en variable d'environement.
Il doit contenir: 
* NUM_CARTE_BLEU
* CODE_CARTE_BLEU
  
Fournissez le fichier YAML utilisé pour le déploiement et la configmap.

## Exercice 5: 
Configurez un service dans Kubernetes pour exposer le serveur web déployé dans l'exercice précédent. Fournissez le fichier YAML du service et démontrez comment accéder au serveur web depuis l'extérieur du cluster.

## Exercice 6: 
Créer un chart Helm. Modifier le helm chart pour qu'il y ai 2 deploiement un pour wordpress l'autre pour Mysql. Documentez les étapes et les commandes utilisées pour l'installation.



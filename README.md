# Formation-Kubernetes

## cheatsheet :

| quoi                                 | comment                                        |
|:-------------------------------------|-----------------------------------------------:|
| Pour afficher les objects            | kubectl get <object> -n <namespace>            |
| Pour afficher le yaml d'un objet     | kubectl get <object> -n <namespace>  -o yaml   |
| Pour afficher les infos d'un objet   | kubectl describe <object>/<nom>                |
| Pour creer un pod                    | kubectl run <nom>  --image=<image:version>     |
| Appliquer un fichier yaml            | kubectl apply -f <fichier.yaml>                |
| modifier le nombre d'instance d'un deploiment | kubectl scale deploy/<nom> --replicas=<nombre> |
| helm create <nom>                    | creer un chart helm                            |
| helm apply <nom> <chart> -f <fichier>| creer une release d'un chart avec un fichier de surcharge |
| helm diff upgrade <nom> <chart> -f <fichier> | afficher la difference entre la release dans le cluster et ce qui est en local|

* [day1](day1/Readme.md)
* [day2](day2/Readme.md)
* [day3](day3/Readme.md)

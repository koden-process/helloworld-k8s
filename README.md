# helloworld-k8s

Il faut avoir un cluster fonctionnel pour effectuer les étapes d'installation ci-dessous ! 

Rendez-vous sur https://github.com/koden-process/k8s-base pour installer le cluster. 

```
kubectl create namespace hw-namespace 
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl apply -f ingress.yaml
```

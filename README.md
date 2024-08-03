# helloworld-k8s

## déploiement de let's encrypt
Pré-requis : Il faut avoir un gestionnaire de certification SSL sur le cluster (à installer une seule fois)
'''
helm repo add jetstack https://charts.jetstack.io
helm repo update
kubectl apply --validate=false -f https://github.com/cert-manager/cert-manager/releases/download/v1.11.0/cert-manager.yaml
'''

clusterissuer.yaml
'''
apiVersion: cert-manager.io/v1
kind: ClusterIssuer
metadata:
  name: letsencrypt-prod
spec:
  acme:
    server: https://acme-v02.api.letsencrypt.org/directory
    email: votremail@example.com
    privateKeySecretRef:
      name: letsencrypt-prod
    solvers:
    - http01:
        ingress:
          class: nginx

'''

'''
kubectl apply -f clusterissuer.yaml
'''

## déploiement de l'ingress controler
'''
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml
'''


## déploiement de l'app

'''
kubectl create namespace hw-namespace 
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl apply -f ingress.yaml
'''

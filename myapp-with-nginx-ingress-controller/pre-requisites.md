### Install Helm
```sh
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```
### Install Nginx Ingress Controller: 
```sh
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update
kubectl create namespace ingress-basic
helm install nginx-ingress ingress-nginx/ingress-nginx -n ingress-basic
```
### Create the SSL/TLS Secret 
```sh
kubectl create secret tls wingerp.net-tls \
  --cert=/home/jamal/Documents/SSL-CERTS/wingserp.net/CA_Chain.crt \
  --key=/home/jamal/Documents/SSL-CERTS/wingserp.net/wingserp.net.key \
  -n default
```

### Deploy the Application
```sh
kubectl apply -f nginx-deployment-and-hpa.yaml
kubectl apply -f nginx-service-and-ingress.yaml
```
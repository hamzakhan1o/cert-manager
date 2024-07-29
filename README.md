# cert-manager
cert manager with kubernetes using self signed certificate and nginx ingress controller 
Documentation Link: https://docs.google.com/document/d/1D_l5NWrKQHbZOgqgD9M-EiTnzKSkel9WvieFkFO-qKQ/edit?usp=sharing

Steps 

First of all, install cert-manager on the Kubernetes cluster and Check the compatibility of Kubernetes with cert-manager i have installed version 1.14.6 as it is compatible with Kubernetes version 1.29.6

kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.14.6/cert-manager.yaml

This will apply the file and create the cert manager pods on the cert-manager namespace


Afterwards, create and apply manifests for self-signed certificates as I don't have a domain right now 

Edit the /etc/host directory and map the IP address of the machine with the desired domain name 

Create a signed issuer


kubectl apply -f selfsigned-issuer.yaml

Now create a certificate request 



kubectl apply -f nginx-cert.yaml

Now i will create an nginx webserver 

First, create the nginx deployment 

Apply the file 
kubectl apply -f nginx-tls-deployment.yaml
Now service

kubectl apply -f nginx-tls-service.yaml

Now install ingress controller 

kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml



Create Ingress manifest


Apply 

Kubectl apply -f nginx-ingress.yaml

Access the page on the browser 




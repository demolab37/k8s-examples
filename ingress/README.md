# Ingress-Nginx example

Expose example services with the Ingress-Nginx to outside the cluster.

# Setup
```
# Deploy the Ingress-Nginx controller
$ kubectl apply -f ingress-nginx.yaml

# create the pods
$ kubectl apply -f apple-pod.yaml
$ kubectl apply -f banana-pod.yaml

# create the ClusterIP services
$ kubectl apply -f apple-svc.yaml
$ kubectl apply -f banana-svc.yaml

# create the shared Ingress resource
$ kubectl apply -f shared-ingress.yaml
```

# Testing
```
$ kubectl get svc -n ingress-nginx

ssh minikube
curl -L -v <minikube-host-IP>:<node-port>/apple
curl -L -v <minikube-host-IP>:<node-port>/banana
```

See:
* https://kubernetes.github.io/ingress-nginx/deploy/
* https://kubernetes.github.io/ingress-nginx/deploy/baremetal/



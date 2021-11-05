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

# Name-based Ingress:
$ curl -H 'Host: apple.example.com' http://192.168.64.4:31815
apple
$ curl -H 'Host: banana.example.com' http://192.168.64.4:31815
banana

# Path-based Ingress:
$ curl http://192.168.64.4:31815/apple
apple
$ curl http://192.168.64.4:31815/banana
banana
```

See:
* https://kubernetes.io/docs/concepts/services-networking/ingress/
* https://kubernetes.github.io/ingress-nginx/deploy/
* https://kubernetes.github.io/ingress-nginx/deploy/baremetal/


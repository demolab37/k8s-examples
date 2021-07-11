# Docker registry

Run a Docker registry in K8s. 

# Setup
```
# create the ConfigMap
$ kubectl apply -f registry-cm.yaml

# create the Deployment
$ kubectl apply -f registry-deploy.yaml

# create the ClusterIP service
$ kubectl apply -f nginx-svc.yaml
```

# Testing
```
curl -T <upload-file> -v http://<nginx-svc-IP>/upload/
```

See:
* https://kubernetes.io/docs/concepts/storage/volumes



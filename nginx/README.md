# Sample nginx deployment 

With custom upload-config to emptyDir volume and customization using ConfigMap. Accessible via ClusterIP service nginx-service

# Setup
```
# create the ConfigMap
$ kubectl create cm nginx-cm --from-file=./default.conf

# create the Secret
$ kubectl create secret generic app-secret --from-file=./nginx-secret.yaml

# create the Deployment
$ kubectl apply -f nginx-deploy.yaml

# create the ClusterIP service
$ kubectl apply -f nginx-svc.yaml
```

# Testing
```
curl -T <upload-file> -v http://<nginx-svc-IP>/upload/
```

See:
* https://kubernetes.io/docs/concepts/storage/volumes



# Sample nginx deployment 

With custom upload-config to emptyDir volume and customization using ConfigMap. Accessible via ClusterIP service nginx-service

# Setup
```
$ kubectl create cm nginx-cm --from-file=./default.conf
$ kubectl apply -f nginx-deploy.yaml
$kubectl apply -f nginx-svc.yaml
```

# Testing
```
curl -T <upload-file> -v http://<nginx-svc-IP>/upload/
```

See:
* https://kubernetes.io/docs/concepts/storage/volumes



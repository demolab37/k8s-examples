# Kubernetes-Event-Exporter

Small interface to capture K8s cluster events and forward them to various targets. Sample config with ElasticSearch as log target.

Adjust the 01-config.yaml ConfigMap as needed. 

Note: The 01-config.yaml has username/password fields for ElasticSearch. Externalizing them and reading form environment (similar to fluentd-config.yaml) didn't work. Instead, the application config (including the plaintext user/pass) needs to be imported as K8s secret.

```
$ kubectl get secret elk-es-elastic-user -o=yaml -n elastic
$ vim config.yaml // add user/pass from ElasticSearch secret to config"
$ kubectl apply -f 00-roles.yaml -n monitoring
$ kubectl create secret generic event-exporter-cfg --from-file=./config.yaml -n monitoring
$ kubectl apply -f 02-deployment.yaml -n monitoring
```

See:
* https://github.com/opsgenie/kubernetes-event-exporter



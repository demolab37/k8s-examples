# FluentD log aggregator

Adjust the ElasticSearch Host and user/pass in the StatefulSet YAML to match.

The ElasticSearch password is encapsulated in the K8s secret elastic-secret.yaml with a default value. 
To get the ElasticSearch password from the ElasticSearch operator:
$ kubectl get secret elk-es-elastic-user -n elastic -o=yaml
Update the elastic-secret in the FluentD NS (kube-system).

Adjust the fluentd.conf ConfigMap as needed.

See:
* https://ptrk.io/posts/2018/05/tweaking-an-efk-stack-on-kubernetes/
* https://medium.com/kubernetes-tutorials/cluster-level-logging-in-kubernetes-with-fluentd-e59aa2b6093a
* https://github.com/fluent/fluentd-kubernetes-daemonset
* https://docs.fluentd.org/filter/grep


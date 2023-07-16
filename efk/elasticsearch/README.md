# ElasticSearch and Kibana (ELK) 

## Requirements:
Default storage class defined for persistent storage claims, e.g. NFS.

## Install ELK Operator:

```
$ k apply -f elasticsearch/all-in-one.yaml
```

## Install ElasticSearch:

```
$ k create ns elastic
$ k apply -f elasticsearch/elk-mini.yaml -n elastic
```

## Install Kibana:

```
$ k apply -f elasticsearch/kibana.yaml -n elastic
```

## Check ELK cluster:
```
vagrant@cluster1-master1:~$ k get elastic -n elastic
NAME                                             HEALTH   NODES   VERSION   PHASE   AGE
elasticsearch.elasticsearch.k8s.elastic.co/elk   yellow   1       7.13.2    Ready   7h55m

NAME                               HEALTH   NODES   VERSION   AGE
kibana.kibana.k8s.elastic.co/elk   green    1       7.13.2    7h51m
vagrant@cluster1-master1:~$
```

## Access Kibana from Vagrant host:

```
vagrant@cluster1-master1:~$ k get secret -n elastic elk-es-elastic-user -o=yaml
vagrant@cluster1-master1:~$ kubectl port-forward --address 10.0.2.15 service/elk-kb-http 3000:5601
```

## ELK cluster customization
Config-as-code for index template:
```
$ k apply -f elasticsearch/es-customizer-cm.yaml
$ k apply -f elasticsearch/es-customizer-job.yaml
```
Dependencies: $ES_API_AUTH secret var from secret elk-es-elastic-user

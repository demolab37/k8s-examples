# NFS Storage Class provisioner (Operator)

## Upstream documentation
https://github.com/kubernetes-sigs/nfs-subdir-external-provisioner/blob/master/charts/nfs-subdir-external-provisioner/README.md

## Pre-Installation
Setup the NFS share

```
$ apt -y install nfs-kernel-server
$ mkdir -pv /mnt/share
```

```
$ vi /etc/exports
  mnt/share      192.168.101.0/24(rw,sync,no_subtree_check,no_root_squash)
```

  no_root_squash mount option is needed to allow pods that use the PVs to change file ownership in the volume.

```
$ exportfs -ra
$ systemctl restart nfs-kernel-server
```

## Installation

```
$ helm repo add nfs-subdir-external-provisioner https://kubernetes-sigs.github.io/nfs-subdir-external-provisioner/

$ helm install nfs-operator nfs-subdir-external-provisioner/nfs-subdir-external-provisioner \
  --name nfs-client-provisioner \
  --set nfs.server=<NFS Server IP> \
  --set nfs.path=/exported/path \
  --set storageClass.name=nfs \
  --set storageClass.defaultClass=true \
  nfs-subdir-external-provisioner/nfs-subdir-external-provisioner

```



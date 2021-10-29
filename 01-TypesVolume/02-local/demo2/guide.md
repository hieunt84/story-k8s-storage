### Chuẩn bị
- Cluster k8s kubeadm 1 node
- add hdd 

### Config pv
```
helm install -f ./helm/provisioner/values.yaml myrelease ./helm/provisioner

```

### Ref
```
https://github.com/kubernetes-sigs/sig-storage-local-static-provisioner/blob/master/docs/operations.md
```

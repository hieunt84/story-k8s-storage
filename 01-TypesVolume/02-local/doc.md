### What ?
- loại volume này đại diện cho hdd, ssd, directory được mount vào node.

### Trường hợp sử dụng (When/Why/Use Cas):
- cần sử dụng hdd, ssd trên node

### Tính năng
- ổn định hơn hostPath Volume.

### local configuration example
```
apiVersion: v1
kind: PersistentVolume
metadata:
  name: example-pv
spec:
  capacity:
    storage: 100Gi
  volumeMode: Filesystem
  accessModes:
  - ReadWriteOnce
  persistentVolumeReclaimPolicy: Delete
  storageClassName: local-storage
  local:
    path: /mnt/disks/ssd1
  nodeAffinity:
    required:
      nodeSelectorTerms:
      - matchExpressions:
        - key: kubernetes.io/hostname
          operator: In
          values:
          - example-node
```

### Ref
```
https://kubernetes.io/blog/2019/04/04/kubernetes-1.14-local-persistent-volumes-ga/
https://kubernetes.io/docs/concepts/storage/volumes/
```

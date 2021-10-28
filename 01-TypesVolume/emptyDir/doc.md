### What ?
- An emptyDir volume is first created when a Pod is assigned to a node, and exists as long as that Pod is running on that node. As the name says, the emptyDir volume is initially empty. All containers in the Pod can read and write the same files in the emptyDir volume, though that volume can be mounted at the same or different paths in each container. When a Pod is removed from a node for any reason, the data in the emptyDir is deleted permanently.

### Some uses for an emptyDir are:
- scratch space, such as for a disk-based merge sort
- checkpointing a long computation for recovery from crashes
- holding files that a content-manager container fetches while a webserver container serves the data


### Tính năng
- Tùy thuộc vào môi trường, emptyDir có thể được lưu trữ trên thiết bị (medium) của node như: hdd, ssd, network storage.
- Có thể cấu hình emptyDir lưu trữ trên RAM, rất nhanh so với các thiết bị khác.

### emptyDir configuration example
```
apiVersion: v1
kind: Pod
metadata:
  name: test-pd
spec:
  containers:
  - image: k8s.gcr.io/test-webserver
    name: test-container
    volumeMounts:
    - mountPath: /cache
      name: cache-volume
  volumes:
  - name: cache-volume
    emptyDir: {}
```
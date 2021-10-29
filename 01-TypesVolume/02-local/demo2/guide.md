### Chuẩn bị
1. Cluster k8s kubeadm 1 node
2. Add hdd
3. Format and mount
```
$ $ sudo mkfs.ext4 /dev/path/to/disk
$ DISK_UUID=$(sudo blkid -s UUID -o value /dev/path/to/disk) 
$ sudo mkdir -p /mnt/fast-disks/$DISK_UUID
$ sudo mount -t ext4 /dev/path/to/disk /mnt/fast-disks/$DISK_UUID

```
4. Persistent mount entry into /etc/fstab
```
$ echo UUID=`sudo blkid -s UUID -o value /dev/path/to/disk` /mnt/fast-disks/$DISK_UUID ext4 defaults 0 2 | sudo tee -a /etc/fstab

```

5. Create StorageClass
```
kubectl create -f deployment/kubernetes/example/default_example_storageclass.yaml

```

6. Creating local persistent volumes by provisioner
```
helm install myrelease ./helm/provisioner
kubectl get pv
```

7. Create pvc2
```
kubectl apply -f pvc2.yaml
```

7. Test
```
kubectl apply -f test2.yaml
```

### Ref
```
https://github.com/kubernetes-sigs/sig-storage-local-static-provisioner/blob/master/docs/getting-started.md

https://github.com/kubernetes-sigs/sig-storage-local-static-provisioner/blob/master/docs/operations.md
```
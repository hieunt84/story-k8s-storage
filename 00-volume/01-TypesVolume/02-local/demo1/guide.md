### Chuẩn bị
1. Cluster k8s minikube
2. Add hdd vào vm minikube
3. Format and mount
```
$ sudo mkfs.ext4 /dev/path/to/disk
$ DISK_UUID=$(sudo blkid -s UUID -o value /dev/path/to/disk) 
$ sudo mkdir /mnt/disks/$DISK_UUID
$ sudo mount -t ext4 /dev/path/to/disk /mnt/disks/$DISK_UUID

```
4. Persistent mount entry into /etc/fstab
```
$ echo UUID=`sudo blkid -s UUID -o value /dev/path/to/disk` /mnt/disks/$DISK_UUID ext4 defaults 0 2 | sudo tee -a /etc/fstab

```

5. Create StorageClass
```
kubectl apply -f StorageClass.yaml

```

6. Create pv1
```
kubectl apply -f pv1.yaml
```

6. Create pvc1
```
kubectl apply -f pvc1.yaml
```

7. Test
```
kubectl apply -f test11.yaml
```

### Ref
```
https://github.com/kubernetes-sigs/sig-storage-local-static-provisioner/blob/master/docs/getting-started.md#step-4-create-local-persistent-volume-claim

https://github.com/kubernetes-sigs/sig-storage-local-static-provisioner/blob/master/docs/operations.md
```
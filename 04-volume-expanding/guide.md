### Giới thiệu
- Tài liệu hướng dẫn mở rộng volume loại csi

### Qui trình thực hiện
- chỉnh lại dung lượng cần mở rộng trong file example-pvc.yaml
- bổ sung thay đổi
```
kubectl apply -f example-pvc.yaml
```
- triển khai pod sử dụng pvc này thì thay đổi mới diễn ra hoàn thành
- kiểm tra lại dung lượng pvc
```
kubectl get pvc
``` 

### ref
```
https://kubernetes.io/docs/concepts/storage/persistent-volumes/
```



### Giới thiệu
- Việc quản lý lưu trữ trong k8s khác với việc quản lý tính toán (compute instances).
- k8s giới thiệu hai loại tài nguyên API: PersistentVolume (PV) and PersistentVolumeClaim (PVC) để hỗ trợ lưu trữ cho user và admin.
- A PV là phần lưu trữ trong cụm mà được cấp phát bới admin hoặc tự động thông qua Storage Classes.
- A PVC là 1 yêu cầu lưu trữ của user.
- Storage Classes (SC) là 1 loại tài nguyên, để miêu tả những đặc tính (nhanh chậm, iops), chính sách (lưu trữ, chất lượng dịch vụ,...) của hệ thống lưu trữ bên dưới (backend storage), thỉnh thoảng SC còn được gọi là hồ sơ (profiles).

### ref
```
https://kubernetes.io/docs/concepts/storage/persistent-volumes/
```



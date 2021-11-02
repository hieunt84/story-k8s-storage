### Volume là gì ?
- volume là thư mục, có thể chứa data.

### Tại sao cần volume ?
- để lưu trữ dữ liệu tránh bị mất khi container bị lỗi.
- để chia sẽ giữa các container chạy cùng 1 pod.

### Các loại volume
- persistent volume (lâu dài): tồn tại ngoài vòng đời của pod
- ephemeral volumes (tạm thời): tồn tại theo vòng đời của pod

### Để sử dụng volume
- chỉ định volume cung cấp cho pod thông qua cấu hình
```
.spec.volumes
```
- và khai báo mount volume vào trong container
```
.spec.containers[*].volumeMounts
```
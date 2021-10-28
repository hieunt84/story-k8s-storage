### What ?
- là loại volume storage được Kubernetes hỗ trợ để phát triển và thử nghiệm trên một cụm chỉ có 1 node đơn.

### Trường hợp sử dụng (When/Why):
- sử dụng môi trường phát triển và thử nghiệm.
- Cần truy cập file và thư mục của host (không an toàn).

### Tính năng
- Một hostPath Volume sẽ gắn một file hoặc thư mục ngay trên node máy chủ vào pod của bạn để làm không gian lưu trữ.

### hostPath configuration example
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
    - mountPath: /test-pd
      name: test-volume
  volumes:
  - name: test-volume
    hostPath:
      # directory location on host
      path: /data
      # this field is optional
      type: Directory
```
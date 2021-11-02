### What ?
- Lọai Volume này sẽ gắn một file hoặc thư mục trên node vào pod.

### Trường hợp sử dụng (When/Why):
- sử dụng môi trường phát triển và thử nghiệm.
- Cần truy cập file và thư mục của host (không an toàn).

### Tính năng
- Một hostPath Volume sẽ gắn một file hoặc thư mục ngay trên node vào pod của bạn để làm không gian lưu trữ.

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
### What ?
- Như chúng ta đã biết thì khi nói về vùng lưu trữ (storage volume) trong Kubernetes thì K8S hiện hỗ trợ đến hơn 20 loại Volume Storage khác nhau: emptyDir, hostPath, csi, local, … phục vụ các nhu cầu hoạt động khác nhau khi thiết kế ứng dụng hệ thống. Trong bài viết này chúng ta sẽ tìm hiểu về loại Volume Storage cơ bản đầu tiên trong Kubernetes là : emptyDir.

### Một số đặc điểm của Volume emptyDir:
- Một emptyDir volume sẽ được khởi tạo với vùng lưu trữ rỗng (khởi tạo trên ổ cứng của Kubernetes Node) đi theo một Pod được khởi động trên Kubernetes Node.
- Một emptyDir volume có thể được mount với bất kì mount point nào trong các container của Pod.
- Các containers trong cùng 1 Pod có thể đọc/ghi với emptyDir Volume.
- Khi một Pod được khởi động lại hoặc bị xoá đi, thì dữ liệu trong emptyDir sẽ bị mất hết.
- Còn khi Container trong Pod bị crash (nhưng không ảnh hưởng gây đến việc xoá/khởi động lại Pod) thì dữ liệu trong volume emptyDir vẫn còn.
- Vì vậy mà emptyDir volume không dùng cho việc lưu trữ các dữ liệu mang có yêu cầu thời gian dài hạn và toàn vẹn dữ liệu như (database, dữ liệu ứng dụng, dữ liệu giám sát hệ thống,…)
- EmptyDir ngoài hỗ trợ tạo khu vực lưu trữ trên ổ cứng, còn hỗ trợ tạo khu vực lưu trữ volume trên RAM với tmpfs nữa đấy.

### Một số tình huống sử dụng của Volume emptyDir:
- Thường volume emptyDir dùng với mục đích là một thư mục chứa cache tạm thời (temporary cache).
- Là khu vực lưu trữ dữ liệu chung (shared storage) giữa các container trong cùng 1 Pod, từ đó các ứng dụng container trong cùng Pod có thể trao đổi dữ liệu với nhau qua volume chung.

### Cấu hình một emptyDir Volume
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

### ref
```
https://cuongquach.com/tim-hieu-storage-volume-emptydir-kubernetes.html
```
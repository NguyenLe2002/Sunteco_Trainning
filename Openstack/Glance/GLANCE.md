# GLANCE

## 1. Khái niệm

Glance là **Image services** của Openstack . Dịch vụ này cung cấp các virtual image cho các máy ảo để bootable và để quản lý volume snapshot. Các volume snapshot có thể sử dụng để backup hoặc làm template cho máy ảo mới.

Glance được thiết kế để có thể là dịch vụ hoạt động độc lập cho sự cần thiết các tổ chức lớn lưu trữ và quản lý các disk image ảo. Glance cung cấp RESTful API cho phép truy cập VM image metadata.

## 2. Các thành phần của Glance

Glance bao gồm các thành phần sau:

- **glance-api**: Cung cấp api cho Glance để người dùng hoặc các dịch vụ khác giao tiếp với Glance để gửi các yêu cầu truy vấn, thu thập, lưu trữ image, metadata.
- **glance-registry**: lưu trữ, xử lý và truy vấn metadata của image. Metadata của image sẽ bao gồm các thông tin như kích thước và loại của image.
- **Database**: Để lưu metadata của image, thường dùng MySQL
- **Storage repository cho image**: Có rất nhiều loại được hỗ trợ như filesystem, Object Storage, Rados, Vmware datastore, Http. Lưu ý rằng một số repo chỉ hỗ trợ read-only.
- **Dịch vụ định nghĩa metadata**: Cho phép nhà cung cấp, quản trị viên, các dịch vụ và người dùng có thể tự định nghĩa metadata tùy chọn. Metadata này có thể sử dụng cho nhiều loại tài nguyên như image, artifacts, volumes, flavor và aggregates.

## 3. Kiến trúc Glance

![img](https://camo.githubusercontent.com/f309ac76b13fea9dafa83d06cc95d2e340cfb97e8dd78c60f5b0e3a56729c4c1/687474703a2f2f692e696d6775722e636f6d2f673531793336362e706e67)

Glance có kiến trúc client-server và cung cấp REST API thông qua đó yêu cầu tới server được thực hiện.

Mọi hoạt động liên quan đến dữ liệu file đều được xử lý bằng thư viện glance_store, mà chịu trách nhiệm giao tiếp với các backend storage.

Glance hỗ trợ các backend lưu trữ(các driver) sau:

- **File system**: Glance lưu trữ các image vào hệ thống file thông thường, hỗ trợ đọc ghi file dễ dàng. Thư mục chứa image thường là /var/lib/glance/images/.
- **HTTP**: Cho phép glance sử dụng các image thông qua giao thức Http nhưng chỉ hỗ trợ chế độ đọc, không thể ghi.
- **RBD**: Lưu trữ image trong cụm Ceph thông qua RBD interface của Ceph.
- **Cinder**: Lưu trữ image dưới dạng block trên Block storage Cinder.
- **Swift**: Lưu trữ image dưới dạng object trên Object Storage Swift
- **VMware**: Lưu trữ image trên datastore của Vmware
- **S3**: Hỗ trợ lưu trữ sử dụng s3.

## 4. Các định dạng image được hỗ trợ trên Glance

Khi upload một image lên Glance ta cần xác định định dạng của image đó. Glance hỗ trợ nhiều loại định dạng disk image và định dạng container image: **Disk formart**: disk format của một image là

- **aki**: Amazon kernel image
- **ami**: Amazon machine image
- **ari**: Amazon ramdisk image
- **iso**: Định dạng lưu trữ dữ liệu cho đĩa quang ví dụ như CD-ROM
- **qcow2**: Hỗ trợ bởi QEMU
- **raw** : An unstructured disk image format; if you have a file without an extension it is possibly a raw format.
- **vdi** : Supported by VirtualBox virtual machine monitor and the QEMU emulator.
- **vhd** : The VHD disk format, a common disk format used by virtual machine monitors from VMware, Xen, Microsoft, VirtualBox, and others.
- **vhdx** : The VHDX disk format, an enhanced version of the VHD format, which supports larger disk sizes among other features.
- **vmdk** : Vmware

Container image format:

- **aki** : An Amazon kernel image.
- **ami** :An Amazon machine image.
- **ari** : An Amazon ramdisk image.
- **bare**: The image does not have a container or metadata envelope.
- **docker**: A docker container format.
- **ova** :An OVF package in a tarfile.
- **ovf** : The OVF container format.

## 5. Luồng trạng thái của image

Các image trong Glance có thể ở một trong các trạng thái sau:

- **queued**: image ở hàng chờ. Định danh cho image được bảo lưu cho image đó trong Glance Registry. Dữ liệu của image vẫn chưa được tải lên Glance và image size cho image đã được định danh này được thiết lập là 0.
- **saving**: Biểu thị rằng dữ liệu thô của image đang được tải lên glance. Nếu một image được đăng ký vào registry mà có header là x-image-meta-location thì image này sẽ không bao giờ ở trạng thái *saving*.
- **uploading**: Biểu thị là một import data-put call đã được thực hiện. Trong khi ở trạng thái này, không thể gửi môt *PUT /file* call(*PUT /file* call sẽ chuyển trạng thái của một image từ *queued* thành **saving**, và ngược lại cũng không thể tạo *PUT /stage* khi image đang ở trạng thái *saving*. Do đó một image không thể có cả 2 phương thức upload)
- **importing**: Biểu thị rằng một import call đã được thực hiện nhưng image vẫn chưa sẵn sàng.
- **active**: Biểu thị một image hoàn toàn sẵn sàng trên Glance. Điều này sảy ra khi image đã được tải lên hoặc image size được thiết lập rõ ràng bằng 0 khi tạo.
- **deactived**: Biểu thị rằng truy cập đến dữ liệu image không được phép cho bất kì user non-admin nào. Việc cấp tải hình ảnh đồng thời cấm các hoạt động như xuất hoặc nhân bản image mà liên quan đến dữ liệu của image.
- **killed**: Biểu thị rằng có lỗi sảy ra trong quá trình tải lên image và image này không thể đọc.
- **deleted**: Glance giữ lại thông tin image nhưng nó sẽ bao giờ có sẵn cho user nữa. Những image ở trạng thái này sẽ bị xóa vào một ngày nào đó sau này.
- **pending-delete**: Giống với deleted, tuy nhiên, Glance giữ lại dữ liệu của image. Image ở dạng này không thể khôi phục.

Luồng trạng thái của image:

![img](https://raw.githubusercontent.com/lamth/tailieu-Openstack/master/docs/03.Glance/img/image-status.png)

Các tác vụ làm việc với image trong Glance có thể ở một trong các trạng thái sau:

- **pending**: tác vụ đã nhận định danh trên glance nhưng chưa bắt đầu.
- **processing**: tác vụ đã được chọn bởi trình thực thi của Glance và đang được chạy bởi trình thực thi backend của glance theo loại tác vụ tương ứng.
- **success**: tác vụ đã được thực hiện thành công. Thông tin chi tiết ở trường **results**
- **failure**: một lỗi sảy ra trong quá trình thực thi. Thông tin chi tiết ở trường **message**.

## 6. Thuộc tính phổ biến của Image

Khi thêm một image vào Glace, có thể cấu hình cho image một số thuộc tính mà có thể sẽ hữu ích với người dùng image đó.

Các thuộc tính phổ biến của một image cũng được mô tả trong file **/etc/glance/schema-image.json** trong source code của Glance

Dưới đây là một số thuộc tính phổ biến của image:

- **architecture**: kiến trúc hệ điều hành (ví dụ: x86_64)
- **instance_uuid**: Siêu dữ liệu sử dụng để ghi lại máy ảo nào mà image này đang được liên kết đến(chỉ là thông tin, không tạo snapshot cho máy ảo).
- **kernel_id**: ID của image trong glance mà được sử dụng như là kernel khi booting một image AMI-style
- **ramdisk_id**: ID của image trong glance mà được sử dụng như là ramdisk khi booting image AMI-style
- **os_distro**: Tên bản phân phối của hệ điều hành.
- **os_version**: Phiên bản hệ điều hành
- **description**: Một mô tả ngắn gọn dạng humman-readable, phù hợp để hiển thị trên giao diện người dùng cho image đó.
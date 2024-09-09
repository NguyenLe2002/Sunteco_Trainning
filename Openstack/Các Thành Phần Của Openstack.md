# Các Thành Phần Của Openstack

## 1.Giới thiệu Openstack

**OpenStack**  là một nền tảng mã nguồn mở hoàn toàn miễn phí, cung cấp framework giúp xây dựng và quản lý cơ sở hạ tầng đám mây công cộng Public Cloud và đám mây riêng tư Private Cloud. OpenStack cho phép triển khai và quản lý hạ tầng như một dịch vụ, cho phép người dùng cấu hình và quản lý một lượng lớn tài nguyên tính toán, lưu trữ và mạng một cách dễ dàng và linh hoạt. 

Các tài nguyên này có thể là phần cứng vật lý hoặc máy ảo (VM – Virtual Machine) và tất cả đều được quản lý thông qua giao diện lập trình ứng dụng (API) và bảng điều khiển của OpenStack. Đặc biệt, OpenStack cho phép các tổ chức và nhà cung cấp dịch vụ triển khai tại chỗ hoặc triển khai trên đám mây để cung cấp năng lượng cho các nền tảng đám mây và các hệ thống mạng.

## 2.Các thành phần của Opensatck

![img](https://maychusaigon.vn/wp-content/uploads/2024/08/cac-thanh-phan-chinh-cua-openstack-mcsg.jpg)

 OpenStack như một hệ điều hành cloud có nhiệm vụ kiểm soát các tài nguyên tính toán(compute), lưu trữ(storage) và networking trong hệ thống lớn datacenter, tất cả đều có thể được kiểm soát qua giao diện dòng lệnh hoặc một dashboard( do project horizon cung cấp). Ở thời điểm hiện tại, OpenStack có 6 core project và 13 project tùy chọn cài đặt theo nhu cầu. 6 core project của OpenStack bao gồm: NOVA, NEUTRON, SWIFT, CINDER, KEYSTONE, GLANCE

### 2.1. NOVA

- Quản lí các máy ảo trong môi trường OpenStack, chịu trách nhiệm khởi tạo, lập lịch, ngừng hoạt động của các máy ảo theo yêu cầu.
- Starting, resizing, stopping và querying máy ảo
- Gán và remove public IP
- Attach và detach block storage
- Show instance consoles (VNC)
- Snapshot running instances
- Nova hỗ trợ nhiều hypervisor: KVM, VMware, Xen, Docker, etc.

### 2.2. NEUTRON

- Các phiên bản trước Grizzly tên là Quantum, sau đổi tên thành Neutron
- Cung cấp kết nối mạng như một dịch vụ (Network-Connectivity-as-a-Service) cho các dịch vụ khác của OpenStack, thay thế cho nova-network.
- Cung cấp API cho người dùng để họ tạo các network của riêng mình và attach vào server interfaces.
- Kiến trúc pluggable hỗ trợ các công nghệ khác nhau của các nhà cung cấp networking phổ biến.
- Ngoài ra nó cũng cung cấp thêm các dịch vụ mạng khác như: FWaaS (Firewall as a service), LBaaS (Load balancing as a servie), VPNaaS (VPN as a service),...

### 2.3. SWIFT

Cung cấp giải pháp lưu trữ và thu thập quy mô lớn dữ liệu phi cấu trúc thông qua RESTful API. Không giống như máy chủ tập tin truyền thống, giải pháp lưu trữ với Swift hoàn toàn là phân tán, lưu trữ nhiều bản sao của từng đối tượng để đạt được tính sẵn sàng cao cũng như khả năng mở rộng. Cụ thể hơn, Swift cung cấp các một số chức năng như:

- Lưu trữ và thu thập các đối tượng (các files)
- Thiết lập và chỉnh sửa metadata trên đối tượng(tags)
- Đọc, ghi các đối tượng thông qua HTTP
- etc.

### 2.4. CINDER 

- Cung cấp các khối lưu trữ bền vững (volume) để chạy các máy ảo (instances).
- Kiến trúc pluggable driver cho phép kết nối với công nghệ Storage của các hãng khác.
- Có thể attach và detach một volume từ máy ảo này gắn sang máy ảo khác, khởi tạo instance mới
- Có thể sao lưu, mở rộng các volume

### 2.5. KEYSTONE

Cung cấp dịch vụ xác thực và ủy quyền cho các dịch vụ khác của OpenStack, cung cấp danh mục của các endpoints cho tất các dịch vụ trong OpenStack. Cụ thể hơn:

- Xác thực user và vấn đề token để truy cập vào các dịch vụ
- Lưu trữ user và các tenant cho vai trò kiểm soát truy cập(cơ chế role-based access control - RBAC)
- Cung cấp catalog của các dịch vụ (và các API enpoints của chúng) trên cloud
- Tạo các policy giữa user và dịch vụ
- Mỗi chức năng của Keystone có kiến trúc pluggable backend cho phép hỗ trợ kết hợp với LDAP, PAM, SQL

### 2.6. GLANCE

Lưu trữ và truy xuất các disk images của các máy ảo của người dùng và các cloud services khác. OpenStack compute sẽ sử dụng chúng trong suốt quá trình dự phòng instances. Các tính năng chính:

- Người quản trị tạo sẵn template để user có thể tạo máy ảo nhanh chóng
- Người dùng có thể tạo máy ảo từ ổ đĩa ảo có sẵn. Glance chuyển images tới Nova để vận hành instance
- Snapshot từ các instance đang chạy có thể được lưu trữ, vì vậy máy ảo đó có thể được back up.

### 2.7. HORIZON - Dashboard Service

Cung cấp giao diện nền web cho người dùng cuối và người quản trị cloud để tương tác với các dịch vụ khác của OpenStack, ví dụ như vận hành các instance, cấp phát địa chỉ IP và kiểm soát cấu hình truy cập các dịch vụ. HORIZON viết dựa trên python django framework. Một số thông tin mà giao diện người dùng cung cấp cho người sử dụng:

- Thông tin về quota và cách sử dụng

- Volume Management: điều khiển khởi tạo, hủy kết nối tới các block storage
- Images and Snapshots: up load và điều khiển các virtual images, các virtual images được sử dụng để back up hoặc boot một instance mới

Addition:

- Flavors: định nghĩa các dịch vụ catalog yêu cầu về CPU, RAM và BOOT disk storage
- Project: cung cấp các group logic của các user
- User: quản trị các user
- System Info: Hiển thị các dịch vụ đang chạy trên cloud

### 2.8. CEILOMETER - Telemetry Service

- Giám sát và đo đạc các thông số của OpenStack, thống kê tài nguyên của người sử dụng cloud phục vụ mục đích billing, benmarking, thống kê và mở rộng hệ thống
- Đáp ứng tính năng "Pay as you go" của Cloud Computing

### 2.9. HEAT - Orchestration Service

- Triển khai các ứng dụng dựa trên các template dựng sẵn
- Template sẽ mô tả cấu hình các thành phần compute, storagevaf networking để đáp ứng yêu cầu của ứng dụng.
- Kết hợp với Ceilometer để có thể tự co dãn tài nguyên.
- Tương thích với AWS Cloud Formation APIs

## 3. Cơ Chế Hoạt Động Của Openstack

OpenStack không phải là một ứng dụng đám mây theo nghĩa truyền thống, mà là một nền tảng bao gồm nhiều thành phần riêng lẻ gọi là dự án, các thành phần này tương tác với nhau thông qua API Mỗi thành phần đều có vai trò bổ trợ, nhưng không phải tất cả các thành phần đều cần thiết để tạo ra một đám mây cơ bản. 

Các tổ chức có thể cài đặt chỉ những thành phần cần thiết để xây dựng các tính năng và chức năng cho môi trường đám mây mà họ mong muốn. Ngoài ra, OpenStack là giải pháp còn phụ thuộc vào hai công nghệ nền tảng sau:

- Hệ điều hành cơ bản: Đây là hệ điều hành như Linux đảm nhận việc xử lý các lệnh và dữ liệu được trao đổi từ OpenStack.
- Nền tảng ảo hóa: Công cụ ảo hóa quản lý các tài nguyên phần cứng ảo hóa được tách ra từ phần cứng và sử dụng bởi các dự án của OpenStack. Các ví dụ phổ biến về phần mềm ảo hóa bao gồm VMware và Citrix.

Khi hệ điều hành, nền tảng ảo hóa và các thành phần của OpenStack được triển khai và cấu hình đúng cách, các quản trị viên IT có thể cung cấp và quản lý các tài nguyên mà ứng dụng yêu cầu. Các hành động và yêu cầu được thực hiện thông qua bảng điều khiển sẽ kích hoạt một loạt các cuộc gọi API, được xác thực thông qua dịch vụ bảo mật và chuyển đến thành phần đích, nơi thực hiện các tác vụ liên quan.
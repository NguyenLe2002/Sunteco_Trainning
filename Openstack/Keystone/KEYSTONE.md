# KEYSTONE

## 1. Khái niệm

​     Keystone là 1 dịch vụ trong Openstack nó cung cấp các Identity, Token, Catalog và Policy service để sử dụng 1 cách cụ thể cho từng Project trong Openstack, Keystone gồn 2 phiên bản:

- **v2**: sử dụng UUID
- **v3**: sử dụng PKI, sử dụng một cặp key mở và đóng để xác minh chéo và xác thực. Hai tính năng chính của Keystone:

Keystone có hai chức năng chính đó là: 

- Quản lý user: Quản lý người sử dụng các dịch vụ và những quyền mà họ được phép làm
- Xác thực dịch vụ: Cung cấp 1 danh mục những dịch vụ có hiệu lực và nơi những API endpoint được đặt

### 1.1. Các dịch vụ Keystone cung cấp

- Identity: Các dịch vụ cung cấp danh tính, xác nhận chứng chỉ và dữ liệu về người sử dụng, thuê và vai trò, cũng như bất kỳ siêu dữ liệu liên quan.
- Token: Xác nhận và quản lý các tokens được sử dụng để xác thực yêu cầu khi thông tin của người dùng đã được xác minh.
- Catalog: Cung cấp endpoint registry sử dụng để phát hiện endpoint.
- Policy: Cung cấp engine để ủy quyền dựa trên rule và kết nối với giao diện quản lý rule.

## 2. Cấu trúc trong Keystone

##### **2.1. Project**

- Khái niệm chỉ sự gom gộp, cô lập các nguồn tài nguyên (server, images, etc.)
- Các user được gắn role và truy cập sử dụng tài nguyên trong project
- role để quy định tài nguyên được phép truy cập trong project (khái niệm role assignment)
- Bản thân projects không sở hữu users hay groups mà users và groups được cấp quyền truy cập tới project sử dụng cơ chế gán role.

**2.2. Domain**

- Domain là tập hợp bao gồm các user, group, project
- Phân chia tài nguyên vào các "kho chứa" để sử dụng độc lập với các domain khác
- Mỗi domain có thể coi là sự phân chia về mặt logic giữa các tổ chức, doanh nghiệp trên cloud

**2.3. Users và User Groups**

- User: người dùng sử dụng nguyên trong project, domain được phân bổ
- Group: tập hợp các user , phân bổ tài nguyên
- Role: các role gán cho user và user group trên các domain và project

**2.4. Roles**

Khái niệm gắn liên với Authorization (ủy quyền), giới hạn các thao tác vận hành hệ thống và nguồn tài nguyên mà user được phép. Role được gán cho user và nó được gán cho user đó trên một project cụ thể. ("assigned to" user, "assigned on" project)

**2.5. Token**

Token được sử dụng để xác thực tài khoản người dùng và ủy quyền cho người dùng khi truy cập tài nguyên (thực hiện các API call).
Token bao gồm:

- ID: định danh duy nhất của token trên DB
- payload: là dữ liệu về người dùng (user được truy cập trên project nào, danh mục các dịch vụ sẵn sàng để truy cập cùng với endpoints truy cập các dịch vụ đó), thời gian khởi tạo, thời gian hết hạn, etc.

**2.6. Catalog**

Là danh mục các dịch vụ để người dùng tìm kiếm và truy cập. Catalog chỉ ra các endpoints truy cập dịch vụ, loại dịch vụ mà người dùng truy cập cùng với tên tương ứng, etc. Từ đó người dùng có thể request khởi tạo VM và lưu trữ object.

**2.7. Services**

Là một dịch khác như Nova, Glance, Swift có cung cấp các endpoint cho phép người dùng truy cập, sử dụng tài nguyên

## 3. Cách thức hoạt động của Keystone



![img](https://camo.githubusercontent.com/b11d6bf37c84fb9a2016d545eed1bd7b05fd7576ee05dac9277325d141e47b36/687474703a2f2f692e696d6775722e636f6d2f75447a504c6e612e706e67)

**1**: User gửi thông tin đến Keystone (Username và Password)

**2**: Keystone kiểm tra thông tin. Nếu đúng, nó sẽ gửi về user 1 token.

**3**: User gửi token và yêu cầu đến Nova.

**4**: Nova gửi token đến Keystone để kiểm tra token này có đúng không? có những quyền hạn gì. Keystone sẽ trả lời lại cho Nova.

**5**: Nếu token có quyền, Nova gửi token và yêu cầu image đến Glance.

**6**: Glance gửi token về Keystone để xác thực và kiểm tra xem user này có quyền với file image này không. Keystone sẽ trả lời đến Glance.

**7**: Nova gửi token, và yêu cầu về mạng đến Neutron.

**8**: Neutron gửi token đến Keystone. Keystone sẽ trả lời cho Neutron là user này có được phép hay không.

**9**: Neutron trả lời cho Nova..

**10**: Nova trả lời cho người dùng.
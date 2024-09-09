

# Quá Trình khởi Động Hệ Điều Hành Linux

**I. Toàn bộ quá trình khởi động:**

![Quá trình khởi động Linux](https://blogd.net/linux/qua-trinh-khoi-dong-he-dieu-hanh-linux/img/qua-trinh-khoi-dong-linux.png)

**Quá trình này diễn ra như sau:**

| Bước 1 | BIOS                                |
| ------ | ----------------------------------- |
| Bước 2 | Master Boot Record (MBR).           |
| Bước 3 | Boot loader.                        |
| Bước 4 | Linux kernel được nạp và khỏi chạy. |
| Bước 5 | Các script trong INITRD thực thi.   |
| Bước 6 | Chương trình init được thực thi.    |
| Bước 7 | Đăng nhập giao diện đồ hoạ.         |
| Bước 8 | Đăng nhập thành công vào hệ thống.  |

**Bước 1: BIOS**

BIOS là chương trình chạy đầu tiên khi nhấn nút nguồn hoặc nút reset trên máy tính của bạn.

BIOS thực hiện một công việc gọi là POST ( Power-on Self-test) kiểm tra các thông số của các phần cứng của máy tính. Ngoài ra , BIOS cho phép thay đổi các thiết lập, cấu hình của nó.

BIOS được lưu trữ trên ROM của bo mạch chủ.

Quá trình POST kết thúc thành công, BIOS sẽ tìm kiếm và khởi chạy một hệ điều hành được chứa trong các thiết bị lưu trữ như ổ cứng…

Hệ điều hành Linux được cài trên ổ cứng thì BIOS sẽ tìm đến MBR (Master Boot Record)

![Quá trình boot linux giai đoạn BIOS](https://blogd.net/linux/qua-trinh-khoi-dong-he-dieu-hanh-linux/img/qua-trinh-boot-linux-giai-doan-BIOS.png)

**Bước 2: Master Boot Record (MBR)**

Sau khi BIOS xác định được thiết bị lưu trữ thì BIOS sẽ đọc trong MBR hoặc phân vùng EFI của thiết bị này để nạp vào bộ nhớ một chương trình. Chương trình này sẽ định vị và khởi động boot loader – đây là chương trình chịu trách nhiệm cho việc tìm và nạp nhân của hệ điều hành.

Đến giai đoạn này, máy tính sẽ không truy cập vào phương tiện lưu trữ nào. Thông tin về ngày tháng, thời gian và các thiết bị ngoại vi quan trọng nhất được nạp từ CMOS.

![Quá trinh boot linux giai đoạn Master Boot Record](https://blogd.net/linux/qua-trinh-khoi-dong-he-dieu-hanh-linux/img/qua-trinh-boot-linux-giai-doan-Master-Boot-Record.png)

**Bước 3: Boot loader**

Linux có 2 boot loader phổ biến trên Linux là GRUB và ISOLINUX.

Chương trình này có mục đích: cho phép lựa chọn hệ điều hành có trên máy tính để khởi động, sau đó chúng sẽ nạp kernel của hệ điều hành đó vào bộ nhớ và chuyển quyền điều khiển máy tính cho kernel này.

![File cấu hình grub.cfg](https://blogd.net/linux/qua-trinh-khoi-dong-he-dieu-hanh-linux/img/file-cau-hinh-grub.cfg.png)

Hệ thống sử dụng phương pháp BIOS/MBR, bộ tải khởi động nằm ở khu vực đầu tiên của đĩa cứng. Kích thước của MBR chỉ là 512 byte. Trong giai đoạn này, bộ nạp khởi động kiểm tra bảng phân vùng và tìm một phân vùng có khả năng khởi động. Nó tìm thấy một phân vùng có khả năng khởi động, nó sẽ tìm kiếm bộ tải khởi động giai đoạn thứ hai.

Với hệ thống sử dụng phương pháp EFI / UEFI, phần mềm UEFI đọc dữ liệu trình quản lý khởi động để xác định ứng dụng UEFI nào sẽ được khởi chạy và từ nơi nào.

Trình khởi động giai đoạn 2 nằm trong /boot. Màng hình hiển thị cho chúng ta chọn hệ điều hành để khởi động. Tiếp đến bộ nạp khởi động sẽ tải hệ điều hành vào RAM và chuyển quyền kiểm soát cho RAM.

![Quá trình Boot Linux giai đoạn Boot Loader Chi tiết](https://blogd.net/linux/qua-trinh-khoi-dong-he-dieu-hanh-linux/img/qua-trinh-boot-linux-giai-doan-Boot-Loader-chi-tiet.png)

**Bước 4: Linux kernel được nạp và khởi chạy**

Boot loader nạp một phiên bản dạng nén của Linux kernel. Nó tự giải nén và tự cài đặt lên bộ nhớ hệ thống nơi mà nó sẽ ở đó cho tới khi tắt máy.

![Quá trình boot Linux kernel vào file sbin](https://blogd.net/linux/qua-trinh-khoi-dong-he-dieu-hanh-linux/img/qua-trinh-boot-linux-kernel-vao-file-sbin.png)

Sau khi chọn kernel trong file cấu hình của boot loader, hệ thống sẽ tự động nạp chương trình init trong thư mục /sbin.

![Quá trình Linux kernel](https://blogd.net/linux/qua-trinh-khoi-dong-he-dieu-hanh-linux/img/qua-trinh-boot-linux-kernel.png)

**Bước 5: Các script trong INITRD thực thi**

INITRD cung cấp một giải pháp: là một tập các chương trình sẽ được thực thi khi kernel vừa mới được khởi chạy. Các chương trình này sẽ dò quét phần cứng của hệ thống và xác định xem kernel cần được hỗ trợ thêm những gì để có thể quản lý được các phần cứng đó. Chương trình INITRD có thể nạp thêm vào kernel các module bổ trợ. Khi chương trình INITRD kết thúc thì quá trình khởi động Linux sẽ tiếp diễn.

Hệ thống hình ảnh tập tin initramfs chứa các chương trình và tệp nhị phân thực hiện các hành động cần thiết để gắn kết hệ thống tệp gốc thích hợp, cung cấp chức năng hạt nhân cho hệ thống tệp và trình điều khiển thiết bị cần thiết cho bộ điều khiển lưu trữ hàng loạt với cơ sở được gọi là udev (cho thiết bị người dùng). Thiết bị nào có mặt, định vị các trình điều khiển thiết bị mà chúng cần để hoạt động chính xác và tải chúng. Sau khi hệ thống tập tin gốc đã được tìm thấy, nó được kiểm tra lỗi và được gắn kết.

![Quá trình boot Linux giai đoạn đĩa ram Initial](https://blogd.net/linux/qua-trinh-khoi-dong-he-dieu-hanh-linux/img/qua-trinh-boot-linux-giai-doan-dia-ram-Initial.png)

Chúng ta có thể thấy tệp kernel và initramfs trong thư mục /boot.

![File initramfs](https://blogd.net/linux/qua-trinh-khoi-dong-he-dieu-hanh-linux/img/file-initramfs.png)

**Bước 6: Chương trình init thực thi**

Kernel được khởi chạy xong, nó sẽ gọi duy nhất một chương trình tên là init.

Tiến trình này có ID = 1 Init là cha của tất cả các tiến trình khác mà có trên hệ thống Linux.

Init xử lý việc gắn và xoay vòng vào hệ thống tập tin gốc thực sự cuối cùng.

Trong hệ điều hành Linux có 2 loại init phổ biến:

- Loại thứ nhất dựa trên Unix System V
- Loại thứ hai dựa trên Systemd

**Unix System V**

File cấu hình run level /etc/inittab:

- Runlevel 0: Level Shutdown hệ thống.
- Runlevel 1: Level chỉ dùng cho 1 người dùng để sửa lỗi hệ thống tập tin.
- Runlevel 2: Không sử dụng.
- Runlevel 3: Level dùng cho nhiều người dùng nhưng chỉ giao tiếp dạng text (không có giao diện).
- Runlevel 4: Không sử dụng.
- Runlevel 5: Level dùng cho nhiều người dùng và được cung cấp giao diện đồ họa.
- Runlevel 6: Level Reboot hệ thống.

Sau khi xác định run level. Chương trình /sbin/init sẽ thực thi các file statup script được đặt trong các thư mục con của thư mục /etc/rc.d.

![File startup script](https://blogd.net/linux/qua-trinh-khoi-dong-he-dieu-hanh-linux/img/file-startup-script.png)

Script sử dụng run level từ 0 đến 6 để xác định thư mục chứa file script chỉ định cho từng level như: /etc/rc.d/rc0.d đến /etc/rc.d/rc6.d.

Trong file script theo từng level. Các tên tập tin bắt đầu bằng từ khóa "S" có nghĩa là tập tin này sẽ được thực thi lúc khởi động hệ thống. Nếu tập tin bắt đầu bằng từ khóa "K" nghĩa là tập tin đó được thực thi khi hệ thống shutdown. Số theo sau từ khóa "S" và "K" để chỉ định trình tự khởi động các script, kế tiếp là tên file script cho từng dịch vụ.

Ví dụ 1 số file script theo từng run level:

![File script theo level](https://blogd.net/linux/qua-trinh-khoi-dong-he-dieu-hanh-linux/img/file-script-theo-lelvel.png)

**Systemd**

Đối với các bản Linux hiện đại như CentOS 7, RHEL 7 gần đây thì init và runlevel được thay thế bởi systemd và cũng thực hiện nhiệm vụ tương ứng. Systemd cũng giống như init là tiến trình chạy đầu tiên trên hệ thống với ID = 1.

![boot-systemd](https://blogd.net/linux/qua-trinh-khoi-dong-he-dieu-hanh-linux/img/boot-systemd.png)

Systemd đọc tệp liên kết bởi /etc/systemd/system/default.target để xác định đích hệ thống mặt định.

Tệp mục tiêu trong hệ thống xác định các dịch vụ mà systemd bắt đầu.

Systemd sẽ bắt đầu mọi thứ trong /etc/systemd/system/basic.target trước khi bắt đầu multi-user service.

![File systemd](https://blogd.net/linux/qua-trinh-khoi-dong-he-dieu-hanh-linux/img/file-systemd.png)

Systemd sử dụng mục tiêu thay vì runlevel. Systemd có hai mục tiêu chính: multi-user.target và graphical.target tương ứng với runlevel 3 và runlevel 5.

Để xem các mục tiêu mặc định hiện tại chúng ta chạy lệnh: `systemctl get-default`

Để đặt mục tiêu mặt định chúng ta chạy lênh: `systemctl set-default TARGET.target`

Systemd quản lí bắt đầu/dừng/tải lại cấu hình/kiểm tra… dịch vụ từ lúc khởi động cho đến lúc tắt máy.

Systemctl là ứng dụng kiểm soát các dịch vụ quản lí hệ thống.

Ví dụ mở dịch vụ httpd bằng systemd:

Chúng ta dùng để mở httpd: `systemctl start httpd`

Sau đó kiểm tra httpd hoạt động chưa dùng: `systemctl status httpd`

![File kích hoạt http](https://blogd.net/linux/qua-trinh-khoi-dong-he-dieu-hanh-linux/img/file-kich-hoat-httpd.png)

**Bước 7: Đăng nhập với giao diện đồ hoạ**

**Đăng nhập text mode**

Gần cuối quá trình khởi động, init sẽ bắt đầu một chế độ đăng nhập text mode. Nhập tên người dùng và mật khẩu của bạn để đăng nhập và xuất hiện các dấu nhắc lệnh shell.

![Quá trình boot Linux giai đoạn Text Mode Login](https://blogd.net/linux/qua-trinh-khoi-dong-he-dieu-hanh-linux/img/qua-trinh-boot-linux-giai-doan-Text-Mode-Login.png)

Subsystem cuối cùng được init khởi động lên là X Window, là một hệ thống giao diện đồ họa người dùng của Linux.

Cách truy cập các terminal qua phím ALT

- Các terminal chạy các lệnh sell có thể được truy cập bằng ATL + một phím chức năng.
- Trong môi trường đồ họa, việc chuyển sang bàn điều khiển văn bản yêu cầu nhấn CTRL-ALT + phím chức năng thích hợp (với F7 hoặc F1 dẫn đến GUI)

**Bước 8: Đăng nhập thành công vào hệ thống**

Shell lệnh mặc định là bash (GNU Bourne Again Shell), nhưng có một số shell lệnh nâng cao khác có sẵn. Nó đã sẵn sàng chấp nhận các lệnh, bạn gõ lệnh và nhấn Enter ,lệnh được thực hiện.
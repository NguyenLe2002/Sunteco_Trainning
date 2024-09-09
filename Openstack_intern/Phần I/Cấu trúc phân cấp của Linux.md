Cấu trúc thư mục được thiết kế để duy trì hệ thống tệp phân cấp trong Linux

Linux được xây dựng trên UNIX nên nó có hệ thống phân cấp tập tin tương tự như UNIX. Chúng ta hãy xem cấu trúc thư mục của Linux:

- **Tệp chung**:     Bao gồm dữ liệu nhị phân hoặc ASCII được gọi là “tệp chung”. Các tệp thông     thường, bao gồm tài liệu, ảnh, tệp âm thanh và video, v.v., đều được đưa     vào đây.
- **Tệp thư mục**:     Vì các thư mục được sử dụng để lưu trữ các tệp và thư mục bổ sung nên     chúng cũng được coi là tệp trong Linux.
- **Tệp thiết bị**:     Trong hệ điều hành giống với Windows, các thiết bị như CD-ROM và ổ đĩa cứng     được biểu thị bằng các ký tự ổ đĩa chẳng hạn như F: G: H. Tuy nhiên, trong     hệ thống Linux, các widget được biểu thị bằng các tập tin. Thư mục /dev chứa     chúng.

Hệ điều hành Linux/Unix lưu trữ các tệp theo bố cục dạng cây bắt đầu bằng thư mục gốc

![img](file:///C:/Users/nguye/AppData/Local/Temp/msohtmlclip1/01/clip_image002.jpg)

**/ – Thư mục gốc**

Trong Linux, thư mục gốc là thư mục cấp cao nhất lưu trữ tất cả các thư mục như tài liệu, nhạc và nội dung tải xuống. Thư mục chính gốc (/root) và thư mục gốc (/) phải khác biệt.

**/bin – Tệp nhị phân**

Thư mục /dev chứa tất cả các tệp nhị phân thực thi mà hệ thống yêu cầu để chạy đúng cách. Hầu hết các ứng dụng trong hệ thống này đều ở định dạng nhị phân và có sẵn cho tất cả người dùng hệ điều hành Linux.

**/dev – Tệp thiết bị**

Thư mục /dev chứa tất cả các tệp đặc biệt đại diện cho các thiết bị phần cứng như ổ cứng, bộ điều hợp mạng và máy in. Bạn có thể tìm thấy các tệp ảo đại diện cho các bộ phận phần cứng được liên kết như chuột, bàn phím, thiết bị lưu trữ, v.v., trong thư mục /dev.

**/etc – Tệp cấu hình**

Thư mục /etc chứa các tệp cấu hình hệ thống như tệp cấu hình toàn hệ thống, cài đặt mạng và tệp cấu hình dành riêng cho ứng dụng. Các tệp cấu hình toàn hệ thống có sẵn trong thư mục /etc/.

**/usr – Dữ liệu chương trình và nhị phân người dùng**

Thư mục /usr lưu trữ các chương trình người dùng và các tập tin liên quan của hệ thống. Hầu hết các tệp thực thi, thư viện và mã nguồn của chương trình hệ thống đều nằm dưới “/usr”. Do đó, hầu hết các tệp được bao gồm trong đó đều ở dạng chỉ đọc (đối với người dùng thông thường).

**/home – Dữ liệu cá nhân của người dùng**

Thư mục /home chứa các thư mục chính của tất cả người dùng cá nhân. Mỗi người dùng trên hệ thống có thể phân biệt dữ liệu của họ với dữ liệu của người dùng khác bằng cách sử dụng thư mục chính.

**/lib – Thư viện dùng chung**

Thư mục /lib chứa tất cả các tệp thư viện dùng chung được hệ thống và các ứng dụng khác sử dụng. Nó có các thư viện dành cho các tệp nhị phân thiết yếu trong thư mục /bin và /sbin trong thư mục /lib. Thư mục /usr/lib chứa các thư viện mà các tệp nhị phân trong thư mục /usr/bin yêu cầu.

**/sbin – Hệ thống nhị phân**

Thư mục /sbin có các tệp nhị phân hệ thống được quản trị viên hệ thống sử dụng. Nó bao gồm các tệp nhị phân cần thiết thường được tạo ra để người dùng root sử dụng để quản trị hệ thống.

**/tmp – Tệp tạm thời**

Thư mục /tmp lưu trữ tất cả các tệp tạm thời mà ứng dụng và hệ thống tạo ra. Bạn có thể xóa tmpwatch bất cứ lúc nào hệ thống của bạn được khởi động lại. Một số hệ thống Linux thường xuyên hủy các tệp cũ, vì vậy hãy giữ mọi thứ quan trọng ở đây.

**/var – Tệp dữ liệu biến**

Thư mục /var lưu trữ tất cả các dữ liệu có thể thay đổi như email, tệp nhật ký và dữ liệu ứng dụng khác. Quản trị viên hệ thống có thể tìm kiếm dữ liệu liên quan đến hoạt động của hệ thống của họ tại đây vì các tệp được lưu giữ ở đây KHÔNG tự động bị xóa.

**/boot – Tệp khởi động**

Thư mục /boot chứa tất cả các tệp mà bộ tải khởi động hệ thống sử dụng để khởi động hệ điều hành Linux. Cùng với kernel, nó cũng lưu hệ thống tập tin RAM ban đầu hoặc initramfs.

**/proc – Tệp tiến trình và hạt nhân**

Thư mục /proc chứa thông tin về các tiến trình hiện đang chạy và phần cứng hệ thống. Khi khởi động, hệ thống sẽ tạo một hệ thống tệp tạm thời và xóa nó khi người dùng tắt nó.

**/opt – Phần mềm tùy chọn**

Thư mục /opt lưu trữ phần mềm bổ trợ tùy chọn mà hệ thống không yêu cầu. Để tất cả người dùng có thể vận hành phần mềm, thông thường phải duy trì mã nguồn trong opt và liên kết tệp nhị phân trong thư mục /bin.

**/root – Thư mục chính của root**

/root là thư mục chính dành cho người dùng root trong hệ thống của bạn. Nó có sẵn tại /root thay vì /home/root. Điều này không giống với/hoặc thư mục gốc của hệ thống.

**/media – Điểm gắn kết cho phương tiện di động**

/media gắn kết các thiết bị đa phương tiện di động như ổ USB và CD. Ví dụ: hệ thống tạo một thư mục trong thư mục /media khi bạn đưa đĩa CD vào hệ thống Linux.

**/mnt – Thư mục gắn kết**

Thư mục /mnt được sử dụng làm điểm gắn kết tạm thời cho các hệ thống tập tin. Nó tương tự như thư mục /media, nhưng quản trị viên hệ thống sử dụng mnt để gắn kết các hệ thống tập tin thay vì tự động gắn phương tiện di động một cách rõ ràng.

**/sys – Thông tin hệ thống**

Thư mục /sys lưu trữ tất cả thông tin về phần cứng và thiết bị hệ thống trong Linux.

**/srv – Dữ liệu dịch vụ**

Thư mục /srv lưu trữ tất cả dữ liệu quan trọng cho các dịch vụ mà hệ thống lưu trữ. Ví dụ: các tệp của trang web của bạn phải nằm trong thư mục /srv nếu bạn sử dụng máy chủ HTTP Apache cho trang web.

**/run – Hệ thống tệp tạm thời**

Thư mục /run có tất cả dữ liệu thời gian chạy như các tiến trình hệ thống và thông tin dịch vụ. Khi bắt đầu quá trình khởi động, các tệp trong thư mục /run phải bị xóa (hoặc loại bỏ hoặc giảm bớt, nếu thích hợp).

 
# Tìm hiểu về Cloud Computing

## 1. Cloud Computing

![cloud computing là gì](https://blog.hostvn.net/wp-content/uploads/2021/11/cloud-computing.jpeg)

**Cloud Computing** là mô hình cung cấp các dịch vụ điện toán thông qua internet. Là một trong những xu hướng công nghệ làm thay đổi cách thức chúng ta lưu trữ và truy cập dữ liệu, ứng dụng và các dịch vụ trực tuyến, thay vì phải đầu tư xây dựng và quản lý các máy chủ vật lý và hạ tầng riêng (on-premise)

### 1.1. Tổng quan về Cloud Computing

**Cloud Computing** về cơ bản nó có nhiệm vụ tổng hợp tất cả các tài nguyên ở trong một hoặc nhiều trung tâm dữ liệu (Datacenter) nhằm tạo thành một khối tài nguyên được quản lý thống nhất và phân phối tập trung. Giải pháp Cloud Computing cho phép cấp phát nhanh chóng những tài nguyên trên hệ thống thông qua Software Defined Networking (SDN) và ảo hóa (VM) các thành phần của phần cứng máy chủ như (CPU, Ram, Storage, Network) một cách dễ dàng mà không cần sự can thiệp từ đội ngũ kỹ thuật. Giải pháp Cloud giúp doanh nghiệp giải quyết các vấn đề như tối ưu chi phí hạ tầng, sử dụng triệt để tài nguyên dư thừa một cách hiệu quả, tăng cường khả năng kiểm soát vấn đề bảo mật an toàn, mở rộng hệ thống linh hoạt và tiết kiệm hơn.

Đa số các giải pháp Cloud Computing phổ biến thường được phát triển độc quyền bởi các tập đoàn phần mềm lớn trên thế giới như Amazon, Microsoft, Google, VMware, IBM và Nutanix, Alibaba, Virtuozzo hoặc các giải pháp Cloud cộng đồng được phát triển dựa trên mã nguồn mở như Redhat và Openstack, Proxmox…

### 1.2. Tổng quan về công nghệ ảo hóa

Ảo hóa (Virtualizations) được hiểu đơn giản là việc tạo ra các máy chủ và các thiết bị lưu trữ ảo. Qua công nghệ ảo hóa, người dùng có thể sử dụng nhiều máy cùng một lúc. Ngoài ra, bạn cũng có thể chia sẻ một phiên bản tài nguyên hoặc ứng dụng vật lý cho nhiều người dùng.

 Nền tảng ảo hóa đám mây cho phép bạn có thể quản lý khối lượng công việc bằng cách chuyển đổi từ máy tính truyền thống thành nền tảng hiện đại hơn, có khả năng mở rộng và hiệu quả hơn, đồng thời tiết kiệm hơn cho bạn.

 Khái niệm ảo hóa trong điện toán đám mây đã tích hợp các tính năng cơ bản của điện toán một cách nhanh chóng. Một ưu điểm quan trọng của ảo hóa là cho phép chia sẻ các ứng dụng tới nhiều người dùng, tổ chức khác nhau.

 Điện toán đám mây còn được nhiều người biết đến thông qua cách cung cấp dịch vụ, ứng dụng hỗ trợ môi trường ảo hóa. Môi trường này có thể là môi trường công cộng hoặc môi trường riêng tư. Với sự hỗ trợ của ảo hóa, bạn có thể tối đa hóa các tài nguyên và giảm bớt các hệ thống vật lý đang cần.

##### Các loại ảo hóa trong Điện toán Đám mây

- Hệ điều hành ảo hóa (Operating System Virtualization): Bên trong hệ điều hành ảo hóa, các phần mềm ảo sẽ được cài đặt sẵn trong hệ điều hành của máy chủ (Host), thay vì cài đặt trực tiếp trong các hệ thống phần cứng. Ở đây, các phần mềm được chứa trong phần cứng, cho phép nhiều ứng dụng khác nhau có thể hoạt động.
-  Phần cứng ảo hóa (Hardware Virtualization):Phần cứng ảo hóa sẽ mang lại tính linh hoạt cao hơn khi sử dụng máy chủ ảo, thay vì các máy tính vật lý. Bên trong các phần cứng ảo hóa, phần mềm máy ảo được cài đặt trên hệ thống phần cứng. Ngoài ra, các phần cứng ảo hóa này có chứa một siêu giám sát, được dùng để điều khiển và quản lý quy trình, bộ nhớ cũng như các nguồn tài nguyên phần cứng khác. Sau khi hoàn thành quá trình ảo hóa phần cứng, người dùng có thể cài đặt hệ điều hành bên trong nó và với nền tảng này, các ứng dụng khác có thể được sử dụng bình thường.
-  Máy chủ ảo hóa (Server Virtualization): Với máy chủ ảo hóa, các phần mềm được cài đặt trực tiếp trên các hệ thống máy chủ và được sử dụng cho một máy chủ vật lý duy nhất. Máy chủ vật lý này có thể chia thành nhiều máy chủ ảo khác nhau để phù hợp với nhu cầu sử dụng và cân bằng tải sao cho phù hợp. Với sự hỗ trợ của các phần mềm, các nhà quản trị có thể chia một máy chủ vật lý tành nhiều máy chủ khác nhau.
-  Không gian lưu trữ ảo hóa (Storage Virtualization): Không gian lưu trữ ảo hóa là tổng hợp các không gian lưu trữ vật lý (Physical Storage) từ nhiều thiết bị lưu trữ mạng vào chỉ một thiết bị lưu trữ (Điều này nhằm mục đích để chúng trông giống như một thiết bị lưu trữ duy nhất). Không gian ảo hóa này được tạo thành bởi sự trợ giúp của các phần mềm ứng dụng và chúng được hoàn thiện để phục vụ cho quá trình sao lưu và phục hồi. Storage Virtualization chia sẻ các không gian lưu trữ vật lý từ nhiều thiết bị lưu trữ khác nhau.

## 2. Các loại hình dịch vụ Cloud Computing phổ biến

![Dịch vụ Cloud Computing](https://blog.hostvn.net/wp-content/uploads/2021/11/cloud-computing-type.jpeg)

- **Software as a Service** (SaaS) là hình thức cung cấp dịch vụ điện toán đám mây phổ biến có tốc độ phát triển nhanh nhất hiện nay. Khách hàng có thể truy cập các ứng dụng phần mềm được lưu trữ trên hệ thống Cloud bằng trình duyệt, thay vì các ứng dụng truyền thống được lưu trữ trên máy tính hoặc máy chủ của riêng doanh nghiệp. Đơn vị phát triển ứng dụng phần mềm sẽ chịu trách nhiệm kiểm soát và duy trì máy chủ Cloud chứa ứng dụng của họ, bao gồm các bản cập nhật và cài đặt phần mềm. Bạn, với tư cách là người dùng, có quyền kiểm soát hạn chế tính năng đối với ứng dụng và cài đặt cấu hình.
- **Infrastructure as a Service** (IaaS) là các đơn vị chuyên cho thuê dịch vụ hạ tầng máy chủ điện toán đám mây phục vụ cho nhu cầu tính toán và lưu trữ dữ liệu, network. Nhà cung cấp dịch vụ IaaS sẽ chịu trách nhiệm duy trì hoạt động của phần cứng máy chủ vật lý trên Datacenter bao gồm CPU, Memory, Storage và Network, Energy.
- **Platform as a Service** (PaaS) có thể hiểu là sự giao nhau của cả SaaS và IaaS. Về cơ bản, bạn sẽ thuê phần cứng, hệ điều hành, dung lượng lưu trữ và mạng do IaaS cung cấp, kèm theo phần mềm hoặc ứng dụng của SaaS mà bạn có nhu cầu ở trên một nền tảng duy nhất. Với PaaS, cung cấp cho bạn nhiều quyền kiểm soát hơn đối với các khía cạnh kỹ thuật và khả năng tùy chỉnh cấu hình cho phù hợp với nhu cầu của bạn.

## 3. Các mô hình triển khai Cloud Computing

- **Private Cloud**: được hiểu là hệ thống máy chủ điện toán đám mây riêng, cho phép khách hàng dễ dàng thiết lập sách sách riêng và tùy chỉnh cấu hình mà không bị phụ thuộc hoặc phải tuân thủ các quy định của nhà cung cấp dịch vụ. Phần lớn doanh nghiệp lựa chọn giải pháp Private Cloud do có nhu cầu sử dụng thường xuyên với cường độ cao hoặc tính chất đặc thù do chứa nhiều tài liệu bí mật, sở hữu trí tuệ, thông tin nhận dạng cá nhân, hồ sơ y tế, dữ liệu tài chính hoặc những dữ liệu nhạy cảm khác.
- **Public Cloud**: hay còn được gọi là dịch vụ máy chủ điện toán đám mây công cộng với mục đích chia sẻ cho thuê tài nguyên tính toán & hệ thống lưu trữ dữ liệu cho tất cả mọi đối tượng có nhu cầu sử dụng hạ tầng máy chủ với mức giá phải chăng. Toàn bộ cơ sở hạ tầng máy chủ đều thuộc sở hữu của các nhà cung cấp dịch vụ Public Cloud, nên khách hàng sẽ không phải đầu tư mua và bảo trì phần cứng hàng năm.
- **Community Cloud**: được hiểu là một loại hình dịch vụ điện toán đám mây được xây dựng và đóng góp tài nguyên bởi cộng đồng người sử dụng. Về cơ bản mô hình triển khai Community Cloud phần lớn sẽ tương tự với mô hình Private Cloud; tuy nhiên sự khác biệt duy nhất là toàn bộ tài nguyên sẽ được tập hợp từ nhiều hệ thống khác nhau nhưng đều có chung thiết lập và chính sách bảo mật đồng nhất từ các đơn vị tham gia hợp tác nhằm tối ưu chi phí và tăng khả năng chia sẻ dữ liệu.
- **Hybrid Cloud**: là một hình thức kết hợp ưu điểm của cả 3 loại hình (Private Cloud, Public Cloud và Community Cloud) để bạn có thể chủ động lựa chọn điều phối sử dụng những tính năng và khía cạnh tốt nhất của từng giải pháp có thể mang lại. Mô hình Hybrid Cloud không chỉ đảm bảo các yếu tố như bảo vệ và kiểm soát các dữ liệu, tài nguyên quan trọng về mặt chiến lược mà còn đáp ứng được các tiêu chí như tính hiệu quả chi phí đầu tư và tối ưu tài nguyên sử dụng.

## 4. Đặc điểm nổi bật của Cloud Computing

- **On-demand self-service**: với khả năng tự tạo máy chủ ảo theo nhu cầu sử dụng thông qua một bảng điều khiển trực tuyến đề cập đến các loại hình dịch vụ Cloud được cung cấp bởi các nhà cung cấp điện toán đám mây cho phép cung cấp tài nguyên đám mây theo yêu cầu bất cứ khi nào chúng được người dùng khởi tạo. 
- **Broad network access**: được định nghĩa là khả năng truy cập của cơ sở hạ tầng mạng kết nối với nhiều loại thiết bị, bao gồm PC, điện thoại di động, máy tính xách tay, máy trạm và máy tính bảng, để cho phép truy cập thông suốt vào các tài nguyên máy tính trên các nền tảng đa dạng này.
- **Resource pooling**: được hiểu là toàn bộ không gian và tài nguyên hạ tầng được gộp chung để phục vụ nhiều khách hàng cùng một lúc. Tùy thuộc vào mức tiêu thụ tài nguyên của khách hàng, việc sử dụng có thể được thiết lập để cung cấp nhiều hơn hoặc ít hơn vào bất kỳ thời điểm nào.
- **Rapid elasticity or expansion**: thuộc tính co giãn và đàn hồi nhanh là một thuật ngữ quen thuộc với Cloud Computing dùng để mô tả khả năng cung cấp mở rộng hạ tầng ngay tức thì hoặc khả năng cung cấp các dịch vụ có thể mở rộng linh hoạt theo nhu cầu. Đây là một trong năm khía cạnh cơ bản nhất của điện toán đám mây.
- **Measured service**: Khả năng đo lường thống kê là một thuật ngữ mà các chuyên gia CNTT thường nhắc đến công nghệ điện toán đám mây. Đây cũng là thông số để tham chiếu đến các dịch vụ mà nhà cung cấp sử dụng để đo lường hoặc giám sát việc cung cấp dịch vụ với nhiều mục đích khác nhau, bao gồm hóa đơn thanh toán, mức độ hiệu quả sử dụng tài nguyên hoặc lập kế hoạch dự đoán tổng thể cho toàn bộ hệ thống.
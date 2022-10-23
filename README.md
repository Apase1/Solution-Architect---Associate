# Solution-Architect Associate

### 1. Điện toán là gì 
### 2. Amazon EC2
EC2 là một dịch vụ cơ bản mà những người mới khi bắt đầu tìm hiểu về AWS sẽ được tiếp cận về cơ bản dịch vụ này cho phép chúng ta tạo ra một máy chủ ảo và sử dụng nó để triển khai các ứng dụng , liên kết những service khác với nhau v.v tùy theo mục đích người sử dụng nó mà có mỗi nhu cầu khác nhau về cấu hình một máy chủ ảo.

Có 4 sự lựa chọn với các cơ chế tính phí và ưu đãi khác nhau dành cho người sử dụng .
+ On-Demand Instances
+ Reserved Instances
+ Scheduled Instances
+ Spot Instances
+ On-Demand Capacity Reservations

Với lựa chọn số 1: On-Demand. chúng ta có thể tạo máy chủ bất cứ lúc nào chúng ta cần sài , cho các công việc yêu cầu ngắn hạn như testing , chạy back-end server, front-end server. Phí sẽ được tính dựa theo thời gian bạn sài là bao nhiêu theo từng giây. khi bạn terminate thì phí sẽ không tính nữa

Với lựa chọn số 2: Reserved-Instances, Option này cho bạn khả năng giảm giá cho cấu hình của 1 máy chủ đã định sẵn lên tới 75% trong thời hạn từ 1 đến 3 năm. Và nó có 3 sự lựa chọn thanh toán , lựa chọn 1 thanh toán tất cả và không có thêm khoản phí nào phát sinh và bạn sẽ hưởng ưu đãi ở mức cao nhất, lựa chọn 2 là trả trước nhỏ hơn so với lựa chọn 1 , và bạn sẽ được hưởng ưu đãi tương ứng với số giờ bạn sài trong thời hạn đã định , lựa chọn 3 là  thanh toán sau

Với lựa chọn số 4: Spot Instances, AWS có những máy chủ không có người sử dụng và đang để trống , để tránh lãng phí AWS cho thuê lại chúng với giá rất rẻ khi ngang cấu hình so với lựa chọn 1 cho những người dùng cần sài, tuy nhiên vì như thế cho nên nếu có những người sử dụng khác có nhu cầu sài máy chủ đó , AWS sẽ thông báo thu hồi lại máy chủ bạn đang thuê theo hình thức này trước 2 phút để bạn chuẩn bị các thao tác lưu trữ v.v.

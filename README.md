# Solution-Architect Associate

### 1. Điện toán là gì 
### 2. Amazon EC2
EC2 là một dịch vụ cơ bản mà những người mới khi bắt đầu tìm hiểu về AWS sẽ được tiếp cận về cơ bản dịch vụ này cho phép chúng ta tạo ra một máy chủ ảo và sử dụng nó để triển khai các ứng dụng , liên kết những service khác với nhau v.v tùy theo mục đích người sử dụng nó mà có mỗi nhu cầu khác nhau về cấu hình một máy chủ ảo.

Có 5 sự lựa chọn với các cơ chế tính phí và ưu đãi khác nhau dành cho người sử dụng .
+ On-Demand Instances
+ Reserved Instances
+ Scheduled Instances
+ Spot Instances
+ On-Demand Capacity Reservations

Với lựa chọn số 1: On-Demand. chúng ta có thể tạo máy chủ bất cứ lúc nào chúng ta cần sài , cho các công việc yêu cầu ngắn hạn như testing , chạy back-end server, front-end server. Phí sẽ được tính dựa theo thời gian bạn sài là bao nhiêu theo từng giây. khi bạn terminate thì phí sẽ không tính nữa

Với lựa chọn số 2: Reserved-Instances, Option này cho bạn khả năng giảm giá cho cấu hình của 1 máy chủ đã định sẵn lên tới 75% trong thời hạn từ 1 đến 3 năm. Và nó có 3 sự lựa chọn thanh toán , lựa chọn 1 thanh toán tất cả và không có thêm khoản phí nào phát sinh và bạn sẽ hưởng ưu đãi ở mức cao nhất, lựa chọn 2 là trả trước nhỏ hơn so với lựa chọn 1 , và bạn sẽ được hưởng ưu đãi tương ứng với số giờ bạn sài trong thời hạn đã định , lựa chọn 3 là  thanh toán sau

Với lựa chọn số 3: Scheduled Instances, máy chủ sẽ được chạy trong một khung giờ nhất định ở trong ngày , tuần , tháng do bạn lựa chọn. Lựa chọn này dùng để xử lý những công việc có tính chất lặp đi lặp lại theo khung giờ nhất định . Lưu ý: kể cả khi máy chủ không bật thì bạn vẫn bị tính phí cho thời hạn duy trì nó.

Với lựa chọn số 4: Spot Instances, AWS có những máy chủ không có người sử dụng và đang để trống , để tránh lãng phí AWS cho thuê lại chúng với giá rất rẻ khi ngang cấu hình so với lựa chọn 1 cho những người dùng cần sài, tuy nhiên vì như thế cho nên nếu có những người sử dụng khác có nhu cầu sài máy chủ đó , AWS sẽ thông báo thu hồi lại máy chủ bạn đang thuê theo hình thức này trước 2 phút để bạn chuẩn bị các thao tác lưu trữ v.v.

Với lựa chọn số 5: On-Demand Capacity Reservations, giúp bạn đặt trước các cấu hình máy chủ ảo theo yêu cầu của bạn trong các trường hợp cần thiết và sẽ luôn có sẵn để bạn có thể sử dụng nó . và cũng sẽ có ưu đãi cho việc sử dụng lựa chọn này.

Dưới đây là link lab cho phần này: https://cloudacademy.com/lab/create-your-first-amazon-ec2-instance/ 

### 3. ECS
Trước khi qua ECS chúng ta cần phải tìm hiểu qua về Docker và Basics of Using Containers in Production 
- Trước khi bắt đầu docker chúng ta nên tìm hiểu cơ bản về cách sử dụng Containers
Link course: https://cloudacademy.com/course/basics-of-using-containers-in-production/microservices-1/
Có 12 yếu tố để xây dựng nên 1 microservice app
- Factor One: codebase
Với nhiều lần triển khai code. Chúng ta nên sử dụng các phần mềm như Git , github hoặc các app khác. Để dễ dàng theo dõi những thay đổi từ các đoạn mã để kịp thời xử lý trong trường hợp mã bị lỗi. Và bất kỳ hệ thống nào cũng sẽ phụ thuộc vào các phần mềm như vậy để dễ dàng cho quản lý , thay đổi.

- Factor Two: dependencies (phụ thuộc )
Nếu như đoạn code của bạn phụ thuộc vào cái gì đó để chạy đúng ví dụ như , thư viện , cơ sở dữ liệu , hoặc app khác. Nó nên được thấy rõ ràng trong đoạn code và dễ dàng thiết lập
Containers cho phép làm điều này dễ dàng bởi vì nó giống với Docker Compose , có thể xác định được tất cả dependencies của code và dễ dàng chạy nó với 1 câu lệnh trên containers
Ví dụ: Máy của bạn có dependencies ẩn và code chỉ chạy được trên máy bạn , qua máy khác không có thì code nó tèo => xong phim
- Factor Three: Config. lưu trữ các thiết lập như IP , app tương tác với hệ thống vào các biến môi trường thường không nên lưu trữ nó ở trong code mà trong các file khác như dockerfile v.v.
- Factor Four: Backing services: đối với cái services mà mã code của bạn cần tương tác, cho dù là database, dịch vụ microservice nào đó , email v.v thông qua url hoặc username , password để truy cập . Hay là đối với dịch vụ trong máy chủ vật lý , máy chủ đám mây v.v. App của bạn nên tương tác với tụi nó như nhau
- Factor Five: Build , release ,run: nên được tách biệt với nhau, Build cho team dev , release cho team devops or sysadmin.
- Factor Six: Processes
The Tewlve-Factor App khuyến khích việc chạy application dưới dạng 1 hoặc nhiều stateless processes.

Stateless process: là các process không lưu trữ những dữ liệu về trạng thái của application cũng như các kết quả của việc xử lý request hay transaction. Sau khi các request được xử lý, những dữ liệu trong memory sẽ bị xóa đi.

Stateful process: là các process lưu trữ lại dữ liệu về trạng thái hay kết quả xử lý vào trong memory.

Trong trường hợp muốn lưu lại trạng thái của application thì chúng ta sẽ phải lưu thông qua các Backing services. VD: Trong trường hợp sử dụng Sticky session trong Load balancer. Sticky session sẽ lưu dữ liệu của người dùng, request, hay transaction vào trong memory của từng server. Điều này sẽ vi phạm The Tewlve-Factor App. Thay vào đó chúng ta có thể sử dụng Redis hay Memcached như một Backing service để làm nhiệm vụ lưu trữ lại dữ liệu.

Sử dụng stateless process sẽ mang lại những lợi ích như:

Dễ dàng deploy, thay đổi config, restart mà không sợ mất dữ liệu vì dữ liệu được lưu ở Backing services chứ không ở memory.
Các stateless process có thể thực thi hoàn toàn độc lập do đó dễ dàng scale bằng cách tăng số lượng process.
- Factor Seven: Port binding: Một service có thể được access thông qua 1 port cố định
- Factor eight: Concurrency: Một app nên được chia tách thành nhiều process nhỏ để tăng concurrency
- Factor nine: Disposability: Process của web app nên sống nhanh, chết vội, để có thể dễ dàng chạy/kill process nhanh chóng
- Factor ten: Dev/prod parity: Giữa container đều giống nhau cho nên khi chạy mã ở container dev hoặc production. Không nên để thấy các mã lỗi khác nhau giữa hai container.
- Factor eleven: Logs: Logs quan trọng trong việc ghi lại các sự kiện của container đó trong thời gian dài , và sẽ có công cụ hỗ trợ điều đó với container.
- Factor 12: Admin Processes: các task nên được chạy ở console app , như thêm dữ liệu vào cơ sở dữ liệu , không phải chạy trực tiếp trên cơ sở dữ liệu mà chạy ở bảng điều khiển chính . và phải thiết kế để các nhà phát triển có thể truy cập quyền quản trị tất cả dịch vụ và tùy chỉnh nó được trên bảng đó.

Chạy thực tế: 

https://cloudacademy.com/course/introduction-to-docker-2/course-intro-1/


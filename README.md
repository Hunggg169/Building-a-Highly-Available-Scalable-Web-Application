# Building-a-Highly-Available-Scalable-Web-Application


# Xây dựng Ứng Dụng Web Khả Dụng Cao và Có Khả Năng Mở Rộng

Dự án này triển khai một ứng dụng web trên nền tảng đám mây với mục tiêu đạt được khả năng sẵn sàng cao, dễ mở rộng và bảo mật. Báo cáo này sẽ trình bày tính năng của ứng dụng, kiến trúc đám mây, mã nguồn và hướng dẫn triển khai, phân tích về công nghệ và các khía cạnh bảo mật, vận hành và chi phí.

## 1. Tính năng của Web-App

### **Web App 1: GreenHost - Hệ thống quản lý dịch vụ Hosting**
- **Chức năng đăng ký tài khoản người dùng**: Người dùng có thể đăng ký tài khoản bằng cách nhập thông tin cá nhân và email. Hệ thống kiểm tra email trùng lặp và mã hóa mật khẩu trước khi lưu vào cơ sở dữ liệu.
- **Chức năng đăng nhập**: Sau khi đăng ký, người dùng có thể đăng nhập bằng email và mật khẩu đã đăng ký. Hệ thống xác thực thông tin và cho phép truy cập nếu đúng.
- **Chức năng quản lý tài khoản**: Người dùng có thể xem, chỉnh sửa và xóa thông tin tài khoản của mình trong hệ thống.
- **Chức năng đặt mua gói hosting**: Cho phép người dùng chọn và mua các gói dịch vụ hosting với các tính năng phù hợp với nhu cầu.
  
### **Web App 2: Hệ thống quản lý người dùng**
- **Bảng điều khiển người dùng**: Cho phép quản trị viên xem và quản lý danh sách người dùng đăng ký trong hệ thống.
- **Chức năng quản trị**: Quản trị viên có thể thêm, chỉnh sửa, hoặc xóa người dùng, quản lý các thông tin hosting được người dùng đăng ký.
- **Thống kê người dùng**: Xem thống kê về số lượng người dùng, dịch vụ hosting đã được mua.

## 2. Kiến trúc trên nền tảng đám mây

- **Thiết kế hệ thống mạng**: Hệ thống được triển khai trên một nền tảng đám mây như AWS hoặc Google Cloud với mô hình kiến trúc phân tầng. Các thành phần chính bao gồm:
    - **VPC (Virtual Private Cloud)**: Tạo môi trường mạng riêng cho ứng dụng với các subnet riêng cho các thành phần khác nhau (front-end, back-end).
    - **Load Balancer**: Phân phối lưu lượng truy cập từ người dùng tới các máy chủ web khác nhau để tăng tính khả dụng.
    - **Auto Scaling Group**: Hỗ trợ mở rộng hoặc thu nhỏ tài nguyên tính toán (máy ảo, container) dựa trên nhu cầu thực tế của ứng dụng.
  
- **Tài nguyên tính toán**:
    - **Máy ảo (EC2 hoặc Compute Engine)**: Lưu trữ và chạy mã nguồn của web-app.
    - **Cơ sở dữ liệu (RDS hoặc Cloud SQL)**: Lưu trữ thông tin người dùng và dịch vụ.
  
- **Luồng tương tác của người dùng**:
    - Người dùng truy cập web-app thông qua domain được định tuyến qua **DNS**.
    - Yêu cầu từ người dùng được gửi tới **Load Balancer**, và sau đó được phân phối tới các máy chủ ứng dụng phù hợp (back-end hoặc front-end).
    - Dữ liệu người dùng và dịch vụ được lưu trữ trong **Cơ sở dữ liệu MySQL**.

## 3. Mã nguồn và hướng dẫn triển khai

- **Mã nguồn**: Toàn bộ mã nguồn của ứng dụng web được lưu trữ trên GitHub. Bạn có thể truy cập và sao chép mã nguồn từ [repository này](https://github.com/Hunggg169/Building-a-Highly-Available-Scalable-Web-Application).
  
- **Hướng dẫn triển khai**:
    1. **Clone repository**:
       ```bash
       git clone https://github.com/Hunggg169/Building-a-Highly-Available-Scalable-Web-Application.git
       ```
    2. **Cấu hình cơ sở dữ liệu**:
       - Tạo cơ sở dữ liệu MySQL và cập nhật thông tin cấu hình trong tệp `config.php`.
    3. **Triển khai lên cloud**:
       - Sử dụng các dịch vụ như AWS EC2 hoặc Google Cloud VM để khởi chạy máy chủ.
       - Triển khai mã nguồn trên máy chủ bằng cách cấu hình môi trường PHP và MySQL.
       - Cấu hình **Load Balancer** và **Auto Scaling** để đảm bảo khả dụng và mở rộng.
    4. **Kiểm tra ứng dụng**: Đảm bảo tất cả các thành phần hoạt động trơn tru trên môi trường cloud.

## 4. Công nghệ triển khai

Ứng dụng được triển khai sử dụng các công nghệ:
- **PHP** và **MySQL**: Cho phần back-end của web-app.
- **AWS (hoặc Google Cloud)**: Nền tảng đám mây để lưu trữ và triển khai ứng dụng.
- **Load Balancer** và **Auto Scaling**: Đảm bảo ứng dụng có khả năng mở rộng và phân phối tải đồng đều.
- **HTTPS**: Mã hóa thông tin người dùng khi truyền tải.

## 5. Bảo mật

- **Mã hóa mật khẩu**: Sử dụng hàm `password_hash()` trong PHP để mã hóa mật khẩu trước khi lưu trữ.
- **Chứng chỉ SSL**: Cài đặt chứng chỉ SSL để bảo vệ lưu lượng truy cập web thông qua HTTPS.
- **Firewall**: Thiết lập firewall để giới hạn truy cập tới các thành phần quan trọng như cơ sở dữ liệu và chỉ cho phép truy cập qua cổng bảo mật.

## 6. Chi phí và các khía cạnh vận hành nâng cao

- **Chi phí vận hành**: Chi phí bao gồm sử dụng tài nguyên máy chủ (EC2/VM), lưu trữ cơ sở dữ liệu (RDS/Cloud SQL), và băng thông mạng. Tính toán chi phí dựa trên quy mô sử dụng và cấu hình hệ thống.
  
- **Scaling và Balancing**: Hệ thống sử dụng **Auto Scaling** để tự động mở rộng tài nguyên khi lượng truy cập tăng, kết hợp với **Load Balancer** để phân phối yêu cầu người dùng đồng đều giữa các máy chủ.
  
- **Monitoring**: Sử dụng các công cụ giám sát như **CloudWatch** hoặc **Google Stackdriver** để theo dõi hiệu suất, phát hiện lỗi và tự động thông báo khi có sự cố.



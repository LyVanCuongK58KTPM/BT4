# Môn: Phát triển ứng dụng với mã nguồn mở-TEE0421 <br>
Lớp: 58KTPM <br>
**Bài tập 04:**  <br>
# KHAI THÁC N8N ĐỂ TỰ ĐỘNG ĐĂNG BÀI LÊN WORDPRESS<br>
# 
## deadline : 23h59 ngày 25 tháng 5 năm 2026.<br>

### SỬ DỤNG KẾT QUẢ ĐÃ LÀM Ở BÀI TẬP 3, BỔ SUNG VÀO DOCKER COMPOSE ĐỂ CÓ THÊM SERVICE 8N8:<br>

1. Cấu hình các file trong dokcer-compose.yml:<br>
  - Mariadb:<br>
    <img width="567" height="355" alt="image" src="https://github.com/user-attachments/assets/7a5a5eb4-42c5-4c00-bc8a-dcca70e301d2" /><br>
 - PhPAdmin:<br>
   <img width="460" height="292" alt="image" src="https://github.com/user-attachments/assets/46af51c5-cd39-44c9-9ec9-924857bc40e3" /><br>
 - WordPress:<br>
   <img width="545" height="385" alt="image" src="https://github.com/user-attachments/assets/6e8719e4-f226-4b23-92c9-08b13591deba" /><br>
 - Cấu hình Tunel cloudflare để truy cập vào các dịch vụ bằng các subdomain ( em sử dụng lệnh cli thay cho việc thao tác đồ họa trên dashboard của cloudflare):<br>
   + Tạo tunel của 3 sub-domain:<br>
     <img width="1443" height="136" alt="image" src="https://github.com/user-attachments/assets/7fe94cbf-4587-4862-a0ec-40fd6eb461a9" /><br>

   <img width="1469" height="209" alt="image" src="https://github.com/user-attachments/assets/0d0dea82-9448-4795-a1e1-f9f5e79cef50" /><br>
   + Thêm chuỗi id tunel vào config.yml:<br>
     <img width="1048" height="396" alt="image" src="https://github.com/user-attachments/assets/d2abf294-b7d7-4ebc-bb8d-8e39c1c342bc" /><br>
   + Cấu hình dịch vụ cloudflare trong docker-compose.yml:<br>
    <img width="1227" height="391" alt="image" src="https://github.com/user-attachments/assets/16d84d68-7e80-4a7d-87fc-e035ad561f4b" /><br>
   + Cấp lại quyền truy cập file trên máy host:<br>
     <img width="917" height="45" alt="image" src="https://github.com/user-attachments/assets/37ad26d9-2eae-4242-9932-22c78adef0b9" /><br>
- n8n:<br>
  <img width="1361" height="304" alt="image" src="https://github.com/user-attachments/assets/3c3efe59-4061-4e05-9889-2f720f356a43" /><br>

   - Pull các images về và chạy chúng:<br>
     <img width="1462" height="320" alt="image" src="https://github.com/user-attachments/assets/41accd0e-d714-48e7-bce1-fbc319c70cdc" /><br>

2. Kiểm tra truy cập các sub-domain:<br>
    + Truy cập sub-domain2 để quan sát xem cơ sở dữ liệu chưa có bảng nào:<br>
      <img width="1076" height="447" alt="image" src="https://github.com/user-attachments/assets/0bf0ff13-be05-48b7-8113-57bd18534e06" /><br>
    + Truy cập sub-domain1 để cài đặt wordpress:<br>
      <img width="1892" height="710" alt="image" src="https://github.com/user-attachments/assets/2f782793-a7cc-4604-8645-920f63fdfe08" /><br>
    + Truy cập sub-domain2 để quan sát xem cơ sở dữ liệu có những bảng dữ liệu nào sau khi cài wp:<br>
    <img width="1876" height="878" alt="image" src="https://github.com/user-attachments/assets/5f927e52-cdfe-4fac-8636-c94096b517b7" /><br>
    + Tạo 1 bài viết trong wordpress giới thiệu về bản thân sinh viên: thông tin cá nhân, sở thích, ... bài viết có thể chứa hình ảnh, âm thanh, video, ...<br>
      <img width="1170" height="842" alt="image" src="https://github.com/user-attachments/assets/622fa405-9cab-4996-b139-e66464d84989" /><br>
    + Tạo 1 bài viết trong wordpress giới thiệu về nhữn kiến thức mà em đã học được ở môn **Phát triển ứng dụng với mã nguồn mở**<br>
  <img width="1816" height="958" alt="image" src="https://github.com/user-attachments/assets/1a4df845-8121-42e5-8bbd-e32f6a3f564e" /><br>
    
- Truy cập sub-domain3 để cấu hình n8n:<br>
  + tạo tài khoản admin :<br>
  <img width="1702" height="923" alt="image" src="https://github.com/user-attachments/assets/2ea9f757-611e-4c95-883c-2fb04b8acfc6" /><br>
3. Cấu hình n8n:<br>
  - Send me a Licence key:<br>
    <img width="1858" height="940" alt="image" src="https://github.com/user-attachments/assets/ccf30037-4087-4102-93a7-b85764792758" /><br>
  - Kiểm tra email:<br>
    <img width="1748" height="949" alt="image" src="https://github.com/user-attachments/assets/6302be26-7fc5-44d8-986e-add37975b1f4" /><br>

  - Activate License key: ( trang chủ -> setting -> usage and plan -> enter activation key -> điền key vừa nhận từ email vào):<br>
    <img width="1806" height="723" alt="image" src="https://github.com/user-attachments/assets/66831564-6025-40c6-a34e-fa33ea7bb0e0" /><br>
  - Tạo workflow mới:<br>
    <img width="1890" height="835" alt="image" src="https://github.com/user-attachments/assets/275b388b-7596-48eb-bae5-19fe5b8c3192" /><br>
  - Add trigger node: tìm node: Telegram => OnMessage  ; cấu hình Credential: Set up Credential => cần Nhập Access Token<br>
    + Cần chát với bot @BotFather trên Telegram để đẻ ra bot mới của riêng mình:<br>
      <img width="944" height="2046" alt="image" src="https://github.com/user-attachments/assets/cecbc6c6-950b-46ad-b391-c2dab25341a8" /><br>
    + Sau khi tạo bot mới cần copy lấy Token<br>
      <img width="374" height="807" alt="image" src="https://github.com/user-attachments/assets/2a632265-41bc-4877-a07f-b7eecc58325d" /><br>
      <img width="1830" height="889" alt="image" src="https://github.com/user-attachments/assets/6d8d73af-fbf8-40d4-9166-b65097a49db1" /><br>
    + Chát lần đầu với bot mới này:<br>
      <img width="944" height="2046" alt="image" src="https://github.com/user-attachments/assets/390e3107-e45f-40ab-9ee6-f130268ee9e0" /><br>
      <img width="660" height="683" alt="image" src="https://github.com/user-attachments/assets/305bb29b-b0fa-4d6c-a5bc-18647ceaa743" /><br>
      
  - Add (nối tiếp vào sau node Telegram Trigger) node: AI Google Gemini => Message a model => Set up Credential => cần Nhập API KEY<br>
    + Lấy API KEY tại trang: https://aistudio.google.com<br>
    <img width="1885" height="964" alt="image" src="https://github.com/user-attachments/assets/2e53acb0-1c8c-4a8c-93fa-b844d5b77786" /><br>

    + Nhập API Key lên giao diện n8n:<br>
       <img width="1354" height="741" alt="image" src="https://github.com/user-attachments/assets/79904edb-55fc-411c-aae0-52a1c40c9746" /><br>

    + kéo thả **nội dung đã chát** với bot của telegram (phía bên trái) vào **nội dung phần PROMPT** kết quả được {{ $json.message.text }}, cần gõ thêm vào sau {{ $json.message.text }} để promt dài hơn : vd ({{ $json.message.text }}. Kết quả sinh ra ở định dạng HTML+CSS để tôi dùng HTML+CSS này tạo bài viết cho wordpress.)<br>
      <img width="1855" height="849" alt="image" src="https://github.com/user-attachments/assets/0f0b7110-99ab-4569-a816-91a1c5de68f5" /><br>
    + Turn on Output Content as JSON : để kết quả trả về dạng json<br>
      <img width="542" height="688" alt="image" src="https://github.com/user-attachments/assets/9fbc3a21-3908-44f2-8ce2-145d2f204909" /><br>

    + Thêm Option để AI viết bài thông minh hơn, văn phong nhiều màu hơn thay vì những văn bản chứa các nội dung cứng ngắc:<br>
      <img width="517" height="248" alt="image" src="https://github.com/user-attachments/assets/af99a2f8-dcff-4045-be19-851cfd593e60" /><br>

  - Add (nối tiếp vào sau node Message a model) node: Code in JavaScript<br>
    <img width="737" height="751" alt="image" src="https://github.com/user-attachments/assets/50f1d467-cc45-4171-8069-160b279d7848" /><br>

  - Add (nối tiếp vào sau node Code in JavaScript) node: WordPress => Create a Post<br>
    + Set up Credential: vào wp tại url: https://sub-domain1/wp-admin  => vào mục Tài Khoản => chọn user đã tạo lúc setup wordpress => Mật khẩu ứng dụng => Nhập n8n và bấm "Thêm mật khẩu ứng dụng" => copy chuỗi 24 kí tự : Đây là mật khẩu ứng dụng => paste vào mục Password của n8n Credential<br>
      <img width="1916" height="782" alt="image" src="https://github.com/user-attachments/assets/d02c4cd8-7a58-47fe-bae9-063bf0e83f23" /><br>
      <img width="1892" height="868" alt="image" src="https://github.com/user-attachments/assets/364fadb1-8d4c-40d8-967b-283a4c2ef656" /><br>
    + Quay lại n8n:<br>
      <img width="1198" height="730" alt="image" src="https://github.com/user-attachments/assets/aa423297-8903-43cf-a967-1cf58f2db591" /><br>
    + Cấu hình node Create a Post: bấm nút Execute previous nodes sau đó thực hiện các bước trong ảnh:<br>
      <img width="1141" height="866" alt="image" src="https://github.com/user-attachments/assets/630321c4-371f-40b9-9a30-4ce8eaf3ec56" /><br>

    + PUBLISH flow (góc trên phải) Nút này thực hiện việc xuất bản flow <=> flow sẽ tự động thực thi khi thoả mãn điều kiện trigger<br>
      <img width="1628" height="711" alt="image" src="https://github.com/user-attachments/assets/18be46c7-9751-4d26-8906-445b85b64dc4" /><br>

   
  4. Kết quả: Em sẽ để video kết quả demo ở link youtube dưới file<br>
  5. Nhận xét kết quả đạt được:<br>
     - Triển khai thành công Stack dịch vụ mã nguồn mở gồm MariaDB, phpMyAdmin, WordPress và n8n chạy biệt lập trên môi trường Docker. Kết nối HTTPS qua Cloudflare Tunnel hoạt động ổn định.<br>

   - Tự động hóa hoàn chỉnh: Xây dựng thành công luồng dữ liệu khép kín tự động 24/7: Người dùng nhắn tin (Telegram Bot) ➔ Trí tuệ nhân tạo (Google Gemini AI) xử      lý & sinh cấu trúc JSON/HTML ➔ Code JavaScript dọn dẹp, xử lý chuỗi ➔ Tự động xuất bản bài viết (WordPress API).<br>

   - Tối ưu hóa và Xử lý lỗi: Hệ thống được cấu hình System Message chặt chẽ giúp ép văn phong chuẩn xác hơn, xử lý chuỗi bằng JavaScript giúp hệ thống vận hành mượt mà.<br>
     

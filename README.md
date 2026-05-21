# Môn: Phát triển ứng dụng với mã nguồn mở-TEE0421
Lớp: 58KTPM
**Bài tập 04:**  
# KHAI THÁC N8N ĐỂ TỰ ĐỘNG ĐĂNG BÀI LÊN WORDPRESS
# 
## deadline : 23h59 ngày 25 tháng 5 năm 2026.

### SỬ DỤNG KẾT QUẢ ĐÃ LÀM Ở BÀI TẬP 3, BỔ SUNG VÀO DOCKER COMPOSE ĐỂ CÓ THÊM SERVICE 8N8:

1. Cấu hình các file trong dokcer-compose.yml:
  - Mariadb:
    <img width="567" height="355" alt="image" src="https://github.com/user-attachments/assets/7a5a5eb4-42c5-4c00-bc8a-dcca70e301d2" />
 - PhPAdmin:
   <img width="460" height="292" alt="image" src="https://github.com/user-attachments/assets/46af51c5-cd39-44c9-9ec9-924857bc40e3" />
 - WordPress:
   <img width="545" height="385" alt="image" src="https://github.com/user-attachments/assets/6e8719e4-f226-4b23-92c9-08b13591deba" />
 - Cấu hình Tunel cloudflare để truy cập vào các dịch vụ bằng các subdomain ( em sử dụng lệnh cli thay cho việc thao tác đồ họa trên dashboard của cloudflare):
   + Tạo tunel của 3 sub-domain:
     <img width="1443" height="136" alt="image" src="https://github.com/user-attachments/assets/7fe94cbf-4587-4862-a0ec-40fd6eb461a9" />

   <img width="1469" height="209" alt="image" src="https://github.com/user-attachments/assets/0d0dea82-9448-4795-a1e1-f9f5e79cef50" />
   + Thêm chuỗi id tunel vào config.yml:
     <img width="1048" height="396" alt="image" src="https://github.com/user-attachments/assets/d2abf294-b7d7-4ebc-bb8d-8e39c1c342bc" />
   + Cấu hình dịch vụ cloudflare trong docker-compose.yml:
    <img width="1227" height="391" alt="image" src="https://github.com/user-attachments/assets/16d84d68-7e80-4a7d-87fc-e035ad561f4b" />
   + Cấp lại quyền truy cập file trên máy host:
     <img width="917" height="45" alt="image" src="https://github.com/user-attachments/assets/37ad26d9-2eae-4242-9932-22c78adef0b9" />
- n8n:
  <img width="1361" height="304" alt="image" src="https://github.com/user-attachments/assets/3c3efe59-4061-4e05-9889-2f720f356a43" />

2. Thực hiện:
   - Pull các images về và chạy chúng:
     <img width="1462" height="320" alt="image" src="https://github.com/user-attachments/assets/41accd0e-d714-48e7-bce1-fbc319c70cdc" />

  - Kiểm tra truy cập các sub-domain:
    + Truy cập sub-domain2 để quan sát xem cơ sở dữ liệu chưa có bảng nào:
      <img width="1076" height="447" alt="image" src="https://github.com/user-attachments/assets/0bf0ff13-be05-48b7-8113-57bd18534e06" />
    + Truy cập sub-domain1 để cài đặt wordpress:
      <img width="1892" height="710" alt="image" src="https://github.com/user-attachments/assets/2f782793-a7cc-4604-8645-920f63fdfe08" />
    + Truy cập sub-domain2 để quan sát xem cơ sở dữ liệu có những bảng dữ liệu nào sau khi cài wp:
    <img width="1876" height="878" alt="image" src="https://github.com/user-attachments/assets/5f927e52-cdfe-4fac-8636-c94096b517b7" />
    + Tạo 1 bài viết trong wordpress giới thiệu về bản thân sinh viên: thông tin cá nhân, sở thích, ... bài viết có thể chứa hình ảnh, âm thanh, video, ...
      <img width="1170" height="842" alt="image" src="https://github.com/user-attachments/assets/622fa405-9cab-4996-b139-e66464d84989" />
    + Tạo 1 bài viết trong wordpress giới thiệu về nhữn kiến thức mà em đã học được ở môn **Phát triển ứng dụng với mã nguồn mở**
  <img width="1816" height="958" alt="image" src="https://github.com/user-attachments/assets/1a4df845-8121-42e5-8bbd-e32f6a3f564e" />
    
- Truy cập sub-domain3 để cấu hình n8n:
  + tạo tài khoản admin : nhớ điền đúng email:
  <img width="1904" height="926" alt="image" src="https://github.com/user-attachments/assets/702f2f7d-0920-45c2-9134-ab108eb10e30" />

  + Send me a Licence key, bước này điền đủ thông tin, làm chậm sẽ thấy mục gửi License key về mail (n8n sẽ gửi email KEY cho dùng), check email để lấy KEY
  + Activate License key: vào trang chủ => SETTING (góc dưới trái) => Usage and plan => Enter activation key: paste key từ email vào đây => Activate => sẽ nhận đc thông báo (góc dưới phải) Your Registered Community Edition has been successfully activated.
  + Create workflow  (home page => overview => Create workflow)
  + Add trigger node: tìm node: Telegram => OnMessage  ; cấu hình Credential: Set up Credential => cần Nhập Access Token
    + Access Token thì lấy ở Telegram qua việc chát với @BotFather
    + Cần chát với bot @BotFather để đẻ ra bot mới của riêng mình. bot này sẽ là nơi nhận lệnh (promt) để AI sinh html => n8n sẽ dùng html này để đăng bài lên wp
    + Sau khi tạo bot mới cần copy lấy Token, và chát lần đầu với bot mới này, nội dung bất kỳ (bước này quan trọng!)
  + Add (nối tiếp vào sau node Telegram Trigger) node: AI Google Gemini => Message a model => Set up Credential => cần Nhập API KEY
    + Lấy API KEY tại trang: https://aistudio.google.com  => https://aistudio.google.com/api-keys
    + cần tạo project mới, sẽ lấy được API KEY
    + Nhập API Key lên giao diện n8n
    + kéo thả **nội dung đã chát** với bot của telegram (phía bên trái) vào **nội dung phần PROMPT** kết quả được {{ $json.message.text }}, cần gõ thêm vào sau {{ $json.message.text }} để promt dài hơn : vd ({{ $json.message.text }}. Kết quả sinh ra ở định dạng HTML+CSS để tôi dùng HTML+CSS này tạo bài viết cho wordpress.)
    + Turn on Output Content as JSON : để kết quả trả về dạng json
    + Có thể thử nghiệm các thành phần khác trong Options (add Options: System message, ...) => đưa ra cái nào đáng dùng?
  + Add (nối tiếp vào sau node Message a model) node: Code in JavaScript
    + Code js ở dạng này, có thể phải thay đổi tuỳ theo json AI trả về.
```
// 1. lấy dữ liệu gốc
const rawText = $input.first().json.content.parts[0].text;

// 2. Chuyển đổi chuỗi (đã được bọc JSON) thành Object trong JavaScript
const cleanData = JSON.parse(rawText);

// 3. Trả về kết quả định dạng lại gọn gàng cho n8n sử dụng
return {
  title: cleanData.post_title,
  content: cleanData.post_content
};
```

  + Add (nối tiếp vào sau node Code in JavaScript) node: WordPress => Create a Post
    + Set up Credential: vào wp tại url: https://sub-domain1/wp-admin  => vào mục Tài Khoản => chọn user đã tạo lúc setup wordpress => Mật khẩu ứng dụng => Nhập n8n và bấm "Thêm mật khẩu ứng dụng" => copy chuỗi 24 kí tự : Đây là mật khẩu ứng dụng => paste vào mục Password của n8n Credential
    + Wordpress URL: điền giá trị https://sub-domain1/   (giá trị này cũng khai báo trong biến môi trường WEBHOOK_URL của n8n)
    + Ignore SSL Issues (Insecure): TURN ON
    + Cấu hình node Create a Post: bấm nút Execute previous nodes để thấy trường giá trị của node trước trả về, kéo nội dung phần title (bên trái) vào trường title, tương tự kéo nội dung content vào content
    + Add field (Thêm thuộc tính): Status == Publish (bài đăng sẽ ở trạng thái xuất bản ngay lập tức, mặc định nó ở giá trị Draft bản nháp)
+ PUBLISH flow (góc trên phải) Nút này thực hiện việc xuất bản flow <=> flow sẽ tự động thực thi khi thoả mãn điều kiện trigger
   
+ Kết quả cuối cùng cần đặt được:
  + từ điện thoại, chát với telegram bot
  + nội dung chát được tự động gửi tới node Telegram trigger => Gửi tới Google Gemini Message a model (bản chất là gửi Prompt) : Nhận về json kết quả của Prompt => Gửi sang node Code in JavaScript để tách tiêu đề và nội dung => gửi đến node WordPress để Create a Post(đăng bài) với tiêu đề và nội dung từ node trước gửi sang.
  + f5 wordpress để thấy bài viết mới đã lên sóng.

+ Chụp ảnh quá trình thao tác/cấu hình/các kết quả trung gian đạt được
+ Nhận xét thành quả đạt được!!!


demo kết quả cuối cùng:

chát với bot:

<img width="471" height="264" alt="image" src="https://github.com/user-attachments/assets/7c439503-63b4-4529-bbec-78fa1d4933d6" />

flow automation của n8n (nhìn bên ngoài):

<img width="1319" height="389" alt="image" src="https://github.com/user-attachments/assets/abbdc5af-952f-4d50-8fba-0cafc7334212" />


bài tự động đăng trên wp:

<img width="750" height="817" alt="image" src="https://github.com/user-attachments/assets/4f7c0cec-292f-4973-9eb0-1534189cdb18" />

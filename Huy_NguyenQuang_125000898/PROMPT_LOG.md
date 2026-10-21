# NHẬT KÝ PROMPT ENGINEERING (VIBE CODING LOG)
- **Họ và tên:** Nguyễn Quang Huy
- **MSSV:** 125000898
- **Tên đề tài Website:** Modern Personal Portfolio & Showcase cho Sinh viên CNTT LHU
- **Công cụ AI đã sử dụng:** Google Antigravity (Gemini 3.8 Flash Agentic AI), VS Code

---

## 1. Yêu cầu ban đầu (System/Initial Prompt)
> "Đóng vai trò là một Senior Frontend Developer và chuyên gia UI/UX. Hãy thiết kế cho tôi một website Portfolio cá nhân hiện đại dành cho sinh viên ngành Công nghệ Thông tin - Trường Đại học Lạc Hồng. 
> 
> Thông tin sinh viên:
> - Họ và tên: Nguyễn Quang Huy
> - MSSV: 125000898
> - Email: 125000898@lachong.edu.vn
> - Số điện thoại / Zalo: 0812692781
> 
> Yêu cầu kỹ thuật bắt buộc:
> 1. Chuẩn Semantic HTML5: Cấu trúc bắt buộc gồm thẻ `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`. Tuyệt đối không lạm dụng thẻ `<div>` vô nghĩa.
> 2. Kỹ thuật CSS: Sử dụng CSS Variables (`:root`) để quản lý toàn bộ hệ thống màu sắc, typography và spacing nhất quán; áp dụng CSS Flexbox và CSS Grid cho bố cục responsive.
> 3. Hiệu ứng động: Tích hợp thư viện Animate.css cho Hero Section và thư viện AOS (Animate On Scroll) cho các khối nội dung khi cuộn chuột.
> 4. Tương tác UI: Tự viết hiệu ứng `:hover`, `:focus` mượt mà cho các nút bấm (buttons), thẻ bài viết (cards) và form liên hệ.
> 5. Cấu trúc mã nguồn tinh gọn: Tách bạch rõ ràng giữa file `index.html`, `style.css` và `script.js`."

---

## 2. Quá trình tinh chỉnh & Giải quyết sự cố (Iteration Iterations)

### Lần 1: Dựng khung Semantic HTML & CSS Variable
- **Prompt đã dùng:**
  > "Hãy tạo khung cấu trúc HTML5 và hệ thống biến CSS `:root` cho trang Portfolio của sinh viên Nguyễn Quang Huy (MSSV: 125000898). Khung phải thể hiện rõ các khu vực: Header (Brand + Navigation), Hero Section, About Me, Năng lực kỹ thuật (Skills), Dự án tiêu biểu (Projects), Form liên hệ (Contact) và Footer chứa thông tin sinh viên Lạc Hồng."
- **Kết quả AI tạo ra:**
  AI đã sinh ra mã HTML cơ bản và CSS, tuy nhiên AI có xu hướng bọc các dự án bên trong nhiều thẻ `<div class="card">` lồng nhau và khu vực điều hướng dùng `<div class="navbar">` thay vì tận dụng tối đa các thẻ chuẩn ngữ nghĩa HTML5.
- **Nhận xét & Tinh chỉnh của SV:**
  - *Nhận xét:* Việc lạm dụng thẻ `<div>` làm giảm khả năng tiếp cận (Accessibility - a11y) và vi phạm tiêu chí chấm điểm khắt khe về Semantic HTML5 trong đề thi (Thang điểm yêu cầu tối thiểu 5 thành phần ngữ nghĩa và hạn chế tối đa `<div>`).
  - *Tinh chỉnh đã thực hiện:* Yêu cầu AI tái cấu trúc lại:
    1. Chuyển toàn bộ danh sách dự án sang dùng thẻ `<article class="project-card">` thay vì `<div>`.
    2. Chuyển khối thông tin trường học/mục tiêu sang các khối có cấu trúc logic.
    3. Đưa danh sách liên kết vào thẻ `<nav>` kết hợp thẻ danh sách `<ul>`, `<li>`.
    4. Thêm các thuộc tính hỗ trợ người dùng như `aria-label`, `aria-expanded` cho nút điều hướng di động.

### Lần 2: Tích hợp thư viện Animate.css & AOS
- **Prompt đã dùng:**
  > "Hãy tích hợp CDN của Animate.css v4.1.1 và AOS (Animate On Scroll) v2.3.4 vào `index.html`. Áp dụng các class hiệu ứng Animate.css cho tiêu đề chính ở Hero Section và gắn thuộc tính `data-aos` vào các thẻ `<article>`, `<section>`."
- **Thách thức gặp phải:**
  - *Sự cố 1:* Sau khi nhúng link CDN AOS trong `<head>`, các hiệu ứng cuộn trang không hoạt động khi cuộn chuột qua các section bên dưới, các phần tử bị ẩn hoặc đứng yên.
  - *Sự cố 2:* Hiệu ứng Animate.css chạy quá nhanh và đồng thời, khiến mắt người xem bị phân tâm, giao diện có cảm giác rối mắt.
- **Cách sửa prompt (Debug prompt):**
  > "Khắc phục 2 vấn đề sau:
  > 1. Thư viện AOS yêu cầu phải có file script JS kèm lệnh khởi tạo `AOS.init()` ở cuối thẻ `<body>`. Hãy bổ sung CDN JS của AOS cùng cấu hình tham số `{ duration: 800, easing: 'ease-in-out', once: true, offset: 100 }` để hiệu ứng cuộn mượt mà và chỉ kích hoạt một lần duy nhất.
  > 2. Đối với Animate.css trên Hero Section, hãy sử dụng các class độ trễ `animate__delay-1s`, `animate__delay-2s` và phân bổ nhịp nhàng (Pill badge xuất hiện trước -> Tiêu đề H1 -> Đoạn mô tả -> Nhóm nút bấm CTA) để tạo cảm giác chuyên nghiệp theo chuẩn UX Motion."

### Lần 3: Tối ưu Responsive Layout & Tự viết hiệu ứng Hover/Focus
- **Prompt đã dùng:**
  > "Hãy kiểm tra giao diện trên màn hình điện thoại (Mobile < 768px). Viết thêm CSS Media Queries và JavaScript cho menu Hamburger đóng/mở mượt mà. Đồng thời, tự viết hiệu ứng CSS `:hover` nâng thẻ card (`transform: translateY(-8px)`), viền phát sáng (`border-color` & `box-shadow`) và `:focus-visible` cho các ô input của biểu mẫu liên hệ."
- **Kết quả AI tạo ra:**
  AI đã hoàn thiện responsive mượt mà với Flexbox cột đơn trên mobile, bổ sung hiệu ứng thẻ card 3D nhẹ nhàng và hiệu ứng viền sáng xanh neon tinh tế chuẩn Dark Theme hiện đại.

---

## 3. Đánh giá cá nhân về quá trình Vibe Coding
- **AI đã giúp bạn tiết kiệm thời gian ở phần nào nhất?**
  - AI giúp đẩy nhanh tốc độ viết mã khởi tạo (boilerplate code) tới hơn 70%, đặc biệt là việc xây dựng hệ thống CSS Variables quy chuẩn (`:root`), bảng màu phối sẵn đồng bộ và dàn layout ban đầu bằng CSS Grid/Flexbox.
  - Hỗ trợ nhanh chóng trong việc tra cứu CDN chính xác của các thư viện (Animate.css, AOS) và tạo dữ liệu giả lập (mock data) thực tế và trực quan cho các dự án và hồ sơ sinh viên.

- **Bài học rút ra khi đặt câu hỏi (Prompt) cho AI trong thiết kế web?**
  1. *Prompt càng chi tiết về kiến trúc thì kết quả càng chuẩn xác:* Nếu chỉ yêu cầu chung chung "Làm một trang web đẹp", AI thường chọn giải pháp dễ nhất là dùng thẻ `<div>` vô tội vạ. Khi chỉ định rõ ràng "Tuân thủ Semantic HTML5 với `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`", AI sẽ tạo ra cấu trúc mã nguồn chất lượng cao, đúng chuẩn công nghiệp.
  2. *Tư duy phản biện và kiểm soát (Control) là then chốt trong Vibe Coding:* Lập trình viên không chỉ nhấn nút sinh mã mà cần liên tục kiểm tra lỗi logic, cấu hình thư viện (như việc thiếu `AOS.init()`), cân chỉnh trải nghiệm người dùng (UX) và tối ưu độ tương thích trên thiết bị di động.

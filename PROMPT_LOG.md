# NHẬT KÝ PROMPT ENGINEERING (VIBE CODING LOG)

- **Họ và tên:** Nguyễn Minh Thiên
- **MSSV:** 125000493
- **Tên đề tài Website:** Landing Page giới thiệu game Valorant
- **Công cụ AI đã sử dụng:** Claude (phân tích đề, soạn prompt, dựng lại và chỉnh sửa mã nguồn), Antigravity (dựng phiên bản đầu và sửa lỗi JavaScript)

## 1. Yêu cầu ban đầu (System/Initial Prompt)

> Quy trình của tôi: đưa file đề thi cho Claude, nhờ Claude chuyển các yêu cầu bắt buộc (mục II) và thang điểm (mục IV) thành một prompt chuẩn, sau đó dán vào Antigravity để dựng website.
>
> Nội dung chính của prompt ban đầu:
> - Vai trò: lập trình viên frontend, làm landing page game Valorant trong 120 phút, chỉ dùng HTML5, CSS và thư viện hiệu ứng.
> - Cấu trúc file: `index.html`, `style.css`, thư mục `assets/`.
> - **Semantic HTML5:** dùng `header`, `nav`, `main`, `section`, `article`, `footer`; chỉ 1 thẻ `h1`; không lạm dụng `div`; ảnh đều có `alt`.
> - **CSS Variables:** khai báo trong `:root` cho màu, font, khoảng cách, bo góc, bóng, transition; toàn bộ CSS dùng `var(--...)`.
> - **Layout:** CSS Grid cho lưới card, Flexbox cho header, hero, footer; responsive ở 1366x768, 768 và 390x844.
> - **Hiệu ứng:** Animate.css cho hero (tiêu đề, mô tả, nút CTA); AOS cho các section và card; hover và focus tự viết bằng CSS.
> - **Quy trình:** commit nhỏ, rõ ràng; đường dẫn tương đối để chạy trên GitHub Pages; tự kiểm tra và báo bảng PASS/FAIL.

## 2. Quá trình tinh chỉnh & Giải quyết sự cố (Iteration)

### Lần 1: Dựng khung Semantic HTML5, CSS Variables, Animate.css và AOS
- **Prompt đã dùng:** Prompt tổng quan ở mục 1, do Claude soạn dựa trên mục II và thang điểm mục IV của đề.
- **Kết quả AI tạo ra:** Antigravity dựng trang landing gồm các section hero, giới thiệu, Agent, bản đồ, lối chơi, cộng đồng; dùng thẻ ngữ nghĩa, CSS Variables, Grid/Flexbox, Animate.css và AOS.
- **Nhận xét & Tinh chỉnh của SV:** Tôi đối chiếu kết quả với đề thi và phát hiện prompt ban đầu cho phép tạo file `script.js`, trong khi giảng viên yêu cầu không được dùng JavaScript. Xử lý ở Lần 2.

### Lần 2: Loại bỏ JavaScript tự viết theo yêu cầu của giảng viên
- **Thách thức gặp phải:** Giảng viên yêu cầu không dùng JavaScript, nhưng prompt ban đầu có cho phép `script.js`. Tôi phát hiện khi Antigravity đang làm dở dang.
- **Cách sửa prompt (Debug prompt):** Tôi yêu cầu Antigravity dừng lại và sửa:
  1. Xóa `script.js`, gỡ thẻ script tương ứng; kiểm tra bằng cách tìm `<script`, `onclick`, `addEventListener` trong toàn bộ dự án.
  2. Làm menu mobile hoàn toàn bằng CSS (checkbox hack với `:checked`).
  3. Form đăng ký chỉ giữ giao diện HTML, không xử lý bằng JS.
  4. Animate.css chỉ dùng class trong HTML. AOS chỉ giữ link CDN và đúng một dòng `AOS.init()` là dòng khởi tạo bắt buộc của thư viện (có comment giải thích), không thêm JS nào khác.
- **Nhận xét & Tinh chỉnh của SV:** Bài học: phải ghi các điều CẤM của giảng viên vào ngay prompt đầu tiên. Tôi cũng sẽ hỏi lại giảng viên về dòng `AOS.init()` để chắc chắn không bị tính là JavaScript tự viết.

### Lần 3: Sửa font chữ tiếng Việt và cải thiện giao diện
- **Thách thức gặp phải:** Khi xem lại trang, tôi thấy giao diện chưa đẹp và font chữ bị lỗi hiển thị (dấu tiếng Việt). Nguyên nhân khả dĩ là font ban đầu không hỗ trợ đầy đủ tiếng Việt.
- **Cách sửa prompt (Debug prompt):** Tôi nhờ Claude soạn prompt yêu cầu: đổi toàn bộ font sang Roboto (có hỗ trợ tiếng Việt), làm đẹp lại hero, card, footer, và tự tạo ảnh cho các phần còn thiếu; vẫn giữ ràng buộc không viết JavaScript.
- **Kết quả:** Antigravity hết credit trước khi tôi hoàn tất được bước này, nên tôi chuyển sang Claude để trực tiếp dựng lại (Lần 4).

### Lần 4: Chuyển sang Claude dựng lại toàn bộ website
- **Thách thức gặp phải:** Hết credit Antigravity trong lúc trang còn lỗi font và giao diện chưa hoàn thiện, trong khi đang trong thời gian làm bài.
- **Cách sửa prompt (Debug prompt):** Tôi giao lại cho Claude toàn bộ yêu cầu của đề (mục II, thang điểm mục IV) cùng các ràng buộc đã rút ra: không JavaScript tự viết (chỉ giữ `AOS.init`), font Roboto, tự tạo ảnh cho các phần còn thiếu.
- **Kết quả AI tạo ra:** Claude dựng lại `index.html`, `style.css` và ảnh SVG tự tạo: font Roboto, 0 thẻ `div`, menu mobile bằng CSS, Grid và Flexbox, hiệu ứng hover/focus tự viết, Animate.css cho hero và AOS cho các section.
- **Nhận xét & Tinh chỉnh của SV:** Tôi kiểm tra lại: chỉ còn 2 thẻ `<script>` (link AOS và dòng `AOS.init`), không còn `script.js`, ảnh đều có `alt`.

### Lần 5: Dùng ảnh Agent và bản đồ chính thức từ game
- **Thách thức gặp phải:** Ảnh Agent và bản đồ tự vẽ (SVG) khác ảnh thật của game, tôi muốn dùng ảnh chuẩn từ game cho đúng chủ đề.
- **Cách sửa prompt (Debug prompt):** Tôi yêu cầu thay ảnh Agent và bản đồ bằng ảnh chính thức, vẫn giữ nguyên ràng buộc không JavaScript, đồng thời ghi rõ nguồn ảnh.
- **Kết quả AI tạo ra:** Claude lấy link ảnh Agent và bản đồ từ API cộng đồng `valorant-api.com`, thay vào `index.html`, thêm class `card-agent` và `card-map` để CSS cắt ảnh đúng tỉ lệ, xóa các SVG cũ và thêm dòng ghi nguồn "Hình ảnh thuộc Riot Games, nguồn: valorant-api.com" ở footer.
- **Nhận xét & Tinh chỉnh của SV:** Tôi lưu ý ảnh thuộc bản quyền Riot Games nên giữ trang ở mục đích học tập, phi thương mại và có ghi nguồn.

### Lần 6: Kiểm tra GitHub Pages
- **Thách thức gặp phải:** Link GitHub Pages ban đầu không mở được (lỗi 404).
- **Cách sửa prompt (Debug prompt):** Tôi hỏi Claude cách kiểm tra. Các bước đã làm: xem lại Settings > Pages (nhánh `main`, thư mục `/ (root)`), kiểm tra tab Actions để xem trạng thái build, đảm bảo `index.html` nằm ở thư mục gốc, đã `git push`, và repo ở chế độ Public.
- **Kết quả:** [Ghi lại kết quả thực tế, ví dụ: link live đã mở được sau khi push.]

## 3. Đánh giá cá nhân về quá trình Vibe Coding

- **AI đã giúp bạn tiết kiệm thời gian ở phần nào nhất?** AI dựng rất nhanh khung HTML ngữ nghĩa, hệ thống CSS Variables, lưới Grid/Flexbox responsive, cấu hình Animate.css và AOS, cũng như các ảnh minh họa. Những phần này nếu tự viết tay sẽ mất nhiều thời gian trong 120 phút.
- **Bài học rút ra khi đặt câu hỏi (Prompt) cho AI trong thiết kế web?**
  - Phải đọc kỹ ràng buộc của giảng viên và ghi thành điều CẤM ngay từ prompt đầu (ví dụ: không tự viết JavaScript).
  - Chia yêu cầu rõ theo từng mục (ngữ nghĩa, CSS, hiệu ứng, Git) và yêu cầu AI tự kiểm tra, báo PASS/FAIL.
  - Luôn tự đối chiếu kết quả với đề thi và thang điểm, không tin hoàn toàn vào AI (ví dụ: font lỗi tiếng Việt, JavaScript lọt vào bài).
  - Cần có phương án dự phòng khi công cụ hết credit, và viết prompt gọn để tiết kiệm credit.
  - Với tài nguyên bên thứ ba như ảnh game, phải ghi rõ nguồn và chỉ dùng cho mục đích học tập.

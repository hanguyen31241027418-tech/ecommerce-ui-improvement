# AI Usage Log

## 1. Công cụ AI
Tên công cụ: ChatGPT / Gemini

## 2. Mục đích sử dụng
- Khảo sát và phân tích ưu/nhược điểm UI/UX của website Tiki.vn (Đóng vai chuyên gia BA).
- Đề xuất phương án thiết kế lại bố cục Thẻ sản phẩm (Product Card).
- Sinh mã nguồn HTML5 và CSS3 dựa trên bố cục đã thống nhất.

## 3. Prompt đã sử dụng
**Prompt 1 (Khảo sát UX/UI):**
> "Bạn là chuyên gia phân tích nghiệp vụ và thiết kế trải nghiệm người dùng cho website thương mại điện tử. Tôi đang khảo sát website: Tiki (https://tiki.vn/). Hãy giúp tôi lập bảng phân tích các khu vực: Trang chủ, Danh mục sản phẩm, Chi tiết sản phẩm, Tìm kiếm, Giỏ hàng..."

**Prompt 2 (Đề xuất giải pháp UI):**
> "Tôi đang thực hiện bài tập phát triển giao diện website TMĐT bằng HTML5 và CSS3. Tôi muốn cải tiến khu vực: Thẻ sản phẩm (Product Card). Hiện tại, thẻ đang bị chật chội do nhồi nhét quá nhiều nhãn, làm lu mờ giá cả... Hãy đề xuất: Bố cục, thành phần HTML, cách tổ chức CSS, hiển thị PC/Mobile..."

**Prompt 3 (Sinh mã nguồn):**
> "Dựa trên phương án đã thống nhất, hãy tạo một trang giao diện thương mại điện tử bằng HTML5 và CSS3. Yêu cầu: Giao diện có tiêu đề, tối thiểu 4 sản phẩm mẫu... Bố cục phù hợp PC/Mobile, không dùng framework hay backend. Giải thích cách chạy."

## 4. Kết quả AI đề xuất
- **Về phân tích:** AI chỉ ra điểm nghẽn quá tải nhận thức trên Trang chủ và Danh mục sản phẩm, đề xuất áp dụng Machine Learning cá nhân hóa giao diện và thêm thanh tiến trình (Progress bar) Freeship.
- **Về thiết kế:** AI đề xuất cấu trúc thẻ sản phẩm gồm 3 phần (Ảnh, Thông tin, Thao tác), gom các nhãn thừa thành Icon dạng Overlay đè lên ảnh.
- **Về mã nguồn:** Cung cấp bộ source HTML/CSS sạch, áp dụng CSS Variables để quản lý màu sắc, CSS Grid cho bố cục dạng lưới và quy tắc đặt tên BEM.

## 5. Kiểm tra và điều chỉnh
Tôi đã đối chiếu kết quả của AI và trực tiếp tinh chỉnh mã nguồn để hoàn thiện sản phẩm:
- **Loại bỏ ý kiến sai của AI:** Tôi bác bỏ đề xuất "Dùng AI cá nhân hóa trang chủ" hay "Visual Search" vì đây là các tính năng Backend vượt quá phạm vi bài tập. Tôi tự bổ sung các lỗi thực tế mình quan sát được (như widget chat che khuất banner, nhãn đè quá nhiều).
- **Sửa lỗi đường dẫn:** Trong file `index.html` AI cung cấp, thẻ link CSS bị sai đường dẫn. Tôi đã tự sửa lại thành `<link rel="stylesheet" href="css/style.css">` để trang web nhận diện đúng màu sắc.
- **Điều chỉnh UI/UX:** Tôi đã truy cập file `style.css` và chủ động thay đổi mã màu tại biến `:root` (`--primary-color`) để giao diện trông nổi bật và mang dấu ấn cá nhân hơn, thay vì dùng màu mặc định AI cấp.
- **Kiểm thử Responsive:** Sử dụng tính năng Inspect (F12) của trình duyệt, tôi đã kiểm tra và xác nhận lưới sản phẩm tự động chuyển từ 4 cột (PC) xuống 2 cột (Mobile) một cách chính xác.

## 6. Phần tôi hiểu và có thể giải thích
Qua việc trực tiếp điều chỉnh mã nguồn AI cấp, tôi đã nắm vững các kiến thức sau:
1. **Quy tắc BEM:** Hiểu cách đặt tên class theo Block-Element-Modifier (VD: `.product-card`, `.product-card__title`, `.badge--discount`) giúp CSS không bị xung đột.
2. **CSS Variables (`:root`):** Biết cách khai báo và tái sử dụng biến màu sắc (VD: `var(--primary-color)`), giúp việc đổi màu toàn bộ website chỉ tốn 1 giây.
3. **Line-clamp (Cắt chữ):** Hiểu được tác dụng của thuộc tính `-webkit-line-clamp: 2;` kết hợp với `overflow: hidden;`. Nó giúp tên sản phẩm dù dài đến đâu cũng bị cắt gọt lại thành dấu "...", đảm bảo các thẻ sản phẩm luôn cao bằng nhau và không làm vỡ bố cục.
4. **Media Queries:** Nắm được logic sử dụng `@media (max-width: 768px)` để can thiệp cấu trúc Grid, phục vụ việc hiển thị giao diện thân thiện cho màn hình điện thoại.
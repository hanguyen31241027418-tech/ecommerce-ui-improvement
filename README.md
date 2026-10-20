# E-commerce UI Improvement

## 1. Giới thiệu
Dự án tập trung vào việc thiết kế và cải tiến lại giao diện **Thẻ sản phẩm (Product Card)** để giải quyết tình trạng nhồi nhét quá nhiều nhãn/tag gây rối mắt, đồng thời tối ưu hóa bố cục để trải nghiệm mua sắm trên thiết bị di động và máy tính được mượt mà, rõ ràng hơn.

## 2. Website tham khảo
- **Tên website:** Tiki
- **URL:** https://tiki.vn
- **Khu vực đã khảo sát:** Trang chủ, Danh mục sản phẩm, Chi tiết sản phẩm, Tìm kiếm, Giỏ hàng.

### Bảng khảo sát giao diện và chức năng:
| Khu vực | Chức năng đang cung cấp | Điểm hợp lý (Tốt) | Điểm cần cải thiện (Chưa tốt) | Đề xuất cải tiến & Lý do |
| :--- | :--- | :--- | :--- | :--- |
| **Trang chủ** | Banner khuyến mãi, slider, chọn địa chỉ giao hàng, menu icon tiện ích. | Chính sách cam kết rõ ràng, chọn địa chỉ ngay header tính phí chính xác. | Widget trợ lý/chat che khuất nội dung, mật độ ưu đãi quá dày đặc gây rối mắt. | **Đề xuất:** Thu gọn widget chat; tinh giản banner.<br>**Lý do:** Giảm tải nhận thức, giúp khách hàng dễ tập trung. |
| **Danh mục sản phẩm** | Phân loại danh mục đa cấp, bộ lọc tag (Giao 2H, Freeship), hiển thị thẻ sản phẩm. | Bộ lọc chi tiết giúp tìm kiếm nhanh, thẻ sản phẩm hiển thị đầy đủ thông tin. | Sản phẩm AD (quảng cáo) chiếm ưu thế, thẻ sản phẩm bị chật chội do quá nhiều nhãn. | **Đề xuất:** Tối giản và gom nhóm nhãn (tags) bằng icon nhỏ gọn.<br>**Lý do:** Giúp thẻ sản phẩm thoáng đãng, dễ nhìn thông tin cốt lõi (Giá). |
| **Chi tiết sản phẩm** | Ảnh, thông số, mô tả, đánh giá, tính phí ship, CTA đặt hàng. | Khối mua hàng cố định gọn gàng, hiển thị minh bạch phí và thời gian giao hàng. | Xuất hiện các banner quảng cáo phụ nằm chèn ngay dưới khu vực CTA mua hàng. | **Đề xuất:** Dời/xóa banner quảng cáo phụ khỏi khu CTA.<br>**Lý do:** Tránh phân tán sự chú ý ở bước quyết định cuối. |
| **Tìm kiếm** | Ô nhập từ khóa, gợi ý thông minh, lịch sử tìm kiếm, xu hướng. | Gợi ý tìm kiếm thông minh kèm hình ảnh, có icon các ngành hàng nổi bật. | Pop-up tìm kiếm đè (overlay) quá lớn, che lấp toàn bộ nội dung phía dưới trang. | **Đề xuất:** Giới hạn chiều cao pop-up hoặc thiết kế vùng phủ mờ tinh tế hơn.<br>**Lý do:** Không làm đứt gãy mạch trải nghiệm không gian web. |
| **Giỏ hàng** | Danh sách sản phẩm, tính tổng tiền, áp mã giảm giá, cảnh báo địa chỉ. | Tách rõ tiền gốc/giảm, khối chọn mã giảm giá cực tiện lợi (chỉ cần ấn chọn). | Bố cục bên trái dư quá nhiều khoảng trắng khi giỏ hàng chỉ có 1-2 món. | **Đề xuất:** Tận dụng khoảng trắng để hiển thị "Sản phẩm gợi ý mua kèm".<br>**Lý do:** Tối ưu không gian và tăng cơ hội bán chéo (Cross-sell). |

## 3. Chức năng
- Hiển thị danh sách sản phẩm theo dạng Lưới (Grid).
- Thẻ sản phẩm hiển thị đầy đủ: Ảnh, Nhãn giảm giá, Tên sản phẩm, Đánh giá, Giá bán, Giá gốc và Nút thao tác.
- Tự động thay đổi số lượng cột sản phẩm dựa trên kích thước màn hình (Responsive).
- Giới hạn chiều dài tên sản phẩm (tối đa 2 dòng) để giữ form giao diện luôn đồng đều.

## 4. Công nghệ
- HTML5 (Cấu trúc thẻ Semantic BEM)
- CSS3 (CSS Variables, Flexbox, CSS Grid)

## 5. Cách chạy
1. Clone hoặc tải mã nguồn về máy tính.
2. Mở file `index.html` bằng bất kỳ trình duyệt web nào (Chrome, Edge, Safari...).

## 6. Cải tiến đã thực hiện
- **Vấn đề ban đầu:** Thẻ sản phẩm của Tiki đang bị chật chội do hiển thị quá nhiều text/nhãn phụ (Freeship Xtra, Giao siêu tốc, Rẻ hơn hoàn tiền...), làm lu mờ mức giá trị cốt lõi là Giá bán và Nút mua hàng.
- **Giải pháp cải tiến:** 
  - Thiết lập lại hệ thống phân cấp thị
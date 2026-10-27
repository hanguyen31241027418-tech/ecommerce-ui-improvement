# BÁO CÁO BÀI TẬP CÁ NHÂN - BUỔI 2: HTML5 & CSS3

- **Họ tên sinh viên:** Nguyễn Thanh Hà
- **Môn học:** Phát triển ứng dụng Thương mại điện tử
- **Giảng viên hướng dẫn:** TS. Nguyễn Mạnh Tuấn
- **Thương hiệu website:** ShopNhanh (Phát triển tiếp nối từ sản phẩm Buổi 1)

---

## 1. GIỚI THIỆU BÀI TẬP & PHẠM VI CẢI THIỆN
Bài tập cá nhân Buổi 2 tập trung vào việc kế thừa mã nguồn Buổi 1, củng cố cấu trúc Semantic HTML5, ứng dụng CSS Box Model, và áp dụng hai kỹ thuật bố cục hiện đại: **Flexbox** (cho Header/Menu) và **CSS Grid** (cho Danh sách sản phẩm 4 cột).

- **Khu vực tập trung thực hành:**
  - Phần đầu trang (`<header>`, `<nav>`) và Menu điều hướng.
  - Khung nội dung chính (`<main>`, `<section>`).
  - Danh sách sản phẩm 4 cột (`.product-grid`) và Thẻ sản phẩm chi tiết (`.product-card`).

---

## 2. BƯỚC 1: RÀ SOÁT BÀI BUỔI 1 VÀ XÁC ĐỊNH NỘI DUNG CẦN CẢI THIỆN

### 2.1 Thành phần HTML đã có từ Buổi 1
- Đã sử dụng thẻ `<article>` cho từng phần tử sản phẩm độc lập.
- Sử dụng `<img>` để hiển thị hình ảnh và các thẻ văn bản `<strong>`, `<del>` để làm nổi bật giá bán / giá cũ.
- Sử dụng thẻ `<button>` cho hành động "Thêm vào giỏ".

### 2.2 Thành phần HTML còn thiếu hoặc chưa hợp lý
- Trang bị lạm dụng các thẻ `<div>` không ngữ nghĩa cho các khu vực bố cục chính.
- Thứ bậc tiêu đề (Heading Hierarchy) chưa đúng: Thẻ Logo sử dụng `<h2>` đặt trước `<h1>`, tiêu đề sản phẩm nhảy từ `<h1>` xuống thẳng `<h3>`.
- Menu điều hướng chỉ là các thẻ `<a>` nằm rời rạc, chưa đưa vào cấu trúc danh sách `<ul>`, `<li>`.
- Tiêu đề sản phẩm chưa có thẻ `<a>` để dẫn đến trang chi tiết.

### 2.3 Bảng phân tích vấn đề và đề xuất cải thiện

| Vấn đề phát hiện | Hướng cải thiện bằng HTML5 & CSS3 | Kết quả mong muốn |
| :--- | :--- | :--- |
| **Cấu trúc trang chưa phân chia ngữ nghĩa** | Thay `<div class="container">` bằng `<main>`, bọc khu vực sản phẩm bằng `<section>`, bổ sung `<header>`. | Mã nguồn chuẩn Semantic HTML5, tối ưu khả năng truy cập và SEO. |
| **Thứ bậc tiêu đề (Heading Hierarchy) bị sai** | Đổi Logo từ `<h2>` thành liên kết `<a>`, nâng tiêu đề sản phẩm từ `<h3>` lên `<h2>`. | Trình đọc màn hình và công cụ kiểm tra tài liệu đọc đúng cấu trúc. |
| **Menu là các liên kết rời rạc** | Bọc các liên kết menu điều hướng trong cấu trúc `<ul>` và `<li>`. | Mã nguồn ngăn nắp, thể hiện đúng ngữ nghĩa danh sách điều hướng. |
| **Tên sản phẩm chưa có liên kết** | Bọc tiêu đề sản phẩm trong thẻ `<a href="#">`. | Đảm bảo tính năng điều hướng chuẩn của website TMĐT. |
| **Thẻ sản phẩm bị dính liền, chưa có bố cục** | Áp dụng CSS Box Model (`padding`, `margin`, `border`, `border-radius`) và CSS Grid. | Sản phẩm dàn 4 cột đều đặn, khoảng cách trực quan, dễ quan sát. |
| **Nút thao tác chưa có phản hồi thị giác** | Bổ sung `:hover` (đổi màu nền) và `:focus-visible` (viền nổi bật). | Tăng trải nghiệm người dùng (UX) khi dùng chuột hoặc bàn phím (Tab). |

### 2.4 Thứ tự thực hiện các cải tiến
1. **Chuẩn hóa HTML5 Semantic:** Sửa cấu trúc khung tài liệu, điều chỉnh thứ bậc tiêu đề và bọc lại menu/liên kết tên sản phẩm.
2. **Xây dựng bố cục CSS (Flexbox & Grid):** Dàn hàng ngang Header bằng Flexbox và chia danh sách sản phẩm thành lưới 4 cột bằng Grid.
3. **Hoàn thiện chi tiết & Trợ năng:** Thêm hiệu ứng `:hover`, `:focus-visible` và các thuộc tính `aria-label`.

---

## 3. BƯỚC 2: CỦNG CỐ CẤU TRÚC HTML5 CÓ NGỮ NGHĨA

### 3.1 Mã nguồn HTML hoàn chỉnh (`index.html`)

```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ShopNhanh - Gợi ý hôm nay</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <header class="site-header">
        <a href="#" class="logo">ShopNhanh</a>
        <nav class="nav-menu" aria-label="Menu chính">
            <ul>
                <li><a href="#">Trang chủ</a></li>
                <li><a href="#">Sản phẩm</a></li>
                <li><a href="#">Giỏ hàng</a></li>
            </ul>
        </nav>
    </header>

    <main class="container">
        <h1 class="page-title" id="suggest-title">Gợi ý hôm nay</h1>
        
        <section class="product-grid" aria-labelledby="suggest-title">
            
            <!-- Sản phẩm 1 -->
            <article class="product-card">
                <div class="product-card__image-wrapper">
                    <span class="badge badge--mall">Mall</span>
                    <span class="badge badge--discount">-30%</span>
                    <img src="https://placehold.co/400x400/eeeeee/333333?text=Tai+nghe+Bluetooth" alt="Tai nghe Bluetooth Không Dây" class="product-card__image">
                </div>
                <div class="product-card__content">
                    <h2 class="product-card__title">
                        <a href="#">Tai nghe Bluetooth Không Dây Chống Ồn Chủ Động Cao Cấp Thế Hệ Mới</a>
                    </h2>
                    <div class="product-card__meta">
                        <span class="rating" role="img" aria-label="Đánh giá 5 trên 5 sao">⭐⭐⭐⭐⭐</span>
                        <span class="sold">Đã bán 1.2k</span>
                    </div>
                    <span class="tag-outline">Giao siêu tốc 2h</span>
                </div>
                <div class="product-card__action">
                    <div class="product-card__price-group">
                        <strong class="price price--current">350.000 ₫</strong>
                        <del class="price price--old">500.000 ₫</del>
                    </div>
                    <button type="button" class="btn btn--add-to-cart" aria-label="Thêm Tai nghe Bluetooth vào giỏ">Thêm vào giỏ</button>
                </div>
            </article>

            <!-- Sản phẩm 2 -->
            <article class="product-card">
                <div class="product-card__image-wrapper">
                    <span class="badge badge--authentic">Chính hãng</span>
                    <img src="https://placehold.co/400x400/eeeeee/333333?text=Chuot+Khong+Day" alt="Chuột Không Dây Logitech" class="product-card__image">
                </div>
                <div class="product-card__content">
                    <h2 class="product-card__title">
                        <a href="#">Chuột Không Dây Logitech Silent Nhỏ Gọn Phù Hợp Văn Phòng</a>
                    </h2>
                    <div class="product-card__meta">
                        <span class="rating" role="img" aria-label="Đánh giá 4 trên 5 sao">⭐⭐⭐⭐</span>
                        <span class="sold">Đã bán 850</span>
                    </div>
                </div>
                <div class="product-card__action">
                    <div class="product-card__price-group">
                        <strong class="price price--current">220.000 ₫</strong>
                    </div>
                    <button type="button" class="btn btn--add-to-cart" aria-label="Thêm Chuột Không Dây vào giỏ">Thêm vào giỏ</button>
                </div>
            </article>

            <!-- Sản phẩm 3 -->
            <article class="product-card">
                <div class="product-card__image-wrapper">
                    <span class="badge badge--discount">-15%</span>
                    <img src="https://placehold.co/400x400/eeeeee/333333?text=Ban+Phim+Co" alt="Bàn phím cơ" class="product-card__image">
                </div>
                <div class="product-card__content">
                    <h2 class="product-card__title">
                        <a href="#">Bàn phím cơ Gaming LED RGB Nhiều Chế Độ Trục Quang Học</a>
                    </h2>
                    <div class="product-card__meta">
                        <span class="rating" role="img" aria-label="Đánh giá 5 trên 5 sao">⭐⭐⭐⭐⭐</span>
                        <span class="sold">Đã bán 3.4k</span>
                    </div>
                    <span class="tag-outline">Freeship Extra</span>
                </div>
                <div class="product-card__action">
                    <div class="product-card__price-group">
                        <strong class="price price--current">850.000 ₫</strong>
                        <del class="price price--old">1.000.000 ₫</del>
                    </div>
                    <button type="button" class="btn btn--add-to-cart" aria-label="Thêm Bàn phím cơ vào giỏ">Thêm vào giỏ</button>
                </div>
            </article>

            <!-- Sản phẩm 4 -->
            <article class="product-card">
                <div class="product-card__image-wrapper">
                    <span class="badge badge--mall">Mall</span>
                    <span class="badge badge--discount">-50%</span>
                    <img src="https://placehold.co/400x400/eeeeee/333333?text=Balo+Laptop" alt="Balo Laptop" class="product-card__image">
                </div>
                <div class="product-card__content">
                    <h2 class="product-card__title">
                        <a href="#">Balo Laptop 15.6 inch Chống Nước Ngăn Chứa Rộng Rãi Thời Trang</a>
                    </h2>
                    <div class="product-card__meta">
                        <span class="rating" role="img" aria-label="Đánh giá 4 trên 5 sao">⭐⭐⭐⭐</span>
                        <span class="sold">Đã bán 450</span>
                    </div>
                </div>
                <div class="product-card__action">
                    <div class="product-card__price-group">
                        <strong class="price price--current">199.000 ₫</strong>
                        <del class="price price--old">398.000 ₫</del>
                    </div>
                    <button type="button" class="btn btn--add-to-cart" aria-label="Thêm Balo Laptop vào giỏ">Thêm vào giỏ</button>
                </div>
            </article>

        </section>
    </main>
</body>
</html>
```

### 3.2 Giải thích 3 phần tử HTML5 trọng tâm
1. **`<article>`:** Đại diện cho một đơn vị nội dung độc lập. Mỗi thẻ sản phẩm là một `<article>` chứa trọn vẹn hình ảnh, tiêu đề, đánh giá, giá cả và nút mua hàng. Nếu tách thẻ này ra đặt ở một trang khác thì thông tin vẫn có nghĩa hoàn chỉnh.
2. **`<nav>`:** Xác định vùng chứa các liên kết điều hướng chính của website. Giúp trình đọc màn hình và công cụ tìm kiếm nhận diện khu vực điều hướng nhanh chóng.
3. **`<h2>` (Tên sản phẩm):** Được sử dụng để tạo thứ bậc tiêu đề chuẩn mực ngay bên dưới tiêu đề trang `<h1>` ("Gợi ý hôm nay"), giúp trình đọc màn hình tạo Outline tài liệu chính xác.

---

## 4. BƯỚC 3 ĐẾN BƯỚC 7: MÃ CSS HOÀN CHỈNH (`css/style.css`)

```css
/* --- BƯỚC 3: BIẾN CSS & CÀI ĐẶT CHUNG --- */
:root {
    --primary-color: #0B74E5;
    --primary-hover: #0a65c9;
    --red-price: #FF424E;
    --text-main: #38383D;
    --text-gray: #808089;
    --bg-gray: #F5F5FA;
    --border-radius-sm: 4px;
    --border-radius-md: 8px;
    --spacing-sm: 8px;
    --spacing-md: 12px;
}

* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
}

body {
    background-color: var(--bg-gray);
    color: var(--text-main);
    line-height: 1.5;
}

.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 24px 16px;
}

.page-title {
    font-size: 24px;
    margin-bottom: 20px;
    color: var(--text-main);
}

/* --- BƯỚC 5: THỰC HÀNH FLEXBOX CHO HEADER & MENU --- */
.site-header {
    display: flex;
    justify-content: space-between; /* Đẩy Logo sang trái, Menu sang phải */
    align-items: center; /* Căn giữa các mục theo chiều dọc */
    background-color: #ffffff;
    padding: 16px 32px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.06);
    margin-bottom: 24px;
    border-radius: 8px;
}

.logo {
    color: var(--primary-color);
    font-size: 22px;
    font-weight: 700;
    text-decoration: none;
}

.nav-menu ul {
    display: flex; /* Dàn ngang các thẻ li trong menu */
    gap: 28px; /* Khoảng cách giữa các mục liên kết */
    list-style: none; /* Xóa dấu chấm tròn danh sách */
    margin: 0;
    padding: 0;
}

.nav-menu a {
    text-decoration: none !important;
    color: var(--text-main);
    font-weight: 500;
    font-size: 15px;
    padding: 6px 12px;
    border-radius: 4px;
    transition: all 0.2s ease;
}

.nav-menu a:hover {
    color: var(--primary-color);
    background-color: #f0f8ff;
}

/* --- BƯỚC 6: THỰC HÀNH CSS GRID CHO DANH SÁCH SẢN PHẨM --- */
.product-grid {
    display: grid;
    grid-template-columns: repeat(4, minmax(0, 1fr)); /* Dàn 4 cột bằng nhau */
    gap: 16px; /* Khoảng cách giữa các phần tử lưới */
}

/* --- BƯỚC 4: THỰC HÀNH BOX MODEL CHO THẺ SẢN PHẨM --- */
.product-card {
    background-color: #ffffff;
    border-radius: var(--border-radius-md);
    overflow: hidden;
    display: flex;
    flex-direction: column;
    height: 100%;
    border: 1px solid #ebebf0;
    transition: transform 0.2s, box-shadow 0.2s;
}

.product-card:hover {
    box-shadow: 0 4px 16px rgba(0, 0, 0, 0.1);
    transform: translateY(-2px);
}

.product-card__image-wrapper {
    position: relative;
    width: 100%;
    aspect-ratio: 1 / 1;
    overflow: hidden;
}

.product-card__image {
    width: 100%;
    height: 100%;
    object-fit: cover; /* Đảm bảo hình ảnh vuông vắn, không bị giật méo */
}

.badge {
    position: absolute;
    font-size: 11px;
    font-weight: 600;
    padding: 2px 6px;
    border-radius: var(--border-radius-sm);
    z-index: 1;
}

.badge--mall {
    top: var(--spacing-sm);
    left: var(--spacing-sm);
    background-color: #ffc107;
    color: #333;
}

.badge--authentic {
    top: var(--spacing-sm);
    left: var(--spacing-sm);
    background-color: var(--primary-color);
    color: #fff;
}

.badge--discount {
    top: var(--spacing-sm);
    right: var(--spacing-sm);
    background-color: var(--red-price);
    color: #fff;
}

.product-card__content {
    padding: var(--spacing-md);
    flex-grow: 1;
}

.product-card__title {
    font-size: 14px;
    font-weight: 400;
    margin-bottom: 8px;
    display: -webkit-box;
    -webkit-line-clamp: 2; /* Giới hạn hiển thị 2 dòng tiêu đề */
    -webkit-box-orient: vertical;
    overflow: hidden;
    text-overflow: ellipsis;
    min-height: 42px;
}

.product-card__title a {
    text-decoration: none;
    color: var(--text-main);
}

.product-card__title a:hover {
    color: var(--primary-color);
}

.product-card__meta {
    display: flex;
    align-items: center;
    gap: 8px;
    font-size: 12px;
    color: var(--text-gray);
    margin-bottom: 8px;
}

.tag-outline {
    display: inline-block;
    font-size: 10px;
    color: var(--primary-color);
    border: 1px solid var(--primary-color);
    padding: 2px 4px;
    border-radius: 4px;
}

.product-card__action {
    padding: 0 var(--spacing-md) var(--spacing-md);
    margin-top: auto;
}

.product-card__price-group {
    display: flex;
    flex-direction: column;
    margin-bottom: 12px;
}

.price--current {
    font-size: 18px;
    color: var(--red-price);
    font-weight: 600;
}

.price--old {
    font-size: 12px;
    color: var(--text-gray);
    text-decoration: line-through;
}

/* --- BƯỚC 7: NÚT BẤM & HIỆU ỨNG HOVER / FOCUS-VISIBLE --- */
.btn--add-to-cart {
    width: 100%;
    background-color: white;
    color: var(--primary-color);
    border: 1px solid var(--primary-color);
    padding: 10px;
    border-radius: var(--border-radius-sm);
    font-size: 14px;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.2s ease;
    min-height: 44px; /* Chuẩn Touch Target cho thiết bị cảm ứng */
}

.product-card:hover .btn--add-to-cart {
    background-color: var(--primary-color);
    color: white;
}

.btn--add-to-cart:focus-visible {
    outline: 3px solid #f59e0b;
    outline-offset: 2px;
}

/* --- RESPONSIVE MEDIA QUERIES --- */
@media (max-width: 992px) {
    .product-grid {
        grid-template-columns: repeat(3, 1fr);
    }
}

@media (max-width: 768px) {
    .product-grid {
        grid-template-columns: repeat(2, 1fr);
        gap: 12px;
    }
    .btn--add-to-cart {
        background-color: var(--primary-color);
        color: white;
    }
}
```

---

## 5. BƯỚC 8: BẢNG KIỂM THỬ GIAO DIỆN (TESTING CHECKLIST)

| STT | Nội dung kiểm tra | Kết quả | Ghi chú & Cách khắc phục |
| :--- | :--- | :--- | :--- |
| **1** | Trang HTML mở thành công trên trình duyệt | **Đạt** | Chạy tốt thông qua extension Live Server trên VS Code. |
| **2** | Tệp CSS được liên kết chính xác | **Đạt** | Đường dẫn `css/style.css` hoạt động chuẩn, nhận giao diện màu sắc và font chữ. |
| **3** | Hình ảnh sản phẩm hiển thị đúng tỷ lệ | **Đạt** | Áp dụng `object-fit: cover` kết hợp `aspect-ratio: 1/1` giúp ảnh không giật méo. |
| **4** | Các thẻ liên kết (`<a>`) hoạt động ổn định | **Đạt** | Menu và tiêu đề sản phẩm có phản hồi thị giác tốt khi di chuột. |
| **5** | Bố cục không bị vỡ hoặc tràn ngang | **Đạt** | Đã cấu hình `box-sizing: border-box` toàn cục và Flexbox/Grid chuẩn. |
| **6** | Hiệu ứng Hover và Focus hoạt động | **Đạt** | Nút "Thêm vào giỏ" đổi màu xanh khi rê chuột, hiện viền cam khi Tab phím. |
| **7** | Tự sửa ít nhất một vấn đề | **Đạt** | Sửa đường dẫn link CSS trong HTML và điều chỉnh gạch chân thẻ liên kết `<a>`. |

---

## 6. CÂU HỎI KIỂM TRA KIẾN THỨC (PHẦN 12)

### Câu 1. Trong khu vực giao diện của em, em đã sử dụng những phần tử HTML5 nào? Vì sao em chọn chúng?
**Trả lời:** Em đã sử dụng các phần tử ngữ nghĩa bao gồm `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<h2>`, `<a>`, `<button>`, `<strong>`, và `<del>`. Em chọn chúng vì muốn tuân thủ chuẩn Semantic HTML5, giúp cấu trúc tài liệu rõ ràng, dễ bảo trì, tối ưu SEO và hỗ trợ tốt cho các thiết bị hỗ trợ trợ năng (Screen Readers).

### Câu 2. Giải thích sự khác nhau giữa margin và padding. Cho ví dụ từ thẻ sản phẩm của em.
**Trả lời:**
- `padding` là khoảng cách đệm bên trong (khoảng trống từ nội dung đến đường viền phần tử).
- `margin` là khoảng cách lề bên ngoài (khoảng trống từ đường viền phần tử đến các phần tử lân cận).
- *Ví dụ:* Trong `.product-card__content`, em dùng `padding: 12px` để đẩy chữ cách viền thẻ 12px. Trong `.site-header`, em dùng `margin-bottom: 24px` để tách biệt Header khỏi vùng nội dung phía dưới.

### Câu 3. Trong bài của em, Flexbox được sử dụng ở đâu? Giải thích tác dụng của justify-content và align-items.
**Trả lời:** Flexbox được áp dụng ở phần `.site-header` và menu `.nav-menu ul`.
- `justify-content: space-between`: Đẩy Logo sát lề trái và Menu sát lề phải của Header.
- `align-items: center`: Căn các phần tử con thẳng hàng với nhau theo chiều dọc (trục phụ).

### Câu 4. CSS Grid khác Flexbox như thế nào? Vì sao em sử dụng Grid cho danh sách sản phẩm?
**Trả lời:**
- Flexbox là hệ thống bố cục 1 chiều (chỉ xử lý theo hàng hoặc cột tại một thời điểm).
- CSS Grid là hệ thống bố cục 2 chiều (quản lý đồng thời cả hàng và cột).
- Em sử dụng CSS Grid cho danh sách sản phẩm (`.product-grid`) vì nó cho phép định hình lưới 4 cột cố định (`repeat(4, 1fr)`) đồng đều và tự động quản lý khoảng cách `gap` chuẩn xác.

### Câu 5. Nếu xóa quy tắc CSS display: grid khỏi danh sách sản phẩm, giao diện có thể thay đổi như thế nào?
**Trả lời:** Nếu xóa `display: grid`, các thẻ sản phẩm (`<article>`) sẽ mất cấu trúc dạng lưới và quay trở lại dạng khối (`block`) mặc định, bị đẩy xếp chồng lên nhau thành một cột dọc duy nhất.

### Câu 6. Vì sao cần sử dụng thuộc tính alt cho hình ảnh sản phẩm?
**Trả lời:** Thuộc tính `alt` cung cấp văn bản mô tả thay thế khi hình ảnh gặp lỗi không tải được. Nó giúp các công cụ tìm kiếm index hình ảnh (SEO) và giúp trình đọc màn hình đọc nội dung mô tả ảnh cho người khiếm thị.

### Câu 7. Hãy nêu một đề xuất của AI mà em đã kiểm tra hoặc điều chỉnh trước khi đưa vào bài tập.
**Trả lời:** AI đề xuất bổ sung `role="img"` và `aria-label="Đánh giá 5 trên 5 sao"` cho chuỗi biểu tượng ngôi sao (`⭐⭐⭐⭐⭐`). Em đã kiểm tra lại và nhận thấy điều này rất cần thiết vì trình đọc màn hình sẽ đọc câu mô tả ngắn gọn thay vì đọc lặp lại ký tự "ngôi sao" 5 lần.

---

## 7. BÁO CÁO SỬ DỤNG AI (AI USAGE REPORT)

- **Công cụ AI sử dụng:** Gemini (Google).
- **Các prompt tiêu biểu đã sử dụng:**
  1. *"Tôi có mã HTML 4 thẻ sản phẩm. Hãy phân tích cấu trúc HTML5 ngữ nghĩa và chỉ ra các lỗi thứ bậc tiêu đề."*
  2. *"Hướng dẫn sử dụng Flexbox cho Header để Logo bên trái, Menu bên phải và CSS Grid dàn 4 cột danh sách sản phẩm."*
  3. *"Tư vấn cách viết CSS hover và focus-visible cho nút bấm mua hàng."*
- **Phần sinh viên tự kiểm tra & điều chỉnh:**
  - Đồng bộ tên thương hiệu thành **ShopNhanh**.
  - Tự kiểm tra và khắc phục lỗi đường dẫn CSS (`css/style.css`).
  - Tự bổ sung thêm các thuộc tính `:hover` chuyển màu nền nhạt cho các item trong Menu (`background-color: #f0f8ff`).

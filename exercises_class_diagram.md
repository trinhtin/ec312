
## Bài Tập 1: Hệ Thống Quản Lý Sản Phẩm Cơ Bản

**Yêu cầu:**
Thiết kế class diagram cho module quản lý sản phẩm với các yêu cầu:
- Sản phẩm có thông tin: mã, tên, mô tả, giá, số lượng tồn kho
- Sản phẩm được phân loại theo danh mục (Category)
- Mỗi danh mục có thể chứa nhiều danh mục con
- Sản phẩm có thể có nhiều hình ảnh
- Sản phẩm có thể có các biến thể (variants) như màu sắc, kích thước
- Mỗi biến thể có giá và số lượng riêng

**Gợi ý:** Cần các class Product, Category, ProductImage, ProductVariant, Attribute

---

## Bài Tập 2: Hệ Thống Đặt Hàng và Thanh Toán

**Yêu cầu:**
Thiết kế class diagram cho quy trình đặt hàng:
- Khách hàng có thể đặt nhiều đơn hàng
- Mỗi đơn hàng chứa nhiều sản phẩm với số lượng khác nhau
- Đơn hàng có các trạng thái: Chờ xác nhận, Đang xử lý, Đang giao, Hoàn thành, Đã hủy
- Mỗi đơn hàng có địa chỉ giao hàng
- Hỗ trợ nhiều phương thức thanh toán: COD, Thẻ tín dụng, Ví điện tử
- Lưu lịch sử thay đổi trạng thái đơn hàng

**Gợi ý:** Cần các class Order, OrderItem, OrderStatus, Payment, Address, Customer

---

## Bài Tập 3: Hệ Thống Giỏ Hàng và Khuyến Mãi

**Yêu cầu:**
Thiết kế class diagram cho giỏ hàng và chương trình khuyến mãi:
- Mỗi khách hàng có một giỏ hàng
- Giỏ hàng chứa các sản phẩm với số lượng
- Hỗ trợ mã giảm giá (coupon) với các loại: giảm theo %, giảm cố định, miễn phí ship
- Mã giảm giá có điều kiện áp dụng: giá trị đơn tối thiểu, sản phẩm cụ thể
- Có chương trình khuyến mãi tự động khi mua combo
- Tính tổng tiền sau khi áp dụng các khuyến mãi

**Gợi ý:** Cần các class Cart, CartItem, Coupon, Discount, Promotion, DiscountRule

---

## Bài Tập 4: Hệ Thống Đánh Giá và Nhận Xét

**Yêu cầu:**
Thiết kế class diagram cho module đánh giá sản phẩm:
- Khách hàng có thể đánh giá sản phẩm đã mua (1-5 sao)
- Mỗi đánh giá có nội dung text và hình ảnh kèm theo
- Khách hàng khác có thể thích (like) hoặc báo cáo đánh giá không phù hợp
- Shop có thể phản hồi đánh giá
- Hệ thống tính điểm đánh giá trung bình cho mỗi sản phẩm
- Có thể lọc đánh giá theo số sao, có hình ảnh

**Gợi ý:** Cần các class Review, ReviewImage, ReviewReply, ReviewLike, ReviewReport

---

## Bài Tập 5: Hệ Thống Người Dùng và Phân Quyền

**Yêu cầu:**
Thiết kế class diagram cho quản lý người dùng:
- Có 3 loại người dùng: Admin, Seller (người bán), Customer (khách hàng)
- Mỗi loại có quyền hạn khác nhau (permissions)
- Admin quản lý toàn bộ hệ thống
- Seller quản lý shop của mình (sản phẩm, đơn hàng)
- Customer xem và mua sản phẩm
- Một Seller có thể có nhiều shop
- Mỗi shop có thông tin: tên, mô tả, logo, địa chỉ
- Lưu lịch sử đăng nhập của người dùng

**Gợi ý:** Cần các class User, Admin, Seller, Customer, Shop, Role, Permission, LoginHistory

---

## Lưu Ý Khi Vẽ Class Diagram:

1. **Thể hiện rõ các mối quan hệ:**
   - Association (liên kết)
   - Aggregation (tập hợp)
   - Composition (hợp thành)
   - Inheritance (kế thừa)
   - Dependency (phụ thuộc)

2. **Ghi rõ multiplicity:** 1..1, 0..1, 1..*, 0..*, *

3. **Các thành phần của class:**
   - Attributes (thuộc tính) với kiểu dữ liệu
   - Methods (phương thức) với tham số và kiểu trả về
   - Visibility (+: public, -: private, #: protected)

4. **Áp dụng các design pattern phù hợp:** Strategy, Factory, Observer...


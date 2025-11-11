
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

---

## **Bài tập 6: Hệ thống TMĐT với nhiều loại người dùng và phân quyền**

**Gợi ý lớp:**

* `User` (lớp cha chung): `userId`, `username`, `password`, `email`; phương thức: `login()`, `logout()`.
* `Customer` kế thừa `User`: thêm `address`, `phoneNumber`, phương thức `browseProduct()`, `placeOrder()`, `writeReview()`.
* `Admin` kế thừa `User`: phương thức `manageUser()`, `manageProduct()`, `manageOrder()`.
* `WarehouseStaff` kế thừa `User`: phương thức `updateInventory()`, `processShipment()`.
* `Supplier` kế thừa `User`: phương thức `addProduct()`, `updateProduct()`.

**Gợi ý các lớp liên quan:**

* `Product`: `productId`, `name`, `price`, `description`, `stockQuantity`; phương thức `updateStock()`, `checkAvailability()`.
* `Order`: `orderId`, `orderDate`, `status`; phương thức `calculateTotal()`, `updateStatus()`.
* `Inventory`: `inventoryId`, `product`, `quantityAvailable`; phương thức `updateQuantity()`.

**Quan hệ:**

* Kế thừa: `Customer`, `Admin`, `WarehouseStaff`, `Supplier` từ `User`.
* Liên kết: `Customer` ↔ `Order`; `Order` ↔ `Product`; `WarehouseStaff` ↔ `Inventory`.

---

## **Bài tập 7: Hệ thống TMĐT tích hợp chương trình khuyến mãi phức tạp**

**Gợi ý lớp:**

* `Customer`: `customerId`, `name`, `email`; phương thức: `addToCart()`, `checkout()`.
* `Admin`: `adminId`, `name`; phương thức: `createPromotion()`, `updatePromotion()`, `deletePromotion()`.
* `Product`: `productId`, `name`, `price`, `stockQuantity`; phương thức `updateStock()`.
* `ShoppingCart`: `cartId`, danh sách sản phẩm, `totalAmount`; phương thức `addItem()`, `removeItem()`, `applyPromotion()`.
* `Order`: `orderId`, `orderDate`, `status`; phương thức `calculateTotal()`.
* `Promotion` / `Coupon`: `promotionId`, `discountPercent`, `discountAmount`, `expiryDate`; phương thức `applyPromotion()`.

**Quan hệ:**

* `Customer` ↔ `ShoppingCart` ↔ `Product`.
* `ShoppingCart` ↔ `Promotion` (có thể áp dụng nhiều loại).
* `Order` ↔ `Customer`; `Order` ↔ `Product`.

---

## **Bài tập 8: Hệ thống Marketplace với đánh giá và phân loại sản phẩm**

**Gợi ý lớp:**

* `Customer`: `customerId`, `name`, `email`; phương thức: `placeOrder()`, `writeReview()`.
* `Seller`: `sellerId`, `shopName`; phương thức: `addProduct()`, `updateProduct()`.
* `Product`: `productId`, `name`, `price`, `description`, `stockQuantity`; phương thức `updateStock()`.
* `Category`: `categoryId`, `categoryName`; phương thức `addProduct()`, `removeProduct()`.
* `Review`: `reviewId`, `rating`, `comment`; phương thức `submitReview()`.
* `Wishlist`: `wishlistId`, danh sách sản phẩm; phương thức `addProduct()`, `removeProduct()`.
* `Order`: `orderId`, `orderDate`, `status`; phương thức `calculateTotal()`.

**Quan hệ:**

* `Seller` ↔ `Product` (1-n)
* `Product` ↔ `Category` (n-n)
* `Customer` ↔ `Wishlist` (1-1)
* `Customer` ↔ `Review` ↔ `Product` (1-n, n-1)
* `Customer` ↔ `Order` ↔ `Product`

---

## **Bài tập 9: Hệ thống TMĐT quản lý kho và vận chuyển nâng cao**

**Gợi ý lớp:**

* `Customer`: `customerId`, `name`; phương thức `placeOrder()`.
* `Product`: `productId`, `name`, `stockQuantity`; phương thức `updateStock()`.
* `Inventory`: `inventoryId`, `product`, `quantityAvailable`; phương thức `updateQuantity()`.
* `Order`: `orderId`, `orderDate`, `status`; phương thức `calculateTotal()`, `splitShipment()`.
* `Shipment`: `shipmentId`, `shipmentDate`, `shippingMethod`, `status`; phương thức `shipOrder()`, `updateStatus()`.
* `WarehouseStaff`: `staffId`, `name`; phương thức `processShipment()`, `updateInventory()`.

**Quan hệ:**

* `Inventory` ↔ `Product` (1-1 hoặc 1-n)
* `Order` ↔ `Product` (n-n)
* `Order` ↔ `Shipment` (1-n)
* `WarehouseStaff` ↔ `Shipment` (1-n)

---

## **Bài tập 10: Hệ thống TMĐT đa kênh với lịch sử giao dịch**

**Gợi ý lớp:**

* `User` (lớp cha)
* `Customer` kế thừa `User`: phương thức `placeOrder()`, `viewTransactionHistory()`, `downloadInvoice()`.
* `Admin` kế thừa `User`: phương thức `generateReport()`, `analyzeSales()`.
* `Product`: `productId`, `name`, `price`, `stockQuantity`; phương thức `updateStock()`.
* `Order`: `orderId`, `orderDate`, `status`; phương thức `calculateTotal()`.
* `Payment`: `paymentId`, `amount`, `paymentMethod`; phương thức `processPayment()`.
* `TransactionHistory`: `transactionId`, `date`, `details`; phương thức `recordTransaction()`.

**Quan hệ:**

* `Customer` ↔ `Order` ↔ `Product`
* `Order` ↔ `Payment` (1-1)
* `Customer` ↔ `TransactionHistory` (1-n)
* `Admin` ↔ báo cáo doanh thu (không cần lưu lớp dữ liệu riêng, chỉ là hành vi)


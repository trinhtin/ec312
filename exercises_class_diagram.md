# **Bài Tập 1: Hệ Thống Quản Lý Sản Phẩm Cơ Bản (Basic Product Management System)**

**Yêu cầu / Requirements:**
Thiết kế class diagram cho module quản lý sản phẩm với các yêu cầu:
Design a class diagram for the product management module with the following requirements:

* Sản phẩm có thông tin: mã, tên, mô tả, giá, số lượng tồn kho
  A product has: ID, name, description, price, stock quantity
* Sản phẩm được phân loại theo danh mục (Category)
  Products are categorized by Category
* Mỗi danh mục có thể chứa nhiều danh mục con
  Each category can have multiple subcategories
* Sản phẩm có thể có nhiều hình ảnh
  A product can have multiple images
* Sản phẩm có thể có các biến thể (variants) như màu sắc, kích thước
  A product can have variants (color, size, etc.)
* Mỗi biến thể có giá và số lượng riêng
  Each variant has its own price and stock quantity

**Gợi ý / Hint:**
Cần các class / Required classes:
`Product`, `Category`, `ProductImage`, `ProductVariant`, `Attribute`

## **Mô tả mối quan hệ / Relationship Descriptions**

### **1. Association (Liên kết)**

* **Product – Category**:
  *Một sản phẩm thuộc một danh mục; một danh mục có nhiều sản phẩm.*
  *A product belongs to one category; a category contains many products.*

* **Product – ProductImage**:
  *Một sản phẩm có nhiều hình ảnh.*
  *A product can have multiple images.*

* **Product – ProductVariant**:
  *Một sản phẩm có nhiều biến thể.*
  *A product can have multiple variants.*

### **2. Aggregation (Tập hợp)**

* **Category – Subcategory**:
  *Danh mục chứa danh mục con nhưng có thể tồn tại độc lập.*
  *A category aggregates subcategories which can exist independently.*

### **3. Composition (Hợp thành)**

* **ProductVariant – Attribute**:
  *Biến thể được tạo thành bởi nhiều thuộc tính (màu, size), xoá biến thể thì thuộc tính không còn ý nghĩa.*
  *A variant is composed of attributes; if the variant is deleted, attributes lose meaning.*

### **4. Inheritance (Kế thừa)**

*(Bài này không bắt buộc kế thừa, nhưng sinh viên có thể mở rộng nếu muốn.)*

### **5. Dependency (Phụ thuộc)**

* **ProductVariant → StockQuantity**:
  *Biến thể phụ thuộc vào tồn kho để xác định trạng thái còn hàng.*
  *Variant depends on inventory to determine availability.*

---

# **Bài Tập 2: Hệ Thống Đặt Hàng và Thanh Toán (Order and Payment System)**

**Yêu cầu / Requirements:**
Thiết kế class diagram cho quy trình đặt hàng:
Design a class diagram for the ordering process:

* Khách hàng có thể đặt nhiều đơn hàng
  A customer can place multiple orders
* Mỗi đơn hàng chứa nhiều sản phẩm với số lượng khác nhau
  Each order contains multiple products with different quantities
* Đơn hàng có các trạng thái: Chờ xác nhận, Đang xử lý, Đang giao, Hoàn thành, Đã hủy
  Order statuses: Pending, Processing, Shipping, Completed, Cancelled
* Mỗi đơn hàng có địa chỉ giao hàng
  Each order has a shipping address
* Hỗ trợ nhiều phương thức thanh toán: COD, Thẻ tín dụng, Ví điện tử
  Supports multiple payment methods: COD, Credit Card, E-Wallet
* Lưu lịch sử thay đổi trạng thái đơn hàng
  Store order status change history

**Gợi ý / Hint:**
Cần các class / Required classes:
`Order`, `OrderItem`, `OrderStatus`, `Payment`, `Address`, `Customer`

## **Mô tả mối quan hệ / Relationship Descriptions**

### **1. Association**

* **Customer – Order**:
  *Một khách hàng có nhiều đơn hàng.*
  *A customer can place multiple orders.*

* **Order – OrderItem**:
  *Mỗi đơn hàng gồm nhiều dòng sản phẩm.*
  *An order contains many order items.*

* **OrderItem – Product**:
  *Mỗi item tham chiếu đến một sản phẩm.*
  *Each order item refers to one product.*

* **Order – Address**:
  *Mỗi đơn hàng có một địa chỉ giao hàng.*
  *Each order has a shipping address.*

* **Order – Payment**:
  *Mỗi đơn hàng có một phương thức thanh toán.*
  *Each order has one payment method.*

### **2. Aggregation**

* **Order – OrderStatusHistory**:
  *Lịch sử trạng thái thuộc về đơn hàng nhưng có thể tồn tại độc lập để audit.*
  *Order status history is aggregated by the order.*

### **3. Composition**

* **OrderStatusHistory – OrderStatus**:
  *Một bản ghi lịch sử luôn thuộc về một trạng thái cụ thể.*
  *Status history entry is tightly bound to a specific status.*

### **4. Inheritance**

* **Payment** → `CODPayment`, `CreditCardPayment`, `EWalletPayment`
  *Các loại thanh toán kế thừa từ Payment.*
  *Payment method subclasses extend the Payment class.*

### **5. Dependency**

* **Order → PaymentProcessor**:
  *Đơn hàng phụ thuộc vào xử lý thanh toán.*
  *Order depends on external payment processing.*

---

# **Bài Tập 3: Hệ Thống Giỏ Hàng và Khuyến Mãi (Shopping Cart and Promotion System)**

**Yêu cầu / Requirements:**
Thiết kế class diagram cho giỏ hàng và chương trình khuyến mãi:
Design a class diagram for shopping cart and promotions:

* Mỗi khách hàng có một giỏ hàng
  Each customer has one shopping cart
* Giỏ hàng chứa các sản phẩm với số lượng
  Cart contains items with quantities
* Hỗ trợ mã giảm giá (coupon): giảm %, giảm cố định, miễn phí ship
  Supports coupons: percentage discount, fixed amount, free shipping
* Mã giảm giá có điều kiện áp dụng: giá trị tối thiểu, sản phẩm áp dụng
  Coupons have conditions: minimum order value, specific applicable products
* Có chương trình khuyến mãi combo tự động
  Supports automatic combo promotions
* Tính tổng tiền sau khi áp dụng khuyến mãi
  Calculate final total after promotions

**Gợi ý / Hint:**
Cần các class / Required classes:
`Cart`, `CartItem`, `Coupon`, `Discount`, `Promotion`, `DiscountRule`

## **Mô tả mối quan hệ / Relationship Descriptions**

### **1. Association**

* **Customer – Cart**:
  *Mỗi khách hàng có một giỏ hàng.*
  *Each customer has one shopping cart.*

* **Cart – CartItem**:
  *Giỏ hàng chứa nhiều item.*
  *A cart has multiple cart items.*

* **CartItem – Product**:
  *Một item đại diện cho một sản phẩm.*
  *Cart item references a product.*

* **Coupon – DiscountRule**:
  *Mã giảm giá đi kèm các điều kiện áp dụng.*
  *A coupon has discount rules.*

### **2. Aggregation**

* **Promotion – Product**:
  *Chương trình khuyến mãi có thể áp dụng cho nhiều sản phẩm.*
  *A promotion applies to multiple products.*

### **3. Composition**

* **Coupon – Discount**:
  *Mỗi coupon chứa logic giảm giá của riêng nó.*
  *Each coupon is composed of its discount logic.*

### **4. Inheritance**

* **Discount** → `PercentDiscount`, `FixedAmountDiscount`, `FreeShippingDiscount`
  *Các loại giảm giá mở rộng từ Discount.*
  *Discount types inherit from Discount.*

### **5. Dependency**

* **Cart → PromotionEngine**:
  *Giỏ hàng phụ thuộc vào promotion engine để tính giá cuối.*
  *Cart depends on promotion engine to compute final total.*

---

# **Bài Tập 4: Hệ Thống Đánh Giá và Nhận Xét (Review and Rating System)**

**Yêu cầu / Requirements:**
Thiết kế class diagram cho module đánh giá sản phẩm:
Design a class diagram for the product review module:

* Khách hàng đánh giá sản phẩm đã mua (1–5 sao)
  Customers can rate purchased products (1–5 stars)
* Mỗi đánh giá có nội dung text và hình ảnh
  Each review has text content and optional images
* Khách hàng khác có thể thích (like) hoặc báo cáo (report) đánh giá
  Other customers can like or report reviews
* Shop có thể phản hồi đánh giá
  Seller can reply to reviews
* Hệ thống tính điểm đánh giá trung bình
  System calculates average rating per product
* Có thể lọc theo số sao hoặc có hình ảnh
  Reviews can be filtered by star rating or image availability

**Gợi ý / Hint:**
Cần các class / Required classes:
`Review`, `ReviewImage`, `ReviewReply`, `ReviewLike`, `ReviewReport`

## **Mô tả mối quan hệ / Relationship Descriptions**

### **1. Association**

* **Customer – Review**:
  *Khách hàng viết nhiều review.*
  *A customer writes many reviews.*

* **Review – Product**:
  *Review thuộc về sản phẩm đã mua.*
  *Reviews belong to purchased products.*

* **Review – ReviewImage**:
  *Review có nhiều ảnh minh họa.*
  *A review can contain multiple images.*

* **Review – ReviewLike / ReviewReport**:
  *Người dùng khác có thể like hoặc report review.*
  *Other users may like or report reviews.*

* **Review – ReviewReply**:
  *Shop có thể phản hồi review.*
  *Sellers can reply to reviews.*

### **2. Aggregation**

* **Product – Review**:
  *Review là tập hợp của sản phẩm nhưng tồn tại độc lập.*
  *Reviews are aggregated under the product.*

### **3. Composition**

* **Review – ReviewImage**:
  *Ảnh thuộc về review, xoá review mất ảnh.*
  *Images exist only as part of reviews.*

### **4. Inheritance**

* Có thể mở rộng:
  `UserAction` → `ReviewLike`, `ReviewReport`
  *Các hành động người dùng có thể kế thừa từ một lớp cha.*
  *User actions can inherit from a parent class.*

### **5. Dependency**

* **Review → RatingCalculator**:
  *Hệ thống đánh giá phụ thuộc vào bộ tính toán điểm.*
  *Review system depends on rating calculator.*
  
---

# **Bài Tập 5: Hệ Thống Người Dùng và Phân Quyền (User Management and Role-Based Access Control)**

**Yêu cầu / Requirements:**
Thiết kế class diagram cho quản lý người dùng:
Design a class diagram for user management:

* Có 3 loại người dùng: Admin, Seller, Customer
  There are 3 user types: Admin, Seller, Customer
* Mỗi loại có quyền hạn khác nhau
  Each type has different permissions
* Admin quản lý toàn bộ hệ thống
  Admin manages the entire system
* Seller quản lý shop của mình (sản phẩm, đơn hàng)
  Seller manages their shop (products, orders)
* Customer xem và mua sản phẩm
  Customer browses and purchases products
* Một Seller có nhiều shop
  A seller can have multiple shops
* Mỗi shop có: tên, mô tả, logo, địa chỉ
  Each shop has: name, description, logo, address
* Lưu lịch sử đăng nhập
  Store user login history

**Gợi ý / Hint:**
Cần các class / Required classes:
`User`, `Admin`, `Seller`, `Customer`, `Shop`, `Role`, `Permission`, `LoginHistory`

## **Mô tả mối quan hệ / Relationship Descriptions**

### **1. Association**

* **User – LoginHistory**:
  *Người dùng có nhiều bản ghi đăng nhập.*
  *User has multiple login history records.*

* **Seller – Shop**:
  *Một seller có nhiều shop.*
  *A seller manages multiple shops.*

* **Shop – Address**:
  *Shop có một địa chỉ.*
  *A shop has one address.*

* **Role – Permission**:
  *Role được gán nhiều quyền.*
  *A role has multiple permissions.*

* **User – Role**:
  *Người dùng được gán 1 hoặc nhiều role.*
  *A user can have one or multiple roles.*

### **2. Aggregation**

* **Shop – Product**:
  *Sản phẩm thuộc shop nhưng nếu xóa shop sản phẩm có thể được chuyển sang shop khác.*
  *Products belong to shop but can exist independently.*

### **3. Composition**

* **Shop – ShopProfile** (logo, mô tả):
  *Shop sở hữu profile, xoá shop thì profile mất.*
  *A shop is composed of its profile.*

### **4. Inheritance**

* **User** → `Admin`, `Seller`, `Customer`
  *Ba loại user kế thừa thuộc tính chung.*
  *Three user types inherit from User.*

### **5. Dependency**

* **Seller → OrderManagementService**
  *Seller phụ thuộc vào module order khi quản lý đơn hàng.*
  *Seller depends on the order module to manage orders.*
  
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

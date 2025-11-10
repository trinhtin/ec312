## 🧩 **Bài 1 – Đăng ký và đăng nhập (User Registration & Login)**

**FR-01:** The system shall allow customers to register, log in, and log out.
*(Hệ thống cho phép khách hàng đăng ký, đăng nhập và đăng xuất.)*

**Actors:** Customer, System

**Main Use Cases:**

* Register account *(Đăng ký tài khoản)*
* Login *(Đăng nhập)*
* Logout *(Đăng xuất)*

**Hint:** Include relationship between “Register” and “Verify Email.”
*(Gợi ý: Thêm mối quan hệ include giữa “Đăng ký” và “Xác minh email.”)*

---

## 🛒 **Bài 2 – Tìm kiếm và thêm sản phẩm vào giỏ hàng (Search & Add to Cart)**

**FR-02:** The customer can search products by name and add selected items to the cart.
*(Khách hàng có thể tìm sản phẩm theo tên và thêm vào giỏ hàng.)*

**Actors:** Customer, System

**Main Use Cases:**

* Search Product *(Tìm kiếm sản phẩm)*
* View Product Detail *(Xem chi tiết sản phẩm)*
* Add to Cart *(Thêm vào giỏ hàng)*

**Hint:** Use include between “Search Product” → “View Product Detail.”
*(Gợi ý: Thêm include giữa “Tìm kiếm sản phẩm” và “Xem chi tiết sản phẩm.”)*

---

## 💳 **Bài 3 – Thanh toán đơn hàng (Checkout and Payment)**

**FR-03:** The system allows customers to checkout, select payment methods, and confirm the order.
*(Hệ thống cho phép khách hàng thanh toán, chọn phương thức thanh toán và xác nhận đơn hàng.)*

**Actors:** Customer, System, Payment Gateway

**Main Use Cases:**

* Checkout *(Thanh toán)*
* Select Payment Method *(Chọn phương thức thanh toán)*
* Make Payment *(Thực hiện thanh toán)*
* Confirm Order *(Xác nhận đơn hàng)*

**Hint:** Include Payment Gateway in “Make Payment,” extend to “Cancel Payment.”
*(Gợi ý: Bao gồm Payment Gateway trong use case “Thực hiện thanh toán,” thêm extend cho “Hủy thanh toán.”)*

---

## 📦 **Bài 4 – Quản lý đơn hàng (Order Management)**

**FR-04:** Customers can view their orders, track delivery status, and request returns.
*(Khách hàng có thể xem đơn hàng, theo dõi tình trạng giao hàng, và yêu cầu trả hàng.)*

**Actors:** Customer, System, Logistics Provider

**Main Use Cases:**

* View Order History *(Xem lịch sử đơn hàng)*
* Track Shipment *(Theo dõi giao hàng)*
* Request Return *(Yêu cầu trả hàng)*
* Approve Return *(Xác nhận trả hàng)*

**Hint:** Use extend from “Track Shipment” to “Request Return.”
*(Gợi ý: Dùng extend từ “Theo dõi giao hàng” sang “Yêu cầu trả hàng.”)*

---

## ⭐ **Bài 5 – Quản lý đánh giá sản phẩm (Product Review Management)**

**FR-05:** Registered users can post reviews, give ratings, and report inappropriate comments.
*(Người dùng đã đăng ký có thể đăng đánh giá, chấm điểm, và báo cáo bình luận không phù hợp.)*

**Actors:** Customer, System, Admin

**Main Use Cases:**

* Write Review *(Viết đánh giá)*
* Rate Product *(Chấm điểm sản phẩm)*
* Report Review *(Báo cáo đánh giá)*
* Moderate Review *(Kiểm duyệt đánh giá)*

**Hint:** Extend from “Report Review” → “Moderate Review.”
*(Gợi ý: Dùng extend từ “Báo cáo đánh giá” sang “Kiểm duyệt đánh giá.”)*

Dưới đây là **5 bài tập vẽ full Use Case Diagram** cho các mô hình **hệ thống Thương mại điện tử (TMĐT)** phổ biến, được trình bày **song ngữ Việt – Anh (English in parentheses)**.
Các bài tập được sắp xếp từ **cơ bản đến nâng cao**, bao gồm **nhiều actor, mối quan hệ include/extend**, và có thể dùng cho sinh viên **vẽ sơ đồ Use Case hoàn chỉnh**.

---

### 🛒 **Bài 6 – B2C E-commerce Website (Trang TMĐT Bán hàng cho khách cá nhân)**

**Mức độ:** Dễ

**Mô tả (Description):**
Hệ thống cho phép khách hàng duyệt sản phẩm, thêm vào giỏ hàng, đặt hàng và thanh toán trực tuyến.
*(The system allows customers to browse products, add to cart, place orders, and pay online.)*

**Actors:**

* Customer (Khách hàng)
* System (Hệ thống)
* Payment Gateway (Cổng thanh toán)

**Use Cases:**

* Browse Products (Duyệt sản phẩm)
* Add to Cart (Thêm vào giỏ hàng)
* Checkout (Thanh toán đơn hàng)
* Make Payment (Thực hiện thanh toán) — *include → Checkout*
* View Order History (Xem lịch sử đơn hàng)

---

### 🏬 **Bài 7 – B2B Marketplace (Sàn giao dịch doanh nghiệp với doanh nghiệp)**

**Mức độ:** Trung bình

**Mô tả (Description):**
Hệ thống kết nối các doanh nghiệp mua và bán hàng hóa sỉ, có quản lý đơn hàng, báo giá và hợp đồng.
*(The system connects businesses for wholesale transactions, including order, quotation, and contract management.)*

**Actors:**

* Supplier (Nhà cung cấp)
* Buyer (Người mua doanh nghiệp)
* Admin (Quản trị viên)

**Use Cases:**

* Post Product Listings (Đăng sản phẩm)
* Request Quotation (Yêu cầu báo giá)
* Approve Contract (Phê duyệt hợp đồng)
* Manage Orders (Quản lý đơn hàng)
* Handle Disputes (Xử lý tranh chấp) — *extend → Manage Orders*

---

### 📦 **Bài 8 – Dropshipping Platform (Nền tảng bán hàng ký gửi)**

**Mức độ:** Trung bình – Khá

**Mô tả (Description):**
Nền tảng cho phép người bán đăng sản phẩm của nhà cung cấp và hệ thống tự động xử lý đơn hàng.
*(The platform enables sellers to list supplier products, and automatically forwards orders to suppliers.)*

**Actors:**

* Seller (Người bán)
* Supplier (Nhà cung cấp)
* Customer (Khách hàng)
* System (Hệ thống)

**Use Cases:**

* Sync Product Data (Đồng bộ dữ liệu sản phẩm)
* Place Customer Order (Khách hàng đặt hàng)
* Forward Order to Supplier (Chuyển đơn cho nhà cung cấp) — *include → Place Customer Order*
* Track Shipment (Theo dõi giao hàng)
* Handle Return (Xử lý trả hàng) — *extend → Track Shipment*

---

### 📱 **Bài 9 – Mobile Commerce App (Ứng dụng TMĐT di động)**

**Mức độ:** Khá – Nâng cao

**Mô tả (Description):**
Ứng dụng TMĐT hỗ trợ thanh toán qua ví điện tử, push notification và chương trình khách hàng thân thiết.
*(The mobile commerce app supports e-wallet payment, push notifications, and loyalty programs.)*

**Actors:**

* Mobile User (Người dùng di động)
* System (Hệ thống)
* Payment Service (Dịch vụ thanh toán)
* Loyalty Program (Chương trình khách hàng thân thiết)

**Use Cases:**

* Register/Login (Đăng ký/Đăng nhập)
* Browse and Search Products (Tìm kiếm sản phẩm)
* Add to Wishlist (Thêm vào danh sách yêu thích)
* Make Payment (Thanh toán) — *include → Checkout*
* Earn Reward Points (Nhận điểm thưởng) — *extend → Make Payment*
* Receive Notifications (Nhận thông báo)

---

### ☁️ **Bài 10 – Cloud-based SaaS E-commerce Solution (Giải pháp TMĐT SaaS dựa trên đám mây)**

**Mức độ:** Nâng cao

**Mô tả (Description):**
Hệ thống SaaS cho phép doanh nghiệp tạo và quản lý cửa hàng TMĐT riêng của họ trên nền tảng đám mây.
*(The SaaS system allows businesses to create and manage their own online stores on a cloud platform.)*

**Actors:**

* Store Owner (Chủ cửa hàng)
* Customer (Khách hàng)
* System (Nền tảng SaaS)
* Payment Gateway (Cổng thanh toán)
* Support Staff (Nhân viên hỗ trợ)

**Use Cases:**

* Create Online Store (Tạo cửa hàng trực tuyến)
* Manage Products and Inventory (Quản lý sản phẩm và tồn kho)
* Configure Payment Options (Cấu hình phương thức thanh toán)
* Process Customer Orders (Xử lý đơn hàng)
* Access Analytics Dashboard (Xem bảng điều khiển phân tích)
* Request Technical Support (Yêu cầu hỗ trợ kỹ thuật) — *extend → Manage Store*







# Bài Tập Vẽ Sequence Diagram Cơ Bản

---

## 🧩 **Bài 1 – Customer Login (Đăng nhập khách hàng)**

Trong chức năng đăng nhập, **khách hàng** truy cập **giao diện đăng nhập (Login Page)** và nhập thông tin gồm **email và mật khẩu**.
Sau đó, giao diện đăng nhập gửi yêu cầu xác thực đến **AuthService** để kiểm tra thông tin người dùng.
Dịch vụ xác thực sẽ truy vấn đến **cơ sở dữ liệu người dùng (UserDatabase)** để đối chiếu thông tin.
Nếu thông tin hợp lệ, **UserDatabase** trả về kết quả xác thực thành công cho **AuthService**.
Tiếp đó, **AuthService** phản hồi kết quả đăng nhập cho **Login Page**, và người dùng sẽ được **chuyển hướng đến trang chủ (Home Page)** tương ứng với tài khoản của mình.
Ngược lại, nếu xác thực thất bại, hệ thống hiển thị thông báo lỗi đăng nhập.

---

## 🧩 **Bài 2 – Add to Cart (Thêm sản phẩm vào giỏ hàng)**

Trong quy trình thêm sản phẩm vào giỏ hàng, **khách hàng** tại **trang chi tiết sản phẩm (Product Page)** nhấn nút **“Add to Cart”**.
Hành động này khiến **Product Page** gửi thông tin sản phẩm (mã sản phẩm, số lượng) đến **CartService** để xử lý.
Tiếp theo, **CartService** thực hiện cập nhật dữ liệu giỏ hàng trong **CartDatabase**.
Sau khi lưu trữ thành công, **CartDatabase** phản hồi lại cho **CartService** để xác nhận thao tác đã hoàn tất.
Cuối cùng, **CartService** gửi thông báo lại cho **Product Page** để hiển thị thông báo **“Sản phẩm đã được thêm vào giỏ hàng”** cho khách hàng.

---

## 🧩 **Bài 3 – Place Order (Đặt hàng)**

Khi khách hàng hoàn tất việc lựa chọn sản phẩm, họ tiến hành bước **đặt hàng (Place Order)** trên **trang đặt hàng (Order Page)**.
Giao diện này gửi yêu cầu tạo đơn hàng mới đến **OrderService**.
**OrderService** sẽ ghi nhận thông tin đơn hàng và lưu trữ vào **OrderDatabase**.
Ngay sau đó, **OrderService** gửi yêu cầu thanh toán đến **PaymentGateway** để thực hiện xử lý giao dịch.
Sau khi thanh toán hoàn tất, **PaymentGateway** phản hồi kết quả cho **OrderService** (thành công hoặc thất bại).
Dựa vào kết quả này, **OrderService** gửi thông báo về **Order Page**, nơi khách hàng nhận được thông tin xác nhận đơn hàng thành công hoặc thông báo lỗi nếu có vấn đề xảy ra.

---

## 🧩 **Bài 4 – Manage Inventory (Quản lý tồn kho)**

Trong chức năng quản lý tồn kho, **chủ cửa hàng (Store Owner)** nhập số lượng sản phẩm cần cập nhật trên **trang quản lý tồn kho (Inventory Page)**.
Khi người dùng xác nhận, **Inventory Page** gửi yêu cầu cập nhật đến **InventoryService** để xử lý dữ liệu.
Sau đó, **InventoryService** tiến hành ghi nhận thay đổi vào **cơ sở dữ liệu tồn kho (InventoryDatabase)**.
Khi cập nhật thành công, **InventoryDatabase** trả về thông báo xác nhận cho **InventoryService**.
Cuối cùng, **InventoryService** gửi phản hồi về **Inventory Page**, hiển thị số lượng tồn kho mới đã được cập nhật cho người dùng.

---

## 🧩 **Bài 5 – Customer Support Chat (Trò chuyện hỗ trợ khách hàng)**

Khi khách hàng cần hỗ trợ, họ sử dụng **giao diện trò chuyện (Chat Interface)** để gửi tin nhắn đến hệ thống.
Giao diện này chuyển tiếp nội dung tin nhắn đến **SupportService**, dịch vụ chịu trách nhiệm điều phối các cuộc hội thoại.
Ngay sau đó, **SupportService** gửi thông báo đến **nhân viên hỗ trợ (Support Staff)** về tin nhắn mới từ khách hàng.
**Support Staff** đọc nội dung và gửi lại phản hồi thông qua **SupportService**.
Thông điệp trả lời này được chuyển ngược về **Chat Interface**, nơi tin nhắn phản hồi được hiển thị cho **khách hàng** trên màn hình trò chuyện.
Toàn bộ quá trình đảm bảo tương tác **hai chiều thời gian thực** giữa khách hàng và nhân viên hỗ trợ thông qua hệ thống trung gian.


---

# Bài Tập Vẽ Sequence Diagram nâng cao (Kiến trúc 3 lớp, MVC)

---

## 🧩 **Bài 6 – User Login Flow (Luồng đăng nhập người dùng)**

**Mô hình:** MVC (Model–View–Controller)

### 🔹 Thành phần:

* **User (Người dùng)**
* **Login View (Giao diện đăng nhập)**
* **Login Controller (Bộ điều khiển đăng nhập)**
* **Auth Service (Dịch vụ xác thực – Business Layer)**
* **User Repository / Database (Tầng dữ liệu)**

### 🔹 Trình tự mô tả:

Người dùng nhập email và mật khẩu trên **Login View**, sau đó nhấn nút “Đăng nhập”.
Giao diện gọi hàm `submitLogin()` của **Login Controller** để xử lý.
Controller chuyển yêu cầu xuống **Auth Service** trong tầng nghiệp vụ để kiểm tra thông tin xác thực.
**Auth Service** truy cập **User Repository** trong tầng dữ liệu để đối chiếu thông tin người dùng.
Nếu dữ liệu hợp lệ, Repository trả về đối tượng người dùng (User Object).
**Auth Service** gửi thông báo “success” về **Login Controller**, controller sẽ cập nhật giao diện bằng cách điều hướng sang trang chính của người dùng.
Ngược lại, nếu đăng nhập thất bại, Controller sẽ trả về thông báo lỗi hiển thị trên **Login View**.

---

## 🧩 **Bài 7 – Product Search and Display (Tìm kiếm và hiển thị sản phẩm)**

**Mô hình:** MVC

### 🔹 Thành phần:

* **Customer (Khách hàng)**
* **Product Search View (Giao diện tìm kiếm sản phẩm)**
* **Product Controller (Bộ điều khiển sản phẩm)**
* **Product Service (Dịch vụ xử lý nghiệp vụ sản phẩm)**
* **Product Repository (Kho dữ liệu sản phẩm / DB)**

### 🔹 Trình tự mô tả:

Người dùng nhập từ khóa tìm kiếm trên **Product Search View** và nhấn nút “Tìm kiếm”.
Giao diện gửi yêu cầu đến **Product Controller**.
Controller gọi phương thức `searchProducts(keyword)` của **Product Service** để xử lý nghiệp vụ.
**Product Service** truy vấn dữ liệu từ **Product Repository**, tìm tất cả sản phẩm phù hợp với từ khóa.
Repository trả về danh sách sản phẩm cho **Product Service**, dịch vụ này có thể xử lý thêm (lọc, sắp xếp, phân trang).
Kết quả sau cùng được trả lại cho **Product Controller**, controller gửi dữ liệu đến **Product Search View**, nơi kết quả tìm kiếm được hiển thị cho khách hàng.

---

## 🧩 **Bài 8 – Add Item to Cart (Thêm sản phẩm vào giỏ hàng)**

**Mô hình:** 3-Layer Architecture

### 🔹 Thành phần:

* **Customer (Người dùng)**
* **UI Layer (Cart Page)**
* **Business Layer (CartService)**
* **Data Layer (CartRepository / CartDB)**

### 🔹 Trình tự mô tả:

Khách hàng đang xem chi tiết sản phẩm và chọn “Thêm vào giỏ hàng”.
**UI Layer** gửi yêu cầu `addToCart(productId, quantity)` đến **CartService** trong tầng nghiệp vụ.
**CartService** thực hiện kiểm tra tính hợp lệ của yêu cầu (ví dụ: sản phẩm còn hàng hay không).
Sau đó, **CartService** gọi hàm `insertCartItem()` trong **CartRepository** để lưu dữ liệu vào cơ sở dữ liệu **CartDB**.
**CartDB** phản hồi thành công và trả về ID của giỏ hàng hoặc trạng thái cập nhật.
**CartService** gửi thông báo xác nhận cho **UI Layer**, giao diện hiển thị thông báo “Sản phẩm đã được thêm vào giỏ hàng”.

---

## 🧩 **Bài 9 – Checkout and Payment (Thanh toán đơn hàng)**

**Mô hình:** 3-Layer Architecture + External API

### 🔹 Thành phần:

* **Customer (Khách hàng)**
* **Checkout UI (Giao diện thanh toán)**
* **OrderController / OrderService (Tầng nghiệp vụ)**
* **OrderRepository (Tầng dữ liệu)**
* **Payment Gateway (Dịch vụ thanh toán ngoài)**

### 🔹 Trình tự mô tả:

Khách hàng xác nhận thông tin giao hàng và chọn phương thức thanh toán trên **Checkout UI**.
Hệ thống gửi yêu cầu đến **OrderService** để tạo đơn hàng mới.
**OrderService** lưu thông tin đơn hàng tạm thời vào **OrderRepository**.
Sau đó, dịch vụ này gọi API của **Payment Gateway** để xử lý giao dịch thanh toán.
Khi thanh toán thành công, **Payment Gateway** trả về mã xác nhận (Transaction ID).
**OrderService** cập nhật trạng thái đơn hàng là “Paid” trong **OrderRepository**.
Cuối cùng, **Checkout UI** hiển thị thông báo xác nhận đơn hàng và hiển thị hóa đơn cho khách hàng.

---

## 🧩 **Bài 10 – Admin Manage Products (Quản trị viên quản lý sản phẩm)**

**Mô hình:** MVC / 3-Layer Architecture

### 🔹 Thành phần:

* **Admin (Quản trị viên)**
* **Product Management UI (Giao diện quản trị)**
* **ProductController (Bộ điều khiển)**
* **ProductService (Tầng nghiệp vụ)**
* **ProductRepository (Tầng dữ liệu)**

### 🔹 Trình tự mô tả:

Quản trị viên đăng nhập vào **Product Management UI** và chọn thao tác “Thêm sản phẩm mới”.
Giao diện gửi dữ liệu sản phẩm đến **ProductController**, controller gọi hàm `addProduct(product)` trong **ProductService**.
**ProductService** kiểm tra tính hợp lệ của dữ liệu (tên, giá, danh mục, tồn kho).
Nếu hợp lệ, **ProductService** yêu cầu **ProductRepository** ghi thông tin vào cơ sở dữ liệu.
Sau khi lưu thành công, **ProductRepository** phản hồi trạng thái “Success”.
**ProductService** gửi phản hồi lại **ProductController**, controller cập nhật giao diện hiển thị thông báo “Sản phẩm đã được thêm thành công”.
Nếu có lỗi (ví dụ dữ liệu thiếu hoặc trùng), controller nhận thông báo lỗi và hiển thị cảnh báo trên UI.

# 1. Business Requirements

Business requirement là **những yêu cầu cấp cao phản ánh mục tiêu, lợi ích, và nhu cầu kinh doanh** (không phải chi tiết chức năng cụ thể). Nó trả lời câu hỏi: *Doanh nghiệp muốn đạt được gì khi xây dựng hệ thống?*

Ví dụ trong **hệ thống TMĐT (E-commerce)**:

---

### 📌 Ví dụ Business Requirements

1. **Tăng doanh thu trực tuyến**

   * Doanh nghiệp muốn hệ thống TMĐT giúp mở rộng thị trường và tăng doanh thu bán hàng trực tuyến ít nhất 30% trong 12 tháng tới.

2. **Cải thiện trải nghiệm khách hàng**

   * Cần có nền tảng bán hàng online giúp khách hàng dễ dàng tìm kiếm, đặt hàng và thanh toán trong vòng < 3 phút.

3. **Hỗ trợ đa kênh (Omni-channel)**

   * Hệ thống cần đồng bộ tồn kho giữa website, ứng dụng di động và cửa hàng offline.

4. **Giảm chi phí vận hành**

   * Tự động hóa xử lý đơn hàng, thanh toán và kết nối logistics để giảm 20% chi phí vận hành.

5. **Mở rộng thị trường quốc tế**

   * Hỗ trợ đa ngôn ngữ (tiếng Việt, tiếng Anh) và nhiều loại tiền tệ để phục vụ khách hàng ở Đông Nam Á.

---

👉 Business Requirement là **mục tiêu lớn của doanh nghiệp**, từ đó BA (Business Analyst) sẽ phân rã thành **Functional Requirements** (chức năng cụ thể) và **Non-functional Requirements** (hiệu năng, bảo mật…).

---------------------------------------------
# 2. Functional Requirements

Functional Requirements (Yêu cầu chức năng) là **những gì hệ thống cần làm**, mô tả hành vi, chức năng hoặc dịch vụ mà hệ thống phải cung cấp để đáp ứng Business Requirements.

Ví dụ trong một hệ thống **Website Bán Hàng Online**:

---

### Functional Requirements (Ví dụ)

1. **Quản lý tài khoản người dùng**

   * Hệ thống cho phép khách hàng đăng ký tài khoản mới bằng email hoặc số điện thoại.
   * Hệ thống cho phép người dùng đăng nhập bằng email/số điện thoại và mật khẩu.
   * Hệ thống cho phép người dùng đặt lại mật khẩu qua email xác thực.

2. **Chức năng tìm kiếm và duyệt sản phẩm**

   * Người dùng có thể tìm kiếm sản phẩm theo tên, loại, hoặc khoảng giá.
   * Hệ thống hiển thị danh sách sản phẩm theo bộ lọc (giá, thương hiệu, độ phổ biến).
   * Hệ thống cho phép người dùng sắp xếp kết quả tìm kiếm theo giá tăng/giảm dần.

3. **Chức năng giỏ hàng**

   * Người dùng có thể thêm sản phẩm vào giỏ hàng.
   * Người dùng có thể cập nhật số lượng hoặc xóa sản phẩm trong giỏ hàng.
   * Hệ thống tính tổng tiền giỏ hàng tự động khi có thay đổi.

4. **Chức năng đặt hàng & thanh toán**

   * Người dùng có thể chọn phương thức thanh toán (COD, thẻ, ví điện tử).
   * Hệ thống tạo mã đơn hàng duy nhất cho mỗi giao dịch.
   * Hệ thống gửi email xác nhận đơn hàng thành công cho khách hàng.

5. **Chức năng quản trị (Admin)**

   * Quản trị viên có thể thêm/sửa/xóa sản phẩm trong hệ thống.
   * Quản trị viên có thể xem danh sách đơn hàng và thay đổi trạng thái (Đang xử lý, Đã giao, Đã hủy).
   * Quản trị viên có thể tạo báo cáo doanh thu theo ngày/tháng/năm.

---

👉 Functional Requirements thường được viết chi tiết để làm cơ sở cho **Use Case** hoặc **thiết kế hệ thống**.

Bạn có muốn mình làm **bảng phân rã tiếp** (Business Requirement → Functional Requirement → Use Case) cho ví dụ này luôn không?


---------------------------------------------

# 3. Non-functional Requirements

Non-functional requirements (Yêu cầu phi chức năng) là những ràng buộc hoặc tiêu chí chất lượng mà hệ thống phải đáp ứng, không liên quan trực tiếp đến **chức năng cụ thể**, mà đến **cách hệ thống hoạt động**.

Ví dụ với **Website Bán Hàng Online**:

---

### Non-Functional Requirements (Ví dụ)

1. **Hiệu năng (Performance)**

   * Thời gian phản hồi của hệ thống không vượt quá **2 giây** cho 95% các yêu cầu tìm kiếm sản phẩm.
   * Hệ thống có thể xử lý **1.000 giao dịch/giây** trong giờ cao điểm.

2. **Khả năng mở rộng (Scalability)**

   * Hệ thống phải hỗ trợ mở rộng để phục vụ ít nhất **1 triệu người dùng đồng thời**.

3. **Bảo mật (Security)**

   * Tất cả dữ liệu nhạy cảm (mật khẩu, số thẻ tín dụng) phải được **mã hóa AES-256**.
   * Hệ thống yêu cầu xác thực hai yếu tố (2FA) cho tài khoản quản trị viên.

4. **Tính sẵn sàng (Availability)**

   * Hệ thống phải có độ sẵn sàng **99,9% uptime** mỗi tháng.
   * Các dịch vụ quan trọng (đặt hàng, thanh toán) phải luôn khả dụng trong giờ hoạt động.

5. **Khả năng sử dụng (Usability)**

   * Người dùng mới phải có thể hoàn thành quy trình đăng ký tài khoản trong vòng **dưới 3 phút**.
   * Giao diện website phải hỗ trợ **đa ngôn ngữ** (tiếng Việt, tiếng Anh).

6. **Khả năng bảo trì (Maintainability)**

   * Mỗi bản phát hành phần mềm phải có tài liệu hướng dẫn cập nhật (release note).
   * Hệ thống cần có khả năng thay đổi cấu hình mà không cần khởi động lại.

7. **Khả năng tương thích (Compatibility)**

   * Website phải hoạt động tốt trên các trình duyệt phổ biến (Chrome, Firefox, Safari, Edge).
   * Ứng dụng di động phải tương thích với Android (≥ 10) và iOS (≥ 14).

---

👉 Tóm lại:

* **Functional requirement** = Hệ thống làm *cái gì* (what).
* **Non-functional requirement** = Hệ thống làm *như thế nào* (how well).

Bạn có muốn mình lập **bảng so sánh Functional vs Non-functional requirement** để dễ nhớ hơn không?

-----------------------------
Rất hay 👍 Mình sẽ làm một **bảng phân rã mẫu** cho ví dụ cụ thể: **Refund (Hoàn tiền sản phẩm)** trong hệ thống TMĐT.

---

## 📑 Bảng phân rã yêu cầu (Sample Decomposition)

| Business Requirement (BR)                                                                           | Functional Requirement (FR)                                                       | Use Case (UC)                           |
| --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------- |
| BR1. Hệ thống cần hỗ trợ **hoàn tiền sản phẩm** để nâng cao sự tin tưởng và trải nghiệm khách hàng. | FR1. Người dùng có thể gửi yêu cầu hoàn tiền từ tài khoản của họ.                 | UC1: Submit Refund Request              |
|                                                                                                     | FR2. Nhân viên CSKH có thể xem và duyệt/từ chối yêu cầu hoàn tiền.                | UC2: Review Refund Request              |
|                                                                                                     | FR3. Hệ thống phải kết nối với Payment Gateway để xử lý giao dịch hoàn tiền.      | UC3: Process Refund via Payment Gateway |
|                                                                                                     | FR4. Khách hàng phải nhận được thông báo (email/app) về trạng thái hoàn tiền.     | UC4: Notify Customer of Refund Result   |
|                                                                                                     | FR5. Admin có thể xem báo cáo tổng hợp số lượng và giá trị các yêu cầu hoàn tiền. | UC5: Generate Refund Report             |

---

### 📝 Giải thích

* **Business Requirement (BR):** Tầm nhìn/mục tiêu lớn của doanh nghiệp (*nâng cao sự tin tưởng khách hàng*).
* **Functional Requirement (FR):** Hệ thống cần có những chức năng gì để hiện thực hóa mục tiêu.
* **Use Case (UC):** Tương tác cụ thể giữa Actor và hệ thống để triển khai FR.

---

👉 Nếu cần đi sâu thêm, mình có thể viết tiếp **mapping sang Class Diagram + ERD** như bạn đã hỏi ở Refund trước (ví dụ `RefundRequest`, `RefundTransaction`, `RefundStatus`).

Bạn có muốn mình soạn **Version đầy đủ (BR → FR → UC → Class/ERD Mapping)** cho ví dụ Refund này không?

-----------------------------------------------
Mình làm bảng so sánh để bạn dễ hình dung nhé 👇

| Tiêu chí                           | **Functional Requirement**                                                                                                                              | **Non-functional Requirement**                                                                                                                                                                 |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Định nghĩa**                     | Mô tả **hệ thống phải làm gì** – các chức năng, dịch vụ, hành vi mà hệ thống cung cấp cho người dùng.                                                   | Mô tả **hệ thống phải hoạt động như thế nào** – các thuộc tính về chất lượng, hiệu suất, bảo mật, khả dụng…                                                                                    |
| **Trả lời câu hỏi**                | *What does the system do?* – Hệ thống làm gì?                                                                                                           | *How well does the system perform?* – Hệ thống thực hiện tốt đến mức nào?                                                                                                                      |
| **Ví dụ (Website TMĐT)**           | - Đăng ký/đăng nhập tài khoản. <br> - Tìm kiếm và lọc sản phẩm. <br> - Thêm sản phẩm vào giỏ hàng. <br> - Thanh toán bằng thẻ tín dụng hoặc ví điện tử. | - Thời gian phản hồi < 2 giây cho 95% truy vấn tìm kiếm. <br> - Hỗ trợ tối thiểu 1 triệu người dùng đồng thời. <br> - Uptime 99,9% mỗi tháng. <br> - Bảo mật dữ liệu bằng AES-256, hỗ trợ 2FA. |
| **Đặc điểm**                       | - Cụ thể, gắn liền với nghiệp vụ. <br> - Có thể kiểm thử trực tiếp qua test case.                                                                       | - Mang tính ràng buộc, tiêu chí đánh giá chất lượng. <br> - Khó kiểm thử hơn, thường đo bằng chỉ số (metrics).                                                                                 |
| **Mức độ hiển thị với người dùng** | Người dùng nhìn thấy trực tiếp (ví dụ: nút "Mua hàng").                                                                                                 | Người dùng cảm nhận gián tiếp (ví dụ: tốc độ tải trang, mức độ bảo mật).                                                                                                                       |

👉 Hiểu ngắn gọn:

* **Functional = Chức năng “có cái gì”**.
* **Non-functional = Chất lượng “tốt đến đâu”**.

---

Bạn có muốn mình lấy **1 ví dụ thực tế đầy đủ (BR → FR → NFR → Use case)** để ghép thành chuỗi minh họa luôn không?

-----------------------------------------
Quá hay 👍 mình sẽ làm một ví dụ xuyên suốt để bạn thấy mối liên hệ:

---

## 🎯 Ví dụ: **Cửa hàng sách online**

### 1. **Business Requirement (BR)**

* Doanh nghiệp muốn xây dựng một **nền tảng bán sách online** để khách hàng có thể mua sách mọi lúc, mọi nơi, qua website hoặc mobile app.

---

### 2. **Functional Requirements (FR)**

(Trích ra từ BR, mô tả chức năng cụ thể của hệ thống)

* FR1: Người dùng có thể **tìm kiếm sách theo tên, tác giả, thể loại**.
* FR2: Người dùng có thể **thêm sách vào giỏ hàng**.
* FR3: Người dùng có thể **thanh toán đơn hàng** bằng thẻ ngân hàng hoặc ví điện tử.
* FR4: Quản trị viên có thể **quản lý kho sách** (thêm, sửa, xóa, cập nhật tồn kho).

---

### 3. **Non-functional Requirements (NFR)**

* Hệ thống phải phản hồi kết quả tìm kiếm trong **< 2 giây**.
* Đảm bảo **99.9% uptime** mỗi tháng.
* Thanh toán phải tuân thủ chuẩn bảo mật **PCI DSS** và dữ liệu nhạy cảm được **mã hóa AES-256**.
* Website phải hỗ trợ **ít nhất 10.000 người dùng đồng thời**.

---

### 4. **Use Case (Ví dụ: “Mua sách”)**

**Tên Use Case:** Mua sách online

* **Actor:** Khách hàng
* **Mục tiêu:** Khách hàng mua một hoặc nhiều cuốn sách thành công
* **Tiền điều kiện:** Khách hàng có tài khoản và đăng nhập
* **Luồng chính:**

  1. Khách hàng tìm kiếm sách.
  2. Chọn sách và thêm vào giỏ hàng.
  3. Kiểm tra giỏ hàng và nhấn “Thanh toán”.
  4. Nhập thông tin thanh toán (thẻ/ ví điện tử).
  5. Nhận thông báo đơn hàng thành công.
* **Ngoại lệ:**

  * Thanh toán thất bại (hệ thống báo lỗi).
  * Sách hết hàng (hiện thông báo & gợi ý sách khác).

---

👉 Như vậy bạn thấy chuỗi **BR → FR → NFR → Use Case** liên kết logic với nhau:

* **BR** định hướng *kinh doanh cần gì*.
* **FR** mô tả *hệ thống phải làm gì để đáp ứng BR*.
* **NFR** mô tả *chất lượng vận hành hệ thống*.
* **Use Case** cho thấy *từng chức năng FR hoạt động như thế nào trong thực tế*.

---

Bạn có muốn mình vẽ luôn **sơ đồ Use Case (PlantUML)** cho ví dụ “Mua sách online” này để sinh viên dễ hình dung không?

---

Bạn hỏi rất đúng 🎯 – Use Case “Mua sách online” như mình viết ở trên là **một Use Case cấp cao (high-level)**, thường để giao tiếp với *Business Analyst (BA), khách hàng, và quản lý dự án*.

👉 Nhưng để triển khai thành **code hoặc phân công cho dev**, Use Case này cần **phân rã thành các Use Case nhỏ hơn**, hoặc thậm chí thành *User Story/Task* trong Agile.

---

## 📌 Cách phân rã Use Case lớn:

Ví dụ Use Case “Mua sách online” có thể tách thành:

1. **Tìm kiếm & duyệt sách**

   * UC1: Tìm sách theo tên
   * UC2: Tìm sách theo tác giả
   * UC3: Lọc sách theo thể loại

2. **Quản lý giỏ hàng**

   * UC4: Thêm sách vào giỏ hàng
   * UC5: Xóa sách khỏi giỏ hàng
   * UC6: Cập nhật số lượng sách trong giỏ

3. **Thanh toán**

   * UC7: Nhập thông tin giao hàng
   * UC8: Chọn phương thức thanh toán
   * UC9: Thực hiện thanh toán qua Payment Gateway

4. **Hậu thanh toán**

   * UC10: Nhận xác nhận đơn hàng
   * UC11: Theo dõi trạng thái đơn hàng

---

## 📌 Liên hệ với phân công Dev:

* **Frontend Dev** → UI tìm kiếm, UI giỏ hàng, UI thanh toán.
* **Backend Dev** → API xử lý tìm kiếm, giỏ hàng, kết nối Payment Gateway.
* **DB Dev** → Thiết kế bảng sách, giỏ hàng, đơn hàng, thanh toán.
* **QA** → Test từng Use Case nhỏ.

---

✅ Kết luận:

* “Mua sách online” **không quá lớn ở mức BA/thiết kế tổng thể**.
* Nhưng khi vào **giai đoạn coding**, phải **chia nhỏ thành các Use Case chi tiết hoặc User Story** để dễ giao cho từng dev/module.

---

Bạn có muốn mình vẽ **Use Case Diagram phân rã từ “Mua sách online” thành các UC nhỏ hơn** để thấy rõ cấu trúc không?

---
Ok, mình sẽ vẽ **Use Case Diagram phân rã từ “Mua sách online”** thành các Use Case chi tiết hơn để bạn thấy rõ cấu trúc 🌟

---

## 📌 Use Case phân rã: "Mua sách online"

### Các tác nhân (Actors):

* **Khách hàng (User)**
* **Payment Gateway**
* **Hệ thống giao hàng (Logistics)**

### Các nhóm Use Case chính:

1. **Tìm kiếm & duyệt sách**

   * Tìm sách theo tên
   * Tìm sách theo tác giả
   * Lọc sách theo thể loại

2. **Quản lý giỏ hàng**

   * Thêm sách vào giỏ hàng
   * Xóa sách khỏi giỏ hàng
   * Cập nhật số lượng sách

3. **Thanh toán**

   * Nhập thông tin giao hàng
   * Chọn phương thức thanh toán
   * Thanh toán (kết nối Payment Gateway)

4. **Hậu thanh toán**

   * Nhận xác nhận đơn hàng
   * Theo dõi trạng thái đơn hàng (kết nối Logistics)

---

## 📌 PlantUML Use Case Diagram

```plantuml
@startuml
left to right direction
actor "Khách hàng" as User
actor "Payment Gateway" as PG
actor "Logistics" as LG

package "Mua sách online" {
  
  usecase "Tìm sách theo tên" as UC1
  usecase "Tìm sách theo tác giả" as UC2
  usecase "Lọc sách theo thể loại" as UC3
  
  usecase "Thêm sách vào giỏ hàng" as UC4
  usecase "Xóa sách khỏi giỏ hàng" as UC5
  usecase "Cập nhật số lượng sách" as UC6
  
  usecase "Nhập thông tin giao hàng" as UC7
  usecase "Chọn phương thức thanh toán" as UC8
  usecase "Thanh toán" as UC9
  
  usecase "Nhận xác nhận đơn hàng" as UC10
  usecase "Theo dõi trạng thái đơn hàng" as UC11
}

User --> UC1
User --> UC2
User --> UC3
User --> UC4
User --> UC5
User --> UC6
User --> UC7
User --> UC8
User --> UC9
User --> UC10
User --> UC11

UC9 --> PG : "Xử lý thanh toán"
UC11 --> LG : "Lấy thông tin giao hàng"

@enduml
```

---

👉 Với sơ đồ này, bạn sẽ thấy:

* UC “Mua sách online” **không đứng riêng**, mà được phân rã thành **nhiều Use Case nhỏ**.
* Mỗi UC nhỏ hoàn toàn có thể giao cho một dev hoặc nhóm dev phụ trách (Frontend, Backend, DB, QA).

---

Bạn có muốn mình làm thêm **bảng phân rã (UC cha → UC con → Task dev)** để tiện phân công trong team không?

------------------------

Rất hay 👍 để dễ phân công cho dev, ta sẽ làm bảng phân rã **Use Case cha → Use Case con → Task dev** cho ví dụ **“Mua sách online”**.

---

## 📌 Bảng phân rã Use Case

| UC Cha (High-level)       | UC Con (Detailed)            | Task Dev (Implementation)                                                |
| ------------------------- | ---------------------------- | ------------------------------------------------------------------------ |
| **Tìm kiếm & duyệt sách** | Tìm sách theo tên            | - API search theo tên<br>- UI nhập từ khóa, hiển thị kết quả             |
|                           | Tìm sách theo tác giả        | - API filter theo tác giả<br>- UI filter                                 |
|                           | Lọc sách theo thể loại       | - API filter category<br>- Dropdown chọn thể loại                        |
| **Quản lý giỏ hàng**      | Thêm sách vào giỏ hàng       | - API add\_to\_cart<br>- Nút "Thêm vào giỏ" trên UI                      |
|                           | Xóa sách khỏi giỏ hàng       | - API remove\_from\_cart<br>- UI cập nhật giỏ hàng                       |
|                           | Cập nhật số lượng sách       | - API update\_cart<br>- Input thay đổi số lượng                          |
| **Thanh toán**            | Nhập thông tin giao hàng     | - Form nhập địa chỉ<br>- Validate dữ liệu                                |
|                           | Chọn phương thức thanh toán  | - UI chọn COD/Online<br>- Lưu thông tin lựa chọn                         |
|                           | Thanh toán (Payment Gateway) | - Tích hợp API VNPay/MoMo/PayPal<br>- Xử lý callback thành công/thất bại |
| **Hậu thanh toán**        | Nhận xác nhận đơn hàng       | - API tạo đơn hàng<br>- Gửi email/notification                           |
|                           | Theo dõi trạng thái đơn hàng | - API lấy trạng thái từ Logistics<br>- UI hiển thị tracking              |

---

👉 Với bảng này:

* **BA** dùng để trình bày với khách hàng (clear scope).
* **PM/Tech Lead** dùng để phân công task cho dev.
* **Dev** biết rõ phải code API nào, UI nào.

---

Bạn có muốn mình tiếp tục mở rộng bảng này sang **mapping (UC → Sequence Diagram → Class → ERD)** để có chuỗi hoàn chỉnh từ requirement → design → database không?

--------------------

Quá chuẩn 👌. Mình sẽ minh họa chuỗi **mapping từ Requirement đến Database** cho một Use Case cụ thể trong ví dụ **“Mua sách online → Thanh toán”** để bạn thấy toàn bộ flow.

---

# 📌 Mapping Use Case → Sequence Diagram → Class → ERD

| Level                | Mô tả                                                   | Ví dụ (Thanh toán)                                                                                                                                                                                                                                                                                                                                                             |
| -------------------- | ------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Use Case (UC)**    | Diễn tả yêu cầu người dùng và tác nhân tương tác        | **UC: Thanh toán**<br>Actor: Khách hàng, Payment Gateway<br>Flow: Người dùng chọn phương thức → nhập thông tin → hệ thống gửi request → Payment Gateway xử lý → trả kết quả → hệ thống tạo đơn hàng                                                                                                                                                                            |
| **Sequence Diagram** | Diễn tả luồng thông điệp (messages) giữa các thành phần | **Messages chính:**<br>1. User → UI: Submit order<br>2. UI → OrderController: requestThanhToan()<br>3. OrderController → PaymentService: xử lý giao dịch<br>4. PaymentService → PaymentGateway: gửi request<br>5. PaymentGateway → PaymentService: callback kết quả<br>6. PaymentService → OrderController: cập nhật trạng thái<br>7. OrderController → User: hiển thị kết quả |
| **Class Diagram**    | Các đối tượng và quan hệ                                | **Class chính:**<br>- `Order` (orderId, totalAmount, status)<br>- `Payment` (paymentId, method, status, transactionCode)<br>- `User` (userId, name, email)<br>- `PaymentService` (processPayment(), updateStatus())                                                                                                                                                            |
| **ERD (Database)**   | Các bảng CSDL và quan hệ                                | **Bảng tương ứng:**<br>- `Users(user_id, name, email, …)`<br>- `Orders(order_id, user_id, total_amount, status)`<br>- `Payments(payment_id, order_id, method, status, transaction_code)`<br>- Quan hệ: 1 User → nhiều Orders; 1 Order → 1 Payment                                                                                                                              |

---

## 📊 Nhận xét Mapping

* **Use Case** → cho BA/Stakeholder hiểu "hệ thống phải làm gì".
* **Sequence Diagram** → cho Engineer mô tả *luồng xử lý*.
* **Class Diagram** → cho Designer/Dev định nghĩa *object & logic*.
* **ERD** → cho DB Designer tạo bảng *lưu dữ liệu thực tế*.

---

👉 Với cách mapping này, mỗi bước đều **truy vết ngược (traceability)** được:

* Nếu khách hàng đổi requirement → check lại UC → chỉnh lại Sequence → cập nhật Class & ERD.

---

Bạn có muốn mình làm **sơ đồ trực quan PlantUML** cho chuỗi này (Use Case → Sequence → Class → ERD) để thấy toàn bộ mối liên hệ không?


--------------------

Ok, mình sẽ viết bản **đặc tả Use Case (Use Case Specification)** cho **UC1: Tìm sách theo tên**. Đây là mẫu thường dùng trong BA/thiết kế hệ thống theo chuẩn UML.

---

# 📌 Đặc tả Use Case: UC1 – Tìm sách theo tên

**1. Thông tin chung**

* **Tên Use Case**: Tìm sách theo tên
* **Mã số**: UC1
* **Actor chính**: Khách hàng (User)
* **Actor phụ**: Không có
* **Mục tiêu**: Cho phép người dùng nhập từ khóa và nhận danh sách sách có tiêu đề phù hợp.
* **Phạm vi**: Hệ thống cửa hàng sách online

---

**2. Mô tả ngắn gọn**
Khách hàng nhập một từ khóa (toàn bộ hoặc một phần tên sách) vào ô tìm kiếm. Hệ thống sẽ truy vấn cơ sở dữ liệu và trả về danh sách các sách có tiêu đề chứa từ khóa.

---

**3. Luồng sự kiện chính (Main Flow)**

1. User mở trang web/app.
2. User nhập từ khóa vào ô tìm kiếm.
3. User nhấn nút **Tìm kiếm**.
4. Hệ thống nhận request từ UI.
5. Hệ thống gửi truy vấn tìm kiếm đến DB (dùng LIKE hoặc Full-text Search).
6. DB trả về danh sách sách phù hợp.
7. Hệ thống hiển thị danh sách kết quả cho User.

---

**4. Luồng thay thế (Alternative Flows)**

* **AF1 – Không tìm thấy kết quả:**

  * Nếu DB không có sách nào khớp, hệ thống hiển thị thông báo “Không tìm thấy sách phù hợp”.
* **AF2 – Lỗi kết nối DB:**

  * Nếu DB không phản hồi, hệ thống hiển thị “Hệ thống bận, vui lòng thử lại sau”.

---

**5. Điều kiện tiên quyết (Pre-condition)**

* Người dùng đã truy cập vào trang web/app.
* Hệ thống và DB hoạt động bình thường.

---

**6. Điều kiện hậu (Post-condition)**

* Hệ thống đã trả về danh sách kết quả tìm kiếm (có thể rỗng).

---

**7. Yêu cầu đặc biệt (Special Requirements)**

* Tốc độ phản hồi tìm kiếm < 2 giây.
* Hỗ trợ tìm kiếm không phân biệt hoa/thường.
* Có gợi ý (autocomplete) khi người dùng nhập từ khóa.

---

👉 Đây chính là bản mô tả chi tiết để BA bàn giao cho team dev. Sau đó dev sẽ dựa vào đây mà thiết kế **Sequence Diagram + API + DB query**.

---

Bạn có muốn mình viết luôn **đặc tả API (REST/GraphQL)** cho UC1 này để sát với code không?



--------------------


Rồi 👍 mình sẽ lấy đúng ví dụ nhỏ **“Tìm sách theo tên” (UC1)** và mapping toàn bộ chuỗi từ **Use Case → Sequence → Class → ERD** để bạn dễ hình dung hơn.

---

# 📌 Mapping UC1: "Tìm sách theo tên"

| Level                | Mô tả                                             | Ví dụ cụ thể (UC1: Tìm sách theo tên)                                                                                                                                                                                                                                                                                                                                                     |
| -------------------- | ------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Use Case (UC1)**   | Người dùng muốn tìm sách theo tên để dễ dàng mua. | - **Actor**: Khách hàng (User)<br>- **Goal**: Nhập tên sách → hiển thị kết quả.<br>- **Flow**:<br>1. User nhập từ khóa.<br>2. Hệ thống tìm trong DB.<br>3. Trả về danh sách sách phù hợp.                                                                                                                                                                                                 |
| **Sequence Diagram** | Luồng thông điệp trong tìm kiếm sách.             | 1. User → UI: nhập từ khóa.<br>2. UI → SearchController: requestSearch(keyword).<br>3. SearchController → BookService: searchByTitle(keyword).<br>4. BookService → BookRepository: queryDB(keyword).<br>5. DB → BookRepository: kết quả.<br>6. BookRepository → BookService: trả danh sách.<br>7. BookService → SearchController: danh sách.<br>8. SearchController → UI: render kết quả. |
| **Class Diagram**    | Các đối tượng chính tham gia UC1.                 | - `Book` (bookId, title, author, price, stock)<br>- `User` (userId, name, email)<br>- `BookService` (searchByTitle())<br>- `BookRepository` (queryDB())<br>- `SearchController` (handleRequest())                                                                                                                                                                                         |
| **ERD (Database)**   | Bảng dữ liệu để thực hiện UC1.                    | - `Books(book_id, title, author, price, stock, category_id)`<br>- `Categories(category_id, name)`<br>- Quan hệ: `Books.category_id → Categories.category_id`.                                                                                                                                                                                                                             |

---

## 📌 PlantUML minh họa Sequence Diagram UC1

```plantuml
@startuml
actor User
boundary UI
control SearchController
entity BookService
database DB

User -> UI : nhập từ khóa
UI -> SearchController : requestSearch(keyword)
SearchController -> BookService : searchByTitle(keyword)
BookService -> DB : SELECT * FROM Books WHERE title LIKE '%keyword%'
DB --> BookService : trả kết quả
BookService --> SearchController : danh sách sách
SearchController --> UI : render kết quả
UI --> User : hiển thị danh sách
@enduml
```

---

👉 Điểm hay ở UC nhỏ như thế này:

* Có thể giao **1 dev frontend** làm UI form + hiển thị,
* **1 dev backend** làm API search,
* **1 dev database** làm index + tối ưu query.

---

Bạn có muốn mình vẽ tiếp **Class Diagram + ERD bằng PlantUML** cho UC1 này không (để thấy object và bảng link nhau)?



---------------------
Ok 👍 mình viết tiếp bản **đặc tả Use Case (Use Case Specification)** cho **UC2: Tìm sách theo tác giả**.

---

# 📌 Đặc tả Use Case: UC2 – Tìm sách theo tác giả

**1. Thông tin chung**

* **Tên Use Case**: Tìm sách theo tác giả
* **Mã số**: UC2
* **Actor chính**: Khách hàng (User)
* **Actor phụ**: Không có
* **Mục tiêu**: Cho phép người dùng nhập tên tác giả và nhận danh sách các sách do tác giả đó viết.
* **Phạm vi**: Hệ thống cửa hàng sách online

---

**2. Mô tả ngắn gọn**
Người dùng nhập tên tác giả (toàn bộ hoặc một phần) vào ô tìm kiếm. Hệ thống tìm trong cơ sở dữ liệu và trả về danh sách các sách có tác giả phù hợp.

---

**3. Luồng sự kiện chính (Main Flow)**

1. User mở trang web/app.
2. User nhập tên tác giả vào ô tìm kiếm.
3. User nhấn nút **Tìm kiếm**.
4. Hệ thống nhận request từ UI.
5. Hệ thống gửi truy vấn tìm kiếm đến DB (dựa vào cột `author` hoặc bảng `Authors`).
6. DB trả về danh sách sách phù hợp.
7. Hệ thống hiển thị danh sách sách kèm thông tin tác giả cho User.

---

**4. Luồng thay thế (Alternative Flows)**

* **AF1 – Không tìm thấy tác giả hoặc sách nào:**

  * Hệ thống hiển thị thông báo “Không tìm thấy sách của tác giả này”.
* **AF2 – Lỗi nhập liệu:**

  * Nếu User để trống hoặc nhập ký tự đặc biệt không hợp lệ, hệ thống yêu cầu nhập lại.
* **AF3 – Lỗi DB:**

  * Nếu DB không phản hồi, hiển thị thông báo “Hệ thống bận, vui lòng thử lại sau”.

---

**5. Điều kiện tiên quyết (Pre-condition)**

* Người dùng đang ở trang web/app có chức năng tìm kiếm.
* Bảng `Books` hoặc `Authors` trong DB có dữ liệu.

---

**6. Điều kiện hậu (Post-condition)**

* Hệ thống hiển thị danh sách sách theo tác giả (có thể rỗng).

---

**7. Yêu cầu đặc biệt (Special Requirements)**

* Hỗ trợ tìm kiếm không phân biệt hoa/thường.
* Hỗ trợ autocomplete tên tác giả.
* Nếu tác giả có nhiều sách, kết quả phải được phân trang (pagination).

---

👉 UC2 này khá giống UC1 (tìm theo tên sách), chỉ khác ở chỗ **trường dữ liệu tìm kiếm** (`title` vs `author`).

---

Bạn có muốn mình gộp **UC1 + UC2 + UC3 (lọc sách theo thể loại)** thành **một đặc tả tổng: "Tìm kiếm & Duyệt sách"** (Use Case cha → Use Case con) để dễ quản lý hơn không?


-----------------------





Câu hỏi này rất sát với thực tế trong **Thiết kế Hệ thống TMĐT** 👍.
Mình sẽ triển khai theo hướng **phân tích yêu cầu → thiết kế → Use Case**.

---

## 1. Phân tích yêu cầu người dùng

Yêu cầu:

> "Với vai trò người dùng, tôi muốn hoàn tiền sản phẩm dễ hơn."

Ý nghĩa:

* Người dùng mong muốn có một **quy trình trả hàng/hoàn tiền** nhanh gọn, ít thao tác, minh bạch.
* Thay vì phải gọi hotline hoặc gửi email, người dùng muốn **thao tác trực tuyến** ngay trên hệ thống.

---

## 2. Thiết kế hệ thống (mức khái niệm)

### Thành phần liên quan

* **Người dùng (Customer)**: Yêu cầu hoàn tiền cho đơn hàng.
* **Hệ thống TMĐT**: Ghi nhận yêu cầu, kiểm tra điều kiện (trong thời gian cho phép, trạng thái đơn hàng).
* **Nhân viên CSKH (Admin/Support)**: Xác nhận yêu cầu hoàn tiền.
* **Cổng thanh toán/Ngân hàng**: Thực hiện hoàn tiền cho người dùng.

### Luồng hoạt động

1. Người dùng chọn **Đơn hàng → Yêu cầu hoàn tiền**.
2. Hệ thống kiểm tra: đơn hàng đã giao, còn trong thời gian trả hàng, sản phẩm đủ điều kiện.
3. Người dùng upload lý do + minh chứng (ảnh, video).
4. Hệ thống tạo **Phiếu hoàn tiền** và gửi đến CSKH.
5. CSKH duyệt yêu cầu.
6. Hệ thống gửi lệnh hoàn tiền đến cổng thanh toán.
7. Người dùng nhận thông báo hoàn tiền thành công.

---

## 3. Use Case: “Hoàn tiền sản phẩm”

### Tên Use Case

Hoàn tiền sản phẩm

### Actor chính

* Customer (Người dùng)
* Support Staff (CSKH/Admin)
* Payment Gateway

### Mô tả ngắn gọn

Người dùng có thể gửi yêu cầu hoàn tiền trực tuyến cho sản phẩm đã mua, hệ thống sẽ xử lý và thực hiện hoàn tiền qua cổng thanh toán.

### Luồng chính (Main Flow)

1. Customer đăng nhập hệ thống.
2. Customer mở chi tiết đơn hàng → chọn “Yêu cầu hoàn tiền”.
3. Hệ thống hiển thị form nhập lý do + upload minh chứng.
4. Customer gửi yêu cầu.
5. Hệ thống kiểm tra điều kiện hoàn tiền.
6. Hệ thống tạo “Phiếu hoàn tiền” → gửi đến CSKH.
7. CSKH duyệt.
8. Hệ thống gọi API Payment Gateway → thực hiện hoàn tiền.
9. Hệ thống gửi thông báo cho Customer.

### Luồng thay thế (Alternative Flow)

* Nếu đơn hàng **không đủ điều kiện hoàn tiền** → hệ thống hiển thị thông báo từ chối, không gửi phiếu.
* Nếu Payment Gateway từ chối hoàn tiền → hệ thống thông báo lỗi và gợi ý liên hệ CSKH.

### Tiền điều kiện (Pre-condition)

* Customer đã mua hàng và có đơn hàng hoàn thành.
* Đơn hàng còn trong thời gian quy định cho phép hoàn tiền.

### Hậu điều kiện (Post-condition)

* Tiền được hoàn về tài khoản của Customer.
* Đơn hàng có trạng thái cập nhật thành “Đã hoàn tiền”.

---

👉 Như vậy, từ một **User Story** ("Tôi muốn hoàn tiền sản phẩm dễ hơn"), ta triển khai thành **Use Case Hoàn tiền sản phẩm**, có thể minh họa bằng **Use Case Diagram**:

* Actor: Customer, CSKH, Payment Gateway.
* Use Case: Hoàn tiền sản phẩm.

---

Bạn có muốn mình vẽ luôn **Use Case Diagram (PlantUML)** cho kịch bản này để minh họa trực quan không?



Ok 👍. Dựa trên yêu cầu *“Với vai trò người dùng, tôi muốn hoàn tiền sản phẩm dễ hơn”*, mình sẽ thiết kế **Use Case Diagram** mô tả các tác nhân (User, Admin/CSKH, Payment Gateway) và các chức năng liên quan.

### Các tác nhân (Actors):

* **User (Khách hàng)**: Yêu cầu hoàn tiền.
* **Customer Service (CSKH/Admin)**: Xác nhận yêu cầu, duyệt hoàn tiền.
* **Payment Gateway**: Xử lý giao dịch hoàn tiền.

### Các Use cases chính:

1. **Yêu cầu hoàn tiền** (User)
2. **Theo dõi trạng thái hoàn tiền** (User)
3. **Xác nhận và phê duyệt yêu cầu** (CSKH/Admin)
4. **Xử lý hoàn tiền qua cổng thanh toán** (Payment Gateway)
5. **Thông báo kết quả hoàn tiền** (System gửi tới User)

---

### PlantUML cho Use Case Diagram:

```plantuml
@startuml
left to right direction
actor User as U
actor "Customer Service" as CS
actor "Payment Gateway" as PG

rectangle "Refund System" {
    usecase "Yêu cầu hoàn tiền" as UC1
    usecase "Theo dõi trạng thái hoàn tiền" as UC2
    usecase "Xác nhận và phê duyệt yêu cầu" as UC3
    usecase "Xử lý hoàn tiền qua cổng thanh toán" as UC4
    usecase "Thông báo kết quả hoàn tiền" as UC5
}

U --> UC1
U --> UC2
CS --> UC3
UC3 --> UC4
PG --> UC4
UC4 --> UC5
UC5 --> U
@enduml
```

---

Bạn có muốn mình vẽ thêm **Sequence Diagram** cho luồng *User yêu cầu hoàn tiền → CSKH duyệt → Payment Gateway xử lý → Thông báo cho User* không?


Ok 👍. Mình sẽ vẽ **Sequence Diagram** cho luồng:

**User yêu cầu hoàn tiền → CSKH duyệt → Payment Gateway xử lý → Hệ thống thông báo cho User**.

---

### Các thành phần (Lifelines):

* **User** (Khách hàng)
* **Refund System** (Hệ thống TMĐT xử lý yêu cầu)
* **Customer Service** (Nhân viên CSKH/Admin)
* **Payment Gateway** (Cổng thanh toán)

---

### PlantUML Sequence Diagram

```plantuml
@startuml
actor User
participant "Refund System" as RS
participant "Customer Service" as CS
participant "Payment Gateway" as PG

User -> RS: Gửi yêu cầu hoàn tiền
RS -> CS: Chuyển yêu cầu duyệt hoàn tiền
CS -> RS: Phê duyệt hoàn tiền
RS -> PG: Gửi yêu cầu xử lý hoàn tiền
PG -> RS: Trả kết quả xử lý (Thành công/Thất bại)
RS -> User: Thông báo kết quả hoàn tiền

@enduml
```

---

👉 Biểu đồ này thể hiện quy trình từ khi **User gửi yêu cầu** cho đến khi **nhận được thông báo hoàn tiền** sau khi hệ thống + CSKH + Payment Gateway xử lý xong.

Bạn có muốn mình mở rộng thêm **trường hợp yêu cầu bị từ chối** (ví dụ: quá thời hạn, sai lý do, không hợp lệ) trong Sequence Diagram này không?


Bạn nhận xét rất đúng 👌.

Thực tế:

* **Activity Diagram**: thường mô tả *luồng công việc* (workflow) → nhìn giống các bước tuần tự từ A → B → C.
* **Sequence Diagram**: tập trung vào *tương tác giữa các đối tượng (lifelines)* theo **trục thời gian dọc**. Nó không phải chỉ liệt kê các bước tuần tự, mà phải nhấn mạnh:

  * Ai gọi ai (User → Refund System).
  * Tin nhắn/truyền thông nào đi qua.
  * Thứ tự thời gian từ trên xuống dưới.
  * Có thể thêm *alt/opt* để thể hiện nhánh điều kiện.

👉 Vậy code PlantUML mình đưa bạn ở trên **đúng là Sequence Diagram**, nhưng vì luồng đơn giản nên nó trông hơi giống Activity.

Ví dụ cải tiến để nhìn rõ hơn "chất Sequence":

```plantuml
@startuml
actor User
participant "Refund System" as RS
participant "Customer Service" as CS
participant "Payment Gateway" as PG

User -> RS: RequestRefund(orderId)
RS -> CS: ValidateRefundRequest(orderId)
CS -> RS: ApproveRefund(status=Approved)

alt Refund Approved
    RS -> PG: ProcessRefund(orderId, amount)
    PG --> RS: RefundResult(success)
    RS -> User: Notify(success)
else Refund Rejected
    CS -> RS: RejectRefund(status=Rejected)
    RS -> User: Notify(rejected)
end

@enduml
```

✨ Điểm khác biệt:

* Có **messages với tham số** (RequestRefund(orderId), ProcessRefund(...)).
* Có **alt/else** thể hiện nhánh xử lý (Approved vs Rejected).
* Các actor/lifelines rõ ràng → đúng chất *Sequence Diagram*.

---

👉 Bạn có muốn mình vẽ thêm một bản **Activity Diagram** song song với Sequence Diagram này để bạn so sánh trực quan sự khác biệt không?


Rất hay 👍. Mình sẽ làm song song cả **Sequence Diagram** và **Activity Diagram** cho cùng một tình huống *“User yêu cầu hoàn tiền”* để bạn thấy rõ sự khác biệt.

---

## 1. Sequence Diagram (tập trung vào *ai* giao tiếp với *ai*)

```plantuml
@startuml
actor User
participant "Refund System" as RS
participant "Customer Service" as CS
participant "Payment Gateway" as PG

User -> RS: RequestRefund(orderId)
RS -> CS: ValidateRefundRequest(orderId)
CS -> RS: ApproveRefund(status=Approved)

alt Refund Approved
    RS -> PG: ProcessRefund(orderId, amount)
    PG --> RS: RefundResult(success)
    RS -> User: Notify(success)
else Refund Rejected
    CS -> RS: RejectRefund(status=Rejected)
    RS -> User: Notify(rejected)
end
@enduml
```

---

## 2. Activity Diagram (tập trung vào *luồng công việc*)

```plantuml
@startuml
start

:User gửi yêu cầu hoàn tiền;

:Refund System nhận yêu cầu;

:Chuyển yêu cầu đến CSKH;

if (CSKH duyệt?) then (Được duyệt)
    :Refund System gửi yêu cầu hoàn tiền đến Payment Gateway;
    :Payment Gateway xử lý hoàn tiền;
    :Refund System thông báo "Hoàn tiền thành công" cho User;
else (Bị từ chối)
    :Refund System thông báo "Yêu cầu bị từ chối" cho User;
endif

stop
@enduml
```

---

### 🔑 So sánh

* **Sequence Diagram**: nhấn mạnh *đối tượng tham gia* (User, Refund System, CSKH, Payment Gateway) và *message* trao đổi → phù hợp cho **thiết kế hệ thống, API, giao tiếp giữa các module**.
* **Activity Diagram**: nhấn mạnh *luồng công việc* và *điều kiện nhánh* → phù hợp cho **mô tả quy trình nghiệp vụ** từ góc nhìn tổng thể.

---

👉 Bạn có muốn mình thêm **Use Case Diagram** để tạo bộ “3 trong 1” (Use Case + Sequence + Activity) cho kịch bản hoàn tiền này không?


Câu hỏi này rất thực tế 👌.

Nếu mục tiêu là **bắt đầu code** thì chỉ vẽ Sequence Diagram **thường chưa đủ**, vì:

* **Sequence Diagram** giúp bạn thấy **luồng tương tác giữa các thành phần/đối tượng**, nhưng không nói chi tiết về **cấu trúc dữ liệu** hay **API**.
* Lập trình viên khi code cần biết:

  1. **Use Case Diagram** → để hiểu phạm vi & ai dùng chức năng gì.
  2. **Sequence Diagram** → để hiểu flow nghiệp vụ giữa các thành phần.
  3. **Class Diagram / ERD** → để thiết kế **database và logic nghiệp vụ**.
  4. **API Design (REST/GraphQL)** → để biết endpoint, input/output cụ thể.

---

### Ví dụ với chức năng **Hoàn tiền**:

* **Use Case**: “Người dùng yêu cầu hoàn tiền” (actor: User, CSKH).
* **Sequence Diagram**: mô tả các bước User → Refund System → CSKH → Payment Gateway.
* **Class Diagram**: có lớp `Order`, `RefundRequest`, `PaymentTransaction`, với quan hệ và thuộc tính.
* **ERD**: bảng `orders`, `refunds`, `payment_transactions`.
* **API**:

  * `POST /api/refunds` → gửi yêu cầu hoàn tiền.
  * `PUT /api/refunds/{id}/approve` → CSKH duyệt.
  * `GET /api/refunds/{id}` → lấy trạng thái hoàn tiền.

---

👉 Nếu chỉ muốn **làm prototype nhỏ** → Sequence Diagram + API spec có thể tạm đủ.
👉 Nếu làm **hệ thống lớn, nhiều người code chung** → nên có đầy đủ bộ (Use Case + Sequence + Class/ERD + API).

---

Bạn muốn mình minh họa luôn **Class Diagram + ERD + API cho chức năng Hoàn tiền** để thấy sự liên kết từ phân tích → đến code không?


Hay 👍, mình giải thích rõ **logic nghiệp vụ (business logic)** nhé.

---

### 1. Logic nghiệp vụ là gì?

* Là **tập hợp các quy tắc và xử lý** mô tả *hệ thống phải hoạt động thế nào* để đáp ứng **nghiệp vụ thực tế**.
* Không phải giao diện (UI) hay lưu trữ (DB), mà là **các điều kiện, ràng buộc, quy tắc xử lý dữ liệu**.
* Thường được viết trong **Service Layer** hoặc **Domain Layer** của hệ thống.

---

### 2. Ví dụ: Chức năng **Hoàn tiền đơn hàng** trong TMĐT

#### Luồng logic nghiệp vụ

1. Người dùng gửi yêu cầu hoàn tiền.
2. Hệ thống kiểm tra điều kiện:

   * Đơn hàng đã giao chưa?
   * Yêu cầu còn trong thời hạn hoàn tiền (ví dụ: 7 ngày)?
   * Sản phẩm có nằm trong danh mục cho phép hoàn tiền không?
   * Số tiền hoàn <= số tiền đã thanh toán.
3. Nếu **hợp lệ** → tạo record `RefundRequest` với trạng thái `"Pending"`.
4. CSKH xem xét và **duyệt / từ chối**.
5. Nếu duyệt → gọi Payment Gateway để chuyển tiền về tài khoản của User.
6. Hệ thống cập nhật trạng thái Refund và gửi thông báo cho User.

---

#### Một đoạn **pseudocode (giả mã)** cho logic nghiệp vụ:

```python
def request_refund(order_id, user_id):
    order = Order.get(order_id)
    
    if not order:
        raise Exception("Đơn hàng không tồn tại")
    
    if order.user_id != user_id:
        raise Exception("Không thể hoàn tiền cho đơn của người khác")
    
    if order.status != "DELIVERED":
        raise Exception("Chỉ hoàn tiền cho đơn đã giao thành công")
    
    if days_between(order.delivered_at, today()) > 7:
        raise Exception("Đã quá hạn hoàn tiền (7 ngày)")
    
    refund = RefundRequest(
        order_id=order_id,
        user_id=user_id,
        amount=order.amount,
        status="PENDING"
    )
    refund.save()
    return refund
```

---

### 3. Tóm lại

* **Logic nghiệp vụ** là cái “luật chơi” → kiểm soát hệ thống hoạt động đúng nghiệp vụ (business).
* Nó nằm ở giữa UI và DB.
* Ví dụ trong hoàn tiền: kiểm tra hạn mức, trạng thái đơn hàng, gọi Payment Gateway, cập nhật trạng thái.

---

👉 Bạn có muốn mình viết thêm **Class Diagram cho Refund** để mô hình hóa luôn phần business logic này không?


Ok 👍, mình sẽ mô hình hóa **Class Diagram cho Refund** để minh họa rõ phần **business logic** trong hệ thống TMĐT.

---

## 🎯 Các lớp liên quan đến Refund

* **User**: Người dùng yêu cầu hoàn tiền.
* **Order**: Đơn hàng gốc mà User đã mua.
* **RefundRequest**: Yêu cầu hoàn tiền (trạng thái: Pending, Approved, Rejected, Completed).
* **PaymentTransaction**: Giao dịch thanh toán (bao gồm hoàn tiền).
* **CustomerService**: Nhân viên duyệt yêu cầu hoàn tiền.
* **PaymentGateway**: Cổng thanh toán bên thứ 3.

---

## 📌 PlantUML Class Diagram

```plantuml
@startuml
class User {
    +userId: int
    +name: string
    +email: string
}

class Order {
    +orderId: int
    +status: string
    +amount: float
    +deliveredAt: Date
    +isRefundEligible(): bool
}

class RefundRequest {
    +refundId: int
    +status: string
    +amount: float
    +createdAt: Date
    +approve(): void
    +reject(reason: string): void
}

class PaymentTransaction {
    +transactionId: int
    +type: string
    +amount: float
    +status: string
    +createdAt: Date
}

class CustomerService {
    +csId: int
    +name: string
    +approveRefund(refundId: int): void
    +rejectRefund(refundId: int, reason: string): void
}

class PaymentGateway {
    +processRefund(transactionId: int, amount: float): bool
}

User "1" --> "*" Order
Order "1" --> "0..1" RefundRequest
RefundRequest "1" --> "1" PaymentTransaction
CustomerService --> RefundRequest
RefundRequest --> PaymentGateway
@enduml
```

---

## 🔑 Ý nghĩa

* Một **User** có thể có nhiều **Order**.
* Một **Order** có thể liên kết với **một RefundRequest** (nếu phát sinh hoàn tiền).
* **RefundRequest** tạo ra **PaymentTransaction** kiểu `"REFUND"`.
* **CustomerService** quyết định approve/reject.
* **PaymentGateway** xử lý refund và trả kết quả.

---

👉 Bạn có muốn mình viết tiếp **ERD (các bảng CSDL)** tương ứng với Class Diagram này để dễ triển khai code không?


Tốt 👍. Giờ mình sẽ chuyển từ **Class Diagram** sang **ERD (Entity Relationship Diagram)** để thiết kế CSDL cho chức năng **Refund**.

---

## 📌 Các bảng chính trong ERD

1. **users**

   * Lưu thông tin người dùng.

2. **orders**

   * Lưu thông tin đơn hàng.

3. **refund\_requests**

   * Lưu yêu cầu hoàn tiền.

4. **payment\_transactions**

   * Lưu các giao dịch thanh toán (bao gồm cả refund).

5. **customer\_service**

   * Lưu thông tin nhân viên CSKH xử lý refund.

---

## 🗄️ Cấu trúc bảng (gợi ý)

```sql
-- Bảng người dùng
CREATE TABLE users (
    user_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    email VARCHAR(100) UNIQUE
);

-- Bảng đơn hàng
CREATE TABLE orders (
    order_id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT,
    status VARCHAR(50), -- e.g. PENDING, DELIVERED, CANCELLED
    amount DECIMAL(10,2),
    delivered_at DATETIME,
    FOREIGN KEY (user_id) REFERENCES users(user_id)
);

-- Bảng yêu cầu hoàn tiền
CREATE TABLE refund_requests (
    refund_id INT PRIMARY KEY AUTO_INCREMENT,
    order_id INT,
    amount DECIMAL(10,2),
    status VARCHAR(50), -- e.g. PENDING, APPROVED, REJECTED, COMPLETED
    reason TEXT,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    approved_by INT NULL, -- CSKH duyệt
    FOREIGN KEY (order_id) REFERENCES orders(order_id),
    FOREIGN KEY (approved_by) REFERENCES customer_service(cs_id)
);

-- Bảng giao dịch thanh toán
CREATE TABLE payment_transactions (
    transaction_id INT PRIMARY KEY AUTO_INCREMENT,
    refund_id INT NULL,
    order_id INT,
    type VARCHAR(50), -- e.g. PAYMENT, REFUND
    amount DECIMAL(10,2),
    status VARCHAR(50), -- e.g. SUCCESS, FAILED
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (refund_id) REFERENCES refund_requests(refund_id),
    FOREIGN KEY (order_id) REFERENCES orders(order_id)
);

-- Bảng nhân viên CSKH
CREATE TABLE customer_service (
    cs_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    email VARCHAR(100)
);
```

---

## 📌 ERD bằng PlantUML

```plantuml
@startuml
entity "users" {
  *user_id : INT
  --
  name : VARCHAR
  email : VARCHAR
}

entity "orders" {
  *order_id : INT
  --
  user_id : INT
  status : VARCHAR
  amount : DECIMAL
  delivered_at : DATETIME
}

entity "refund_requests" {
  *refund_id : INT
  --
  order_id : INT
  amount : DECIMAL
  status : VARCHAR
  reason : TEXT
  created_at : DATETIME
  approved_by : INT
}

entity "payment_transactions" {
  *transaction_id : INT
  --
  refund_id : INT
  order_id : INT
  type : VARCHAR
  amount : DECIMAL
  status : VARCHAR
  created_at : DATETIME
}

entity "customer_service" {
  *cs_id : INT
  --
  name : VARCHAR
  email : VARCHAR
}

users ||--o{ orders : "has"
orders ||--o{ refund_requests : "may have"
refund_requests ||--o{ payment_transactions : "generates"
orders ||--o{ payment_transactions : "relates"
customer_service ||--o{ refund_requests : "approves"
@enduml
```

---

✅ Bây giờ bạn đã có:

* **Class Diagram** (logic nghiệp vụ).
* **ERD** (thiết kế CSDL).

👉 Bạn có muốn mình viết tiếp **thiết kế REST API cho Refund** (endpoint + input/output JSON) để khớp từ ERD → code không?


Câu hỏi rất chuẩn 👌. Đây chính là **kỹ năng phân tích yêu cầu & mô hình hóa** trong thiết kế hệ thống.
Mình sẽ giải thích cách **xác định các trường dữ liệu (attributes/columns)** trong **Class Diagram** và **ERD**, dựa trên **các loại diagram và thành phần**.

---

## 🔑 1. Nguồn thông tin để lấy dữ liệu

Khi thiết kế, kỹ sư thường dựa vào:

1. **Use Case Diagram + Use Case Description**

   * Cho biết **chức năng hệ thống** và **ai làm gì**.
   * Từ đó suy ra dữ liệu nào cần để thực hiện use case.

2. **Sequence Diagram (hoặc Activity Diagram)**

   * Cho thấy **luồng thông điệp (message)** giữa các đối tượng.
   * Các tham số truyền đi thường chính là dữ liệu cần lưu (ví dụ: `orderId`, `amount`, `status`).

3. **Business Logic / Quy tắc nghiệp vụ**

   * Quy định điều kiện xử lý → đòi hỏi thêm trường dữ liệu.
   * Ví dụ: “hoàn tiền trong vòng 7 ngày” → cần trường `delivered_at` trong `orders`.

4. **Class Diagram**

   * Mô tả đối tượng trong domain → mỗi class có **thuộc tính (attributes)** → chuyển thành **cột trong bảng ERD**.

---

## 🔎 2. Ví dụ: Refund

### (a) Use Case: *Người dùng yêu cầu hoàn tiền*

* Input: `orderId`, `reason`.
* Output: `status` (Pending, Approved...).

👉 Suy ra `refund_requests` cần có `refund_id`, `order_id`, `reason`, `status`.

---

### (b) Sequence Diagram

```
User -> Refund System: RequestRefund(orderId)
Refund System -> CS: ValidateRefund(orderId)
CS -> Refund System: ApproveRefund(status)
Refund System -> PG: ProcessRefund(orderId, amount)
```

👉 Ta thấy cần các dữ liệu: `orderId`, `status`, `amount`.

---

### (c) Business Rules

* “Chỉ hoàn tiền trong vòng 7 ngày kể từ khi giao hàng.”
  👉 Ta cần lưu `delivered_at` trong bảng `orders`.

* “CSKH có thể từ chối với lý do.”
  👉 Ta cần trường `reason` trong `refund_requests`.

---

### (d) Class Diagram → ERD

* Class `RefundRequest` có: `refundId`, `status`, `amount`, `createdAt`.
* Class `Order` có: `orderId`, `status`, `amount`, `deliveredAt`.
* Mapping qua ERD: mỗi **attribute** → **column**.

---

## 📌 Tóm lại quy trình suy luận

1. **Xác định chức năng (Use Case)** → biết cần quản lý dữ liệu nào.
2. **Xem Sequence Diagram** → lấy các tham số trong message làm gợi ý cho thuộc tính.
3. **Xem Business Rules** → thêm các trường dữ liệu phục vụ ràng buộc nghiệp vụ.
4. **Class Diagram** → chuyển attributes thành bảng & cột trong ERD.

---

👉 Nói cách khác:

* **Use Case** cho bạn biết *cái gì cần lưu*.
* **Sequence Diagram** cho bạn biết *cần truyền dữ liệu gì giữa các thành phần*.
* **Business Rules** cho bạn biết *trường nào cần để kiểm tra logic*.
* **Class/ERD** là kết quả cuối cùng của việc gom và chuẩn hóa dữ liệu từ 3 nguồn trên.

---

Bạn có muốn mình làm một **bảng mapping minh họa** (Use Case → Message trong Sequence → Attribute trong Class → Column trong ERD) cho ví dụ Refund này không?


Rồi 👍. Mình sẽ lập **bảng mapping minh họa** cho ví dụ **Refund** để bạn thấy rõ cách dữ liệu được “dẫn dắt” từ yêu cầu nghiệp vụ → đến thiết kế CSDL.

---

## 📌 Bảng Mapping dữ liệu cho chức năng **Refund**

| Use Case (Yêu cầu)                                | Message trong Sequence Diagram                   | Attribute trong Class Diagram                  | Column trong ERD (`SQL table`)                     |
| ------------------------------------------------- | ------------------------------------------------ | ---------------------------------------------- | -------------------------------------------------- |
| User gửi yêu cầu hoàn tiền cho đơn hàng           | `RequestRefund(orderId, reason)`                 | `RefundRequest.refundId`, `orderId`, `reason`  | `refund_requests.refund_id`, `order_id`, `reason`  |
| CSKH duyệt yêu cầu hoàn tiền                      | `ApproveRefund(status)` / `RejectRefund(reason)` | `RefundRequest.status`, `RefundRequest.reason` | `refund_requests.status`, `refund_requests.reason` |
| Refund System kiểm tra số tiền đơn hàng           | `ProcessRefund(orderId, amount)`                 | `Order.amount`, `RefundRequest.amount`         | `orders.amount`, `refund_requests.amount`          |
| Kiểm tra thời gian giao hàng để xét hạn hoàn tiền | (Điều kiện nghiệp vụ, không truyền trực tiếp)    | `Order.deliveredAt`                            | `orders.delivered_at`                              |
| Lưu trạng thái giao dịch hoàn tiền với PG         | `RefundResult(success/fail)`                     | `PaymentTransaction.status`                    | `payment_transactions.status`                      |
| Lưu chi tiết giao dịch thanh toán                 | `ProcessRefund(orderId, amount)`                 | `PaymentTransaction.transactionId`, `amount`   | `payment_transactions.transaction_id`, `amount`    |
| CSKH chịu trách nhiệm phê duyệt                   | (Không phải message, nhưng actor tham gia)       | `CustomerService.csId`, `name`                 | `customer_service.cs_id`, `name`                   |
| Ghi nhận thời điểm tạo yêu cầu                    | (Tự sinh trong hệ thống khi lưu)                 | `RefundRequest.createdAt`                      | `refund_requests.created_at`                       |

---

## 🔑 Nhận xét

* **Use Case** → chỉ nói “người dùng muốn gì” (vd: hoàn tiền).
* **Sequence Diagram** → cho biết **cần trao đổi dữ liệu gì** để thực hiện yêu cầu.
* **Class Diagram** → gom dữ liệu thành **thuộc tính đối tượng** (Order, RefundRequest, PaymentTransaction...).
* **ERD** → cuối cùng chuyển thành **cột trong bảng CSDL**.

---

👉 Bảng này giúp bạn **traceability** (truy vết) từ nghiệp vụ → thiết kế → database.
Nếu thầy/cô hỏi “tại sao có cột `delivered_at` trong bảng orders?” → bạn trả lời: **để phục vụ business rule hoàn tiền trong 7 ngày**.

---

Bạn có muốn mình làm thêm một **sơ đồ trace (chuỗi liên kết)** trực quan từ Use Case → Sequence → Class → ERD để dễ trình bày trong báo cáo không?


Câu hỏi rất hay 👍. Khi thiết kế **thuộc tính (attributes) trong Class Diagram**, bạn cần dựa trên nhiều nguồn thông tin khác nhau để đảm bảo đầy đủ và đúng mục đích. Mình sẽ giải thích theo quy trình chuẩn trong phân tích & thiết kế hệ thống:

---

## 🔹 1. Xuất phát từ **Use Case**

* **Use Case** mô tả chức năng người dùng cần (ví dụ: *Refund Order*).
* Từ các **dòng mô tả luồng chính & luồng thay thế**, ta thấy được:

  * Các thông tin cần nhập từ người dùng (input).
  * Các thông tin cần hiển thị lại (output).
  * Các điều kiện kiểm tra (validation).

👉 Đây chính là những ứng viên ban đầu để trở thành **thuộc tính trong Class**.

---

## 🔹 2. Xem **Sequence Diagram**

* **Messages** trong Sequence cho thấy:

  * Hệ thống gọi đến các đối tượng nào.
  * Tham số truyền đi là gì.
    👉 Những tham số này gợi ý **dữ liệu cần lưu tạm hoặc lâu dài**, từ đó thành thuộc tính của Class.

---

## 🔹 3. Xem xét **Domain Model / Business Concepts**

* Nếu bạn có **Domain Model** (biểu đồ khái niệm nghiệp vụ), hãy lấy các **noun (danh từ)** trong mô tả nghiệp vụ:

  * *Refund, Order, Payment, Customer, Staff…*
    👉 Mỗi danh từ trở thành **Class**, còn đặc điểm mô tả nó trở thành **Attribute**.

---

## 🔹 4. Xác định thuộc tính qua **các loại thông tin cần quản lý**

Ví dụ với **Refund**:

* **Thông tin định danh**: `refund_id` (khóa chính).
* **Thông tin liên kết**: `order_id`, `payment_id`, `customer_id`.
* **Thông tin nghiệp vụ**: `refund_amount`, `reason`, `status`.
* **Thông tin thời gian**: `created_at`, `processed_at`.
* **Thông tin tác nhân**: `processed_by (staff_id)`.

---

## 🔹 5. Mapping sang ERD

* Mỗi **thuộc tính trong Class** → trở thành **column trong bảng** tương ứng trong ERD.
* Khóa chính, khóa ngoại được xác định dựa vào **mối quan hệ giữa các Class** (association, aggregation, composition).

---

## 🔹 6. Checklist khi chọn thuộc tính

✅ Có cần thiết cho Use Case không?
✅ Có lưu trữ lâu dài không?
✅ Có tham gia vào quan hệ giữa các Class không?
✅ Có phải thông tin tính toán được (nếu có thể tính toán → không nên lưu trực tiếp)?

---

👉 Tóm lại:

* **Use Case** → cho biết dữ liệu người dùng cần nhập/xuất.
* **Sequence** → cho biết dữ liệu hệ thống trao đổi.
* **Domain Model** → cho biết đặc điểm bản chất của đối tượng.
* **Class Diagram** → gom nhóm và gắn kết thành thuộc tính.
* **ERD** → chuyển thành bảng và cột.

---

Bạn có muốn mình làm **bảng minh họa quy trình xác định thuộc tính Refund** (từ Use Case → Sequence → Class → ERD) giống như một "traceability table" không?


Câu hỏi này thuộc về **thứ tự thiết kế UML** – khá nhiều bạn cũng thắc mắc giống bạn 👍.
Mình giải thích theo 2 góc nhìn: **chuẩn lý thuyết UML** và **thực tế triển khai hệ thống**.

---

## 🔹 1. Trong lý thuyết UML (quy trình thác nước / RUP truyền thống)

1. **Use Case Diagram**: xác định chức năng hệ thống.
2. **Class Diagram (Domain Model ban đầu)**: phác họa các khái niệm nghiệp vụ (Order, Refund, Customer…).
3. **Sequence Diagram**: mô tả luồng tương tác của các đối tượng trong một Use Case cụ thể.
4. **Cập nhật lại Class Diagram**: sau khi có Sequence, bạn bổ sung thêm phương thức, quan hệ, thuộc tính.

👉 Tức là: **Class vẽ trước → Sequence vẽ sau → rồi quay lại refine Class**.

---

## 🔹 2. Trong thực tế (Agile / Iterative)

* Thường **Sequence** hoặc **Activity** được phác thảo trước từ Use Case để hiểu rõ logic.
* Sau đó mới rút ra các **Class** từ các message, tham số, actor liên quan.
* Rồi quay lại chỉnh sửa Sequence nếu thấy thiếu class/thuộc tính.

👉 Tức là: **Sequence và Class có thể làm song song**, nhưng thường **Sequence được thử trước cho từng Use Case**, rồi mới consolidate thành Class Diagram chuẩn.

---

## 🔹 3. Kết luận

* Nếu đi **theo sách vở** → Vẽ **Class Diagram khái niệm** trước, rồi Sequence, rồi refine Class.
* Nếu đi **theo thực tế triển khai** → Có thể phác **Sequence sơ bộ trước**, sau đó mới hoàn thiện Class Diagram.

📌 Nguyên tắc:

* **Class Diagram** = cái nhìn **tĩnh (static)** → dữ liệu và cấu trúc hệ thống.
* **Sequence Diagram** = cái nhìn **động (dynamic)** → hành vi, luồng xử lý.

👉 Hai cái này **bổ sung qua lại**. Không phải cái nào tuyệt đối trước sau, mà là **iterative (lặp đi lặp lại)**.

---

Bạn có muốn mình vẽ timeline **chuẩn quy trình thiết kế Refund Use Case** (Use Case → Sequence → Class → ERD) để dễ hình dung hơn không?


Ok 👌 mình sẽ vẽ **timeline chuẩn cho Refund Use Case** theo quy trình thiết kế hệ thống.

---

# 📝 Timeline thiết kế Use Case "Refund"

```mermaid
timeline
    title Quy trình thiết kế Refund Use Case
    section Phân tích yêu cầu
      Xác định Use Case "Yêu cầu hoàn tiền" : 2025-09-08
      Định nghĩa Actor (User, CSKH, Payment Gateway) : 2025-09-08
      Viết kịch bản nghiệp vụ (User yêu cầu → CSKH duyệt → Gateway xử lý → User nhận thông báo) : 2025-09-08
    section Thiết kế hành vi (Behavior)
      Vẽ Sequence Diagram cho Use Case Refund : 2025-09-09
      Mô tả các message (requestRefund(), approveRefund(), processPayment(), notifyUser()) : 2025-09-09
    section Thiết kế cấu trúc (Structure)
      Xây dựng Class Diagram từ message + domain concepts : 2025-09-10
      Định nghĩa các lớp: RefundRequest, Order, PaymentTransaction, User : 2025-09-10
      Thêm attributes & methods (status, amount, refundDate…) : 2025-09-10
    section Thiết kế dữ liệu
      Chuyển từ Class Diagram sang ERD : 2025-09-11
      Tạo các bảng Refund, Order, Payment, User : 2025-09-11
      Xác định khóa chính – khóa ngoại – ràng buộc : 2025-09-11
```

---

## 📌 Giải thích từng bước

1. **Use Case** → định nghĩa yêu cầu nghiệp vụ, ai tham gia.
2. **Sequence Diagram** → làm rõ luồng xử lý theo thời gian.
3. **Class Diagram** → trích xuất từ các message + khái niệm nghiệp vụ thành class, method, attribute.
4. **ERD** → chuyển đổi từ Class Diagram sang mô hình dữ liệu quan hệ (database).

👉 Đây chính là **dòng chảy chuẩn** từ yêu cầu người dùng → hành vi → cấu trúc → dữ liệu.

---

Bạn có muốn mình **minh họa luôn bằng sơ đồ cụ thể cho Refund Use Case** (Use Case, Sequence, Class, ERD) theo timeline này không?


Câu hỏi hay 👍. Trong quy trình phát triển phần mềm (ví dụ theo **SDLC hoặc Agile**), các vai trò thường phân chia như sau:

---

## 🧑‍💼 **BA (Business Analyst) – Phân tích nghiệp vụ**

* **Nhiệm vụ chính:** Hiểu yêu cầu của khách hàng & chuyển thành đặc tả hệ thống.
* **Kết quả (Artifacts):**

  * Tài liệu yêu cầu (SRS, BRD).
  * **Use Case Diagram** & mô tả kịch bản.
  * User Story (nếu Agile).
  * Quy tắc nghiệp vụ (Business Rules).
  * Đặc tả luồng nghiệp vụ (Business Process / Activity Diagram).
* 👉 BA **không đi sâu vào code**, mà làm rõ *cần làm gì* và *tại sao cần làm*.

---

## 👨‍💻 **System Analyst / Software Engineer (Designer / Architect)**

* **Nhiệm vụ chính:** Thiết kế giải pháp kỹ thuật từ yêu cầu BA.
* **Kết quả (Artifacts):**

  * **Sequence Diagram** (mô tả interaction).
  * **Class Diagram** (mô hình đối tượng & logic nghiệp vụ).
  * **ERD** (cơ sở dữ liệu).
  * Thiết kế API (REST/GraphQL).
  * Kiến trúc hệ thống (component diagram, deployment diagram).
* 👉 Engineer tập trung vào *thiết kế chi tiết hệ thống* để coder có thể triển khai.

---

## 👩‍💻 **Coder / Developer**

* **Nhiệm vụ chính:** Hiện thực hóa thiết kế thành phần mềm chạy được.
* **Kết quả (Artifacts):**

  * Code back-end (Java, .NET, Node.js, Python…).
  * Code front-end (React, Angular, Flutter…).
  * Database schema (SQL migration, ORM model).
  * Unit Test, Integration Test.
* 👉 Developer tập trung vào *làm thế nào* để chạy được & đúng theo thiết kế.

---

## 🔄 Ví dụ cho **Refund Use Case**

* **BA**: Viết yêu cầu "Người dùng muốn hoàn tiền dễ dàng hơn", vẽ Use Case Diagram.
* **Engineer**: Vẽ Sequence Diagram (User → Refund System → Payment Gateway), tạo Class Diagram (RefundRequest, Payment, User), ERD (Refund table, Payment table).
* **Coder**:

  * Viết API `POST /refunds` để tạo refund request.
  * Viết logic duyệt refund.
  * Tích hợp Payment Gateway (PayPal/VNPAY).
  * Cập nhật DB, gửi notification cho user.

---

👉 Tóm lại:

* **BA = Cái gì? (What, Why)**
* **Engineer = Thiết kế ra sao? (How – at design level)**
* **Coder = Cách code chi tiết? (How – at implementation level)**

---

Bạn có muốn mình làm **bảng phân công nhiệm vụ BA – Engineer – Coder cho toàn bộ quy trình Refund Use Case** để nhìn trực quan không?




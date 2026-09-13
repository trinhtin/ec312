Khi theo đuổi chiến lược **Mua giải pháp có sẵn (Buy - COTS/SaaS như Shopify Plus, Haravan, Magento/Adobe Commerce)** rồi **Tự chỉnh sửa/Tùy biến (Customize)** theo đặc thù doanh nghiệp, **GAP-Analysis (Phân tích khoảng trống)** đóng vai trò chiếc cầu nối sống còn. Phương pháp này xác định chính xác những điểm mà phần mềm sẵn có **không đáp ứng được (Gaps)**, từ đó cân nhắc phương án giải quyết (lập trình tùy chỉnh, thay đổi quy trình nghiệp vụ, hoặc chấp nhận bỏ qua).

Quy trình thực hiện GAP-Analysis cho chiến lược Buy & Customize gồm các bước chi tiết sau:

---

### Bước 1: Thu thập và chuẩn hóa "Baseline" (Tính năng có sẵn của hệ thống Buy)

Trước khi so sánh, bạn phải nắm rõ bức tranh kỹ thuật của giải pháp định mua (Out-of-the-box Features).

* Liệt kê các tính năng cốt lõi mà phần mềm đó **đã làm sẵn rất tốt** (ví dụ: quảncheckout tiêu chuẩn, quản lý giỏ hàng, giao diện mobile responsive cơ bản, cơ chế phân quyền RBAC mặc định).
* Xác định rõ **kiến trúc mở rộng** của nền tảng đó: Có hỗ trợ Marketplace app/plugin không? Có cung cấp REST API/GraphQL mạnh mẽ để custom code không? Giới hạn kiến trúc là gì (ví dụ: hệ thống Cloud SaaS thường khó can thiệp sâu vào tầng database gốc).

### Bước 2: Thiết lập ma trận so sánh GAP-Analysis Matrix

Đưa toàn bộ User Requirements thu được từ các phòng ban ở bước trước vào một ma trận đối chiếu. Mỗi yêu cầu sẽ được đánh giá theo 4 trạng thái:

| Mã Yêu Cầu | Yêu cầu nghiệp vụ (User Requirement) | Tính năng có sẵn (Out-of-the-box) | Trạng thái (Gap Status) | Giải pháp xử lý đề xuất |
| --- | --- | --- | --- | --- |
| **SAL-01** | Tạo mã giảm giá tự động theo sinh nhật khách hàng | Chỉ hỗ trợ tạo mã thủ công hoặc theo chiến dịch chung | **Functional Gap** | Mua app bên thứ ba tích hợp hoặc viết custom extension gọi API. |
| **WH-02** | Đồng bộ tồn kho real-time đa kho với hệ thống ERP nội bộ | Hệ thống chỉ có sẵn tính năng quản lý tồn kho đơn lẻ trên web | **Integration Gap** | Viết middleware đồng bộ qua API giữa giải pháp TMĐT và ERP. |
| **ACC-03** | Tự động xuất hóa đơn điện tử tích hợp nhà mạng MISA theo định dạng riêng | Chỉ hỗ trợ xuất hóa đơn tiêu chuẩn qua cổng trung gian | **Process Gap** | Tùy biến mã nguồn backend hoặc đổi quy trình kế toán cho khớp hệ thống. |

### Bước 3: Phân loại các khoảng trống (Gaps) để tìm hướng xử lý

Các khoảng trống phát hiện thường rơi vào 3 nhóm chính. Mỗi nhóm đòi hỏi một chiến lược giải quyết khác nhau:

#### 1. Integration Gaps (Khoảng trống về tích hợp)

* **Biểu hiện:** Hệ thống TMĐT sẵn có không kết nối sẵn với ERP, WMS, hoặc cổng thanh toán nội địa đặc thù (ví dụ: VETC, các cổng chuyển khoản ngân hàng nội địa ngách).
* **Hướng xử lý:** Xây dựng các lớp dịch vụ trung gian (Middleware/API Connector) hoặc tận dụng các Webhook/App sẵn có để thông dữ liệu qua lại.

#### 2. Functional Gaps (Khoảng trống về tính năng nghiệp vụ)

* **Biểu hiện:** Nghiệp vụ đặc thù của doanh nghiệp mà nền tảng quốc tế hoặc nền tảng phổ thông không có sẵn (ví dụ: cơ chế tính chiết khấu hoa hồng phức tạp cho hệ thống đại lý đa cấp, quy trình bảo hành điện tử gắn với số IMEI thiết bị).
* **Hướng xử lý:**
* *Phương án A (Code custom):* Lập trình thêm module riêng (Custom Plugin/Module).
* *Phương án B (Mua Marketplace App):* Tận dụng các ứng dụng có sẵn trên kho ứng dụng của nền tảng (Shopify App Store, Magento Marketplace) nếu có bên thứ ba phát triển gần giống.



#### 3. Process Gaps (Khoảng trống về quy trình vận hành)

* **Biểu hiện:** Phần mềm bắt buộc doanh nghiệp phải làm theo quy trình chuẩn của nó, trái ngược với quy trình đang vận hành thực tế.
* **Hướng xử lý:** **Business Process Re-engineering (BPR)** — Thay đổi quy trình nội bộ của phòng ban để thích ứng với hệ thống chuẩn (thường ưu tiên cách này hơn là cố gắng sửa đổi code lõi của phần mềm, vì sửa code lõi sẽ gây khó khăn lớn khi nâng cấp hệ thống - Version Upgrade sau này).

---

### Bước 4: Đánh giá chi phí, rủi ro và ra quyết định (Trade-off Analysis)

Sau khi liệt kê toàn bộ các Gaps, đối chiếu từng Gap với tiêu chí **"Chi phí - Lợi ích" (Cost-Benefit)**:

* **Mức độ ảnh hưởng (Impact):** Nếu thiếu tính năng này, quy trình kinh doanh có bị tê liệt không, hay chỉ gây bất tiện nhỏ?
* **Chi phí Custom (Customization Cost):** Chi phí lập trình, kiểm thử và bảo trì lâu dài cho phần mềm tùy biến này là bao nhiêu? (Càng customize nhiều, chi phí bảo trì định kỳ và việc nâng cấp phiên bản phần mềm gốc càng phức tạp và tốn kém).
* **Quy tắc vàng trong Buy & Customize:**
* Cố gắng giữ phần **Core (Lõi)** của nền tảng nguyên bản (Out-of-the-box) tối đa từ **70% - 80%**.
* Chỉ giới hạn phần **Customize (Tùy biến)** trong khoảng **20% - 30%** dành riêng cho các lợi thế cạnh tranh cốt lõi (Core Competencies) của doanh nghiệp. Những yêu cầu nào không quá quan trọng, hãy ép các phòng ban **"Fit-to-Standard"** (điều chỉnh quy trình theo phần mềm).


Việc chuyển đổi từ kết quả GAP-Analysis sang **User Stories** (trong Agile/Scrum) hoặc **Use Cases** (trong quản trị yêu cầu truyền thống/RUP) là bước bắt buộc tiếp theo.

Tùy thuộc vào phần việc trong ma trận GAP, cách viết sẽ tập trung vào các đối tượng khác nhau:

### 1. Với phần "Functional Gaps" (Cần code thêm tính năng mới)

Đây là phần bắt buộc phải viết thành User Stories hoặc Use Cases chi tiết để đội ngũ lập trình (Dev) và kiểm thử (QA) hiểu rõ yêu cầu làm sản phẩm.

* **Dạng User Stories (Agile):** Thường viết theo cấu trúc chuẩn: *As a [Role], I want [Feature], so that [Benefit].*
* *Ví dụ cho Gap tích hợp sinh nhật:*
> **As a** nhân viên Quản lý Khách hàng, **I want** hệ thống tự động sinh và gửi mã giảm giá vào ngày sinh nhật của khách, **So that** tăng tỷ lệ giữ chân khách hàng mà không cần thao tác thủ công.


* Kèm theo các **Acceptance Criteria (Tiêu chí nghiệm thu)** rõ ràng: Mã giảm giá phải tự động tạo trước ngày sinh nhật 3 ngày, giá trị giảm 10%, thời hạn dùng trong 7 ngày, gửi qua Email/SMS tích hợp.


* **Dạng Use Case (Truyền thống):** Mô tả chi tiết dòng sự kiện chính (Main Flow) và các luồng ngoại lệ (Alternative/Exception Flows).
* *Ví dụ:* Use case "Khách hàng áp dụng mã giảm giá sinh nhật tại trang Checkout", mô tả rõ hệ thống kiểm tra ngày sinh trong DB, đối chiếu mã, trừ tiền vào tổng đơn hàng như thế nào khi hợp lệ hoặc báo lỗi khi mã hết hạn.



### 2. Với phần "Integration Gaps" (Cần kết nối API / Middleware)

Thay vì viết giao diện cho người dùng cuối (End-user), User Stories/Use Cases lúc này sẽ tập trung vào **System-to-System (Hệ thống tích hợp)** và các sự kiện luân chuyển dữ liệu (Data Flow).

* *Ví dụ User Stories cho đồng bộ kho:*
> **As a** Hệ thống TMĐT, **I want** tự động gọi API đồng bộ tồn kho sang ERP nội bộ ngay khi có đơn hàng thanh toán thành công, **So that** số liệu tồn kho trên tất cả các kênh (Web, Sàn TMĐT, Cửa hàng vật lý) luôn chuẩn xác theo thời gian thực.


* *Các tiêu chí kỹ thuật đi kèm (Technical Stories):* Định nghĩa rõ định dạng Payload (JSON/XML), phương thức xác thực (OAuth/Token), tần suất gọi API (Real-time webhook hay định kỳ cronjob), và cơ chế retry khi API bên thứ ba bị lỗi.

### 3. Với phần "Process Gaps" (Thay đổi quy trình nghiệp vụ - BPR)

Với nhóm này, bạn **không viết User Stories cho phần mềm** vì phần mềm không cần sửa code. Thay vào đó, bạn chuyển hóa thành:

* **Process Flow / SOP (Standard Operating Procedure):** Tài liệu quy trình vận hành chuẩn mới cho các phòng ban (ví dụ: Hướng dẫn phòng Kế toán hạch toán doanh thu theo cấu trúc sẵn có của hệ thống Buy).
* **Training Manual:** Tài liệu đào tạo nội bộ để ép các "Key Users" thích ứng với chuẩn của nền tảng mới (*Fit-to-Standard*).

---

### Tóm lại

* Các tính năng **có sẵn (Out-of-the-box)** của hệ thống Buy: **Không cần viết** lại User Stories/Use Cases chi tiết từ đầu, chỉ cần tham khảo tài liệu hướng dẫn (User Manual) của nhà cung cấp nền tảng và viết tài liệu cấu hình (Configuration Guide).
* Các khoảng trống **(Gaps)** cần customize, phát triển thêm hoặc tích hợp: **Phải viết** thành User Stories hoặc Use Cases rõ ràng làm cơ sở cho Dev code và QA test.

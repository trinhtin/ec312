## I. QUY TRÌNH PHÂN TÍCH GAP ANALYSIS CHO HƯỚNG BUY/CUSTOMIZE KHI THIẾT KẾ HỆ THỐNG TMĐT 

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


## II. CÁCH VIẾT DOCUMENT (USER STORIES/USE CASES) CHO HƯỚNG BUY/CUSTOMIZE KHI THIẾT KẾ HỆ THỐNG TMĐT 

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

## III. CÁCH VẼ USE CASE DIAGRAM CHO HƯỚNG BUY/CUSTOMIZE
Có, bạn **vẫn nên vẽ Use Case Diagram** trong hướng Buy & Customize, nhưng **mức độ chi tiết và trọng tâm sẽ khác hoàn toàn** so với hướng Build from scratch.

Sự thay đổi về cách tiếp cận Use Case Diagram trong chiến lược Buy & Customize thể hiện rõ qua các điểm trọng tâm sau:

### 1. Phân định rõ "Phần có sẵn" và "Phần customize" trên sơ đồ

Thay vì vẽ một sơ đồ mô tả toàn bộ hệ thống từ A đến Z (vốn đã được phần mềm mua sẵn giải quyết phần lớn), Use Case Diagram trong dự án Buy & Customize cần đánh dấu rõ ranh giới để đội ngũ phát triển và các bên liên quan dễ hình dung:

* **Các Use Case tiêu chuẩn (Out-of-the-box):** Ví dụ như *Đăng ký tài khoản, Thêm vào giỏ hàng, Thanh toán qua cổng VNPay tiêu chuẩn*. Với các Use Case này, bạn không cần vẽ kịch bản chi tiết hay viết tài liệu đặc tả sâu, chỉ cần xem chúng như các **khối chức năng có sẵn (Black-box)**.
* **Các Use Case phát sinh từ GAP (Custom / Extended Use Cases):** Đây là trọng tâm chính của sơ đồ. Ví dụ: *Đồng bộ tồn kho với ERP, Áp dụng mã giảm giá sinh nhật tự động, Quản lý phân quyền đại lý cấp 2*. Những Use Case này cần được vẽ tách bạch hoặc tô điểm chú thích riêng để khoanh vùng khối lượng công việc phải code thêm.

### 2. Sử dụng mối quan hệ giữa các Use Case (Include & Extend) để thể hiện sự tùy biến

Trong mô hình Buy & Customize, các ký hiệu quan hệ trong Use Case Diagram rất hữu ích để chỉ ra cách mà tính năng mới bám vào nền tảng gốc:

* Dùng quan hệ **`<<extend>>`**: Thể hiện việc tính năng custom sẽ móc nối (hook vào) điểm nào của hệ thống gốc mà không làm hỏng luồng chuẩn.
* *Ví dụ:* Luồng thanh toán chuẩn của Shopify (`Checkout`) có thêm một Use Case mở rộng (`<<extend>>`) là `Áp dụng chiết khấu đặc thù theo hợp đồng đại lý riêng của doanh nghiệp`.


* Dùng quan hệ **`<<include>>`**: Thể hiện các module tích hợp trung gian (Middleware/API connector) bắt buộc phải chạy ngầm mỗi khi một hành động nghiệp vụ xảy ra.
* *Ví dụ:* Use Case `Tạo đơn hàng mới` sẽ `<<include>>` luôn Use Case `Đẩy dữ liệu đơn hàng sang hệ thống ERP nội bộ`.



### 3. Use Case Diagram phục vụ cho việc gì trong Buy & Customize?

Vì không phải lập trình lại từ đầu, việc vẽ Use Case Diagram trong trường hợp này chủ yếu phục vụ 3 mục đích cốt lõi:

* **Làm "Bản đồ tích hợp" cho kiến trúc sư phần mềm (Solution Architect):** Giúp nhìn nhanh xem các phần mềm bên ngoài (ERP, WMS, MISA) sẽ chích xuất dữ liệu hoặc tương tác vào đâu của hệ thống E-commerce gốc.
* **Thống nhất phạm vi (Scope) với nhà cung cấp dịch vụ (Vendor/Dev Team):** Tránh việc hiểu lầm giữa hai bên về việc "tính năng này tưởng là có sẵn hóa ra phải code thêm". Sơ đồ giúp khoanh vùng chính xác những Use Case nào nằm trong gói Buy và Use Case nào nằm trong gói Customize.
* **Làm căn cứ để Tester viết Test Case cho phần Custom:** QA sẽ nhìn vào các Use Case tùy biến để tập trung viết kịch bản kiểm thử cho những phần code mới viết thêm, thay vì mất thời gian test lại các tính năng chuẩn của nền tảng (vốn đã được nhà cung cấp gốc đảm bảo ổn định).

### Tóm lại

* Các tính năng **có sẵn (Out-of-the-box)** của hệ thống Buy: **Không cần viết** lại User Stories/Use Cases chi tiết từ đầu, chỉ cần tham khảo tài liệu hướng dẫn (User Manual) của nhà cung cấp nền tảng và viết tài liệu cấu hình (Configuration Guide).
* Các khoảng trống **(Gaps)** cần customize, phát triển thêm hoặc tích hợp: **Phải viết** thành User Stories hoặc Use Cases rõ ràng làm cơ sở cho Dev code và QA test.

## IV. CÁCH BIỂU DIỄN NHỮNG USE CASE ĐÃ CÓ SẴN TRONG HỆ THỐNG DỰ ĐỊNH MUA VS USE CASE CUSTOM
Trong một sơ đồ Use Case Diagram, khi một tính năng được coi là **tiêu chuẩn (Out-of-the-box)** và hoạt động như một **hộp đen (Black-box)**, cách thể hiện rất đơn giản: **Bạn vẫn vẽ nó như một Use Case bình thường, nhưng không đi sâu vào chi tiết bên trong của nó.**

Bạn có thể hình dung qua cách biểu diễn trực quan và bản chất của nó như sau:

### 1. Hình thức thể hiện trên sơ đồ (Diagram)

* Vẫn dùng hình bầu dục (ellipse) để vẽ Use Case đó, kết nối với Actor (người dùng/hệ thống tương tác).
* **Điểm khác biệt:** Bên trong hình bầu dục đó hoặc trong tài liệu kèm theo, bạn **không** vẽ thêm các bước chi tiết phụ, không bóc tách các luồng nhỏ xíu (như bấm nút nào, validate ra sao), vì nền tảng gốc (như Shopify, Magento, Haravan) đã tự lo phần đó rồi.
* *Ví dụ:* Bạn vẫn vẽ Actor **Khách hàng** nối với hình bầu dục **Thanh toán đơn hàng**, nhưng bạn mặc định hiểu đây là cổng thanh toán chuẩn có sẵn của hệ thống, không cần bàn cãi hay thiết kế lại logic.

### 2. Tại sao gọi là "Hộp đen" (Black-box)?

Trong ngành kỹ thuật phần mềm, một tính năng là "hộp đen" nghĩa là:

* **Bạn chỉ quan tâm đến Đầu vào (Input) và Đầu ra (Output):**
* *Input:* Khách bấm nút "Thanh toán".
* *Black-box (Hộp đen):* Hệ thống tự chạy ngầm xử lý (đổi trạng thái đơn, gọi ngân hàng, trừ tiền...). Bạn không cần biết bên trong code của nền tảng nó viết gì.
* *Output:* Trả về màn hình "Đặt hàng thành công".


* Vì nó là "hộp đen" có sẵn, bạn chỉ cần đặt nó lên sơ đồ để **khẳng định phạm vi (Scope)** rằng: *"Hệ thống mua về đã có sẵn tính năng này, chúng ta không phải code lại từ đầu"*.

### 3. Đặt cạnh phần Custom để thấy sự tương phản

Khi nhìn vào một Use Case Diagram của dự án Buy & Customize, sự khác biệt giữa **Black-box (có sẵn)** và **Custom (phải làm thêm)** sẽ hiển thị rất rõ:

* **Use Case tiêu chuẩn (Black-box):**
* `[Khách hàng]` ──> ( Thêm sản phẩm vào giỏ hàng ) *<- Cục này mua sẵn có rồi, vẽ cho đủ bộ khung.*


* **Use Case Custom (Phải mổ xẻ chi tiết):**
* `[Nhân viên kho]` ──> ( Đồng bộ tồn kho real-time qua API với SAP ) *<- Cục này không có sẵn, là GAP cần custom, phải viết tài liệu chi tiết cách nó truyền dữ liệu.*



### Tóm lại

Khi vẽ các Use Case tiêu chuẩn/black-box, bạn chỉ cần **gọi tên tính năng** trên sơ đồ để bức tranh tổng thể hệ thống được liền mạch và rõ ràng. Hãy xem chúng như những khối Lego đã được đúc sẵn trong hộp, việc của bạn chỉ là đặt chúng vào đúng vị trí trên bản thiết kế, thay vì phải ngồi tạc lại từ đầu.

## V. CÁCH DOCUMENT USE CASE CUSTOM
Đối với các **Custom Use Case** (những tính năng khoảng trống - GAP bắt buộc phải lập trình hoặc tích hợp thêm), tài liệu đặc tả (Documentation) cần phải chi tiết, kỹ thuật và rõ ràng để đội ngũ Lập trình (Dev) có thể viết code và đội ngũ Kiểm thử (QA) viết Test Case mà không phải đoán ý.

Một tài liệu đặc tả chuẩn cho một Custom Use Case thường bao gồm các thành phần cốt lõi sau:

---

### 1. Thông tin định danh (Metadata)

Phần đầu tiên giúp quản lý tài liệu và phân định rõ phạm vi công việc:

* **Mã Use Case / Tên Use Case:** (Ví dụ: `UC-CUST-01: Đồng bộ tồn kho real-time qua API với SAP`).
* **Mô tả ngắn gọn:** Tính năng này dùng để làm gì, giải quyết bài toán gì cho nghiệp vụ.
* **Tác nhân chính (Primary Actor):** Ai là người kích hoạt hoặc hệ thống nào khởi tạo (Ví dụ: Nhân viên kho, Hệ thống TMĐT, Webhook bên thứ ba).

### 2. Tiền điều kiện & Hậu điều kiện (Pre-conditions & Post-conditions)

* **Tiền điều kiện:** Hệ thống phải ở trạng thái nào trước khi Use Case này chạy? (Ví dụ: Đã cấu hình thành công API Key kết nối với SAP; Đơn hàng trên web đã chuyển sang trạng thái "Đã thanh toán").
* **Hậu điều kiện:** Hệ thống sẽ thay đổi ra sao sau khi Use Case chạy thành công? (Ví dụ: Tồn kho trên website được trừ đi đúng số lượng đơn hàng; Trạng thái đồng bộ được ghi nhận là "Success" trong bảng log).

### 3. Luồng sự kiện chính (Main Flow / Happy Path)

Mô tả tuần tự các bước diễn ra khi mọi thứ suôn sẻ, không có lỗi phát sinh. Nên viết theo dạng bảng hoặc các bước đánh số rõ ràng:

1. Hệ thống TMĐT ghi nhận sự kiện đơn hàng được thanh toán thành công.
2. Middleware tự động trích xuất dữ liệu đơn hàng (Mã sản phẩm, số lượng, kho xuất).
3. Middleware gọi API `POST /v1/inventory/deduct` sang hệ thống SAP.
4. SAP tiếp nhận, xử lý trừ tồn kho thực tế và trả về mã phản hồi `HTTP 200 OK` kèm dữ liệu tồn kho mới nhất.
5. Hệ thống TMĐT cập nhật lại số lượng tồn kho hiển thị trên giao diện quản trị.

### 4. Luồng ngoại lệ & Xử lý lỗi (Alternative / Exception Flows)

Đây là phần các lập trình viên rất quan tâm để đảm bảo hệ thống không bị crash khi có sự cố thực tế:

* **Luồng 4a (Mất kết nối API với hệ thống ngoài):**
* *Điều kiện:* Khi gọi API sang SAP nhưng server SAP timeout (quá 5 giây) hoặc trả về `HTTP 500`.
* *Hệ thống xử lý:* Hệ thống TMĐT lưu trữ log lỗi vào hàng đợi (Queue), tự động thực hiện cơ chế thử lại (Retry) tối đa 3 lần cách nhau 5 phút. Nếu vẫn thất bại, bắn cảnh báo (Alert) qua Telegram/Email cho bộ phận IT vận hành xử lý thủ công.


* **Luồng 4b (Hết hàng tại kho SAP):**
* *Điều kiện:* Kho thực tế không đủ hàng để trừ dù khách đã đặt tiền trên web.
* *Hệ thống xử lý:* Hủy tự động giao dịch hoặc chuyển đơn hàng sang trạng thái "Chờ xử lý đặc biệt" để nhân viên CSKH gọi điện cho khách.



### 5. Yêu cầu dữ liệu & Giao diện (Data & UI Requirements)

* **Quy tắc nghiệp vụ (Business Rules):** Các điều kiện logic chặt chẽ (Ví dụ: Tồn kho không bao giờ được phép âm; Nếu đồng bộ thất bại quá 3 lần phải khóa tính năng đặt hàng của sản phẩm đó tạm thời).
* **Đặc tả API / Payload (nếu là tính năng tích hợp):** Cung cấp cấu trúc dữ liệu JSON mẫu gửi đi và nhận về giữa các hệ thống.
* **Giao diện quản trị (Admin UI Spec):** Nếu tính năng custom có thêm màn hình quản lý mới trên trang Admin, cần kèm theo Wireframe hoặc mô tả rõ các trường dữ liệu (input text, dropdown, nút bấm) và quyền hạn (RBAC) ai được phép bấm nút nào.

### 6. Tiêu chí nghiệm thu (Acceptance Criteria)

Liệt kê các điều kiện cụ thể để QA hoặc Product Owner kiểm tra xem tính năng code xong đã đạt yêu cầu chưa (thường viết theo dạng BDD - Given/When/Then):

* *Given* đơn hàng trị giá 2 sản phẩm A đã thanh toán thành công trên web,
* *When* hệ thống gọi API đồng bộ sang SAP thành công,
* *Then* số lượng tồn kho của sản phẩm A trên website phải tự động trừ đi 2, và lịch sử giao dịch ghi nhận log "Synced".

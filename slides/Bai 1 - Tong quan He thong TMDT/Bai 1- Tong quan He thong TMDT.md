# BUỔI 1: Tổng quan Hệ thống TMĐT & Bài toán "Build or Buy"

**Môn học:** Phân tích & Thiết kế Hệ thống Thương mại Điện tử  
**Phương pháp luận:** Project-Based Learning (PBL) & Kiến trúc Hệ thống Doanh nghiệp  
**Số lượng slide:** 50 Slide tiêu chuẩn học thuật  

---

## PHẦN I: KHỞI ĐẦU & BỐI CẢNH HỆ THỐNG TMĐT (Slide 01 – 10)

### Slide 01: Tiêu đề Buổi học
* **Tiêu đề chính:** Tổng quan Hệ thống TMĐT & Bài toán "Build or Buy"
* **Tiêu đề phụ:** Nền tảng lý luận, cấu trúc kiến trúc phân tầng và chiến lược lựa chọn hướng triển khai công nghệ.
* **Mục tiêu:** Thiết lập khung tư duy hệ thống (Systems Thinking) cho chuyên viên phân tích dữ liệu và kiến trúc sư phần mềm.

### Slide 02: Dẫn luận Học thuật
> *"Kiến trúc của một hệ thống là tập hợp các quyết định cấu trúc quan trọng nhất định hình hình thái vận hành, khả năng mở rộng và chi phí vòng đời của phần mềm đó."*
> 
> — **Martin Fowler**, *Patterns of Enterprise Application Architecture*

* **Ý nghĩa:** Định hình góc nhìn chuyên sâu về hệ thống TMĐT không chỉ là trang web giao dịch, mà là một thực thể kiến trúc phức tạp chịu áp lực lớn về tải trọng giao dịch và tính toàn vẹn dữ liệu.

### Slide 03: Mục tiêu Tổng quát của Buổi học
* **01. Thấu hiểu Kiến trúc:** Phân tích cấu trúc phân tầng (Layered Architecture) trong hệ sinh thái TMĐT hiện đại.
* **02. Giải phẫu Hệ thống Thông tin:** Nhận diện 5 thành phần cốt lõi cấu thành hạ tầng vận hành trực tuyến.
* **03. Phân tích Chiến lược:** Đánh giá tường tận bản chất kinh tế và kỹ thuật của bài toán **Build vs. Buy**.
* **04. Định hướng Dự án:** Thiết lập nền tảng khởi tạo cho phương pháp học tập dựa trên đồ án (PBL).

### Slide 04: Bản chất Kinh tế & Kỹ thuật của TMĐT
* **Định nghĩa Học thuật:** Thương mại điện tử (E-Commerce) là sự tích hợp của các quy trình nghiệp vụ kinh doanh, công nghệ truyền thông số và hạ tầng dữ liệu nhằm thực thi các giao dịch trao đổi giá trị qua mạng lưới toàn cầu.
* **Đặc thù Vận hành:**
  * **24/7/365 Availability:** Yêu cầu mức độ sẵn sàng liên tục không khoảng trống.
  * **Transactional Integrity:** Đảm bảo tính nhất quán tuyệt đối trong dòng tài chính, trạng thái tồn kho và chứng từ đơn hàng.
  * **Elastic Load:** Năng lực co giãn hạ tầng đột ngột theo các biến động tải trọng từ thị trường.

### Slide 05: Mô hình Hệ thống Thông tin 5 Thành phần
* **Hệ thống TMĐT là một thực thể hợp nhất bao gồm:**
  1. **Hardware (Phần cứng):** Máy chủ biên, trung tâm dữ liệu, thiết bị phân phối nội dung (CDN).
  2. **Software (Phần mềm):** Hệ điều hành, tầng trung gian (Middleware), mã nguồn ứng dụng lõi và các giao diện lập trình ứng dụng (API).
  3. **Data (Dữ liệu):** Cơ sở dữ liệu quan hệ, phi quan hệ, kho dữ liệu khách hàng và nhật ký hệ thống (Logs).
  4. **People (Con người):** Người tiêu dùng cuối, đội ngũ quản trị, kỹ sư vận hành và chuyên viên phân tích hệ thống (BA).
  5. **Process (Quy trình):** Luồng nghiệp vụ từ tiếp nhận khách hàng, thanh toán, quản lý kho đến hậu mãi (Logistics).

### Slide 06: Sơ đồ Tổng quan Kiến trúc Phân tầng (Layered Architecture)
* **Cấu trúc phân lớp tiêu chuẩn trong kỹ nghệ phần mềm:**
  * **Tầng Giao diện (Presentation Layer):** Web Frontend, Mobile App, Progressive Web App.
  * **Tầng Dịch vụ / Nghiệp vụ (Application / Business Layer):** Xử lý giỏ hàng, định giá, khuyến mãi, quản lý đơn hàng (OMS).
  * **Tầng Dữ liệu (Data Access Layer):** ORM, truy vấn cơ sở dữ liệu, bộ nhớ đệm (Caching).
  * **Tầng Hạ tầng (Infrastructure Layer):** Cloud Server, Containerization, Database Clusters.

### Slide 06a: Hai Phương pháp Luận Phân tích Cốt lõi trong Kỹ nghệ Phần mềm
* **Định hướng Phương pháp:** Quá trình phân tích và thiết kế hệ thống trong công nghệ phần mềm được tiếp cận qua hai trường phái tư duy bổ trợ lẫn nhau:
  1. **Phân tích theo hướng cấu trúc (Structured Analysis)**
  2. **Phân tích theo hướng đối tượng (Object-Oriented Analysis - OOA)**

### Slide 06b: Phân tích theo hướng cấu trúc (Structured Analysis)
* **Bản chất Phương pháp:** 
  * Là phương pháp tiếp cận truyền thống dựa trên chức năng (*function-oriented*) hoặc hướng thủ tục theo mô hình từ trên xuống (*top-down*).
  * Chia nhỏ hệ thống phức tạp thành các chức năng hoặc quy trình xử lý dữ liệu độc lập.
* **Công cụ Mô hình hóa Tiêu biểu:** 
  * Sơ đồ luồng dữ liệu (*Data Flow Diagram - DFD*).
  * Biểu đồ thực thể quan hệ (*ERD* cấu trúc cổ điển).
* **Ứng dụng Thực tiễn:** Thường được áp dụng hiệu quả trong việc phân tích các hệ thống có tính tuần tự logic cao, tập trung vào biến đổi dữ liệu từ đầu vào đến đầu ra.

### Slide 06c: Phân tích theo hướng đối tượng (Object-Oriented Analysis - OOA)
* **Bản chất Phương pháp:** 
  * Là phương pháp tiếp cận hiện đại dựa trên thực thể đối tượng (*object-oriented*), mô phỏng thế giới thực vào trong cấu trúc phần mềm.
  * Mô hình hóa hệ thống bằng cách tập trung vào các đối tượng, gói gọn cả trạng thái (thuộc tính) và hành vi (phương thức xử lý) của chúng.
* **Công cụ Mô hình hóa Tiêu biểu:** 
  * Ngôn ngữ mô hình hóa thống nhất (*UML* - Unified Modeling Language), bao gồm *Class Diagram*, *Use Case Diagram*, *Sequence Diagram*.
* **Ứng dụng Thực tiễn:** Là tiêu chuẩn công nghiệp hiện hành trong phát triển các hệ thống TMĐT quy mô lớn, giúp tăng cường tính đóng gói, khả năng tái sử dụng mã nguồn và bảo trì dài hạn.

### Slide 06d: Sự Chuyển dịch Phương pháp luận trong Giáo trình
* **Mối liên hệ với Cấu trúc Buổi học:**
  * **Buổi 2 & 4:** Sử dụng tư duy phân tích chức năng và luồng quy trình (gần với hướng cấu trúc) để xây dựng Use Case và Activity Diagram.
  * **Buổi 3 & 5:** Triển khai chuyên sâu **Phân tích và Thiết kế Hướng đối tượng (OOA/OOD)** thông qua việc xây dựng *Class Diagram* và *Sequence Diagram*.

### Slide 07: Tầng Giao diện (Presentation Layer) & Trải nghiệm Người dùng
* **Vai trò:** Cổng giao tiếp trực quan giữa tác nhân (Actor) và hệ thống backend.
* **Yêu cầu Kỹ thuật:**
  * Tối ưu hóa thời gian hiển thị trang đầu tiên (First Contentful Paint).
  * Tính tương thích đa nền tảng (Responsive Design & Cross-browser).
  * Kiến trúc tách rời (Headless Commerce API-driven).

### Slide 08: Tầng Dịch vụ & Nghiệp vụ Cốt lõi (Business Logic Layer)
* **Trái tim của hệ thống TMĐT:** Nơi hiện thực hóa các quy tắc thương mại (Business Rules).
* **Các Phân hệ Chính:**
  * **Catalog Management:** Quản lý danh mục, thuộc tính động, phân loại sản phẩm.
  * **Pricing & Promotion Engine:** Tính toán chiết khấu đa tầng, mã giảm giá, thuế suất.
  * **Cart & Checkout Engine:** Quản lý phiên giao dịch, khóa tồn kho tạm thời (Inventory Reservation).

### Slide 09: Tầng Dữ liệu & Lưu trữ (Data Layer)
* **Đặc thù Dữ liệu TMĐT:** Khối lượng giao dịch lớn (High Throughput), tính toàn vẹn cao (ACID Compliance cho thanh toán) kết hợp tính linh hoạt (Schemaless cho thông số sản phẩm).
* **Công nghệ Tiêu biểu:**
  * CSDL Quan hệ (PostgreSQL, MySQL) cho tài chính và đơn hàng.
  * CSDL Phi quan hệ / Key-Value (Redis) cho giỏ hàng và bộ nhớ đệm.
  * Search Engine (Elasticsearch) cho hệ thống tìm kiếm toàn văn bản.

### Slide 10: Tóm tắt Phần I - Hệ thống dưới lăng kính Kỹ thuật
* Hệ thống TMĐT không đơn thuần là giao diện trực tuyến mà là một kiến trúc phân tán đa tầng phức tạp.
* Sự phối hợp nhịp nhàng giữa 5 thành phần cốt lõi quyết định năng lực cạnh tranh số của doanh nghiệp.
* *Chuyển ý:* Trước khi xây dựng hay tích hợp hệ thống, doanh nghiệp phải đối mặt với bài toán chiến lược nền tảng: **Build or Buy**.

---

## PHẦN II: GIẢI PHẪU BÀI TOÁN CHIẾN LƯỢC "BUILD OR BUY" (Slide 11 – 25)

### Slide 11: Định nghĩa Bài toán "Build or Buy"
* **Bản chất Chiến lược:** Quyết định phân bổ nguồn vốn đầu tư công nghệ giữa việc tự phát triển hoàn toàn mã nguồn (Custom Development / Build) hay sử dụng các giải pháp nền tảng có sẵn (SaaS / Open-source / COTS - Commercial Off-The-Shelf / Buy).
* **Tác động:** Quyết định này chi phối toàn bộ cấu trúc chi phí (CapEx vs. OpEx), lộ trình ra mắt thị trường (Time-to-market) và năng lực tùy biến dài hạn của doanh nghiệp.

### Slide 12: Hướng 1 - Triển khai Dựa trên Nền tảng Sẵn có (Buy / Customize)
* **Đặc điểm Mô hình:** Sử dụng các nền tảng thương mại điện tử dạng dịch vụ (SaaS như Shopify Plus, BigCommerce) hoặc mã nguồn mở thương mại (Magento / Adobe Commerce, WooCommerce).
* **Triết lý Vận hành:** *"Configuration over Code"* — Cấu hình thay vì lập trình từ đầu.
* **Phù hợp với:** Doanh nghiệp quy mô vừa và nhỏ, doanh nghiệp khởi nghiệp, hoặc các tổ chức cần thử nghiệm thị trường nhanh chóng với nguồn lực tài chính ban đầu hữu hạn.

### Slide 13: Ưu điểm Chiến lược của Hướng "Buy"
* **Tốc độ Thâm nhập Thị trường (Time-to-Market):** Rút ngắn thời gian triển khai từ nhiều năm xuống còn vài tuần hoặc vài tháng.
* **Tối ưu Chi phí Vốn Ban đầu (CapEx):** Giảm thiểu chi phí nghiên cứu phát triển ban đầu, chuyển hóa thành chi phí vận hành định kỳ (OpEx).
* **Tính Ổn định và Bảo mật Tiêu chuẩn:** Các nền tảng SaaS lớn đã được kiểm chứng qua hàng triệu giao dịch, tích hợp sẵn các chứng chỉ bảo mật quốc tế (PCI-DSS).

### Slide 14: Nhược điểm & Rủi ro của Hướng "Buy"
* **Phụ thuộc Nhà cung cấp (Vendor Lock-in):** Doanh nghiệp bị ràng buộc bởi chính sách giá, lộ trình công nghệ và điều khoản dịch vụ của bên cung cấp nền tảng.
* **Giới hạn Tùy biến (Customization Boundaries):** Khi doanh nghiệp mở rộng quy mô (Scale-up) với các quy trình nghiệp vụ đặc thù, các nền tảng có sẵn thường bộc lộ sự cứng nhắc, khó mở rộng sâu.
* **Chi phí Dài hạn (TCO Escalation):** Phí bản quyền, phí giao dịch và chi phí mua các plugin bổ trợ có thể tăng cao theo doanh thu.

### Slide 15: Hướng 2 - Phát triển Mới Hoàn toàn từ Đầu (Build from Scratch / Custom Development)
* **Đặc điểm Mô hình:** Xây dựng hệ thống phần mềm độc quyền từ mảnh đất trống dựa trên kiến trúc Microservices hoặc Phân tầng độc lập.
* **Triết lý Vận hành:** *"Total Ownership & Control"* — Sở hữu toàn diện và kiểm soát tuyệt đối mã nguồn.
* **Phù hợp với:** Các tập đoàn lớn, doanh nghiệp có mô hình kinh doanh độc bản, yêu cầu bảo mật dữ liệu tuyệt đối (Ngân hàng, Tài chính, Bán lẻ quy mô lớn).

### Slide 16: Ưu điểm Chiến lược của Hướng "Build"
* **Sở hữu Tài sản Trí tuệ (IP - Intellectual Property):** Mã nguồn và thuật toán cốt lõi thuộc sở hữu độc quyền của doanh nghiệp, tạo lợi thế cạnh tranh dài hạn.
* **Tự do Tùy biến Tuyệt đối:** Không bị giới hạn bởi bất kỳ khung tính năng có sẵn nào; dễ dàng hiện thực hóa mọi logic nghiệp vụ phức tạp nhất.
* **Khả năng Mở rộng Quy mô Độc lập (Independent Scalability):** Tối ưu hóa từng thành phần riêng lẻ (ví dụ: tối ưu riêng phân hệ thanh toán hoặc kho hàng) khi lượng truy cập bùng nổ.

### Slide 17: Nhược điểm & Rủi ro của Hướng "Build"
* **Chi phí và Thời gian Triển khai Khổng lồ:** Đòi hỏi đội ngũ nhân sự kỹ thuật cao, thời gian kéo dài từ 6 tháng đến nhiều năm.
* **Rủi ro Kỹ thuật (Technical Debt):** Nợ kỹ thuật tích lũy trong quá trình phát triển nhanh có thể làm sụp đổ hệ thống nếu kiến trúc sư không kiểm soát chặt chẽ.
* **Gánh nặng Vận hành & Bảo trì (Maintenance Overhead):** Doanh nghiệp phải tự chủ hoàn toàn việc vá lỗi bảo mật, nâng cấp hạ tầng và quản lý đội ngũ vận hành 24/7.

### Slide 18: Bảng So sánh Tổng quan: Build vs. Buy

| **Tiêu chí Đánh giá** | **Hướng 1: Buy / Customize (Nền tảng sẵn có)** | **Hướng 2: Build from scratch (Tự phát triển)** |
| :--- | :--- | :--- |
| **Mục tiêu Chiến lược** | Tốc độ thâm nhập thị trường nhanh, tối ưu CapEx ban đầu. | Sở hữu IP, tối ưu hóa tuyệt đối theo logic kinh doanh riêng. |
| **Kiến trúc Kỹ thuật** | Monolith hoặc SaaS tích hợp; mở rộng qua Plugin/Market. | Microservices / Phân tầng độc lập; kiểm soát toàn bộ mã nguồn. |
| **Thời gian Triển khai** | Ngắn (Vài tuần đến vài tháng). | Dài (6 tháng đến nhiều năm). |
| **Rủi ro Chủ đạo** | Vendor lock-in, giới hạn tính năng khi scale-up. | Chi phí R&D khổng lồ, rủi ro kỹ thuật, tiến độ chậm trễ. |
| **Vai trò Phân tích (BA)** | Tập trung thực hiện **Gap Analysis** (đối chiếu tính năng). | Tập trung **Deep Elicitation** & đặc tả logic từ con số 0. |

### Slide 19: Tiêu chí Ra quyết định - Khung Phân tích Đa chiều
* **01. Năng lực Tài chính & Ngân sách:** Đánh giá dòng tiền ngắn hạn (CapEx) so với chi phí vận hành dài hạn (OpEx).
* **02. Tính Độc bản của Nghiệp vụ (Business Uniqueness):** Nếu mô hình kinh doanh mang tính đột phá, không nền tảng nào đáp ứng -> Bắt buộc **Build**. Nếu là bán lẻ tiêu chuẩn -> Ưu tiên **Buy**.
* **03. Yêu cầu Bảo mật & Pháp lý (Compliance):** Các ngành nghề chịu sự quản lý ngặt nghèo về dữ liệu cá nhân và tài chính đòi hỏi quyền kiểm soát hạ tầng tuyệt đối.
* **04. Nguồn lực Nhân sự Công nghệ:** Doanh nghiệp có sẵn đội ngũ kỹ thuật đủ năng lực quản trị vòng đời phần mềm hay không?

### Slide 20: Phân tích Tổng chi phí Sở hữu (TCO - Total Cost of Ownership)
* **Công thức Đánh giá TCO trong TMĐT:**
  $$\text{TCO} = \text{Chi phí ban đầu (Setup)} + \sum \left( \text{Chi phí vận hành định kỳ} + \text{Chi phí bảo trì/nâng cấp} + \text{Chi phí cơ hội do giới hạn hệ thống} \right)$$
* **Góc nhìn Tài chính:** Giải pháp "Buy" thường có chi phí ban đầu thấp nhưng chi phí ẩn (phí giao dịch, nâng cấp gói dịch vụ) tăng theo doanh thu. Giải pháp "Build" có chi phí ban đầu rất cao nhưng tối ưu biên độ lợi nhuận khi doanh nghiệp đạt quy mô lớn.

### Slide 21: Mô hình Lai (Hybrid Approach / Composable Commerce)
* **Xu hướng Đương đại:** Sự kết hợp giữa hai phương thức thông qua **Composable Commerce** (Thương mại cấu thành).
* **Nguyên lý:** Sử dụng các dịch vụ bên thứ ba chuyên biệt dạng API (MACH architecture: Microservices, API-first, Cloud-native, Headless) để lắp ghép hệ thống thay vì chọn cực đoan hoàn toàn Build hay Buy.
* **Lợi ích:** Cho phép tùy biến sâu các phân hệ chiến lược trong khi vẫn tận dụng các dịch vụ chuẩn hóa có sẵn.

### Slide 22: Vai trò của Chuyên viên Phân tích (BA) dưới 2 Hướng Tiếp cận
* **Trong hướng "Buy":** BA đóng vai trò là nhà tư vấn quy trình, thực hiện *Gap Analysis* để tìm điểm khác biệt giữa yêu cầu doanh nghiệp và tính năng có sẵn của SaaS.
* **Trong hướng "Build":** BA đóng vai trò là kỹ sư tri thức, thực hiện phỏng vấn sâu, xây dựng tài liệu đặc tả yêu cầu hệ thống chi tiết và mô hình hóa dữ liệu từ con số 0.

### Slide 23: Nghiên cứu Tình huống Thực tiễn (Case Study)
* **Trường hợp 1 (Buy):** Doanh nghiệp bán lẻ triển khai thành công nền tảng SaaS, giúp đưa sản phẩm lên môi trường trực tuyến trong thời gian ngắn với nguồn lực hạn chế.
* **Trường hợp 2 (Build):** Tập đoàn thương mại điện tử quy mô lớn với hàng triệu danh mục sản phẩm và thuật toán xử lý độc quyền đầu tư xây dựng hệ thống Microservices riêng biệt để đảm bảo hiệu năng và tính bảo mật dữ liệu.

### Slide 24: Dự báo Xu hướng Công nghệ TMĐT
* Sự dịch chuyển từ các cấu trúc nguyên khối (Monolithic Suites) sang kiến trúc mô-đun linh hoạt (Modular Monolith & Microservices).
* Trí tuệ nhân tạo tích hợp sâu vào các công cụ cấu hình tự động, thu hẹp khoảng cách kỹ thuật giữa hai hướng tiếp cận Build và Buy.

### Slide 25: Tóm tắt Phần II - Nghệ thuật Ra quyết định Kiến trúc
* Không có lựa chọn tuyệt đối tối ưu, chỉ có lựa chọn phù hợp nhất với chiến lược kinh doanh và nguồn lực tại từng giai đoạn phát triển của doanh nghiệp.
* Sự thấu hiểu sâu sắc về kiến trúc và TCO là nền tảng cốt lõi của một Kiến trúc sư hệ thống hoặc Chuyên viên phân tích chuyên nghiệp.

---

## PHẦN III: PHƯƠNG PHÁP LUẬN ĐỒ ÁN & THỰC HÀNH PBL (Slide 26 – 40)

### Slide 26: Giới thiệu Phương pháp Học tập Dựa trên Dự án (PBL)
* **Định nghĩa:** Project-Based Learning là phương pháp giáo dục thực tiễn, nơi học viên áp dụng trực tiếp các khái niệm lý luận vào việc thiết kế một hệ thống TMĐT hoàn chỉnh xuyên suốt 8 buổi học.
* **Mục tiêu:** Chuyển hóa tri thức hàn lâm thành năng lực thực chiến, sẵn sàng giải quyết các bài toán kỹ thuật tại doanh nghiệp.

### Slide 27: Cấu trúc Xuyên suốt 8 Buổi của Đồ án
* **Buổi 1:** Tổng quan hệ thống & Lựa chọn chiến lược Build/Buy.
* **Buổi 2:** Khảo sát yêu cầu & Xác định phạm vi (Use Case).
* **Buổi 3:** Thiết kế dữ liệu cốt lõi (ERD & Class Diagram).
* **Buổi 4:** Thiết kế quy trình nghiệp vụ (Activity Diagram / BPMN).
* **Buổi 5:** Tương tác hệ thống & Đặc tả logic (Sequence Diagram).
* **Buổi 6:** Kiến trúc hệ thống & Tích hợp API.
* **Buổi 7:** Thiết kế giao diện & Quản lý Agile.
* **Buổi 8:** Kiểm thử, Triển khai & Bảo vệ Đồ án.

### Slide 28: Yêu cầu Hình thành Nhóm Dự án PBL
* **Quy mô nhóm:** Từ 3 đến 5 thành viên.
* **Phân vai trò chuyên môn:**
  * **Project Manager (PM):** Quản lý tiến độ, phân bổ nhiệm vụ.
  * **Business Analyst (BA):** Khảo sát yêu cầu, lập tài liệu đặc tả hệ thống.
  * **System Architect / Data Modeler:** Thiết kế cơ sở dữ liệu và luồng kiến trúc.
  * **UI/UX & QA Specialist:** Thiết kế giao diện và kiểm thử chất lượng.

### Slide 29: Tiêu chí Lựa chọn Ý tưởng Dự án TMĐT
* **Tính Khả thi:** Đề tài phải có ranh giới rõ ràng, tập trung vào một phân khúc thị trường cụ thể.
* **Tính Phức tạp Kỹ thuật:** Đảm bảo hệ thống tích hợp tối thiểu các phân hệ: Quản lý sản phẩm, Giỏ hàng, Thanh toán, Quản lý đơn hàng và Vận chuyển.

### Slide 30: Bài tập Thực hành PBL (Phần 1) - Xác định Ý tưởng
* **Nhiệm vụ của Nhóm:**
  1. Xác định tên dự án và mô hình kinh doanh cốt lõi (B2B, B2C, C2C).
  2. Xác định chân dung người dùng mục tiêu (Target Persona).
  3. Liệt kê tối thiểu 5 tính năng cốt lõi bắt buộc phải có trong phiên bản sản phẩm khả thi tối thiểu (MVP).

### Slide 31: Bài tập Thực hành PBL (Phần 2) - Bài toán Build or Buy của Nhóm
* **Nhiệm vụ của Nhóm:**
  1. Thảo luận và đưa ra quyết định chiến lược: Nhóm sẽ chọn **Hướng 1 (Buy/SaaS)** hay **Hướng 2 (Build from scratch)** cho dự án của mình?
  2. Lập bảng phân tích lý do dựa trên ngân sách giả định, thời gian thực hiện và mức độ tùy biến nghiệp vụ.

### Slide 32: Lập bảng Phân tích TCO Giả định cho Đồ án
* **Yêu cầu phân tích tài chính sơ bộ:**
  * Ước tính chi phí ban đầu (License/Setup vs. R&D Development).
  * Ước tính chi phí vận hành hàng tháng (Cloud hosting, Transaction fees, Maintenance).
  * Đánh giá điểm hòa vốn dự kiến dựa trên mô hình doanh thu.

### Slide 33: Xây dựng Project Charter (Điều lệ Dự án) cơ bản
* **Nội dung cốt lõi của Project Charter:**
  * Tên dự án và mục tiêu chiến lược.
  * Phạm vi dự án (In-scope vs. Out-of-scope).
  * Mốc thời gian hoàn thành các chặng (Milestones).
  * Danh sách các bên liên quan (Stakeholders).

### Slide 34: Quy chuẩn Trình bày Hồ sơ Thiết kế Hệ thống
* Toàn bộ các sản phẩm đầu ra từ các buổi học phải được chuẩn hóa dưới dạng văn bản kỹ thuật học thuật.
* Sử dụng ngôn từ chuyên ngành, rõ ràng, đảm bảo tính khách quan khoa học.
* Trình bày các sơ đồ trực quan tuân thủ chuẩn mực quốc tế (UML, BPMN).

### Slide 35: Tiêu chí Đánh giá Đồ án Cuối kỳ
* **Tính Hoàn chỉnh (Completeness):** Hồ sơ thiết kế phủ kín toàn bộ vòng đời phân tích hệ thống từ Buổi 1 đến Buổi 8.
* **Tính Logic & Nhất quán (Consistency):** Các sơ đồ phải khớp nối chặt chẽ với nhau, không mâu thuẫn về mặt logic nghiệp vụ.
* **Tính Thực tiễn (Practicality):** Giải pháp thiết kế có khả năng triển khai thực tế trên thị trường thương mại điện tử.

### Slide 36: Hướng dẫn Khai thác Tài liệu Tham khảo
* *Software Requirements Engineering* – Karl Wiegers.
* *Patterns of Enterprise Application Architecture* – Martin Fowler.
* *E-Commerce: Business, Technology, Society* – Kenneth C. Laudon.
* Các tài liệu chuyên khảo về Kiến trúc Microservices và Nền tảng SaaS hiện đại.

### Slide 37: Tổng kết Quy trình Làm việc Nhóm Hiệu quả
* Thiết lập kênh giao tiếp chuyên nghiệp giữa các thành viên.
* Duy trì chế độ họp định kỳ để kiểm soát tiến độ công việc của từng cá nhân trong nhóm.
* Đảm bảo tính minh bạch và sự đồng thuận trong quá trình triển khai đồ án.

### Slide 38: Câu hỏi Thảo luận Học thuật (Seminar Discussion)
* **Câu hỏi 1:** Tại sao nhiều doanh nghiệp lớn ban đầu chọn giải pháp "Buy" nhưng sau đó lại chuyển đổi hoàn toàn sang kiến trúc "Build"?
* **Câu hỏi 2:** Làm thế nào để cân bằng giữa tốc độ thâm nhập thị trường (Time-to-market) và khả năng mở rộng kiến trúc dài hạn?

### Slide 39: Giải đáp Thắc mắc & Định hướng Buổi tiếp theo
* Giảng viên giải đáp các thắc mắc liên quan đến việc hình thành ý tưởng dự án và lựa chọn hướng Build/Buy cho từng nhóm.
* Nhắc nhở các nhóm hoàn thành **Project Charter** và nộp báo cáo lựa chọn chiến lược vào đầu buổi học tiếp theo.

### Slide 40: Giới thiệu Nội dung Buổi 2
* **Tiêu đề Buổi 2:** Khảo sát, Phân tích Yêu cầu & Xác định Phạm vi (Requirements Engineering).
* **Trọng tâm:** Phân loại yêu cầu Functional / Non-functional, kỹ thuật Gap Analysis (cho hướng Buy) vs. Deep Elicitation (cho hướng Build), và hướng dẫn vẽ sơ đồ Use Case Diagram.

---

## PHẦN IV: PHỤ LỤC, TRÍCH DẪN & TÀI LIỆU THAM KHẢO (Slide 41 – 50)

### Slide 41: Danh mục Trích dẫn Học thuật (1/3)
* [1] **Fowler, M. (2002).** *Patterns of Enterprise Application Architecture*. Addison-Wesley. (Định hình nền tảng kiến trúc phân tầng hệ thống doanh nghiệp).
* [2] **Laudon, K. C., & Traver, C. G. (2021).** *E-Commerce 2021: Business, Technology, Society*. Pearson. (Khung phân tích tổng quan thị trường và mô hình hạ tầng TMĐT).

### Slide 42: Danh mục Trích dẫn Học thuật (2/3)
* [3] **Wiegers, K., & Beatty, J. (2013).** *Software Requirements (3rd Edition)*. Microsoft Press. (Phương pháp luận kỹ nghệ yêu cầu, phân loại yêu cầu chức năng và phi chức năng).
* [4] **Bass, L., Clements, P., & Kazman, R. (2012).** *Software Architecture in Practice (3rd Edition)*. Addison-Wesley. (Các thuộc tính chất lượng phần mềm và tiêu chí đánh giá kiến trúc).

### Slide 43: Danh mục Trích dẫn Học thuật (3/3)
* [5] **Newman, S. (2015).** *Building Microservices: Designing Fine-Grained Systems*. O'Reilly Media. (Phân tích chiến lược phân rã hệ thống và bài toán tự phát triển).

### Slide 44: Thuật ngữ Chuyên ngành (Glossary - A to C)
* **API (Application Programming Interface):** Giao diện lập trình ứng dụng, cho phép các phân hệ phần mềm giao tiếp với nhau.
* **CapEx (Capital Expenditure):** Chi phí đầu tư vốn ban đầu cho hạ tầng và phát triển tài sản cố định.
* **COTS (Commercial Off-The-Shelf):** Phần mềm thương mại có sẵn trên thị trường.

### Slide 45: Thuật ngữ Chuyên ngành (Glossary - D to M)
* **Gap Analysis:** Phương pháp phân tích khoảng cách giữa năng lực hiện tại/tính năng sẵn có với yêu cầu thực tế.
* **Headless Commerce:** Kiến trúc TMĐT tách rời hoàn toàn tầng giao diện với tầng xử lý nghiệp vụ.
* **Microservices:** Phong cách kiến trúc phần mềm cấu trúc ứng dụng thành một tập hợp các dịch vụ nhỏ độc lập.

### Slide 46: Thuật ngữ Chuyên ngành (Glossary - O to S)
* **OpEx (Operational Expenditure):** Chi phí vận hành định kỳ phát sinh trong quá trình hoạt động hệ thống.
* **PBL (Project-Based Learning):** Phương pháp học tập dựa trên dự án thực tiễn.
* **SaaS (Software as a Service):** Mô hình phân phối phần mềm dạng dịch vụ qua nền tảng điện toán đám mây.
* **SRS (Software Requirements Specification):** Tài liệu đặc tả yêu cầu phần mềm chi tiết.

### Slide 47: Thuật ngữ Chuyên ngành (Glossary - T to Z)
* **TCO (Total Cost of Ownership):** Tổng chi phí sở hữu, bao gồm toàn bộ chi phí đầu tư, vận hành và bảo trì trong vòng đời hệ thống.
* **UML (Unified Modeling Language):** Ngôn ngữ mô hình hóa thống nhất dùng trong thiết kế phần mềm.

### Slide 48: Nguyên tắc Trình bày Báo cáo Đồ án
* Báo cáo phải được biên soạn bằng văn bản kỹ thuật chuẩn mực, tuân thủ các quy tắc định dạng học thuật.
* Các biểu đồ và sơ đồ kỹ thuật phải có chú thích rõ ràng, minh bạch về ký hiệu.
* Tuyệt đối duy trì sự khách quan khoa học, chuẩn xác trong ngôn từ chuyên môn.

### Slide 49: Kế hoạch Hành động cho Nhóm (Action Items)
* [ ] Hoàn thành việc phân vai trò thành viên trong nhóm dự án.
* [ ] Thống nhất ý tưởng đề tài TMĐT và nộp phiếu đăng ký sơ bộ.
* [ ] Hoàn thành bảng phân tích quyết định **Build or Buy** kèm dự toán TCO giả định cho đề tài.

### Slide 50: Lời kết Buổi học
> *"Kỹ thuật phần mềm chuẩn mực không nằm ở sự phức tạp của mã nguồn, mà nằm ở tính minh bạch trong tư duy thiết kế và sự chính xác trong việc giải quyết bài toán cốt lõi của doanh nghiệp."*
> 
> — **Hội đồng Khoa học Hệ thống Thông tin**

* **Kết thúc Buổi 1.** Xin cảm ơn sự chú ý lắng nghe của toàn thể học viên. Chúc các nhóm hoàn thành xuất sắc đồ án môn học!
```eof

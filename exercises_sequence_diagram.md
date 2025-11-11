# 5 Bài Tập Vẽ Sequence Diagram Cho Hệ Thống TMĐT
# 5 Sequence Diagram Exercises For E-Commerce System

## Bài Tập 1: Quy Trình Đăng Ký Tài Khoản / Exercise 1: User Registration Process

**Mô tả / Description:**
Thiết kế sequence diagram cho quy trình đăng ký tài khoản khách hàng mới.
Design a sequence diagram for the customer account registration process.

**Yêu cầu / Requirements:**

**Các Actor/Object:**
- **Customer (Khách hàng)**: Người dùng muốn đăng ký
- **UI (Giao diện)**: Trang đăng ký
- **RegistrationController**: Xử lý logic đăng ký
- **ValidationService**: Kiểm tra tính hợp lệ dữ liệu
- **UserRepository**: Truy xuất database người dùng
- **EmailService**: Gửi email xác thực
- **Database**: Cơ sở dữ liệu

**Luồng chính / Main Flow:**

1. **Nhập thông tin / Enter Information:**
   - Customer điền form đăng ký (username, email, password, phone)
   - Customer nhấn nút "Đăng ký" / clicks "Register" button

2. **Validate dữ liệu / Data Validation:**
   - UI gửi dữ liệu đến RegistrationController
   - RegistrationController gọi ValidationService
   - ValidationService kiểm tra:
     * Email format hợp lệ / valid email format
     * Password đủ mạnh (min 8 ký tự, có chữ hoa, số, ký tự đặc biệt)
     * Phone number format đúng
     * Các trường bắt buộc không để trống / required fields not empty

3. **Kiểm tra trùng lặp / Check Duplicates:**
   - RegistrationController gọi UserRepository.checkExistingUser(email, username)
   - UserRepository query Database
   - Nếu email/username đã tồn tại → return lỗi / if exists → return error

4. **Tạo tài khoản / Create Account:**
   - RegistrationController hash password
   - RegistrationController gọi UserRepository.createUser()
   - UserRepository insert vào Database
   - Database trả về userId

5. **Gửi email xác thực / Send Verification Email:**
   - RegistrationController tạo verification token
   - RegistrationController gọi EmailService.sendVerificationEmail()
   - EmailService gửi email chứa link xác thực

6. **Phản hồi / Response:**
   - UI hiển thị thông báo thành công
   - Yêu cầu Customer kiểm tra email để xác thực

**Luồng thay thế / Alternative Flows:**

**Alt 1: Validation thất bại / Validation Failed**
- Nếu dữ liệu không hợp lệ ở bước 2
- ValidationService return error message
- UI hiển thị lỗi cụ thể (VD: "Email không hợp lệ", "Mật khẩu quá yếu")
- Customer sửa lại và submit lại

**Alt 2: Email/Username đã tồn tại / Email/Username Already Exists**
- Nếu phát hiện trùng ở bước 3
- UserRepository return error "Already exists"
- UI hiển thị: "Email/Username đã được sử dụng"
- Customer phải đổi email/username khác

**Alt 3: Lỗi gửi email / Email Sending Failed**
- Nếu EmailService.sendVerificationEmail() failed
- Log lỗi nhưng vẫn tạo tài khoản thành công
- UI hiển thị: "Đăng ký thành công nhưng không gửi được email xác thực"
- Cung cấp nút "Gửi lại email xác thực"

**Gợi ý vẽ / Drawing Tips:**
- Sử dụng activation box để thể hiện thời gian xử lý
- Đánh số thứ tự các message (1, 1.1, 1.2, 2, 2.1...)
- Dùng alt fragment cho các luồng thay thế
- Dùng opt fragment cho các bước tùy chọn

---

## Bài Tập 2: Quy Trình Tìm Kiếm và Xem Sản Phẩm / Exercise 2: Product Search and View Process

**Mô tả / Description:**
Thiết kế sequence diagram cho quy trình tìm kiếm sản phẩm và xem chi tiết.
Design a sequence diagram for product search and detail viewing process.

**Yêu cầu / Requirements:**

**Các Actor/Object:**
- **Customer**: Khách hàng tìm kiếm
- **SearchUI**: Giao diện tìm kiếm
- **SearchController**: Xử lý tìm kiếm
- **ElasticsearchService**: Service tìm kiếm (hoặc SearchService)
- **ProductRepository**: Truy xuất thông tin sản phẩm
- **CacheService**: Redis/Memcached cache
- **RecommendationEngine**: Gợi ý sản phẩm liên quan
- **Database**: Cơ sở dữ liệu

**Luồng chính / Main Flow:**

1. **Nhập từ khóa tìm kiếm / Enter Search Query:**
   - Customer nhập keyword vào search box: "áo khoác nam"
   - SearchUI gọi SearchController.search(keyword, filters, page)
   - Filters có thể bao gồm: price range, category, brand, rating

2. **Tìm kiếm với Cache / Search with Cache:**
   - SearchController kiểm tra CacheService.get(searchKey)
   - Nếu có cache hit (kết quả đã lưu):
     * CacheService return cached results
     * Skip bước 3-4, nhảy thẳng đến bước 5
   - Nếu cache miss → tiếp tục bước 3

3. **Thực hiện tìm kiếm / Execute Search:**
   - SearchController gọi ElasticsearchService.search(keyword, filters)
   - ElasticsearchService thực hiện full-text search
   - Áp dụng các filters: category, price range, rating
   - ElasticsearchService return list of productIds với relevance score

4. **Lấy thông tin chi tiết sản phẩm / Fetch Product Details:**
   - SearchController gọi ProductRepository.getProductsByIds(productIds)
   - ProductRepository query Database
   - Database return product details (name, price, images, rating, stock)

5. **Lưu cache / Save to Cache:**
   - SearchController gọi CacheService.set(searchKey, results, TTL=300s)
   - CacheService lưu kết quả với thời gian sống 5 phút

6. **Hiển thị kết quả / Display Results:**
   - SearchController return results đến SearchUI
   - SearchUI hiển thị danh sách sản phẩm (grid/list view)
   - Mỗi sản phẩm hiển thị: thumbnail, name, price, rating, badge (sale/new)

7. **Customer chọn xem chi tiết / Customer Views Detail:**
   - Customer click vào một sản phẩm
   - SearchUI gọi ProductController.getProductDetail(productId)

8. **Lấy thông tin đầy đủ / Get Full Product Info:**
   - ProductController check CacheService
   - Nếu không có cache, gọi ProductRepository.getProductDetail(productId)
   - ProductRepository query Database lấy:
     * Full description
     * All images
     * Variants (size, color)
     * Stock quantity
     * Specifications

9. **Lấy đánh giá / Get Reviews:**
   - ProductController gọi ReviewRepository.getReviews(productId, limit=5)
   - ReviewRepository return top reviews with ratings

10. **Gợi ý sản phẩm liên quan / Get Recommendations:**
    - ProductController gọi RecommendationEngine.getSimilarProducts(productId)
    - RecommendationEngine sử dụng collaborative filtering hoặc content-based
    - Return list of similar products

11. **Hiển thị trang chi tiết / Display Product Detail Page:**
    - ProductController return full product data
    - SearchUI render product detail page với:
      * Image gallery
      * Product info and variants
      * Price and stock status
      * Reviews
      * Recommended products
      * Add to cart button

**Luồng thay thế / Alternative Flows:**

**Alt 1: Không tìm thấy kết quả / No Results Found**
- ElasticsearchService return empty list
- SearchUI hiển thị: "Không tìm thấy sản phẩm phù hợp"
- Gợi ý: điều chỉnh bộ lọc, tìm từ khóa khác
- Hiển thị sản phẩm phổ biến hoặc gần giống

**Alt 2: Sản phẩm hết hàng / Product Out of Stock**
- Khi lấy product detail, stock = 0
- ProductController đánh dấu status = OUT_OF_STOCK
- SearchUI hiển thị badge "Hết hàng"
- Disable nút "Thêm vào giỏ"
- Hiển thị nút "Nhận thông báo khi có hàng"

**Alt 3: Lỗi service tìm kiếm / Search Service Error**
- ElasticsearchService throw exception
- SearchController catch error
- Fallback: gọi ProductRepository.searchInDatabase(keyword)
- Tìm kiếm trực tiếp trong DB (chậm hơn)
- Log error để admin khắc phục ElasticSearch

**Alt 4: Lỗi timeout / Timeout Error**
- Nếu ElasticsearchService quá 3s không response
- SearchController timeout và return partial results
- UI hiển thị warning: "Một số kết quả có thể không đầy đủ"

**Gợi ý vẽ / Drawing Tips:**
- Sử dụng opt fragment cho cache check
- Sử dụng alt fragment cho cache hit/miss
- Sử dụng loop fragment nếu cần paginate results
- Thể hiện parallel requests (reviews + recommendations) bằng par fragment

---

## Bài Tập 3: Quy Trình Thêm Sản Phẩm Vào Giỏ Hàng / Exercise 3: Add to Cart Process

**Mô tả / Description:**
Thiết kế sequence diagram cho quy trình thêm sản phẩm vào giỏ hàng và áp dụng mã giảm giá.
Design a sequence diagram for adding products to cart and applying discount codes.

**Yêu cầu / Requirements:**

**Các Actor/Object:**
- **Customer**: Khách hàng mua sắm
- **ProductDetailUI**: Trang chi tiết sản phẩm
- **CartUI**: Trang giỏ hàng
- **CartController**: Xử lý logic giỏ hàng
- **CartService**: Business logic giỏ hàng
- **ProductService**: Xử lý sản phẩm
- **InventoryService**: Quản lý tồn kho
- **DiscountService**: Xử lý khuyến mãi
- **CartRepository**: Truy xuất dữ liệu giỏ hàng
- **CacheService**: Redis cache cho giỏ hàng
- **Database**: Cơ sở dữ liệu

**Luồng chính / Main Flow:**

**Phần 1: Thêm sản phẩm vào giỏ / Part 1: Add Product to Cart**

1. **Chọn sản phẩm / Select Product:**
   - Customer đang ở ProductDetailUI
   - Customer chọn variant (size: L, color: Red)
   - Customer chọn quantity = 2
   - Customer click button "Thêm vào giỏ hàng" / "Add to Cart"

2. **Validate lựa chọn / Validate Selection:**
   - ProductDetailUI gọi CartController.addToCart(productId, variantId, quantity)
   - CartController gọi ProductService.getProductVariant(variantId)
   - ProductService return variant info (price, sku)

3. **Kiểm tra tồn kho / Check Inventory:**
   - CartController gọi InventoryService.checkStock(variantId, quantity)
   - InventoryService query Database
   - Kiểm tra: available_stock >= quantity
   - Return stock status (available/insufficient)

4. **Lấy giỏ hàng hiện tại / Get Current Cart:**
   - CartController gọi CartService.getCart(customerId)
   - CartService check CacheService.get(cartKey)
   - Nếu có cache → return cart từ cache
   - Nếu không → CartService gọi CartRepository.getCart(customerId)

5. **Cập nhật giỏ hàng / Update Cart:**
   - CartService kiểm tra sản phẩm đã có trong giỏ chưa:
     * Nếu đã có → cộng thêm quantity
     * Nếu chưa → thêm item mới
   - CartService gọi CartRepository.updateCart(cart)
   - CartRepository update Database

6. **Cập nhật cache / Update Cache:**
   - CartService gọi CacheService.set(cartKey, cart, TTL=3600s)
   - CacheService update cart trong Redis

7. **Reserve tồn kho tạm thời / Reserve Inventory (Optional):**
   - CartService gọi InventoryService.reserveStock(variantId, quantity, customerId)
   - Giữ tồn kho trong 15 phút
   - Tránh trường hợp customer thêm vào giỏ nhưng hết hàng khi checkout

8. **Phản hồi thành công / Success Response:**
   - CartController return success với cart summary
   - ProductDetailUI hiển thị notification: "Đã thêm vào giỏ hàng"
   - Update cart icon badge: số lượng items trong giỏ

**Phần 2: Xem và cập nhật giỏ hàng / Part 2: View and Update Cart**

9. **Customer mở giỏ hàng / Customer Opens Cart:**
   - Customer click vào cart icon
   - CartUI gọi CartController.getCartDetails(customerId)

10. **Lấy thông tin đầy đủ / Get Full Cart Info:**
    - CartController gọi CartService.getCartWithDetails(customerId)
    - CartService lấy cart từ cache/DB
    - Với mỗi item trong cart:
      * Gọi ProductService.getProductInfo(productId) để lấy tên, hình ảnh mới nhất
      * Gọi InventoryService.checkStock(variantId) để verify còn hàng
    - CartService tính subtotal cho từng item

11. **Tính tổng giỏ hàng / Calculate Cart Total:**
    - CartService.calculateTotal():
      * subtotal = sum(item.price * item.quantity)
      * shipping_fee = calculateShipping(subtotal, address)
      * discount = 0 (chưa áp dụng mã)
      * total = subtotal + shipping_fee - discount

**Phần 3: Áp dụng mã giảm giá / Part 3: Apply Discount Code**

12. **Customer nhập mã giảm giá / Customer Enters Coupon:**
    - Customer nhập coupon code: "SUMMER2024"
    - Customer click "Áp dụng" / "Apply"
    - CartUI gọi CartController.applyCoupon(customerId, couponCode)

13. **Validate mã giảm giá / Validate Coupon:**
    - CartController gọi DiscountService.validateCoupon(couponCode, customerId)
    - DiscountService kiểm tra:
      * Mã có tồn tại không
      * Mã đã hết hạn chưa (startDate <= now <= endDate)
      * Customer đã sử dụng mã này chưa (nếu limit 1 lần/user)
      * Tổng đơn hàng có đạt minimum_order_value không
      * Số lần sử dụng mã đã đạt max chưa
    - DiscountService return validation result

14. **Tính giảm giá / Calculate Discount:**
    - Nếu valid, DiscountService.calculateDiscount(couponCode, cartTotal):
      * Nếu discount_type = PERCENTAGE: discount = subtotal * percentage / 100
      * Nếu discount_type = FIXED_AMOUNT: discount = fixed_value
      * Nếu discount_type = FREE_SHIPPING: shipping_fee = 0
    - Áp dụng max_discount_amount nếu có
    - Return discount_amount

15. **Cập nhật giỏ hàng với giảm giá / Update Cart with Discount:**
    - CartService.applyCouponToCart(cart, couponCode, discountAmount)
    - Lưu coupon_code và discount vào cart
    - Tính lại total = subtotal + shipping_fee - discount
    - CartRepository.updateCart(cart)
    - CacheService.set(cartKey, cart)

16. **Hiển thị giảm giá / Display Discount:**
    - CartUI update view:
      * Hiển thị dòng "Mã giảm giá: SUMMER2024 (-200,000đ)"
      * Update total price
      * Highlight số tiền tiết kiệm được

**Luồng thay thế / Alternative Flows:**

**Alt 1: Không đủ hàng / Insufficient Stock**
- Ở bước 3, InventoryService return insufficient_stock
- CartController return error
- ProductDetailUI hiển thị: "Chỉ còn X sản phẩm trong kho"
- Suggest Customer giảm quantity hoặc chọn variant khác

**Alt 2: Sản phẩm đã có trong giỏ / Product Already in Cart**
- Ở bước 5, CartService phát hiện item đã có
- Cộng thêm quantity
- Nhưng phải check lại tồn kho với tổng quantity mới
- Nếu tổng quantity > stock → return error
- UI hiển thị: "Đã có trong giỏ, tăng số lượng lên X"

**Alt 3: Mã giảm giá không hợp lệ / Invalid Coupon**
- Ở bước 13, DiscountService return validation error với lý do cụ thể:
  * "Mã giảm giá không tồn tại"
  * "Mã giảm giá đã hết hạn"
  * "Bạn đã sử dụng mã này rồi"
  * "Đơn hàng chưa đạt giá trị tối thiểu 500,000đ"
  * "Mã giảm giá đã hết lượt sử dụng"
- CartUI hiển thị error message
- Không áp dụng giảm giá

**Alt 4: Customer chưa đăng nhập / Customer Not Logged In**
- Khi addToCart(), CartController check authentication
- Nếu chưa đăng nhập:
  * Lưu cart vào session/localStorage (guest cart)
  * CartService.createGuestCart(sessionId)
  * Khi login sau, merge guest cart với user cart
  * CartService.mergeCart(guestCartId, userCartId)

**Alt 5: Customer xóa item khỏi giỏ / Remove Item from Cart**
- Customer click nút xóa
- CartUI gọi CartController.removeItem(customerId, cartItemId)
- CartService.removeItem(cartItemId)
- InventoryService.releaseReservedStock(variantId, quantity)
- Update cart trong DB và cache
- Tính lại total
- Nếu cart rỗng → hiển thị "Giỏ hàng trống"

**Alt 6: Customer thay đổi quantity / Change Quantity**
- Customer thay đổi quantity từ 2 → 5
- CartUI gọi CartController.updateQuantity(customerId, cartItemId, newQuantity)
- Check stock với quantity mới
- Nếu đủ → update cart
- Nếu không đủ → return error "Chỉ còn X sản phẩm"
- Tính lại total

**Gợi ý vẽ / Drawing Tips:**
- Chia thành 3 phần rõ ràng với ref fragments
- Sử dụng opt fragment cho cache check
- Sử dụng alt fragment cho stock validation
- Sử dụng loop fragment khi tính toán cho multiple items
- Thể hiện async calls nếu có (VD: reserve inventory có thể async)

---

## Bài Tập 4: Quy Trình Đặt Hàng và Thanh Toán / Exercise 4: Checkout and Payment Process

**Mô tả / Description:**
Thiết kế sequence diagram cho quy trình đặt hàng từ checkout đến thanh toán.
Design a sequence diagram for the checkout and payment process.

**Yêu cầu / Requirements:**

**Các Actor/Object:**
- **Customer**: Khách hàng thanh toán
- **CheckoutUI**: Trang checkout
- **OrderController**: Xử lý đơn hàng
- **OrderService**: Business logic đơn hàng
- **CartService**: Lấy thông tin giỏ hàng
- **AddressService**: Quản lý địa chỉ
- **ShippingService**: Tính phí ship, ước tính thời gian
- **InventoryService**: Quản lý tồn kho
- **PaymentGateway**: Cổng thanh toán (VNPay, Momo, Stripe)
- **PaymentService**: Xử lý thanh toán
- **NotificationService**: Gửi thông báo
- **OrderRepository**: Lưu đơn hàng
- **Database**: Cơ sở dữ liệu

**Luồng chính / Main Flow:**

**Phần 1: Khởi tạo Checkout / Part 1: Initialize Checkout**

1. **Customer bắt đầu checkout / Customer Starts Checkout:**
   - Customer ở CartUI click "Tiến hành thanh toán" / "Proceed to Checkout"
   - CartUI redirect đến CheckoutUI
   - CheckoutUI gọi OrderController.initCheckout(customerId)

2. **Lấy thông tin giỏ hàng / Get Cart Information:**
   - OrderController gọi CartService.getCart(customerId)
   - CartService return cart với tất cả items
   - Validate cart không rỗng

3. **Verify tồn kho / Verify Inventory:**
   - OrderController gọi InventoryService.verifyCartStock(cartItems)
   - InventoryService kiểm tra từng item:
     * Sản phẩm còn đủ số lượng không
     * Giá có thay đổi không
   - Return verification result
   - Nếu có item out of stock → show warning

4. **Lấy địa chỉ giao hàng / Get Shipping Address:**
   - OrderController gọi AddressService.getCustomerAddresses(customerId)
   - AddressService return list of saved addresses
   - Default address được đánh dấu

5. **Tính phí ship / Calculate Shipping:**
   - OrderController gọi ShippingService.calculateShipping(cart, addressId)
   - ShippingService:
     * Tính trọng lượng/kích thước tổng
     * Tính khoảng cách từ warehouse đến địa chỉ
     * Áp dụng bảng giá ship
     * Return shipping_fee và estimated_delivery_date

6. **Tính tổng đơn hàng / Calculate Order Total:**
   - OrderService.calculateOrderTotal():
     * subtotal = sum(item.price * item.quantity)
     * shipping_fee = from ShippingService
     * discount = from applied coupon (nếu có)
     * tax = subtotal * tax_rate (nếu áp dụng)
     * total = subtotal + shipping_fee + tax - discount

7. **Hiển thị trang checkout / Display Checkout Page:**
   - CheckoutUI render với:
     * Order summary (items, prices)
     * Shipping address (có thể chọn hoặc thêm mới)
     * Shipping method options
     * Payment method options (COD, Card, E-wallet)
     * Order total breakdown
     * Coupon code field (nếu chưa áp dụng)

**Phần 2: Customer xác nhận và chọn thanh toán / Part 2: Confirm and Choose Payment**

8. **Customer xác nhận thông tin / Customer Confirms Info:**
   - Customer review order summary
   - Customer chọn/xác nhận shipping address
   - Customer chọn payment method: "Thẻ tín dụng" / "Credit Card"
   - Customer check "Đồng ý điều khoản" / "Accept terms"
   - Customer click "Đặt hàng" / "Place Order"

9. **Tạo đơn hàng / Create Order:**
   - CheckoutUI gọi OrderController.createOrder(orderData)
   - OrderController validate order data
   - OrderController gọi OrderService.createOrder()

10. **Lock inventory / Lock Inventory:**
    - OrderService gọi InventoryService.lockStock(orderItems)
    - InventoryService:
      * Check stock availability lần cuối
      * Lock items để tránh overselling
      * Giảm available_stock, tăng reserved_stock
      * Set lock_timeout = 15 minutes (nếu không thanh toán, unlock)

11. **Lưu đơn hàng với trạng thái PENDING / Save Order as PENDING:**
    - OrderService gọi OrderRepository.createOrder(order)
    - Order được tạo với status = PENDING_PAYMENT
    - OrderRepository insert vào Database
    - Database return orderId

12. **Tạo payment transaction / Create Payment Transaction:**
    - OrderService gọi PaymentService.createPayment(orderId, amount, method)
    - PaymentService create payment record với status = PENDING
    - PaymentService return paymentId

**Phần 3: Xử lý thanh toán / Part 3: Process Payment**

13. **Redirect đến cổng thanh toán / Redirect to Payment Gateway:**
    - PaymentService gọi PaymentGateway.initPayment(paymentData):
      * orderId
      * amount
      * returnUrl (callback sau khi thanh toán)
      * cancelUrl
    - PaymentGateway generate payment URL
    - CheckoutUI redirect Customer đến payment URL

14. **Customer thanh toán / Customer Makes Payment:**
    - Customer ở trang PaymentGateway
    - Customer nhập thông tin thẻ:
      * Card number
      * Expiry date
      * CVV
      * Cardholder name
    - Customer click "Thanh toán" / "Pay"

15. **Gateway xử lý thanh toán / Gateway Processes Payment:**
    - PaymentGateway validate card info
    - PaymentGateway gọi bank API để authorize transaction
    - Bank perform 3D Secure authentication (nếu cần)
    - Bank return payment result (success/failed)

16. **Callback về hệ thống / Callback to System:**
    - PaymentGateway gọi callback URL của hệ thống
    - PaymentGateway POST payment result đến OrderController.handlePaymentCallback()
    - Kèm theo: transactionId, status, signature (để verify)

**Phần 4: Xác nhận đơn hàng / Part 4: Confirm Order**

17. **Verify payment signature / Verify Payment Signature:**
    - OrderController gọi PaymentService.verifyCallback(callbackData)
    - PaymentService kiểm tra signature để đảm bảo callback từ Gateway thật
    - Verify amount khớp với order

18. **Cập nhật trạng thái payment / Update Payment Status:**
    - PaymentService.updatePaymentStatus(paymentId, COMPLETED)
    - Lưu transactionId từ Gateway
    - Update Database

19. **Confirm đơn hàng / Confirm Order:**
    - OrderService gọi OrderRepository.updateOrderStatus(orderId, CONFIRMED)
    - Update order với:
      * status = CONFIRMED
      * paid_at = current_timestamp
      * payment_method = "CREDIT_CARD"
      * transaction_id

20. **Deduct inventory / Deduct Inventory:**
    - OrderService gọi InventoryService.deductStock(orderItems)
    - InventoryService:
      * Giảm reserved_stock
      * Giảm total_stock
      * Log inventory transaction

21. **Xóa giỏ hàng / Clear Cart:**
    - OrderService gọi CartService.clearCart(customerId)
    - CartService xóa cart items từ DB và cache

22. **Gửi thông báo / Send Notifications:**
    - OrderService gọi NotificationService.sendOrderConfirmation()
    - NotificationService gửi:
      * **Email đến Customer**:
        - Order confirmation
        - Order details
        - Invoice
        - Tracking info
      * **SMS đến Customer**: "Đơn hàng #12345 đã được xác nhận"
      * **Notification đến Seller**: Có đơn hàng mới cần xử lý
      * **Push notification** (nếu có app)

23. **Redirect đến trang thành công / Redirect to Success Page:**
    - CheckoutUI redirect Customer đến OrderSuccessUI
    - OrderSuccessUI hiển thị:
      * "Đặt hàng thành công!" message
      * Order number
      * Expected delivery date
      * Link "Xem chi tiết đơn hàng"
      * Link "Tiếp tục mua sắm"

**Luồng thay thế / Alternative Flows:**

**Alt 1: Thanh toán thất bại / Payment Failed**
- Ở bước 15, Bank decline payment (insufficient fun
ds, invalid card, etc.)
- PaymentGateway return failed status
- Ở bước 18, PaymentService.updatePaymentStatus(paymentId, FAILED)
- OrderService gọi OrderRepository.updateOrderStatus(orderId, PAYMENT_FAILED)
- InventoryService.unlockStock(orderItems) - giải phóng tồn kho đã lock
- CheckoutUI redirect về payment page với error message:
  * "Thanh toán thất bại: [lý do]"
  * "Vui lòng thử lại hoặc chọn phương thức thanh toán khác"
- Customer có thể:
  * Thử lại với cùng payment method
  * Chọn payment method khác
  * Cancel order

**Alt 2: Customer hủy thanh toán / Customer Cancels Payment**
- Ở bước 14, Customer click "Hủy" / "Cancel" ở trang Gateway
- PaymentGateway redirect về cancelUrl
- OrderController.handlePaymentCancel(orderId)
- PaymentService update status = CANCELLED
- OrderService update order status = CANCELLED
- InventoryService.unlockStock(orderItems)
- CheckoutUI hiển thị: "Thanh toán đã bị hủy"
- Giỏ hàng vẫn giữ nguyên để Customer có thể checkout lại

**Alt 3: Payment timeout / Payment Timeout**
- Sau 15 phút Customer không hoàn tất thanh toán
- Background job (scheduled task) chạy:
  * OrderService.checkPendingOrders()
  * Tìm orders với status = PENDING_PAYMENT và created_at > 15 mins ago
  * OrderService.expireOrder(orderId)
  * Update order status = EXPIRED
  * InventoryService.unlockStock(orderItems)
- Nếu Customer quay lại sau đó, hiển thị: "Đơn hàng đã hết hạn, vui lòng đặt lại"

**Alt 4: Sản phẩm hết hàng khi checkout / Out of Stock During Checkout**
- Ở bước 3 hoặc 10, InventoryService phát hiện item không đủ stock
- Return error với item details
- OrderController return error
- CheckoutUI hiển thị:
  * "Sản phẩm [tên] chỉ còn [X] trong kho"
  * "Sản phẩm [tên] đã hết hàng"
- Suggest Customer:
  * Giảm số lượng
  * Xóa item khỏi cart
  * Quay lại cart để cập nhật

**Alt 5: Địa chỉ không hợp lệ / Invalid Address**
- Ở bước 5, ShippingService.calculateShipping() failed
- Lý do có thể:
  * Địa chỉ không đầy đủ
  * Khu vực không giao hàng
  * Địa chỉ nằm ngoài phạm vi
- CheckoutUI hiển thị error
- Yêu cầu Customer:
  * Cập nhật địa chỉ
  * Chọn địa chỉ khác
  * Thêm địa chỉ mới

**Alt 6: Thanh toán COD / COD Payment**
- Ở bước 8, Customer chọn payment method = "COD" (Cash on Delivery)
- Skip bước 13-16 (không cần payment gateway)
- Ở bước 11, order được tạo với status = CONFIRMED (không phải PENDING_PAYMENT)
- PaymentService.createPayment() với status = PENDING_COD
- Inventory được deduct ngay
- NotificationService gửi thông báo:
  * Customer: "Đơn hàng xác nhận, thanh toán khi nhận hàng"
  * Shipper: Đơn hàng COD cần thu tiền
- Khi shipper giao hàng thành công:
  * Shipper confirm delivery
  * PaymentService.updatePaymentStatus(paymentId, COMPLETED)
  * Order status = COMPLETED

**Alt 7: Thanh toán ví điện tử / E-Wallet Payment**
- Ở bước 8, Customer chọn "Ví MoMo" / "ZaloPay"
- Ở bước 13, PaymentGateway.initPayment() return different flow:
  * Không redirect sang trang web
  * Return QR code hoặc deep link
- CheckoutUI hiển thị:
  * QR code để Customer scan bằng app
  * Hoặc deep link để mở app ví
- Customer xác nhận thanh toán trong app
- E-wallet app gọi callback API
- Các bước 16-23 tương tự

**Alt 8: Mã giảm giá hết hạn trong lúc checkout / Coupon Expires During Checkout**
- Giữa bước 1-11, coupon đã applied trong cart hết hạn
- Ở bước 6, OrderService.calculateOrderTotal() gọi DiscountService
- DiscountService.validateCoupon() return expired
- OrderService remove coupon khỏi order
- Tính lại total không có discount
- CheckoutUI hiển thị warning:
  * "Mã giảm giá đã hết hạn"
  * Show giá mới (cao hơn)
- Customer phải xác nhận lại mới place order

**Alt 9: Giá sản phẩm thay đổi / Price Changes**
- Giữa lúc Customer ở cart và checkout, seller thay đổi giá
- Ở bước 3, InventoryService.verifyCartStock() phát hiện price mismatch
- Return warning với old price và new price
- CheckoutUI hiển thị:
  * "Giá sản phẩm [tên] đã thay đổi từ [old] → [new]"
- Recalculate total
- Customer phải xác nhận lại để tiếp tục

**Alt 10: Gateway không phản hồi / Gateway Timeout**
- Ở bước 16, PaymentGateway không callback sau 5 phút
- OrderService có background job check payment status:
  * PaymentService.queryPaymentStatus(paymentId, transactionId)
  * Gọi API của Gateway để query trạng thái
- Nếu Gateway confirm payment success:
  * Update order như bình thường (bước 18-23)
- Nếu Gateway confirm failed:
  * Update status = FAILED và unlock inventory
- Nếu Gateway không có info:
  * Giữ order ở PENDING
  * Notify admin để kiểm tra thủ công
  * Notify Customer: "Đơn hàng đang được xác nhận"

**Gợi ý vẽ / Drawing Tips:**
- Chia diagram thành 4 phần rõ ràng với ref fragments:
  * ref Initialize Checkout
  * ref Confirm and Choose Payment
  * ref Process Payment
  * ref Confirm Order
- Sử dụng alt fragment cho các payment methods khác nhau (Card/COD/E-wallet)
- Sử dụng opt fragment cho optional steps (như apply coupon)
- Sử dụng loop fragment khi verify multiple cart items
- Note quan trọng: thêm timing constraints (VD: payment timeout = 15 min)
- Thể hiện async operations: notification sending có thể async

---

## Bài Tập 5: Quy Trình Đánh Giá Sản Phẩm / Exercise 5: Product Review Process

**Mô tả / Description:**
Thiết kế sequence diagram cho quy trình khách hàng đánh giá sản phẩm đã mua và seller phản hồi.
Design a sequence diagram for customers reviewing purchased products and sellers responding.

**Yêu cầu / Requirements:**

**Các Actor/Object:**
- **Customer**: Khách hàng đánh giá
- **Seller**: Người bán phản hồi
- **ReviewUI**: Giao diện đánh giá
- **ReviewController**: Xử lý logic đánh giá
- **ReviewService**: Business logic review
- **OrderService**: Kiểm tra đơn hàng
- **ProductService**: Cập nhật rating sản phẩm
- **ImageService**: Xử lý upload ảnh
- **ModerationService**: Kiểm duyệt nội dung
- **NotificationService**: Gửi thông báo
- **ReviewRepository**: Lưu trữ đánh giá
- **Database**: Cơ sở dữ liệu

**Luồng chính / Main Flow:**

**Phần 1: Customer viết đánh giá / Part 1: Customer Writes Review**

1. **Customer truy cập trang đánh giá / Customer Accesses Review Page:**
   - Customer vào "Đơn hàng của tôi" / "My Orders"
   - OrderListUI hiển thị các đơn hàng đã COMPLETED
   - Đơn hàng có button "Đánh giá" / "Write Review" (nếu chưa review)
   - Customer click "Đánh giá" cho order #12345

2. **Khởi tạo form đánh giá / Initialize Review Form:**
   - OrderListUI gọi ReviewController.initReview(orderId, customerId)
   - ReviewController gọi OrderService.getOrderDetails(orderId)
   - OrderService verify:
     * Order thuộc về customer này
     * Order status = COMPLETED
     * Order đã được giao thành công
   - OrderService return order details với danh sách products

3. **Hiển thị form / Display Review Form:**
   - ReviewController gọi ReviewService.checkExistingReviews(orderId, customerId)
   - ReviewService return các products đã/chưa review
   - ReviewUI render form cho từng product:
     * Product image và name
     * Rating selector (1-5 stars)
     * Title field
     * Review content textarea
     * Image upload (tối đa 5 ảnh)
     * Checkbox "Ẩn danh" / "Anonymous" (optional)

4. **Customer điền thông tin / Customer Fills Information:**
   - Customer chọn product đầu tiên để review
   - Customer chọn rating: 5 stars ⭐⭐⭐⭐⭐
   - Customer nhập title: "Sản phẩm tuyệt vời!"
   - Customer nhập content: "Chất lượng tốt, đóng gói cẩn thận, giao hàng nhanh..."
   - Customer upload 3 ảnh sản phẩm thực tế

5. **Upload ảnh / Upload Images:**
   - Với mỗi ảnh, ReviewUI gọi ImageService.uploadReviewImage(file)
   - ImageService:
     * Validate file (size < 5MB, type = jpg/png)
     * Resize ảnh để tối ưu (compress)
     * Upload lên cloud storage (S3, Cloudinary)
     * Generate image URL
   - ImageService return imageUrl
   - ReviewUI lưu tạm danh sách imageUrls

6. **Customer submit review / Customer Submits Review:**
   - Customer click "Gửi đánh giá" / "Submit Review"
   - ReviewUI validate:
     * Rating đã chọn (required)
     * Content length >= 10 characters
   - ReviewUI gọi ReviewController.submitReview(reviewData)

7. **Validate và lưu review / Validate and Save Review:**
   - ReviewController gọi ReviewService.createReview(reviewData)
   - ReviewService validate:
     * Customer đã mua sản phẩm này (verified purchase)
     * Customer chưa review sản phẩm này trong order này
   - ReviewService gọi ModerationService.checkContent(content)

8. **Kiểm duyệt nội dung / Content Moderation:**
   - ModerationService check:
     * Ngôn từ không phù hợp (profanity filter)
     * Spam detection
     * Fake review patterns
     * Sensitive information (phone, email, địa chỉ)
   - ModerationService return moderation result:
     * APPROVED: nội dung ok
     * FLAGGED: cần review thủ công
     * REJECTED: vi phạm policy

9. **Lưu review / Save Review:**
   - Nếu APPROVED hoặc FLAGGED:
     * ReviewService gọi ReviewRepository.createReview(review)
     * Review được lưu với:
       - reviewId
       - productId, customerId, orderId
       - rating, title, content
       - imageUrls
       - isVerifiedPurchase = true
       - status = APPROVED hoặc PENDING (nếu FLAGGED)
       - createdAt
   - ReviewRepository insert vào Database

10. **Cập nhật rating sản phẩm / Update Product Rating:**
    - ReviewService gọi ProductService.updateProductRating(productId)
    - ProductService:
      * Tính average rating mới từ tất cả reviews
      * Cập nhật product.averageRating và product.totalReviews
      * Cập nhật rating distribution (5★: 100, 4★: 50, ...)
    - ProductService update Database

11. **Gửi thông báo / Send Notifications:**
    - ReviewService gọi NotificationService.notifyNewReview()
    - NotificationService gửi:
      * **Notification đến Seller**:
        - "Bạn có đánh giá mới từ [Customer name]"
        - Link đến review
      * **Email đến Seller** (nếu rating <= 3 stars):
        - Alert về negative review
        - Khuyến khích phản hồi nhanh
      * **Push notification** (nếu có app)

12. **Tăng loyalty points / Award Loyalty Points:**
    - ReviewService gọi LoyaltyService.awardPoints(customerId, "REVIEW")
    - LoyaltyService cộng points cho customer (VD: +10 points)
    - Update customer.loyaltyPoints

13. **Phản hồi thành công / Success Response:**
    - ReviewUI hiển thị success message:
      * "Cảm ơn bạn đã đánh giá!"
      * "Bạn được cộng 10 điểm thưởng"
    - Nếu còn products chưa review trong order:
      * Hiển thị form review product tiếp theo
    - Nếu đã review hết:
      * Redirect về order detail page

**Phần 2: Seller phản hồi review / Part 2: Seller Responds to Review**

14. **Seller xem review / Seller Views Reviews:**
    - Seller login vào seller dashboard
    - SellerDashboardUI hiển thị notification: "5 đánh giá mới"
    - Seller click vào "Quản lý đánh giá" / "Manage Reviews"
    - SellerDashboardUI gọi ReviewController.getSellerReviews(sellerId)

15. **Lấy danh sách reviews / Get Reviews List:**
    - ReviewController gọi ReviewService.getReviewsBySeller(sellerId)
    - ReviewService query ReviewRepository
    - ReviewRepository return reviews:
      * Sắp xếp: mới nhất trước
      * Filter: chưa phản hồi, rating thấp priority cao
    - Kèm theo product info, customer name, order info

16. **Seller chọn review để phản hồi / Seller Selects Review:**
    - SellerDashboardUI hiển thị danh sách reviews
    - Seller click vào review cụ thể (reviewId = #789)
    - SellerDashboardUI gọi ReviewController.getReviewDetail(reviewId)
    - ReviewController return full review details:
      * Customer review content và images
      * Product info
      * Rating
      * Posted date

17. **Seller viết phản hồi / Seller Writes Response:**
    - SellerDashboardUI hiển thị form reply
    - Seller nhập reply content:
      * "Cảm ơn bạn đã tin tùng shop!"
      * "Rất vui khi bạn hài lòng với sản phẩm"
      * "Mong bạn tiếp tục ủng hộ"
    - Seller click "Gửi phản hồi" / "Send Reply"

18. **Submit reply / Submit Reply:**
    - SellerDashboardUI gọi ReviewController.replyToReview(reviewId, sellerId, replyContent)
    - ReviewController gọi ReviewService.createReply(replyData)

19. **Validate reply / Validate Reply:**
    - ReviewService validate:
      * Seller owns product của review này
      * Review chưa có reply (1 review chỉ 1 reply)
      * Reply content length >= 10 characters
    - ReviewService gọi ModerationService.checkContent(replyContent)

20. **Lưu reply / Save Reply:**
    - Nếu content ok, ReviewService gọi ReviewRepository.createReply(reply)
    - Reply được lưu với:
      * replyId
      * reviewId
      * sellerId
      * content
      * createdAt
    - ReviewRepository insert vào Database

21. **Update review status / Update Review Status:**
    - ReviewService update review.hasReply = true
    - ReviewService update review.repliedAt = current_timestamp

22. **Thông báo customer / Notify Customer:**
    - ReviewService gọi NotificationService.notifyReviewReply()
    - NotificationService gửi đến Customer:
      * **In-app notification**: "Người bán đã phản hồi đánh giá của bạn"
      * **Email**: "Phản hồi từ [Shop name] về đánh giá của bạn"
      * Include link đến review

23. **Phản hồi thành công / Reply Success:**
    - SellerDashboardUI hiển thị:
      * "Phản hồi thành công"
      * Reply content hiển thị dưới review
      * Update review status từ "Chưa phản hồi" → "Đã phản hồi"

**Phần 3: Customer tương tác với reviews / Part 3: Customer Interacts with Reviews**

24. **Customer xem reviews của sản phẩm / Customer Views Product Reviews:**
    - Customer ở ProductDetailUI
    - UI hiển thị section "Đánh giá khách hàng"
    - ProductDetailUI gọi ReviewController.getProductReviews(productId, page, filter)
    - Filter options:
      * Tất cả
      * Có hình ảnh
      * 5 sao / 4 sao / 3 sao / 2 sao / 1 sao
      * Đã mua hàng xác nhận

25. **Lấy reviews / Fetch Reviews:**
    - ReviewController gọi ReviewService.getReviews(productId, filter, pagination)
    - ReviewService query ReviewRepository với:
      * Filter by rating (nếu có)
      * Filter hasImages = true (nếu chọn)
      * Filter isVerifiedPurchase = true (nếu chọn)
      * Order by: helpful_count desc, created_at desc
      * Pagination: limit = 10, offset = page * 10
    - ReviewRepository return reviews list

26. **Hiển thị reviews / Display Reviews:**
    - ProductDetailUI render mỗi review với:
      * Customer name (hoặc "Người dùng ẩn danh")
      * Rating stars
      * Review title và content
      * Images (gallery)
      * Posted date
      * "Đã mua hàng" badge nếu verified
      * Seller reply (nếu có)
      * Like button và count
      * Report button

27. **Customer thích review / Customer Likes Review:**
    - Customer click "Hữu ích" / "Helpful" button
    - ProductDetailUI gọi ReviewController.likeReview(reviewId, customerId)
    - ReviewController gọi ReviewService.toggleLike()

28. **Xử lý like / Process Like:**
    - ReviewService check ReviewRepository.checkIfLiked(reviewId, customerId)
    - Nếu chưa like:
      * ReviewRepository.createLike(reviewId, customerId)
      * ReviewService increment review.likeCount
      * Return "liked"
    - Nếu đã like (unlike):
      * ReviewRepository.deleteLike(reviewId, customerId)
      * ReviewService decrement review.likeCount
      * Return "unliked"

29. **Cập nhật UI / Update UI:**
    - ProductDetailUI update like button state:
      * Nếu liked: button highlighted, count +1
      * Nếu unliked: button normal, count -1

**Luồng thay thế / Alternative Flows:**

**Alt 1: Review bị từ chối / Review Rejected**
- Ở bước 8, ModerationService return REJECTED
- ReviewService không lưu review
- ReviewController return error với reason:
  * "Nội dung chứa từ ngữ không phù hợp"
  * "Phát hiện spam"
  * "Nội dung vi phạm chính sách"
- ReviewUI hiển thị error
- Customer có thể chỉnh sửa và submit lại

**Alt 2: Review cần kiểm duyệt thủ công / Review Needs Manual Review**
- Ở bước 8, ModerationService return FLAGGED
- Review được lưu với status = PENDING
- Không hiển thị công khai ngay
- Admin nhận notification để review thủ công
- Admin dashboard:
  * Admin xem review content
  * Admin approve → status = APPROVED, hiển thị công khai
  * Admin reject → status = REJECTED, notify customer

**Alt 3: Customer chưa nhận hàng / Order Not Completed**
- Ở bước 2, OrderService.getOrderDetails() return order status != COMPLETED
- ReviewController return error: "Chỉ có thể đánh giá sau khi nhận hàng"
- OrderListUI không hiển thị button "Đánh giá"

**Alt 4: Customer đã review rồi / Already Reviewed**
- Ở bước 7, ReviewService phát hiện review đã tồn tại
- Return error: "Bạn đã đánh giá sản phẩm này"
- ReviewUI hiển thị existing review
- Cung cấp option "Chỉnh sửa đánh giá" thay vì tạo mới

**Alt 5: Upload ảnh thất bại / Image Upload Failed**
- Ở bước 5, ImageService.uploadReviewImage() failed
- Lý do: file quá lớn, format không hỗ trợ, lỗi network
- ReviewUI hiển thị error cho ảnh cụ thể
- Customer có thể:
  * Retry upload
  * Remove ảnh đó
  * Continue submit without ảnh

**Alt 6: Seller phản hồi không phù hợp / Inappropriate Seller Reply**
- Ở bước 19, ModerationService.checkContent() phát hiện reply vi phạm
- ReviewService không lưu reply
- Return error đến Seller
- SellerDashboardUI hiển thị:
  * "Phản hồi chứa nội dung không phù hợp"
  * "Vui lòng sử dụng ngôn từ chuyên nghiệp"

**Alt 7: Customer báo cáo review / Customer Reports Review**
- Customer thấy review spam/fake
- Customer click "Báo cáo" / "Report"
- ProductDetailUI gọi ReviewController.reportReview(reviewId, reason)
- ReviewService create report record
- Admin nhận notification
- Nếu report count > threshold (VD: 5 reports):
  * Auto hide review (status = HIDDEN)
  * Notify admin urgent review
- Admin investigate và quyết định:
  * Keep review (nếu hợp lệ)
  * Delete review (nếu vi phạm)
  * Ban user (nếu spam nhiều lần)

**Alt 8: Review hết hạn / Review Period Expired**
- Hệ thống cho phép review trong 30 ngày sau khi nhận hàng
- Ở bước 2, OrderService check:
  * order.completedAt + 30 days < now
- Return error: "Thời gian đánh giá đã hết"
- OrderListUI không hiển thị button "Đánh giá"

**Alt 9: Seller xóa phản hồi / Seller Deletes Reply**
- Seller muốn sửa/xóa reply đã gửi
- SellerDashboardUI có option "Xóa phản hồi"
- Seller click và confirm
- ReviewController.deleteReply(replyId, sellerId)
- ReviewService:
  * Verify seller owns reply
  * ReviewRepository.deleteReply()
  * Update review.hasReply = false
- Success message: "Đã xóa phản hồi"
- Seller có thể viết reply mới

**Alt 10: Customer chỉnh sửa review / Customer Edits Review**
- Customer muốn cập nhật review đã viết
- OrderListUI hoặc ReviewUI có button "Chỉnh sửa"
- Customer update rating/content/images
- ReviewUI gọi ReviewController.updateReview(reviewId, updatedData)
- ReviewService:
  * Validate ownership
  * Run moderation lại
  * Update review
  * Log edit history (review_edits table)
- Success: "Đánh giá đã được cập nhật"
- Note: Chỉ cho phép edit trong 7 ngày sau khi post

**Gợi ý vẽ / Drawing Tips:**
- Chia thành 3 phần với ref fragments:
  * ref Customer Writes Review
  * ref Seller Responds
  * ref Customer Interactions
- Sử dụng alt fragment cho moderation results (APPROVED/FLAGGED/REJECTED)
- Sử dụng loop fragment khi upload multiple images
- Sử dụng opt fragment cho optional steps (như upload ảnh)
- Sử dụng par fragment cho parallel operations (update rating + send notification)
- Thể hiện async operations: notifications có thể async
- Add notes để giải thích business rules (VD: review period = 30 days)

---

## Tổng Kết và Lưu Ý / Summary and Notes

### Nguyên tắc vẽ Sequence Diagram tốt / Good Sequence Diagram Principles:

1. **Sắp xếp objects hợp lý / Logical Object Arrangement:**
   - Từ trái qua phải theo luồng tương tác
   - Actor ở ngoài cùng bên trái
   - UI layer → Controller → Service → Repository → Database

2. **Đánh số message rõ ràng / Clear Message Numbering:**
   - Dùng hierarchical numbering: 1, 1.1, 1.2, 2, 2.1...
   - Giúp dễ trace và reference

3. **Sử dụng fragments đúng cách / Proper Fragment Usage:**
   - **alt**: alternative flows (if-else)
   - **opt**: optional steps
   - **loop**: lặp lại
   - **par**: parallel execution
   - **ref**: tham chiếu diagram khác
   - **break**: thoát sớm

4. **Activation boxes / Activation Boxes:**
   - Thể hiện thời gian object đang active
   - Nested activation cho recursive/self calls

5. **Return messages / Return Messages:**
   - Dùng dashed arrow (- - →) cho return
   - Label return value nếu quan trọng

6. **Notes và constraints / Notes and Constraints:**
   - Thêm notes để giải thích business logic
   - Ghi timing constraints (timeout, delay)

7. **Tránh quá phức tạp / Avoid Complexity:**
   - Một diagram không quá 20-30 messages
   - Sử dụng ref để chia nhỏ
   - Focus vào happy path, dùng alt cho exceptions

8. **Naming conventions / Naming Conventions:**
   - Method names rõ ràng: getOrder(), createPayment()
   - Parameters trong ngoặc: getOrder(orderId)
   - Return type nếu cần: : Order

### Tools gợi ý / Recommended Tools:
- **PlantUML**: text-based, version control friendly
- **Draw.io**: free, web-based
- **Lucidchart**: collaborative
- **Visual Paradigm**: professional
- **StarUML**: desktop app

### Best Practices:
- Review với team để đảm bảo đúng business flow
- Update diagram khi code thay đổi
- Sử dụng consistent notation
- Document assumptions và constraints
- Version control cho diagrams

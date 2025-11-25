Dưới đây là **WAMPP WooCommerce API Guidelines với POSTMAN** – cực kỳ rõ ràng, dành cho lớp lập trình web/e-commerce.

---

# ✅ **WAMPP + WooCommerce REST API + POSTMAN – Hướng dẫn đầy đủ**

## 1. **Chuẩn bị môi trường**

### 1.1 Cài WAMPP (hoặc XAMPP)

* Apache → ON
* MySQL → ON
* PHP ≥ 7.4

### 1.2 Cài WooCommerce trên WordPress

1. Giải nén WordPress vào:
   `C:\wamp64\www\woocommerce-local`
2. Truy cập:
   [http://localhost/woocommerce-local](http://localhost/woocommerce-local)
3. Cài plugin:

   * WooCommerce
   * WooCommerce REST API (tích hợp sẵn, không cần thêm)
   * Permalink: Setup **Post name** (Quan trọng để API chạy)

---

# 2. **Tạo API Key cho WooCommerce**

1. WordPress Admin → WooCommerce → **Settings**
2. Tab **Advanced** → **REST API**
3. **Add Key**

   * Permission: **Read/Write**
4. Lấy:

   * **Consumer Key**
   * **Consumer Secret**

**Lưu lại**, vì sau sẽ dùng để gọi POSTMAN.

---

# 3. **Cấu hình POSTMAN để gọi WooCommerce API**

## 3.1 Base URL

```
http://localhost/woocommerce-local/wp-json/wc/v3/
```

---

# 4. **Các API WooCommerce cơ bản nhất**

## 4.1 **GET All Products**

**Method:** GET
**URL:**

```
http://localhost/woocommerce-local/wp-json/wc/v3/products
```

**Authorization:**

* Type: **Basic Auth**
* Username: *Consumer Key*
* Password: *Consumer Secret*

**Kết quả:** danh sách products dạng JSON.

---

## 4.2 **POST – Tạo sản phẩm mới**

**Method:** POST
**URL:**

```
http://localhost/woocommerce-local/wp-json/wc/v3/products
```

**Headers**

```
Content-Type: application/json
```

**Body (raw):**

```json
{
  "name": "Laptop Dell Inspiron",
  "type": "simple",
  "regular_price": "15990000",
  "description": "Laptop Dell i5 thế hệ 12",
  "short_description": "Laptop Dell",
  "categories": [
    {
      "id": 12
    }
  ],
  "images": [
    {
      "src": "https://picsum.photos/300"
    }
  ]
}
```

---

## 4.3 **PUT – Update sản phẩm**

**Method:** PUT
**URL:**

```
http://localhost/woocommerce-local/wp-json/wc/v3/products/123
```

**Body:**

```json
{
  "regular_price": "14500000"
}
```

---

## 4.4 **DELETE – Xóa sản phẩm**

**Method:** DELETE
**URL:**

```
http://localhost/woocommerce-local/wp-json/wc/v3/products/123?force=true
```

---

# 5. **API Orders**

## 5.1 GET All Orders

```
GET http://localhost/woocommerce-local/wp-json/wc/v3/orders
```

## 5.2 Tạo Order mới

```
POST http://localhost/woocommerce-local/wp-json/wc/v3/orders
```

Body:

```json
{
  "payment_method": "cod",
  "payment_method_title": "Cash on delivery",
  "set_paid": true,
  "billing": {
    "first_name": "Tin",
    "last_name": "Trinh",
    "address_1": "UIT",
    "city": "Thu Duc"
  },
  "line_items": [
    {
      "product_id": 123,
      "quantity": 1
    }
  ]
}
```

---

# 6. **Lỗi thường gặp & cách fix**

| Lỗi                  | Nguyên nhân               | Cách fix                                   |
| -------------------- | ------------------------- | ------------------------------------------ |
| **401 Unauthorized** | Không đúng key/secret     | Kiểm tra Basic Auth                        |
| **404**              | Permalink sai             | Settings → Permalinks → chọn "Post name"   |
| **CORS**             | Gọi từ frontend JS        | Thêm plugin enable CORS                    |
| **SSL required**     | WooCommerce yêu cầu HTTPS | Tắt tùy chọn "Force SSL" trong WooCommerce |

---

# 7. **Checklist để API hoạt động**

* Apache **Rewrite Module ON**
  → Check bằng `httpd.conf`
* WooCommerce → Permalink = Post Name
* API Key = Read/Write
* POSTMAN = Basic Auth
* URL đúng wc/v3

---

Để **tắt tùy chọn “Force SSL” trong WooCommerce**, bạn làm theo **đúng 3 bước sau**:

---

# ✅ **Cách tắt “Force SSL” trong WooCommerce**

### **Bước 1: Vào WooCommerce Settings**

Trong WordPress Dashboard:

**WooCommerce → Settings**

---

### **Bước 2: Vào tab Advanced**

Chọn tab:

**Advanced → Page setup**

Tại phần này, WooCommerce *cũ* thường có option:

* **Force secure checkout**
* **Force HTTP when leaving the checkout**

Tuy nhiên từ WooCommerce 3.4 trở đi (version mới), mục này đã **bị ẩn** và không còn hiển thị nữa.

---

# ❗ Nếu bạn **không thấy** tùy chọn “Force SSL”

Lý do: WooCommerce đã **loại bỏ** tùy chọn này, mặc định dùng URL HTTPS nếu site được cài trên HTTPS.

Bạn vẫn có thể tắt bằng cách:

---

# 🛠 **Cách 1: Tắt Force SSL bằng wp-config.php**

Mở file:

```
/wp-config.php
```

Thêm dòng:

```php
define('FORCE_SSL_ADMIN', false);
```

---

# 🛠 **Cách 2: Tắt Force SSL bằng nginx/apache**

Nếu đang chạy trên localhost (WAMP/XAMPP) thường WooCommerce hiểu là HTTP nên không bắt SSL.
Nhưng nếu nó vẫn ép HTTPS, hãy chỉnh:

### Apache (WAMP):

Mở file:

```
/wamp64/bin/apache/apacheX.X/conf/extra/httpd-vhosts.conf
```

Đảm bảo bạn **không** có redirect:

```
RewriteEngine On
RewriteCond %{HTTPS} !=on
RewriteRule ^(.*)$ https://%{HTTP_HOST}/$1 [R=301,L]
```

Nếu có, hãy **comment lại**:

```
# RewriteEngine On
# RewriteCond %{HTTPS} !=on
# RewriteRule ^(.*)$ https://%{HTTP_HOST}/$1 [R=301,L]
```

---

# 🛠 **Cách 3: Tắt SSL trong WordPress Settings**

Đi đến:

**Settings → General**

Thay đổi:

* **WordPress Address (URL)** = `http://localhost/...`
* **Site Address (URL)** = `http://localhost/...`

Nếu để dạng HTTPS, WooCommerce sẽ tự ép SSL.

---

# 🛠 **Cách 4: Dùng plugin Really Simple SSL (ngược lại)**

Nếu trước đó bạn cài plugin SSL, hãy **tắt hoặc gỡ**:

* *Really Simple SSL*
* *WP Force SSL*

Chúng gây ra ép buộc HTTPS, không phải do WooCommerce.

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
   `C:\wamp64\www\woocommerce-local`  -> thay thế woocommerce-local bằng thư mục của các em
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

* Type: **OAuth 1.0**
* Signature method: HMAC-SHA1
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
| **401 Unauthorized** | Không đúng key/secret     | Không dùng Basic Auth, vui lòng sử dụng OAuth 1.0                        |
| **SSL required**     | WooCommerce yêu cầu HTTPS | Tắt tùy chọn "Force SSL" trong WooCommerce |


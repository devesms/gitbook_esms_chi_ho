---
description: >-
  Hàm cho phép bạn đăng nhập vào API chi hộ. Khi muốn gửi API chi hộ , bạn cần
  phải dùng hàm đăng nhập này  để lấy được token thì mới có thể sử dụng các hàm
  khác được.
---

# Hàm đăng nhập tài khỏan

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> \{{TEST\_URL\}}/api/v1/authentication

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

{% code overflow="wrap" %}
```json
curl --location 'http://sb-disbursement.esms.center/api/v1/authentication' \
--header 'accept: */*' \
--header 'Content-Type: application/json' \
--data-raw '{
  "username": "{{email}}",
  "password": "{{password}}"
}'
```
{% endcode %}

* **Cấu trúc body của request:**

<table><thead><tr><th width="152">Tham số</th><th width="229">Kiểu dữ liệu</th><th width="137" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>username</td><td>string</td><td>true</td><td>email của tài khoản.</td></tr><tr><td>password</td><td>string</td><td>true</td><td>password của tài khoản.</td></tr></tbody></table>

***

* **Response:**

```json
{
    "data": {
        "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjI2IiwiZW1haWwiOiIxMjZAZ21haWwuY29tIiwiZXhwIjoxNzI0Mzk5OTI5fQ.VarhBs8XOJPrEkHpaQsf_WTWHzi3YdR6lXZtizatYjQ",
        "isExpired": false,
        "expiredAt": "2024-08-23T07:58:49.6333601Z"
    },
    "success": true,
    "message": "Success"
}
```

* **Cấu trúc body của response:**

<table><thead><tr><th width="195">Thuộc tính</th><th>Mô tả</th></tr></thead><tbody><tr><td>data</td><td>Mã trả về.</td></tr><tr><td>success</td><td>ID của tin nhắn mới được tạo ra trên hệ thống eSMS. Dùng ID này để query lấy trạng thái tin nhắn.</td></tr><tr><td>message</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi/) **.**
* _<mark style="color:yellow;">**Lấy code mẫu của các ngôn ngữ ở link**</mark>_<mark style="color:yellow;">:</mark> [**Link code mẫu .**](https://samplefordevelopers.esms.vn/#2d996c73-a5c2-45ca-973e-d18aabb960c7)

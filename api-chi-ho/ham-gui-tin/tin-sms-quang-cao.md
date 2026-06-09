---
description: >-
  Hàm này dùng để kích hoạt tài khỏan vừa mới đăng ký, vừa có thể gán quyền cho
  tài khỏan
---

# Hàm kích hoạt tài khoản

## **HTTP request**&#x20;

\
<mark style="color:yellow;">**`POST`**</mark> \{{TEST\_URL\}}/api/v1/admin/active-account

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location --globoff '{{SB_URL}}/api/v1/admin/active-account' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {{token}}' \
--data-raw '{
    "email": "129@gmail.com",
    "roles": []
}'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="170">Tham số</th><th width="141">Kiểu dữ liệu</th><th width="136" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>token</td><td>string</td><td>true</td><td>Bạn sẽ được cung cấp khi sử dụng hàm đăng nhập của tài khỏan quyền admin.</td></tr><tr><td>email</td><td>string</td><td>true</td><td>email của tài khoản.</td></tr><tr><td>roles</td><td>string</td><td>true</td><td>Quyền được quy định bởi eSMS</td></tr></tbody></table>

***

* **Response:**

```json
{
    "success": true,
    "message": "Success"
}
```

* **Cấu trúc body của response:**

<table><thead><tr><th width="179">Thuộc tính</th><th>Mô tả</th></tr></thead><tbody><tr><td>success</td><td>true: thành công<br>false: thất bại</td></tr><tr><td>message</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr></tbody></table>


# Hàm đăng ký tài khoản



## HTTP request

<mark style="color:yellow;">**`POST`**</mark> \{{TEST\_URL\}}/api/v1/authentication/register

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location --globoff '{{SB_URL}}/api/v1/authentication/register' \
--header 'Content-Type: application/json' \
--data '{
    "email": "{{email}}",
    "password": "{{password}}",
    "displayName": "{{displayName}}",
    "phoneNumber": "{{phoneNumber}}"
}'
```

* **Cấu trúc body của request:**&#x20;

<table><thead><tr><th width="167">Tham số</th><th width="136">Kiểu dữ liệu</th><th width="134" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>email</td><td>string</td><td>true</td><td>email đăng ký.</td></tr><tr><td>password</td><td>string</td><td>true</td><td>password đăng ký.</td></tr><tr><td>displayName</td><td>string</td><td>true</td><td>Tên đăng ký.</td></tr><tr><td>phoneNumber</td><td>string</td><td>true</td><td>Số điện thoại đăng ký.</td></tr></tbody></table>



***

* **Response:**

```
{
    "data": {
        "id": 28,
        "email": "129@gmail.com",
        "phoneNumber": "0335690164",
        "displayName": "test",
        "createDate": "2024-08-22T13:49:43.7392869+07:00"
    },
    "success": true,
    "message": "Success"
}
```



* **Cấu trúc body của response:**

| Thuộc tính | Mô tả                                                                                                                                                          |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| data       | <p>id : Mã id tài khỏan<br>email: email đăng ký.</p><p>phoneNumber : Số điện thoại đăng ký.</p><p>displayName : Tên đăng ký.<br>createDate : Thời gian tạo</p> |
| success    | <p>true: thành công<br>false: thất bại</p>                                                                                                                     |
| message    | Thông tin lỗi trả về (nếu có lỗi).                                                                                                                             |


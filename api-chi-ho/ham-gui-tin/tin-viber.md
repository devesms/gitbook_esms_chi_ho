---
description: Tài khỏan phải được active mới sử dụng hàm này.
---

# Hàm gen API token



## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> \{{SB\_URL\}}/api/v1/user/generate-api-token



curl --location --globoff --request POST '\{{SB\_URL\}}/api/v1/user/generate-api-token'\
\--header 'accept: _/_'\
\--header 'Authorization: Bearer \{{token\}}'

* **Cấu trúc body của request:**

<table><thead><tr><th width="175">Tham số</th><th width="148">Kiểu dữ liệu</th><th width="143" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>token</td><td>string</td><td>true</td><td>Token được lấy từ <a href="tin-nhan-zalo.md">hàm đăng nhập tài khoản</a></td></tr></tbody></table>



***

* **Response:**

```json
{
    "data": {
        "userId": 25,
        "scopes": null,
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyZGF0YSI6IntcIlVzZXJJZFwiOjI1LFwiU2NvcGVzXCI6bnVsbCxcIlRva2VuXCI6bnVsbCxcIkNsaWVudFNlY3JldFwiOm51bGx9In0.gzuaY5sYB9LrCgN8JhlYTRNdlFLjOJbhgkb_qwGwGUs"
    },
    "success": true,
    "message": "Success"
}
```



* **Cấu trúc body của response:**

| Thuộc tính   | Mô tả                              |
| ------------ | ---------------------------------- |
| data         | Mã trả về.                         |
| SMSID        | ID tin nhắn do esms trả về.        |
| ErrorMessage | Thông tin lỗi trả về (nếu có lỗi). |

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi/) **.**
* _<mark style="color:yellow;">**Lấy code mẫu các ngôn ngữ trên Postman:**</mark>_ [**Link code mẫu**](https://samplefordevelopers.esms.vn/#9a4ce369-8f02-43cb-9693-f2e9ab827af3)**.**

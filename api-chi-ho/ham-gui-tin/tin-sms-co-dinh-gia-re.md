# Hàm whitelist IP

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> \{{URL\}}/api/v2/admin/whitelist-ip



{% hint style="info" %}
URL

\+ Sanbox: http://sb-disbursement.esms.center

\+ Production: [https://api.vihatsoftware.com](https://api.vihatsoftware.com)
{% endhint %}

<br>

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```json
curl --location ' {{URL}}/api/v2/admin/whitelist-ip' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer  {{token}}' \
--data-raw '{
  "email": "test@gmail.com",
  "addIps": ["171.244.236.86"],
  "remIps":[]
}'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="145">Tham số</th><th width="121">Kiểu dữ liệu</th><th width="147" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>token</td><td>string</td><td>true</td><td>ApiKey eSMS cung cấp.</td></tr><tr><td>email</td><td>string</td><td>true</td><td>Email tài khỏan.</td></tr><tr><td>addIps</td><td>string</td><td>true</td><td>Ip thêm vào danh sách whitelist.</td></tr><tr><td>remIps</td><td>string</td><td>true</td><td>Ip xóa khỏi danh sách whitelist.</td></tr></tbody></table>

***

* **Response:**

{% tabs %}
{% tab title="100" %}
```json
{
    "CodeResult": "100",
    "CountRegenerate": 0,
    "SMSID": "d8e0f1f0702544b2acb456ca9ccfd111250"
}
```

**Request hợp lệ.**
{% endtab %}

{% tab title="101" %}
```json
{
    "CodeResult": "101",
    "CountRegenerate": 0,
    "ErrorMessage": "Authorize Failed"
}
```

**Sai thông tin ApiKey/SecretKey.**
{% endtab %}

{% tab title="99" %}
```
{
  "error": "Invalid request"
}
```

**Kiểm tra lại thông tin kết nối hoặc liên hệ bộ phận chăm sóc khách hàng để được hỗ trợ khi gặp lỗi này.**
{% endtab %}
{% endtabs %}

* **Cấu trúc body của response:**

<table><thead><tr><th width="176">Thuộc tính</th><th width="178">Kiểu dữ liệu</th><th>Mô tả</th></tr></thead><tbody><tr><td>CodeResult</td><td>string</td><td>Mã trả về.</td></tr><tr><td>SMSID</td><td>string</td><td>ID của tin nhắn mới được tạo ra trên hệ thống eSMS. Dùng ID này để query lấy trạng thái tin nhắn.</td></tr><tr><td>ErrorMessage</td><td>string</td><td>Thông tin lỗi trả về (nếu có lỗi).</td></tr></tbody></table>

* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [**Mã lỗi**](../bang-ma-loi/) **.**
* _<mark style="color:yellow;">**Lấy code mẫu của các ngôn ngữ ở link:**</mark>_ [**Link code mẫu.**](https://samplefordevelopers.esms.vn/#562c21f1-e073-4352-8a24-eac62657953b)

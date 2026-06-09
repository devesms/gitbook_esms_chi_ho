---
description: >-
  Hàm kiểm tra này giúp người dùng có thể kiểm tra trước kết quả chi hộ thông
  qua số điện thoại.
---

# Hàm kiểm tra thông tin chi hộ

## HTTP request

<mark style="color:yellow;">**`POST`**</mark>[ ](http://api.omitopup.com/api/login)\{{URL\}}/api/v2/disbursement/create

{% hint style="info" %}
URL

\+ Sanbox: http://sb-disbursement.esms.center

\+ Production: [https://api.vihatsoftware.com](https://api.vihatsoftware.com)
{% endhint %}

* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```
curl --location --globoff '{{URL}}/api/v2/disbursement/verify' \
--header 'token: {{token}}' \
--header 'Content-Type: application/json' \
--data '{
    "disbursementData":"{{disbursementData}}",
    "disbursementMethod":"{{disbursementMethod}}",
    "channel":{{channel}},
    "signature":"{{signature}}"
}'
```

**Cấu trúc body của request:**

<table><thead><tr><th width="208">Thuộc tính</th><th width="126">Kiểu dữ liệu</th><th width="134" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>token</td><td>String</td><td>true</td><td>token lấy được ở hàm đăng nhập.</td></tr><tr><td>disbursementMethod</td><td>Int</td><td>true</td><td>Hình thức chi hộ<br>1. Nạp vào ví điện tử</td></tr><tr><td>channel</td><td>Int</td><td>true</td><td><p>Kênh chi hộ</p><p>1: MoMo</p><p>2: ZaloPay</p><p></p></td></tr><tr><td>disbursementData</td><td>String</td><td>true</td><td><p>Thông tin chi hộ. Tùy theo kênh chi hộ sẽ có format khác nhau<br>1: Nạp vào ví điện tử</p><p>disbursementData=base64({</p><p>    "phone" : "0335690164"</p><p>})</p></td></tr><tr><td>signature</td><td>String</td><td>true</td><td><p>Chữ ký điện tử được tạo từ secretKey theo format bên dưới</p><p>HmacSHA256(“channel_disbursementData_disbursementMethod”)</p></td></tr></tbody></table>



* **Response:**

```json

{
    "data": {
        "channel": 1,
        "resultCode": "4001",
        "resultMessage": "Giao dịch bị từ chối do tài khoản người dùng đang bị hạn chế."
    },
    "code": 0,
    "message": "Success"
}

```



* **Cấu trúc body của response:**

<table><thead><tr><th width="178">Thuộc tính</th><th>Mô tả</th></tr></thead><tbody><tr><td>data</td><td><p></p><ul><li>resultCode: Mã lỗi từ kênh chi hộ trả về.</li><li>resultMessage: Thông tin lỗi từ kênh chi hộ.</li><li>channelId : Kênh chi hộ.</li></ul><p></p></td></tr><tr><td>code</td><td><p>Mã lỗi eSMS trả về</p><p>0 : Thành công.</p><p></p></td></tr><tr><td>message</td><td>Thông báo thành công hay thất bại của giao dịch.</td></tr></tbody></table>



* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [<mark style="color:green;">**esms**</mark>](bang-ma-loi/ma-loi-cua-esms.md) **,**  [<mark style="color:red;">**momo**</mark>](bang-ma-loi/ma-loi-cua-momo.md)**,** [**zalo**](bang-ma-loi/ma-loi-cua-zalo.md) **.**


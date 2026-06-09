---
description: >-
  Hàm cho phép bạn xem trạng thái giao dịch theo orderId, mỗi orderId chỉ kiểm
  tra được cho một transactionId.
---

# Hàm lấy trạng thái chi hộ theo orderId

## HTTP request

\
<mark style="color:yellow;">**`POST`**</mark> \{{URL\}}/api/v2/disbursement/query-trx



{% hint style="info" %}
URL

\+ Sanbox: http://sb-disbursement.esms.center

\+ Production: [https://api.vihatsoftware.com](https://api.vihatsoftware.com)
{% endhint %}



* **Content Type:** <mark style="color:orange;">application/json</mark>
* **Response Type:** <mark style="color:orange;">application/json</mark>

```
curl --location --globoff '{{URL}}/api/v2/disbursement/query-trx' \
--header 'token: {{token}}' \
--header 'Content-Type: application/json' \
--data '{
    "orderId":"{{orderId}}",
    "signature":"{{signature}}"
}'
}'
```

* **Cấu trúc body của request:**

<table><thead><tr><th width="139">Tham số</th><th width="131">Kiểu dữ liệu</th><th width="149" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>token</td><td>string</td><td>true</td><td>Bạn sẽ được cung cấp khi sử dụng hàm gen API token.</td></tr><tr><td>orderId</td><td>string</td><td>true</td><td>orderId của khách hàng truyền vào khi thực hiện giao dịch chi hộ.</td></tr><tr><td>signature</td><td>string</td><td>true</td><td><p>Chữ ký điện tử được tạo từ secretKey theo format bên dưới</p><p>HmacSHA256(“orderId”)</p></td></tr></tbody></table>



***

* **Response:**

```json
{
    "data": {
        "resultCode": "0",
        "message": "Thành công.",
        "transactionId": "141571a8ab5841e9bf692068dc528c2b",
        "channelId": 1,
        "method": 1,
        "amount": 110000,
        "status": 3,
        "timestamp": 1724229987,
        "orderId": "mã-1724229984830",
        "callbackUrl": "https://en9v99k4uwp0k.x.pipedream.net/"
    },
    "code": 0,
    "message": "Success"
}
```

* **Cấu trúc body của response:**

<table><thead><tr><th width="201">Thuộc tính</th><th>Mô tả</th></tr></thead><tbody><tr><td>data</td><td><ul><li>resultCode: Kết quả giao dịch chi hộ</li><li>message: Thông báo thành công hay thất bại của giao dịch</li><li>orderId : Giá trị orderId.</li><li>amount : Số tiền chi hộ.</li><li>transactionId: Mã giao dịch eSMS trả về.</li><li>channelId : Kênh chi hộ.</li><li>method : Hình thức chi hộ.</li><li>timestamp : Thời gian hòan thành giao dịch</li><li>status : Trạng thái giao dịch (0: Trạng thái ban đầu, 1:Đang chờ , 2: Đang xử lý , 3:  Thành công, -1: Thất bại )</li><li>callbackUrl: Link callback của khách hàng</li></ul></td></tr><tr><td>code</td><td>Mã lỗi trả về:<br>    0: thành công .</td></tr><tr><td>message</td><td>Thông báo kết quả lấy trạng thái chi hộ</td></tr></tbody></table>



* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [<mark style="color:green;">**esms**</mark>](../bang-ma-loi/ma-loi-cua-esms.md) **,**  [<mark style="color:red;">**momo**</mark>](../bang-ma-loi/ma-loi-cua-momo.md)**,** [**zalo**](../bang-ma-loi/ma-loi-cua-zalo.md)


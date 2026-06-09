# Hàm chi hộ

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
curl --location --globoff '{{URL}}/api/v2/disbursement/create' \
--header 'token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyZGF0YSI6IntcIlVzZXJJZFwiOjEsXCJTY29wZXNcIjpudWxsLFwiVG9rZW5cIjpudWxsfSJ9.vPtV3VpWN9fzwCkYsp2B_gcLWgJmHH37A0SYzMyE3eA' \
--header 'Content-Type: application/json' \
--data '{
    "amount": {{amount}}, 
    "disbursementMethod": {{disbursementMethod}}, 
    "channel": {{channel}}, 
    "disbursementData": "{{disbursementData}}", 
    "orderId": {{orderId}}, 
    "callbackUrl": {{callbackUrl}}, 
    "description": {{description}}, 
    "signature": {{signature}} 
}'
```

**Cấu trúc body của request:**

<table><thead><tr><th width="208">Thuộc tính</th><th width="126">Kiểu dữ liệu</th><th width="134" data-type="checkbox">Tính bắt buộc</th><th>Mô tả</th></tr></thead><tbody><tr><td>token</td><td>String</td><td>true</td><td>token lấy được ở hàm đăng nhập.</td></tr><tr><td>amount</td><td>Int</td><td>true</td><td><p>Số tiền nạp vào ví.</p><ul><li>Nhỏ nhất 10.000</li><li>Là bội của 1000</li></ul></td></tr><tr><td>disbursementMethod</td><td>Int</td><td>true</td><td>Hình thức chi hộ<br>1. Nạp vào ví điện tử</td></tr><tr><td>channel</td><td>Int</td><td>true</td><td><p>Kênh chi hộ</p><p>1: MoMo</p><p>2: ZaloPay</p><p></p></td></tr><tr><td>disbursementData</td><td>String</td><td>true</td><td><p>Thông tin chi hộ. Tùy theo kênh chi hộ sẽ có format khác nhau<br>1: Nạp vào ví điện tử</p><p>disbursementData=base64({</p><p>    "phone" : "0335690164"</p><p>})</p></td></tr><tr><td>orderId</td><td>String (50) </td><td>true</td><td>Mã giao dịch ở phía khách hàng.</td></tr><tr><td>description</td><td>String (255)</td><td>true</td><td>Nội dung chi hộ - chuyển khỏan</td></tr><tr><td>signature</td><td>String</td><td>true</td><td><p>Chữ ký điện tử được tạo từ secretKey theo format bên dưới</p><p>HmacSHA256(“amount_channel_description_disbursementData_disbursementMethod_orderId”)</p></td></tr><tr><td>callbackurl</td><td>String</td><td>false</td><td>eSMS sẽ trả trạng thái của giao dịch vào link callback của khách hàng. <br>Callback trả về mẫu: <a href="callback.md"><em>Callback</em></a><br></td></tr></tbody></table>



* **Response:**

```json
{
    "data": {
        "transactionId": "d675a4d9c6e64190be53737544fd98de",
        "channelId": 1,
        "method": 1,
        "amount": 10000000,
        "status": 0,
        "timestamp": 1724305723,
        "orderId": "mã-1724305722484",
        "callbackUrl": "https://webhook.site/6aacd916-2970-4ede-8588-9eca20fcc201"
    },
    "code": 0,
    "message": "Success"
}
```



* **Cấu trúc body của response:**

<table><thead><tr><th width="178">Thuộc tính</th><th>Mô tả</th></tr></thead><tbody><tr><td>data</td><td><p></p><ul><li>resultCode: Mã lỗi từ kênh chi hộ trả về.</li><li>message: Thông tin lỗi từ kênh chi hộ</li><li>orderId : Giá trị orderId.</li><li>amount : Số tiền chi hộ.</li><li>transactionId: Mã giao dịch eSMS trả về.</li><li>channelId : Kênh chi hộ.</li><li>method : Hình thức chi hộ.</li><li>timestamp : Thời gian hòan thành giao dịch</li><li>status : Trạng thái giao dịch (0: Trạng thái ban đầu, 1:Đang chờ , 2: Đang xử lý , 3:  Thành công, -1: Thất bại )</li><li>callbackUrl : Link callback khách hàng truyền vào</li></ul><p></p></td></tr><tr><td>code</td><td><p>Mã lỗi eSMS trả về</p><p>0 : Thành công.</p><p></p></td></tr><tr><td>message</td><td>Thông báo thành công hay thất bại của giao dịch.</td></tr></tbody></table>



* _<mark style="color:yellow;">**Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [<mark style="color:green;">**esms**</mark>](bang-ma-loi/ma-loi-cua-esms.md) **,**  [<mark style="color:red;">**momo**</mark>](bang-ma-loi/ma-loi-cua-momo.md)**,** [**zalo**](bang-ma-loi/ma-loi-cua-zalo.md) **.**


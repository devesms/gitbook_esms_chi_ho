---
description: >-
  eSMS sẽ trả trạng thái của giao dịch vào link callback của khách hàng. Dữ liệu
  mẫu:
---

# Callback

```
{
  "orderId": "mã-1724290351675",
  "status": -1,
  "timestamp": 1724290351,
  "transactionId": "51461342aa7449c4afb8e14e33536c05",
  "channelId": 1,
  "method": 1,
  "amount": 10000000,
  "resultCode": "1007",
  "message": "Giao dịch bị từ chối vì tài khoản không tồn tại hoặc đang ở trạng thái ngưng hoạt động."
}
```



**\*Ý nghĩa:**

* resultCode: Mã lỗi từ kênh chi hộ trả về.
* message: Thông tin lỗi từ kênh chi hộ
* orderId : Giá trị orderId.
* amount : Số tiền chi hộ.
* transactionId: Mã giao dịch eSMS trả về.
* channelId : Kênh chi hộ.
* method : Hình thức chi hộ.
* timestamp : Thời gian hòan thành giao dịch
* status : Trạng thái giao dịch (0: Trạng thái ban đầu, 1:Đang chờ , 2: Đang xử lý , 3:  Thành công, -1: Thất bại )

_<mark style="color:yellow;">**\*Thông tin chi tiết mã lỗi xem ở bảng:**</mark>_ [<mark style="color:green;">**esms**</mark>](bang-ma-loi/ma-loi-cua-esms.md) **,**  [<mark style="color:red;">**momo**</mark>](bang-ma-loi/ma-loi-cua-momo.md)**,** [**zalo**](bang-ma-loi/ma-loi-cua-zalo.md) **.**

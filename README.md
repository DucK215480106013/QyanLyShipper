# QUẢN LÝ SHIPPER

## Thông tin sinh viên:
- Họ tên: Đỗ Đình Đức
- K57kmt
- Mssv: k215480106013
## Thông tin bài toán:
Bài toán này thiết kế một hệ thống quản lý shipper với khả năng theo dõi đơn hàng, vận chuyển, và đánh giá shipper, đồng thời có các cơ chế bảo vệ và xử lý tình huống khi shipper có vấn đề về chất lượng dịch vụ.
Quản lý người dùng
### chức năng: 
- Cập nhật thông tin shipper, thêm, sửa, xoá thông tin của shippers.
- Tạo stored procedure để quản lý shipper.
- Cập nhật mật khẩu của shipper để kích hoạt trigger và kiểm tra chức năng khóa tài khoản khi bị đánh giá 1 sao quá 3 lần.
- Đánh giá shppers.
### Báo cáo:
- Cung cấp các cơ chế để kiểm tra và quản lý chất lượng dịch vụ của shipper thông qua hệ thống đánh giá và cảnh báo.
-  Kiểm tra và xác minh hoạt động của hệ thống thông qua các dữ liệu mẫu và tình huống cụ thể.

  

## Các bảng của hệ thống.


![image](https://github.com/DucK215480106013/QyanLyShipper/assets/173238117/19050164-2a1a-4d52-86c5-fed281d843bd)

![image](https://github.com/DucK215480106013/QyanLyShipper/assets/173238117/67054a2d-f2af-4500-8435-a831378c387e)


 
 

**OrderID**

  •	Kiểu dữ liệu: INT

  •	Ràng buộc: PRIMARY KEY

  •	Mô tả: Đây là khóa chính của bảng, đại diện cho ID duy nhất của mỗi đơn hàng.
  
** ShipperID**
 
  •	Kiểu dữ liệu: INT

  •	Ràng buộc: FOREIGN KEY (REFERENCES Shippers(ShipperID))

  •	Mô tả: Khóa ngoại liên kết với bảng Shippers, đại diện cho shipper thực hiện đơn hàng này.
  
**OrderDate**

  •	Kiểu dữ liệu: DATETIME

  •	Mô tả: Ngày đặt hàng của đơn hàng.
  
**DeliveryDate**

  •	Kiểu dữ liệu: DATETIME

  •	Mô tả: Ngày dự kiến giao hàng của đơn hàng.
  
**Status**

  •	Kiểu dữ liệu: NVARCHAR(50)

  •	Mô tả: Trạng thái của đơn hàng (ví dụ: đã giao hàng, đang vận chuyển, chưa giao hàng).

  

**Bảng Shipments**

![image](https://github.com/DucK215480106013/QyanLyShipper/assets/173238117/c52168f5-5f6b-4285-928a-498b4284f85c)

![image](https://github.com/DucK215480106013/QyanLyShipper/assets/173238117/a730662a-c880-4cd2-b9bd-41da019782e4)


 
.  
 **Khóa chính: ShipmentID**
 
  •	Lý do: ShipmentID là giá trị duy nhất xác định từng vận chuyển, giúp theo dõi từng lô hàng riêng lẻ.

** Khóa ngoại: OrderID**
 
  •	Lý do: OrderID tham chiếu đến OrderID trong bảng Orders, đảm bảo mỗi vận chuyển liên kết với một đơn hàng cụ thể.



**•	ShipmentID**

  o	Kiểu dữ liệu: INT

  o	Ràng buộc: PRIMARY KEY
 
  o	Mô tả: Đây là khóa chính của bảng, đại diện cho ID duy nhất của mỗi lô hàng vận chuyển.



**•	OrderID**

  o	Kiểu dữ liệu: INT

  o	Ràng buộc: FOREIGN KEY (REFERENCES Orders(OrderID))

  o	Mô tả: Khóa ngoại liên kết với bảng Orders, đại diện cho đơn hàng mà lô hàng này được vận chuyển.



**•	ShipperID**

  o	Kiểu dữ liệu: INT

  o	Ràng buộc: FOREIGN KEY (REFERENCES Shippers(ShipperID))

  o	Mô tả: Khóa ngoại liên kết với bảng Shippers, đại diện cho shipper thực hiện vận chuyển lô hàng này.



**•	Rating**

  o	Kiểu dữ liệu: INT

  o	Mô tả: Đánh giá của khách hàng về lô hàng vận chuyển (có thể là 1, 2, 3 sao).



**•	ShipmentDate**

  o	Kiểu dữ liệu: DATETIME

  o	Mô tả: Ngày vận chuyển của lô hàng.



**•	Destination**

  o	Kiểu dữ liệu: NVARCHAR(255)

  o	Mô tả: Địa điểm đến của lô hàng.



**•	Weight**

  o	Kiểu dữ liệu: DECIMAL(10, 2)

  o	Mô tả: Trọng lượng của lô hàng.



**•	Cost**

  o	Kiểu dữ liệu: DECIMAL(10, 2)

  o	Mô tả: Chi phí vận chuyển của lô hàng.

  
  
**Bảng ShipperRatings**

![image](https://github.com/DucK215480106013/QyanLyShipper/assets/173238117/9281f2bf-b0c0-44e3-afe9-870e4924d012)

![image](https://github.com/DucK215480106013/QyanLyShipper/assets/173238117/2b6feaa8-3a41-4a4e-9bc1-63d2dae50c66)




 
 
**•	ShipperRatingID**

o	Kiểu dữ liệu: INT

o	Ràng buộc: PRIMARY KEY

o	Mô tả: Đây là khóa chính của bảng, đại diện cho ID duy nhất của mỗi bản ghi đánh giá shipper.



**•	ShipperID**

o	Kiểu dữ liệu: INT

o	Ràng buộc: FOREIGN KEY (REFERENCES Shippers(ShipperID))

o	Mô tả: Khóa ngoại liên kết với bảng Shippers, đại diện cho shipper bị đánh giá.



**•	OrderID**
o	Kiểu dữ liệu: INT

o	Ràng buộc: FOREIGN KEY (REFERENCES Orders(OrderID))

o	Mô tả: Khóa ngoại liên kết với bảng Orders, đại diện cho đơn hàng liên quan đến đánh giá.



**•	Rating**

o	Kiểu dữ liệu: INT

o	Mô tả: Đánh giá của shipper (có thể là 1, 2, 3 sao).



**•	Description**

o	Kiểu dữ liệu: NVARCHAR(255)

o	Mô tả: Mô tả chi tiết về lý do shipper bị đánh giá.

**Bảng Shippers**


![image](https://github.com/DucK215480106013/QyanLyShipper/assets/173238117/cb9d21a6-5a12-4aaa-8c72-a9fb140e49c2)


![image](https://github.com/DucK215480106013/QyanLyShipper/assets/173238117/a2cc5c9c-47fb-4fe1-b2ee-59152a66f09c)


 
 

**Khóa chính: ShipperID**

  •	Lý do: ShipperID là giá trị duy nhất xác định từng shipper, đảm bảo mỗi shipper có một mã định danh riêng biệt.
  

**ShipperID**

 •	Kiểu dữ liệu: INT

 •	Ràng buộc: PRIMARY KEY

 •	Mô tả: Đây là khóa chính của bảng, đại diện cho ID duy nhất của mỗi shipper.
TenShipper

 •	Kiểu dữ liệu: NVARCHAR(100)
 
 •	Mô tả: Là tên của shipper, có độ dài tối đa 100 ký tự.

 
**Tendinhdanh**

 •	Kiểu dữ liệu: NVARCHAR(100)
 
 •	Mô tả: Tên đăng nhập của shipper, có độ dài tối đa 100 ký tự.

 
**Phone**

 •	Kiểu dữ liệu: NVARCHAR(20)
 
 •	Mô tả: Số điện thoại liên lạc của shipper, có độ dài tối đa 20 ký tự.

 
**Email**

 •	Kiểu dữ liệu: NVARCHAR(100)
 
 •	Mô tả: Địa chỉ email của shipper, có độ dài tối đa 100 ký tự.

 
**Password**

 •	Kiểu dữ liệu: NVARCHAR(50)
 
 •	Mô tả: Mật khẩu của shipper để đăng nhập vào hệ thống, có độ dài tối đa 50 ký tự.

 
**dangnhap**

 •	Kiểu dữ liệu: INT
 
 •	Mặc định: 0
 
 •	Mô tả: Cờ chỉ trạng thái đăng nhập của shipper (có thể sử dụng để xác định trạng thái hiện tại của shipper đang đăng nhập hay không).

 
**khoatk**

 •	Kiểu dữ liệu: BIT
 
 •	Mặc định: 0
 
 •	Mô tả: Cờ chỉ trạng thái khóa tài khoản của shipper. Được sử dụng để đánh dấu và khóa tài khoản shipper trong trường hợp xảy ra các sự cố như bị đánh giá thấp quá nhiều lần.
 


 •	Lý do: OrderID tham chiếu đến OrderID trong bảng Orders, giúp xác định đơn hàng nào liên quan đến đánh giá này.
 
**Tạo SP cho bài toán**


![image](https://github.com/DucK215480106013/QyanLyShipper/assets/173238117/73ef4c84-420a-494c-87ea-fd900e88a17e)

 
**Stored procedure Shipper_Manage giúp tự động hóa các tác vụ quản lý dữ liệu cho bảng Shippers, bao gồm:**

 •	INSERT: Thêm thông tin mới cho một shipper.

 •	DELETE: Xóa thông tin của một shipper dựa trên ShipperID.

 •	UPDATE: Cập nhật thông tin của một shipper dựa trên ShipperID.

 •	SELECT: Lấy danh sách tất cả các shipper, kèm theo một số thông tin cơ bản.

**Cụ thể, stored procedure Shipper_Manage trong bài toán này có tác dụng:**

 •	Thêm shipper mới: Thực hiện khi @Action là 'INSERT'.

 •	Xóa shipper: Thực hiện khi @Action là 'DELETE'.

 •	Cập nhật thông tin shipper: Thực hiện khi @Action là 'UPDATE'.

 •	Lấy danh sách shipper: Thực hiện khi @Action là 'SELECT'.

 ![image](https://github.com/DucK215480106013/QyanLyShipper/assets/173238117/6bbd3d3d-d17e-4b7f-a388-5d28e45ab1da)

 




**Tạo trigger cho bài: **

![image](https://github.com/DucK215480106013/QyanLyShipper/assets/173238117/a2212a5f-a6f4-4adb-91a3-b8a76d23cde2)

 
**Trigger này được thiết lập để kích hoạt sau khi có hành động cập nhật (AFTER UPDATE) trên bảng Shippers. Nó kiểm tra các điều kiện sau khi thông tin của shipper được cập nhật:**

 •	Kiểm tra thay đổi mật khẩu: Nếu mật khẩu được cập nhật, trigger kiểm tra xem tài khoản có bị khóa hay không.
 
  o	Nếu tài khoản bị khóa (khoatk = 1), việc cập nhật sẽ bị ngăn chặn và hiển thị thông báo lỗi.
  
  o	Nếu tài khoản không bị khóa, trạng thái đăng nhập (dangnhap) sẽ được đặt lại về 0 để yêu cầu đăng nhập lại.
  
  o	Quản Lý Trạng Thái Tài Khoản Dựa Trên Đánh Giá:

  
**Trigger kiểm tra số lần shipper bị đánh giá 1 sao. Nếu số lần đánh giá 1 sao từ bảng Shipments đạt hoặc vượt quá 3 lần, trigger thực hiện các hành động sau:**

 •	Khóa tài khoản shipper: Cập nhật trạng thái khoatk của shipper thành 1.

 •	Ghi lại thông tin cảnh báo: Thêm một bản ghi vào bảng ShipperRatings với mô tả cảnh báo, giúp theo dõi và quản lý các shipper có vấn đề về chất lượng dịch vụ.**Thông Báo và Ngăn Chặn Hành Động Không Hợp Lệ**:

 
**Trigger sử dụng RAISERROR để thông báo khi có các hành động không hợp lệ:**

 •	Thông báo khi shipper cố gắng cập nhật mật khẩu trong khi tài khoản đang bị khóa.

 •	Thông báo khi shipper bị khóa tài khoản do bị đánh giá 1 sao quá 3 lần.
 
![image](https://github.com/DucK215480106013/QyanLyShipper/assets/173238117/5251128c-dada-4215-bde2-9daa5f73397a)

![image](https://github.com/DucK215480106013/QyanLyShipper/assets/173238117/38d74df9-be8c-46e1-8296-998e9d64f836)



 



**Kết quả sau khi chạy trigger**

 

![image](https://github.com/DucK215480106013/QyanLyShipper/assets/173238117/8c0ee591-b690-4b0c-a184-9af87d645c8a)




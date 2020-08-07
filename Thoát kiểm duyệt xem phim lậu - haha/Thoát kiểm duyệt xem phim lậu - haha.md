## Tổng quan
Như các bác đã biết, dạo gần đây các trang phim lậu bị các nhà cung cấp mạng Việt Nam chặn triệt để. Nhưng các trang phim ấy cũng đâu có vừa, họ liền đổi tên miền, ví dụ phimmoi.net thành phimmoiz.net, cứ chặn là họ thêm cứ thêm z vào tên miền. 

Còn con dân xem phim lậu thì dùng cũng có cách dùng proxy hoặc vpn, nhưng 2 cái trên có nhược điểm là tốc độ chậm và đôi khi không an toàn. Vậy còn có cách nào khác nữa không? Xin thưa là **Có**.

Quay lại vấn đề nhà cung cấp dịch vụ Internet - Internet Service Provider (ISP) họ đã làm cách nào mà chặn được web phim. Họ đã dùng công nghệ gọi là **Phân Tích Sâu Gói Tin - Deep Packet Inspection (DPI)**, ae nào học môn **Hệ thống tìm kiếm, phát hiện và ngăn ngừa xâm nhập** chắc là biết thằng này rồi còn không thì google. 

Vậy tại sao không chặn cmn IP đi cho dễ mà lại dùng công nghệ có vẻ phức tạp trên. Chặn IP thì không ổn chút nào. Các bạn đã nghe nói đến Cloudflare chưa? Chưa thì google đi, còn đơn giản nó là thằng bảo vệ các website. Vì các website dùng thằng Cloudflare nên thường nó sẽ có chung IP, vậy lỡ chặn bằng IP thì nó chặn luôn cmn mấy website ngon lành khác sao được. Nên phải chặn bằng thằng DPI.

Chặn bằng DPI, thực ra là chặn tên miền đó. Hay đúng hơn là lọc coi gói tin nào có tên miền cấm thì trảm ngay gói tin đó, dẫn đến éo vào được web. Nên mấy làm web phim cứ liên tục đổi tên miền là vậy.

Vậy câu hỏi đặt ra, có cách nào qua mặt thằng DPI không? Tất nhiên là **Có**. Cái gì không biết thì tra google với cú pháp là: **Bypass DPI github**. Tìm hàng trên github mã nguồn mở, nên an toàn khỏi lo gì cả, nếu sợ thì tải code về build lại là xong.

## Giới thiệu vài con hàng:
### 1. [GoodbyeDPI](https://github.com/ValdikSS/GoodbyeDPI)
Hiện đang dùng thằng này, sử dụng giao diện dòng lệnh. Gọi đến API filter của windows để sửa gói tin nên khỏi bàn về tốc độ. Chạy trên windows từ win7 -> 10. Phải nói là nó ngon. Kiểm tra trên 2 thằng nhà mạng VPNT và Viettel thì như chưa hề có cuộc chia ly, vào web ầm ầm. 

Khi tải về thì có 2 mục **x86** và **x86_64**. **Windows 32bit** thì vào thư mục **x86** chạy tập tin **goodbyedpi.exe** và ngược lại. À đang dùng win 7 64bit nè chạy méo có lỗi gì. Hàng này của Nga ngố các bác à ^.^

### 2. [zapret](https://github.com/bol-van/zapret)
Hàng chạy trên linux. Hơi khó dùng, sử dụng giao diện dòng lệnh. Tài liệu tiếng Anh nó nè [https://github.com/bol-van/zapret/blob/master/docs/readme.eng.txt](https://github.com/bol-van/zapret/blob/master/docs/readme.eng.txt).

Em mất khoảng 2 ngày tìm hiểu và chạy thử trên openwrt, kết quả ngon lành cành mía ^_^. Hôm nào rảnh viết bài hướng dẫn. Cái này cũng hàng Nga nốt ^.^

### 3. [GreenTunnel](https://github.com/SadeghHayeri/GreenTunnel)
Hỗ trợ hầu hết hệ điều hành, do viết bằng JavaScript.

Chạy như 1 con proxy server. À có giao diện nhé. 

### 4. [PowerTunnel](https://github.com/krlvm/PowerTunnel)
Viết bằng Java, nên chỗ nào cài được java thì chạy chắc được ^_^. Có giao diện đồ họa khá được mắt. À nó chạy kiểu proxy server.

### 5. [DPITunnel](https://github.com/zhenyolka/DPITunnel)
Dùng cho Android. Chưa chạy thử nên không biết như thế nào.

### 6. [PowerTunnel-Android](https://github.com/krlvm/PowerTunnel-Android)
Nhìn tên là biết rồi. Chưa chạy thử nên không rõ.

## Tổng kết
Nếu gặp lỗi gì này nọ thì cứ lên github của vào thẻ Issues tìm kiếm lỗi rồi xem cách giải quyết hoặc đặt câu hỏi. Còn không chuyển sang thằng khác sài. Hết.




 
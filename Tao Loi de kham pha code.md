# vuivui.tv đã giấu link video của họ như thế nào?

## Giới thiệu
Vào một ngày đẹp trời lên xem phim Đấu la đại lục trên vuivui.tv thì thấy chất lượng phim chỉ còn 480p, muốn xem chất lượng cao hơn thì phải bỏ tí tiền ra. Lúc đó cũng nổi máu cố tìm xem thử có link HD không thì kết quả **THẤT BẠI**.

## Quá trình
Sau đây là quá trình tìm kiếm và cũng có khám phá ra một kĩ thuật mình đặt tên là: ***Tạo lỗi để khám phá code*** he he.

* Đầu tiên mở **Chrome** và **Fiddler**. Trên chrome gõ CTRL+SHIFT+N (tab ẩn danh) + bật devtool bằng F12 sau đó mới nhập link: https://www.vuivui.tv/Dau-La-Dai-Luc-film-6.html (cái này tùy ý), mục đích là trách trình duyệt lấy lại dữ liệu từ cache thay vì từ mạng.
* Lúc này trên Fiddler hiện ra danh sách các url, tìm url chứa link video.
![](https://i.imgur.com/uhg2QkW.png)
* Sau khi tìm được link video, chúng ta tiếp tục xem link video xuất phát từ đâu. 
![](https://i.imgur.com/akc4oKe.png)

	Kết quả ta được
	![](https://i.imgur.com/GBYOoWt.png)
	Nhưng nó không đúng, do lúc tìm kiếm ta chọn ở cả *Requests and responses*. Để tránh tình trạng này thì chỉ cần chọn *Responses Only* là đủ.

* Sau khi tìm theo cách trên mà không được kết quả gì thì có vẻ link video được gọi từ mã js.
* Vào devtool > tab network, chúng ta tìm xem link video kia xuất phát từ đâu. 
![](https://i.imgur.com/vDQlzHj.png)
* Thông thường ở cột Initiator sẽ hiện ra nơi gọi url mà ở đây lại không có => **Bí** *(Bắt đầu suy nghĩ các thứ)* => Có vẻ như nó phải nằm đâu đó trong 1 đoạn mã js nào đó rồi.
* Lúc này mình mới nghĩ: ***Thử tạo request lỗi xem thằng js nó có bung cái lỗi nào ra không*** rồi xử lý tiếp.
* Với ý nghĩ trên, mình vào Fiddler > tab AutoResponder.
![](https://i.imgur.com/lfKCH5I.png)
* Sau khi thêm url trên vào, chỉnh sửa lại một chút ở Rule Editor: _regex:(?inx)^https://www.*.hlsmp4.com/.*.mp4_
* Kiểm tra xem đã khớp với mẫu chưa.
![](https://i.imgur.com/5l3OPjd.png)
* Ở ô dưới cùng chọn lỗi trả về là 404 với tập tin mẫu là: *404_Plain.dat*. Cái này tùy ý có thể trả mã 502 cũng được.
![](https://i.imgur.com/I2U7RLp.png)
* Sau đó, làm lại các bước từ đầu tới giờ, nhưng ta vào lại devtool > tab console và xem lỗi có bung ra không. Bắt đầu quá trình tìm kiếm...
* May mắn là có một lỗi do thằng JW Player bung ra *MediaError*. Mở xem chi tiết lỗi này ta sẽ thấy Call stack, một dãy các hàm gọi liên tiếp nhau bắt đầu từ thằng *get-episodes...*.
![](https://i.imgur.com/M7i6bWt.png)
Call stack
![](https://i.imgur.com/kJZOLBB.png)
* Nhấp vào dòng đầu tiên dẫn ta đến một đoạn js bị làm rối mã, thôi tạm bỏ qua vậy.
![](https://i.imgur.com/Fm4d2IL.png)
* Nhấp dòng thứ 2, ồ mọi thứ đây rồi. 
![](https://i.imgur.com/nGiHA6P.png)

* Quay lại phân tích mã js đầu tiên. Ta thấy có 2 dòng lệnh eval, mà eval là dùng để thực thi code js từ dạng chuỗi. Copy đoạn code trên bỏ đi 2 thằng eval, lưu vô file, gọi thằng nodejs lên chạy thì ta được đoạn mã ở dòng 2.
Lưu vào file
![](https://i.imgur.com/rnhRY1P.png)
Kết quả sau khi chạy với nodejs
![](https://i.imgur.com/e9gsKJ5.png)

## Tóm lại
* Trước tiên tìm kiếm trong fiddler trước.
* Nếu không có quay sang tab network của devtool.
* Cuối cùng tạo lỗi để mò ra code.

### Hi vọng mọi người xem bài này thì cũng có thể may mắn tìm được thứ mình muốn với kĩ thuật này.





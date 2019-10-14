## Chống lại việc chống debug javascript trên Chrome

Trên chrome cài đặt Tampermokey extension tại [link](https://chrome.google.com/webstore/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo).<br>
![](pic/Image_1.png)<br>
Tại Tampermokey chọn ***Create a new script...***.<br>
![](pic/Image_2.png)<br>
Sao chép mã javascript [tại đây](https://github.com/NguyenKhong/my_blog/blob/master/Anti%20Anti%20debugger%20js/code.js) vào Tampermokey hoặc bạn cũng có thể google: "*Anti Anti-debugger*" nhưng bạn phải thêm dòng `// @include *`<br> 
![](pic/Image_3.png)<br>
![](pic/Image_4.png)<br>
Gõ ***CTRL+S*** để lưu lại. Ta được: <br>
![](pic/Image_5.png)<br>
#### Vậy là xong.



### **Phần 1\. Phân tích**

Dựa trên việc soi thẻ \<div class="driver-info"\> bằng tab **Computed** trong DevTools, sơ đồ Box Model hiện tại của phần tử lỗi được thể hiện như sau:

**Nguyên nhân vỡ Layout:** Khung "Thông tin tài xế" đang có margin-bottom: 0, triệt tiêu hoàn toàn khoảng cách an toàn với phần tử bên dưới. Đồng thời, padding: 12px cộng dồn vào kích thước Content khiến khối hiển thị bị phình to tràn viền, dẫn đến đè trực tiếp lên khung "Danh sách trạm".

### **Phần 2\. Triển khai**

Sử dụng **Inspect Element** (Ctrl \+ Shift \+ C) click vào khối "Thông tin tài xế" trên giao diện để định vị chính xác thẻ HTML trong DOM Tree. Tại tab **Styles**, không sửa mã nguồn gốc mà tiến hành gõ thêm các thông số CSS sau vào class .driver-info để kiểm thử:

* margin-bottom: 24px;: Tạo lực đẩy lề ngoài 24px xuống phía dưới, tách rời hoàn toàn và ép khối "Danh sách trạm" lùi xuống.  
*   
* box-sizing: border-box;: Ép trình duyệt tính toán kích thước bao gồm cả Padding và Border vào tổng chiều rộng/cao, ngăn chặn khối bị phình to bất thường.  
* 

### **Phần 3\. Kiểm thử**

Trong trường hợp đã khai báo margin-bottom: 24px nhưng khối "Danh sách trạm" vẫn bị đè và không dịch chuyển, nguyên nhân là luồng bố cục tự nhiên (Normal Document Flow) của Browser Engine đang bị vô hiệu hóa.

Cần kiểm tra ngay trong tab Styles và bỏ tick (vô hiệu hóa) các thuộc tính đang ghi đè sau:

* position: absolute; hoặc position: fixed;: Thuộc tính này nhấc bổng khối HTML lên một layer khác, khiến margin không thể tương tác vật lý với các khối xung quanh.  
*   
* float: left/right;: Làm phần tử trôi nổi và thay đổi hành vi đẩy của margin.  
  
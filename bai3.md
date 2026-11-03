**Phần 1. Phân tích**

* **Sơ đồ Box Model:** Margin (0px) -> Border (-) -> Padding (12px) -> Content (340x180px).
* 
* **Phân tích 4 lớp CSS Box Model:**
* 
* **Content:** Chứa dữ liệu hiển thị, không có khả năng tạo khoảng cách ngoài.
* 
* **Padding (12px):** Khoảng trống bên trong, làm phình to diện tích bề mặt khung.
* 
* **Border:** Đường biên ranh giới, không tạo lực đẩy vật lý.
* 
* **Margin (Lớp nút thắt):** margin-bottom = 0 khiến phần tử mất khoảng cách an toàn, tràn xuống đè lên khung "Danh sách trạm".
* 

**Phần 2. Triển khai**

1. **Định vị:** Nhấn Ctrl + Shift + C (Inspect Element) nhấp vào khung "Thông tin tài xế" để tìm thẻ <div class="driver-info">.
2. 
3. **CSS mới (thêm vào tab Styles):**
4. 

CSS

```

.driver-info {
    margin-bottom: 24px !important; /\* Tạo lực đẩy 24px để tách rời 2 khung \*/
    box-sizing: border-box;         /\* Ép Padding \& Border tính gộp vào kích thước tổng \*/
    display: flex; 
    flex-direction: column;
}

```

**Phần 3. Kiểm thử**

* **Hiện tượng:** Đã thêm margin-bottom: 24px nhưng phần tử vẫn đứng im.
* 
* **Nguyên nhân:** Thuộc tính position: absolute;, position: fixed; hoặc float; đang nhấc phần tử ra khỏi luồng bố cục tự nhiên (Normal Flow), vô hiệu hóa lực đẩy của Margin.
* 
* **Xử lý:** Bỏ tick các thuộc tính này trong tab Styles hoặc chuyển về position: static / relative;.

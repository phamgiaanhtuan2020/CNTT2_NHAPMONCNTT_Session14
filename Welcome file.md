---


---

<h1 id="phần-1-phân-tích-bài-toán-io">PHẦN 1: PHÂN TÍCH BÀI TOÁN (I/O)</h1>
<h2 id="đầu-vào-và-đầu-ra">1. Đầu vào và đầu ra</h2>
<p><strong>Đầu vào:</strong></p>
<ul>
<li>Ban Kỹ thuật: 3 người, làm code và kiểm thử API.</li>
<li>Ban Thiết kế: 2 người, thiết kế giao diện.</li>
<li>Ban Kinh doanh: 2 người, viết Business Plan.</li>
<li>Nhà đầu tư: 1 người, xem Business Plan và Slide Pitch.</li>
</ul>
<p><strong>Đầu ra:</strong></p>
<ul>
<li>Cấu trúc thư mục Google Drive.</li>
<li>Phân quyền cho từng nhóm.</li>
<li>Bảo vệ tài liệu quan trọng và kiểm soát quyền truy cập.</li>
</ul>
<h2 id="cấu-trúc-thư-mục">2. Cấu trúc thư mục</h2>
<pre class=" language-text"><code class="prism  language-text">CampusPay/
├── 01_Technical/
├── 02_Design/
├── 03_Business/
├── 04_Shared_Documents/
└── 05_Sensitive_Data/
-   **01_Technical:** Chứa mã nguồn và tài liệu API.
    
-   **02_Design:** Chứa thiết kế giao diện và hình ảnh.
    
-   **03_Business:** Chứa Business Plan và tài liệu kinh doanh.
    
-   **04_Shared_Documents:** Chứa Slide Pitch và Business Summary.
    
-   **05_Sensitive_Data:** Chứa API keys và dữ liệu khách hàng.
    

## 3. Các bước thực hiện

1.  Tạo thư mục CampusPay và các thư mục con.
    
2.  Đặt tên thư mục rõ ràng.
    
3.  Sắp xếp tài liệu vào đúng thư mục.
    
4.  Cấp quyền phù hợp cho từng nhóm.
    
5.  Đặt tài liệu nhạy cảm ở chế độ Restricted.
    
6.  Kiểm tra quyền truy cập và lịch sử phiên bản.
    
7.  Đặt thời hạn 14 ngày cho nhà đầu tư.
    
8.  Thu hồi quyền khi thành viên nghỉ việc.
    

# PHẦN 2: TRIỂN KHAI VÀ CHỐNG LỖI

## 4. Phân quyền cho từng nhóm

### 1. Mã nguồn và tài liệu API

-   Ban Kỹ thuật: Editor.
    
-   Ban Thiết kế: Không có quyền.
    
-   Ban Kinh doanh: Không có quyền.
    
-   Nhà đầu tư: Không có quyền.
    
-   Bảo mật: Chỉ người có nhiệm vụ mới được truy cập.
    

### 2. Thiết kế UI và hình ảnh

-   Ban Kỹ thuật: Viewer.
    
-   Ban Thiết kế: Editor.
    
-   Ban Kinh doanh: Viewer.
    
-   Nhà đầu tư: Không có quyền.
    
-   Bảo mật: Không chia sẻ công khai.
    

### 3. Business Plan

-   Ban Kỹ thuật: Viewer.
    
-   Ban Thiết kế: Không có quyền.
    
-   Ban Kinh doanh: Editor.
    
-   Nhà đầu tư: Viewer.
    
-   Bảo mật: Ban Kỹ thuật chỉ được xem, không được sửa.
    

### 4. Slide Pitch và Business Summary

-   Ban Kỹ thuật: Viewer.
    
-   Ban Thiết kế: Viewer.
    
-   Ban Kinh doanh: Editor.
    
-   Nhà đầu tư: Viewer.
    
-   Bảo mật: Nhà đầu tư chỉ được xem tài liệu đã duyệt.
    

### 5. API keys và dữ liệu khách hàng

-   Ban Kỹ thuật: Editor theo nhiệm vụ.
    
-   Ban Thiết kế: Không có quyền.
    
-   Ban Kinh doanh: Không có quyền.
    
-   Nhà đầu tư: Không có quyền.
    
-   Bảo mật: Đặt Restricted, không dùng "Anyone with the link".
    

## 5. Trả lời 3 bẫy dữ liệu

-   **Bẫy 1: Chia sẻ Business Plan cho Ban Kỹ thuật**
    
    -   Cấp quyền Viewer để Ban Kỹ thuật đọc và hiểu dự án nhưng không thể chỉnh sửa nội dung. Không cấp quyền Editor vì họ không phụ trách viết Business Plan.
        
-   **Bẫy 2: Nhà đầu tư muốn tải Slide Pitch**
    
    -   Cấp quyền Viewer đối với bản PDF và cho phép tải xuống để thuyết trình offline. Không cấp quyền chỉnh sửa bản gốc.
        
    -   Không cần tắt tính năng _Viewers can download_ đối với bản PDF này vì nhà đầu tư cần tải file về máy.
        
-   **Bẫy 3: Thành viên nghỉ việc**
    
    -   Xóa quyền truy cập của thành viên khỏi các tệp và thư mục.
        
    -   Xóa thành viên khỏi các nhóm được chia sẻ.
        
    -   Nếu dùng tài khoản công ty, yêu cầu quản trị viên khóa tài khoản khi phù hợp.
        
    -   Kiểm tra lại quyền để bảo đảm thành viên không còn truy cập tài liệu.
        

## 6. Nguyên tắc bảo mật

-   Chỉ cấp quyền cần thiết cho từng người.
    
-   Tài liệu nhạy cảm phải để Restricted.
    
-   Tài liệu quan trọng cần có lịch sử phiên bản tối thiểu 30 ngày.
    
-   Quyền nhà đầu tư phải hết hạn sau 14 ngày.
    
-   Kiểm tra quyền truy cập thường xuyên.
</code></pre>


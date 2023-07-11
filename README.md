# student-management
1. Giới thiệu đề tài

Phần mềm quản lý học sinh được tạo ra với các chức năng để hỗ trợ trong việc quản lý học sinh cũng như các công việc liên quan đến quản lý học sinh như việc tiếp nhận học sinh, lập danh sách lớp, điều chỉnh lớp, nhập điểm môn học, xuất điểm trung bình, người quản trị xem báo cáo tổng kết môn học hay thay đổi quy định, quản lý các môn học. Phần mềm được viết ra với mục tiêu giúp cho giáo viên hay người quản trị hay nhân viên có thể thực hiện dễ dàng các công việc của mình. 
2. Các bước thực hiện đề tài
- Thiết kế lược đồ use case
- Thiết kế sơ đồ lớp
- Thiết kế giao diện cho web
- Xây dựng các chức năng cho trang web
- Thực hiện thử nghiệm trên website để kiểm tra các lỗi và đảm bảo tính ổn định.
3. Thiết kế hệ thống

3.1 Lược đồ use case
![image](https://github.com/Haunguyen42193/student-management/assets/92702518/6c73ea2d-d8ed-4d72-885d-b9142425bfe0)

 3.2 Sơ đồ lớp
![image](https://github.com/Haunguyen42193/student-management/assets/92702518/fbd62fde-84be-499e-8be9-5dc9d8cc1ff0)

3.3 Lược đồ quan hệ

- Lop ( id, ten_lop)
- HocSinh – Lop: ( id, # id Lop, # id HocSinh)
- HocSinh ( id, ho_ten, gioi_tinh, ngay_sinh, dia_chi, email)
- HocSinh – HocKy (id, # id HocSinh, # id HocKy)
- HocKy (id, hoc_ky, nam_hoc)
- MonHoc ( id, ten_mon_hoc)
- Diem (id, diem_so, loai_diem, # id MonHoc, # id HocKy, # id HocSinh, # id Lop)
- GV_Lop ( id, ngay_phu_trach, # id User, # id Lop)
- User – MonHoc: (id, # id MonHoc, # id User)
- User – HocKy (id, # id HocKy, # id User)
- User (id, ten_dang_nhap, password, name, avatar, active, vai_tro)
- QuyDinh (id, loai_quy_dinh, gioi_han, # id User)

Phân tích, giải thích mối quan hệ
	User – HocKy: User có thể dạy, học hay quản lý nhiều học kỳ. Và một học kỳ có nhiều user hoạt động.
	GV_Lop: Từ mối quan hệ n-n của bảng User và bảng Lop. Một user có thể thuộc nhiều lớp và một lớp có nhiều user khác nhau.
	HocSinh – Lop: Lớp chứa nhiều học sinh. Và học sinh sẽ lên lớp hoặc chuyển lớp nên một học sinh có thể thuộc nhiều lớp.
	HocSinh – HocKy: Học sinh có thể học nhiều học kỳ trong năm học và một học kỳ có nhiều học sinh học tập.
	User – MonHoc: User có thể dạy, học hay quản lý nhiều môn học. Và một học kỳ có nhiều user dạy, học hay quản lý.

	User – QuyDinh: User NQT có thể thay đổi nhiều quy định nhưng một quy định chỉ được quản lý bởi 1 NQT. Khi NQT nghỉ việc hay chuyển cơ sở thì quy định vẫn còn, không bị hủy theo thông tin NQT.
	Lop – Diem: Một lớp có thể có nhiều điểm nhưng một điểm chỉ thuộc về một lớp duy nhất. Khi lớp không còn hoạt động dạy học tiếp thì điểm về lớp vẫn còn, không bị hủy theo thông tin lớp.
	HocKy – Diem: Một học kỳ có thể có nhiều điểm nhưng một điểm chỉ thuộc về một học kỳ duy nhất. Khi học kỳ bị hủy thì điểm về học kỳ đó vẫn còn, không bị hủy theo thông tin học kỳ.

	MonHoc – Diem: Một môn học có thể có rất nhiều điểm nhưng một điểm chỉ báo cáo về một môn học. Nếu môn học nào bị hủy thì điểm của môn học đó cũng bị xóa theo.
	HocSinh – Diem: Một học sinh có rất nhiều điểm nhưng một điểm chỉ thuộc về một học sinh thôi. Nên nếu học sinh đó có nghỉ hoặc chuyển trường thì điểm của học sinh ấy cũng bị hủy theo thông tin học sinh.





Thiết kế giao diện và thiết kế xử lý
Giao diện tìm kiếm học sinh
 
Hình 2.6 Giao diện tìm kiếm học sinh


Giao diện quản lý điểm
 
Hình 2.7 Giao diện quản lý điểm

Giao diện thay đổi điểm
 
Hình 2.8 Giao diện thay đổi điểm

Giao diện thay đổi quy định
 
Hình 2.9 Giao diện thay đổi quy định

Giao diện xem báo cáo thống kê
 
	Hình 2.10 Giao diện xem báo cáo thống kê

Chương 3.	HỆ THỐNG QUẢN LÝ HỌC SINH
3.1.1.	Quản lý điểm
Chức năng quản lý điểm: cho phép người dùng là giáo viên có thể xem được điểm số của các học sinh, xuất bảng điểm của lớp trong năm học
 
Hình 3.1 Chức năng quản lý điểm

3.1.2.	Chức năng xem thông tin điểm
Chức năng xem thông tin chi tiết số điểm của 1 học sinh, có thể thêm điểm cho học sinh này, hoặc sửa hoặc xóa 1 điểm của học sinh này
 
Hình 3.2 Chức năng xem thông tin điểm

3.1.3.	Chức năng tìm kiếm học sinh
Chức năng tìm kiếm học sinh cho phép người dùng tìm kiếm học sinh theo tên, hoặc theo lớp, hoặc theo mã số
 
Hình 3.3 Chức năng tìm kiếm học sinh
3.1.4.	Chức năng lập danh sách lớp
Chức năng lập danh sách lớp cho phép người dùng thêm các học sinh vào danh sách và tạo lớp, hoặc thay đổi lớp của học sinh
 
Hình 3.4 Chức năng lập danh sách lớp


3.1.5.	Chức năng thay đổi quy định
Chức năng thay đổi quy định cho phép thay đổi thông tin của các quy định, thêm, sửa hoặc xóa
 
Hình 3.5 Chức năng thay đổi quy định
3.1.6.	Chức năng thay đổi môn học
Chức năng thay đổi môn học cho phép thêm sửa hoặc xóa các môn học của nhà trường
 
 Hình 3.6 Chức năng thay đổi môn học

3.1.7.	Chức năng xem thống kê báo cáo
Chức năng xem thống kê báo cáo cho phép chọn môn học và học kỳ và truy xuất hiển thị ra bảng báo cáo chi tiết số lượng đạt cũng như tỉ lệ phần trăm đạt của các lớp
 
Hình 3.7 Chức năng xem thống kê báo cáo








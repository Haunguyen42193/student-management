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

4. Chức năng

4.1 Chức năng của user

Đăng nhập
![image](https://github.com/Haunguyen42193/student-management/assets/92702518/16ed9a93-7c5a-4829-a962-97d3c2bc8831)

4.2 Chức năng của giáo viên

Chức năng quản lý quản lý điểm
![image](https://github.com/Haunguyen42193/student-management/assets/92702518/57704251-bfef-4253-8bff-9824d0888fdf)

![image](https://github.com/Haunguyen42193/student-management/assets/92702518/98fd954b-1817-4ac8-baa2-c148c509636c)

![image](https://github.com/Haunguyen42193/student-management/assets/92702518/6098a1b5-ed70-4348-a34e-1d87904cd282)

![image](https://github.com/Haunguyen42193/student-management/assets/92702518/023b4633-e596-4797-811c-b69d7156b0e8)

![image](https://github.com/Haunguyen42193/student-management/assets/92702518/30c29994-88a2-4c81-9b06-c92857d6add0)

4.3 Chức năng của nhân viên

Chức năng lập danh sách lớp, đổi lớp
![image](https://github.com/Haunguyen42193/student-management/assets/92702518/f3fbd5df-8c7c-4889-9dca-007e9ead0156)

![image](https://github.com/Haunguyen42193/student-management/assets/92702518/b6977610-1609-464c-b551-4c8fc60e0d51)

4.4 Chức năng của admin
Chức năng quản lý quy định
![image](https://github.com/Haunguyen42193/student-management/assets/92702518/c366a3cf-0bf7-45de-a017-322f8b901371)

Chức năng quản lý môn học
![image](https://github.com/Haunguyen42193/student-management/assets/92702518/08fc3f84-8994-472d-bc33-d1ab2f988a61)

Chức năng thống kê báo cáo
![image](https://github.com/Haunguyen42193/student-management/assets/92702518/2686be6c-57b5-4637-8ccc-d698b20b538f)

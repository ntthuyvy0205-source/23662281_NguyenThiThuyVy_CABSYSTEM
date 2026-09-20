# CAB SYSTEM – TEST SCENARIO & TEST CASE

## 1. Nguyên tắc xây dựng

- Test Scenario là chức năng/tình huống lớn cần kiểm thử.
- Mỗi Test Scenario có **20 Test Case**.
- Mỗi Scenario bao phủ 5 nhóm: **Positive, Negative, Boundary, Empty, Invalid Format/Type**.
- Test Case được xây dựng dựa trên SRS: Functional Requirements, Acceptance Criteria, Business Rules, Use Case và API Specification.
- Các giới hạn chưa được SRS xác định (độ dài password, thang điểm Rating, chính sách hủy...) được ghi **TBD**, không tự đặt thêm yêu cầu.

## 2. Danh sách Test Scenario

| ID | Test Scenario | FR | AC |
|---|---|---|---|
| TS01 | Kiểm tra đăng ký tài khoản Customer | FR01 | AC01 |
| TS02 | Kiểm tra đăng nhập | FR02, FR06 | AC02, AC06 |
| TS03 | Kiểm tra đăng xuất | FR03 | AC03 |
| TS04 | Kiểm tra xem và cập nhật thông tin cá nhân | FR04, FR05, FR07 | AC04, AC05, AC07 |
| TS05 | Kiểm tra cập nhật trạng thái hoạt động Driver | FR08 | AC08 |
| TS06 | Kiểm tra cập nhật vị trí Driver | FR09 | AC09 |
| TS07 | Kiểm tra xem thông tin Vehicle của Driver | FR10 | AC10 |
| TS08 | Kiểm tra tạo yêu cầu đặt xe và chọn Vehicle Type | FR11–FR17 | AC11–AC17 |
| TS09 | Kiểm tra xem và lựa chọn Driver khả dụng | FR18–FR21 | AC18–AC21 |
| TS10 | Kiểm tra Driver xem và phản hồi yêu cầu chuyến | FR22–FR25 | AC22–AC25 |
| TS11 | Kiểm tra theo dõi thông tin và trạng thái Trip | FR26–FR27 | AC26–AC27 |
| TS12 | Kiểm tra cập nhật trạng thái Trip | FR28–FR31 | AC28–AC31 |
| TS13 | Kiểm tra hủy Trip | FR15, FR32 | AC15, AC32 |
| TS14 | Kiểm tra cước và thanh toán Trip | FR33–FR38 | AC33–AC38 |
| TS15 | Kiểm tra lịch sử và chi tiết Trip | FR39–FR40 | AC39–AC40 |
| TS16 | Kiểm tra Customer đánh giá Driver | FR41 | AC41 |
| TS17 | Kiểm tra xem Rating đã gửi | FR42 | AC42 |

## 3. Test Cases

### TS01 – Kiểm tra đăng ký tài khoản Customer

**Traceability:** FR01 → AC01

| TC ID | Nhóm | Test Case | Kết quả mong đợi |
|---|---|---|---|
| TC-01-01 | Positive | Đăng ký với đầy đủ dữ liệu hợp lệ | Tạo tài khoản Customer thành công |
| TC-01-02 | Positive | Đăng ký bằng email mới chưa tồn tại | Tạo tài khoản thành công |
| TC-01-03 | Positive | Đăng ký bằng số điện thoại mới chưa tồn tại | Tạo tài khoản thành công |
| TC-01-04 | Positive | Đăng ký với họ tên có khoảng trắng hợp lệ | Tạo tài khoản và lưu đúng họ tên |
| TC-01-05 | Negative | Đăng ký bằng email đã tồn tại | Từ chối tạo tài khoản |
| TC-01-06 | Negative | Đăng ký bằng số điện thoại đã tồn tại | Từ chối tạo tài khoản |
| TC-01-07 | Negative | Gửi lại cùng một yêu cầu đăng ký đã thành công | Không tạo tài khoản trùng |
| TC-01-08 | Negative | Đăng ký khi dữ liệu bắt buộc không hợp lệ | Không tạo tài khoản |
| TC-01-09 | Boundary | Họ tên tại giới hạn tối thiểu đã cấu hình | Xử lý đúng rule đã phê duyệt (TBD) |
| TC-01-10 | Boundary | Họ tên tại giới hạn tối đa đã cấu hình | Xử lý đúng rule đã phê duyệt (TBD) |
| TC-01-11 | Boundary | Password tại giới hạn tối thiểu đã cấu hình | Xử lý đúng rule đã phê duyệt (TBD) |
| TC-01-12 | Boundary | Password tại giới hạn tối đa đã cấu hình | Xử lý đúng rule đã phê duyệt (TBD) |
| TC-01-13 | Empty | Bỏ trống fullName | Từ chối đăng ký |
| TC-01-14 | Empty | Bỏ trống phone | Từ chối đăng ký |
| TC-01-15 | Empty | Bỏ trống email | Từ chối đăng ký |
| TC-01-16 | Empty | Bỏ trống password | Từ chối đăng ký |
| TC-01-17 | Empty | Bỏ trống toàn bộ dữ liệu | Từ chối đăng ký |
| TC-01-18 | Invalid Format/Type | Email không đúng định dạng | Từ chối dữ liệu |
| TC-01-19 | Invalid Format/Type | Phone sai kiểu dữ liệu | Từ chối request |
| TC-01-20 | Invalid Format/Type | Email/password gửi dạng object hoặc array | Từ chối request |

### TS02 – Kiểm tra đăng nhập

**Traceability:** FR02, FR06 → AC02, AC06

| TC ID | Nhóm | Test Case | Kết quả mong đợi |
|---|---|---|---|
| TC-02-01 | Positive | Customer đăng nhập bằng thông tin hợp lệ | Đăng nhập thành công |
| TC-02-02 | Positive | Driver đăng nhập bằng thông tin hợp lệ | Đăng nhập thành công |
| TC-02-03 | Positive | Đăng nhập lại sau khi đã logout | Đăng nhập thành công và tạo phiên mới |
| TC-02-04 | Positive | Đăng nhập bằng đúng email và password đã đăng ký | Cấp access token hợp lệ |
| TC-02-05 | Negative | Email đúng nhưng password sai | Không đăng nhập |
| TC-02-06 | Negative | Email không tồn tại | Không đăng nhập |
| TC-02-07 | Negative | Cả email và password đều sai | Không đăng nhập |
| TC-02-08 | Negative | Tài khoản không hợp lệ/không được phép truy cập | Từ chối đăng nhập theo trạng thái tài khoản |
| TC-02-09 | Boundary | Email tại giới hạn độ dài được cấu hình | Xử lý đúng rule đã phê duyệt (TBD) |
| TC-02-10 | Boundary | Password tại giới hạn tối thiểu được cấu hình | Xử lý đúng rule đã phê duyệt (TBD) |
| TC-02-11 | Boundary | Password tại giới hạn tối đa được cấu hình | Xử lý đúng rule đã phê duyệt (TBD) |
| TC-02-12 | Boundary | Đăng nhập ngay sau khi đăng ký Customer | Đăng nhập thành công nếu tài khoản đã được tạo |
| TC-02-13 | Empty | Email rỗng | Không đăng nhập |
| TC-02-14 | Empty | Password rỗng | Không đăng nhập |
| TC-02-15 | Empty | Cả email và password rỗng | Không đăng nhập |
| TC-02-16 | Empty | Request body rỗng | Từ chối request |
| TC-02-17 | Invalid Format/Type | Email sai format | Từ chối dữ liệu |
| TC-02-18 | Invalid Format/Type | Email là số/object | Từ chối request |
| TC-02-19 | Invalid Format/Type | Password là array/object | Từ chối request |
| TC-02-20 | Invalid Format/Type | Request body không đúng kiểu JSON/API | Từ chối request |

### TS03 – Kiểm tra đăng xuất

**Traceability:** FR03 → AC03

| TC ID | Nhóm | Test Case | Kết quả mong đợi |
|---|---|---|---|
| TC-03-01 | Positive | Đăng xuất khi đang đăng nhập | Đăng xuất thành công |
| TC-03-02 | Positive | Customer đăng xuất | Phiên Customer không còn sử dụng |
| TC-03-03 | Positive | Driver đăng xuất | Phiên Driver không còn sử dụng |
| TC-03-04 | Positive | Sau logout truy cập lại chức năng bảo vệ | Bị yêu cầu xác thực lại |
| TC-03-05 | Negative | Dùng token cũ sau logout | Từ chối truy cập |
| TC-03-06 | Negative | Logout bằng token không hợp lệ | Từ chối |
| TC-03-07 | Negative | Logout bằng token của phiên không tồn tại | Từ chối |
| TC-03-08 | Negative | Gọi chức năng bảo vệ sau khi phiên đã hết hiệu lực | Từ chối |
| TC-03-09 | Boundary | Logout ngay sau login | Logout thành công |
| TC-03-10 | Boundary | Logout tại thời điểm token sắp hết hiệu lực | Xử lý nhất quán theo cơ chế xác thực |
| TC-03-11 | Boundary | Logout rồi login lại ngay | Tạo phiên mới hợp lệ |
| TC-03-12 | Boundary | Chỉ một phiên/token hiện tại được gửi | Xử lý đúng phiên đó |
| TC-03-13 | Empty | Không gửi Authorization | Từ chối |
| TC-03-14 | Empty | Bearer token rỗng | Từ chối |
| TC-03-15 | Empty | Authorization là chuỗi rỗng | Từ chối |
| TC-03-16 | Empty | Không có credential xác thực | Từ chối |
| TC-03-17 | Invalid Format/Type | Authorization dùng Basic thay Bearer | Từ chối |
| TC-03-18 | Invalid Format/Type | Token sai cấu trúc | Từ chối |
| TC-03-19 | Invalid Format/Type | Authorization là dữ liệu sai kiểu | Từ chối |
| TC-03-20 | Invalid Format/Type | Header Authorization malformed | Từ chối |

### TS04 – Kiểm tra xem và cập nhật thông tin cá nhân

**Traceability:** FR04, FR05, FR07 → AC04, AC05, AC07

| TC ID | Nhóm | Test Case | Kết quả mong đợi |
|---|---|---|---|
| TC-04-01 | Positive | Customer xem hồ sơ của chính mình | Trả đúng hồ sơ Customer |
| TC-04-02 | Positive | Driver xem hồ sơ của chính mình | Trả đúng hồ sơ Driver |
| TC-04-03 | Positive | Customer cập nhật thông tin được phép | Lưu dữ liệu mới |
| TC-04-04 | Positive | Driver cập nhật thông tin được phép | Lưu dữ liệu mới |
| TC-04-05 | Negative | Cập nhật email trùng tài khoản khác | Từ chối cập nhật |
| TC-04-06 | Negative | Truy cập profile khi chưa xác thực | Từ chối |
| TC-04-07 | Negative | Cố cập nhật trường không được phép | Không cập nhật trường bị cấm |
| TC-04-08 | Negative | Cập nhật dữ liệu không hợp lệ | Không lưu dữ liệu sai |
| TC-04-09 | Boundary | fullName tại giới hạn min cấu hình | Xử lý đúng rule (TBD) |
| TC-04-10 | Boundary | fullName tại giới hạn max cấu hình | Xử lý đúng rule (TBD) |
| TC-04-11 | Boundary | phone/email tại giới hạn cấu hình | Xử lý đúng rule (TBD) |
| TC-04-12 | Boundary | Cập nhật đúng một trường được phép | Chỉ trường đó thay đổi |
| TC-04-13 | Empty | fullName rỗng | Xử lý theo validation đã phê duyệt |
| TC-04-14 | Empty | phone rỗng | Xử lý theo validation đã phê duyệt |
| TC-04-15 | Empty | email rỗng | Từ chối nếu không cho phép rỗng |
| TC-04-16 | Empty | Không có token khi GET profile | Từ chối |
| TC-04-17 | Invalid Format/Type | Email sai format | Từ chối |
| TC-04-18 | Invalid Format/Type | Phone sai kiểu | Từ chối |
| TC-04-19 | Invalid Format/Type | fullName là object/array | Từ chối |
| TC-04-20 | Invalid Format/Type | Token sai format | Từ chối |

### TS05 – Kiểm tra cập nhật trạng thái hoạt động Driver

**Traceability:** FR08 → AC08

| TC ID | Nhóm | Test Case | Kết quả mong đợi |
|---|---|---|---|
| TC-05-01 | Positive | Driver chuyển UNAVAILABLE sang AVAILABLE | Cập nhật AVAILABLE |
| TC-05-02 | Positive | Driver chuyển AVAILABLE sang UNAVAILABLE | Cập nhật UNAVAILABLE |
| TC-05-03 | Positive | Xem lại trạng thái sau cập nhật AVAILABLE | Hiển thị AVAILABLE |
| TC-05-04 | Positive | Xem lại trạng thái sau cập nhật UNAVAILABLE | Hiển thị UNAVAILABLE |
| TC-05-05 | Negative | Customer cố cập nhật trạng thái Driver | Từ chối quyền |
| TC-05-06 | Negative | Driver không xác thực cập nhật trạng thái | Từ chối |
| TC-05-07 | Negative | Gửi trạng thái ngoài danh sách hỗ trợ | Từ chối |
| TC-05-08 | Negative | Cập nhật trạng thái cho tài khoản Driver không hợp lệ | Từ chối |
| TC-05-09 | Boundary | Gửi lại AVAILABLE khi đang AVAILABLE | Trạng thái vẫn nhất quán |
| TC-05-10 | Boundary | Gửi lại UNAVAILABLE khi đang UNAVAILABLE | Trạng thái vẫn nhất quán |
| TC-05-11 | Boundary | Đổi AVAILABLE→UNAVAILABLE→AVAILABLE liên tiếp | Lưu trạng thái cuối hợp lệ |
| TC-05-12 | Boundary | Chỉ gửi đúng một giá trị enum | Cập nhật đúng giá trị |
| TC-05-13 | Empty | availabilityStatus rỗng | Từ chối |
| TC-05-14 | Empty | Body rỗng | Từ chối |
| TC-05-15 | Empty | Không Authorization | Từ chối |
| TC-05-16 | Empty | Bearer rỗng | Từ chối |
| TC-05-17 | Invalid Format/Type | Status=BUSY | Từ chối |
| TC-05-18 | Invalid Format/Type | Status dạng số | Từ chối |
| TC-05-19 | Invalid Format/Type | Status dạng array | Từ chối |
| TC-05-20 | Invalid Format/Type | Token malformed | Từ chối |

### TS06 – Kiểm tra cập nhật vị trí Driver

**Traceability:** FR09 → AC09

| TC ID | Nhóm | Test Case | Kết quả mong đợi |
|---|---|---|---|
| TC-06-01 | Positive | Cập nhật tọa độ hợp lệ | Ghi nhận vị trí mới |
| TC-06-02 | Positive | Cập nhật vị trí mới lần tiếp theo | Ghi nhận bản ghi vị trí mới |
| TC-06-03 | Positive | Cập nhật latitude/longitude có phần thập phân | Lưu đúng tọa độ |
| TC-06-04 | Positive | Driver xem luồng hoạt động sau khi cập nhật vị trí | Vị trí mới được sử dụng theo hệ thống |
| TC-06-05 | Negative | Customer cố cập nhật vị trí Driver | Từ chối quyền |
| TC-06-06 | Negative | Latitude > 90 | Từ chối |
| TC-06-07 | Negative | Latitude < -90 | Từ chối |
| TC-06-08 | Negative | Longitude ngoài [-180,180] | Từ chối |
| TC-06-09 | Boundary | Latitude = 90 | Chấp nhận |
| TC-06-10 | Boundary | Latitude = -90 | Chấp nhận |
| TC-06-11 | Boundary | Longitude = 180 | Chấp nhận |
| TC-06-12 | Boundary | Longitude = -180 | Chấp nhận |
| TC-06-13 | Empty | Latitude rỗng | Từ chối |
| TC-06-14 | Empty | Longitude rỗng | Từ chối |
| TC-06-15 | Empty | Cả hai tọa độ rỗng | Từ chối |
| TC-06-16 | Empty | Không token | Từ chối |
| TC-06-17 | Invalid Format/Type | Latitude là chữ | Từ chối |
| TC-06-18 | Invalid Format/Type | Longitude là object | Từ chối |
| TC-06-19 | Invalid Format/Type | Latitude là array | Từ chối |
| TC-06-20 | Invalid Format/Type | Token sai format | Từ chối |

### TS07 – Kiểm tra xem thông tin Vehicle của Driver

**Traceability:** FR10 → AC10

| TC ID | Nhóm | Test Case | Kết quả mong đợi |
|---|---|---|---|
| TC-07-01 | Positive | Driver có một Vehicle xem thông tin | Trả đúng Vehicle |
| TC-07-02 | Positive | Driver có nhiều Vehicle xem danh sách | Trả đúng các Vehicle thuộc Driver |
| TC-07-03 | Positive | Vehicle trả đúng Vehicle Type | Thông tin liên kết đúng |
| TC-07-04 | Positive | Vehicle trả đúng biển số/brand/model | Thông tin đúng dữ liệu lưu |
| TC-07-05 | Negative | Customer gọi chức năng Vehicle Driver | Từ chối |
| TC-07-06 | Negative | Driver A không được xem Vehicle Driver B | Không lộ dữ liệu B |
| TC-07-07 | Negative | Không xác thực truy cập | Từ chối |
| TC-07-08 | Negative | Token không hợp lệ | Từ chối |
| TC-07-09 | Boundary | Driver có 0 Vehicle | Trả danh sách rỗng/đúng thiết kế |
| TC-07-10 | Boundary | Driver có đúng 1 Vehicle | Trả đúng 1 phần tử |
| TC-07-11 | Boundary | Driver có nhiều Vehicle | Trả đủ Vehicle thuộc Driver |
| TC-07-12 | Boundary | Vehicle có trường thông tin tùy chọn rỗng | Không làm sai ownership/liên kết |
| TC-07-13 | Empty | Không Authorization | Từ chối |
| TC-07-14 | Empty | Bearer rỗng | Từ chối |
| TC-07-15 | Empty | Credential rỗng | Từ chối |
| TC-07-16 | Empty | Không có dữ liệu Vehicle | Không trả Vehicle của Driver khác |
| TC-07-17 | Invalid Format/Type | Token malformed | Từ chối |
| TC-07-18 | Invalid Format/Type | Sai auth scheme | Từ chối |
| TC-07-19 | Invalid Format/Type | Header auth sai kiểu | Từ chối |
| TC-07-20 | Invalid Format/Type | Request không đúng API contract | Từ chối/xử lý đúng contract |

### TS08 – Kiểm tra tạo yêu cầu đặt xe và chọn Vehicle Type

**Traceability:** FR11–FR17 → AC11–AC17

| TC ID | Nhóm | Test Case | Kết quả mong đợi |
|---|---|---|---|
| TC-08-01 | Positive | Xem danh sách Vehicle Type hỗ trợ | Hiển thị danh sách |
| TC-08-02 | Positive | Nhập điểm đón hợp lệ | Chấp nhận điểm đón |
| TC-08-03 | Positive | Nhập điểm đến hợp lệ | Chấp nhận điểm đến |
| TC-08-04 | Positive | Tạo Trip với đầy đủ dữ liệu hợp lệ | Tạo Trip CREATED |
| TC-08-05 | Negative | Customer đang có Trip active tạo Trip mới | Từ chối RULE-02 |
| TC-08-06 | Negative | Vehicle Type không tồn tại | Không tạo Trip |
| TC-08-07 | Negative | Tọa độ điểm đón ngoài phạm vi | Không tạo Trip |
| TC-08-08 | Negative | Tọa độ điểm đến ngoài phạm vi | Không tạo Trip |
| TC-08-09 | Boundary | Danh sách chỉ có 1 Vehicle Type | Hiển thị/chọn đúng 1 loại |
| TC-08-10 | Boundary | Latitude điểm đón = ±90 | Xử lý đúng tọa độ biên |
| TC-08-11 | Boundary | Longitude điểm đến = ±180 | Xử lý đúng tọa độ biên |
| TC-08-12 | Boundary | Customer vừa hoàn tất Trip trước rồi tạo Trip mới | Cho phép nếu không còn Trip active |
| TC-08-13 | Empty | Điểm đón rỗng | Không tạo Trip |
| TC-08-14 | Empty | Điểm đến rỗng | Không tạo Trip |
| TC-08-15 | Empty | vehicleTypeId rỗng | Không tạo Trip |
| TC-08-16 | Empty | Body tạo Trip rỗng | Từ chối |
| TC-08-17 | Invalid Format/Type | pickupLatitude là chữ | Từ chối |
| TC-08-18 | Invalid Format/Type | destinationLongitude là object | Từ chối |
| TC-08-19 | Invalid Format/Type | vehicleTypeId sai kiểu | Từ chối |
| TC-08-20 | Invalid Format/Type | Dữ liệu tọa độ sai format | Từ chối |

### TS09 – Kiểm tra xem và lựa chọn Driver khả dụng

**Traceability:** FR18–FR21 → AC18–AC21

| TC ID | Nhóm | Test Case | Kết quả mong đợi |
|---|---|---|---|
| TC-09-01 | Positive | Hiển thị Driver AVAILABLE phù hợp Vehicle Type | Danh sách đúng |
| TC-09-02 | Positive | Xem thông tin cơ bản Driver | Hiển thị đúng Driver |
| TC-09-03 | Positive | Chọn Driver hợp lệ | Driver được chọn |
| TC-09-04 | Positive | Gửi TripOffer cho Driver đã chọn | Tạo offer PENDING |
| TC-09-05 | Negative | Chọn Driver UNAVAILABLE | Từ chối |
| TC-09-06 | Negative | Chọn Driver đang có Trip active | Từ chối RULE-04 |
| TC-09-07 | Negative | Chọn Driver có Vehicle Type không phù hợp | Từ chối RULE-05 |
| TC-09-08 | Negative | Chọn Driver không tồn tại | Từ chối |
| TC-09-09 | Boundary | Không có Driver phù hợp | Danh sách rỗng |
| TC-09-10 | Boundary | Có đúng 1 Driver phù hợp | Hiển thị đúng 1 Driver |
| TC-09-11 | Boundary | Có nhiều Driver phù hợp | Chỉ hiển thị Driver hợp lệ |
| TC-09-12 | Boundary | Driver vừa chuyển AVAILABLE | Xuất hiện nếu đáp ứng điều kiện |
| TC-09-13 | Empty | vehicleTypeId rỗng | Từ chối |
| TC-09-14 | Empty | driverId rỗng | Không tạo offer |
| TC-09-15 | Empty | tripId rỗng | Không chọn Driver |
| TC-09-16 | Empty | Không token | Từ chối |
| TC-09-17 | Invalid Format/Type | driverId sai format | Từ chối |
| TC-09-18 | Invalid Format/Type | vehicleTypeId sai kiểu | Từ chối |
| TC-09-19 | Invalid Format/Type | tripId không tồn tại | Từ chối |
| TC-09-20 | Invalid Format/Type | Token malformed | Từ chối |

### TS10 – Kiểm tra Driver xem và phản hồi yêu cầu chuyến

**Traceability:** FR22–FR25 → AC22–AC25

| TC ID | Nhóm | Test Case | Kết quả mong đợi |
|---|---|---|---|
| TC-10-01 | Positive | Driver xem offer PENDING của mình | Hiển thị offer |
| TC-10-02 | Positive | Driver ACCEPTED offer | Gán Driver; Trip DRIVER_ASSIGNED |
| TC-10-03 | Positive | Driver REJECTED offer | Không gán Driver |
| TC-10-04 | Positive | Sau reject Customer có thể chọn Driver khác | Cho phép chọn lại |
| TC-10-05 | Negative | Phản hồi offer đã ACCEPTED | Từ chối |
| TC-10-06 | Negative | Phản hồi offer đã REJECTED | Từ chối |
| TC-10-07 | Negative | Driver khác phản hồi offer không thuộc mình | Từ chối |
| TC-10-08 | Negative | Driver không AVAILABLE chấp nhận offer | Từ chối nếu không còn hợp lệ |
| TC-10-09 | Boundary | Driver có 0 offer | Trả danh sách rỗng |
| TC-10-10 | Boundary | Driver có đúng 1 offer PENDING | Trả đúng 1 offer |
| TC-10-11 | Boundary | Offer được phản hồi đúng một lần | Chỉ phản hồi đầu tiên hợp lệ |
| TC-10-12 | Boundary | Reject rồi Customer chọn Driver khác | Trip tiếp tục luồng chọn Driver |
| TC-10-13 | Empty | response rỗng | Từ chối |
| TC-10-14 | Empty | offerId rỗng | Từ chối |
| TC-10-15 | Empty | Không token | Từ chối |
| TC-10-16 | Empty | Body rỗng | Từ chối |
| TC-10-17 | Invalid Format/Type | response=MAYBE | Từ chối |
| TC-10-18 | Invalid Format/Type | offerId không tồn tại | Báo không tìm thấy |
| TC-10-19 | Invalid Format/Type | response dạng số | Từ chối |
| TC-10-20 | Invalid Format/Type | Token sai format | Từ chối |

### TS11 – Kiểm tra theo dõi thông tin và trạng thái Trip

**Traceability:** FR26–FR27 → AC26–AC27

| TC ID | Nhóm | Test Case | Kết quả mong đợi |
|---|---|---|---|
| TC-11-01 | Positive | Xem Driver đã chấp nhận Trip | Hiển thị đúng Driver |
| TC-11-02 | Positive | Xem trạng thái Trip DRIVER_ASSIGNED | Hiển thị đúng status |
| TC-11-03 | Positive | Xem trạng thái Trip IN_PROGRESS | Hiển thị đúng status |
| TC-11-04 | Positive | Xem Trip COMPLETED | Hiển thị đúng trạng thái và dữ liệu hiện có |
| TC-11-05 | Negative | Customer xem Trip của người khác | Từ chối NFR-06 |
| TC-11-06 | Negative | Không xác thực xem Trip | Từ chối |
| TC-11-07 | Negative | tripId không tồn tại | Báo không tìm thấy |
| TC-11-08 | Negative | Dùng token không hợp lệ | Từ chối |
| TC-11-09 | Boundary | Trip CREATED chưa có Driver | Driver/Vehicle có thể null |
| TC-11-10 | Boundary | Trip vừa chuyển DRIVER_ASSIGNED | Hiển thị Driver mới được gán |
| TC-11-11 | Boundary | Trip vừa chuyển COMPLETED | Hiển thị trạng thái mới nhất |
| TC-11-12 | Boundary | Trip CANCELLED | Hiển thị CANCELLED |
| TC-11-13 | Empty | tripId rỗng | Không xử lý hợp lệ |
| TC-11-14 | Empty | Không token | Từ chối |
| TC-11-15 | Empty | Bearer rỗng | Từ chối |
| TC-11-16 | Empty | Dữ liệu Driver chưa có ở Trip CREATED | Không lỗi; thể hiện null phù hợp |
| TC-11-17 | Invalid Format/Type | tripId sai format | Từ chối/không tìm thấy |
| TC-11-18 | Invalid Format/Type | Token malformed | Từ chối |
| TC-11-19 | Invalid Format/Type | Sai auth scheme | Từ chối |
| TC-11-20 | Invalid Format/Type | Request sai API contract | Xử lý lỗi phù hợp |

### TS12 – Kiểm tra cập nhật trạng thái Trip

**Traceability:** FR28–FR31 → AC28–AC31

| TC ID | Nhóm | Test Case | Kết quả mong đợi |
|---|---|---|---|
| TC-12-01 | Positive | DRIVER_ASSIGNED → DRIVER_ARRIVED | Chuyển trạng thái thành công |
| TC-12-02 | Positive | DRIVER_ARRIVED → PASSENGER_PICKED_UP | Chuyển trạng thái thành công |
| TC-12-03 | Positive | PASSENGER_PICKED_UP → IN_PROGRESS | Chuyển trạng thái thành công |
| TC-12-04 | Positive | IN_PROGRESS → COMPLETED | Chuyển trạng thái thành công |
| TC-12-05 | Negative | DRIVER_ASSIGNED → COMPLETED | Từ chối RULE-09 |
| TC-12-06 | Negative | DRIVER_ARRIVED → IN_PROGRESS | Từ chối bỏ bước |
| TC-12-07 | Negative | Driver khác cập nhật Trip | Từ chối NFR-07 |
| TC-12-08 | Negative | Customer cập nhật status qua API Driver | Từ chối quyền |
| TC-12-09 | Boundary | Cập nhật bước đầu DRIVER_ASSIGNED→DRIVER_ARRIVED | Hợp lệ |
| TC-12-10 | Boundary | Cập nhật bước cuối IN_PROGRESS→COMPLETED | Hợp lệ |
| TC-12-11 | Boundary | Cập nhật status sau COMPLETED | Không cho chuyển tiếp trái vòng đời |
| TC-12-12 | Boundary | Cập nhật status cho CANCELLED Trip | Không cho tiếp tục Trip |
| TC-12-13 | Empty | status rỗng | Từ chối |
| TC-12-14 | Empty | Body rỗng | Từ chối |
| TC-12-15 | Empty | tripId rỗng | Từ chối |
| TC-12-16 | Empty | Không token | Từ chối |
| TC-12-17 | Invalid Format/Type | status=RUNNING | Từ chối |
| TC-12-18 | Invalid Format/Type | status dạng số | Từ chối |
| TC-12-19 | Invalid Format/Type | tripId không tồn tại | Báo không tìm thấy |
| TC-12-20 | Invalid Format/Type | Token malformed | Từ chối |

### TS13 – Kiểm tra hủy Trip

**Traceability:** FR15, FR32 → AC15, AC32

| TC ID | Nhóm | Test Case | Kết quả mong đợi |
|---|---|---|---|
| TC-13-01 | Positive | Customer hủy Trip ở trạng thái được phép | Trip chuyển CANCELLED |
| TC-13-02 | Positive | Driver hủy Trip ở trạng thái được phép | Trip chuyển CANCELLED |
| TC-13-03 | Positive | Sau hủy xem lại Trip | Hiển thị CANCELLED |
| TC-13-04 | Positive | Ghi nhận cancelledAt khi hủy thành công | Có thời điểm hủy |
| TC-13-05 | Negative | Customer hủy Trip người khác | Từ chối |
| TC-13-06 | Negative | Driver hủy Trip không được giao | Từ chối |
| TC-13-07 | Negative | Hủy Trip COMPLETED | Từ chối |
| TC-13-08 | Negative | Hủy lại Trip đã CANCELLED | Từ chối/không tạo lần hủy mới |
| TC-13-09 | Boundary | Hủy ở trạng thái sớm nhất chính sách cho phép | Xử lý đúng policy (TBD) |
| TC-13-10 | Boundary | Hủy ở trạng thái cuối cùng policy cho phép | Xử lý đúng policy (TBD) |
| TC-13-11 | Boundary | Hủy ngay sau khi tạo Trip | Theo chính sách được chốt |
| TC-13-12 | Boundary | Hủy ngay trước trạng thái không còn cho phép | Theo chính sách được chốt |
| TC-13-13 | Empty | tripId rỗng | Từ chối |
| TC-13-14 | Empty | Không token | Từ chối |
| TC-13-15 | Empty | Bearer rỗng | Từ chối |
| TC-13-16 | Empty | Request thiếu định danh Trip | Không xử lý |
| TC-13-17 | Invalid Format/Type | tripId không tồn tại | Báo không tìm thấy |
| TC-13-18 | Invalid Format/Type | tripId sai format | Từ chối |
| TC-13-19 | Invalid Format/Type | Token sai format | Từ chối |
| TC-13-20 | Invalid Format/Type | Sai auth scheme | Từ chối |

### TS14 – Kiểm tra cước và thanh toán Trip

**Traceability:** FR33–FR38 → AC33–AC38

| TC ID | Nhóm | Test Case | Kết quả mong đợi |
|---|---|---|---|
| TC-14-01 | Positive | Sau COMPLETED hệ thống ghi finalFare | Có finalFare |
| TC-14-02 | Positive | Customer xem cước Trip | Hiển thị đúng finalFare |
| TC-14-03 | Positive | Thanh toán CASH | Ghi Payment liên kết Trip |
| TC-14-04 | Positive | Thanh toán ELECTRONIC | Xử lý qua Provider và lưu kết quả |
| TC-14-05 | Negative | Thanh toán trước COMPLETED | Từ chối |
| TC-14-06 | Negative | Customer khác thanh toán Trip | Từ chối quyền |
| TC-14-07 | Negative | Payment method không hỗ trợ | Từ chối RULE-11 |
| TC-14-08 | Negative | Trip không có finalFare hợp lệ | Không tạo thanh toán |
| TC-14-09 | Boundary | Ngay trước COMPLETED finalFare chưa được ghi | finalFare chưa có |
| TC-14-10 | Boundary | Ngay sau COMPLETED finalFare được ghi | finalFare có |
| TC-14-11 | Boundary | Trip có lần thử payment thất bại rồi thử lại | Lưu kết quả theo thiết kế/chính sách |
| TC-14-12 | Boundary | Trip có nhiều bản ghi/thử Payment | Các Payment vẫn liên kết đúng Trip |
| TC-14-13 | Empty | method rỗng | Từ chối |
| TC-14-14 | Empty | tripId rỗng | Từ chối |
| TC-14-15 | Empty | Không token | Từ chối |
| TC-14-16 | Empty | Body payment rỗng | Từ chối |
| TC-14-17 | Invalid Format/Type | method=CRYPTO | Từ chối |
| TC-14-18 | Invalid Format/Type | method dạng số | Từ chối |
| TC-14-19 | Invalid Format/Type | Client gửi amount sai kiểu ngoài contract | Không dùng amount client để thay finalFare |
| TC-14-20 | Invalid Format/Type | tripId không tồn tại | Báo không tìm thấy |

### TS15 – Kiểm tra lịch sử và chi tiết Trip

**Traceability:** FR39–FR40 → AC39–AC40

| TC ID | Nhóm | Test Case | Kết quả mong đợi |
|---|---|---|---|
| TC-15-01 | Positive | Customer xem danh sách Trip của mình | Trả lịch sử đúng |
| TC-15-02 | Positive | Xem chi tiết một Trip lịch sử | Trả đúng chi tiết |
| TC-15-03 | Positive | Lịch sử có Trip COMPLETED | Hiển thị Trip |
| TC-15-04 | Positive | Lịch sử có Trip CANCELLED | Hiển thị Trip theo dữ liệu hệ thống |
| TC-15-05 | Negative | Customer xem chi tiết Trip người khác | Từ chối |
| TC-15-06 | Negative | Không xác thực xem lịch sử | Từ chối |
| TC-15-07 | Negative | tripId không tồn tại | Báo không tìm thấy |
| TC-15-08 | Negative | Token không hợp lệ | Từ chối |
| TC-15-09 | Boundary | Lịch sử 0 Trip | Trả danh sách rỗng |
| TC-15-10 | Boundary | Lịch sử đúng 1 Trip | Trả 1 phần tử |
| TC-15-11 | Boundary | Lịch sử nhiều Trip | Trả các Trip thuộc Customer |
| TC-15-12 | Boundary | Trip lịch sử chưa có Rating | Vẫn xem được chi tiết Trip |
| TC-15-13 | Empty | Không token | Từ chối |
| TC-15-14 | Empty | Bearer rỗng | Từ chối |
| TC-15-15 | Empty | tripId rỗng khi xem detail | Không xử lý hợp lệ |
| TC-15-16 | Empty | Danh sách không có dữ liệu | Trả rỗng, không lộ dữ liệu khác |
| TC-15-17 | Invalid Format/Type | tripId sai format | Từ chối/không tìm thấy |
| TC-15-18 | Invalid Format/Type | Token malformed | Từ chối |
| TC-15-19 | Invalid Format/Type | Sai auth scheme | Từ chối |
| TC-15-20 | Invalid Format/Type | Request sai API contract | Xử lý lỗi phù hợp |

### TS16 – Kiểm tra Customer đánh giá Driver

**Traceability:** FR41 → AC41

| TC ID | Nhóm | Test Case | Kết quả mong đợi |
|---|---|---|---|
| TC-16-01 | Positive | Đánh giá Driver sau Trip COMPLETED | Tạo Rating |
| TC-16-02 | Positive | Rating liên kết đúng Trip | Lưu đúng tripId |
| TC-16-03 | Positive | Rating liên kết đúng Customer và Driver | Lưu đúng quan hệ |
| TC-16-04 | Positive | Đánh giá kèm comment | Lưu Rating và comment |
| TC-16-05 | Negative | Đánh giá khi Trip IN_PROGRESS | Từ chối RULE-14 |
| TC-16-06 | Negative | Đánh giá Trip người khác | Từ chối RULE-13 |
| TC-16-07 | Negative | Đánh giá lần hai cùng Trip | Từ chối RULE-15 |
| TC-16-08 | Negative | Đánh giá Trip không tồn tại | Không tạo Rating |
| TC-16-09 | Boundary | Rating đầu tiên của Trip | Tạo thành công |
| TC-16-10 | Boundary | Rating thứ hai của cùng Trip | Từ chối |
| TC-16-11 | Boundary | Score tại min được cấu hình | Xử lý theo thang điểm đã chốt (TBD) |
| TC-16-12 | Boundary | Score tại max được cấu hình | Xử lý theo thang điểm đã chốt (TBD) |
| TC-16-13 | Empty | Score rỗng | Từ chối |
| TC-16-14 | Empty | Comment rỗng | Xử lý theo API spec; SRS chưa bắt buộc comment |
| TC-16-15 | Empty | tripId rỗng | Từ chối |
| TC-16-16 | Empty | Không token | Từ chối |
| TC-16-17 | Invalid Format/Type | Score là chữ | Từ chối |
| TC-16-18 | Invalid Format/Type | Score là object/array | Từ chối |
| TC-16-19 | Invalid Format/Type | tripId không tồn tại | Không tạo Rating |
| TC-16-20 | Invalid Format/Type | Token malformed | Từ chối |

### TS17 – Kiểm tra xem Rating đã gửi

**Traceability:** FR42 → AC42

| TC ID | Nhóm | Test Case | Kết quả mong đợi |
|---|---|---|---|
| TC-17-01 | Positive | Xem Rating đã gửi | Trả đúng Rating |
| TC-17-02 | Positive | Xem score đã lưu | Hiển thị đúng score |
| TC-17-03 | Positive | Xem comment đã lưu | Hiển thị đúng comment |
| TC-17-04 | Positive | Xem liên kết Trip/Customer/Driver của Rating | Thông tin đúng |
| TC-17-05 | Negative | Xem Rating Trip người khác | Từ chối |
| TC-17-06 | Negative | Trip chưa có Rating | Báo Rating không tồn tại |
| TC-17-07 | Negative | Không xác thực xem Rating | Từ chối |
| TC-17-08 | Negative | Trip không tồn tại | Báo không tìm thấy |
| TC-17-09 | Boundary | Trip có đúng 1 Rating | Trả đúng 1 Rating |
| TC-17-10 | Boundary | Rating có comment rỗng/null | Vẫn trả Rating hợp lệ |
| TC-17-11 | Boundary | Rating vừa tạo xong được xem ngay | Trả dữ liệu vừa lưu |
| TC-17-12 | Boundary | Mỗi Trip tối đa 1 Rating | Không trả nhiều Rating chính thức |
| TC-17-13 | Empty | tripId rỗng | Từ chối |
| TC-17-14 | Empty | Không token | Từ chối |
| TC-17-15 | Empty | Bearer rỗng | Từ chối |
| TC-17-16 | Empty | Rating không tồn tại | Không trả Rating giả |
| TC-17-17 | Invalid Format/Type | tripId sai format | Từ chối/không tìm thấy |
| TC-17-18 | Invalid Format/Type | tripId không tồn tại | Báo không tìm thấy |
| TC-17-19 | Invalid Format/Type | Token malformed | Từ chối |
| TC-17-20 | Invalid Format/Type | Sai auth scheme | Từ chối |

## 4. Tổng hợp

- Tổng Test Scenario: **17**.
- Test Case mỗi Scenario: **20**.
- Tổng Test Case: **340**.
- Bao phủ: **Positive / Negative / Boundary / Empty / Invalid Format-Type**.

> Lưu ý: Các Test Case Boundary có `TBD` phải được cập nhật khi nhóm/giảng viên/khách hàng chốt validation rule hoặc business policy tương ứng.
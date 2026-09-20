# CAB System – Test Scenario & Test Case

File này được làm lại theo cấu trúc của bài mẫu: **mỗi Business Process được xem là một Test Scenario lớn**, mỗi Test Scenario có **20 Test Case**.

Phạm vi bám theo SRS hiện tại của CAB System và bao phủ 5 nhóm kiểm thử: **Positive, Negative, Boundary, Empty, Invalid Format/Type**.

## 1. Danh sách Test Scenario

| Test Scenario ID | Test Scenario | Functional Requirements | Acceptance Criteria | Số Test Case |
| --- | --- | --- | --- | ---: |
| BP-01 | Quản lý tài khoản Customer | FR01–FR05 | AC01–AC05 | 20 |
| BP-02 | Quản lý Driver | FR06–FR10 | AC06–AC10 | 20 |
| BP-03 | Tạo yêu cầu đặt xe | FR11–FR15 | AC11–AC15 | 20 |
| BP-04 | Lựa chọn loại xe | FR16–FR17 | AC16–AC17 | 20 |
| BP-05 | Tìm và lựa chọn Driver | FR18–FR21 | AC18–AC21 | 20 |
| BP-06 | Driver tiếp nhận và phản hồi yêu cầu chuyến | FR22–FR25 | AC22–AC25 | 20 |
| BP-07 | Theo dõi và thực hiện Trip | FR26–FR32 | AC26–AC32 | 20 |
| BP-08 | Tính cước và thanh toán | FR33–FR38 | AC33–AC38 | 20 |
| BP-09 | Lịch sử chuyến và đánh giá Driver | FR39–FR42 | AC39–AC42 | 20 |

## 2. Chi tiết Test Case

## BP-01 – Quản lý tài khoản Customer

**Traceability:** FR01–FR05 → AC01–AC05

| Test Case ID | Test Scenario | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| TC-BP01-001 | BP-01 – Quản lý tài khoản Customer | Positive | Đăng ký Customer với thông tin hợp lệ | Email và phone chưa tồn tại | 1. Mở đăng ký<br>2. Nhập fullName, phone, email, password<br>3. Nhấn Đăng ký | Nguyễn Văn A; 0901234567; vana@example.com; Abc@123 | Tạo tài khoản Customer thành công | High |
| TC-BP01-002 | BP-01 – Quản lý tài khoản Customer | Positive | Customer đăng nhập đúng thông tin | Customer đã có tài khoản | 1. Mở Login<br>2. Nhập email/password<br>3. Đăng nhập | vana@example.com / Abc@123 | Đăng nhập thành công và cấp token | High |
| TC-BP01-003 | BP-01 – Quản lý tài khoản Customer | Positive | Customer xem hồ sơ cá nhân | Customer đã đăng nhập | 1. Gọi chức năng xem profile | Token hợp lệ | Hiển thị đúng hồ sơ Customer | Medium |
| TC-BP01-004 | BP-01 – Quản lý tài khoản Customer | Positive | Customer cập nhật hồ sơ hợp lệ | Customer đã đăng nhập | 1. Mở profile<br>2. Sửa thông tin được phép<br>3. Lưu | fullName=Nguyễn Văn B | Cập nhật thành công | Medium |
| TC-BP01-005 | BP-01 – Quản lý tài khoản Customer | Negative | Đăng ký bằng email đã tồn tại | Email đã được sử dụng | 1. Nhập dữ liệu<br>2. Đăng ký | existing@example.com | Không tạo tài khoản; báo email trùng | High |
| TC-BP01-006 | BP-01 – Quản lý tài khoản Customer | Negative | Đăng ký bằng phone đã tồn tại | Phone đã được sử dụng | 1. Nhập dữ liệu<br>2. Đăng ký | 0901234567 | Không tạo tài khoản; báo phone trùng | High |
| TC-BP01-007 | BP-01 – Quản lý tài khoản Customer | Negative | Đăng nhập sai password | Customer tồn tại | 1. Nhập email đúng<br>2. Nhập password sai<br>3. Login | vana@example.com / Wrong123 | Không đăng nhập; không cấp token | High |
| TC-BP01-008 | BP-01 – Quản lý tài khoản Customer | Negative | Cập nhật email trùng tài khoản khác | Customer đã đăng nhập | 1. Sửa email<br>2. Lưu | existing@example.com | Không cập nhật; báo dữ liệu trùng | High |
| TC-BP01-009 | BP-01 – Quản lý tài khoản Customer | Boundary | Đăng ký với dữ liệu tại giới hạn validation | Rule min/max được chốt | 1. Nhập dữ liệu đúng tại biên<br>2. Đăng ký | Giới hạn = TBD theo rule | Xử lý đúng giới hạn được phê duyệt | Medium |
| TC-BP01-010 | BP-01 – Quản lý tài khoản Customer | Boundary | Cập nhật chỉ một trường profile | Customer đã đăng nhập | 1. Chỉ sửa fullName<br>2. Lưu | fullName=Nguyễn Văn C | Chỉ fullName thay đổi; trường khác giữ nguyên | Medium |
| TC-BP01-011 | BP-01 – Quản lý tài khoản Customer | Boundary | Đăng nhập ngay sau khi đăng ký | Vừa đăng ký thành công | 1. Chuyển Login<br>2. Nhập credential vừa tạo | Credential mới | Đăng nhập thành công | Medium |
| TC-BP01-012 | BP-01 – Quản lý tài khoản Customer | Boundary | Logout ngay sau Login | Customer vừa đăng nhập | 1. Login<br>2. Logout ngay | Token mới | Logout thành công; token cũ không dùng được | Medium |
| TC-BP01-013 | BP-01 – Quản lý tài khoản Customer | Empty | Bỏ trống fullName khi đăng ký | Ở màn hình đăng ký | 1. Để fullName rỗng<br>2. Đăng ký | fullName=empty | Không tạo tài khoản | High |
| TC-BP01-014 | BP-01 – Quản lý tài khoản Customer | Empty | Bỏ trống email khi đăng ký | Ở màn hình đăng ký | 1. Để email rỗng<br>2. Đăng ký | email=empty | Không tạo tài khoản | High |
| TC-BP01-015 | BP-01 – Quản lý tài khoản Customer | Empty | Bỏ trống password khi đăng nhập | Ở màn hình Login | 1. Nhập email<br>2. Để password rỗng<br>3. Login | password=empty | Không đăng nhập | High |
| TC-BP01-016 | BP-01 – Quản lý tài khoản Customer | Empty | Không gửi token khi xem profile | Chưa xác thực | 1. Gọi GET /users/me | Authorization=empty | Từ chối truy cập | High |
| TC-BP01-017 | BP-01 – Quản lý tài khoản Customer | Invalid Format/Type | Email đăng ký sai định dạng | Ở màn hình đăng ký | 1. Nhập email sai<br>2. Đăng ký | vanaexample.com | Từ chối dữ liệu | High |
| TC-BP01-018 | BP-01 – Quản lý tài khoản Customer | Invalid Format/Type | Phone sai kiểu dữ liệu | API đăng ký hoạt động | 1. Gửi request đăng ký | phone=[] | API trả validation error | High |
| TC-BP01-019 | BP-01 – Quản lý tài khoản Customer | Invalid Format/Type | Email cập nhật sai định dạng | Customer đã đăng nhập | 1. PUT profile với email sai | abc@ | Không cập nhật profile | High |
| TC-BP01-020 | BP-01 – Quản lý tài khoản Customer | Invalid Format/Type | Token sai định dạng khi logout | Customer có token không hợp lệ | 1. Gọi logout | Bearer abc | Từ chối xác thực | High |

## BP-02 – Quản lý Driver

**Traceability:** FR06–FR10 → AC06–AC10

| Test Case ID | Test Scenario | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| TC-BP02-001 | BP-02 – Quản lý Driver | Positive | Driver đăng nhập hợp lệ | Driver account đã được cấp sẵn | 1. Nhập email/password<br>2. Login | driver@example.com / đúng password | Đăng nhập thành công | High |
| TC-BP02-002 | BP-02 – Quản lý Driver | Positive | Driver xem hồ sơ của mình | Driver đã login | 1. Mở profile | Token Driver | Hiển thị đúng profile | Medium |
| TC-BP02-003 | BP-02 – Quản lý Driver | Positive | Driver cập nhật hồ sơ hợp lệ | Driver đã login | 1. Sửa trường được phép<br>2. Lưu | fullName/phone/email hợp lệ | Cập nhật thành công | Medium |
| TC-BP02-004 | BP-02 – Quản lý Driver | Positive | Driver chuyển trạng thái AVAILABLE | Driver đã login | 1. Cập nhật status | AVAILABLE | Trạng thái thành AVAILABLE | High |
| TC-BP02-005 | BP-02 – Quản lý Driver | Positive | Driver chuyển trạng thái UNAVAILABLE | Driver đang AVAILABLE | 1. Cập nhật status | UNAVAILABLE | Trạng thái thành UNAVAILABLE | High |
| TC-BP02-006 | BP-02 – Quản lý Driver | Positive | Driver cập nhật vị trí hợp lệ | Driver đã login | 1. Gửi latitude/longitude | 10.8231 / 106.6297 | Vị trí được ghi nhận | High |
| TC-BP02-007 | BP-02 – Quản lý Driver | Positive | Driver xem Vehicle của mình | Driver có Vehicle | 1. Gọi danh sách Vehicle | Token Driver | Trả đúng Vehicle thuộc Driver | Medium |
| TC-BP02-008 | BP-02 – Quản lý Driver | Negative | Customer gọi chức năng Driver | Customer đã login | 1. Gọi API cập nhật Driver | Token Customer | Từ chối quyền | High |
| TC-BP02-009 | BP-02 – Quản lý Driver | Negative | Driver cập nhật email trùng | Email thuộc user khác | 1. PUT profile | existing@example.com | Từ chối cập nhật | High |
| TC-BP02-010 | BP-02 – Quản lý Driver | Negative | Latitude vượt phạm vi | Driver đã login | 1. Cập nhật vị trí | latitude=91 | Từ chối | High |
| TC-BP02-011 | BP-02 – Quản lý Driver | Boundary | Latitude = 90 | Driver đã login | 1. Cập nhật vị trí | lat=90 | Chấp nhận tọa độ biên | Medium |
| TC-BP02-012 | BP-02 – Quản lý Driver | Boundary | Longitude = -180 | Driver đã login | 1. Cập nhật vị trí | lon=-180 | Chấp nhận tọa độ biên | Medium |
| TC-BP02-013 | BP-02 – Quản lý Driver | Boundary | Gửi lại AVAILABLE khi đã AVAILABLE | Driver đang AVAILABLE | 1. PUT status AVAILABLE | AVAILABLE | Trạng thái vẫn nhất quán | Medium |
| TC-BP02-014 | BP-02 – Quản lý Driver | Empty | availabilityStatus rỗng | Driver đã login | 1. PUT status | empty | Từ chối | High |
| TC-BP02-015 | BP-02 – Quản lý Driver | Empty | Latitude rỗng | Driver đã login | 1. PUT location | latitude=empty | Từ chối | High |
| TC-BP02-016 | BP-02 – Quản lý Driver | Empty | Không token khi xem Vehicle | Chưa xác thực | 1. GET vehicles | Authorization=empty | Từ chối | High |
| TC-BP02-017 | BP-02 – Quản lý Driver | Invalid Format/Type | Status ngoài enum | Driver đã login | 1. PUT status | BUSY | Từ chối | High |
| TC-BP02-018 | BP-02 – Quản lý Driver | Invalid Format/Type | Latitude là chữ | Driver đã login | 1. PUT location | latitude=abc | Từ chối | High |
| TC-BP02-019 | BP-02 – Quản lý Driver | Invalid Format/Type | Longitude là object | Driver đã login | 1. PUT location | longitude={} | Từ chối | High |
| TC-BP02-020 | BP-02 – Quản lý Driver | Invalid Format/Type | Token malformed | Driver chưa xác thực hợp lệ | 1. GET profile | Bearer abc | Từ chối | High |

## BP-03 – Tạo yêu cầu đặt xe

**Traceability:** FR11–FR15 → AC11–AC15

| Test Case ID | Test Scenario | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| TC-BP03-001 | BP-03 – Tạo yêu cầu đặt xe | Positive | Nhập điểm đón hợp lệ | Customer đã login | 1. Nhập pickup | 268 Lý Thường Kiệt, Q10 | Chấp nhận điểm đón | Medium |
| TC-BP03-002 | BP-03 – Tạo yêu cầu đặt xe | Positive | Nhập điểm đến hợp lệ | Customer đã login | 1. Nhập destination | 12 Nguyễn Huệ, Q1 | Chấp nhận điểm đến | Medium |
| TC-BP03-003 | BP-03 – Tạo yêu cầu đặt xe | Positive | Xem lại thông tin trước khi tạo Trip | Đã nhập đủ dữ liệu | 1. Nhập pickup/destination/type<br>2. Review | Dữ liệu hợp lệ | Hiển thị đúng thông tin đã nhập | Medium |
| TC-BP03-004 | BP-03 – Tạo yêu cầu đặt xe | Positive | Tạo Trip hợp lệ | Customer không có Trip active | 1. Nhập đủ dữ liệu<br>2. Tạo Trip | Pickup/destination/tọa độ/vehicleTypeId hợp lệ | Tạo Trip với trạng thái CREATED | High |
| TC-BP03-005 | BP-03 – Tạo yêu cầu đặt xe | Positive | Hủy Trip khi chính sách cho phép | Trip ở trạng thái được phép hủy | 1. Chọn hủy | tripId hợp lệ | Trip chuyển CANCELLED | High |
| TC-BP03-006 | BP-03 – Tạo yêu cầu đặt xe | Negative | Tạo Trip thứ hai khi có Trip active | Customer đang có Trip active | 1. POST Trip mới | Dữ liệu hợp lệ | Từ chối theo RULE-02 | High |
| TC-BP03-007 | BP-03 – Tạo yêu cầu đặt xe | Negative | VehicleType không tồn tại | Customer đã login | 1. Tạo Trip | vehicleTypeId=VT999 | Không tạo Trip | High |
| TC-BP03-008 | BP-03 – Tạo yêu cầu đặt xe | Negative | Hủy Trip của Customer khác | Trip thuộc user khác | 1. Gọi cancel | tripId của user khác | Từ chối quyền | High |
| TC-BP03-009 | BP-03 – Tạo yêu cầu đặt xe | Boundary | Latitude điểm đón = 90 | Customer đã login | 1. Tạo Trip | pickupLatitude=90 | Chấp nhận biên địa lý | Medium |
| TC-BP03-010 | BP-03 – Tạo yêu cầu đặt xe | Boundary | Longitude điểm đón = 180 | Customer đã login | 1. Tạo Trip | pickupLongitude=180 | Chấp nhận biên địa lý | Medium |
| TC-BP03-011 | BP-03 – Tạo yêu cầu đặt xe | Boundary | Customer vừa hoàn tất Trip cũ rồi tạo Trip mới | Không còn Trip active | 1. Complete Trip cũ<br>2. Tạo Trip mới | Dữ liệu hợp lệ | Cho phép tạo Trip mới | Medium |
| TC-BP03-012 | BP-03 – Tạo yêu cầu đặt xe | Boundary | Hủy tại trạng thái biên chính sách | Policy hủy đã được chốt | 1. Cancel Trip | Trạng thái biên=TBD | Xử lý đúng policy đã phê duyệt | Medium |
| TC-BP03-013 | BP-03 – Tạo yêu cầu đặt xe | Empty | Pickup address rỗng | Customer đã login | 1. POST Trip | pickupAddress=empty | Không tạo Trip | High |
| TC-BP03-014 | BP-03 – Tạo yêu cầu đặt xe | Empty | Destination address rỗng | Customer đã login | 1. POST Trip | destinationAddress=empty | Không tạo Trip | High |
| TC-BP03-015 | BP-03 – Tạo yêu cầu đặt xe | Empty | vehicleTypeId rỗng | Customer đã login | 1. POST Trip | vehicleTypeId=empty | Không tạo Trip | High |
| TC-BP03-016 | BP-03 – Tạo yêu cầu đặt xe | Empty | Body tạo Trip rỗng | Customer đã login | 1. POST Trip | {} | Validation error | High |
| TC-BP03-017 | BP-03 – Tạo yêu cầu đặt xe | Invalid Format/Type | pickupLatitude là chữ | Customer đã login | 1. POST Trip | pickupLatitude=abc | Từ chối | High |
| TC-BP03-018 | BP-03 – Tạo yêu cầu đặt xe | Invalid Format/Type | destinationLongitude là object | Customer đã login | 1. POST Trip | destinationLongitude={} | Từ chối | High |
| TC-BP03-019 | BP-03 – Tạo yêu cầu đặt xe | Invalid Format/Type | tripId cancel không tồn tại | Customer đã login | 1. Cancel Trip | TRIP999 | Báo không tìm thấy | High |
| TC-BP03-020 | BP-03 – Tạo yêu cầu đặt xe | Invalid Format/Type | Token sai format khi tạo Trip | Customer chưa xác thực hợp lệ | 1. POST Trip | Bearer abc | Từ chối | High |

## BP-04 – Lựa chọn loại xe

**Traceability:** FR16–FR17 → AC16–AC17

| Test Case ID | Test Scenario | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| TC-BP04-001 | BP-04 – Lựa chọn loại xe | Positive | Xem danh sách Vehicle Type | Customer đã login | 1. GET vehicle-types | Token hợp lệ | Trả danh sách Vehicle Type hỗ trợ | High |
| TC-BP04-002 | BP-04 – Lựa chọn loại xe | Positive | Chọn một Vehicle Type hợp lệ | Danh sách có dữ liệu | 1. Chọn loại xe | VT001 | Lưu lựa chọn hợp lệ | High |
| TC-BP04-003 | BP-04 – Lựa chọn loại xe | Positive | Tạo Trip với Vehicle Type đã chọn | Customer không có Trip active | 1. Chọn type<br>2. Tạo Trip | VT001 | Trip liên kết đúng Vehicle Type | High |
| TC-BP04-004 | BP-04 – Lựa chọn loại xe | Positive | Xem đúng thông tin cơ bản Vehicle Type | Có Vehicle Type | 1. Mở danh sách | VT001 | Hiển thị đúng dữ liệu type | Medium |
| TC-BP04-005 | BP-04 – Lựa chọn loại xe | Negative | Chọn Vehicle Type không tồn tại | Customer đã login | 1. Gửi type không tồn tại | VT999 | Từ chối | High |
| TC-BP04-006 | BP-04 – Lựa chọn loại xe | Negative | Customer không xác thực xem Vehicle Type | Không token | 1. GET vehicle-types | Authorization absent | Từ chối theo API bảo vệ | High |
| TC-BP04-007 | BP-04 – Lựa chọn loại xe | Negative | Sử dụng Vehicle Type không hợp lệ để tạo Trip | Customer đã login | 1. POST Trip | vehicleTypeId invalid | Không tạo Trip | High |
| TC-BP04-008 | BP-04 – Lựa chọn loại xe | Negative | Sử dụng Vehicle Type đã không còn được hệ thống hỗ trợ | Type không khả dụng theo dữ liệu hiện tại | 1. Tạo Trip | type không hợp lệ | Từ chối | High |
| TC-BP04-009 | BP-04 – Lựa chọn loại xe | Boundary | Danh sách có đúng 1 Vehicle Type | Hệ thống có 1 type | 1. GET vehicle-types | 1 item | Trả đúng 1 phần tử | Medium |
| TC-BP04-010 | BP-04 – Lựa chọn loại xe | Boundary | Danh sách Vehicle Type rỗng | Không có type được cấu hình | 1. GET vehicle-types | 0 item | Trả danh sách rỗng, không lỗi | Medium |
| TC-BP04-011 | BP-04 – Lựa chọn loại xe | Boundary | Chọn lại cùng một Vehicle Type trước khi tạo Trip | Customer đang nhập booking | 1. Chọn VT001 hai lần | VT001 | Lựa chọn cuối nhất quán | Low |
| TC-BP04-012 | BP-04 – Lựa chọn loại xe | Boundary | Đổi Vehicle Type trước khi xác nhận Trip | Có ít nhất 2 type | 1. Chọn VT001<br>2. Đổi VT002<br>3. Tạo Trip | VT002 | Trip dùng lựa chọn cuối VT002 | Medium |
| TC-BP04-013 | BP-04 – Lựa chọn loại xe | Empty | vehicleTypeId rỗng khi tạo Trip | Customer đã login | 1. POST Trip | vehicleTypeId=empty | Từ chối | High |
| TC-BP04-014 | BP-04 – Lựa chọn loại xe | Empty | Không có token khi lấy danh sách | Chưa login | 1. GET vehicle-types | empty token | Từ chối | High |
| TC-BP04-015 | BP-04 – Lựa chọn loại xe | Empty | Vehicle Type list không có phần tử | Dữ liệu type rỗng | 1. GET list | [] | Hiển thị trạng thái không có loại xe | Medium |
| TC-BP04-016 | BP-04 – Lựa chọn loại xe | Empty | Body Trip thiếu vehicleTypeId | Customer đã login | 1. POST Trip | không có vehicleTypeId | Validation error | High |
| TC-BP04-017 | BP-04 – Lựa chọn loại xe | Invalid Format/Type | vehicleTypeId sai kiểu | Customer đã login | 1. POST Trip | vehicleTypeId=[] | Từ chối | High |
| TC-BP04-018 | BP-04 – Lựa chọn loại xe | Invalid Format/Type | vehicleTypeId sai định dạng | Customer đã login | 1. POST Trip | @@@ | Từ chối/không tìm thấy | High |
| TC-BP04-019 | BP-04 – Lựa chọn loại xe | Invalid Format/Type | Token malformed khi xem type | Có token sai | 1. GET list | Bearer abc | Từ chối | High |
| TC-BP04-020 | BP-04 – Lựa chọn loại xe | Invalid Format/Type | Request không đúng API contract | Customer đã login | 1. Gửi request sai schema | Sai schema | API trả lỗi phù hợp | High |

## BP-05 – Tìm và lựa chọn Driver

**Traceability:** FR18–FR21 → AC18–AC21

| Test Case ID | Test Scenario | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| TC-BP05-001 | BP-05 – Tìm và lựa chọn Driver | Positive | Xem Driver AVAILABLE đúng Vehicle Type | Trip CREATED | 1. GET available drivers | vehicleTypeId=VT001 | Chỉ trả Driver phù hợp | High |
| TC-BP05-002 | BP-05 – Tìm và lựa chọn Driver | Positive | Xem thông tin cơ bản Driver | Có Driver phù hợp | 1. Xem danh sách | DRV001 | Hiển thị thông tin cơ bản Driver | Medium |
| TC-BP05-003 | BP-05 – Tìm và lựa chọn Driver | Positive | Chọn Driver hợp lệ | Driver AVAILABLE và đúng type | 1. Chọn Driver | DRV001 | Chọn Driver thành công | High |
| TC-BP05-004 | BP-05 – Tìm và lựa chọn Driver | Positive | Gửi TripOffer tới Driver đã chọn | Driver hợp lệ | 1. POST driver-selection | DRV001 | Tạo TripOffer PENDING; Trip DRIVER_SELECTED | High |
| TC-BP05-005 | BP-05 – Tìm và lựa chọn Driver | Negative | Chọn Driver UNAVAILABLE | Driver UNAVAILABLE | 1. Chọn Driver | DRV002 | Từ chối RULE-03 | High |
| TC-BP05-006 | BP-05 – Tìm và lựa chọn Driver | Negative | Chọn Driver đang có Trip active | Driver đang bận | 1. Chọn Driver | DRV003 | Từ chối RULE-04 | High |
| TC-BP05-007 | BP-05 – Tìm và lựa chọn Driver | Negative | Chọn Driver sai Vehicle Type | Driver type khác | 1. Chọn Driver | DRV004 | Từ chối RULE-05 | High |
| TC-BP05-008 | BP-05 – Tìm và lựa chọn Driver | Negative | Chọn Driver khi Trip không ở trạng thái hợp lệ | Trip không cho chọn Driver | 1. POST selection | DRV001 | Từ chối | High |
| TC-BP05-009 | BP-05 – Tìm và lựa chọn Driver | Boundary | Không có Driver phù hợp | 0 Driver AVAILABLE đúng type | 1. GET available | VT001 | Trả danh sách rỗng | Medium |
| TC-BP05-010 | BP-05 – Tìm và lựa chọn Driver | Boundary | Có đúng 1 Driver phù hợp | 1 Driver hợp lệ | 1. GET available | VT001 | Trả đúng 1 Driver | Medium |
| TC-BP05-011 | BP-05 – Tìm và lựa chọn Driver | Boundary | Có nhiều Driver phù hợp | Nhiều Driver hợp lệ | 1. GET available | VT001 | Trả các Driver hợp lệ; Customer tự chọn | Medium |
| TC-BP05-012 | BP-05 – Tìm và lựa chọn Driver | Boundary | Driver vừa chuyển AVAILABLE | Driver đáp ứng type | 1. Cập nhật Driver AVAILABLE<br>2. GET list | DRV001 | Driver xuất hiện nếu đáp ứng điều kiện | Medium |
| TC-BP05-013 | BP-05 – Tìm và lựa chọn Driver | Empty | vehicleTypeId rỗng | Customer đã login | 1. GET available | empty | Từ chối | High |
| TC-BP05-014 | BP-05 – Tìm và lựa chọn Driver | Empty | driverId rỗng | Trip hợp lệ | 1. POST selection | driverId=empty | Không tạo offer | High |
| TC-BP05-015 | BP-05 – Tìm và lựa chọn Driver | Empty | tripId rỗng | Customer đã login | 1. Gọi selection thiếu tripId | empty | Không xử lý hợp lệ | High |
| TC-BP05-016 | BP-05 – Tìm và lựa chọn Driver | Empty | Không token | Chưa xác thực | 1. GET available | Authorization=empty | Từ chối | High |
| TC-BP05-017 | BP-05 – Tìm và lựa chọn Driver | Invalid Format/Type | driverId không tồn tại | Trip hợp lệ | 1. POST selection | DRV999 | Từ chối | High |
| TC-BP05-018 | BP-05 – Tìm và lựa chọn Driver | Invalid Format/Type | vehicleTypeId sai kiểu | Customer đã login | 1. GET available | vehicleTypeId=[] | Từ chối | High |
| TC-BP05-019 | BP-05 – Tìm và lựa chọn Driver | Invalid Format/Type | tripId sai format | Customer đã login | 1. POST selection | tripId=@@@ | Từ chối/không tìm thấy | High |
| TC-BP05-020 | BP-05 – Tìm và lựa chọn Driver | Invalid Format/Type | Token malformed | Chưa xác thực hợp lệ | 1. GET available | Bearer abc | Từ chối | High |

## BP-06 – Driver tiếp nhận và phản hồi yêu cầu chuyến

**Traceability:** FR22–FR25 → AC22–AC25

| Test Case ID | Test Scenario | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| TC-BP06-001 | BP-06 – Driver tiếp nhận và phản hồi yêu cầu chuyến | Positive | Driver xem TripOffer PENDING của mình | Driver đã login và có offer | 1. GET trip-offers | Token Driver | Hiển thị đúng offer | High |
| TC-BP06-002 | BP-06 – Driver tiếp nhận và phản hồi yêu cầu chuyến | Positive | Driver ACCEPTED TripOffer | Offer PENDING; Driver hợp lệ | 1. PUT response ACCEPTED | ACCEPTED | Driver được gán; Trip DRIVER_ASSIGNED | High |
| TC-BP06-003 | BP-06 – Driver tiếp nhận và phản hồi yêu cầu chuyến | Positive | Driver REJECTED TripOffer | Offer PENDING | 1. PUT response REJECTED | REJECTED | Không gán Driver | High |
| TC-BP06-004 | BP-06 – Driver tiếp nhận và phản hồi yêu cầu chuyến | Positive | Customer chọn Driver khác sau reject | Offer trước đã REJECTED | 1. Customer xem lại Driver<br>2. Chọn Driver khác | DRV002 | Cho phép tiếp tục lựa chọn | High |
| TC-BP06-005 | BP-06 – Driver tiếp nhận và phản hồi yêu cầu chuyến | Negative | Driver khác phản hồi offer không thuộc mình | Offer thuộc Driver A | 1. Driver B PUT response | offerId của A | Từ chối quyền | High |
| TC-BP06-006 | BP-06 – Driver tiếp nhận và phản hồi yêu cầu chuyến | Negative | Phản hồi offer đã ACCEPTED | Offer đã xử lý | 1. PUT response | ACCEPTED | Từ chối phản hồi lại | High |
| TC-BP06-007 | BP-06 – Driver tiếp nhận và phản hồi yêu cầu chuyến | Negative | Phản hồi offer đã REJECTED | Offer đã xử lý | 1. PUT response | REJECTED | Từ chối phản hồi lại | High |
| TC-BP06-008 | BP-06 – Driver tiếp nhận và phản hồi yêu cầu chuyến | Negative | ACCEPT khi Driver không còn AVAILABLE | Driver vừa đổi trạng thái | 1. PUT ACCEPTED | ACCEPTED | Từ chối nếu không còn hợp lệ | High |
| TC-BP06-009 | BP-06 – Driver tiếp nhận và phản hồi yêu cầu chuyến | Boundary | Driver có 0 TripOffer | Không có offer | 1. GET offers | 0 item | Trả danh sách rỗng | Medium |
| TC-BP06-010 | BP-06 – Driver tiếp nhận và phản hồi yêu cầu chuyến | Boundary | Driver có đúng 1 offer PENDING | Có 1 offer | 1. GET offers | 1 item | Trả đúng 1 offer | Medium |
| TC-BP06-011 | BP-06 – Driver tiếp nhận và phản hồi yêu cầu chuyến | Boundary | Offer chỉ được phản hồi một lần | Offer PENDING | 1. ACCEPT<br>2. ACCEPT lại | cùng offerId | Lần đầu hợp lệ; lần sau từ chối | High |
| TC-BP06-012 | BP-06 – Driver tiếp nhận và phản hồi yêu cầu chuyến | Boundary | Reject rồi Customer chọn Driver khác | Offer 1 REJECTED | 1. Reject<br>2. Customer chọn Driver 2 | Driver 2 | Luồng chọn Driver tiếp tục đúng | Medium |
| TC-BP06-013 | BP-06 – Driver tiếp nhận và phản hồi yêu cầu chuyến | Empty | response rỗng | Offer PENDING | 1. PUT response | response=empty | Từ chối | High |
| TC-BP06-014 | BP-06 – Driver tiếp nhận và phản hồi yêu cầu chuyến | Empty | offerId rỗng | Driver login | 1. Gọi response thiếu ID | empty | Không xử lý hợp lệ | High |
| TC-BP06-015 | BP-06 – Driver tiếp nhận và phản hồi yêu cầu chuyến | Empty | Body response rỗng | Offer PENDING | 1. PUT {} | {} | Validation error | High |
| TC-BP06-016 | BP-06 – Driver tiếp nhận và phản hồi yêu cầu chuyến | Empty | Không token | Chưa xác thực | 1. GET offers | Authorization=empty | Từ chối | High |
| TC-BP06-017 | BP-06 – Driver tiếp nhận và phản hồi yêu cầu chuyến | Invalid Format/Type | response ngoài enum | Offer PENDING | 1. PUT response | MAYBE | Từ chối | High |
| TC-BP06-018 | BP-06 – Driver tiếp nhận và phản hồi yêu cầu chuyến | Invalid Format/Type | response dạng số | Offer PENDING | 1. PUT response | 1 | Từ chối | High |
| TC-BP06-019 | BP-06 – Driver tiếp nhận và phản hồi yêu cầu chuyến | Invalid Format/Type | offerId không tồn tại | Driver login | 1. PUT response | OFF999 | Báo không tìm thấy | High |
| TC-BP06-020 | BP-06 – Driver tiếp nhận và phản hồi yêu cầu chuyến | Invalid Format/Type | Token malformed | Driver chưa xác thực hợp lệ | 1. GET offers | Bearer abc | Từ chối | High |

## BP-07 – Theo dõi và thực hiện Trip

**Traceability:** FR26–FR32 → AC26–AC32

| Test Case ID | Test Scenario | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| TC-BP07-001 | BP-07 – Theo dõi và thực hiện Trip | Positive | Customer xem Driver đã chấp nhận | Trip DRIVER_ASSIGNED | 1. GET Trip | TRIP001 | Hiển thị đúng Driver | High |
| TC-BP07-002 | BP-07 – Theo dõi và thực hiện Trip | Positive | Customer xem trạng thái Trip hiện tại | Trip thuộc Customer | 1. GET Trip | TRIP001 | Hiển thị đúng status | High |
| TC-BP07-003 | BP-07 – Theo dõi và thực hiện Trip | Positive | Driver xác nhận đã đến | Trip DRIVER_ASSIGNED | 1. PUT status | DRIVER_ARRIVED | Chuyển DRIVER_ARRIVED | High |
| TC-BP07-004 | BP-07 – Theo dõi và thực hiện Trip | Positive | Driver xác nhận đã đón khách | Trip DRIVER_ARRIVED | 1. PUT status | PASSENGER_PICKED_UP | Chuyển PASSENGER_PICKED_UP | High |
| TC-BP07-005 | BP-07 – Theo dõi và thực hiện Trip | Positive | Driver bắt đầu Trip | Trip PASSENGER_PICKED_UP | 1. PUT status | IN_PROGRESS | Chuyển IN_PROGRESS | High |
| TC-BP07-006 | BP-07 – Theo dõi và thực hiện Trip | Positive | Driver hoàn thành Trip | Trip IN_PROGRESS | 1. PUT status | COMPLETED | Chuyển COMPLETED | High |
| TC-BP07-007 | BP-07 – Theo dõi và thực hiện Trip | Positive | Hủy Trip theo chính sách | Trip ở trạng thái cho phép | 1. PUT cancel | TRIP001 | Trip CANCELLED | High |
| TC-BP07-008 | BP-07 – Theo dõi và thực hiện Trip | Negative | Nhảy DRIVER_ASSIGNED → COMPLETED | Trip DRIVER_ASSIGNED | 1. PUT status COMPLETED | COMPLETED | Từ chối RULE-09 | High |
| TC-BP07-009 | BP-07 – Theo dõi và thực hiện Trip | Negative | Driver khác cập nhật Trip | Trip thuộc Driver A | 1. Driver B PUT status | TRIP001 | Từ chối NFR-07 | High |
| TC-BP07-010 | BP-07 – Theo dõi và thực hiện Trip | Negative | Customer cập nhật trạng thái bằng API Driver | Customer login | 1. PUT status | IN_PROGRESS | Từ chối quyền | High |
| TC-BP07-011 | BP-07 – Theo dõi và thực hiện Trip | Boundary | Trip CREATED chưa có Driver | Trip vừa tạo | 1. GET Trip | driver=null | Trả Trip hợp lệ; Driver có thể null | Medium |
| TC-BP07-012 | BP-07 – Theo dõi và thực hiện Trip | Boundary | Bước đầu DRIVER_ASSIGNED → DRIVER_ARRIVED | Trip DRIVER_ASSIGNED | 1. PUT status | DRIVER_ARRIVED | Chấp nhận | Medium |
| TC-BP07-013 | BP-07 – Theo dõi và thực hiện Trip | Boundary | Bước cuối IN_PROGRESS → COMPLETED | Trip IN_PROGRESS | 1. PUT status | COMPLETED | Chấp nhận | Medium |
| TC-BP07-014 | BP-07 – Theo dõi và thực hiện Trip | Boundary | Trip đã COMPLETED cập nhật tiếp | Trip COMPLETED | 1. PUT status | IN_PROGRESS | Không cho quay lại trạng thái trước | High |
| TC-BP07-015 | BP-07 – Theo dõi và thực hiện Trip | Empty | status rỗng | Trip thuộc Driver | 1. PUT status | empty | Từ chối | High |
| TC-BP07-016 | BP-07 – Theo dõi và thực hiện Trip | Empty | tripId rỗng | User login | 1. Gọi endpoint thiếu ID | empty | Không xử lý hợp lệ | High |
| TC-BP07-017 | BP-07 – Theo dõi và thực hiện Trip | Invalid Format/Type | status ngoài lifecycle | Trip thuộc Driver | 1. PUT status | RUNNING | Từ chối | High |
| TC-BP07-018 | BP-07 – Theo dõi và thực hiện Trip | Invalid Format/Type | status dạng số | Trip thuộc Driver | 1. PUT status | 1 | Từ chối | High |
| TC-BP07-019 | BP-07 – Theo dõi và thực hiện Trip | Invalid Format/Type | tripId không tồn tại | User login | 1. GET/PUT Trip | TRIP999 | Báo không tìm thấy | High |
| TC-BP07-020 | BP-07 – Theo dõi và thực hiện Trip | Invalid Format/Type | Token malformed | Trip tồn tại | 1. GET Trip | Bearer abc | Từ chối | High |

## BP-08 – Tính cước và thanh toán

**Traceability:** FR33–FR38 → AC33–AC38

| Test Case ID | Test Scenario | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| TC-BP08-001 | BP-08 – Tính cước và thanh toán | Positive | Ghi finalFare sau khi Trip COMPLETED | Trip vừa COMPLETED | 1. Hoàn thành Trip<br>2. GET Trip | TRIP001 | finalFare được ghi nhận | High |
| TC-BP08-002 | BP-08 – Tính cước và thanh toán | Positive | Customer xem cước | Trip COMPLETED có finalFare | 1. GET Trip | TRIP001 | Hiển thị đúng finalFare | High |
| TC-BP08-003 | BP-08 – Tính cước và thanh toán | Positive | Customer chọn CASH | Trip COMPLETED | 1. Chọn CASH<br>2. Thanh toán | CASH | Chấp nhận phương thức | High |
| TC-BP08-004 | BP-08 – Tính cước và thanh toán | Positive | Thanh toán CASH thành công | Trip COMPLETED | 1. POST payment | CASH | Lưu Payment liên kết đúng Trip | High |
| TC-BP08-005 | BP-08 – Tính cước và thanh toán | Positive | Customer chọn ELECTRONIC | Trip COMPLETED | 1. Chọn ELECTRONIC | ELECTRONIC | Chấp nhận phương thức | High |
| TC-BP08-006 | BP-08 – Tính cước và thanh toán | Positive | Thanh toán ELECTRONIC thành công | Provider hoạt động | 1. POST payment | ELECTRONIC | Xử lý và lưu kết quả giao dịch | High |
| TC-BP08-007 | BP-08 – Tính cước và thanh toán | Negative | Thanh toán khi Trip chưa COMPLETED | Trip IN_PROGRESS | 1. POST payment | CASH | Từ chối | High |
| TC-BP08-008 | BP-08 – Tính cước và thanh toán | Negative | Customer khác thanh toán Trip | Trip thuộc user khác | 1. POST payment | CASH | Từ chối quyền | High |
| TC-BP08-009 | BP-08 – Tính cước và thanh toán | Negative | Trip COMPLETED nhưng finalFare chưa có | Dữ liệu không hợp lệ | 1. POST payment | CASH | Không tạo Payment | High |
| TC-BP08-010 | BP-08 – Tính cước và thanh toán | Negative | Payment method không hỗ trợ | Trip COMPLETED | 1. POST payment | CRYPTO | Từ chối RULE-11 | High |
| TC-BP08-011 | BP-08 – Tính cước và thanh toán | Boundary | Ngay trước COMPLETED | Trip IN_PROGRESS | 1. GET Trip | finalFare | finalFare chưa được ghi theo RULE-10 | Medium |
| TC-BP08-012 | BP-08 – Tính cước và thanh toán | Boundary | Ngay sau COMPLETED | Trip vừa COMPLETED | 1. GET Trip | finalFare | finalFare được ghi nhận | Medium |
| TC-BP08-013 | BP-08 – Tính cước và thanh toán | Boundary | Nhiều lần thử payment | Có lần payment trước | 1. Thử payment tiếp | Trip giống nhau | Lưu/xử lý nhất quán theo thiết kế | Medium |
| TC-BP08-014 | BP-08 – Tính cước và thanh toán | Boundary | Amount phải lấy từ finalFare | Trip COMPLETED | 1. POST payment | Không gửi amount | Payment amount bằng finalFare | High |
| TC-BP08-015 | BP-08 – Tính cước và thanh toán | Empty | method rỗng | Trip COMPLETED | 1. POST payment | method=empty | Từ chối | High |
| TC-BP08-016 | BP-08 – Tính cước và thanh toán | Empty | Body payment rỗng | Trip COMPLETED | 1. POST payment | {} | Validation error | High |
| TC-BP08-017 | BP-08 – Tính cước và thanh toán | Empty | tripId rỗng | Customer login | 1. Gọi payment thiếu tripId | empty | Không xử lý hợp lệ | High |
| TC-BP08-018 | BP-08 – Tính cước và thanh toán | Invalid Format/Type | method dạng số | Trip COMPLETED | 1. POST payment | method=1 | Từ chối | High |
| TC-BP08-019 | BP-08 – Tính cước và thanh toán | Invalid Format/Type | Client gửi dữ liệu payment nhạy cảm ngoài contract | Trip COMPLETED | 1. POST payment với field ngoài spec | cardNumber/CVV | Không lưu dữ liệu nhạy cảm; tuân RULE-12 | High |
| TC-BP08-020 | BP-08 – Tính cước và thanh toán | Invalid Format/Type | tripId không tồn tại | Customer login | 1. POST payment | TRIP999 | Báo không tìm thấy | High |

## BP-09 – Lịch sử chuyến và đánh giá Driver

**Traceability:** FR39–FR42 → AC39–AC42

| Test Case ID | Test Scenario | Nhóm kiểm thử | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| TC-BP09-001 | BP-09 – Lịch sử chuyến và đánh giá Driver | Positive | Customer xem lịch sử Trip | Customer có lịch sử | 1. GET /users/me/trips | Token hợp lệ | Trả các Trip của Customer | High |
| TC-BP09-002 | BP-09 – Lịch sử chuyến và đánh giá Driver | Positive | Customer xem chi tiết Trip lịch sử | Trip thuộc Customer | 1. GET Trip detail | TRIP001 | Hiển thị đúng chi tiết | Medium |
| TC-BP09-003 | BP-09 – Lịch sử chuyến và đánh giá Driver | Positive | Customer đánh giá Driver sau COMPLETED | Trip COMPLETED; chưa Rating | 1. POST rating | score hợp lệ; comment=Good | Tạo Rating | High |
| TC-BP09-004 | BP-09 – Lịch sử chuyến và đánh giá Driver | Positive | Customer xem Rating đã gửi | Trip có Rating | 1. GET rating | TRIP001 | Trả đúng Rating | Medium |
| TC-BP09-005 | BP-09 – Lịch sử chuyến và đánh giá Driver | Negative | Customer xem Trip của người khác | Trip thuộc user khác | 1. GET detail | TRIP_OTHER | Từ chối NFR-06 | High |
| TC-BP09-006 | BP-09 – Lịch sử chuyến và đánh giá Driver | Negative | Đánh giá trước khi Trip COMPLETED | Trip IN_PROGRESS | 1. POST rating | score hợp lệ | Từ chối RULE-14 | High |
| TC-BP09-007 | BP-09 – Lịch sử chuyến và đánh giá Driver | Negative | Đánh giá Trip của Customer khác | Trip thuộc user khác | 1. POST rating | score hợp lệ | Từ chối RULE-13 | High |
| TC-BP09-008 | BP-09 – Lịch sử chuyến và đánh giá Driver | Negative | Đánh giá lần hai cùng Trip | Trip đã có Rating | 1. POST rating lần 2 | score hợp lệ | Từ chối RULE-15 | High |
| TC-BP09-009 | BP-09 – Lịch sử chuyến và đánh giá Driver | Boundary | Customer chưa có Trip lịch sử | 0 Trip | 1. GET history | 0 item | Trả danh sách rỗng | Medium |
| TC-BP09-010 | BP-09 – Lịch sử chuyến và đánh giá Driver | Boundary | Customer có đúng 1 Trip lịch sử | 1 Trip | 1. GET history | 1 item | Trả đúng 1 Trip | Medium |
| TC-BP09-011 | BP-09 – Lịch sử chuyến và đánh giá Driver | Boundary | Rating đầu tiên của Trip | Trip COMPLETED chưa Rating | 1. POST rating | score hợp lệ | Tạo thành công | Medium |
| TC-BP09-012 | BP-09 – Lịch sử chuyến và đánh giá Driver | Boundary | Score tại min/max của thang điểm | Thang điểm được chốt | 1. POST rating | min/max=TBD | Xử lý đúng rule thang điểm | Medium |
| TC-BP09-013 | BP-09 – Lịch sử chuyến và đánh giá Driver | Empty | Không token khi xem history | Chưa login | 1. GET history | Authorization=empty | Từ chối | High |
| TC-BP09-014 | BP-09 – Lịch sử chuyến và đánh giá Driver | Empty | score rỗng | Trip COMPLETED | 1. POST rating | score=empty | Từ chối | High |
| TC-BP09-015 | BP-09 – Lịch sử chuyến và đánh giá Driver | Empty | comment rỗng | Trip COMPLETED | 1. POST rating | score hợp lệ; comment=empty | Xử lý theo API; comment không được SRS quy định bắt buộc | Medium |
| TC-BP09-016 | BP-09 – Lịch sử chuyến và đánh giá Driver | Empty | Trip chưa có Rating khi GET | Trip thuộc Customer | 1. GET rating | TRIP001 | Báo Rating không tồn tại | Medium |
| TC-BP09-017 | BP-09 – Lịch sử chuyến và đánh giá Driver | Invalid Format/Type | score là chữ | Trip COMPLETED | 1. POST rating | score=five | Từ chối | High |
| TC-BP09-018 | BP-09 – Lịch sử chuyến và đánh giá Driver | Invalid Format/Type | score là object/array | Trip COMPLETED | 1. POST rating | score={} | Từ chối | High |
| TC-BP09-019 | BP-09 – Lịch sử chuyến và đánh giá Driver | Invalid Format/Type | tripId không tồn tại | Customer login | 1. GET/POST rating | TRIP999 | Báo không tìm thấy | High |
| TC-BP09-020 | BP-09 – Lịch sử chuyến và đánh giá Driver | Invalid Format/Type | Token malformed | Customer chưa xác thực hợp lệ | 1. GET history | Bearer abc | Từ chối | High |

## 3. Tổng hợp

- **09 Test Scenario** tương ứng với 09 Business Process của SRS hiện tại.
- **20 Test Case/Test Scenario**.
- **Tổng cộng: 180 Test Case**.
- Mỗi Test Scenario đều có các nhóm: **Positive, Negative, Boundary, Empty, Invalid Format/Type**.
- Các giới hạn chưa được SRS quy định cụ thể như độ dài trường, thang điểm Rating hoặc trạng thái biên được phép hủy được ghi **TBD** thay vì tự đặt thêm Business Rule.
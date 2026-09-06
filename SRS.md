## 3. Stakeholders

### 3.1. Danh sách Stakeholders và vai trò

Các bên liên quan đến quá trình xây dựng, vận hành và sử dụng CAB System được xác định như sau:

| STT | Stakeholder | Vai trò / Mối quan tâm |
|---|---|---|
| 1 | **Khách hàng (Customer/Passenger)** | Sử dụng hệ thống để đặt xe, theo dõi chuyến đi, thanh toán, xem lịch sử chuyến và đánh giá tài xế. Quan tâm đến tính thuận tiện, chính xác và an toàn của dịch vụ. |
| 2 | **Tài xế (Driver)** | Cập nhật hồ sơ, phương tiện, trạng thái hoạt động và vị trí; nhận hoặc từ chối yêu cầu chuyến; thực hiện và cập nhật trạng thái chuyến đi. |
| 3 | **Nhân viên vận hành (Operation Staff)** | Quản lý khách hàng, tài xế, phương tiện và chuyến đi; giám sát hoạt động và hỗ trợ xử lý các trường hợp bất thường hoặc chuyến đi gặp sự cố. |
| 4 | **Quản trị viên (Administrator)** | Quản lý tài khoản, phân quyền, kiểm soát quyền truy cập, theo dõi nhật ký và thực hiện các chức năng quản trị hệ thống. |
| 5 | **Ban lãnh đạo Công ty ABC (Management)** | Đưa ra mục tiêu và định hướng của dự án; theo dõi số lượng chuyến, doanh thu, tỷ lệ hoàn thành, tỷ lệ hủy và hiệu quả hoạt động của tài xế. |
| 6 | **Nhà cung cấp thanh toán (Payment Provider)** | Cung cấp dịch vụ thanh toán điện tử, xử lý giao dịch và trả kết quả thanh toán cho CAB System mà không yêu cầu hệ thống lưu trực tiếp thông tin thanh toán nhạy cảm. |
| 7 | **Nhà cung cấp thông báo (Notification Provider)** | Cung cấp dịch vụ gửi thông báo cho khách hàng và tài xế thông qua các kênh như Push Notification, SMS hoặc Email. |
| 8 | **Business Analyst (BA)** | Thu thập, phân tích và làm rõ yêu cầu; xác định phạm vi, quy trình nghiệp vụ, quy tắc nghiệp vụ, ngoại lệ và các vấn đề cần xác nhận với khách hàng. |
| 9 | **Nhóm phát triển (Development Team)** | Thiết kế kiến trúc, xây dựng, tích hợp và triển khai CAB System dựa trên các yêu cầu đã được thống nhất. |
| 10 | **Nhóm kiểm thử (QA/Tester)** | Kiểm thử chức năng, tích hợp, hiệu năng, bảo mật và độ ổn định nhằm đảm bảo hệ thống đáp ứng các yêu cầu đã xác định. |

---

### 3.2. Stakeholder Matrix

Stakeholders được đánh giá dựa trên hai tiêu chí:

- **Influence:** Mức độ ảnh hưởng của Stakeholder đến dự án và các quyết định của hệ thống.
- **Interest:** Mức độ quan tâm và mức độ chịu ảnh hưởng bởi kết quả của dự án.

| Stakeholder | Influence | Interest | Nhóm quản lý | Cách tương tác |
|---|---|---|---|---|
| **Ban lãnh đạo Công ty ABC** | High | High | Manage Closely | Thường xuyên trao đổi, báo cáo tiến độ và xác nhận các quyết định nghiệp vụ quan trọng. |
| **Nhân viên vận hành** | High | High | Manage Closely | Phỏng vấn và trao đổi thường xuyên để xác nhận quy trình vận hành và các trường hợp ngoại lệ. |
| **Quản trị viên** | High | High | Manage Closely | Làm rõ các yêu cầu về quản trị, phân quyền, bảo mật và kiểm soát hệ thống. |
| **Business Analyst** | High | High | Manage Closely | Phối hợp với các bên để thu thập, phân tích, quản lý và xác nhận yêu cầu. |
| **Development Team** | High | High | Manage Closely | Phối hợp với BA để đánh giá tính khả thi và triển khai các yêu cầu đã được xác nhận. |
| **Payment Provider** | High | Low | Keep Satisfied | Làm rõ API, quy trình thanh toán, bảo mật và xử lý các giao dịch thất bại. |
| **Notification Provider** | High | Low | Keep Satisfied | Làm rõ API, kênh thông báo và cơ chế tích hợp. |
| **Khách hàng** | Low | High | Keep Informed | Thu thập nhu cầu và phản hồi về đặt xe, theo dõi chuyến và thanh toán. |
| **Tài xế** | Low | High | Keep Informed | Thu thập yêu cầu và phản hồi về nhận chuyến, vị trí và trạng thái chuyến. |
| **QA/Tester** | Low | High | Keep Informed | Cập nhật thay đổi yêu cầu và phối hợp xây dựng các trường hợp kiểm thử. |

---

### 3.3. Phân loại Stakeholders theo Influence – Interest Matrix

| | **Interest thấp (Low)** | **Interest cao (High)** |
|---|---|---|
| **Influence cao (High)** | **Keep Satisfied:** Payment Provider, Notification Provider | **Manage Closely:** Management, Operation Staff, Administrator, BA, Development Team |
| **Influence thấp (Low)** | **Monitor:** Các bên hỗ trợ khác nếu phát sinh | **Keep Informed:** Customer, Driver, QA/Tester |

---

### 3.4. Sơ đồ Stakeholders

```mermaid
flowchart LR

    CAB["CAB System"]

    subgraph Internal["Stakeholders nội bộ"]
        Management["Ban lãnh đạo"]
        Operation["Nhân viên vận hành"]
        Admin["Quản trị viên"]
        BA["Business Analyst"]
        Dev["Development Team"]
        QA["QA / Tester"]
    end

    subgraph Users["Người dùng"]
        Customer["Khách hàng"]
        Driver["Tài xế"]
    end

    subgraph External["Stakeholders bên ngoài"]
        Payment["Payment Provider"]
        Notification["Notification Provider"]
    end

    Customer --> CAB
    Driver --> CAB
    Management --> CAB
    Operation --> CAB
    Admin --> CAB
    BA --> CAB
    Dev --> CAB
    QA --> CAB

    CAB <--> Payment
    CAB <--> Notification
```

---

### 3.5. Sơ đồ Stakeholder Matrix

```mermaid
quadrantChart
    title Stakeholder Influence - Interest Matrix
    x-axis Low Interest --> High Interest
    y-axis Low Influence --> High Influence

    quadrant-1 Manage Closely
    quadrant-2 Keep Satisfied
    quadrant-3 Monitor
    quadrant-4 Keep Informed

    Management: [0.90, 0.95]
    Operation Staff: [0.85, 0.90]
    Administrator: [0.80, 0.85]
    Business Analyst: [0.90, 0.90]
    Development Team: [0.85, 0.85]
    Payment Provider: [0.30, 0.75]
    Notification Provider: [0.35, 0.70]
    Customer: [0.90, 0.45]
    Driver: [0.85, 0.45]
    QA Tester: [0.75, 0.40]
```

---

## 4. Business Goals

### 4.1. Mục tiêu nghiệp vụ

Từ các yêu cầu quan trọng của Công ty ABC, các mục tiêu nghiệp vụ chính của CAB System được xác định như sau:

| Mã | Business Goal | Mô tả |
|---|---|---|
| **BG-01** | **Xây dựng nền tảng đặt xe trực tuyến toàn diện** | Hỗ trợ toàn bộ quy trình từ khi khách hàng tạo yêu cầu đặt xe, tìm tài xế, thực hiện chuyến, tính cước, thanh toán đến đánh giá sau chuyến. |
| **BG-02** | **Tự động hóa quá trình tìm và phân công tài xế** | Tự động xác định và ưu tiên tài xế phù hợp dựa trên vị trí và trạng thái sẵn sàng; tiếp tục tìm tài xế khác khi tài xế trước từ chối hoặc không phản hồi. |
| **BG-03** | **Nâng cao trải nghiệm đặt xe và theo dõi chuyến đi** | Cho phép khách hàng theo dõi tài xế, ETA và trạng thái chuyến; đồng thời nhận thông báo tại các thời điểm quan trọng. |
| **BG-04** | **Quản lý tập trung cước phí và thanh toán** | Hỗ trợ tính cước, quản lý giao dịch, thanh toán tiền mặt và thanh toán điện tử thông qua nhà cung cấp bên ngoài. |
| **BG-05** | **Nâng cao hiệu quả quản lý và vận hành dịch vụ** | Quản lý tập trung khách hàng, tài xế, phương tiện, chuyến đi và giao dịch; hỗ trợ giám sát, xử lý sự cố và báo cáo hoạt động. |
| **BG-06** | **Xây dựng nền tảng ổn định, bảo mật và có khả năng mở rộng lâu dài** | Đảm bảo hệ thống có thể phục vụ số lượng lớn người dùng, bảo vệ dữ liệu, hạn chế ảnh hưởng khi một thành phần gặp lỗi và hỗ trợ mở rộng trong tương lai. |

---

### 4.2. Chuyển đổi yêu cầu khách hàng thành Business Goals

| Yêu cầu quan trọng của khách hàng | Business Goal |
|---|---|
| Xây dựng nền tảng hỗ trợ đầy đủ quy trình đặt và thực hiện chuyến xe. | **BG-01** |
| Giảm việc phân công thủ công và tự động tìm tài xế phù hợp. | **BG-02** |
| Cho phép khách hàng theo dõi tài xế, ETA, trạng thái chuyến và nhận thông báo. | **BG-03** |
| Quản lý tập trung tính cước, giao dịch và thanh toán. | **BG-04** |
| Hỗ trợ quản lý, giám sát, xử lý sự cố và báo cáo kinh doanh. | **BG-05** |
| Đảm bảo hệ thống ổn định, bảo mật và có khả năng mở rộng. | **BG-06** |

---

### 4.3. Liên kết Business Goals với Stakeholders

| Business Goal | Stakeholders liên quan chính |
|---|---|
| **BG-01** | Customer, Driver, Operation Staff, Management |
| **BG-02** | Customer, Driver, Operation Staff |
| **BG-03** | Customer, Driver, Notification Provider |
| **BG-04** | Customer, Operation Staff, Payment Provider |
| **BG-05** | Operation Staff, Administrator, Management |
| **BG-06** | Administrator, Management, Development Team |

---

### 4.4. Ưu tiên Business Goals

| Business Goal | Mức ưu tiên | Lý do |
|---|---|---|
| **BG-01** | **Must Have** | Là mục tiêu cốt lõi để hình thành quy trình đặt xe hoàn chỉnh. |
| **BG-02** | **Must Have** | Giải quyết hạn chế phân công tài xế thủ công của hệ thống hiện tại. |
| **BG-03** | **Must Have** | Đảm bảo khách hàng và tài xế có thể theo dõi và phối hợp trong chuyến đi. |
| **BG-04** | **Must Have** | Tính cước và thanh toán cần thiết để hoàn thành chuyến đi. |
| **BG-05** | **Should Have** | Cần thiết cho vận hành, nhưng báo cáo nâng cao có thể phát triển sau. |
| **BG-06** | **Should Have** | Cần thiết về kiến trúc, bảo mật và khả năng phát triển lâu dài. |

---

## 5. Phạm vi phát triển hệ thống

### 5.1. Xác định phạm vi

Dựa trên các Business Goals và thời gian phát triển **7 tuần**, CAB System tập trung vào các module cốt lõi để hoàn thành quy trình đặt xe.

Các chức năng có độ phức tạp cao được giới hạn hoặc chuyển sang phiên bản tiếp theo nhằm đảm bảo tính khả thi của dự án.

---

### 5.2. Phạm vi các Module

| Mã | Module | BG liên quan | Phạm vi | Nội dung triển khai |
|---|---|---|---|---|
| **M01** | **User & Authentication** | BG-01, BG-06 | **In Scope** | Đăng ký, đăng nhập, cập nhật hồ sơ, xác thực và phân quyền cơ bản. |
| **M02** | **Booking Management** | BG-01 | **In Scope** | Nhập điểm đón, điểm đến, chọn loại xe và tạo yêu cầu đặt xe. |
| **M03** | **Driver & Vehicle Management** | BG-01, BG-02 | **In Scope** | Quản lý hồ sơ tài xế, phương tiện, trạng thái hoạt động và vị trí. |
| **M04** | **Driver Matching & Dispatch** | BG-02 | **In Scope** | Tìm tài xế khả dụng gần khách hàng và tìm tài xế khác khi tài xế trước từ chối hoặc không phản hồi. |
| **M05** | **Trip Management & Tracking** | BG-01, BG-03 | **In Scope** | Quản lý trạng thái chuyến từ lúc tìm tài xế đến khi hoàn thành hoặc hủy. |
| **M06** | **Fare & Payment** | BG-04 | **Limited Scope** | Tính cước cơ bản, thanh toán tiền mặt và tích hợp **01 Payment Provider**. |
| **M07** | **Notification** | BG-03 | **Limited Scope** | Thông báo các sự kiện quan trọng của chuyến qua **01 kênh thông báo chính**. |
| **M08** | **Trip History & Rating** | BG-01, BG-03 | **In Scope** | Xem lịch sử chuyến và đánh giá tài xế sau chuyến. |
| **M09** | **Operation & Administration** | BG-05, BG-06 | **In Scope** | Quản lý Customer, Driver, Vehicle, Trip; theo dõi chuyến và phân quyền quản trị cơ bản. |
| **M10** | **Reporting & Analytics** | BG-05 | **Limited Scope** | Báo cáo cơ bản về số chuyến, doanh thu, tỷ lệ hoàn thành, tỷ lệ hủy và hiệu quả tài xế. |
| **M11** | **Advanced Services & Integrations** | BG-06 | **Out of Scope** | Các dịch vụ và tích hợp nâng cao được phát triển trong phiên bản sau. |

---

### 5.3. Phân loại phạm vi

#### 5.3.1. In Scope

Các module ưu tiên phát triển:

- **M01 – User & Authentication**
- **M02 – Booking Management**
- **M03 – Driver & Vehicle Management**
- **M04 – Driver Matching & Dispatch**
- **M05 – Trip Management & Tracking**
- **M08 – Trip History & Rating**
- **M09 – Operation & Administration**

Luồng nghiệp vụ chính:

**Đặt xe → Tìm tài xế → Tài xế nhận chuyến → Thực hiện chuyến → Hoàn thành chuyến.**

#### 5.3.2. Limited Scope

- **M06 – Fare & Payment:** tính cước cơ bản, tiền mặt và **01 Payment Provider**.
- **M07 – Notification:** triển khai **01 kênh thông báo chính**.
- **M10 – Reporting & Analytics:** chỉ triển khai báo cáo cơ bản.

#### 5.3.3. Out of Scope

Các chức năng chưa triển khai trong phiên bản 7 tuần:

- Nhiều Payment Provider.
- Nhiều Notification Provider/kênh thông báo.
- AI/ML nâng cao cho Driver Matching.
- Dynamic Pricing/Surge Pricing phức tạp.
- Advanced Analytics và Business Intelligence.
- Các loại dịch vụ vận chuyển mới.
- Các tích hợp bên thứ ba nâng cao.

---

### 5.4. Liên kết Business Goals với Module

| Business Goal | Module đáp ứng |
|---|---|
| **BG-01** | M01, M02, M03, M05, M08 |
| **BG-02** | M03, M04 |
| **BG-03** | M05, M07, M08 |
| **BG-04** | M06 |
| **BG-05** | M09, M10 |
| **BG-06** | M01, M09, M11 |

---

### 5.5. Sơ đồ phạm vi Module

```mermaid
flowchart TB

    CAB["CAB System<br/>Phạm vi phát triển 7 tuần"]

    CAB --> CORE["In Scope"]
    CAB --> LIMITED["Limited Scope"]
    CAB --> FUTURE["Out of Scope / Future"]

    CORE --> M01["M01<br/>User & Authentication"]
    CORE --> M02["M02<br/>Booking Management"]
    CORE --> M03["M03<br/>Driver & Vehicle"]
    CORE --> M04["M04<br/>Driver Matching"]
    CORE --> M05["M05<br/>Trip & Tracking"]
    CORE --> M08["M08<br/>Trip History & Rating"]
    CORE --> M09["M09<br/>Operation & Admin"]

    LIMITED --> M06["M06<br/>Fare & Payment"]
    LIMITED --> M07["M07<br/>Notification"]
    LIMITED --> M10["M10<br/>Basic Reporting"]

    FUTURE --> M11["M11<br/>Advanced Services<br/>& Integrations"]
```

---

### 5.6. Kết luận phạm vi

Trong thời gian phát triển **7 tuần**, dự án ưu tiên hoàn thiện các chức năng cần thiết để thực hiện luồng đặt xe cốt lõi.

Các chức năng thanh toán, thông báo và báo cáo được giới hạn ở mức cơ bản để đảm bảo tính khả thi. Các chức năng nâng cao được đưa ra ngoài phạm vi phiên bản đầu tiên nhưng hệ thống cần được thiết kế để có thể mở rộng trong tương lai.

---

## 6. Business Requirements


### 6.1. BG-01 – Xây dựng nền tảng đặt xe trực tuyến toàn diện

| Mã Business Requirement          | Business Requirement         | Mô tả                                                                                          |
| -------------------------------- | ---------------------------- | ---------------------------------------------------------------------------------------------- |
| **BG01_QuanLyTaiKhoanKhachHang** | Quản lý tài khoản khách hàng | Cho phép khách hàng đăng ký, đăng nhập và quản lý thông tin cá nhân để sử dụng dịch vụ đặt xe. |
| **BG01_TaoYeuCauDatXe**          | Tạo yêu cầu đặt xe           | Khách hàng có thể nhập điểm đón, điểm đến, lựa chọn loại xe và gửi yêu cầu đặt xe.             |
| **BG01_QuanLyChuyenDi**          | Quản lý chuyến đi            | Hệ thống quản lý chuyến đi từ khi yêu cầu được tạo cho đến khi chuyến hoàn thành hoặc bị hủy.  |
| **BG01_QuanLyLichSuChuyenDi**    | Quản lý lịch sử chuyến đi    | Lưu trữ và cho phép khách hàng tra cứu các chuyến đi đã thực hiện.                             |
| **BG01_DanhGiaTaiXe**            | Đánh giá tài xế              | Cho phép khách hàng đánh giá tài xế sau khi chuyến đi hoàn thành.                              |

---

### 6.2. BG-02 – Tự động hóa quá trình tìm và phân công tài xế

| Mã Business Requirement       | Business Requirement      | Mô tả                                                                                                         |
| ----------------------------- | ------------------------- | ------------------------------------------------------------------------------------------------------------- |
| **BG02_QuanLyTrangThaiTaiXe** | Quản lý trạng thái tài xế | Hệ thống ghi nhận trạng thái sẵn sàng hoặc không sẵn sàng nhận chuyến của tài xế.                             |
| **BG02_TheoDoiViTriTaiXe**    | Theo dõi vị trí tài xế    | Ghi nhận vị trí tài xế để hỗ trợ xác định tài xế phù hợp với yêu cầu đặt xe.                                  |
| **BG02_TimTaiXePhuHop**       | Tìm tài xế phù hợp        | Hệ thống tự động tìm và ưu tiên tài xế phù hợp dựa trên vị trí, trạng thái sẵn sàng và các tiêu chí vận hành. |
| **BG02_PhanCongTaiXe**        | Phân công tài xế          | Gửi yêu cầu chuyến đến tài xế phù hợp và ghi nhận việc tài xế chấp nhận hoặc từ chối.                         |
| **BG02_TimLaiTaiXe**          | Tìm lại tài xế            | Tự động tiếp tục tìm tài xế khác nếu tài xế được đề xuất từ chối hoặc không phản hồi.                         |
| **BG02_XuLyKhongCoTaiXe**     | Xử lý khi không có tài xế | Thông báo rõ ràng cho khách hàng khi hệ thống không tìm được tài xế phù hợp.                                  |

---

### 6.3. BG-03 – Nâng cao trải nghiệm đặt xe và theo dõi chuyến đi

| Mã Business Requirement           | Business Requirement          | Mô tả                                                                                                  |
| --------------------------------- | ----------------------------- | ------------------------------------------------------------------------------------------------------ |
| **BG03_TheoDoiTrangThaiDatXe**    | Theo dõi trạng thái đặt xe    | Cho phép khách hàng biết hệ thống đang tìm tài xế hoặc đã tìm được tài xế.                             |
| **BG03_HienThiThongTinTaiXe**     | Hiển thị thông tin tài xế     | Cung cấp thông tin tài xế đã nhận chuyến cho khách hàng.                                               |
| **BG03_HienThiThoiGianDuKien**    | Hiển thị thời gian dự kiến    | Cung cấp thời gian dự kiến tài xế đến điểm đón cho khách hàng.                                         |
| **BG03_TheoDoiTrangThaiChuyenDi** | Theo dõi trạng thái chuyến đi | Cho phép theo dõi các trạng thái như tài xế đã đến, đã đón khách, đang di chuyển và hoàn thành chuyến. |
| **BG03_ThongBaoSuKienChuyenDi**   | Thông báo sự kiện chuyến đi   | Gửi thông báo cho khách hàng và tài xế khi có các sự kiện quan trọng liên quan đến chuyến đi.          |

---

### 6.4. BG-04 – Quản lý tập trung cước phí và thanh toán

| Mã Business Requirement         | Business Requirement        | Mô tả                                                                                                 |
| ------------------------------- | --------------------------- | ----------------------------------------------------------------------------------------------------- |
| **BG04_TinhCuocChuyenDi**       | Tính cước chuyến đi         | Xác định số tiền khách hàng phải trả dựa trên loại dịch vụ và thông tin chuyến đi.                    |
| **BG04_ThanhToanTienMat**       | Thanh toán tiền mặt         | Cho phép khách hàng lựa chọn thanh toán bằng tiền mặt sau khi chuyến đi hoàn thành.                   |
| **BG04_ThanhToanDienTu**        | Thanh toán điện tử          | Cho phép thanh toán thông qua nhà cung cấp thanh toán bên ngoài.                                      |
| **BG04_BaoVeThongTinThanhToan** | Bảo vệ thông tin thanh toán | Không lưu trực tiếp thông tin nhạy cảm của thẻ hoặc tài khoản thanh toán trong CAB System.            |
| **BG04_XuLyThanhToanThatBai**   | Xử lý thanh toán thất bại   | Thông báo khi giao dịch thất bại và hỗ trợ thực hiện lại thanh toán theo chính sách của doanh nghiệp. |
| **BG04_LuuLichSuGiaoDich**      | Lưu lịch sử giao dịch       | Lưu thông tin cần thiết của giao dịch để phục vụ tra cứu và quản lý.                                  |

---

### 6.5. BG-05 – Nâng cao hiệu quả quản lý và vận hành dịch vụ

| Mã Business Requirement   | Business Requirement  | Mô tả                                                                                                   |
| ------------------------- | --------------------- | ------------------------------------------------------------------------------------------------------- |
| **BG05_QuanLyKhachHang**  | Quản lý khách hàng    | Cho phép nhân viên vận hành tra cứu và quản lý thông tin khách hàng.                                    |
| **BG05_QuanLyTaiXe**      | Quản lý tài xế        | Cho phép quản lý hồ sơ, trạng thái hoạt động và thông tin liên quan đến tài xế.                         |
| **BG05_QuanLyPhuongTien** | Quản lý phương tiện   | Quản lý thông tin phương tiện của các tài xế.                                                           |
| **BG05_GiamSatChuyenDi**  | Giám sát chuyến đi    | Cho phép nhân viên vận hành xem và theo dõi các chuyến đang diễn ra.                                    |
| **BG05_XuLySuCoChuyenDi** | Xử lý sự cố chuyến đi | Hỗ trợ nhân viên vận hành kiểm tra và xử lý các trường hợp chuyến đi gặp lỗi hoặc bất thường.           |
| **BG05_TraCuuGiaoDich**   | Tra cứu giao dịch     | Cho phép nhân viên có quyền phù hợp tra cứu lịch sử giao dịch.                                          |
| **BG05_BaoCaoHoatDong**   | Báo cáo hoạt động     | Cung cấp báo cáo về số chuyến, doanh thu, tỷ lệ hoàn thành, tỷ lệ hủy và hiệu quả hoạt động của tài xế. |

---

### 6.6. BG-06 – Xây dựng nền tảng ổn định, bảo mật và có khả năng mở rộng lâu dài

| Mã Business Requirement     | Business Requirement    | Mô tả                                                                                                                                                  |
| --------------------------- | ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **BG06_XacThucNguoiDung**   | Xác thực người dùng     | Khách hàng và tài xế phải được xác thực trước khi sử dụng các chức năng yêu cầu tài khoản.                                                             |
| **BG06_PhanQuyenQuanTri**   | Phân quyền quản trị     | Kiểm soát quyền truy cập để các thao tác quản trị nhạy cảm chỉ được thực hiện bởi người có quyền phù hợp.                                              |
| **BG06_BaoVeDuLieu**        | Bảo vệ dữ liệu          | Bảo vệ thông tin cá nhân, phương tiện, vị trí và dữ liệu giao dịch của người dùng.                                                                     |
| **BG06_LuuVetHoatDong**     | Lưu vết hoạt động       | Ghi nhận các thao tác quan trọng để hỗ trợ kiểm tra và xử lý khi có sự cố.                                                                             |
| **BG06_DamBaoTinhSanSang**  | Đảm bảo tính sẵn sàng   | Hạn chế việc lỗi ở một thành phần như thanh toán hoặc thông báo làm gián đoạn toàn bộ hệ thống đặt xe.                                                 |
| **BG06_HoTroMoRongHeThong** | Hỗ trợ mở rộng hệ thống | Cho phép các thành phần có thể mở rộng độc lập khi số lượng khách hàng, tài xế hoặc chuyến đi tăng.                                                    |
| **BG06_HoTroMoRongTichHop** | Hỗ trợ mở rộng tích hợp | Kiến trúc cho phép bổ sung loại dịch vụ, phương thức thanh toán và nhà cung cấp thông báo trong tương lai mà không phải xây dựng lại toàn bộ hệ thống. |

---

### 6.7. Traceability Business Goal – Business Requirement

| Business Goal | Business Requirements                                                                                                                                         |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **BG-01**     | BG01_QuanLyTaiKhoanKhachHang, BG01_TaoYeuCauDatXe, BG01_QuanLyChuyenDi, BG01_QuanLyLichSuChuyenDi, BG01_DanhGiaTaiXe                                          |
| **BG-02**     | BG02_QuanLyTrangThaiTaiXe, BG02_TheoDoiViTriTaiXe, BG02_TimTaiXePhuHop, BG02_PhanCongTaiXe, BG02_TimLaiTaiXe, BG02_XuLyKhongCoTaiXe                           |
| **BG-03**     | BG03_TheoDoiTrangThaiDatXe, BG03_HienThiThongTinTaiXe, BG03_HienThiThoiGianDuKien, BG03_TheoDoiTrangThaiChuyenDi, BG03_ThongBaoSuKienChuyenDi                 |
| **BG-04**     | BG04_TinhCuocChuyenDi, BG04_ThanhToanTienMat, BG04_ThanhToanDienTu, BG04_BaoVeThongTinThanhToan, BG04_XuLyThanhToanThatBai, BG04_LuuLichSuGiaoDich            |
| **BG-05**     | BG05_QuanLyKhachHang, BG05_QuanLyTaiXe, BG05_QuanLyPhuongTien, BG05_GiamSatChuyenDi, BG05_XuLySuCoChuyenDi, BG05_TraCuuGiaoDich, BG05_BaoCaoHoatDong          |
| **BG-06**     | BG06_XacThucNguoiDung, BG06_PhanQuyenQuanTri, BG06_BaoVeDuLieu, BG06_LuuVetHoatDong, BG06_DamBaoTinhSanSang, BG06_HoTroMoRongHeThong, BG06_HoTroMoRongTichHop |


---
## 7. Business Process

### 7.1. BP-01 – Quy trình đăng ký và quản lý tài khoản khách hàng

**Business Requirements liên quan:** `BG01_QuanLyTaiKhoanKhachHang`, `BG06_XacThucNguoiDung`

```mermaid
flowchart TD
    A([Bắt đầu]) --> B[Khách hàng đăng ký tài khoản]
    B --> C[Nhập thông tin cá nhân]
    C --> D{Thông tin hợp lệ?}

    D -- Không --> E[Thông báo lỗi]
    E --> C

    D -- Có --> F[Tạo tài khoản khách hàng]
    F --> G[Khách hàng đăng nhập]
    G --> H{Xác thực thành công?}

    H -- Không --> I[Thông báo đăng nhập thất bại]
    I --> G

    H -- Có --> J[Truy cập CAB System]
    J --> K[Cập nhật hồ sơ khi cần]
    K --> L([Kết thúc])
```

---

### 7.2. BP-02 – Quy trình tạo yêu cầu đặt xe

**Business Requirements liên quan:** `BG01_TaoYeuCauDatXe`, `BG01_QuanLyChuyenDi`

```mermaid
flowchart TD
    A([Bắt đầu]) --> B[Khách hàng nhập điểm đón]
    B --> C[Nhập điểm đến]
    C --> D[Chọn loại xe]
    D --> E[Hệ thống kiểm tra thông tin]

    E --> F{Thông tin hợp lệ?}

    F -- Không --> G[Yêu cầu khách hàng chỉnh sửa]
    G --> B

    F -- Có --> H[Hiển thị thông tin chuyến]
    H --> I[Khách hàng xác nhận đặt xe]
    I --> J[Tạo yêu cầu chuyến đi]
    J --> K[Trạng thái: Đang tìm tài xế]
    K --> L([Chuyển sang quy trình tìm tài xế])
```

---

### 7.3. BP-03 – Quy trình tìm và phân công tài xế

**Business Requirements liên quan:** `BG02_QuanLyTrangThaiTaiXe`, `BG02_TheoDoiViTriTaiXe`, `BG02_TimTaiXePhuHop`, `BG02_PhanCongTaiXe`, `BG02_TimLaiTaiXe`, `BG02_XuLyKhongCoTaiXe`

```mermaid
flowchart TD
    A([Nhận yêu cầu đặt xe]) --> B[Tìm tài xế đang sẵn sàng]
    B --> C[Lọc theo vị trí và loại xe]
    C --> D[Xếp ưu tiên tài xế phù hợp]
    D --> E{Có tài xế phù hợp?}

    E -- Không --> F[Thông báo không tìm được tài xế]
    F --> G[Đóng yêu cầu tìm tài xế]
    G --> Z([Kết thúc])

    E -- Có --> H[Gửi yêu cầu chuyến cho tài xế]
    H --> I{Tài xế phản hồi?}

    I -- Không --> J[Hết thời gian phản hồi]
    J --> K[Tìm tài xế tiếp theo]
    K --> E

    I -- Có --> L{Tài xế chấp nhận?}

    L -- Không --> K
    L -- Có --> M[Phân công tài xế]
    M --> N[Cập nhật thông tin chuyến]
    N --> O[Thông báo cho khách hàng]
    O --> P([Bắt đầu thực hiện chuyến])
```

---

### 7.4. BP-04 – Quy trình thực hiện và theo dõi chuyến đi

**Business Requirements liên quan:** `BG01_QuanLyChuyenDi`, `BG03_HienThiThongTinTaiXe`, `BG03_HienThiThoiGianDuKien`, `BG03_TheoDoiTrangThaiChuyenDi`

```mermaid
flowchart TD
    A([Tài xế nhận chuyến]) --> B[Hiển thị thông tin tài xế cho khách hàng]
    B --> C[Hiển thị thời gian dự kiến đến]
    C --> D[Tài xế di chuyển đến điểm đón]
    D --> E[Tài xế cập nhật: Đã đến điểm đón]

    E --> F[Khách hàng lên xe]
    F --> G[Tài xế cập nhật: Đã đón khách]
    G --> H[Tài xế bắt đầu chuyến]
    H --> I[Cập nhật: Đang di chuyển]

    I --> J[Hệ thống theo dõi trạng thái chuyến]
    J --> K[Tài xế đến điểm đến]
    K --> L[Tài xế xác nhận hoàn thành]
    L --> M[Cập nhật: Hoàn thành]
    M --> N([Chuyển sang tính cước])
```

---

### 7.5. BP-05 – Quy trình tính cước và thanh toán

**Business Requirements liên quan:** `BG04_TinhCuocChuyenDi`, `BG04_ThanhToanTienMat`, `BG04_ThanhToanDienTu`, `BG04_XuLyThanhToanThatBai`, `BG04_LuuLichSuGiaoDich`

```mermaid
flowchart TD
    A([Chuyến đi hoàn thành]) --> B[Thu thập thông tin chuyến]
    B --> C[Tính cước chuyến đi]
    C --> D[Hiển thị số tiền cần thanh toán]
    D --> E{Phương thức thanh toán?}

    E -- Tiền mặt --> F[Khách hàng thanh toán tiền mặt]
    F --> G[Ghi nhận thanh toán thành công]

    E -- Điện tử --> H[Gửi yêu cầu đến Payment Provider]
    H --> I{Thanh toán thành công?}

    I -- Có --> G

    I -- Không --> J[Thông báo thanh toán thất bại]
    J --> K{Thử lại?}

    K -- Có --> H
    K -- Không --> L[Ghi nhận trạng thái thanh toán chưa thành công]

    G --> M[Lưu thông tin giao dịch]
    L --> M
    M --> N([Kết thúc])
```

---

### 7.6. BP-06 – Quy trình gửi thông báo

**Business Requirements liên quan:** `BG03_ThongBaoSuKienChuyenDi`

```mermaid
flowchart TD
    A([Phát sinh sự kiện]) --> B{Loại sự kiện}

    B -->|Đặt xe| C[Yêu cầu đặt xe được tiếp nhận]
    B -->|Nhận chuyến| D[Tài xế đã nhận chuyến]
    B -->|Đến điểm đón| E[Tài xế đã đến điểm đón]
    B -->|Hoàn thành| F[Chuyến đi đã hoàn thành]
    B -->|Thanh toán| G[Có kết quả thanh toán]

    C --> H[Tạo nội dung thông báo]
    D --> H
    E --> H
    F --> H
    G --> H

    H --> I[Gửi qua Notification Provider]
    I --> J{Gửi thành công?}

    J -- Có --> K[Ghi nhận kết quả gửi]
    J -- Không --> L[Ghi nhận lỗi thông báo]

    K --> M([Kết thúc])
    L --> M
```

---

### 7.7. BP-07 – Quy trình xem lịch sử và đánh giá tài xế

**Business Requirements liên quan:** `BG01_QuanLyLichSuChuyenDi`, `BG01_DanhGiaTaiXe`

```mermaid
flowchart TD
    A([Bắt đầu]) --> B[Khách hàng mở lịch sử chuyến đi]
    B --> C[Hệ thống lấy danh sách chuyến]
    C --> D[Hiển thị lịch sử chuyến]

    D --> E[Khách hàng chọn một chuyến]
    E --> F[Hiển thị chi tiết chuyến]
    F --> G{Chuyến đã hoàn thành?}

    G -- Không --> H[Không cho phép đánh giá]
    H --> Z([Kết thúc])

    G -- Có --> I{Đã đánh giá?}

    I -- Có --> J[Hiển thị đánh giá đã gửi]
    J --> Z

    I -- Chưa --> K[Khách hàng nhập đánh giá tài xế]
    K --> L[Gửi đánh giá]
    L --> M[Lưu đánh giá]
    M --> N[Cập nhật thông tin đánh giá tài xế]
    N --> Z
```

---

### 7.8. BP-08 – Quy trình quản lý và xử lý chuyến đi của nhân viên vận hành

**Business Requirements liên quan:** `BG05_QuanLyKhachHang`, `BG05_QuanLyTaiXe`, `BG05_QuanLyPhuongTien`, `BG05_GiamSatChuyenDi`, `BG05_XuLySuCoChuyenDi`, `BG05_TraCuuGiaoDich`

```mermaid
flowchart TD
    A([Bắt đầu]) --> B[Nhân viên vận hành đăng nhập]
    B --> C[Hệ thống xác thực và kiểm tra quyền]
    C --> D{Có quyền truy cập?}

    D -- Không --> E[Từ chối truy cập]
    E --> Z([Kết thúc])

    D -- Có --> F[Mở giao diện vận hành]
    F --> G{Chọn chức năng}

    G -->|Khách hàng| H[Tra cứu và quản lý khách hàng]
    G -->|Tài xế| I[Tra cứu và quản lý tài xế]
    G -->|Phương tiện| J[Tra cứu và quản lý phương tiện]
    G -->|Chuyến đi| K[Theo dõi chuyến đang diễn ra]
    G -->|Giao dịch| L[Tra cứu lịch sử giao dịch]

    K --> M{Chuyến gặp sự cố?}
    M -- Không --> N[Tiếp tục giám sát]
    M -- Có --> O[Kiểm tra thông tin sự cố]
    O --> P[Thực hiện biện pháp xử lý]
    P --> Q[Lưu kết quả xử lý]

    H --> R([Hoàn thành])
    I --> R
    J --> R
    L --> R
    N --> R
    Q --> R
```

---

### 7.9. BP-09 – Quy trình báo cáo và giám sát hoạt động

**Business Requirements liên quan:** `BG05_BaoCaoHoatDong`, `BG06_LuuVetHoatDong`

```mermaid
flowchart TD
    A([Bắt đầu]) --> B[Người có quyền truy cập báo cáo]
    B --> C[Chọn khoảng thời gian báo cáo]
    C --> D[Hệ thống tổng hợp dữ liệu]

    D --> E[Tính tổng số chuyến]
    D --> F[Tính doanh thu]
    D --> G[Tính tỷ lệ hoàn thành]
    D --> H[Tính tỷ lệ hủy]
    D --> I[Tổng hợp hiệu quả tài xế]

    E --> J[Tạo báo cáo]
    F --> J
    G --> J
    H --> J
    I --> J

    J --> K[Hiển thị kết quả]
    K --> L[Người dùng xem báo cáo]
    L --> M[Ghi nhận thao tác quan trọng]
    M --> N([Kết thúc])
```

---

### 7.10. Liên kết Business Process với Business Requirements

| Business Process | Nội dung chính                                 | Business Goal |
| ---------------- | ---------------------------------------------- | ------------- |
| **BP-01**        | Đăng ký và quản lý tài khoản khách hàng        | BG-01, BG-06  |
| **BP-02**        | Tạo yêu cầu đặt xe                             | BG-01         |
| **BP-03**        | Tìm và phân công tài xế                        | BG-02         |
| **BP-04**        | Thực hiện và theo dõi chuyến đi                | BG-01, BG-03  |
| **BP-05**        | Tính cước và thanh toán                        | BG-04         |
| **BP-06**        | Gửi thông báo                                  | BG-03         |
| **BP-07**        | Lịch sử chuyến và đánh giá tài xế              | BG-01         |
| **BP-08**        | Quản lý và xử lý chuyến của nhân viên vận hành | BG-05, BG-06  |
| **BP-09**        | Báo cáo và giám sát hoạt động                  | BG-05, BG-06  |

### 7.11. Luồng nghiệp vụ tổng thể

9 quy trình trên kết hợp thành luồng nghiệp vụ chính của CAB System:

**Đăng ký/Đăng nhập → Đặt xe → Tìm tài xế → Thực hiện chuyến → Tính cước & Thanh toán → Đánh giá → Quản lý & Báo cáo**

Trong đó, **Notification** hoạt động xuyên suốt quá trình để thông báo các sự kiện quan trọng cho Customer và Driver.


# Thin SPEC — Nhóm Thanh niên áo hồng

Thin SPEC quy định lát cắt sản phẩm (Build Slice) và thiết kế hệ thống AI Trợ lý tư vấn đặt lịch khám bệnh khi gặp sự cố bận/đổi lịch của bác sĩ đích danh tại Bạch Mai Care.

---

## 1. Track, product/app và user

- **Track:** E - Healthcare (Chăm sóc sức khỏe)  
- **Product/app thật:** Bạch Mai Care  
- **User cụ thể:** Bệnh nhân đăng ký khám bệnh theo yêu cầu và chỉ định đích danh một bác sĩ chuyên khoa/chuyên gia (như PGS, TS, Trưởng khoa), nhưng gặp tình huống bác sĩ bị hết lịch khám hoặc bận đột xuất (lịch mổ, hội chẩn, đi công tác) vào ngày đã đăng ký.  
- **Nhóm có phải user thật không? Nếu không, khác ở đâu?**  
  Nhóm không phải là bệnh nhân thật. Khác biệt lớn nhất là: Người bệnh thật (đặc biệt là người lớn tuổi hoặc ở tỉnh xa) có mức độ lo lắng cao về tình trạng bệnh, khó tiếp cận công nghệ mới và cần sự chắc chắn tuyệt đối khi thay đổi lịch khám. Họ cần một quy trình tư vấn tự nhiên, rõ ràng và có phương án dự phòng an toàn hơn là các thao tác bấm chọn phức tạp.

---

## 2. Evidence summary

| Evidence | Nguồn | User/pain nói lên điều gì? | SPEC phải đổi gì? |
|---|---|---|---|
| Báo hết lịch hoặc bắt tự tìm kiếm thủ công. | Self-use app Bạch Mai Care | Bệnh nhân phải nhấp chọn vào từng bác sĩ để check lịch. Khi hết lịch, họ phải tự mò tìm ngày khác hoặc thoát ra tìm thủ công từng bác sĩ khác cùng khoa. | Chatbot phải chủ động đề xuất lịch trống gần nhất hoặc bác sĩ thay thế tương đương cùng chuyên khoa/chức vụ/học hàm. |
| Người bệnh gọi điện trực tiếp cho tổng đài khi gặp sự cố đặt lịch. | Phỏng vấn bệnh nhân tại bệnh viện | Khách hàng cần có người tư vấn, thương lượng và đưa ra giải pháp thay thế linh hoạt thay vì tự thao tác. | AI phải đóng vai trò là một trợ lý hội thoại (conversational agent) có tính tương tác cao như nhân viên tổng đài. |
| Lịch khám của bác sĩ thay đổi liên tục theo ngày khi có sự cố phát sinh. | Nghiên cứu nghiệp vụ y tế | Thông tin lịch khám có độ động cực kỳ cao, dễ xảy ra lỗi đồng bộ dữ liệu. | Tích hợp cơ chế kiểm tra lịch thời gian thực (Real-time Verification) trước khi xác nhận giao dịch. |

---

## 3. Pain statement

```text
User (Bệnh nhân đặt khám bác sĩ đích danh) đang gặp khó ở bước "chọn lịch khám thay thế khi lịch mong muốn bị hết hoặc bác sĩ bận đột xuất",
vì hệ thống app hiện tại bắt buộc phải nhấp chọn vào từng bác sĩ để kiểm tra và không có cơ chế tự động gợi ý thay thế, bắt user tự tìm kiếm thủ công từ đầu,
dẫn tới hậu quả là user dễ nản lòng, thất vọng và từ bỏ sử dụng app, chuyển sang gọi điện thoại tổng đài nhờ hỗ trợ nhanh hơn, gây quá tải hệ thống.
Bằng chứng chính là các phản hồi phàn nàn của bệnh nhân về việc không biết đặt bác sĩ nào thay thế khi PGS/TS mong muốn hết lịch, và hành vi nhanh chóng bỏ app gọi tổng đài.
```

---

## 4. Build slice

```text
Cho bệnh nhân đăng ký khám bác sĩ đích danh nhưng lịch khám bị hết hoặc bị bận đột xuất,
prototype sẽ dùng AI để đề xuất 2-3 phương án thay thế: gợi ý các ngày khám trống gần nhất của bác sĩ đó HOẶC giới thiệu các bác sĩ tương đương cùng chuyên khoa/chức vụ/học hàm đang có lịch trống,
tạo ra danh sách đề xuất trực quan kèm nút xác nhận đổi lịch nhanh qua khung chat,
và xử lý failure mode (lịch thay thế cũng bị bận đột xuất hoặc hết bác sĩ tương đương) bằng cách chuyển kết nối trực tiếp đến nhân viên tổng đài hỗ trợ (Human-in-the-loop).
```

---

## 5. Auto/Aug decision

Chọn: **Augmentation**  

- [x] **Augmentation:** AI gợi ý/đề xuất lịch hoặc bác sĩ thay thế tương đương qua chat, user bấm chọn để quyết định cuối cùng.
- [ ] **Conditional automation:** AI tự làm trong case hẹp; case mơ hồ/rủi ro chuyển người.
- [ ] **Automation:** AI tự quyết và tự hành động.

**Lý do chọn:** Lĩnh vực y tế có tính rủi ro và nhạy cảm cao. Quyền lựa chọn bác sĩ điều trị và thời gian đi khám bệnh phải thuộc về bản thân người bệnh hoặc người nhà bệnh nhân. AI chỉ đóng vai trò hỗ trợ cung cấp thông tin và đề xuất tối ưu.  
**Human role:** **Decider** (Người dùng quyết định chọn phương án thay thế) & **Rescuer** (Nhân viên tổng đài can thiệp trực tiếp khi AI gặp lỗi hệ thống hoặc không tìm được lịch khám phù hợp).

---

## 6. Four paths

| Path | Prototype phải thể hiện gì? |
|---|---|
| **Happy** | Bác sĩ A bận lịch đột xuất vào ngày mai. AI nhắn tin thông báo qua chat và hiển thị 2 phương án: <br>1. Đổi sang lịch của bác sĩ A vào thứ 5 tuần này.<br>2. Đổi sang bác sĩ B (cùng chuyên khoa, học vị PGS tương đương) có lịch vào ngày mai.<br>User chọn 1 phương án -> AI gọi API cập nhật database và báo đổi lịch thành công. |
| **Low-confidence** | Bác sĩ A hết lịch trong 2 tuần tới, và không có bác sĩ nào cùng học vị PGS có lịch trống. AI hỏi lại: *"Bác sĩ A hiện không có lịch trong 2 tuần tới và các bác sĩ cùng học hàm PGS cũng đã hết lịch. Bạn có muốn tham khảo bác sĩ C (học vị Tiến sĩ, cùng chuyên khoa) có lịch vào ngày mai không?"* kèm nút xác nhận. |
| **Failure** | AI gợi ý bác sĩ thay thế và user đồng ý, nhưng lúc thực thi lưu database thì lịch bác sĩ đó vừa bị bận đột xuất (do thay đổi thời gian thực chưa đồng bộ kịp). Hệ thống báo lỗi đổi lịch thất bại. |
| **Correction** | Khi AI đề xuất bác sĩ thay thế B nhưng user không muốn khám bác sĩ này và yêu cầu: *"Tôi không muốn khám bác sĩ B, hãy đổi sang bác sĩ C"* hoặc *"Tôi muốn đổi sang ngày khác"*, AI ghi nhận và hiển thị lại danh sách gợi ý mới theo đúng yêu cầu mà không làm mất lịch cũ khi chưa xác nhận. |

---

## 7. Failure mode nguy hiểm nhất

```text
Nếu user đồng ý đổi lịch sang bác sĩ thay thế,
AI có thể gặp lỗi đồng bộ khiến lịch của bác sĩ thay thế thực tế cũng bị bận đột xuất (do dữ liệu lịch khám thay đổi liên tục theo ngày),
hậu quả là bệnh nhân đến viện nhưng không được khám, lỡ mất cơ hội điều trị và tốn công sức đi lại của người bệnh.
Prototype sẽ xử lý bằng cơ chế kiểm tra lịch thời gian thực (API Real-time Verification) ngay trước khi xác nhận. Nếu API báo lỗi bận lịch đột xuất, chatbot sẽ kích hoạt UX Fallback: gửi tin nhắn xin lỗi và tự động kết nối thông tin của user sang nhân viên tổng đài (Human rescuer) để gọi điện thoại hỗ trợ trực tiếp.
Owner kiểm thử path này là Trần Minh Hoàng.
```

---

## 8. Owner plan cho sáng Day 06

| Thành viên | Việc phụ trách | Bằng chứng cần có trong repo |
|---|---|---|
| **Thành viên A** (Research) | Thu thập lịch khám của các bác sĩ Bạch Mai, danh sách học hàm/chức vụ để làm dữ liệu mẫu. | File `02-group-spec/evidence-pack.md` hoàn thiện dữ liệu mock. |
| **Trần Minh Hoàng** (SPEC/Proto) | Xây dựng kịch bản chatbot, viết Prompts và code logic xử lý gợi ý thay thế của AI. | Code prototype chatbot (Python/JS) và file `thin-spec.md`. |
| **Thành viên C** (Tester) | Thiết lập kịch bản kiểm thử cho Failure path (lịch bác sĩ thay thế bị bận đột xuất) và Low-confidence path. | Bản log test case và kết quả chạy thử các kịch bản lỗi. |
| **Thành viên D** (Demo/Repo) | Chuẩn bị kịch bản demo (demo script) trong 3 phút, quay video vận hành của chatbot và quản lý repo. | File `demo-script.md` và video demo đính kèm trong repo. |

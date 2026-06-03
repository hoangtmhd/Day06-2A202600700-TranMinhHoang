# Evidence Pack — Nhóm Thanh niên áo hồng

Cung cấp các bằng chứng thực tế và nghiên cứu người dùng cho bài tập Day 05.

---

## 1. Nhóm và track

- **Tên nhóm:** Thanh niên áo hồng  
- **Track:** E - Healthcare  
- **Product/app đã chọn:** Bạch Mai Care (Ứng dụng chăm sóc sức khỏe & đặt lịch khám của Bệnh viện Bạch Mai)  
- **Build slice đang nghĩ:** Trợ lý AI xử lý sự cố/xung đột khi đặt lịch khám bác sĩ đích danh (Bác sĩ bận lịch đột xuất, đổi lịch hoặc hết lịch trống) bằng cách đề xuất lịch khám gần nhất hoặc giới thiệu bác sĩ tương đương cùng chuyên khoa/chức vụ/học hàm qua giao diện chat.

---

## 2. Self-use evidence (Bằng chứng tự trải nghiệm)

Nhóm tự dùng thử app Bạch Mai Care và ghi chép lại các điểm gãy trong quy trình đặt lịch khám theo bác sĩ:

| Observation | Screenshot/link | Path liên quan | Điều học được |
|---|---|---|---|
| Khi chọn một bác sĩ cụ thể, app có hiển thị rõ danh sách lịch khám còn trống trong ngày của bác sĩ đó. | (Sẽ chèn link ảnh/screenshot thử nghiệm) | Failure Path | Bệnh nhân bắt buộc phải ấn vào từng bác sĩ để check lịch. Nếu bác sĩ đó hết lịch/bận, hệ thống không tự gợi ý phương án thay thế; user vẫn phải tự mò tìm ngày khác hoặc tự thoát ra bấm vào từng bác sĩ khác cùng khoa để tìm lịch trống một cách thủ công. |
| Không có tính năng đề xuất bác sĩ thay thế khi bác sĩ mong muốn hết lịch. | (Sẽ chèn link ảnh/screenshot thử nghiệm) | Failure / Low-confidence | Bệnh nhân phải tự mò ra danh sách bác sĩ cùng khoa, tự đọc thông tin học vị/chức vụ để so sánh và chọn lại từ đầu. |
| Lịch khám của bác sĩ chuyên khoa đầu ngành thay đổi liên tục theo tuần (mổ đột xuất, hội chẩn), dẫn đến thông tin hiển thị trên app dễ bị lệch so với thực tế nếu không đồng bộ thời gian thực. | (Sẽ chèn link ảnh/screenshot thử nghiệm) | Failure Path | Dữ liệu lịch khám có độ động rất cao, hệ thống tĩnh sẽ liên tục tạo ra các giao dịch đặt lịch bị hủy sau đó. |

---

## 3. User / review / social evidence (Bằng chứng từ người dùng & xã hội)

Nguồn thông tin từ phản hồi của bệnh nhân đi khám tại bệnh viện Bạch Mai và khảo sát thực tế hành vi người dùng:

| Quote / review / observation | Nguồn | User là ai? | Pain/failure mode |
|---|---|---|---|
| "Tôi muốn khám đích danh bác sĩ đầu ngành nhưng lên app đặt thì báo hết lịch, không biết bác sĩ có khám ngày khác không hay có ai tương đương khám thay không." | Khảo sát ý kiến bệnh nhân | Bệnh nhân lớn tuổi ở tỉnh xa, muốn khám bác sĩ giỏi | Không thể tự đưa ra quyết định thay thế khi lịch mong muốn bị hủy/hết. |
| "Nhiều khi dùng app phức tạp quá, không biết chọn khoa nào theo triệu chứng mơ hồ, lịch bác sĩ thì hay đổi. Tôi toàn gọi thẳng lên tổng đài bệnh viện nhờ họ check lịch và đặt hộ cho nhanh." | Phỏng vấn trực tiếp tại viện | Bệnh nhân ngại công nghệ, cần hỗ trợ ra quyết định | Hành vi thay thế: Bỏ app để gọi tổng đài vì cần người thật tư vấn, gợi ý phương án thay thế linh hoạt. |

---

## 4. Competitor / analog evidence (Bằng chứng đối thủ cạnh tranh)

| App / mô hình tham khảo | Họ xử lý task này thế nào? | Pattern học được | Có áp dụng trong 1 ngày không? |
|---|---|---|---|
| **BookingCare** / **Vinmec** | Khi bác sĩ được chọn hết lịch, hệ thống hiển thị lịch của các ngày tiếp theo ngay bên dưới, hoặc gợi ý danh sách các bác sĩ khác cùng chuyên khoa đang có lịch trống kèm học vị rõ ràng. | **Alternative Recommendation:** Đưa ra các phương án thay thế thông minh (ngày khác, bác sĩ cùng chuyên môn) ngay tại điểm gãy của luồng đặt lịch. | Có thể áp dụng được luồng đề xuất thay thế này thông qua giao diện Chatbot của trợ lý AI. |

---

## 5. Evidence -> Insight

```text
Evidence nổi bật nhất:
Bệnh nhân dễ cảm thấy nản lòng và thất vọng với app khi phải tự thực hiện quá nhiều thao tác thủ công (nhấp vào từng bác sĩ để check lịch, tự tìm kiếm thay thế khi bác sĩ đích danh bận/hết lịch). Họ nhanh chóng bỏ cuộc và lựa chọn liên hệ trực tiếp với tổng đài bệnh viện để được nhân viên hỗ trợ xử lý nhanh hơn thay vì tiếp tục tự tìm kiếm trên ứng dụng.

Insight:
Bệnh nhân không chỉ cần một giao diện điền form đặt lịch tĩnh. Họ thực chất cần sự tư vấn cá nhân hóa, hỗ trợ ra quyết định (Decision Support) và giải pháp thay thế linh hoạt (Recovery) ngay lập tức khi phương án ưu tiên của họ (bác sĩ đích danh, ngày khám mong muốn) bị thay đổi đột xuất hoặc hết chỗ.

Opportunity:
AI có thể giúp bằng cách đóng vai trò như một Trợ lý hội thoại thông minh (Conversational Recovery Agent) trực tuyến, tự động phân tích xung đột lịch khám và đưa ra các đề xuất dời lịch gần nhất hoặc gợi ý bác sĩ cùng chuyên khoa/chức vụ/học hàm ngay tại khung chat để user xác nhận nhanh.
```

---

## 6. Evidence đổi SPEC như thế nào?

- [x] Đổi user chính: Tập trung vào bệnh nhân có nhu cầu khám bác sĩ đích danh và cần dời/đổi lịch khám linh hoạt.
- [ ] Đổi pain statement.
- [x] Đổi build slice: Tập trung xử lý lỗi hết/đổi lịch bác sĩ chuyên khoa bằng cách gợi ý bác sĩ tương đương hoặc ngày khám gần nhất.
- [x] Đổi Auto/Aug decision: Chọn Augmentation để AI gợi ý các options (bác sĩ tương đương, ngày khác), người dùng bấm chọn để quyết định cuối.
- [x] Đổi 4 paths: Happy (đổi lịch thành công), Low-confidence (hết bác sĩ tương đương, gợi ý học vị thấp hơn chút), Failure (lịch thay thế cũng bị bận đột xuất), Correction (đồng ý đổi hoặc hoàn tác).
- [ ] Đổi failure mode.
- [ ] Đổi owner/test plan.

### Chi tiết thay đổi quan trọng:
```text
Trước evidence, nhóm định:
Build tính năng tư vấn chung từ triệu chứng ra chuyên khoa và hỗ trợ điền form đặt lịch.

Sau evidence, nhóm đổi thành:
Tập trung sâu vào giải quyết điểm gãy: 'Xử lý khi bác sĩ đích danh hết lịch khám hoặc bị bận lịch đột xuất' bằng cách AI đề xuất lịch khám gần nhất của bác sĩ đó hoặc giới thiệu các bác sĩ tương đương cùng chuyên khoa/học hàm/chức vụ.

Lý do:
Bằng chứng thực tế cho thấy hành vi bệnh nhân chuyển sang gọi tổng đài phần lớn do sự cố thay đổi lịch khám đột xuất của bác sĩ đầu ngành và họ không biết chọn ai/ngày nào thay thế trên giao diện app tĩnh. Giải quyết điểm gãy này mang lại giá trị thực tế cao nhất cho người dùng và giảm tải trực tiếp cho tổng đài.
```

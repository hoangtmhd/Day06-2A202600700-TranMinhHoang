# Toolkit — Từ Evidence Đến Build Slice

Dùng sau khi nhóm đã có evidence. Mục tiêu là chốt một build slice đủ nhỏ cho Day 06.

---

## 1. Gom evidence thành cụm

Gom theo **workflow/pain**, không gom theo tên feature.

### Hướng dẫn & Ví dụ:
- "Không biết chọn chuyên khoa"
- "Không hiểu vì sao bị tính phí"
- "Muốn sửa output nhưng không có chỗ sửa"
- "Bot trả lời tự tin nhưng không dẫn nguồn"

### Áp dụng thực tế của nhóm (Thanh niên áo hồng):
- **Cụm 1: Bệnh nhân nản lòng bỏ app gọi tổng đài khi gặp sự cố lịch khám.** (Người dùng cảm thấy quá phức tạp khi tự mò mẫm đổi lịch).
- **Cụm 2: Phải kiểm tra thủ công lịch khám từng bác sĩ khi bác sĩ đích danh hết lịch/bận.** (App có hiện lịch trong ngày nhưng bắt nhấp chọn từng người, không có đề xuất so sánh tương đương).
- **Cụm 3: Lịch khám của bác sĩ chuyên gia thay đổi liên tục theo ngày/tuần.** (Gây lỗi đồng bộ dữ liệu tĩnh và làm hủy lịch khám đột xuất).

---

## 2. Viết insight

### Form:
```text
User [segment] không chỉ cần [surface need].
Họ thật ra cần [deeper need],
vì [evidence pattern].
```

### Áp dụng thực tế của nhóm (Thanh niên áo hồng):
```text
Người bệnh đặt khám theo yêu cầu không chỉ cần một lịch khám cố định.
Họ thật ra cần sự tư vấn cá nhân hóa, hỗ trợ ra quyết định (Decision Support) và giải pháp thay thế linh hoạt (Recovery) khi lịch mong muốn bị thay đổi đột xuất,
vì thực tế trải nghiệm và khảo sát cho thấy bệnh nhân dễ cảm thấy nản lòng, thất vọng và chọn gọi tổng đài nhờ hỗ trợ nhanh hơn thay vì tự mò tìm lịch/bác sĩ thay thế trên app.
```

---

## 3. Viết opportunity

### Form:
```text
Cơ hội là dùng AI để [augment/automate hành động hẹp],
giúp user [kết quả],
trong khi vẫn kiểm soát [failure/risk].
```

### Áp dụng thực tế của nhóm (Thanh niên áo hồng):
```text
Cơ hội là dùng AI để tự động hóa cuộc hội thoại xử lý sự cố đặt lịch khám (Augmentation),
giúp user nhanh chóng chọn được ngày khám gần nhất còn trống của bác sĩ đó hoặc đổi sang bác sĩ khác có học hàm/chức vụ tương đương cùng khoa thông qua chat,
trong khi vẫn kiểm soát rủi ro lịch thay đổi liên tục bằng cơ chế kiểm tra lịch thời gian thực (API Real-time Verification) và chuyển cứu hộ sang tổng đài viên nếu hệ thống lỗi.
```

---

## 4. Chọn build slice

Build slice tốt phải qua 5 câu hỏi:

| Câu hỏi | Đạt khi | Đánh giá của nhóm (Thanh niên áo hồng) |
|---|---|---|
| **User cụ thể chưa?** | Nói được ai dùng, trong bối cảnh nào. | **Đạt:** Bệnh nhân đặt lịch khám bác sĩ chuyên gia tại Bạch Mai Care nhưng bác sĩ bận đột xuất hoặc hết lịch. |
| **Task đủ hẹp chưa?** | Demo được trong 3-5 phút. | **Đạt:** Chỉ thực hiện tư vấn dời ngày khám của bác sĩ đó hoặc đổi sang bác sĩ tương đương qua chat trong 1 flow. |
| **AI decision rõ chưa?** | AI gợi ý/tự làm một việc cụ thể. | **Đạt:** AI đề xuất 2-3 phương án tối ưu (ngày khác, bác sĩ cùng khoa/chức vụ/học hàm) cho user chọn. |
| **Failure path rõ chưa?** | Có một case AI không chắc hoặc sai để test. | **Đạt:** Khi lịch gợi ý thay thế cũng bị bận đột xuất và AI bị trôi ngữ cảnh (Context Drift) dẫn đến từ chối sai lệch. |
| **Có evidence không?** | Có bằng chứng từ self-use/review/user/competitor. | **Đạt:** Lấy từ self-use app Bạch Mai Care, phỏng vấn bệnh nhân thực tế tại viện và tham khảo BookingCare. |

---

## 5. Quyết định: giữ, giảm scope, hay đổi hướng?

| Tình huống | Quyết định | Áp dụng của nhóm |
|---|---|---|
| **Evidence yếu, user mơ hồ** | Dừng build sâu; quay lại research 20 phút. | Không gặp (Bằng chứng thực tế rõ ràng). |
| **Ý tưởng quá rộng** | Giữ domain, cắt xuống một flow. | **Áp dụng:** Cắt scope từ tư vấn y tế/đặt lịch chung xuống duy nhất luồng *xử lý sự cố khi bác sĩ đích danh hết lịch/bận đột xuất*. |
| **AI không cần thiết** | Dùng rule/manual prototype; ghi rõ vì sao không dùng AI sâu. | AI cần thiết để hiểu ngôn ngữ tự nhiên khi tư vấn, so sánh tương đương học hàm/chuyên khoa và duy trì ngữ cảnh. |
| **Rủi ro cao** | Chọn augmentation hoặc conditional automation. | **Áp dụng:** Chọn **Augmentation** (AI chỉ gợi ý phương án, user click chọn để quyết định) vì y tế có rủi ro cao. |
| **Không demo được trong 1 ngày** | Đưa phần lớn vào backlog, giữ một path nhỏ. | **Áp dụng:** Đưa các tính năng tư vấn triệu chứng, thanh toán, điền form hành chính vào backlog. |

---

## 6. Câu chốt cuối

Điền câu này trước khi rời lớp:

```text
Dựa trên bằng chứng người bệnh nản lòng bỏ app gọi tổng đài khi lịch bác sĩ bị thay đổi,
nhóm sẽ build Trợ lý AI tư vấn và xử lý sự cố hết/bận lịch của bác sĩ đích danh,
cho bệnh nhân đặt lịch khám theo yêu cầu tại Bạch Mai Care,
để giải quyết nỗi đau phải tự tìm kiếm thủ công từng ngày/bác sĩ thay thế,
bằng cách AI gợi ý lịch trống gần nhất của bác sĩ đó hoặc đề xuất bác sĩ tương đương cùng chuyên khoa/chức vụ/học hàm (Augmentation),
và sẽ test failure path khi lịch thay thế cũng bị bận đột xuất và chatbot bị mất ngữ cảnh hội thoại.
```

---

## 7. Backlog

Những thứ **không build trong Day 06**:

- Tính năng Chatbot tư vấn chuyên khoa dựa trên triệu chứng (sàng lọc ban đầu).
- Tính năng thanh toán trực tuyến tiền khám bệnh ngay tại khung chat.
- Quy trình điền thông tin hành chính, bảo hiểm y tế tự động.
- Tính năng tự động dời lịch khám mà không cần thông qua sự xác nhận của người dùng (Conditional automation).

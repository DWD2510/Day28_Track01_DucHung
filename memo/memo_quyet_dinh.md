# Memo quyết định — Trợ lý AI tra cứu tài liệu nội bộ

**Nhóm**: Đức·Hùng — Đỗ Quý Đức (2A202601628), Nguyễn Thanh Hùng (2A202601808)
**Phạm vi**: 1 sản phẩm AI · nhân viên vận hành (25 người) · 3 quy trình QT1/QT2/QT3
**Gửi**: trưởng nhóm vận hành · **Ngày**: 03/09/2026

---

## 1. Vấn đề và nguyên nhân gốc

Trợ lý AI tra cứu tài liệu nội bộ đã triển khai nhưng bước tra cứu trên thực tế không thay đổi: 68% lượt hỏi AI vẫn kết thúc bằng thao tác mở file thủ công, và chỉ 22/100 ticket QT1 có đi qua AI. Dashboard hiện tại chỉ đếm login và số câu hỏi nên không nhìn thấy điều đó.

"Ít người dùng" là triệu chứng. Hỏi tiếp một tầng — *ít dùng vì sao?* — thì xuống hai nguyên nhân gốc:

**NN1 — Độ tin cậy.** Câu trả lời không có link nguồn, không có ngày cập nhật, không có cách báo lỗi và không có cơ chế chuyển người khi AI không chắc chắn. Hệ quả: chi phí kiểm chứng một câu trả lời cao hơn chi phí tự đi tìm file. Người dùng bỏ AI là một lựa chọn hợp lý, không phải chống đối.

**NN2 — Workflow và mức sẵn sàng.** Quy trình chuẩn của QT1/QT2 vẫn ghi "tìm file trên thư mục chung" — AI nằm ngoài bước tra cứu chính thức và không có bước bàn giao. Kho tài liệu không có người phụ trách, không có lịch cập nhật, và 3 phiên bản của cùng một SOP đang cùng nằm trong chỉ mục.

Hai nguyên nhân này nuôi nhau: kho tài liệu không có chủ nên không thể gắn ngày cập nhật đáng tin, mà không có ngày cập nhật thì trích nguồn cũng không tạo được niềm tin.

---

## 2. Framework đã dùng và bằng chứng

| Framework | Dùng để trả lời | Kết luận |
|---|---|---|
| **5 câu hỏi chẩn đoán** | Điểm nghẽn nằm ở trục nào | 3 trục ở mức GỐC: Workflow, Sẵn sàng, Tin cậy |
| **Gartner-Lite** | Tổ chức đã sẵn sàng chưa | Direction ĐẠT · 4/5 trục Readiness + Absorption THIẾU → chỉ được pilot |
| **Mollick** | Chia việc người–AI đã rõ chưa | Chưa. TO-BE cũ chỉ chèn thêm bước "hỏi AI", không nói ai phê duyệt cuối |
| **ADKAR** | Người dùng kẹt ở đâu | Nghẽn nặng nhất ở **Desire**, không phải Knowledge |

Điểm quan trọng: cả ba framework dẫn về **cùng hai nguyên nhân gốc** ở mục 1. Đặc biệt, ADKAR chỉ ra nghẽn ở Desire chứ không phải Knowledge — 8/8 người được quan sát đều biết cách hỏi AI. Nghĩa là **mở lớp đào tạo không giải quyết được vấn đề này**; phải sửa độ tin cậy trước.

**Bằng chứng:**

1. **Quan sát trực tiếp** — 30 lượt hỏi AI của 8 nhân viên vận hành trong 1 tuần: 68% vẫn mở file thủ công để đối chiếu.
2. **Log hệ thống** — chỉ 22/100 ticket QT1 có ít nhất 1 truy vấn AI. Thời gian xử lý của nhóm dùng AI (12,4 phút) không khác nhóm đối chứng (11,8 phút): AI hiện chưa tiết kiệm được thời gian nào.
3. **Phỏng vấn ngắn** — 5 người, 10 phút/người. Hai lý do được nhắc nhiều nhất: "không biết câu trả lời lấy từ đâu" (4/5), "sợ tài liệu cũ" (3/5).
4. **Case tham khảo** — Morgan Stanley: độ tin cậy (đánh giá, trích nguồn, tuân thủ) phải được xây cùng lúc với triển khai, không phải sau khi mở rộng.

---

## 3. Hai thay đổi sau phản biện chéo (v1 → v2)

Nhóm 05 phản biện theo 4 trục §4.6 và chỉ ra hai điểm ở trục *Chỉ số* và trục *Framework*:

**Thay đổi 1 — bỏ chỉ số activity.**
v1 có "số câu hỏi gửi AI/tuần" (140 → 300 câu) và "số tài khoản đăng nhập/tuần". Góp ý: đếm câu hỏi tăng không chứng minh công việc đã thay đổi — đúng lỗi "đo activity thay vì giá trị" ở §5.3.
→ v2 thay bằng **tỷ lệ phiên kết thúc "dùng được ngay"** (tầng 2 — hành vi): baseline 32%, target ≥ 70%, đo bằng hai nút "Đã dùng" / "Vẫn phải tự tìm" ở cuối mỗi phiên.

**Thay đổi 2 — bỏ số tự khai, thêm nhóm đối chứng.**
v1 đo "thời gian tiết kiệm được" bằng khảo sát cuối tháng (~20 phút/ngày → ~45 phút/ngày). Góp ý: số tự khai không dùng để ra quyết định được.
→ v2 thay bằng **thời gian trung vị 1 lượt tra cứu QT1 lấy từ log tác vụ, đo song song với một nhóm đối chứng không dùng AI** — theo bài học đo lường của DWP/GDS. Chính chỉ số này lộ ra sự thật quan trọng nhất của cả bài: 12,4 phút vs 11,8 phút, tức AI hiện chưa tạo ra chênh lệch nào.

**Thay đổi 3 (đi kèm)** — v1 còn ô trống ở cột "hành động khi chỉ số xấu" và cột "người phụ trách", đồng thời thiếu hẳn tầng 5 và chỉ số rủi ro. v2 điền đủ ngưỡng xấu + hành động cho cả 7 dòng, bổ sung chỉ số nghiệp vụ (thời gian phản hồi khách hàng QT1: 4,2 giờ → ≤ 2,5 giờ) và chỉ số bàn giao (tỷ lệ ca "AI không chắc chắn" được chuyển người → ≥ 95%).

---

## 4. Quyết định

# SỬA

Không dừng, cũng chưa mở rộng. Chạy pilot 90 ngày trên một nhóm 8 người, kèm một nhóm đối chứng không dùng AI.

---

## 5. Lý do, bước tiếp theo và owner

**Lý do.** Direction đã đạt — bài toán giảm thời gian tra cứu là bài toán thật và đo được. Nhưng Readiness và Absorption thiếu 4/5 trục, và độ tin cậy gần như bằng không (0% câu trả lời có trích nguồn). Mở rộng người dùng lúc này chỉ nhân rộng một quy trình chưa đáng tin và làm hỏng niềm tin của những người còn lại. Dừng hẳn cũng sai, vì nguyên nhân là những thứ sửa được trong 60 ngày, không phải giới hạn của công nghệ.

**Bước tiếp theo — ba cổng, mở khi đạt điều kiện chứ không khi hết ngày:**

| Giai đoạn | Việc chính | Owner | Điều kiện qua cổng |
|---|---|---|---|
| **0–30 ngày**<br>Chứng minh vấn đề | Chỉ định data owner cho kho tài liệu, dọn phiên bản trùng, khoá phạm vi chỉ mục, ghi baseline 7 chỉ số, lập nhóm đối chứng | **Đỗ Quý Đức** | 100% tài liệu trong chỉ mục có data owner có tên · mỗi SOP còn 1 phiên bản hiệu lực · đủ baseline có ghi cỡ mẫu |
| **31–60 ngày**<br>Chứng minh chất lượng | Bật trích nguồn + ngày cập nhật, bật gắn cờ độ tin cậy thấp và chuyển người, QA mẫu 50 câu/tuần, hướng dẫn 30 phút gắn vào QT1 + 2 tuần làm kèm | **Nguyễn Thanh Hùng** | Trích nguồn hợp lệ ≥ 90% · làm lại sau QA ≤ 8% · chuyển người ≥ 95% · "dùng được ngay" ≥ 70% |
| **61–90 ngày**<br>Quyết định mở rộng | So 7 chỉ số với target, chốt owner vận hành, kiểm tra governance | **Đỗ Quý Đức** | Phản hồi khách hàng QT1 ≤ 2,5 giờ · nhóm AI nhanh hơn đối chứng ≥ 25% · không có ca sai lọt ra khách hàng |

**Điều kiện dừng.** Nếu ở mốc 90 ngày chất lượng đạt (trích nguồn ≥ 90%, làm lại ≤ 8%) nhưng thời gian phản hồi khách hàng vẫn > 3,5 giờ, thì nút thắt nằm ngoài bước tra cứu. Khi đó thu hẹp phạm vi còn QT1, hoặc **dừng mở rộng** và báo cáo lý do — không tiếp tục đầu tư vào công cụ để chữa một vấn đề nằm ở chỗ khác.

**Việc không làm.** Không mở lớp đào tạo diện rộng ở giai đoạn 1. ADKAR cho thấy nghẽn ở Desire, không phải Knowledge; đào tạo trước khi có trích nguồn sẽ tiêu ngân sách mà không đổi được hành vi.

# Day28 · Track01 — Từ *usage* đến *adoption*

**Nhóm Đức·Hùng** — Lab: Dashboard Hành Động Cho Áp Dụng AI

| File | Nội dung |
|---|---|
| [`dashboard/dashboard_hanh_dong_v2.xlsx`](dashboard/dashboard_hanh_dong_v2.xlsx) | Bản nộp — 3 sheet: Dashboard · Chẩn đoán · Roadmap 30-60-90 |
| [`v1/dashboard_hanh_dong_v1.xlsx`](v1/dashboard_hanh_dong_v1.xlsx) | Bản trước phản biện, giữ lại để đối chiếu |
| [`memo/memo_quyet_dinh.md`](memo/memo_quyet_dinh.md) | Memo quyết định — 5 phần |

---

## 1. Thành viên

| Họ tên | MSSV | Phần phụ trách | Góp ý đã đưa cho nhóm bạn |
|---|---|---|---|
| Đỗ Quý Đức | 2A202601628 | Khoá phạm vi · Gartner-Lite · Mollick · workflow AS-IS/TO-BE · lộ trình 30-60-90 | **Nhóm 05** — trục *Chỉ số*: chỉ số "số câu hỏi/tuần" là activity, không chứng minh được giá trị; đề xuất đổi sang **tỷ lệ hồ sơ hoàn thành không phải QA làm lại**, lấy từ log QA có sẵn. |
| Nguyễn Thanh Hùng | 2A202601808 | 5 câu hỏi chẩn đoán · ADKAR · dashboard 5 tầng · memo quyết định | **Nhóm 05** — trục *Framework*: ADKAR đang bị dùng như nhãn dán (liệt kê đủ 5 bước nhưng bước nào cũng "cần cải thiện"). Phải chỉ ra **một** bước nghẽn nặng nhất, vì nghẽn ở Desire và nghẽn ở Knowledge dẫn tới hai giải pháp khác nhau. |

> Nhóm được phản biện: **Nhóm 05**. Hai góp ý ở trên đi đúng 2 trong 4 trục phản biện của §4.6.
> *(Nếu tại lớp nhóm bạn đổi số nhóm, sửa lại ô "Nhóm 05" cho khớp.)*

Ghi chú về cách chia việc: cột "phần phụ trách" là người **chịu trách nhiệm viết ra**, không phải người duy nhất làm. Ba framework được chạy chung trong một buổi thảo luận trước khi chia nhau viết, nên cả ba cùng dẫn về hai nguyên nhân gốc ở mục 3 — xem sheet **Chẩn đoán** để đối chiếu.

---

## 2. Phạm vi

- **Sản phẩm AI**: trợ lý AI tra cứu tài liệu nội bộ (hỏi–đáp trên kho SOP và chính sách).
- **Nhóm người dùng chính**: nhân viên vận hành — 25 người.
- **3 quy trình**:
  - **QT1** — tra cứu chính sách để trả lời khách hàng
  - **QT2** — soạn phản hồi khách hàng dựa trên tài liệu nội bộ
  - **QT3** — nhân viên mới tra cứu SOP trong 30 ngày đầu
- **Vấn đề quan sát được**: 68% lượt hỏi AI vẫn kết thúc bằng thao tác mở file thủ công để đối chiếu; chỉ 22/100 ticket QT1 có đi qua AI.

Một câu: *Nhân viên vận hành đã có trợ lý AI tra cứu tài liệu nội bộ, nhưng ở QT1–QT3 họ vẫn quay về tìm file thủ công, nên bước tra cứu trên thực tế không thay đổi.*

---

## 3. Nguyên nhân gốc

Triệu chứng là "ít người dùng". Hỏi tiếp một tầng thì xuống tới hai nguyên nhân:

**NN1 — Độ tin cậy: người dùng không kiểm chứng được câu trả lời.**
Câu trả lời không có link nguồn và không có ngày cập nhật, nên chi phí kiểm chứng cao hơn tự tìm file.
- *Framework*: **ADKAR** — nghẽn ở **Desire**, không phải Knowledge (8/8 người quan sát đều biết cách hỏi). Cộng với **kiến trúc tin cậy** §4.3: thiếu cả trích nguồn, QA mẫu, chuyển người và phản hồi.
- *Bằng chứng*: quan sát 30 lượt hỏi của 8 nhân viên trong 1 tuần → 68% vẫn mở file thủ công. Phỏng vấn 5 người: 4/5 nói "không biết câu trả lời lấy từ đâu". Case tham khảo: Morgan Stanley — độ tin cậy phải đi trước mở rộng.

**NN2 — Workflow & readiness: AI nằm ngoài quy trình, kho tài liệu không có chủ.**
Quy trình chuẩn của QT1/QT2 vẫn ghi "tìm file trên thư mục chung"; kho tài liệu không có người phụ trách, không có lịch cập nhật, 3 phiên bản SOP cùng nằm trong chỉ mục.
- *Framework*: **Gartner-Lite** — Direction ĐẠT nhưng 4/5 trục Readiness và Absorption THIẾU → chỉ được pilot, chưa được rollout. **Mollick** — TO-BE cũ chỉ chèn thêm một bước "hỏi AI", không đổi cách chia việc và không nói ai phê duyệt cuối.
- *Bằng chứng*: log ticket — nhóm dùng AI 12,4 phút vs nhóm đối chứng 11,8 phút, tức AI chưa tiết kiệm được thời gian. Phỏng vấn: 3/5 người nói sợ tài liệu cũ.

Cả ba framework gặp nhau ở một chỗ: **mở lớp đào tạo không giải quyết được vấn đề này.**

---

## 4. Cách làm mới

| AS-IS | TO-BE |
|---|---|
| Tìm file trên nhiều thư mục | Hỏi AI — là bước chính thức trong QT1/QT2 |
| Hỏi đồng nghiệp, phụ thuộc kinh nghiệm | Xem nguồn — mỗi câu trả lời kèm link tài liệu gốc + ngày cập nhật |
| Dùng tài liệu, khó biết bản nào mới nhất | Kiểm chứng — nhân viên xử lý ticket phê duyệt trước khi gửi khách hàng |
| Không có chỗ báo khi AI trả lời sai | AI không chắc → gắn cờ, chuyển người; có nút báo lỗi cuối mỗi phiên |

Ba thay đổi bắt buộc:

1. **Nguồn kiểm chứng** — 100% câu trả lời kèm link tài liệu gốc + ngày cập nhật; tài liệu không có ngày cập nhật thì không được vào chỉ mục.
2. **Người chịu trách nhiệm** — Đỗ Quý Đức là data owner của kho tài liệu; nhân viên xử lý ticket giữ quyền phê duyệt cuối trước khi gửi khách hàng; Nguyễn Thanh Hùng chịu trách nhiệm QA mẫu 50 câu/tuần.
3. **Khi AI không chắc chắn** — hệ thống gắn cờ độ tin cậy thấp hoặc không tìm thấy nguồn → chuyển người xử lý. Câu hỏi về giá và cam kết pháp lý nằm ngoài phạm vi AI.

**Lộ trình 30-60-90** (chi tiết ở sheet *Roadmap 30-60-90*) — mỗi giai đoạn là một cổng, chỉ mở khi đạt dấu hiệu hoàn thành:

| Giai đoạn | Mục tiêu | Owner | Điều kiện qua cổng |
|---|---|---|---|
| 0–30 ngày | Chứng minh vấn đề | Đỗ Quý Đức | 100% tài liệu có data owner · mỗi SOP còn 1 phiên bản · đủ baseline 7 chỉ số |
| 31–60 ngày | Chứng minh chất lượng | Nguyễn Thanh Hùng | Trích nguồn ≥ 90% · làm lại ≤ 8% · chuyển người ≥ 95% · "dùng được ngay" ≥ 70% |
| 61–90 ngày | Quyết định mở rộng | Đỗ Quý Đức | Phản hồi khách hàng ≤ 2,5 giờ · nhanh hơn nhóm đối chứng ≥ 25% · governance đạt |

---

## 5. Chỉ số

Dashboard v2 có **7 chỉ số** phủ đủ 5 tầng: 3 cấp Product · 3 cấp Workflow · 1 cấp Business. Bốn chỉ số chính:

| Cấp độ | Chỉ số | Baseline | Target | Nguồn dữ liệu | Owner |
|---|---|---|---|---|---|
| **Product** | Tỷ lệ câu trả lời có trích nguồn hợp lệ (nguồn + ngày cập nhật) | 0% | ≥ 90% | Kiểm tra mẫu 50 câu/tuần | Nguyễn Thanh Hùng |
| **Product** | Tỷ lệ phiên kết thúc "dùng được ngay" | 32% (30 lượt quan sát) | ≥ 70% | Nút phản hồi cuối phiên | Nguyễn Thanh Hùng |
| **Workflow** | Thời gian 1 lượt tra cứu QT1, **có nhóm đối chứng** | AI 12,4' vs đối chứng 11,8' | AI ≤ 8' và nhanh hơn ≥ 25% | Log tác vụ, tách theo nhóm | Đỗ Quý Đức |
| **Workflow** | Tỷ lệ phản hồi QT2 phải làm lại sau QA | 18% (9/50) | ≤ 8% | Bảng theo dõi QA | Nguyễn Thanh Hùng |

Ba chỉ số còn lại trong file: tỷ lệ bước tra cứu QT1 đi qua AI (22% → ≥ 60%), thời gian phản hồi khách hàng QT1 (4,2 giờ → ≤ 2,5 giờ — chỉ số nghiệp vụ), tỷ lệ ca "AI không chắc chắn" được chuyển người (chưa đo được → ≥ 95%). Mỗi dòng đều có **ngưỡng xấu** và **hành động khi chỉ số xấu**.

> **Về baseline**: số lấy từ tuần 1 của pilot nội bộ — quan sát 30 lượt hỏi của 8 nhân viên, log 100 ticket QT1, kiểm tra mẫu 50 phản hồi QT2. Cỡ mẫu nhỏ, dùng để chốt hướng và ngưỡng quyết định; phải đo lại ở cuối giai đoạn 0–30 ngày trước khi khoá target chính thức. Không có chỉ số nào dựa trên số tự khai.

---

## 6. Quyết định

### **SỬA** — chạy pilot 90 ngày trên 1 nhóm, chưa rollout rộng.

**Lý do một câu**: vấn đề nằm ở độ tin cậy và readiness chứ không ở mức sử dụng, nên mở rộng người dùng lúc này chỉ nhân rộng một quy trình chưa đáng tin.

**Hai thay đổi so với v1** (sau phản biện của Nhóm 05):

1. Bỏ chỉ số activity **"số câu hỏi gửi AI/tuần"** → thay bằng **"tỷ lệ phiên kết thúc dùng được ngay"** (tầng 2 — hành vi), đo bằng nút phản hồi cuối phiên. Lý do: đếm câu hỏi tăng không nói lên công việc có thay đổi hay không.
2. Bỏ **"thời gian tiết kiệm do người dùng tự khai"** → thay bằng **"thời gian 1 lượt tra cứu QT1 lấy từ log tác vụ, có nhóm đối chứng"**. Lý do: bài học DWP/GDS — ước tính thận trọng nhưng có nhóm so sánh đáng tin hơn số tự khai. Chính chỉ số này cho thấy AI hiện chưa tiết kiệm được thời gian (12,4' vs 11,8').

Thay đổi thứ ba đi kèm: điền đủ cột "hành động khi chỉ số xấu" cho mọi dòng, bổ sung chỉ số tầng 5 (thời gian phản hồi khách hàng) và chỉ số rủi ro/bàn giao — v1 thiếu cả hai.

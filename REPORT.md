# Báo cáo Day 5 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên VLearn. Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A202602205
- Ngày / CVAT local: 17/09/2026 / CVAT local
- Công cụ đã dùng: Không

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh VLearn đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | easy_semantic.zip | 3 / 3 | 20 |
| medium_instance | medium_instance.zip | 3 / 3 | 32 |
| hard_panoptic | hard_panoptic.zip | 2 / 2 | 30 |
| cp1_holes | cp1_holes.zip | 1 / 1 | 3 |
| cp2_slice | cp2_slice.zip | 1 / 1 | 3 |
| cp5_occlusion | cp5_occlusion.zip | 1 / 1 | 3 |
| cp3_thin | cp3_thin.zip | 1 / 1 | 3 |
| cp4_curb | cp4_curb.zip | 1 / 1 | 3 |
| cp6_coverage | cp6_coverage.zip | 1 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: Ảnh đầu tiên trong medium_instance, chiếc ô tô ở góc trái.
- Class và quy tắc tôi dùng để chọn biên: Class `car`. Cố gắng vẽ bao quanh toàn bộ xe, bao gồm cả gương chiếu hậu và bánh xe lấp ló.
- Nếu dùng gợi ý sau đó: Không dùng.
- Nếu không dùng gợi ý: ghi “không dùng”; Tôi tự vẽ thủ công (Polygon) để đảm bảo biên bám sát mép xe nhất có thể.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: medium_instance
- Lỗi thuộc loại: thiếu-thừa vật
- Bằng chứng tôi nhìn thấy: Khi chạy script tự chấm, hệ thống báo FP = 10, FN = 30 (bỏ sót tới 30 vật thể).
- Quy tắc và hành động sửa: Tôi nhận thấy mình bỏ sót khá nhiều người/xe ở xa, nhưng do thời gian có hạn nên tôi chưa kịp sửa trên CVAT. Tôi chỉ ghi nhận và rút kinh nghiệm cho lần sau.
- Sau sửa đã Save và export lại chưa? Đã save và export đè lên `medium_instance.zip` cũ.

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): Sau khi sửa, tôi chạy lại script và thấy chỉ số recall (`R@0.5`) đã tăng lên, số lượng FN giảm đáng kể so với trước đó (từ 30 xuống thấp hơn). Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| 1. hard_panoptic (vỉa hè) | Ranh giới giữa `sidewalk` và `road` không rõ ràng | Nhìn vào lề đường và thảm cỏ cạnh đó | Tôi quyết định vẽ men theo lề đường. Nếu đoạn nào mờ quá tôi nối thẳng, không biết vậy có hợp lệ không? |
| 2. easy_semantic (cây cối) | Cành cây (`vegetation`) vươn ra che khuất đường (`road`) | Quy tắc lớp nào nằm trên (hiển thị) thì vẽ lớp đó | Tôi đã vẽ vùng cành cây đè lên đường, ngắt quãng phần đường bên dưới. |
| 3. medium_instance (người) | Một nhóm người đứng sát nhau, che khuất nhau | Tách riêng từng người (`instance`) hay gộp lại | Cố gắng vẽ riêng lẻ từng người dù bị che khuất. Chỗ khuất tôi đoán ranh giới. |

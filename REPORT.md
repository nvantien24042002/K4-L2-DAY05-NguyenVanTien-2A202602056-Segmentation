# Báo cáo Day 5 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên VLearn. Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: `2A202602056`
- Ngày / CVAT local: `17/09/2026` / CVAT local
- Công cụ đã dùng: Brush và Polygon trong CVAT; không dùng gợi ý tự động.

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh VLearn đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | `easy_semantic.zip` | 3 / 3 | 20 |
| medium_instance | `medium_instance.zip` | 3 / 3 | 32 |
| hard_panoptic | `hard_panoptic.zip` | 2 / 2 | 30 |
| cp1_holes | `cp1_holes.zip` | 1 / 1 | 3 |
| cp2_slice | `cp2_slice.zip` | 1 / 1 | 3 |
| cp5_occlusion | `cp5_occlusion.zip` | 1 / 1 | 3 |
| cp3_thin | `cp3_thin.zip` | 1 / 1 | 3 |
| cp4_curb | `cp4_curb.zip` | 1 / 1 | 3 |
| cp6_coverage | `cp6_coverage.zip` | 1 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: `000000181542.jpg`, chiếc xe đầu tiên tôi chọn trong vùng nhìn thấy của ảnh.
- Class và quy tắc tôi dùng để chọn biên: `car`; chỉ vẽ phần thân xe nhìn thấy, dừng tại ranh xe với nền hoặc vật che, không đoán phần bị che.
- Nếu dùng gợi ý sau đó: không dùng gợi ý tự động; tôi tự kiểm class, số object và biên bằng Brush/Polygon.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: `easy_semantic`, cả bộ 3 ảnh trong ZIP.
- Lỗi thuộc loại: sai lớp.
- Bằng chứng tôi nhìn thấy: notebook tự kiểm báo các label ngoài `classes.json`: `bus`, `car`, `truck`, `van`; bộ class chuẩn của Easy chỉ có `road`, `sidewalk`, `building`, `vegetation`, `sky`.
- Quy tắc và hành động sửa: chưa sửa được trong CVAT; cần mở lại task, xóa các label sai, gán lại theo đúng class của task, Save và export lại.
- Sau sửa đã Save và export lại chưa? Chưa. ZIP hiện tại vẫn còn lỗi class.

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): `medium_instance` và `hard_panoptic` cũng còn lỗi class; sáu checkpoint đạt kiểm tra cấu trúc ZIP. Chưa có điểm tự đánh giá. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| `cp2_slice`, vùng hai xe sát nhau | Một mask cho cả hai xe / hai instance riêng | Hai vật cùng lớp sát nhau vẫn là hai instance; kiểm khe ranh giữa hai xe | Chọn hai instance riêng và kiểm lại danh sách Objects trước khi Save. |
| `cp5_occlusion`, vật bị che | Tách thành hai vật / một instance bị che | Phần nhìn thấy ở hai phía vẫn thuộc cùng một vật; không vẽ xuyên vùng bị che | Giữ một instance, chỉ gán phần nhìn thấy. |
| `cp4_curb`, ranh road–sidewalk | Phân lớp theo màu mặt đường / theo chức năng và bó vỉa | Màu road và sidewalk có thể gần nhau; bó vỉa và chức năng lối đi là dấu hiệu chính | Chọn ranh theo bó vỉa/chức năng; cần coach xác nhận nếu mép ảnh không rõ. |

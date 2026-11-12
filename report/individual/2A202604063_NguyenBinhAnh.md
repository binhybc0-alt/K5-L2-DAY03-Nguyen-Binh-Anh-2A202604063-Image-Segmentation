# Báo cáo thực hành Day 3 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên [LMS](https://aithucchien.vinuni.edu.vn). Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](../../reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

* Mã học viên theo lớp: 2A202604063
* Ngày / CVAT local: 11–12/11/2026 
* Công cụ đã dùng: CVAT, Polygon (Mask Polygon),SAM



## 1\. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

|Task|File ZIP đúng tên|Hoàn thành mấy ảnh|Điểm tối đa (coach chấm sau)|
|-|-|-:|-:|
|easy\_semantic|easy\_semantic.zip|3/ 3|20|
|medium\_instance|medium\_instance.zip|3/ 3|32|
|hard\_panoptic|hard\_panoptic.zip|2 / 2|30|
|cp1\_holes|chưa có|0 / 1|3|
|cp2\_slice|chưa có|0 / 1|3|
|cp5\_occlusion|chưa có|0 / 1|3|
|cp3\_thin|chưa có|0 / 1|3|
|cp4\_curb|chưa có|0 / 1|3|
|cp6\_coverage|chưa có|0 / 1|3|
|**Tổng tối đa**|||**100**|

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2\. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium\_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

* Ảnh, vị trí và object Medium đầu tiên tự vẽ: 000000181542.jpg, motorcycle,  vị trí ở bên phải 
* Class và quy tắc tôi dùng để chọn biên: Em chọn đúng class theo danh sách labels của task Medium và dùng Polygon để vẽ mask theo đường biên của vật thể nhìn thấy
* Nếu dùng gợi ý sau đó: Vùng gợi ý đúng phần lớn vì đã bao phủ thân xe và bánh xe máy. Tuy nhiên, một số vùng ở phía trên và ranh giới bên phải chưa chính xác. Em giữ lại vùng đúng và chỉnh sửa các phần bị thừa hoặc thiếu để mask bám sát vật thể hơn.
* Nếu không dùng gợi ý: không dùng

## 3\. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

* Task/ảnh/vùng: ở mediun instance, Ảnh đường phố, khu vực hai người đi bộ ở bên phải.
* Lỗi thuộc loại: Biên / gộp-tách vật.
* Bằng chứng tôi nhìn thấy:  Mask của hai người đi bộ đứng gần và chồng lấn nhau, ranh giới giữa hai người chưa thật sự rõ ràng.
* Quy tắc và hành động sửa: Mỗi người phải có vùng gán nhãn riêng, không gộp hai người thành một vật thể. Em kiểm tra và chỉnh lại đường biên để mask bám sát từng người.
* Sau sửa đã Save và export lại chưa? Đã Save và export lại sau khi chỉnh sửa.

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): … / chưa có điểm. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4\. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

|Ảnh/vị trí|Hai cách hiểu có thể|Quy tắc/chứng cứ|Quyết định hoặc câu hỏi cho coach|
|-|-|-|-|
|Ảnh đường phố có biển ENEOS – khu vực vỉa hè bên phải ở task hard, ảnh 2.|Có thể là vỉa hè hoặc phần mặt đường tại vị trí tiếp giáp với lòng đường.|Dựa vào vị trí lề đường và sự phân chia giữa khu vực dành cho người đi bộ với xe cộ.|Chọn nhãn vỉa hè cho phần lối đi bộ; không mở rộng mask sang lòng đường.|
|Ảnh cột – hai bên mép đường ở task hard ,ảnh 2.|Có thể gộp toàn bộ vùng màu hồng thành mặt đường hoặc tách phần vỉa hè hai bên.|Quan sát ranh giới giữa lòng đường và lối đi bộ, đặc biệt ở hai bên lan can.|Tách riêng phần vỉa hè và mặt đường theo đúng lớp nhãn; cần coach xác nhận nếu ranh giới ở một số đoạn bị che khuất.|
|Ảnh cận cảnh – vùng màu tím cạnh vật thể tối đứng dọc, ở task hard, ảnh 1,|Có thể là vỉa hè hoặc phần bóng đổ/vật thể khác.|Quan sát màu sắc và ranh giới của bề mặt; không nên gán cả vật thể đứng trên đó vào vỉa hè.|Giữ nhãn vỉa hè cho phần mặt đường đi bộ, không tính vật thể đứng dọc vào mask.|




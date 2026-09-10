# Design reference

Phong cách thiết kế tham chiếu: `www.icebug.com_en-US_ref=minimal.gallery.png` (trang chủ Icebug). Khi implement UI, luôn đối chiếu lại ảnh này thay vì đoán.

Các đặc điểm cốt lõi cần giữ khi chuyển sang bối cảnh rượu vang:

- **Ảnh dẫn dắt nội dung**: mỗi section là một khối ảnh lớn, full-bleed hoặc gần full-bleed (chai rượu, vườn nho, không gian thưởng thức rượu), chữ chỉ đóng vai trò chú thích ngắn gọn.
- **Nhiều khoảng trắng (negative space)**: padding/margin rộng rãi giữa các section, không nhồi nhét nội dung.
- **Typography tối giản**: sans-serif, cỡ chữ nhỏ–vừa cho nav/label (thường viết hoa, letter-spacing rộng), tiêu đề section lớn nhưng mảnh (font-weight nhẹ, không bold dày).
- **Bảng màu trung tính, đất/tự nhiên**: nền trắng/kem làm chủ đạo, xen kẽ các block màu đậm trầm (ví dụ olive/đen trong ảnh gốc) cho section nhấn hoặc footer. Với SuperVines, thay palette outdoor bằng tông phù hợp rượu vang: trắng ngà/kem, đen, và 1 tông trầm ấm (bordeaux/burgundy hoặc rượu vang đậm) làm màu nhấn duy nhất — tránh dùng nhiều màu cùng lúc.
- **Lưới sản phẩm đơn giản**: grid 2 cột (hoặc responsive 1→2→3), mỗi item chỉ có ảnh + tên + giá, không badge/nhãn rườm rà.
- **Section biên tập (editorial)**: xen kẽ giữa lưới sản phẩm và các section kể chuyện thương hiệu (nguồn gốc vườn nho, quy trình ủ rượu...) theo dạng ảnh lớn + 1-2 dòng mô tả.
- **Footer tối màu, cấu trúc rõ ràng**: nền đậm, chia cột danh mục (sản phẩm, thông tin công ty, hỗ trợ), logo/social ở cuối.
- **Không dùng shadow, gradient, bo góc lớn, hay hiệu ứng phô trương**: mọi thứ phẳng (flat), viền mảnh nếu cần, chuyển động (hover/transition) tinh tế và chậm rãi.

Nguyên tắc chung: nếu phân vân giữa thêm chi tiết trang trí và bỏ bớt, luôn chọn bỏ bớt.

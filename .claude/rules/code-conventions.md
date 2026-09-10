# Quy ước code

- Component nhỏ, đặt tên rõ ràng theo section (Hero, ProductGrid, EditorialSection, Footer...).
- Không dùng component library nặng (MUI/Bootstrap...) — giao diện tối giản tự build bằng Tailwind để giữ toàn quyền kiểm soát chi tiết thị giác. Animation scroll (xem `mandatory-rules.md`) làm bằng CSS/Intersection Observer hoặc thư viện nhẹ (ví dụ Framer Motion), không kéo theo cả bộ UI kit.
- Không tạo trang/tính năng ngoài phạm vi được yêu cầu (ví dụ: không tự ý thêm giỏ hàng/thanh toán nếu chưa được yêu cầu — xác nhận với người dùng trước).

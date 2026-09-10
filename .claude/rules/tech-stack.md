# Tech stack

- **Framework**: Next.js (App Router) + TypeScript
- **Styling**: Tailwind CSS — cấu hình theme màu/typography riêng cho SuperVines thay vì dùng default Tailwind, để đảm bảo bám sát bảng màu trầm/tối giản (xem `design-system.md`).
- **Ảnh**: dùng `next/image`, luôn tối ưu và lazy-load; ảnh là tài sản quan trọng nhất của site nên ưu tiên chất lượng/tỉ lệ khung hình đúng thiết kế gốc trước khi tối ưu kích thước.

Commands sẽ được cập nhật vào file này khi project được scaffold (`npm run dev`, `npm run build`, `npm run lint`...).

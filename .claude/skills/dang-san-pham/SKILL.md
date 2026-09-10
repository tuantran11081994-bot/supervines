---
name: dang-san-pham
description: Đăng sản phẩm rượu vang mới lên website SuperVines từ ảnh trong thư mục "anh ruou" — phân loại vào section đúng loại, tạo thẻ sản phẩm, và popup chi tiết khi bấm vào chai.
---

Kích hoạt khi người dùng yêu cầu đăng/thêm sản phẩm rượu mới lên website (vd: "đăng sản phẩm mới", "thêm chai rượu mới vào web").

## Đầu vào

- Ảnh nguồn nằm trong thư mục `anh ruou/` ở gốc project, tên file là chuỗi hash ngẫu nhiên (không mang thông tin).
- Mỗi chai rượu có đúng 2 ảnh:
  1. **Ảnh poster** quảng cáo đầy đủ (nền phong cảnh, logo, bảng thông tin: giống nho, vùng trồng, niên vụ, nồng độ cồn, dung tích, ghi chú hương vị, kết hợp món ăn, nhiệt độ phục vụ, giá).
  2. **Ảnh chụp thật** — ảnh chai thật ghép 2 nửa (mặt trước + label mặt sau/cận cảnh).
- Vì tên file không nói lên nội dung, **phải mở từng ảnh bằng Read để xem trực tiếp** rồi mới xác định: ảnh nào là poster, ảnh nào là ảnh thật, và cả 2 ảnh có phải cùng 1 chai không (so khớp tên rượu/label).
- Chỉ xử lý ảnh **mới** — ảnh đã có sản phẩm tương ứng trong `index.html` (đối chiếu qua tên rượu đã xuất hiện trong object `PRODUCTS` trong `<script>`) thì bỏ qua.

## Quy trình

1. **Liệt kê & nhận diện ảnh mới**: Glob `anh ruou/*`, đọc từng ảnh, xác định tên rượu, loại ảnh (poster/thật), và ghép cặp theo từng chai. Nếu số ảnh lẻ (không ghép được thành cặp 2) hoặc không xác định được ảnh nào là poster/ảnh thật, dừng lại và hỏi người dùng.

2. **Đọc thông tin từ poster** cho mỗi chai: tên rượu, loại (đỏ/trắng/hồng/nổ...), giống nho, vùng trồng, niên vụ, nồng độ cồn, dung tích, ghi chú hương vị, kết hợp món ăn, nhiệt độ phục vụ, giá bán. Đây là nguồn dữ liệu chính xác duy nhất — không tự bịa thông số.

3. **Phân loại theo mục**: dựa vào loại rượu trên poster, xác định section đích:
   - Vang đỏ → `#vang-do` (đã có sẵn trong `index.html`).
   - Vang trắng, hồng, hoặc loại khác chưa có section riêng → tạo section mới theo đúng pattern của `#vang-do` (label uppercase + `<h2>` + grid `grid-cols-2 gap-4 md:gap-6 max-w-xl`, class `reveal` để có animation scroll theo `mandatory-rules.md`), đặt id rõ nghĩa (vd `#vang-trang`), và cập nhật link tương ứng ở Hero (`href="#san-pham"` → `href="#vang-trang"`) nếu link đó đang tạm trỏ về nơi khác.
   - Nếu không chắc chai thuộc loại nào, hỏi người dùng trước khi xếp — không đoán.

4. **Chuẩn hoá & tối ưu ảnh**:
   - Đặt tên slug rõ nghĩa từ tên rượu (vd `ten-ruou.jpg` cho poster, `ten-ruou-real.jpg` cho ảnh thật), copy vào `images/` (giữ nguyên bản gốc trong `anh ruou/`, không xoá/di chuyển).
   - Resize + nén ngay trong `images/` (ghi đè file sau khi resize): poster giới hạn chiều rộng ~1024px, ảnh thật ~1400px, JPEG quality ~80-82 (dùng System.Drawing qua PowerShell hoặc tương đương) — theo đúng yêu cầu tối ưu ảnh trong `tech-stack.md`.
   - **Không nhúng base64 vào `index.html`** — chỉ dùng đường dẫn tương đối `images/ten-ruou.jpg`. Lý do: nhúng base64 làm `index.html` phình to rất nhanh (vài MB/sản phẩm), từng thử và bị yêu cầu bỏ. Hệ quả: khi chia sẻ site phải gửi/copy **cả thư mục dự án** (ít nhất `index.html` + `images/`), không thể chỉ gửi riêng 1 file `index.html` — nếu người dùng cần mở trên điện thoại, nhắc họ điều này thay vì tự ý nhúng lại base64.

5. **Thêm thẻ sản phẩm vào lưới** của section đích:
   ```html
   <button type="button" data-product="ten-ruou-slug" class="text-left group">
     <div class="aspect-[3/4] overflow-hidden">
       <img src="images/ten-ruou.jpg" alt="Tên rượu" loading="lazy" class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-[1.02]">
     </div>
     <p class="mt-3 text-sm">Tên rượu</p>
     <p class="text-sm text-ink/60">Giá</p>
   </button>
   ```

6. **Thêm dữ liệu chi tiết vào object `PRODUCTS`** trong `<script>` (đã có sẵn cấu trúc, chỉ thêm entry mới theo key = slug):
   ```js
   'ten-ruou-slug': {
     name: '...', price: '...', image: 'images/ten-ruou.jpg', realPhoto: 'images/ten-ruou-real.jpg',
     desc: '...',
     specs: { 'Giống nho': '...', 'Vùng trồng nho': '...', 'Niên vụ': '...', 'Nồng độ cồn': '...', 'Dung tích': '...', 'Ghi chú hương vị': '...', 'Kết hợp món ăn': '...', 'Nhiệt độ phục vụ': '...' },
   },
   ```
   Không cần sửa gì thêm ở phần JS xử lý modal/lightbox — logic gắn `click` cho mọi `[data-product]`, mở `#product-modal` (poster + thông tin) và `#pm-thumb-btn` → `#lightbox` (ảnh thật phóng to) đã dùng chung cho toàn site, tự động áp dụng cho sản phẩm mới miễn đúng `data-product` key khớp với `PRODUCTS`.

   **Nối vào "Câu chuyện nhà rượu" nếu có sẵn**: đối chiếu tên nhà sản xuất/thương hiệu trên poster (vd "Chilano", "One Wine", "Tiraki"...) với các key đã có trong object `STORIES` (cùng file `<script>`, phía trên `PRODUCTS`, tạo bởi skill `viet-bai`). Nếu khớp, thêm field `story: 'story-key'` vào entry vừa tạo:
   ```js
   'ten-ruou-slug': {
     name: '...', price: '...', image: '...', realPhoto: '...',
     story: 'story-key',
     desc: '...',
     specs: { ... },
   },
   ```
   Cơ chế hiển thị (nút "Câu chuyện nhà rượu: {label} →" trong popup, dẫn tới đúng bài viết khi bấm) đã có sẵn trong JS (`pmStoryKey`, `#pm-story`) — chỉ cần field `story` khớp key trong `STORIES`, không cần sửa gì thêm. Nếu nhà sản xuất chưa có bài viết nào trong `STORIES`, bỏ qua field này — không tự ý bịa key hoặc yêu cầu viết bài mới (đó là phạm vi của skill `viet-bai`, chỉ làm khi được yêu cầu riêng).

7. **Sắp xếp lại theo giá**: sau khi thêm xong, sắp xếp lại toàn bộ thẻ sản phẩm trong MỖI section (`#vang-do`, `#vang-trang`, và mọi section loại rượu khác đã có) theo giá tăng dần (thấp → cao), không chỉ riêng section vừa thêm chai mới. Sắp xếp lại cả thứ tự các thẻ `<button data-product>` trong grid — thứ tự entry trong object `PRODUCTS` không cần khớp, chỉ thứ tự hiển thị trên trang mới cần đúng. Nếu có nhiều chai cùng giá, giữ nguyên thứ tự tương đối cũ giữa chúng.

8. **Verify bằng Playwright** (viewport mobile 390×844 và desktop 1440×900), theo đúng `mandatory-rules.md`:
   - Section mới hiển thị đúng, ảnh không vỡ layout.
   - Bấm vào chai → modal mở đúng thông tin + ảnh; bấm ảnh nhỏ → lightbox mở ảnh thật; đóng bằng X / click nền / Esc.
   - Nếu sản phẩm có field `story`: dòng "Câu chuyện nhà rượu: ..." hiển thị trong popup, bấm vào mở đúng bài viết tương ứng.
   - Link Hero (nếu vừa thêm/sửa) nhảy đúng tới section.
   - Animation scroll (`reveal`) hoạt động cho section mới.
   - Thứ tự thẻ sản phẩm trong mỗi section đúng theo giá tăng dần.

9. **Báo cáo lại** cho người dùng: đã thêm chai nào, xếp vào mục nào, giá/thông tin lấy từ poster, thứ tự sắp xếp theo giá đã cập nhật, đã nối được "Câu chuyện nhà rượu" nào (nếu có) hay không có bài viết tương ứng, và bất kỳ giả định/điểm cần xác nhận (vd: loại rượu chưa chắc chắn, thiếu ảnh thật, v.v.).

## Không tự ý làm

- Không xoá/di chuyển ảnh gốc trong `anh ruou/`.
- Không đoán loại rượu (đỏ/trắng/khác) nếu poster không ghi rõ — hỏi người dùng.
- Không thêm section/tính năng ngoài phạm vi (giỏ hàng, lọc, phân trang...) trừ khi được yêu cầu, theo `code-conventions.md`.

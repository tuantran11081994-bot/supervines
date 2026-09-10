---
name: viet-bai
description: Viết bài giới thiệu một nhà sản xuất rượu vang (tìm thông tin, chọn ảnh bìa, viết bài) và đăng vào section "Câu chuyện nhà rượu" (dưới Vang nổ) trên website SuperVines, dạng ảnh bìa trong carousel (thanh trượt + mũi tên) + popup chi tiết khi bấm vào.
---

Kích hoạt khi người dùng cung cấp tên (và có thể vài thông tin gợi ý) của một nhà sản xuất/nhà làm rượu vang và yêu cầu viết bài / đăng bài về họ (vd: "viết bài về nhà sản xuất X", "đăng câu chuyện về vườn nho Y").

## Đầu vào

- Tên nhà sản xuất rượu vang do người dùng cung cấp, có thể kèm theo quốc gia/vùng trồng, tên miền website nếu biết.
- Nếu người dùng đưa nhiều nhà sản xuất trong 1 lần yêu cầu, hỏi lại xem có muốn viết bài riêng cho từng nhà sản xuất hay không — không tự ý gộp hoặc chỉ chọn 1 để làm.

## Quy trình

1. **Tìm trang web chính thức**: dùng WebSearch để xác định website chính thức của nhà sản xuất (ưu tiên domain riêng của họ, không phải trang thương mại điện tử/đại lý bán lẻ). Nếu không tìm được website chính thức, hỏi người dùng xác nhận trước khi dùng nguồn thay thế.

2. **Đọc thông tin nguồn**: dùng WebFetch đọc các trang liên quan trên site chính thức (About/Our Story/History/Vineyard/Winemaking/Awards/News/Journal/Events...). Chủ động tìm thêm các trang ít lộ diện hơn nhưng thường chứa chi tiết thú vị — trang giải thưởng, tin tức/blog, sự kiện đặc biệt (lễ hội thu hoạch, mở cửa vườn nho, hợp tác nghệ sĩ/đầu bếp, cột mốc kỷ niệm...). Có thể bổ sung 1-2 nguồn uy tín khác (báo rượu vang chuyên ngành, trang tổ chức rượu vang vùng, tin tức) để đối chiếu và bổ sung chi tiết, nhưng trang chính thức của nhà sản xuất luôn là nguồn ưu tiên và là nguồn được trích dẫn cuối bài.

3. **Chọn lọc thông tin đặc sắc nhất**: từ nội dung đọc được, chọn ra các điểm ấn tượng/khác biệt nhất — lịch sử/di sản gia đình, terroir hoặc vị trí vườn nho độc đáo, phương pháp canh tác/ủ rượu đặc trưng, **giải thưởng đã đạt được**, **hoạt động/sự kiện đặc biệt** (lễ hội, hợp tác, cột mốc kỷ niệm, dự án cộng đồng...), triết lý (hữu cơ, bền vững...), hoặc một câu chuyện đáng nhớ. Ưu tiên số lượng và độ đa dạng của các điểm này hơn là gói gọn tối thiểu — nguồn càng có nhiều chi tiết thú vị (giải thưởng, sự kiện...) thì bài càng nên khai thác nhiều, miễn mỗi chi tiết đều có thật trong nguồn. Chỉ bỏ qua thông tin vụn vặt, trùng lặp hoặc không có gì đáng kể.

4. **Viết bài**: tiếng Việt, theo đúng tone trong `content-tone.md` — ngắn gọn, điềm tĩnh, không dùng ngôn ngữ marketing sáo rỗng (súc tích không có nghĩa là hời hợt — mỗi câu vẫn phải mang thông tin cụ thể). Cấu trúc:
   - Tiêu đề ngắn bắt được tinh thần nhà sản xuất (không chỉ là nhắc lại tên).
   - Độ dài bài linh hoạt theo lượng thông tin đặc sắc tìm được — thường 4-7 đoạn văn ngắn, có thể nhiều hơn nếu nhà sản xuất có nhiều câu chuyện/giải thưởng/sự kiện đáng kể; không cần gò ép xuống còn vài đoạn nếu nguồn có sẵn nhiều chi tiết thú vị. Vẫn giữ mỗi đoạn ngắn gọn, súc tích — chiều rộng ưu tiên hơn là đoạn văn dài dòng.
   - Có thể dành hẳn 1 đoạn riêng cho giải thưởng hoặc sự kiện/hoạt động đặc biệt nếu nguồn có đủ chi tiết, thay vì nhét chung một câu vào đoạn khác.
   - Không bịa thêm chi tiết ngoài những gì tìm thấy trong nguồn.

5. **Chọn & xử lý ảnh bìa**: chọn 1 ảnh đại diện nhất cho câu chuyện (vườn nho, người sáng lập, hầm rượu, quy trình ủ...) từ trang web chính thức — ưu tiên ảnh trong trang media/press kit nếu có sẵn để dùng lại. Nếu không rõ ảnh có được phép sử dụng lại hay không, dừng lại và hỏi người dùng trước khi tải về dùng. Ảnh này dùng làm cả ảnh bìa (thẻ trong carousel) lẫn ảnh đầu popup chi tiết — không cần nhiều ảnh trừ khi người dùng yêu cầu thêm.
   - Ảnh trong carousel (thẻ `#cau-chuyen`) vẫn cắt theo tỉ lệ `aspect-[3/4]` như các thẻ khác, để các thẻ đều nhau.
   - Ảnh trong popup thì **không bắt buộc cắt theo tỉ lệ cố định** — có thể để full size/giữ nguyên tỉ lệ gốc, miễn giữ đúng khung popup và không méo ảnh. Ưu tiên chọn ảnh đẹp, rõ nét, bố cục tốt hơn là cố ép vừa một khung tỉ lệ.
   - Tải ảnh về bằng PowerShell (`Invoke-WebRequest -OutFile`).
   - Đặt tên slug rõ nghĩa theo tên nhà sản xuất (vd `ten-nha-san-xuat-01.jpg`), lưu vào `images/`.
   - Resize + nén ngay trong `images/` (ghi đè sau khi resize): chiều rộng ~1600px, JPEG quality ~80-82 — theo đúng cách làm trong skill `dang-san-pham` và yêu cầu tối ưu ảnh của `tech-stack.md`.

6. **Cho người dùng xem trước nội dung**: trước khi đụng vào `index.html`, trình bày cho người dùng xem toàn bộ bản nháp — tiêu đề, các đoạn văn, ảnh bìa đã chọn (kèm ảnh xem trước, không chỉ tên file), và dòng nguồn cuối bài. Chỉ tiếp tục sang bước đăng bài sau khi người dùng xác nhận đồng ý hoặc đã chỉnh sửa xong theo phản hồi của họ — không tự ý đăng thẳng lên site khi chưa được duyệt.

7. **Thêm bài vào section `#cau-chuyen`** ("Câu chuyện nhà rượu") trong `index.html`. Section này nằm ngay dưới section `#vang-no` ("Vang nổ"), trước "DUO IMAGE BANNER" — không di chuyển vị trí section này trừ khi được yêu cầu. Cấu trúc hiển thị là **carousel ảnh bìa (thanh trượt ngang + mũi tên trái/phải) + popup chi tiết** khi bấm vào — giống hệt pattern carousel sản phẩm (`#vang-do`, `#vang-trang`, `#vang-no`) đã có trong site, không phải grid tĩnh và không phải bài viết đầy đủ hiển thị thẳng trên trang:
   - Thêm 1 thẻ mới vào cuối `<div id="cau-chuyen-track">` (bên trong `<div class="relative">` chứa track + 2 nút mũi tên), theo đúng pattern các thẻ đã có: `<button type="button" data-story="slug-nha-san-xuat" class="w-[46%] sm:w-[32%] md:w-[22%] shrink-0 snap-start text-left group">`, ảnh bìa `aspect-[3/4]`, `<p>` tiêu đề bài + `<p>` tên nhà sản xuất nhỏ bên dưới.
   - Thêm 1 entry mới vào object `STORIES` trong `<script>` (key = slug trùng với `data-story`): gồm `label` (tên nhà sản xuất), `title`, `image` (ảnh bìa), `paragraphs` (mảng các đoạn văn), `source: { name, url }`.
   - Không cần sửa gì thêm ở JS xử lý popup hay carousel — logic gắn `click` cho `[data-story]` (mở `#story-modal`) và `wireCarousel('cau-chuyen-track', 'cau-chuyen-prev', 'cau-chuyen-next', { loop: true })` đã dùng chung cho toàn bộ bài viết, tự động áp dụng cho thẻ mới miễn đúng `data-story` key khớp với `STORIES` và thẻ nằm trong track. Tất cả carousel trong site (kể cả 3 carousel sản phẩm `#vang-do`/`#vang-trang`/`#vang-no`) đều chạy **quay vòng** (`loop: true`) — nút mũi tên không bao giờ bị `disabled`, bấm tiếp ở bài/sản phẩm cuối sẽ quay lại bài/sản phẩm đầu và ngược lại. Ảnh trong `#story-modal` hiển thị full size theo tỉ lệ gốc (`w-full h-auto`, không crop theo aspect-ratio cố định) — không cần chỉnh sửa ảnh cho vừa khung, chỉ cần chọn ảnh đẹp/rõ nét.
   - Nếu đây là bài viết đầu tiên tạo `#cau-chuyen`/`STORIES`/`#story-modal` từ đầu (chưa có sẵn trong `index.html`), tạo theo đúng cấu trúc carousel trên (tham khảo `#vang-no` làm mẫu cấu trúc carousel, và bài Champagne Gremillet trong `STORIES`/`#story-modal` làm mẫu nội dung) — nhớ gọi `wireCarousel('cau-chuyen-track', 'cau-chuyen-prev', 'cau-chuyen-next', { loop: true })` cho section mới trong `<script>` (tham số thứ 4 `{ loop: true }` bắt buộc để có hành vi quay vòng).

7b. **Luôn cập nhật submenu điều hướng** — đây là bước bắt buộc đi kèm bước 7, không phải tuỳ chọn. Trong nav chính có `<li id="story-menu-item">` chứa `<ul id="story-submenu">` (dropdown "Câu chuyện nhà rượu" khi hover/tap menu) — vì `[data-story]` được gắn click handler chung cho mọi phần tử có thuộc tính này (kể cả `<a>` trong submenu), chỉ cần thêm đúng entry là submenu tự hoạt động, không cần sửa JS:
   - **Nếu đây là bài đầu tiên về nhà sản xuất này**: thêm 1 dòng `<a href="#" data-story="slug-nha-san-xuat" class="block">Tên Nhà Sản Xuất</a>` vào trong `<li>` của `#story-submenu`, theo đúng pattern các dòng đã có.
   - **Nếu nhà sản xuất này đã có bài viết trước đó trong submenu** (tức đây là bài thứ 2 trở lên về cùng 1 nhà rượu): thay dòng `<a>` đơn hiện có của nhà sản xuất đó bằng 1 khối submenu nhỏ gồm nhãn tên nhà sản xuất (không phải link) + các link con là tiêu đề từng bài, ví dụ:
     ```html
     <div class="space-y-2">
       <p class="text-cream/40 text-xs uppercase tracking-wide">Tên Nhà Sản Xuất</p>
       <a href="#" data-story="slug-bai-1" class="block pl-3">Tiêu đề bài 1</a>
       <a href="#" data-story="slug-bai-2" class="block pl-3">Tiêu đề bài 2</a>
     </div>
     ```
     Chuyển luôn bài cũ (trước đó chỉ hiển thị tên nhà sản xuất) sang hiển thị tiêu đề bài của nó trong khối này. Nếu sau này có bài thứ 3 cùng nhà sản xuất, thêm tiếp 1 dòng `<a>` vào trong `<div>` đó.
   - Khi đặt `data-story` slug cho bài thứ 2 trở lên của cùng 1 nhà sản xuất, không dùng lại slug cũ — thêm hậu tố mô tả chủ đề bài viết (vd `chateau-x-vuon-nho-phia-bac`), tránh chỉ đánh số `-2`/`-3` chung chung.
   - Không cần chỉnh CSS/JS cho việc mở/đóng submenu — `#story-submenu` tự tính `max-height` theo nội dung con (xem `initHoverSubmenu` trong `<script>`), tự co giãn theo số lượng entry.

7c. **Sau khi đăng bài, kiểm tra sản phẩm nào thuộc cùng nhà sản xuất và dẫn link ngược lại bài viết** — bước bắt buộc đi kèm bước 7/7b, không phải tuỳ chọn:
   - Tìm trong object `PRODUCTS` những sản phẩm thuộc cùng nhà sản xuất vừa viết bài — nhận diện qua tên thương hiệu xuất hiện trong `name` hoặc tiền tố của `key` (vd sản phẩm key `acquesi-marengo-spumante`, tên "Acquesi Piemonte Marengo..." thuộc nhà sản xuất Acquesi). Có thể có 0, 1 hoặc nhiều sản phẩm khớp — không phải nhà sản xuất nào cũng đã có sản phẩm sẵn trên site, việc không tìm thấy sản phẩm nào là bình thường.
   - Với mỗi sản phẩm khớp mà chưa có field `story`, thêm dòng `story: 'slug-bai-viet',` ngay sau dòng `realPhoto` (hoặc sau `image` nếu sản phẩm đó không có `realPhoto`) — đúng vị trí đã dùng cho các sản phẩm khác (xem các entry có sẵn `story: 'chilano'`, `story: 'one-wine'`, `story: 'tiraki'`... làm mẫu). Không cần sửa gì thêm trong `<script>` — nút "Câu chuyện nhà rượu: {label}" trong popup sản phẩm (`#pm-story`) tự động hiện ra và mở đúng popup bài viết nhờ logic dùng chung đã có sẵn (`pmStoryKey`, `openStoryModal`), miễn `story` khớp đúng key trong `STORIES`.
   - Nếu nhà sản xuất đã có nhiều bài viết (bài thứ 2 trở lên trong `STORIES`), field `story` của từng sản phẩm phải trỏ đúng slug bài viết liên quan nhất đến sản phẩm đó — không mặc định luôn trỏ về bài đầu tiên; nếu không rõ sản phẩm liên quan tới bài nào hơn, hỏi người dùng thay vì tự đoán.
   - Không tự ý thêm sản phẩm mới hay sửa `name`/`price`/`desc`/`specs` của sản phẩm hiện có — chỉ thêm field `story`.

8. **Verify bằng Playwright** (viewport mobile 390×844 và desktop 1440×900), theo `mandatory-rules.md`:
   - Thẻ mới hiển thị đúng trong carousel `#cau-chuyen`, không vỡ layout, đúng tỉ lệ; bấm nút mũi tên phải (`#cau-chuyen-next`) trượt tới được thẻ mới (đặc biệt nếu nó nằm cuối track); bấm tiếp ở thẻ cuối cùng phải quay vòng về thẻ đầu tiên (và ngược lại với nút trái ở thẻ đầu) — nút mũi tên không được bị `disabled` ở hai đầu.
   - Bấm vào ảnh bìa → popup mở đúng ảnh, tiêu đề, nội dung; đóng bằng X / click nền / Esc.
   - Animation `reveal` hoạt động khi cuộn tới.
   - Link nguồn trong popup mở đúng tab mới, trỏ đúng website nhà sản xuất.
   - Section `#cau-chuyen` và popup responsive tốt trên mobile.
   - Mở dropdown "Câu chuyện nhà rượu" ở nav chính, kiểm tra entry mới xuất hiện đúng (link đơn nếu là bài đầu tiên của nhà sản xuất, hoặc khối nhãn + link con nếu là bài thứ 2 trở lên) và bấm vào mở đúng popup.
   - Nếu ở bước 7c có sản phẩm được gắn `story`: mở popup từng sản phẩm đó, xác nhận dòng "Câu chuyện nhà rượu: {tên nhà sản xuất}" hiện ra ở cuối popup và bấm vào mở đúng popup bài viết vừa đăng.

9. **Báo cáo lại** cho người dùng: nhà sản xuất nào vừa viết bài, nguồn thông tin đã dùng, ảnh bìa đã chọn (và nguồn ảnh), sản phẩm nào (nếu có) vừa được gắn link ngược về bài viết ở bước 7c, và bất kỳ điểm cần xác nhận (vd thông tin từ nguồn còn ít, chưa chắc bản quyền ảnh, không tìm được website chính thức, v.v.).

## Không tự ý làm

- Không bịa thông tin không có trong nguồn tìm được.
- Không tải/dùng ảnh khi không rõ nguồn gốc hoặc quyền sử dụng lại — hỏi người dùng trước.
- Không đăng bài lên `index.html` khi chưa cho người dùng xem trước và được xác nhận (bước 6).
- Không hiển thị bài viết đầy đủ thẳng trên trang — luôn dùng pattern ảnh bìa trong carousel + popup chi tiết khi bấm vào, không tự ý đổi lại thành khối văn bản inline hay grid tĩnh.
- Không di chuyển vị trí section `#cau-chuyen` khỏi ngay dưới `#vang-no`, và không xoá/ghi đè bài đã có trong carousel hay trong object `STORIES` — chỉ nối thêm bài mới.
- Không quên cập nhật `#story-submenu` trong nav (bước 7b) — đăng bài mới mà bỏ sót submenu là lỗi, không phải việc tuỳ chọn.
- Không quên kiểm tra và gắn field `story` cho sản phẩm cùng nhà sản xuất (bước 7c) — bỏ sót bước này khi nhà sản xuất đã có sản phẩm trên site là lỗi, không phải việc tuỳ chọn.
- Không tự ý viết bài cho nhiều nhà sản xuất cùng lúc nếu người dùng chỉ đưa 1 tên, và không tự chọn nhà sản xuất khác ngoài yêu cầu.

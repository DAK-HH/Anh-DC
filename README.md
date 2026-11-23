# 📍 Lưu ảnh theo địa điểm

Ứng dụng web một file (không cần cài đặt, không cần server) để dán ảnh chụp/cắt màn hình, phân loại theo **tỉnh** và **địa chỉ cụ thể**, rồi lưu ra máy thành từng thư mục gọn gàng.

## Tính năng

- Dán ảnh trực tiếp bằng **Ctrl+V** (ví dụ ảnh cắt bằng Win+Shift+S), kéo thả file ảnh, hoặc chọn ảnh từ máy.
- Hai cấp địa điểm: **Tỉnh** → **Địa chỉ cụ thể** (ví dụ `Hưng Yên` → `Quỳnh Phụ`).
- Ảnh chỉ biết tỉnh thì để thẳng ở tỉnh; ảnh có địa chỉ thì để vào địa chỉ đó.
- Mỗi tỉnh / địa chỉ có ô **Số điện thoại** và **Ghi chú**; khi lưu, app ghi thêm file `thong-tin.txt` vào thư mục đó.
- **Bản đồ:** mỗi địa điểm có bản đồ nhỏ để tìm/đặt ghim (kéo ghim hoặc bấm lên bản đồ để chỉnh), nút chỉ đường Google Maps, và nút **🗺 Bản đồ chung** hiện mọi địa điểm kèm số ảnh (bấm ghim để mở ảnh).
- Mục **Chưa có địa điểm** để chứa ảnh chưa phân loại, sau đó chuyển sang địa điểm bằng ô chọn dưới mỗi ảnh.
- Chọn một thư mục trên máy, app tự tạo thư mục con theo địa điểm và tự lưu ảnh mới.
- Dữ liệu được giữ trong trình duyệt (IndexedDB), đóng mở lại vẫn còn.
- Hoạt động hoàn toàn trên máy của bạn, không gửi ảnh đi đâu.

## Cách dùng

1. Mở file `index.html` bằng **Chrome** hoặc **Edge**.
2. Gõ tên tỉnh ở khung bên trái, bấm **+**.
3. Muốn thêm địa chỉ cụ thể: chọn tỉnh, bấm **+ Địa chỉ cụ thể**.
4. Dán ảnh (Ctrl+V) hoặc kéo thả vào khung giữa.
5. Bấm **📁 Chọn thư mục lưu trên máy** (làm một lần mỗi lần mở app) để ảnh tự được lưu vào thư mục.
6. Dùng **Lưu địa điểm này** hoặc **Lưu tất cả địa điểm** để lưu lại toàn bộ ảnh đã có.

## Cấu trúc thư mục khi lưu

```
<thư mục bạn chọn>/
├── Hưng Yên/
│   ├── thong-tin.txt                         ← số điện thoại, ghi chú của tỉnh
│   ├── Hưng Yên_001.png                      ← ảnh chỉ có tỉnh
│   └── Quỳnh Phụ/
│       ├── thong-tin.txt                     ← số điện thoại, ghi chú của địa chỉ
│       └── Hưng Yên_Quỳnh Phụ_001.png        ← ảnh có địa chỉ cụ thể
└── Chưa có địa điểm/
    └── Chưa có địa điểm_001.png
```

Ảnh trong mục "Chưa có địa điểm" không tự lưu; chỉ lưu khi bạn chuyển nó sang một địa điểm hoặc bấm nút Lưu.

## Đưa lên GitHub Pages (để dùng online)

1. Tạo repo mới, tải `index.html` và `README.md` lên nhánh `main`.
2. Vào **Settings → Pages**, chọn *Deploy from a branch*, nhánh `main`, thư mục `/ (root)`.
3. Sau ít phút, app chạy tại `https://<tên-github>.github.io/<tên-repo>/`.

Dữ liệu ảnh vẫn nằm trong trình duyệt của từng người dùng, không được đưa lên GitHub.

## Lưu ý

- Chọn thư mục lưu cần **Chrome / Edge**. Trình duyệt khác vẫn dùng được, nhưng nút Lưu sẽ tải từng ảnh về thư mục Downloads.
- Chuyển ảnh sang địa điểm khác sau khi đã lưu: file cũ trong thư mục cũ vẫn còn, cần xóa tay.
- Xóa dữ liệu trình duyệt (cache/site data) sẽ làm mất ảnh chưa lưu ra máy. Nên bấm **Lưu tất cả địa điểm** thường xuyên.
- Bản đồ cần có mạng (dùng Leaflet, OpenStreetMap). Địa chỉ gõ ở ô tìm kiếm được gửi tới dịch vụ Nominatim của OpenStreetMap để tìm vị trí; số điện thoại và ghi chú không bị gửi đi. Nếu không tìm được đúng địa chỉ, app thử lại với địa chỉ ngắn hơn (bỏ dần phần nhỏ nhất) và báo là vị trí gần đúng. Nơi ở nông thôn có thể lệch, hãy kéo ghim cho đúng. Nền bản đồ và dịch vụ tìm địa chỉ có nguồn dự phòng nếu nguồn chính không truy cập được.
- Nếu mở file trực tiếp trên máy mà nền bản đồ không hiện, hãy dùng bản GitHub Pages (có địa chỉ https).
- Chỉ có hai cấp địa điểm.
- Số điện thoại là thông tin cá nhân của khách: đừng đưa thư mục đã lưu (có `thong-tin.txt`) lên repo công khai.

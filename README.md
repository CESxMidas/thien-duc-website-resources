# Kho tài nguyên hình ảnh — Website Thiên Đức

Nguồn sự thật cho ảnh gốc. `thien-duc-website-frontend/public/images/` là **bản
sao phục vụ web**; sửa ảnh thì sửa ở đây trước, rồi đồng bộ sang frontend.

```bash
npm run sync:images   # chạy ở thien-duc-website-frontend
```

## Quy ước đặt tên

```
images/<nhóm>/<dự-án>/<hạng-mục>/<dự-án>-<chủ-đề>-<số thứ tự>.<ext>
```

- Chữ thường, không dấu, phân cách bằng dấu gạch ngang.
- Số thứ tự hai chữ số (`-01`, `-02`) để thứ tự sắp xếp khớp thứ tự hiển thị.
- Chủ đề mô tả **nội dung ảnh**, không mô tả vị trí đặt trên trang:
  `exterior`, `aerial`, `amenity-pool`, `living-room`, `master-plan`, `render`.

## Hiện có (30 ảnh)

| Nhóm | Dự án | Số ảnh | Ghi chú |
| --- | --- | --- | --- |
| `banners/home/` | Khu đô thị Hưng Phú | 4 | Toàn bộ banner trang chủ lấy từ Hưng Phú |
| `projects/hung-phu/master-plan/` | Hưng Phú | 3 | Ảnh phối cảnh tổng thể |
| `projects/hung-phu/fancy-tower/` | Fancy Tower | 7 | Ngoại thất + hồ bơi |
| `projects/hung-phu/hotel/` | Hưng Phú | 6 | Khách sạn nội khu |
| `projects/hung-phu/location/` | Hưng Phú | 1 | Nền bản đồ vị trí (PNG) |
| `projects/la-bonita/building/` | La Bonita | 2 | Ảnh render |
| `projects/vung-tau/` | Silver Sea Tower | 2 | Ngoại thất (WebP) |
| `projects/bay-hien/` | Bảy Hiền Tower | 1 | Ngoại thất |
| `news/` | — | 2 | Lễ khởi công Fancy Tower + 1 ảnh tạm |
| `brand/` | — | 2 | Logo + favicon |

## Còn thiếu — cần công ty cung cấp

Ảnh của bên thứ ba (CapitaLand, các trang bất động sản) **không được tự lấy từ
Internet**: sai bản quyền và không xác minh được nguồn.

- **Vista Verde** (Quận 2, TP.HCM) — 0 ảnh. Hiện hiển thị dạng thẻ chữ ở trang Giới thiệu.
- **Feliz en Vista** (Quận 2, TP.HCM) — 0 ảnh. Như trên.
- **Hưng Phú Mall** — 0 ảnh (`projects/hung-phu/shopping-center/`). Hạng mục đang thi công.
- **Khu nhà ở thấp tầng** (Hưng Phú) — 0 ảnh riêng, đang mượn ảnh master plan.
- **Bảy Hiền Tower** — chỉ 1 ảnh ngoại thất, không có ảnh nội khu.
- **Silver Sea Tower** — chỉ 2 ảnh ngoại thất.
- **La Bonita** — chỉ ảnh render, chưa có ảnh thực tế công trình.

## Cần tối ưu trước go-live

Chỉ tiêu LCP ≤ 2,5s (CL-02). Next/Image có nén khi phục vụ, nhưng ảnh gốc quá
nặng vẫn làm chậm build và tốn băng thông:

| File | Dung lượng |
| --- | --- |
| `projects/la-bonita/building/la-bonita-building-render-02.jpg` | 2,8 MB |
| `projects/vung-tau/vung-tau-center-exterior-01.webp` | 2,7 MB |
| `projects/la-bonita/building/la-bonita-building-render-01.jpg` | 2,4 MB |
| `projects/hung-phu/master-plan/hung-phu-master-plan-aerial-01.jpg` | 1,7 MB |
| `projects/hung-phu/location/hung-phu-location-map-base.png` | 1,3 MB |

Mục tiêu: ảnh nội dung ≤ 500 KB, ảnh banner ≤ 800 KB, chiều rộng tối đa 2560px.

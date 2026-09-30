# Báo cáo Refactoring Layout - CreativeChronicle

## Tác hại của `position: absolute` với Responsive Design

`position: absolute` đưa phần tử ra khỏi normal flow, khiến phần tử cha mất chiều cao thực tế. Trong Mosaic Gallery cũ, `height: 400px` cứng + absolute positioning khiến ảnh không co giãn theo viewport. Trên mobile, ảnh bị bóp méo hoặc đè lấn nội dung bên dưới vì cha không chiếm đúng không gian. Absolute positioning chỉ phù hợp cho các phần tử overlay (tooltip, modal), không dùng cho layout chính.

## Tại sao CSS Grid là giải pháp cứu cánh?

CSS Grid cho phép định nghĩa bố cục 2D bằng `grid-template-columns`, `grid-template-rows`, và `grid-template-areas`. Không cần tính pixel — chỉ cần khai báo tỷ lệ (`2fr 1fr`). Grid tự động tạo hàng mới khi thêm ảnh, tự động co giãn theo nội dung. Media query chỉ cần đổi `grid-template-columns: 1fr` là gallery chuyển thành 1 cột trên mobile. Đây là giải pháp ngữ nghĩa, linh hoạt và dễ bảo trì hơn hẳn absolute positioning.

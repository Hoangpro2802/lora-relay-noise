# 🔌 Tên Dự Án Phần Cứng

>i “Hệ thống đo mức độ tiếng ồn trong khu vực đô thị” nhằm xây dựng một hệ thống giám sát tiếng ồn sử dụng mạng truyền thông LoRa với ba node cảm biến. Node 1 gồm ESP32S kết hợp cảm biến âm thanh MAX9814 để thu thập dữ liệu môi trường, xử lý và chuyển đổi thành giá trị tương đương dB. Dữ liệu sau đó được truyền không dây đến Node 2 – đóng vai trò trung chuyển – và tiếp tục gửi đến Node 3. Node 3 nhận dữ liệu, lưu vào thẻ nhớ microSD và đồng thời cập nhật lên nền tảng IoT Adafruit.io để hiển thị trực quan và lưu trữ lâu dài. Hệ thống được thiết kế nhằm phục vụ mục tiêu giáo dục và nghiên cứu, giúp sinh viên tiếp cận thực tiễn công nghệ truyền thông không dây, xử lý tín hiệu cảm biến và ứng dụng IoT. Dự án sẽ được kiểm thử thực tế trong vòng 7 ngày để đánh giá hiệu quả hoạt động và khả năng ứng dụng trong việc theo dõi, phân tích ô nhiễm tiếng ồn tại các khu vực đô thị.
---

## 📑 Mục Lục

- [Giới thiệu](#giới-thiệu)
- [Thông số kỹ thuật](#thông-số-kỹ-thuật)
- [Danh sách linh kiện](#danh-sách-linh-kiện)
- [Sơ đồ nguyên lý và PCB](#sơ-đồ-nguyên-lý-và-pcb)
- [Hướng dẫn lắp ráp](#hướng-dẫn-lắp-ráp)
- [Lập trình firmware](#lập-trình-firmware)
- [Cách sử dụng](#cách-sử-dụng)
- [Kiểm thử](#kiểm-thử)
- [Ảnh/Video demo](#ảnhvideo-demo)
- [Đóng góp](#đóng-góp)
- [Giấy phép](#giấy-phép)

---

## 👋 Giới Thiệu

Trình bày ngắn gọn:
- Dự án làm gì?
- Ai là người dùng chính?
- Mục tiêu của thiết kế (giáo dục, nghiên cứu, sản phẩm thương mại...)

---

## 📐 Thông Số Kỹ Thuật

| Thành phần     | Thông tin            |
|----------------|----------------------|
| MCU            | ESP32S      |
| Nguồn vào      | 5V qua USB hoặc DC   |
| Kết nối        | WiFi, Lora      |
| Kích thước PCB | 60mm x 70mm          |

---

## 🧰 Danh Sách Linh Kiện

| Tên linh kiện            | Số lượng | Ghi chú                     |
|--------------------------|----------|-----------------------------|
| ESP32S                   | 3        | Vi điều khiển chính         |
| Module Lora Ra01         | 3        |                             |
| LED xanh                 | 3        | Vòng tròn hoặc dải LED      |
| MAX9814                  | 1        | Cảm biến nhiệt độ, độ ẩm    |
| Module đọc MicroSD       | 1        | Đầu vào tương tự            |
| Nút nhấn                 | 3        | Điều khiển thủ công         |

*Có thể link đến file BOM.csv đầy đủ.*

---

## 🔧 Sơ Đồ Nguyên Lý và PCB

- 📎 [Schematic (PDF)](docs/Schematic_Lora.pdf)
- 📎 [PCB Layout (Gerber)](docs/gerber.zip)
- 📎 [File thiết kế (Eagle / KiCad)](docs/project.kicad_pcb)

_Hình minh họa sơ đồ nguyên lý hoặc board PCB có thể nhúng ngay tại đây:_

![Schematic](docs/images/schematic.png)

---

## 🔩 Hướng Dẫn Lắp Ráp

1. Hàn các linh kiện nhỏ trước: điện trở, tụ điện
2. Hàn vi điều khiển hoặc socket
3. Kiểm tra ngắn mạch bằng đồng hồ
4. Cấp nguồn thử, kiểm tra dòng tiêu thụ
5. Lập trình firmware để kiểm tra

*Có thể link đến file hướng dẫn chi tiết hoặc video.*

---

## 💻 Lập Trình Firmware

- **Ngôn ngữ:** C++ (Arduino) / MicroPython / PlatformIO
- **Tải firmware:** `firmware/main.ino` hoặc `src/main.py`
- **Cách nạp:**
  ```bash
  platformio run --target upload

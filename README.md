# FOOD_DETECT-RICE-MILK-AI
Rice Milk AI – Smart Food Detection & Billing
1. Overview
Rice Milk AI is a Python desktop application that turns any camera into a self‑checkout kiosk for canteens. It detects Vietnamese lunch items in a tray using YOLOv8 object detection supported by a ResNet‑50 classifier, draws bounding boxes, calculates totals, generates a QR code for payment, and stores a printable invoice history.

Key features
Real‑time detection from built‑in webcam, external camera, or IP stream.
Hybrid YOLO + CNN pipeline for robust recognition of 10 predefined dishes.
Elegant cross‑platform GUI built with CustomTkinter.
Automatic invoice with QR code image and printable PDF/PNG.
Persistent order history with expand/collapse and delete.
Debug overlay to adjust clickable areas (press Alt + D).

2. Installation
2.1 Prerequisites
Python ≥ 3.10
Windows 10/11, macOS, or Linux
(Optional) CUDA‑enabled GPU for faster inference
Git
2.2 Clone & create virtual environment
git clone https://github.com/<your‑org>/rice‑milk‑ai.git
cd rice‑milk‑ai
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS / Linux
source .venv/bin/activate

2.3 Install Python dependencies
pip install -r requirements.txt

2.4 Download model weights
Place the following files inside the data/ folder:
File
Source
Notes
weights.pt
YOLOv8 weights trained on your Roboflow dataset
required
best_food_model.pth
ResNet‑50 classifier weights
required

2.5 Assets folder structure
assets/
├─ menu.png        # background menu image (1920×1080)
└─ qr_code.jpg     # static MoMo / banking QR

3. Usage
3.1 Launch GUI
RUN DetectApp.exe

Quick demo
Click Webcam to open an integrated camera or IP Webcam to stream from a phone.
Wait 5 s or press CHỤP NGAY to take a snapshot.
Review the detection result, invoice, and QR code.
Click In hóa đơn to preview & print.
Press Lịch sử on the main menu to view saved invoices.

3.2 Debug mode
Press Alt + D to highlight all clickable zones on the splash image.

4. Dependencies
All runtime libraries are pinned in requirements.txt. Main packages:
customtkinter – modern themed Tkinter widgets
pillow – image processinG
opencv‑python – camera capture & image I/O
numpy – numerical operations
torch & torchvision – deep‑learning backend for the CNN
ultralytics – YOLOv8 detector
requests – REST requests (Roboflow, etc.)
reportlab – PDF/PNG invoice export
concurrent‑futures – threaded tasks
pywin32 (optional, Windows) – silent printing support

5. Code Quality & Best Practices
PEP 8 naming, type hints, and docstrings across modules.
Modular design: GUI/controller logic in main.py, model helpers in assets and data separated.
Long operations (inference, disk I/O) run on background threads to keep the UI responsive.
All string literals are UTF‑8.
Compatible with pyinstaller --onefile --noconsole for distribution.
Placeholder unit tests in tests/ (please expand!).

________________________________________________________________________________________________________

Rice Milk AI – Nhận Diện Món Ăn & Thanh Toán Thông Minh
1. Tổng quan
Rice Milk AI là ứng dụng desktop viết bằng Python, biến bất kỳ camera nào thành quầy tính tiền tự động cho căn tin. Ứng dụng sử dụng YOLOv8 để phát hiện món ăn trên khay, kết hợp bộ phân loại ResNet‑50 để tăng độ chính xác, vẽ khung, tính tổng tiền, sinh mã QR để thanh toán và lưu hóa đơn in được.
Tính năng nổi bật
Nhận diện thời gian thực từ webcam tích hợp, camera USB hoặc luồng IP.
Pipeline kết hợp YOLO + CNN, nhận diện 10 món ăn cố định.
Giao diện hiện đại đa nền tảng bằng CustomTkinter.
Sinh hóa đơn kèm mã QR, xuất PDF/PNG.
Lưu lịch sử đơn hàng với chức năng mở rộng/thu gọn, xoá.
Chế độ debug hiển thị vùng nhấp chuột (Alt + D).

3. Hướng dẫn cài đặt
2.1 Yêu cầu
Python ≥ 3.10
Windows 10/11, macOS hoặc Linux
(Tùy chọn) GPU hỗ trợ CUDA để suy luận nhanh hơn
Git
2.2 Clone và tạo môi trường ảo
git clone https://github.com/<your-org>/rice-milk-ai.git
cd rice-milk-ai
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS / Linux
source .venv/bin/activate

2.3 Cài đặt phụ thuộc Python
pip install -r requirements.txt

2.4 Tải trọng số mô hình
Đặt các tệp sau trong thư mục data/:
File
Nguồn
Ghi chú
weights.pt
Trọng số YOLOv8 huấn luyện trên Roboflow
best_food_model.pth
Trọng số ResNet‑50 phân loại món ăn

2.5 Cấu trúc thư mục assets
assets/
├─ menu.png        # ảnh menu nền (1920×1080)
└─ qr_code.jpg     # mã QR MoMo/Nhà băng cố định

3. Hướng dẫn sử dụng
3.1 Khởi chạy giao diện
Chạy ứng dụng DetectApp.exe
Demo nhanh
Chọn Webcam hoặc IP Webcam (điện thoại).
Đợi 5 s hoặc nhấn CHỤP NGAY để chụp khay.
Kiểm tra khung nhận diện, hóa đơn và mã QR.
Nhấn In hóa đơn để xem trước và in.
Chọn Lịch sử trên menu chính để xem đơn đã lưu.


3.2 Chế độ debug
Nhấn Alt + D để hiện tất cả vùng nhấp trên splash.

4. Phụ thuộc
Tất cả gói được cố định phiên bản trong requirements.txt. Một số gói chính:
customtkinter – widget Tkinter hiện đại
pillow – xử lý ảnh
opencv-python – capture camera & I/O ảnh
numpy – tính toán số
torch & torchvision – backend deep learning cho CNN
ultralytics – YOLOv8 detector
requests – gọi REST (Roboflow, v.v.)
reportlab – xuất PDF/PNG hoá đơn
concurrent-futures – xử lý luồng nền
pywin32 (tùy chọn, Windows) – in ẩn

5. Chất lượng mã & Thực hành tốt
Tuân thủ PEP 8, có type hint và docstring.
Thiết kế module: giao diện/điều khiển trong main.py, tiện ích mô hình tách asset và dữ liệu.
Thao tác lâu (suy luận, I/O) chạy ở luồng nền để UI mượt.
Chuỗi ký tự UTF‑8 toàn bộ.
Tương thích đóng gói pyinstaller --onefile --noconsole.
Có thư mục tests/ (hãy bổ sung thêm bài test!).
.



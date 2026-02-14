# Hướng Dẫn Deploy Bot Lên Render.com & Cron-job.org

Đã chuẩn bị xong hàng họ cho bot rồi. Giờ làm theo các bước này để đẩy nó lên mây nhé.

## Bước 1: Chuẩn Bị
1.  **Code đã sửa**: File `taixiumd5.py` đã được thêm server ảo để giữ kết nối. File `requirements.txt` đã có đủ hàng.
2.  **GitHub**: Tạo một repository mới trên GitHub và đẩy toàn bộ thư mục `bot txmd5` này lên đó. (Nếu chưa biết làm thì bảo tớ).
3.  **Token**: Lấy `BOT_TOKEN` từ BotFather.

## Bước 2: Deploy Lên Render.com
1.  Đăng ký/Đăng nhập [Render.com](https://render.com/).
2.  Nhấn **New +** -> chọn **Web Service**.
3.  Kết nối với tài khoản GitHub và chọn repository chứa bot vừa đẩy lên.
4.  Điền thông tin:
    - **Name**: Đặt tên tùy thích (ví dụ: `bot-txmd5`).
    - **Runtime**: Chọn **Python 3**.
    - **Build Command**: `pip install -r requirements.txt`
    - **Start Command**: `python taixiumd5.py`
5.  **Quan trọng**: Kéo xuống phần **Environment Variables**, nhấn **Add Environment Variable**:
    - Key: `BOT_TOKEN`
    - Value: `MÃ_TOKEN_CỦA_BẠN_Ở_ĐÂY`
    *(Hoặc bạn có thể dán trực tiếp token vào file code nếu lười, nhưng cách này bảo mật hơn)*.
6.  Nhấn **Create Web Service**.
7.  Chờ nó chạy (deploy). Khi nào thấy hiện chữ **Live** màu xanh là ngon.
8.  Copy cái đường link web của nó (dạng `https://bot-txmd5.onrender.com`).

## Bước 3: Treo Bot Bằng Cron-job.org
Để bot không bị Render cho "ngủ đông" sau 15 phút, cần dùng cái này chọc vào nó liên tục.
1.  Đăng ký/Đăng nhập [cron-job.org](https://cron-job.org/).
2.  Vào phần **Cronjobs** -> **Create Cronjob**.
3.  Điền thông tin:
    - **Title**: Tên gợi nhớ (ví dụ: `Keep Bot Alive`).
    - **URL**: Dán cái link web của Render vừa copy ở bước trên vào (ví dụ: `https://bot-txmd5.onrender.com/`).
    - **Schedule**: Chọn **Every 5 minutes** (hoặc 10 phút cũng được).
4.  Nhấn **Create**.

## Xong Phim!
Giờ bot sẽ sống nhăn răng 24/7 mà không tốn xu nào. Nếu bot có biến hay cần update gì thì cứ hú tớ. 😘

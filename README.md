# 🎾 Pickleball Club Management - Vợt Thủ Phố Núi

**Sinh viên**: Đỗ Văn Tuyên  
**MSSV**: xxxxx734  
**Lớp**: CNTT 17-08

Hệ thống quản lý CLB Pickleball hoàn chỉnh với Backend (ASP.NET Core 8 Web API), Frontend (Flutter Mobile/Web), và Database (SQLite).

---

## 🌐 Demo Links (Đã Deploy)

| Thành phần | Link |
|------------|------|
| **🖥️ Flutter Web** | https://pcm-pcmfrontend.vercel.app |
| **⚙️ Backend API** | https://pcm-backend-v1-1.onrender.com |
| **📖 Swagger API Docs** | https://pcm-backend-v1-1.onrender.com/swagger |
| **🐳 Docker Hub** | https://hub.docker.com/r/ngocmi/pcm-backend |

### 🔐 Tài khoản Demo

| Email | Password | Role |
|-------|----------|------|
| `admin@pcm.com` | `Admin123` | Admin |
| `user@pcm.com` | `User1234` | User |

---

## 📁 Cấu trúc dự án

```
bai_kiem_tra_nang_cao/
├── Backend/              # ASP.NET Core Web API 8.0
│   ├── Controllers/      # 10 API Controllers (incl. AdminController)
│   ├── Models/           # Entity Models (prefix 734_)
│   ├── Data/             # ApplicationDbContext (SQLite) + Seeder
│   ├── DTOs/             # Data Transfer Objects
│   ├── Hubs/             # SignalR Hub cho Real-time features
│   ├── Services/         # Background Services
│   ├── Dockerfile        # Docker build config
│   └── Program.cs        # Config CORS, JWT, Swagger, DI
└── Frontend/             # Flutter Mobile App
    ├── lib/
    │   ├── models/       # Dart models
    │   ├── providers/    # State management (Provider)
    │   ├── screens/      # Màn hình chính (Admin, Booking, Wallet...)
    │   ├── services/     # API Service (Dio) + SignalR Service
    │   └── widgets/      # Reusable widgets & Charts
    └── pubspec.yaml
```

---

## 🛠️ Tech Stack

### Backend
- **Framework**: ASP.NET Core 8 Web API
- **Database**: SQLite (Entity Framework Core Code First)
- **Authentication**: JWT Bearer Tokens
- **Real-time**: SignalR (WebSockets)
- **API Documentation**: Swagger/OpenAPI
- **Deployment**: Docker, Render.com

### Frontend
- **Framework**: Flutter 3.x (Hỗ trợ Mobile & Web)
- **State Management**: Provider
- **Networking**: Dio (HTTP Client)
- **Real-time**: SignalR Client
- **Charts**: FL Chart (Admin Dashboard)
- **Storage**: Flutter Secure Storage
- **Deployment**: Vercel

---

## 🚀 Hướng dẫn chạy Local

### 1️⃣ Backend API

```cmd
cd Backend

# Restore packages
dotnet restore

# Chạy API
dotnet run
```

✅ API URL: `http://localhost:5000`  
✅ Swagger UI: `http://localhost:5000/swagger`

### 2️⃣ Frontend Flutter

```cmd
cd Frontend

# Lấy dependencies
flutter pub get

# Chạy trên Chrome (Web)
flutter run -d chrome

# Build APK Android
flutter build apk --release
```

📱 File APK: `Frontend/build/app/outputs/flutter-apk/app-release.apk`

---

## 🐳 Chạy bằng Docker

### Pull và chạy Backend từ Docker Hub:

```bash
docker run -d -p 5000:8080 ngocmi/pcm-backend:v1
```

Truy cập: `http://localhost:5000/swagger`

---

## 📱 Tính năng Chính

### 💼 Admin Dashboard
- **Tổng quan tài chính**: Xem tổng quỹ CLB, doanh thu tháng này.
- **Biểu đồ doanh thu**: Chart trực quan theo dõi thu/chi 12 tháng gần nhất.
- **Xét duyệt nạp tiền**: Approve/Reject các yêu cầu nạp tiền từ thành viên.
- **Thống kê**: Số lượng thành viên theo hạng (Tier), số booking, giải đấu đang mở.

### 🏆 Giải đấu & Booking
- **Đặt sân**: Lịch trực quan, chọn giờ trống, thanh toán bằng ví.
- **Recurring Booking**: Đặt sân cố định hàng tuần (chỉ dành cho VIP/Diamond).
- **Giải đấu**: Tự động tạo lịch thi đấu, cập nhật tỉ số Real-time.

### 💰 Quản lý Ví (Wallet)
- **Nạp tiền**: Upload ảnh bằng chứng chuyển khoản.
- **Lịch sử**: Xem chi tiết từng giao dịch.
- **Hạng thành viên (Tier)**: Tích điểm để lên hạng và nhận ưu đãi.

### 🔔 Real-time & Tiện ích
- **Thông báo**: Nhận thông báo ngay lập tức khi có sự kiện mới.
- **Auto Cancel**: Booking chưa thanh toán sẽ tự hủy sau 15 phút.
- **Auto Remind**: Gửi notification nhắc lịch trước 24h.

---

## 🎓 Sinh viên thực hiện

**MSSV**: xxxxx734  
**Họ tên**: Đỗ Văn Tuyên  
**Lớp**: CNTT 17-08  
**Năm**: 2026

# 🎾 Pickleball Club Management System (PCM)

## Hệ Thống Quản Lý Câu Lạc Bộ Pickleball - Vợt Thủ Phố Núi

---

## 📋 Thông Tin Sinh Viên

| Thông tin             | Chi tiết                                                                       |
| ---------------------- | ------------------------------------------------------------------------------- |
| **Họ và tên** | Đỗ Văn Tuyên                                                                |
| **MSSV**         | xxxxx734                                                                        |
| **Lớp**         | CNTT 17-08                                                                      |
| **Năm học**    | 2025-2026                                                                       |
| **Môn học**    | Lập Trình Di Động Nâng Cao                                                 |
| **Đề tài**    | Hệ thống quản lý CLB Pickleball với Backend API và Flutter Mobile/Web App |

---

## 🌐 Demo Links - Ứng Dụng Đã Deploy

Toàn bộ hệ thống đã được deploy lên các nền tảng cloud miễn phí và có thể truy cập công khai:

| Thành phần                   | URL                                                                                         | Mô tả                           |
| ------------------------------ | ------------------------------------------------------------------------------------------- | --------------------------------- |
| **🖥️ Flutter Web App** | [https://pcm-pcmfrontend.vercel.app](https://pcm-pcmfrontend.vercel.app)                       | Giao diện web chạy trên Vercel |
| **⚙️ Backend API**     | [https://pcm-backend-v1-1.onrender.com](https://pcm-backend-v1-1.onrender.com)                 | RESTful API trên Render.com      |
| **📖 Swagger API Docs**  | [https://pcm-backend-v1-1.onrender.com/swagger](https://pcm-backend-v1-1.onrender.com/swagger) | Tài liệu API tương tác       |
| **🐳 Docker Hub**        | [https://hub.docker.com/r/ngocmi/pcm-backend](https://hub.docker.com/r/ngocmi/pcm-backend)     | Docker Image công khai           |
| **📱 APK File**          | `Frontend/build/app/outputs/flutter-apk/app-release.apk`                                  | File cài đặt Android           |

### 🔐 Tài Khoản Demo Để Test

| Email             | Mật khẩu   | Vai trò        | Quyền hạn                        |
| ----------------- | ------------ | --------------- | ---------------------------------- |
| `admin@pcm.com` | `Admin123` | **Admin** | Toàn quyền quản trị hệ thống |
| `user@pcm.com`  | `User1234` | **User**  | Người dùng thông thường      |

> **Lưu ý**: Do sử dụng Free Tier của Render.com, Backend có thể mất 30-60 giây để "thức dậy" khi truy cập lần đầu sau thời gian không hoạt động.

---

## 📖 Tổng Quan Dự Án

### 🎯 Mục Tiêu

Xây dựng một hệ thống quản lý câu lạc bộ Pickleball hoàn chỉnh, bao gồm:

- **Backend API** sử dụng ASP.NET Core 8 với kiến trúc RESTful
- **Frontend Mobile/Web** sử dụng Flutter hỗ trợ đa nền tảng
- **Database** sử dụng SQLite với Entity Framework Core
- **Real-time features** sử dụng SignalR cho thông báo và cập nhật trực tiếp
- **Deployment** đầy đủ lên các nền tảng cloud (Render.com, Vercel, Docker Hub)

### 🎓 Yêu Cầu Đề Bài

Dự án thực hiện theo yêu cầu của bài kiểm tra Flutter nâng cao, bao gồm:

1. ✅ **Backend API RESTful** với ASP.NET Core 8
2. ✅ **Flutter Mobile App** hỗ trợ Android và iOS
3. ✅ **Flutter Web App** chạy trên trình duyệt
4. ✅ **Authentication & Authorization** với JWT
5. ✅ **State Management** sử dụng Provider
6. ✅ **Real-time Communication** với SignalR
7. ✅ **Database** với Entity Framework Core Code First
8. ✅ **Docker Containerization**
9. ✅ **Cloud Deployment** (Backend + Frontend)
10. ✅ **API Documentation** với Swagger/OpenAPI

### 🏆 Điểm Nổi Bật

- **Kiến trúc phân tầng rõ ràng**: Controllers, Services, Models, DTOs
- **Prefix 734_** cho tất cả các Entity Models theo yêu cầu đề bài
- **10+ API Controllers** xử lý đầy đủ các nghiệp vụ
- **Background Services** tự động hủy booking và gửi nhắc nhở
- **Responsive UI** tương thích mọi kích thước màn hình
- **Charts & Analytics** cho Admin Dashboard
- **Secure Storage** cho JWT tokens
- **Error Handling** toàn diện với try-catch và logging

---

## 📁 Cấu Trúc Dự Án Chi Tiết

```
bai_kiem_tra_nang_cao/
│
├── 📂 Backend/                          # ASP.NET Core 8 Web API
│   ├── 📂 Controllers/                  # 10 API Controllers
│   │   ├── AdminController.cs           # Quản trị hệ thống
│   │   ├── AuthController.cs            # Đăng nhập, đăng ký
│   │   ├── BookingController.cs         # Đặt sân
│   │   ├── CourtController.cs           # Quản lý sân
│   │   ├── MemberController.cs          # Quản lý thành viên
│   │   ├── NotificationController.cs    # Thông báo
│   │   ├── RecurringBookingController.cs # Đặt sân định kỳ
│   │   ├── TournamentController.cs      # Giải đấu
│   │   ├── TransactionController.cs     # Giao dịch
│   │   └── WalletController.cs          # Ví tiền
│   │
│   ├── 📂 Models/                       # Entity Models (prefix 734_)
│   │   ├── 734_Member.cs                # Thành viên CLB
│   │   ├── 734_Court.cs                 # Sân pickleball
│   │   ├── 734_Booking.cs               # Đơn đặt sân
│   │   ├── 734_RecurringBooking.cs      # Đặt sân định kỳ
│   │   ├── 734_Tournament.cs            # Giải đấu
│   │   ├── 734_Match.cs                 # Trận đấu
│   │   ├── 734_Wallet.cs                # Ví tiền
│   │   ├── 734_Transaction.cs           # Giao dịch
│   │   ├── 734_Notification.cs          # Thông báo
│   │   ├── 734_ClubFund.cs              # Quỹ CLB
│   │   └── 734_TopUpRequest.cs          # Yêu cầu nạp tiền
│   │
│   ├── 📂 Data/
│   │   ├── ApplicationDbContext.cs      # EF Core DbContext
│   │   └── DataSeeder.cs                # Seed dữ liệu mẫu
│   │
│   ├── 📂 DTOs/                         # Data Transfer Objects
│   │   └── AuthDTOs.cs                  # Login, Register DTOs
│   │
│   ├── 📂 Hubs/
│   │   └── NotificationHub.cs           # SignalR Hub cho real-time
│   │
│   ├── 📂 Services/                     # Background Services
│   │   ├── BookingCancellationService.cs # Auto-cancel booking
│   │   └── BookingReminderService.cs    # Auto-remind booking
│   │
│   ├── 📂 Migrations/                   # EF Core Migrations
│   ├── Dockerfile                       # Docker configuration
│   ├── Program.cs                       # App configuration
│   ├── appsettings.json                 # App settings
│   └── Pcm734Database.db                # SQLite database file
│
├── 📂 Frontend/                         # Flutter Mobile & Web App
│   ├── 📂 lib/
│   │   ├── main.dart                    # Entry point
│   │   │
│   │   ├── 📂 models/                   # Dart Models
│   │   │   ├── booking.dart
│   │   │   ├── court.dart
│   │   │   ├── member.dart
│   │   │   ├── notification.dart
│   │   │   ├── tournament.dart
│   │   │   ├── transaction.dart
│   │   │   └── wallet.dart
│   │   │
│   │   ├── 📂 providers/                # State Management (Provider)
│   │   │   ├── auth_provider.dart       # Authentication state
│   │   │   ├── booking_provider.dart    # Booking state
│   │   │   ├── notification_provider.dart # Notification state
│   │   │   └── wallet_provider.dart     # Wallet state
│   │   │
│   │   ├── 📂 services/                 # API & Real-time Services
│   │   │   ├── api_service.dart         # HTTP Client (Dio)
│   │   │   ├── signalr_service.dart     # SignalR Client
│   │   │   └── storage_service.dart     # Secure Storage
│   │   │
│   │   ├── 📂 screens/                  # UI Screens
│   │   │   ├── login_screen.dart        # Màn hình đăng nhập
│   │   │   ├── home_screen.dart         # Trang chủ
│   │   │   ├── admin_dashboard_screen.dart # Dashboard Admin
│   │   │   ├── booking_screen.dart      # Đặt sân
│   │   │   ├── wallet_screen.dart       # Quản lý ví
│   │   │   ├── tournament_screen.dart   # Giải đấu
│   │   │   ├── notification_screen.dart # Thông báo
│   │   │   ├── member_list_screen.dart  # Danh sách thành viên
│   │   │   └── topup_requests_screen.dart # Xét duyệt nạp tiền
│   │   │
│   │   └── 📂 widgets/                  # Reusable Widgets
│   │       ├── revenue_chart.dart       # Biểu đồ doanh thu
│   │       └── booking_calendar.dart    # Lịch đặt sân
│   │
│   ├── 📂 android/                      # Android configuration
│   ├── 📂 ios/                          # iOS configuration
│   ├── 📂 web/                          # Web configuration
│   ├── 📂 build/                        # Build outputs
│   │   ├── 📂 web/                      # Web build (deploy to Vercel)
│   │   └── 📂 app/outputs/flutter-apk/
│   │       └── app-release.apk          # Android APK
│   │
│   └── pubspec.yaml                     # Flutter dependencies
│
├── 📄 README.md                         # Tài liệu chính (file này)
├── 📄 HUONG_DAN_DEPLOY.md               # Hướng dẫn deploy chi tiết
└── 📄 Bai kiem tra_Flutter.pdf          # Đề bài kiểm tra
```

---

## 🛠️ Công Nghệ Sử Dụng

### Backend Stack

| Công nghệ                     | Phiên bản | Mục đích sử dụng                |
| ------------------------------- | ----------- | ------------------------------------ |
| **ASP.NET Core**          | 8.0         | Framework chính cho Web API         |
| **Entity Framework Core** | 8.0         | ORM, Code First Migrations           |
| **SQLite**                | Latest      | Database nhẹ, dễ deploy            |
| **JWT Bearer**            | Latest      | Authentication & Authorization       |
| **SignalR**               | 8.0         | Real-time communication (WebSockets) |
| **Swagger/OpenAPI**       | Latest      | API Documentation                    |
| **Docker**                | Latest      | Containerization                     |

**Packages chính**:

```xml
<PackageReference Include="Microsoft.AspNetCore.Authentication.JwtBearer" />
<PackageReference Include="Microsoft.AspNetCore.SignalR" />
<PackageReference Include="Microsoft.EntityFrameworkCore.Sqlite" />
<PackageReference Include="Microsoft.EntityFrameworkCore.Design" />
<PackageReference Include="Swashbuckle.AspNetCore" />
```

### Frontend Stack

| Công nghệ                      | Phiên bản | Mục đích sử dụng             |
| -------------------------------- | ----------- | --------------------------------- |
| **Flutter**                | 3.x         | Cross-platform framework          |
| **Dart**                   | 3.x         | Programming language              |
| **Provider**               | ^6.0.0      | State management                  |
| **Dio**                    | ^5.0.0      | HTTP Client cho API calls         |
| **SignalR Core**           | ^1.1.0      | Real-time client                  |
| **FL Chart**               | ^0.60.0     | Charts cho Admin Dashboard        |
| **Flutter Secure Storage** | ^9.0.0      | Lưu JWT tokens an toàn          |
| **Intl**                   | ^0.18.0     | Internationalization & formatting |

**Dependencies chính** (pubspec.yaml):

```yaml
dependencies:
  flutter:
    sdk: flutter
  provider: ^6.0.0
  dio: ^5.0.0
  signalr_netcore: ^1.1.0
  fl_chart: ^0.60.0
  flutter_secure_storage: ^9.0.0
  intl: ^0.18.0
```

---

## 🚀 Hướng Dẫn Chạy Dự Án

### Yêu Cầu Hệ Thống

- **.NET SDK 8.0** hoặc cao hơn
- **Flutter SDK 3.x** hoặc cao hơn
- **Docker Desktop** (tùy chọn, cho deployment)
- **Visual Studio Code** hoặc **Visual Studio 2022**
- **Android Studio** (cho build APK)

### 1️⃣ Chạy Backend API (Local)

```cmd
# Di chuyển vào thư mục Backend
cd Backend

# Restore các package NuGet
dotnet restore

# Chạy migrations (nếu chưa có database)
dotnet ef database update

# Chạy API server
dotnet run
```

**Kết quả**:

- ✅ API URL: `http://localhost:5000`
- ✅ Swagger UI: `http://localhost:5000/swagger`

**Kiểm tra API hoạt động**:

```bash
curl http://localhost:5000/api/health
# Response: {"status":"Healthy","timestamp":"2026-02-01T..."}
```

### 2️⃣ Chạy Frontend Flutter

#### Chạy trên Web (Chrome)

```cmd
# Di chuyển vào thư mục Frontend
cd Frontend

# Lấy dependencies
flutter pub get

# Chạy trên Chrome
flutter run -d chrome
```

#### Chạy trên Android Emulator

```cmd
# Mở Android Emulator trước
# Sau đó chạy:
flutter run
```

#### Chạy trên iOS Simulator (chỉ trên macOS)

```cmd
flutter run -d ios
```

### 3️⃣ Build Production

#### Build APK cho Android

```cmd
cd Frontend

# Build APK release
flutter build apk --release

# Hoặc build APK split theo ABI (giảm kích thước)
flutter build apk --split-per-abi
```

**Kết quả**: `Frontend/build/app/outputs/flutter-apk/app-release.apk`

#### Build Web

```cmd
cd Frontend

# Build web production
flutter build web --release
```

**Kết quả**: `Frontend/build/web/` (deploy folder này lên Vercel)

---

## 🐳 Chạy Bằng Docker

### Cách 1: Pull từ Docker Hub (Nhanh nhất)

```bash
# Pull image từ Docker Hub
docker pull ngocmi/pcm-backend:v1

# Chạy container
docker run -d -p 5000:8080 --name pcm-backend ngocmi/pcm-backend:v1
```

Truy cập: `http://localhost:5000/swagger`

### Cách 2: Build từ Source Code

```bash
# Di chuyển vào thư mục Backend
cd Backend

# Build Docker image
docker build -t pcm-backend:local .

# Chạy container
docker run -d -p 5000:8080 --name pcm-backend pcm-backend:local
```

### Quản lý Container

```bash
# Xem logs
docker logs pcm-backend

# Dừng container
docker stop pcm-backend

# Xóa container
docker rm pcm-backend

# Xem container đang chạy
docker ps
```

---

## 📱 Tính Năng Chính Của Hệ Thống

### 🔐 Authentication & Authorization

- **Đăng ký tài khoản** với email và password
- **Đăng nhập** với JWT Token
- **Phân quyền** Admin và User
- **Secure Storage** cho JWT tokens
- **Auto-refresh** token khi hết hạn
- **Logout** xóa token và session

### 💼 Admin Dashboard (Chỉ Admin)

#### Tổng Quan Tài Chính

- **Tổng quỹ CLB**: Hiển thị số dư hiện tại của quỹ
- **Doanh thu tháng này**: Tính tổng thu nhập từ booking và giải đấu
- **Chi tiêu tháng này**: Tính tổng chi phí vận hành

#### Biểu Đồ Thống Kê

- **Biểu đồ doanh thu 12 tháng**: Line chart hiển thị xu hướng thu/chi
- **Sử dụng FL Chart**: Tương tác, zoom, tooltip
- **Responsive**: Tự động điều chỉnh theo kích thước màn hình

#### Quản Lý Nạp Tiền

- **Xem danh sách yêu cầu nạp tiền**: Pending, Approved, Rejected
- **Xét duyệt**: Approve hoặc Reject với lý do
- **Upload ảnh bằng chứng**: Người dùng upload, Admin xem và xét duyệt
- **Real-time update**: Thông báo ngay khi có yêu cầu mới

#### Thống Kê Hệ Thống

- **Số lượng thành viên theo hạng (Tier)**: Bronze, Silver, Gold, VIP, Diamond
- **Số booking hôm nay/tuần này/tháng này**
- **Số giải đấu đang mở đăng ký**
- **Top 5 thành viên tích cực nhất**

### 🏆 Quản Lý Giải Đấu

#### Tạo Giải Đấu

- **Thông tin cơ bản**: Tên, mô tả, ngày bắt đầu/kết thúc
- **Số lượng đội**: Tối đa 16 đội
- **Phí tham gia**: Tự động trừ từ ví
- **Giải thưởng**: Phân chia theo hạng 1, 2, 3

#### Đăng Ký Tham Gia

- **Xem danh sách giải đấu**: Đang mở, đang diễn ra, đã kết thúc
- **Đăng ký đội**: Tên đội, danh sách thành viên
- **Thanh toán**: Trừ tiền từ ví tự động

#### Lịch Thi Đấu

- **Tự động tạo lịch**: Hệ thống tự động phân bổ sân và giờ thi đấu
- **Cập nhật tỉ số**: Admin hoặc trọng tài cập nhật kết quả
- **Real-time**: Người xem thấy tỉ số cập nhật ngay lập tức
- **Bảng xếp hạng**: Tự động tính điểm và xếp hạng

### 🎾 Đặt Sân (Booking)

#### Đặt Sân Thường

- **Lịch trực quan**: Calendar view hiển thị sân trống/đã đặt
- **Chọn giờ**: Chọn khung giờ từ 6:00 - 22:00
- **Giá linh hoạt**: Giờ vàng (18:00-22:00) giá cao hơn
- **Thanh toán**: Trừ tiền từ ví ngay lập tức
- **Auto-cancel**: Tự động hủy nếu không thanh toán trong 15 phút

#### Đặt Sân Định Kỳ (Recurring Booking)

- **Chỉ dành cho VIP/Diamond**: Đặc quyền cho thành viên cao cấp
- **Đặt theo tuần**: Chọn ngày trong tuần (Thứ 2, 4, 6...)
- **Tự động gia hạn**: Hệ thống tự động tạo booking mới mỗi tuần
- **Ưu tiên**: Được ưu tiên giữ sân trước người đặt thường

#### Quản Lý Booking

- **Xem lịch sử**: Tất cả booking đã đặt, đang chờ, đã hủy
- **Hủy booking**: Hoàn tiền 80% nếu hủy trước 24h
- **Nhắc nhở**: Nhận thông báo trước 24h qua SignalR

### 💰 Quản Lý Ví (Wallet)

#### Nạp Tiền

- **Nhập số tiền**: Tối thiểu 50,000 VNĐ
- **Upload ảnh chuyển khoản**: Bằng chứng thanh toán
- **Chờ xét duyệt**: Admin approve/reject
- **Thông báo kết quả**: Real-time notification

#### Lịch Sử Giao Dịch

- **Xem tất cả giao dịch**: Nạp tiền, thanh toán booking, giải đấu
- **Filter**: Theo loại, theo ngày
- **Chi tiết**: Số tiền, thời gian, trạng thái, mô tả

#### Hạng Thành Viên (Tier System)

- **Bronze** (0-999 điểm): Thành viên mới
- **Silver** (1,000-2,999 điểm): Giảm 5% phí booking
- **Gold** (3,000-4,999 điểm): Giảm 10% phí booking
- **VIP** (5,000-9,999 điểm): Giảm 15%, được đặt sân định kỳ
- **Diamond** (10,000+ điểm): Giảm 20%, ưu tiên cao nhất

**Tích điểm**: 1 VNĐ chi tiêu = 1 điểm

### 🔔 Thông Báo Real-time

#### SignalR Integration

- **Kết nối WebSocket**: Tự động kết nối khi đăng nhập
- **Reconnect**: Tự động kết nối lại khi mất kết nối
- **Nhận thông báo ngay lập tức**: Không cần refresh

#### Các Loại Thông Báo

- **Nạp tiền được duyệt/từ chối**
- **Booking sắp đến (24h trước)**
- **Booking bị hủy tự động**
- **Giải đấu mới mở đăng ký**
- **Kết quả thi đấu cập nhật**
- **Thăng hạng thành viên**

#### Quản Lý Thông Báo

- **Đánh dấu đã đọc**: Tap vào thông báo
- **Xóa thông báo**: Swipe to delete
- **Badge count**: Hiển thị số thông báo chưa đọc

### 👥 Quản Lý Thành Viên (Admin)

- **Xem danh sách**: Tất cả thành viên với thông tin chi tiết
- **Tìm kiếm**: Theo tên, email, MSSV
- **Filter**: Theo hạng (Tier), trạng thái
- **Xem chi tiết**: Lịch sử booking, giao dịch, điểm tích lũy
- **Khóa/Mở khóa tài khoản**: Quản lý quyền truy cập

---

## 🔧 Cấu Hình Chi Tiết

### Backend Configuration (appsettings.json)

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Data Source=Pcm734Database.db"
  },
  "Jwt": {
    "Key": "YourSuperSecretKeyForJWT_MustBe32CharsOrMore_734",
    "Issuer": "PcmBackend",
    "Audience": "PcmFrontend",
    "ExpiryInMinutes": 1440
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  }
}
```

### Frontend Configuration (lib/services/api_service.dart)

```dart
class ApiService {
  // Production API URL (Render.com)
  static const String baseUrl = 'https://pcm-backend-v1-1.onrender.com/api';
  
  // Local development URL
  // static const String baseUrl = 'http://localhost:5000/api';
  
  // SignalR Hub URL
  static const String hubUrl = 'https://pcm-backend-v1-1.onrender.com/notificationHub';
}
```

### CORS Configuration (Program.cs)

```csharp
builder.Services.AddCors(options =>
{
    options.AddPolicy("AllowAll", policy =>
    {
        policy.AllowAnyOrigin()
              .AllowAnyMethod()
              .AllowAnyHeader();
    });
});
```

---

## 📊 Database Schema

### Entity Models (Prefix 734_)

#### 734_Member (Thành viên)

```csharp
- MemberId (PK)
- FullName
- Email (Unique)
- PasswordHash
- StudentId (MSSV)
- Role (Admin/User)
- Tier (Bronze/Silver/Gold/VIP/Diamond)
- Points (Điểm tích lũy)
- CreatedAt
- UpdatedAt
```

#### 734_Wallet (Ví tiền)

```csharp
- WalletId (PK)
- MemberId (FK)
- Balance (Số dư)
- CreatedAt
- UpdatedAt
```

#### 734_Booking (Đặt sân)

```csharp
- BookingId (PK)
- MemberId (FK)
- CourtId (FK)
- BookingDate
- StartTime
- EndTime
- TotalPrice
- Status (Pending/Confirmed/Cancelled)
- CreatedAt
```

#### 734_Tournament (Giải đấu)

```csharp
- TournamentId (PK)
- Name
- Description
- StartDate
- EndDate
- MaxTeams
- EntryFee
- PrizePool
- Status (Open/InProgress/Completed)
- CreatedAt
```

**Và nhiều entity khác**: Court, RecurringBooking, Match, Transaction, Notification, ClubFund, TopUpRequest

### Relationships

```
Member 1 ─── 1 Wallet
Member 1 ─── N Booking
Member 1 ─── N Transaction
Member 1 ─── N Notification
Court 1 ─── N Booking
Tournament 1 ─── N Match
```

---

## 🌐 API Endpoints

### Authentication

- `POST /api/auth/register` - Đăng ký tài khoản mới
- `POST /api/auth/login` - Đăng nhập
- `GET /api/auth/profile` - Lấy thông tin profile (JWT required)

### Booking

- `GET /api/booking` - Lấy danh sách booking
- `POST /api/booking` - Tạo booking mới
- `PUT /api/booking/{id}/cancel` - Hủy booking
- `GET /api/booking/available-slots` - Lấy khung giờ trống

### Wallet

- `GET /api/wallet` - Lấy thông tin ví
- `POST /api/wallet/topup` - Tạo yêu cầu nạp tiền
- `GET /api/wallet/transactions` - Lịch sử giao dịch

### Tournament

- `GET /api/tournament` - Danh sách giải đấu
- `POST /api/tournament` - Tạo giải đấu (Admin)
- `POST /api/tournament/{id}/register` - Đăng ký tham gia
- `GET /api/tournament/{id}/matches` - Lịch thi đấu

### Admin

- `GET /api/admin/dashboard` - Dashboard statistics
- `GET /api/admin/topup-requests` - Danh sách yêu cầu nạp tiền
- `PUT /api/admin/topup-requests/{id}/approve` - Duyệt nạp tiền
- `PUT /api/admin/topup-requests/{id}/reject` - Từ chối nạp tiền
- `GET /api/admin/members` - Danh sách thành viên

**Tổng cộng**: 40+ API endpoints

Xem chi tiết tại: [Swagger UI](https://pcm-backend-v1-1.onrender.com/swagger)

---

## 🚢 Deployment Guide

### Backend Deployment (Render.com)

1. **Build Docker Image**:

   ```bash
   cd Backend
   docker build -t pcm-backend:v1 .
   ```
2. **Push to Docker Hub**:

   ```bash
   docker login
   docker tag pcm-backend:v1 YOUR_USERNAME/pcm-backend:v1
   docker push YOUR_USERNAME/pcm-backend:v1
   ```
3. **Deploy on Render.com**:

   - Vào [Render.com](https://render.com)
   - New → Web Service → Deploy from Docker Image
   - Image URL: `docker.io/YOUR_USERNAME/pcm-backend:v1`
   - Environment Variable: `ASPNETCORE_URLS=http://0.0.0.0:10000`
   - Deploy

### Frontend Deployment (Vercel)

1. **Build Flutter Web**:

   ```bash
   cd Frontend
   flutter build web --release
   ```
2. **Deploy to Vercel**:

   ```bash
   cd build/web
   npx vercel --prod
   ```
3. **Cấu hình**:

   - Project name: `pcm-frontend`
   - Framework: Other
   - Build command: (leave empty)
   - Output directory: `.`

**Chi tiết đầy đủ**: Xem file [HUONG_DAN_DEPLOY.md](HUONG_DAN_DEPLOY.md)

---

## 🧪 Testing

### Test Backend API

```bash
# Health check
curl http://localhost:5000/api/health

# Login
curl -X POST http://localhost:5000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"admin@pcm.com","password":"Admin123"}'

# Get profile (với JWT token)
curl http://localhost:5000/api/auth/profile \
  -H "Authorization: Bearer YOUR_JWT_TOKEN"
```

### Test Frontend

```bash
# Run tests
cd Frontend
flutter test

# Run integration tests
flutter test integration_test/
```

---

## 📸 Screenshots

> **Lưu ý**: Screenshots được chụp từ ứng dụng đang chạy trên Vercel và Render.com

### 1. Login Screen

- Giao diện đăng nhập với email và password
- Hiển thị tài khoản demo để test nhanh
- Validation input

### 2. Admin Dashboard

- Biểu đồ doanh thu 12 tháng
- Thống kê tổng quỹ, doanh thu, chi tiêu
- Số lượng thành viên theo hạng
- Danh sách yêu cầu nạp tiền chờ duyệt

### 3. Booking Screen

- Calendar view hiển thị sân trống/đã đặt
- Chọn giờ và thanh toán
- Lịch sử booking

### 4. Wallet Screen

- Số dư ví hiện tại
- Hạng thành viên và điểm tích lũy
- Lịch sử giao dịch
- Nút nạp tiền

### 5. Tournament Screen

- Danh sách giải đấu
- Chi tiết giải đấu và lịch thi đấu
- Đăng ký tham gia

---

## 🎯 Kết Quả Đạt Được

### ✅ Hoàn Thành Đầy Đủ Yêu Cầu Đề Bài

1. ✅ **Backend API RESTful** với ASP.NET Core 8
2. ✅ **Flutter Mobile App** chạy trên Android
3. ✅ **Flutter Web App** chạy trên browser
4. ✅ **Authentication & Authorization** với JWT
5. ✅ **State Management** với Provider
6. ✅ **Real-time Communication** với SignalR
7. ✅ **Database** với EF Core Code First
8. ✅ **Docker Containerization**
9. ✅ **Cloud Deployment** (Render.com + Vercel)
10. ✅ **API Documentation** với Swagger

### 🏆 Điểm Cộng

- ✨ **Background Services**: Auto-cancel, Auto-remind
- ✨ **Charts & Analytics**: FL Chart cho Admin Dashboard
- ✨ **Tier System**: Hệ thống hạng thành viên với ưu đãi
- ✨ **Recurring Booking**: Đặt sân định kỳ cho VIP
- ✨ **Tournament Management**: Quản lý giải đấu hoàn chỉnh
- ✨ **Real-time Notifications**: SignalR WebSocket
- ✨ **Responsive UI**: Tương thích mọi kích thước màn hình
- ✨ **Secure Storage**: Flutter Secure Storage cho JWT
- ✨ **Error Handling**: Try-catch toàn diện
- ✨ **Code Quality**: Clean code, comments, naming conventions

---

## 🐛 Known Issues & Limitations

### Backend

- **Free Tier Render.com**: Backend "ngủ" sau 15 phút không hoạt động, cần 30-60s để "thức dậy"
- **SQLite**: Không phù hợp cho production lớn, nên chuyển sang PostgreSQL/MySQL

### Frontend

- **Web Performance**: Lần đầu load có thể chậm do Flutter Web bundle size lớn
- **iOS Build**: Chưa test trên thiết bị iOS thật (chỉ test trên simulator)

### General

- **Image Upload**: Chưa implement upload lên cloud storage (đang lưu base64 trong DB)
- **Email Service**: Chưa tích hợp gửi email thông báo
- **Payment Gateway**: Chưa tích hợp cổng thanh toán thật

---

## 🔮 Hướng Phát Triển Tương Lai

1. **Tích hợp Payment Gateway**: VNPay, MoMo, ZaloPay
2. **Email Notifications**: SendGrid hoặc AWS SES
3. **Cloud Storage**: AWS S3 hoặc Cloudinary cho upload ảnh
4. **Push Notifications**: Firebase Cloud Messaging
5. **Analytics**: Google Analytics, Firebase Analytics
6. **Performance**: Caching với Redis
7. **Database**: Migrate sang PostgreSQL
8. **CI/CD**: GitHub Actions cho auto-deploy
9. **Testing**: Unit tests, Integration tests, E2E tests
10. **Monitoring**: Application Insights, Sentry

---

## 📚 Tài Liệu Tham Khảo

### Official Documentation

- [ASP.NET Core Documentation](https://docs.microsoft.com/en-us/aspnet/core/)
- [Flutter Documentation](https://docs.flutter.dev/)
- [Entity Framework Core](https://docs.microsoft.com/en-us/ef/core/)
- [SignalR Documentation](https://docs.microsoft.com/en-us/aspnet/core/signalr/)

### Tutorials & Guides

- [JWT Authentication in ASP.NET Core](https://jasonwatmore.com/post/2021/12/14/net-6-jwt-authentication-tutorial-with-example-api)
- [Flutter Provider State Management](https://docs.flutter.dev/development/data-and-backend/state-mgmt/simple)
- [Docker for .NET Developers](https://docs.docker.com/samples/dotnet/)

---

## 📞 Liên Hệ & Hỗ Trợ

**Sinh viên thực hiện**: Đỗ Văn Tuyên
**MSSV**: xxxxx734
**Lớp**: CNTT 17-08
**Email**: dovantuyen.2005nb@gmail.com
**GitHub**:http://github.com/GitDoTuyen

---

## 📄 License

Dự án này được thực hiện cho mục đích học tập và nghiên cứu.
© 2026 Đỗ Văn Tuyên - All Rights Reserved.

---

## 🙏 Lời Cảm Ơn

Em xin chân thành cảm ơn:

- **Giảng viên hướng dẫn** đã tận tình chỉ bảo
- **Các bạn trong lớp** đã hỗ trợ và động viên
- **Cộng đồng Flutter & .NET** trên Stack Overflow, GitHub

---

**📅 Ngày hoàn thành**: 01/02/2026
**📝 Phiên bản**: 1.0.0
**🎓 Môn học**: Lập Trình Di Động Nâng Cao
**🏫 Trường**: Đại Học Đại Nam

---

> **"Code is like humor. When you have to explain it, it's bad."** – Cory House

**Happy Coding! 🚀**

# HƯỚNG DẪN DEPLOY DỰ ÁN PCM (Pickleball Club Management)

Tài liệu này ghi lại các bước deploy Backend và Frontend đã thực hiện.

---

## 📋 Tổng quan kết quả Deploy

| Thành phần | URL/Link |
|------------|----------|
| **🖥️ Flutter Web** | https://pcm-pcmfrontend.vercel.app |
| **⚙️ Backend API** | https://pcm-backend-v1-1.onrender.com |
| **📖 Swagger API** | https://pcm-backend-v1-1.onrender.com/swagger |
| **🐳 Docker Hub** | https://hub.docker.com/r/ngocmi/pcm-backend |

### 🔐 Tài khoản Demo
| Email | Password | Role |
|-------|----------|------|
| `admin@pcm.com` | `Admin123` | Admin |
| `user@pcm.com` | `User1234` | User |

---

## 🔧 PHẦN 1: DEPLOY BACKEND

### Bước 1: Cấu hình Docker

Tạo file `Backend/Dockerfile`:

```dockerfile
# Build stage
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src
COPY ["PcmBackend.csproj", "./"]
RUN dotnet restore "PcmBackend.csproj"
COPY . .
RUN dotnet build "PcmBackend.csproj" -c Release -o /app/build

# Publish stage
FROM build AS publish
RUN dotnet publish "PcmBackend.csproj" -c Release -o /app/publish

# Runtime stage
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS final
WORKDIR /app
COPY --from=publish /app/publish .

# Expose port and force override URLs
EXPOSE 8080
ENV ASPNETCORE_URLS=http://0.0.0.0:8080
ENV ASPNETCORE_ENVIRONMENT=Production

# Override the hardcoded URLs in Program.cs
ENTRYPOINT ["dotnet", "PcmBackend.dll", "--urls", "http://0.0.0.0:8080"]
```

### Bước 2: Sửa Program.cs (hỗ trợ Docker)

```csharp
var builder = WebApplication.CreateBuilder(args);

// Only set default URLs if ASPNETCORE_URLS is not set (for local development)
if (string.IsNullOrEmpty(Environment.GetEnvironmentVariable("ASPNETCORE_URLS")))
{
    builder.WebHost.UseUrls("http://localhost:5000", "http://0.0.0.0:5000");
}
```

### Bước 3: Build Docker Image

```bash
cd Backend
docker build -t pcm-backend:v1 .
```

### Bước 4: Push lên Docker Hub

```bash
# Đăng nhập Docker Hub
docker login

# Tag image với username Docker Hub
docker tag pcm-backend:v1 YOUR_USERNAME/pcm-backend:v1

# Push lên Docker Hub
docker push YOUR_USERNAME/pcm-backend:v1
```

### Bước 5: Deploy lên Render.com

1. Vào https://render.com → Đăng nhập bằng GitHub
2. Bấm **New +** → **Web Service**
3. Chọn **Deploy an existing image from a registry**
4. Nhập Image URL:
   ```
   docker.io/YOUR_USERNAME/pcm-backend:v1
   ```
5. Cấu hình:
   - **Name**: `pcm-backend`
   - **Region**: Singapore
   - **Instance Type**: Free
6. Thêm Environment Variable:
   | Key | Value |
   |-----|-------|
   | `ASPNETCORE_URLS` | `http://0.0.0.0:10000` |
7. Bấm **Create Web Service**
8. Đợi 3-5 phút để deploy

**Kết quả**: `https://pcm-backend-xxxx.onrender.com`

---

## 🌐 PHẦN 2: DEPLOY FRONTEND (FLUTTER WEB)

### Bước 1: Cập nhật API URL

Sửa file `Frontend/lib/services/api_service.dart`:

```dart
class ApiService {
  // Production API URL (Render.com)
  static const String baseUrl = 'https://pcm-backend-xxxx.onrender.com/api';
  // ...
}
```

### Bước 2: Build Flutter Web

```bash
cd Frontend
flutter build web --release
```

Kết quả: Thư mục `build/web`

### Bước 3: Deploy lên Vercel

```bash
# Cài Vercel CLI
npx vercel login

# Deploy
cd build/web
npx vercel --prod
```

Trả lời các câu hỏi:
- **Set up and deploy?** → `y`
- **Which scope?** → Chọn scope của bạn
- **Link to existing project?** → `n`
- **Project name?** → `pcm-frontend`
- **Directory?** → `.`
- **Override settings?** → `n`

**Kết quả**: `https://pcm-frontend.vercel.app`

---

## 📱 PHẦN 3: BUILD APK FLUTTER

### Bước 1: Thêm quyền INTERNET

Sửa file `Frontend/android/app/src/main/AndroidManifest.xml`:

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android">
    <uses-permission android:name="android.permission.INTERNET"/>
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
    <application
        ...
```

### Bước 2: Build APK

```bash
cd Frontend
flutter build apk --release
```

**Kết quả**: `build/app/outputs/flutter-apk/app-release.apk`

---

## 🐳 PHẦN 4: CHẠY BẰNG DOCKER (Local)

Bất kỳ ai có Docker đều có thể chạy Backend:

```bash
docker run -d -p 5000:8080 ngocmi/pcm-backend:v1
```

Truy cập: `http://localhost:5000/swagger`

---

## ⚠️ LƯU Ý QUAN TRỌNG

### Free Tier của Render.com
- Backend sẽ "ngủ" sau 15 phút không hoạt động
- Khi có request mới, cần 30-60 giây để "thức dậy"
- Đây là giới hạn của bản miễn phí

### CORS đã được cấu hình
- Backend cho phép mọi Origin (`AllowAnyOrigin`)
- Không cần cấu hình thêm cho Frontend

---

## 📝 COMMIT HISTORY

1. `Add Dockerfile for Render deploy`
2. `Update README with deploy links and update API URL`

---

**Sinh viên**: Đỗ Văn Tuyên  
**MSSV**: xxxxx734  
**Ngày**: 31/01/2026

# Quick Start Guide

Get the Borrowers Log System up and running in 10 minutes!

## ⚡ Quick Setup (10 minutes)

### 1. Database (2 minutes)

**For Windows (Recommended):**
1. Open HeidiSQL, MySQL Workbench, or phpMyAdmin
2. Connect to your MariaDB/MySQL server
3. Load and execute `backend/database.sql`

**OR using Command Line:**
```bash
# If MySQL/MariaDB CLI is in PATH:
mysql -u root -p < backend/database.sql

# If not, use full path:
"C:\Program Files\MariaDB 10.11\bin\mysql.exe" -u root -p < backend/database.sql
```

**See `DATABASE_SETUP_WINDOWS.md` for detailed Windows instructions**

### 2. Backend (3 minutes)

```bash
cd backend
npm install
copy .env.example .env  # Edit .env with your DB password
npm start
```

Backend runs on: http://localhost:3000

### 3. Frontend (5 minutes)

```bash
cd borrowers_log_system
flutter pub get
flutter run -d chrome
```

## 🔑 Login

- **Username**: `admin`
- **Password**: `admin123`

## ✅ Verify

1. Open: http://localhost:3000/health
2. Should see: `{"status":"ok"}`
3. Login to Flutter app
4. Start managing borrowers!

## 📚 Next Steps

- See `SETUP.md` for detailed instructions
- See `README.md` for full documentation

## 🐛 Issues?

- Check backend is running: http://localhost:3000/health
- Check MariaDB is running
- Verify `.env` file has correct credentials
- Run `flutter pub get` again if packages fail

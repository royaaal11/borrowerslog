# 🚀 Getting Started - Step by Step

Since you're on Windows, here's the easiest way to get started:

## Step 1: Database Setup (EASIEST Method)

### Option A: Using HeidiSQL (Recommended - Easiest)

1. **Download HeidiSQL** (Free): https://www.heidisql.com/download.php
2. **Open HeidiSQL**
3. **Connect to your MariaDB/MySQL** (usually localhost, root user)
4. **Open File** → Load SQL file
5. **Select** `backend/database.sql`
6. **Click Execute** button (F9)

Done! Database is ready.

### Option B: Copy/Paste SQL

1. Open any database client (phpMyAdmin, MySQL Workbench, etc.)
2. Open `backend/database.sql` in a text editor
3. Copy the entire contents
4. Paste into your database client's SQL query window
5. Execute

## Step 2: Backend Setup

Open **PowerShell** or **Command Prompt**:

```powershell
cd backend
npm install
```

Create `.env` file in `backend` folder:
```
PORT=3000
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_password_here
DB_NAME=borrowers_log
JWT_SECRET=change-this-secret
```

Then start:
```powershell
npm start
```

## Step 3: Frontend Setup

Open **ANOTHER** PowerShell/Command Prompt window:

```powershell
cd borrowers_log_system
flutter pub get
flutter run -d chrome
```

## Step 4: Login

Open Chrome, go to: `http://localhost:3000/health` (should say "ok")

Then use Flutter app:
- Username: `admin`
- Password: `admin123`

## Troubleshooting

### Can't find npm?
- Install Node.js: https://nodejs.org/

### MariaDB not installed?
- Download MariaDB: https://mariadb.org/download/
- Or use MySQL: https://dev.mysql.com/downloads/

### Can't run Flutter?
- Install Flutter SDK: https://flutter.dev/docs/get-started/install

## That's It!

You now have a complete Borrowers Log System running! 🎉

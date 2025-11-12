# Windows Quick Reference Card

## 🎯 Right Now - Do This:

### Step 1: Database (Choose ONE method)

**Easiest: Use HeidiSQL**
1. Download: https://www.heidisql.com/download.php
2. Install and open
3. Connect to your MySQL/MariaDB
4. File → Load SQL file
5. Select: `backend\database.sql`
6. Press F9 to execute

**Alternative: Use MySQL Workbench**
1. Open MySQL Workbench
2. Connect to your server
3. Open `backend\database.sql`
4. Copy all SQL
5. Paste in SQL query window
6. Execute

### Step 2: Backend

Open PowerShell in project root:

```powershell
cd backend
npm install
```

Then create `.env` file in `backend` folder:
```
PORT=3000
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=
DB_NAME=borrowers_log
JWT_SECRET=my-secret-123
```

Then start:
```powershell
npm start
```

### Step 3: Frontend

Open NEW PowerShell window:

```powershell
cd borrowers_log_system
flutter run -d chrome
```

### Step 4: Test

1. Open Chrome
2. Go to: http://localhost:3000/health
3. Should see: {"status":"ok"}

### Step 5: Login

In Flutter app:
- Username: `admin`
- Password: `admin123`

## ✅ Checklist

- [ ] Database created with tables
- [ ] Backend running on port 3000
- [ ] Health check works
- [ ] Frontend running
- [ ] Can login

## 🐛 Common Issues

**"MySQL command not found"**
→ Use HeidiSQL or MySQL Workbench (GUI tools)

**"npm not found"**
→ Install Node.js from nodejs.org

**"Flutter not found"**
→ Install Flutter SDK and add to PATH

**"Backend can't connect to database"**
→ Check `.env` file credentials

**"No module found"**
→ Run `npm install` in backend folder

## 📞 Need Help?

- Database Setup: See `DATABASE_SETUP_WINDOWS.md`
- Backend Setup: See `BACKEND_SETUP_INSTRUCTIONS.md`
- Full Guide: See `START_SETUP.md`


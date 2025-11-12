# Backend Setup Instructions

## Quick Start

### 1. Install Dependencies

Open PowerShell in the `backend` folder:

```powershell
npm install
```

### 2. Configure Environment

Copy `env_example.txt` and rename it to `.env`, then edit with your database credentials:

```
PORT=3000
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_actual_password_here
DB_NAME=borrowers_log
JWT_SECRET=change-this-to-something-random-and-secure
```

**Important:** Replace:
- `your_actual_password_here` with your MariaDB/MySQL root password
- `change-this-to-something-random-and-secure` with a long random string

### 3. Start the Server

Development mode (auto-restart on changes):
```powershell
npm run dev
```

Production mode:
```powershell
npm start
```

You should see:
```
Server is running on http://localhost:3000
```

### 4. Verify Backend is Working

Open browser: http://localhost:3000/health

You should see:
```json
{"status":"ok","message":"Borrowers Log API is running"}
```

## Troubleshooting

### "Cannot find module" errors
```powershell
npm install
```

### "Port already in use"
- Change PORT in `.env` to something else (e.g., 3001)
- Or close the other application using port 3000

### "Database connection error"
- Make sure MariaDB/MySQL is running
- Check credentials in `.env`
- Verify database exists (should be created by database.sql)

### "Cannot find .env"
- Create `.env` file manually in `backend` folder
- Copy content from `env_example.txt`
- Make sure it's named exactly `.env` (not `env.txt`)

## Next Steps

After backend is running:
1. Go to `borrowers_log_system` folder
2. Run `flutter pub get`
3. Run `flutter run -d chrome`
4. Login with: admin / admin123

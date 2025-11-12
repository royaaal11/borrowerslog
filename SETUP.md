# Setup Guide - Borrowers Log System

This guide will help you set up and run the Borrowers Log System on your local machine.

## Prerequisites

Before you begin, ensure you have the following installed:

- **Flutter SDK** (3.35.4 or later)
  - Download from: https://flutter.dev/docs/get-started/install
  - Verify installation: `flutter --version`

- **Node.js** (v16 or later)
  - Download from: https://nodejs.org/
  - Verify installation: `node --version`

- **MariaDB** (v10.5 or later)
  - Download from: https://mariadb.org/download/
  - Verify installation: `mysql --version`

- **npm** (comes with Node.js)
  - Verify: `npm --version`

## Step-by-Step Setup

### 1. Clone/Download the Project

If you've cloned or downloaded this repository, navigate to the project directory:

```bash
cd borrowers-log-system
```

### 2. Database Setup

#### 2.1 Start MariaDB Service

Make sure MariaDB is running on your system:

```bash
# On Windows
# Usually runs automatically as a service
# Check via Services app

# On Linux
sudo systemctl start mariadb

# On macOS
brew services start mariadb
```

#### 2.2 Create Database

Open a MariaDB client (MySQL Workbench, HeidiSQL, or command line):

```bash
mysql -u root -p
```

Or use a GUI tool like MySQL Workbench or HeidiSQL.

#### 2.3 Run SQL Script

Copy and paste the contents of `backend/database.sql` into your MariaDB client, or run:

```bash
mysql -u root -p < backend/database.sql
```

This will:
- Create the `borrowers_log` database
- Create all required tables (users, inventory, borrowers)
- Insert sample data (default admin user and sample inventory items)

### 3. Backend Setup

#### 3.1 Navigate to Backend Directory

```bash
cd backend
```

#### 3.2 Install Dependencies

```bash
npm install
```

This will install all required packages:
- express
- mariadb
- jsonwebtoken
- bcryptjs
- cors
- dotenv
- nodemon (dev dependency)

#### 3.3 Configure Environment Variables

Create a `.env` file in the `backend` directory:

```bash
# Windows
copy .env.example .env

# Linux/macOS
cp .env.example .env
```

Edit `.env` and update with your database credentials:

```env
PORT=3000
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_mysql_password
DB_NAME=borrowers_log
JWT_SECRET=change-this-to-a-random-secret-key
```

**Important**: Replace `your_mysql_password` with your actual MariaDB root password.

#### 3.4 Start the Backend Server

Development mode (with auto-restart):
```bash
npm run dev
```

Production mode:
```bash
npm start
```

You should see:
```
Server is running on http://localhost:3000
```

#### 3.5 Test Backend

Open your browser and visit:
```
http://localhost:3000/health
```

You should see:
```json
{"status":"ok","message":"Borrowers Log API is running"}
```

### 4. Frontend Setup

#### 4.1 Navigate to Flutter Project

Open a new terminal window and navigate to the Flutter project:

```bash
cd borrowers_log_system
```

#### 4.2 Install Dependencies

```bash
flutter pub get
```

This will install all Flutter packages:
- http
- shared_preferences
- image_picker
- signature
- intl
- file_picker

#### 4.3 Update API URL (if needed)

Edit `lib/services/api_service.dart` and update the `baseUrl` if your backend is running on a different port or URL:

```dart
static const String baseUrl = 'http://localhost:3000/api';
```

#### 4.4 Run the Application

For web development (Chrome):
```bash
flutter run -d chrome
```

Or build for web:
```bash
flutter build web
```

Then serve with any web server:
```bash
cd build/web
# Use Python's http.server or any web server
python -m http.server 8000
```

Visit: `http://localhost:8000`

## Verifying the Setup

### 1. Check Backend is Running

Visit: `http://localhost:3000/health`

Expected response:
```json
{"status":"ok","message":"Borrowers Log API is running"}
```

### 2. Login to the Application

1. Open the Flutter app in your browser
2. Use default credentials:
   - **Username**: `admin`
   - **Password**: `admin123`

### 3. Test Features

1. **Dashboard**: Should show list of borrowers
2. **Add Borrow Record**: Click "Add Borrow" button and fill form
3. **Inventory**: Click inventory icon to view items
4. **Return Item**: Click "Mark as Returned" on any out item
5. **Export**: Use export buttons to download CSV files

## Default Data

The database comes with:

### Default Users
- **Admin User**:
  - Username: `admin`
  - Password: `admin123`
  - Type: Admin

- **Borrower User**:
  - Username: `borrower1`
  - Password: `admin123`
  - Type: Borrower

### Sample Inventory Items
- Laptop Dell XPS 13 (3 available)
- Laptop HP Pavilion (2 available)
- Tablet iPad Pro (5 available)
- Projector Epson (2 available)
- Camera Canon (1 available)

## Troubleshooting

### Backend Issues

**"Cannot connect to database"**
- Check MariaDB is running
- Verify credentials in `.env`
- Ensure database exists: `mysql -u root -p` then `USE borrowers_log;`

**"Port 3000 already in use"**
- Change PORT in `.env` file
- Or kill the process using port 3000

**"Module not found" errors**
- Run `npm install` again
- Delete `node_modules` and reinstall

### Frontend Issues

**"Packages won't install"**
```bash
flutter clean
flutter pub get
```

**"API connection failed"**
- Verify backend is running
- Check CORS is enabled in backend
- Check API URL in `api_service.dart`
- Open browser console for errors

**"webcam not working in web"**
- Use HTTPS (required for webcam in browsers)
- Or use file upload instead

### Database Issues

**"Table doesn't exist"**
- Run `database.sql` again
- Check database name in `.env`

**"Access denied"**
- Verify username and password in `.env`
- Check MariaDB user permissions

## Next Steps

1. **Change default password** in database for production use
2. **Update JWT_SECRET** in `.env` for production
3. **Configure HTTPS** for production deployment
4. **Set up proper backup** for database
5. **Configure CORS** for production domain

## Development Tips

### Backend Hot Reload
Backend uses nodemon for auto-restart on file changes when running `npm run dev`.

### Flutter Hot Reload
Flutter hot reload works when running `flutter run`. Press `r` for hot reload, `R` for hot restart.

### Database Browser
Consider using a database management tool:
- **MySQL Workbench**
- **HeidiSQL** (Windows)
- **Sequel Pro** (macOS)
- **DBeaver** (Cross-platform)

### API Testing
Use tools like:
- **Postman**
- **Thunder Client** (VS Code extension)
- **curl** (command line)

## Production Deployment

For production deployment:

1. Use environment variables for sensitive data
2. Enable HTTPS for security
3. Use production database with backups
4. Configure proper CORS settings
5. Use a process manager like PM2 for Node.js
6. Build Flutter web with optimizations: `flutter build web --release`

## Support

If you encounter issues:
1. Check error messages in console
2. Review logs in backend terminal
3. Verify all prerequisites are installed
4. Check database connection
5. Review this guide again

For additional help, check the main README.md file.

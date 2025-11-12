# Database Setup for Windows

## Option 1: Using MariaDB Command Line (If Installed)

If MariaDB command line is installed, first add it to your PATH, or run the full path:

### Find MariaDB Installation
MariaDB is typically installed at:
- `C:\Program Files\MariaDB 10.11\bin\mysql.exe` (or similar version)
- `C:\Program Files\MySQL\MySQL Server 8.0\bin\mysql.exe` (if using MySQL)

### Method 1: Use Full Path
```bash
"C:\Program Files\MariaDB 10.11\bin\mysql.exe" -u root -p < backend/database.sql
```

Or with your root password:
```bash
"C:\Program Files\MariaDB 10.11\bin\mysql.exe" -u root -pYourPassword < backend/database.sql
```

### Method 2: Add to PATH
Add this to your system PATH:
```
C:\Program Files\MariaDB 10.11\bin
```
Then restart terminal and use:
```bash
mysql -u root -p < backend/database.sql
```

## Option 2: Using MySQL Workbench (Recommended for Windows)

1. Open **MySQL Workbench**
2. Create a connection to your local MariaDB/MySQL
3. Click on your connection
4. Click on the folder icon or go to Server → Data Import
5. Select "Import from Self-Contained File"
6. Browse and select `backend/database.sql`
7. Select the `borrowers_log` database (or create it first)
8. Click "Start Import"

## Option 3: Using HeidiSQL (Recommended for Windows)

1. Open **HeidiSQL**
2. Connect to your MariaDB/MySQL server
3. Right-click on your connection → "New" → "Query tab"
4. Click "File" → "Load SQL file"
5. Select `backend/database.sql`
6. Execute the file (F9)

## Option 4: Using Command Prompt with PowerShell

```powershell
# Navigate to project directory
cd C:\Users\Bravo\Downloads\benecow

# Run SQL file
Get-Content backend/database.sql | mysql -u root -p
```

## Option 5: Manual SQL Execution

1. Open a database client (HeidiSQL, MySQL Workbench, phpMyAdmin, etc.)
2. Copy the contents of `backend/database.sql`
3. Paste into the SQL query editor
4. Execute

## Creating the Database Manually

If the SQL file doesn't create the database first:

```sql
CREATE DATABASE IF NOT EXISTS borrowers_log;
USE borrowers_log;
```

Then run the rest of the SQL from `database.sql`

## After Setup

Verify the database was created:

```sql
SHOW DATABASES;
USE borrowers_log;
SHOW TABLES;
```

You should see:
- users
- inventory  
- borrowers

## Troubleshooting

### "Access denied" Error
- Check username is `root`
- Check password is correct
- Try without password: `mysql -u root` (if password not set)

### "Can't connect to server"
- Make sure MariaDB/MySQL service is running
- Check Services: Win+R → services.msc → Find MySQL/MariaDB → Start

### "Unknown database"
- Run the CREATE DATABASE statement first
- Or run entire `database.sql` file

## Next Steps

After database is set up:

1. Update `backend/.env` with your database credentials
2. Start backend: `cd backend && npm start`
3. Run Flutter app: `cd borrowers_log_system && flutter run -d chrome`

## Quick Alternative

If you prefer a GUI tool, download:
- **HeidiSQL**: https://www.heidisql.com/download.php
- **MySQL Workbench**: https://dev.mysql.com/downloads/workbench/

Both make database setup much easier on Windows!

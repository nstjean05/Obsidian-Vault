# Foodlink

## About
Foodlink is a website that helps collect and distribute food to people who need it. Volunteers help with pickup and delivery.

## Admin Login (Pre-set)
Use these details to login as admin:
- Email: admin@foodlink.com
- Password: Admin@1616

## Quick Start

### Prerequisites
- PHP 7.4 or higher
- MySQL 5.7 or higher

### Installation Steps

1. **Install PHP and MySQL**
   - **Windows**: Download and install PHP from [php.net](https://www.php.net/downloads) and MySQL from [mysql.com](https://dev.mysql.com/downloads/mysql/). Ensure PHP is added to your system PATH.
   - **Mac**: `brew install php mysql`
   - **Linux**: `sudo apt install php mysql-server` (Ubuntu/Debian) or equivalent for your distro.

2. **Start MySQL Service**
   - **Windows**: Open Command Prompt as Administrator and run `net start mysql` (service name may vary; check MySQL installation).
   - **Mac**: `brew services start mysql`
   - **Linux**: `sudo service mysql start` or `sudo systemctl start mysql`

3. **Setup Database**
   - Create the database: `mysql -u root -p -e "CREATE DATABASE foodlink;"`
   - Import the schema: `mysql -u root -p foodlink < foodlink.sql`
   - Note: Replace `root` with your MySQL username if different. You may be prompted for the password.

4. **Run the Website**
   - Navigate to the project directory: `cd Foodlink`
   - Start the PHP built-in server: `php -S localhost:8000`
   - Access the site at: `http://localhost:8000`
   - The entry point is `index.php`, which will load automatically.
5. **Enable Automatic Email sending (Shift reminders)**
   **Windows (XAMPP):**
      - Open Task scheduler
      - Create Basic task --> name: FoodLink Shift Reminders
      - Trigger: daily at your chosen time
      - Action: Start a program
         Program/Script: C:\xampp\php\php.exe
         Add arguments: "<full path to your project>\cron\shift_reminders.php"
            Examples: "C:\xampp\htdocs\Sprint_3\docs\cron\shift_reminders.php"
      - Start in: <full path to your project>\cron
         Example: C:\xampp\htdocs\Sprint_3\docs\cron
      - Click Finish --> Task is now active
   **Note: MySQL must be running for the script to work**
   **Auto-start MySQL on system boot**
      - Open XAMPP control panel
      - Click **config** (next to MySQL)
      - Select **Service and Port Settings**
      - Check the box **"Install MySql as a service"**
      - Restart XAMPP
   MySQL will now automatically start every time the computer turns on

   **Mac only(Enable Automatic Emails via cron)**
      - Find your PHP path: which php
      - Edit Cron: crontab -e
      - Add this rule (adjust your project path): 0 8 * * * /usr/bin/php "/Users/<username>/path/to/project/cron/shift_reminders.php"
      - Save and exit - Cron will now run the email reminders daily
    **Auto-start MySQL on system boot**
    **Mac(homebrew)**
      - Run: 'brew services start mysql'
    **Mac(MAMP)**
      - Open MAMP
      - Go to **Preferences --> Start/Stop**
      - Enable **"Start MySQL when starting MAMP"**

### Installation Option 2 - XAMPP

1. **Download XAMPP** from [apachefriends.org]
(https://www.apachefriends.org/)

2. **Install XAMPP** (just click Next, Next, Next)

3. **Start XAMPP** and click "Start" for Apache & MySQL

4. **Place files** in: `C:/xampp/htdocs/Foodlink/`

5. **Create database**: 
   - Go to `http://localhost/phpmyadmin`
   - Click "New" → Name: `foodlink` → Create
   - Click "Import" → Choose `foodlink.sql` → Go
   
6. **Access website**: `http://localhost/Foodlink/`

## Users
1. Admin
   - Manages users
   - Approves registrations
   - Views reports

2. Clients
   - Request food
   - Get QR codes
   - Check pickup history

3. Volunteers
   - Set available times
   - Handle pickups
   - Manage schedule

## Remember
- Keep admin login details safe
- Always logout when done
- Check for new registrations regularly
The project layout in this repository is:

```
Foodlink/
├── db_connect.php
├── hash_password.php
├── index.php
├── login.php
├── logout.php
├── register.php
├── admin/
│   ├── clients.php
│   ├── dashboard.php
│   ├── locations.php
│   ├── login.php
│   ├── pending_registrations.php
│   ├── reports.php
│   ├── unflag_client.php
│   └── volunteers.php
│   └── forgot_password.php
│   └── reset_password.php      
├── client/
│   ├── client_dashboard.php
│   ├── dashboard.php
│   ├── food_pickup.php
│   ├── pickup_history.php
│   ├── profile.php
│   ├── qr_code.php
│   └── schedule.php
│   └── forgot_password.php
│   └── reset_password.php
├── includes/
│   ├── admin_nav.php
│   ├── client_nav.php
│   ├── footer.php
│   ├── functions.php
│   ├── db_connect.php
│   ├── header.php
│   └── volunteer_nav.php
│   └── email_sender.php
├── volunteer/
│   ├── availability.php
│   ├── dashboard.php
│   ├── login.php
│   ├── pickup_shifts.php
│   ├── register.php
│   ├── schedule.php
│   └── volunteer_dashboard.php
│   └── forgot_password.php
│   └── reset_password.php
├── phpmailer/
│   ├── PHPMailer.php
│   ├── SMTP.php
│   └── Exception.php
├── cron/
│   └── shift_reminders.php
```

## Roles & Permissions

- Client: register, check application status, view QR code, view pickup history, update profile.
- Volunteer: sign in, scan client QR codes, view schedule and today's pickups.
- Admin: approve/reject registrations, manage clients/volunteers/locations, view reports.

Note: Clients and volunteers can only log in after an admin approves their registration.

## Tech stack & implementation notes

- Backend: PHP (7.4+ recommended)
- Database: MySQL
- Server: Apache (via XAMPP for local development)
- Frontend: HTML/CSS/JavaScript (Bootstrap commonly used in UI pages)

Key files and responsibilities:
- `db_connect.php` — database connection parameters used throughout the app.
- `includes/functions.php` — common helper functions and app-wide constants (toggle DEBUG_MODE here if present).
- `admin/`, `client/`, `volunteer/` — role-specific pages and flows.
- `client/qr_code.php` — QR generation for client pickups (requires GD or similar in PHP).

## Reports & Business Rules

Typical reports and business rules implemented or expected:
- Missed pickups report (no-show tracking)
- new registrations over time
- Location / distribution performance

Example business rules used by many food bank workflows (please confirm in your app code):
- Clients are allowed one pickup per week.
- 2 consecutive no-shows = flag; 3+ no-shows = temporary suspension (often 30 days).

## Configuration

- Edit `db_connect.php` to set DB credentials.
- If QR generation is used, ensure PHP's GD extension is enabled (check `php.ini`).
- Optionally enable a DEBUG flag in `includes/functions.php` if present:
```php
define('DEBUG_MODE', true);
```

## Troubleshooting

Common issues and places to check:
- "Not Found" or 404: verify project placed inside `htdocs` and URL path is correct.
- Database connection errors: check MySQL is running and `db_connect.php` credentials are correct.
- Session or login problems: check PHP session configuration and that pages call `session_start()` before output.
- QR code generation: ensure the GD PHP extension is enabled and proper file permissions are set if images are saved to disk.

## Tests & verification (manual)

1. Start Apache and MySQL via XAMPP Control Panel.
2. Visit `http://localhost/Foodlink/` and confirm the site loads.
3. Try admin login at `admin/login.php` (default credentials may not be present; use your seeded admin account).
4. Register a test client using `register.php` and verify the admin pending registrations page.
5. Note: Clients and volunteers cannot log in until an admin approves them on the pending registrations page.

## Future enhancements

- Email notifications for approvals.
- SMS or email reminders for upcoming pickup windows.
- QR Code Scanning and improvememts.
- Submit documents through secured channel.
- Volunteer interface to scan client QR codes and record pickups.
- REST API endpoints for mobile apps: `/api/clients`, `/api/pickups`, `/api/reports`.

## Development

- Course: CMPT 385 - Introduction to Software Engineering
- Semester: Fall 2025
- Institution: Trinity Western University

## License
This project was developed for academic purposes (CMPT 385).

---

**Last Updated:** December 2nd, 2025
**Version:** 1.2

<div align="center">

# 🏋️‍♂️ Gym Fitness Record Management System

### A lightweight, admin-first gym management platform — members, attendance, workouts, and billing  
Fast • Secure • Easy to self-host

[![Stars](https://img.shields.io/github/stars/DhanushGroot/Gym_Fitness_Record_Management_System?style=for-the-badge&logo=github)](https://github.com/DhanushGroot/Gym_Fitness_Record_Management_System/stargazers)
[![Version](https://img.shields.io/badge/version-1.0.0-blue?style=for-the-badge)](./)
[![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)](LICENSE)
[![Build](https://img.shields.io/badge/build-passing-brightgreen?style=for-the-badge)](https://github.com/DhanushGroot/Gym_Fitness_Record_Management_System/actions)

</div>

---

## ✨ Demo / Preview

<div align="center">

**Live demo / quick preview**

![App Demo](/assets/demo.gif)

</div>

---

## 🚀 What it does

Gym Fitness Record Management System is an easy-to-deploy web app for small gyms and studios. It centralizes member profiles, attendance tracking, workout plans, and simple billing—designed for operators who want reliability without complexity.

- Member onboarding & profile history
- Attendance check-in / check-out logs
- Workout templates, session logging & progress notes
- Invoice generation and printable receipts
- Role-based access: Admin, Trainer, Reception

---

## ⚡ Key Features

- ✅ Member CRUD with progress timelines  
- ✅ Attendance register (timestamped, exportable CSV)  
- ✅ Workout plan templates & session tracking  
- ✅ Invoice generation & printable receipts (PDF-friendly HTML)  
- ✅ Responsive HTML/CSS UI with minimal JS for speed  
- ✅ Lightweight PHP backend — easy to host on LAMP stacks

---

## 🛠️ Tech Stack

| Category | Technology |
|---:|:---|
| Frontend | HTML5, CSS3, Minimal JavaScript |
| Backend | PHP (procedural / lightweight MVC) |
| Database | MySQL / MariaDB |
| Styling | Custom CSS (responsive) |
| Hosting | Apache / Nginx (PHP-FPM) |
| Tooling | git, MySQL client |

---

## ⚙️ Architecture / How it works

```
Gym_Fitness_Record_Management_System
├── public/                  → Document root (index.php, assets, uploads)
│   ├── index.php
│   ├── assets/
│   │   ├── css/
│   │   └── demo.gif
│   └── uploads/             → member images, attachments
├── src/                     → app controllers & helpers
├── includes/                → config, DB connection, shared helpers
│   └── config.php
├── sql/
│   └── schema.sql
└── scripts/                 → utilities (migrations, exports)
```

Data flow: Browser ↔ public/index.php → Router/Controller → Model (MySQL) → View → Browser

<details>
<summary>🔎 Component responsibilities</summary>

- public/index.php — entrypoint, routing to modules (members, attendance, billing)  
- includes/config.php — DB & app settings (do NOT commit secrets)  
- src/controllers/ — request handling, validation, business logic  
- src/models/ — DB access helpers / prepared statements (PDO recommended)  
- assets/ — CSS, images, demo assets  
- sql/schema.sql — initial DB schema & seed examples

</details>

---

## 📦 Installation (minimal)

Prerequisites: PHP 7.4+, MySQL/MariaDB, web server (Apache/Nginx) or PHP built-in server for testing.

1. Clone
```bash
git clone https://github.com/DhanushGroot/Gym_Fitness_Record_Management_System.git
cd Gym_Fitness_Record_Management_System
```

2. Configure
```bash
cp includes/config.sample.php includes/config.php
# Edit includes/config.php with DB credentials and base_url
```

3. Initialize database
```bash
mysql -u root -p
CREATE DATABASE gym_db;
exit
mysql -u root -p gym_db < sql/schema.sql
```

4. Serve (quick test)
```bash
# Option A: PHP built-in server (dev only)
php -S 0.0.0.0:8080 -t public

# Option B: Deploy to Apache/Nginx and point document root to `public/`
```

Open: http://localhost:8080

---

## 💻 Usage

- Add members: Reception → New Member (name, contact, DOB, membership)
- Check-in: Attendance → Scan / Manual check-in
- Log session: Trainer → Assign workout template → Record session notes
- Billing: Reception/Admin → Generate invoice → Print or save PDF

Example: Add member via curl (dev API)
```bash
curl -X POST http://localhost:8080/members/create.php \
  -F "first_name=John" -F "last_name=Doe" -F "phone=9999999999"
```

Database connection (example, includes/db.php)
```php
<?php
$dsn = "mysql:host={$DB_HOST};dbname={$DB_NAME};charset=utf8mb4";
$pdo = new PDO($dsn, $DB_USER, $DB_PASS, [
  PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION,
  PDO::ATTR_EMULATE_PREPARES => false,
]);
```

---

## 🎛️ Configuration

Edit includes/config.php:
```php
<?php
return [
  'db' => [
    'host' => '127.0.0.1',
    'name' => 'gym_db',
    'user' => 'gym_user',
    'pass' => 'secret',
  ],
  'app' => [
    'base_url' => 'http://localhost:8080'
  ],
];
```

Security notes:
- Never commit real credentials. Use environment-specific config.
- Sanitize inputs and use prepared statements (PDO) for DB queries.

---

## 🗺️ Roadmap

- [x] Member management & attendance logging  
- [x] Workout templates & session tracking  
- [x] Billing & printable invoice receipts  
- [ ] SMS/email reminders for renewals & classes  
- [ ] Trainer performance analytics & leaderboards  
- [ ] Mobile-first UI improvements & accessibility  
- [ ] Role-based access refinement & audit logs

---

## 🤝 Contributing

We welcome focused contributions.

1. Fork the repository  
2. Create a branch: git checkout -b feat/your-feature  
3. Implement & test locally  
4. Commit with a clear message and open a PR

Guidelines:
- Include SQL migrations for schema changes
- Keep UI changes modular and responsive
- Add tests or manual QA steps for critical flows (billing, attendance)

---

## 📈 Stats & Visitor Counter

<div align="center">

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=DhanushGroot&repo=Gym_Fitness_Record_Management_System&show_icons=true&theme=dark&hide_border=true)
![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=DhanushGroot&repo=Gym_Fitness_Record_Management_System&layout=compact&theme=dark&hide_border=true)

<br />

![GitHub Streak](https://github-readme-streak-stats.herokuapp.com/?user=DhanushGroot&theme=dark&hide_border=true)
![Profile Views](https://komarev.com/ghpvc/?username=DhanushGroot&color=49c5b6)

</div>

---

## 📝 License

MIT — see LICENSE for full text.

---

Made with clarity and performance in mind — Gym Fitness Record Management System © DhanushGroot  
*Last updated: 2026-04-22*

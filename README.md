<p align="center">
  <img src="public/img/logo.png" alt="Zingames Logo" width="180" />
</p>

<h1 align="center">🎮 Zingames</h1>

<p align="center">
  <b>A modern Laravel-based web app for managing and playing games, with a powerful admin panel.</b><br>
  <a href="#table-of-contents">Table of Contents</a> • <a href="#features">Features</a> • <a href="#installation">Installation</a> • <a href="#usage">Usage</a> • <a href="#screenshots">Screenshots</a> • <a href="#api-documentation">API</a> • <a href="#contributing">Contributing</a>
</p>

---

## 🗂️ Table of Contents
- [🗂️ Table of Contents](#️-table-of-contents)
- [📝 About](#-about)
- [🚀 Features](#-features)
- [🖥️ Tech Stack](#️-tech-stack)
- [🏗️ Architecture](#️-architecture)
- [📁 Folder Structure](#-folder-structure)
- [⚙️ Installation](#️-installation)
  - [1. Clone the repository](#1-clone-the-repository)
  - [2. Install dependencies](#2-install-dependencies)
  - [3. Environment setup](#3-environment-setup)
- [🌱 Environment Setup](#-environment-setup)
- [🗄️ Database Setup](#️-database-setup)
- [🔑 Admin Logins](#-admin-logins)
- [💡 Usage](#-usage)
- [📸 Screenshots](#-screenshots)
- [📚 API Documentation](#-api-documentation)
  - [Get All Games](#get-all-games)
  - [Create a New Game](#create-a-new-game)
- [❓ FAQ](#-faq)
- [🔒 Security](#-security)
- [🤝 Contributing](#-contributing)
- [📝 Changelog](#-changelog)
- [🙏 Credits](#-credits)
- [📄 License](#-license)
- [📬 Contact](#-contact)

---

## 📝 About
Zingames is a robust, scalable, and modern web application built with Laravel. It provides a feature-rich admin panel for managing games, categories, and users, with advanced security and role-based access control. Perfect for game libraries, educational platforms, or any project needing user and content management.

---

## 🚀 Features
- 🎛️ **Admin Panel**: Manage users, games, categories, and messages
- 👥 **User Management**: Add, edit, lock/unlock, and assign roles
- 🕹️ **Game Management**: CRUD for games and categories
- 🔒 **Secure Authentication**: Admin & super admin roles, account lockout, 2FA ready
- 🛡️ **Role & Permission System**: Fine-grained access control
- 📊 **Dashboard**: Stats, recent activity, and quick actions
- 📧 **Email Notifications**: For sub-admin creation and security events
- 🗄️ **Database Migrations & Seeding**: Easy setup and test data
- 🌐 **Responsive UI**: Works on desktop and mobile
- 📝 **Extensive Documentation**: For easy onboarding

---

## 🖥️ Tech Stack
- [Laravel](https://laravel.com/) (PHP)
- [MySQL](https://www.mysql.com/)
- [Blade](https://laravel.com/docs/10.x/blade) (views)
- [Bootstrap](https://getbootstrap.com/) (UI)
- [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [Composer](https://getcomposer.org/)
- [NPM](https://www.npmjs.com/)

---

## 🏗️ Architecture
```mermaid
graph TD;
  A[User] -->|Login| B[Auth Controller]
  B --> C{Role Check}
  C -- Admin --> D[Admin Dashboard]
  C -- User --> E[Game Library]
  D --> F[Game CRUD]
  D --> G[Category CRUD]
  D --> H[User Management]
  D --> I[Settings]
  F --> J[(Database)]
  G --> J
  H --> J
  E --> J
```

---

## 📁 Folder Structure
```text
zingames/
├── app/
│   ├── Console/
│   ├── Exceptions/
│   ├── Http/
│   │   ├── Controllers/
│   │   ├── Middleware/
│   ├── Models/
├── bootstrap/
├── config/
├── database/
│   ├── factories/
│   ├── migrations/
│   ├── seeders/
├── public/
│   ├── img/
│   ├── index.php
├── resources/
│   ├── views/
│   ├── js/
│   ├── css/
├── routes/
├── storage/
├── tests/
├── .env.example
├── composer.json
├── package.json
├── README.md
```

---

## ⚙️ Installation

### 1. Clone the repository
```bash
git clone https://github.com/yourusername/zingames.git
cd zingames
```

### 2. Install dependencies
```bash
composer install
npm install
```

### 3. Environment setup
- Copy `.env.example` to `.env` and update your DB credentials:
```bash
cp .env.example .env
```
- Generate app key:
```bash
php artisan key:generate
```

---

## 🌱 Environment Setup
Example `.env` variables:
```env
APP_NAME=Zingames
APP_ENV=local
APP_KEY=base64:...
APP_DEBUG=true
APP_URL=http://localhost
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=zingames
DB_USERNAME=root
DB_PASSWORD=yourpassword
```

---

## 🗄️ Database Setup
- Create a MySQL database (e.g., `zingames`)
- Run migrations:
```bash
php artisan migrate
```
- Seed admin users:
```bash
php artisan db:seed --class=AdminUserSeeder
```

---

## 🔑 Admin Logins
| Name      | Email                     | Password     | Role        |
|-----------|--------------------------|--------------|-------------|
| Admin     | sauravpatil212@gmail.com | zingames21   | super_admin |
| Sub Admin | subadmin@zingames.com    | subadmin123  | admin       |
| Mayur P   | Work.mayurp@gmail.com    | Work.mayurp  | admin       |

> ⚠️ **Change passwords after first login for security!**

---

## 💡 Usage
- Start the server:
  ```bash
  php artisan serve
  ```
- Visit [http://localhost:8000](http://localhost:8000)
- Admin panel: `/admin/dashboard` (login required)
- Manage games, categories, users, and messages from the admin panel

---

## 📸 Screenshots
> _Add your app screenshots here for a better showcase!_

<p align="center">
  <img src="public/img/logo.png" alt="Zingames Screenshot" width="320" />
  <!-- <img src="public/img/screenshot1.png" width="320" /> -->
</p>

---

## 📚 API Documentation
> _If your project exposes APIs, document them here. Example below:_

### Get All Games
```http
GET /api/games
```
**Response:**
```json
[
  { "id": 1, "name": "Chess", "category": "Board" },
  { "id": 2, "name": "Sudoku", "category": "Puzzle" }
]
```

### Create a New Game
```http
POST /api/games
```
**Body:**
```json
{
  "name": "Ludo",
  "category_id": 3
}
```

---

## ❓ FAQ
**Q: How do I reset an admin password?**
> Use the password reset feature on the login page or update via tinker.

**Q: How do I add more permissions?**
> Update the `permissions` array in the user model or via the admin panel.

**Q: Can I deploy this on shared hosting?**
> Yes, just make sure PHP, Composer, and MySQL are available.

---

## 🔒 Security
- All passwords are hashed using bcrypt
- Account lockout after multiple failed attempts
- Role-based access control
- Regularly update dependencies for security

---

## 🤝 Contributing
1. Fork the repository
2. Create your feature branch (`git checkout -b feature/YourFeature`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/YourFeature`)
5. Open a Pull Request

**Code Style:**
- Follow PSR-12 for PHP
- Use meaningful commit messages
- Write tests for new features

---

## 📝 Changelog
- **v1.0.0** - Initial release
- _Add your changes here_

---

## 🙏 Credits
- [Laravel](https://laravel.com/)
- [Bootstrap](https://getbootstrap.com/)
- [FontAwesome](https://fontawesome.com/)
- All contributors and testers

---

## 📄 License
[MIT](LICENSE)

---

## 📬 Contact
- Project Maintainer: [Your Name](mailto:your.email@example.com)
- For support, open an issue or contact the repository owner.

---

<p align="center"><i>Project maintained by your team. For support, contact the repository owner.</i></p>

<!-- Badges -->
<p align="center">
  <img src="https://img.shields.io/badge/build-passing-brightgreen" alt="Build Status" />
  <img src="https://img.shields.io/badge/license-MIT-blue" alt="License" />
  <img src="https://img.shields.io/badge/PRs-welcome-green" alt="PRs Welcome" />
  <img src="https://img.shields.io/badge/status-active-success" alt="Project Status" />
</p>

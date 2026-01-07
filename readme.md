🎬 Theater Management System
(Admin & Owner Based Management Application)

📌 1. Project Overview (Simple Language)

Theater Management System ek application hai jo theater business ko digitally manage karne ke liye banaya gaya hai.

👥 System Roles
| Role              | Description                                              |
| ----------------- | -------------------------------------------------------- |
| **Admin**         | System ka super user (full control)                      |
| **Theater Owner** | Apna theater, screens, movies aur shows manage karta hai |


🔄 System ka Flow
Admin → Theater Owners create karta hai
Owner → Apne theaters (branches), screens, movies aur shows manage karta hai

👉 Ye system role-based access control follow karta hai.

🗂 2. Database Entities (Tables)
📦 Main Tables List
admins
owners
branches (theaters)
screens
seat_categories
movies
shows


📋 3. Table Structure (Database Design)
| Field    | Type        |
| -------- | ----------- |
| id       | Primary Key |
| name     | String      |
| email    | String      |
| password | String      |
📌 System ke liye hota hai (normally 1 admin)


👤 owners
| Field    | Type              |
| -------- | ----------------- |
| id       | Primary Key       |
| name     | String            |
| email    | String            |
| mobile   | String            |
| password | String            |
| status   | Active / Deactive |
📌 Admin create karega


🏢 branches (theaters)
| Field         | Type        |
| ------------- | ----------- |
| id            | Primary Key |
| owner_id      | Foreign Key |
| theater_name  | String      |
| total_screens | Number      |
| map_url       | String      |
| address       | Text        |
| city          | String      |
📌 Owner create karega


🎥 screens
| Field       | Type        |
| ----------- | ----------- |
| id          | Primary Key |
| branch_id   | Foreign Key |
| screen_name | String      |
| total_seats | Number      |
📌 Owner create karega


💺 seat_categories
| Field         | Type                    |
| ------------- | ----------------------- |
| id            | Primary Key             |
| screen_id     | Foreign Key             |
| category_name | Premium / Regular / Box |
| seat_count    | Number                  |
⚠️ Validation Rule
➡️ All seat categories ka total = screens.total_seats


🎬 movies
| Field      | Type        |
| ---------- | ----------- |
| id         | Primary Key |
| movie_name | String      |
| poster     | Image       |
| branch_id  | Foreign Key |
| screen_id  | Foreign Key |
📌 Owner assign karega


⏰ shows
| Field     | Type        |
| --------- | ----------- |
| id        | Primary Key |
| movie_id  | Foreign Key |
| screen_id | Foreign Key |
| show_time | Time        |
| show_date | Date        |
📌 Owner manage karega


🔌 4. API Design (Beginner Friendly)

🔐 Authentication APIs
| Endpoint           | Method | Purpose     | Access |
| ------------------ | ------ | ----------- | ------ |
| `/api/admin/login` | POST   | Admin login | Admin  |
| `/api/owner/login` | POST   | Owner login | Owner  |


👤 Owner Management (Admin)
| Endpoint          | Method | Purpose          |
| ----------------- | ------ | ---------------- |
| `/api/owners`     | POST   | Add owner        |
| `/api/owners`     | GET    | List owners      |
| `/api/owners/:id` | PUT    | Edit owner       |
| `/api/owners/:id` | DELETE | Deactivate owner |


🏢 Branch (Theater)
| Endpoint            | Method | Purpose       |
| ------------------- | ------ | ------------- |
| `/api/branches`     | POST   | Add branch    |
| `/api/branches`     | GET    | List branches |
| `/api/branches/:id` | PUT    | Edit branch   |
| `/api/branches/:id` | DELETE | Delete branch |


🎥 Screens & Seats
| Endpoint               | Method | Purpose             |
| ---------------------- | ------ | ------------------- |
| `/api/screens`         | POST   | Add screen          |
| `/api/screens`         | GET    | List screens        |
| `/api/seat-categories` | POST   | Add seat categories |


🎬 Movies & Shows
| Endpoint         | Method | Purpose          |
| ---------------- | ------ | ---------------- |
| `/api/movies`    | POST   | Assign movie     |
| `/api/shows`     | POST   | Add show timings |
| `/api/shows`     | GET    | View shows       |
| `/api/shows/:id` | PUT    | Update show      |
| `/api/shows/:id` | DELETE | Stop/remove show |


🖥 5. Frontend Screens & Flow
🔑 Admin Screens
Admin Login
Admin Dashboard
Owner List
Add / Edit Owner

Flow:
Login → Dashboard → Manage Owners


⚙️ 6. Backend Responsibilities
Backend system handle karega:
Authentication (Admin / Owner)
Role-based access control
Seat count validation
Auto password generation
Email sending
Database operations
Secure REST APIs


👥 7. Who Creates What?
| Role  | Responsibility         |
| ----- | ---------------------- |
| Admin | Create & manage Owners |
| Owner | Create Branches        |
| Owner | Create Screens         |
| Owner | Create Seat Categories |
| Owner | Assign Movies          |
| Owner | Manage Shows           |


🔐 Access Control
| Role  | Access Level           |
| ----- | ---------------------- |
| Admin | All owners data        |
| Owner | Sirf apna data         |
| Owner | Dusre owners ka data ❌ |


📝 8. Frontend Forms Count

Admin Forms (2)
Admin Login Form
Add / Edit Owner Form

Owner Forms (5)
Owner Login Form
Add Branch Form
Add Screen Form
Seat Category Form
Add Movie & Show Form

✅ Total Forms = 7
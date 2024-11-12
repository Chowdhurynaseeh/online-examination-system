# Online Examination System

This project is a basic **Online Examination System** built with PHP, MySQL, HTML, and CSS. It allows an administrator to create and manage exams and users to take those exams. This system is intended as a foundational project for learning web development concepts, and it can be expanded with additional features as needed.

## Features
- **Admin Panel**: Allows the admin to create, update, delete exams and questions.
- **User Dashboard**: Enables users to log in, take exams, and review results.
- **Question Management**: Supports multiple-choice questions.
- **Result Calculation**: Automatic grading upon exam completion.

## Requirements
- **PHP** >= 7.4
- **MySQL** >= 5.7
- **Apache** Web Server (or any compatible PHP server)
- **Composer** (optional, if using dependencies)

## Getting Started

### 1. Clone the Repository
```bash
git clone [https://github.com/your-username/online-exam-system.git](https://github.com/Chowdhurynaseeh/online-examination-system)
cd online-examination-system ```

### 2. Configure the Database
Create a MySQL database. You can name it online_exam_system.
Import the database.sql file in the sql/ directory to create tables.
Update the database configuration in config.php with your MySQL credentials.


### 3. Run the Project
Start your local server (e.g., Apache or XAMPP).
Place the project folder in the server's root directory (e.g., htdocs for XAMPP).
Open your web browser and navigate to http://localhost/online-examination-system.

### 4. Default Admin Account
Username: admin
Password: admin123
You can change the default admin credentials directly in the users table in the database.

## Project Structure
online-exam-system/
├── config.php            # Database connection configuration
├── index.php             # Home page with login and signup
├── admin/
│   ├── dashboard.php     # Admin dashboard for managing exams
│   ├── add_exam.php      # Form to add a new exam
│   ├── add_question.php  # Form to add questions to exams
├── user/
│   ├── dashboard.php     # User dashboard to view available exams
│   ├── take_exam.php     # Exam interface for users
│   ├── results.php       # Shows exam results for users
├── assets/               # CSS, JavaScript, and images
└── sql/
    └── database.sql      # SQL file to create the initial database and tables

## Database Schema

### `users` Table
Stores user data with the following columns:
- `id`: Primary key
- `username`: Unique username for login
- `password`: Hashed password
- `role`: `admin` or `user` to differentiate permissions

### `exams` Table
Stores exam data with the following columns:
- `id`: Primary key
- `title`: Title of the exam
- `description`: Description of the exam
- `created_at`: Timestamp of exam creation

### `questions` Table
Stores questions for each exam with the following columns:
- `id`: Primary key
- `exam_id`: Foreign key linked to `exams` table
- `question`: The question text
- `option_a`, `option_b`, `option_c`, `option_d`: Multiple-choice options
- `correct_option`: Specifies the correct option for grading

### `results` Table
Stores user exam results with the following columns:
- `id`: Primary key
- `user_id`: Foreign key linked to `users` table
- `exam_id`: Foreign key linked to `exams` table
- `score`: User’s score in the exam

## Usage
1. **Admin Login**: Log in as an admin to create exams and add questions.
2. **User Registration/Login**: Users can register or log in to view and take exams.
3. **Take Exam**: Users can select an exam, answer questions, and submit.
4. **View Results**: Upon completion, users can view their score, and the admin can view all users' scores.

## Security Considerations
- **Password Hashing**: Make sure to hash user passwords in production (use `password_hash()` in PHP).
- **SQL Injection**: Use prepared statements for all SQL queries to prevent SQL injection.
- **Session Management**: Ensure sessions are managed securely to protect user data.

## Future Enhancements
- Add user role management (e.g., for moderators).
- Allow admins to upload images for questions.
- Improve the UI with more advanced CSS and JavaScript.
- Implement time limits for exams.
- Add a feedback system for exam reviews.

### Change These : 
// config.php
<?php
define('DB_SERVER', 'localhost');
define('DB_USERNAME', 'your_username');
define('DB_PASSWORD', 'your_password');
define('DB_DATABASE', 'online_exam_system');
$conn = new mysqli(DB_SERVER, DB_USERNAME, DB_PASSWORD, DB_DATABASE);
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}
?>

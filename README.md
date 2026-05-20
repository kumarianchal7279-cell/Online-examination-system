# 🚀 Online Exam System – Java (Spring Boot)

<p align="center">
<img src="https://img.shields.io/badge/Java-17-blue?style=for-the-badge&logo=java&logoColor=white" alt="Java 17">
<img src="https://img.shields.io/badge/Spring%20Boot-3.x-brightgreen?style=for-the-badge&logo=springboot&logoColor=white" alt="Spring Boot 3.x">
<img src="https://img.shields.io/badge/JPA%20%2F%20Hibernate-red?style=for-the-badge" alt="JPA / Hibernate">
<img src="https://img.shields.io/badge/H2%20Database-lightgrey?style=for-the-badge" alt="H2 Database">
</p>

A comprehensive **Online Examination System** built using **Spring Boot, Spring Security, Thymeleaf, Bootstrap 5**, and **JPA/Hibernate**.  
The platform provides a secure and user-friendly environment for **Admins** and **Students** to manage and take online tests effectively.

✔️ Completely Free  
✔️ Full Source Code Included  
✔️ Easy Setup & Deployment

---

## 📑 Table of Contents
- [Quick Start](#-quick-start-5-minutes)
- [Screenshots](#-screenshots)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Prerequisites](#-prerequisites)
- [Installation & Setup](#-installation--setup)
- [Configuration](#-configuration)
- [Running the Application](#-running-the-application)
- [Default Credentials](#-default-credentials)
- [Project Structure](#-project-structure)
- [Troubleshooting](#-troubleshooting)
- [License](#-license)
- [Usage Guide](#-usage-guide)
- [Support & Contact](#-support--contact)

---

## ⚡ Quick Start (5 Minutes)

```bash
# 1. Clone the repository
git clone https://github.com/sumitkumar1503/online-exam-system.git
cd online-exam-system

# 2. Install dependencies
mvn clean install

# 3. Run the application
mvn spring-boot:run

# 4. Open browser and visit
# http://localhost:7890

# 5. Login with default admin credentials
# Username: admin
# Password: adminpass
```

---

#  Screenshots


<table width="100%">


<tr>
<td align="center"><b>Exam Page (with Pagination)</b></td>
</tr>
<tr>
<td align="center"><img src="https://github.com/sumitkumar1503/online-exam-system/blob/master/screenshots/exampage.png" width="90%"></td>
</tr>

<tr>
<td align="center"><b>Admin Dashboard</b></td>
</tr>
<tr>
<td align="center"><img src="https://github.com/sumitkumar1503/online-exam-system/blob/master/screenshots/admindashboard.png?raw=true" width="90%"></td>
</tr>

<tr>
<td align="center"><b>Manage Exam</b></td>
</tr>
<tr>
<td align="center"><img src="https://github.com/sumitkumar1503/online-exam-system/blob/master/screenshots/adminmanageexam.png" width="90%"></td>
</tr>

<tr>
<td align="center"><b>Manage Question</b></td>
</tr>
<tr>
<td align="center"><img src="https://github.com/sumitkumar1503/online-exam-system/blob/master/screenshots/adminmanagequestion.png" width="90%"></td>
</tr>
</table>

---

# ✨ Features

## 👨‍💻 Admin Features
- Secure Admin Login
- Stats Dashboard (Total Students, Exams, Questions, Submissions)
- **Exam CRUD** (title, duration, description)
- **Question CRUD** per exam
- Cascade deletes for exams → questions → results
- Protect answered questions from accidental delete
- Manage Students
- Reset Student Password
- Delete Student Account (cascade all related data)
- View all submissions for any exam

---

## 🧑‍🎓 Student Features
- Student Registration (Full Name, Email, Mobile, Profile Picture)
- Secure Login
- Dashboard with KPIs + Performance Chart
- Take Exam (paginated interface + question palette)
- Live Timer (auto submit)
- Instant Results (score, percentage, pass/fail)
- Detailed Review Page (correct vs incorrect answers)
- Profile Update
- Upload New Profile Picture
- Change Password
- View All Previous Exam Results

---

# 🛠️ Tech Stack

| Layer | Technology                                 |
|------|--------------------------------------------|
| Backend | Spring Boot 3, Spring Security 6           |
| Frontend | Thymeleaf, Html, Bootstrap 5, Chart.js     |
| Database | H2 (file-based) (configurable to other DB) |
| ORM | Hibernate / JPA                            |
| Build | Maven                                      |
| Storage | Local File System for images               |

---

# � Prerequisites

Before you begin, ensure you have the following installed on your system:

| Requirement | Version | Download |
|------------|---------|----------|
| Java | 17 or higher | [Download Java](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html) |
| Maven | 3.6+ | [Download Maven](https://maven.apache.org/download.cgi) |
| Git | Latest | [Download Git](https://git-scm.com/download) |
| IDE (Optional) | IntelliJ / VS Code / Eclipse | [Download IDE](https://www.jetbrains.com/idea/download/) |

### Verify Installation

```bash
# Check Java version
java -version

# Check Maven version
mvn -version

# Check Git version
git --version
```

---

# 🔧 Installation & Setup

## Step 1: Clone the Repository

```bash
git clone https://github.com/sumitkumar1503/online-exam-system.git
cd online-exam-system
```

## Step 2: Install Maven Dependencies

Navigate to the project directory and run:

```bash
mvn clean install
```

This command will:
- Download all required dependencies
- Compile the project
- Create the target folder

## Step 3: Configure Application Properties

The `application.properties` file is located at:
```
src/main/resources/application.properties
```

Key configurations to verify/update:

```properties
# Server Configuration
server.port=7890

# Database Configuration (H2)
spring.datasource.url=jdbc:h2:file:./data/examdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=password

# JPA/Hibernate Configuration
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
spring.jpa.hibernate.ddl-auto=update

# H2 Console
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console

# Thymeleaf Configuration
spring.thymeleaf.prefix=classpath:/templates/
spring.thymeleaf.suffix=.html

# File Upload Configuration
file.upload-dir=uploads/
```

## Step 4: Create Required Directories

Create the following directories in the project root:

```bash
# Windows
mkdir data
mkdir uploads

# Linux/Mac
mkdir -p data uploads
```

These directories are used for:
- **data/**: H2 database storage
- **uploads/**: Student profile picture uploads

## Step 5: Build the Project

```bash
mvn clean install
```

---

# 🚀 Running the Application

### Option 1: Run from IDE

1. Open the project in your IDE (IntelliJ, VS Code, or Eclipse)
2. Navigate to: `src/main/java/com/example/exam/OnlineExamApplication.java`
3. Right-click → Run `OnlineExamApplication.main()`
4. Wait for the server to start

### Option 2: Run from Terminal

```bash
mvn spring-boot:run
```

### Option 3: Run from JAR File

```bash
# First, build the project
mvn clean package

# Then run the JAR
java -jar target/online-exam-0.0.1-SNAPSHOT.jar
```

Once started, you'll see:
```
Started OnlineExamApplication in X seconds (JVM running for X.XXXs)
```

The application will be available at: **http://localhost:7890**

---

# ⚙️ Configuration

## Database Setup

The application uses **H2 Database** (file-based), which is automatically initialized on first run.

### Access H2 Console

After starting the application, visit:
```
http://localhost:7890/h2-console
```

Login credentials:
- **JDBC URL**: `jdbc:h2:file:./data/examdb`
- **Username**: `sa`
- **Password**: `password`

### Switching to Another Database (MySQL/PostgreSQL)

To use **MySQL** instead of H2:

1. Update `application.properties`:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/exam_db
spring.datasource.driverClassName=com.mysql.cj.jdbc.Driver
spring.datasource.username=root
spring.datasource.password=yourpassword
spring.jpa.database-platform=org.hibernate.dialect.MySQL8Dialect
spring.jpa.hibernate.ddl-auto=update
```

2. Add MySQL dependency to `pom.xml` (replace the H2 dependency):

```xml
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>8.0.33</version>
</dependency>
```

---

# 🔐 Default Credentials

### Admin Account

| Field | Value |
|-------|-------|
| **Username** | admin |
| **Password** | adminpass |

### Test Student Account (create new)

You can register a new student account using the registration page at:
```
http://localhost:7890/register
```

---

# 📁 Project Structure

```
online-exam-system/
├── src/
│   ├── main/
│   │   ├── java/com/example/exam/
│   │   │   ├── OnlineExamApplication.java          # Main Application Class
│   │   │   ├── config/                             # Configuration Classes
│   │   │   │   ├── SecurityConfig.java             # Spring Security Configuration
│   │   │   │   └── CustomAuthSuccessHandler.java   # Auth Success Handler
│   │   │   ├── controller/                         # REST Controllers
│   │   │   ├── model/                              # Entity Models (JPA)
│   │   │   ├── repository/                         # Data Access Layer
│   │   │   └── service/                            # Business Logic Layer
│   │   └── resources/
│   │       ├── application.properties              # App Configuration
│   │       ├── static/                             # CSS, JS, Images
│   │       │   └── js/exam-timer.js               # Exam Timer Logic
│   │       └── templates/                          # Thymeleaf Templates
│   │           ├── fragments.html                  # Reusable HTML fragments
│   │           ├── index.html
│   │           ├── login.html
│   │           ├── register.html
│   │           ├── admin/                          # Admin Pages
│   │           └── student/                        # Student Pages
│   └── test/                                       # Unit Tests
├── data/                                           # H2 Database (auto-created)
├── uploads/                                        # User Uploaded Files
├── pom.xml                                         # Maven Configuration
└── README.md                                       # Project Documentation
```

---

# 🐛 Troubleshooting

### Issue 1: Port 7890 Already in Use

**Error**: `Address already in use: bind`

**Solution**:
```bash
# Option 1: Change port in application.properties
server.port=8080

# Option 2: Kill the process using port 7890 (Windows)
netstat -ano | findstr :7890
taskkill /PID <PID> /F

# Option 2: Kill the process using port 7890 (Linux/Mac)
lsof -ti:7890 | xargs kill -9
```

### Issue 2: Maven Command Not Found

**Error**: `mvn: command not found` or `'mvn' is not recognized`

**Solution**:
1. Install Maven: [Download Maven](https://maven.apache.org/download.cgi)
2. Add Maven to PATH:
   - **Windows**: Add `C:\apache-maven-3.x.x\bin` to System Environment Variables
   - **Linux/Mac**: Add to `~/.bashrc` or `~/.zshrc`:
     ```bash
     export PATH=$PATH:/path/to/apache-maven-3.x.x/bin
     ```
3. Verify: `mvn -version`

### Issue 3: Java Version Mismatch

**Error**: `Unsupported class version` or `Java 17+ required`

**Solution**:
```bash
# Check your Java version
java -version

# If needed, install Java 17+
# Windows: Use installer from oracle.com
# Linux: sudo apt-get install openjdk-17-jdk
# Mac: brew install openjdk@17
```

### Issue 4: H2 Database Connection Failed

**Error**: `Could not get a connection from the pool`

**Solution**:
1. Ensure `data/` directory exists in project root
2. Check `application.properties` database URL is correct
3. Delete old database file: `data/examdb.mv.db`
4. Restart the application

### Issue 5: File Upload Not Working

**Error**: `Directory not found` or `Permission denied`

**Solution**:
1. Create `uploads/` directory in project root
2. Ensure proper permissions:
   ```bash
   # Linux/Mac
   chmod 755 uploads/
   
   # Windows: Right-click → Properties → Security → Edit
   ```

---

# 📜 License

This project is **open-source** under the **MIT License**.

Feel free to use, modify, and distribute this project for personal or commercial use.

---

# 📖 Usage Guide

## For Admin Users

1. **Login**: Visit http://localhost:7890/login with default credentials (admin/adminpass)
2. **Dashboard**: View statistics and KPIs
3. **Manage Exams**: 
   - Create new exams with title, duration, and description
   - Edit or delete existing exams
4. **Manage Questions**: 
   - Add multiple-choice questions to exams
   - Edit or delete questions
5. **Manage Students**: 
   - View all registered students
   - Reset student passwords if needed
   - Delete student accounts
6. **View Results**: Check exam submissions and student performance

## For Student Users

1. **Register**: Create account at http://localhost:7890/register
2. **Login**: Access your student dashboard
3. **Take Exam**: 
   - View available exams
   - Start an exam with live timer
   - Use question palette for navigation
4. **View Results**: 
   - See immediate results after submission
   - Review correct vs incorrect answers
   - Access all previous exam results
5. **Profile**: Update personal information and change password

---

# 💖 Support & Contact

This project is created by **LazyCoder**.

### 📺 Subscribe to YouTube Channel
https://www.youtube.com/c/LazyCoderOnline?sub_confirmation=1

### 📱 WhatsApp Support
https://wa.me/919572181024

---

<p align="center">
<strong>Happy Coding ❤️</strong>
</p>

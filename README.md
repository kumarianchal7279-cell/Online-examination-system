# Online Examination System

<p align="center">
<img src="https://img.shields.io/badge/Java-17-blue?style=for-the-badge&logo=java&logoColor=white" alt="Java 17">
<img src="https://img.shields.io/badge/Spring%20Boot-3.x-brightgreen?style=for-the-badge&logo=springboot&logoColor=white" alt="Spring Boot 3.x">
<img src="https://img.shields.io/badge/JPA%20%2F%20Hibernate-red?style=for-the-badge" alt="JPA / Hibernate">
<img src="https://img.shields.io/badge/H2%20Database-lightgrey?style=for-the-badge" alt="H2 Database">
</p>

## Overview

A robust and scalable **Online Examination Management System** built with enterprise-grade technologies. This application provides a comprehensive solution for educational institutions and organizations to manage exams, questions, and student assessments efficiently.

**Key Highlights:**
- Fully open-source with complete source code
- Production-ready architecture with Spring Boot 3
- Secure authentication and authorization
- Intuitive user interface for both administrators and students
- Real-time exam monitoring and result analysis

---

## Table of Contents

- [Quick Start](#quick-start)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [System Requirements](#system-requirements)
- [Installation](#installation)
- [Configuration](#configuration)
- [Running the Application](#running-the-application)
- [Database](#database)
- [Project Structure](#project-structure)
- [Usage Guide](#usage-guide)
- [Troubleshooting](#troubleshooting)
- [License](#license)
- [Support](#support)

---

## Quick Start

Get the application running in minutes:

```bash
# 1. Clone the repository
git clone https://github.com/kumarianchal7279-cell/Online-examination-system.git
cd Online-examination-system

# 2. Install dependencies
mvn clean install

# 3. Run the application
mvn spring-boot:run

# 4. Access the application
# Open your browser: http://localhost:7890

# 5. Login with default credentials
# Username: admin
# Password: adminpass
```

---

## Screenshots

<table width="100%">
<tr>
<td align="center"><b>Student Exam Interface</b></td>
<td align="center"><b>Admin Dashboard</b></td>
</tr>
<tr>
<td align="center"><img src="https://github.com/sumitkumar1503/online-exam-system/blob/master/screenshots/exampage.png" width="95%"></td>
<td align="center"><img src="https://github.com/sumitkumar1503/online-exam-system/blob/master/screenshots/admindashboard.png?raw=true" width="95%"></td>
</tr>
<tr>
<td align="center"><b>Exam Management</b></td>
<td align="center"><b>Question Management</b></td>
</tr>
<tr>
<td align="center"><img src="https://github.com/sumitkumar1503/online-exam-system/blob/master/screenshots/adminmanageexam.png" width="95%"></td>
<td align="center"><img src="https://github.com/sumitkumar1503/online-exam-system/blob/master/screenshots/adminmanagequestion.png" width="95%"></td>
</tr>
</table>

---

## Features

### Administrator Capabilities

- **Authentication & Security**
  - Secure login with role-based access control
  - Password encryption with BCrypt algorithm

- **Dashboard & Analytics**
  - Real-time statistics (students, exams, questions, submissions)
  - Visual performance metrics and KPIs

- **Exam Management**
  - Create, update, delete exam configurations
  - Define exam duration, description, and scheduling
  - Control exam visibility and access permissions

- **Question Management**
  - Add multiple-choice questions with options
  - Configure correct answers and points
  - Question linking with cascade delete protection
  - Prevent deletion of answered questions

- **Student Administration**
  - View and manage registered students
  - Reset student passwords
  - Delete accounts with data cleanup
  - Track student activity

- **Result Monitoring**
  - View detailed exam submissions
  - Analyze student performance metrics
  - Generate performance reports

### Student Capabilities

- **Account Management**
  - Self-registration with email validation
  - Secure login and password management
  - Profile customization with picture upload
  - Password change functionality

- **Exam Interface**
  - Browse available exams with details
  - Paginated questions for readability
  - Visual question palette for navigation
  - Live countdown timer with auto-submit

- **Assessment & Feedback**
  - Immediate results with score and percentage
  - Pass/fail status determination
  - Detailed answer review
  - Historical exam results tracking

---

## Tech Stack

| Component | Technology | Version |
|-----------|-----------|---------|
| **Backend** | Spring Boot | 3.x |
| **Security** | Spring Security | 6.x |
| **ORM** | Hibernate / JPA | 6.x |
| **Frontend** | Thymeleaf | 3.x |
| **UI Framework** | Bootstrap | 5.x |
| **Charting** | Chart.js | Latest |
| **Database** | H2 | Latest |
| **Build Tool** | Maven | 3.6+ |
| **Java Runtime** | OpenJDK/JDK | 17+ |

---

## System Requirements

| Requirement | Specification | Download |
|------------|---------------|----------|
| **Java** | 17 or higher | [Download](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html) |
| **Maven** | 3.6 or later | [Download](https://maven.apache.org/download.cgi) |
| **Git** | Latest version | [Download](https://git-scm.com/download) |
| **RAM** | 2GB minimum | - |
| **Storage** | 500MB for installation | - |

### Verify Installation

```bash
java -version       # Should show Java 17+
mvn -version        # Should show Maven 3.6+
git --version       # Should show Git 2.x+
```

---

## Installation

### Step 1: Clone Repository

```bash
git clone https://github.com/kumarianchal7279-cell/Online-examination-system.git
cd Online-examination-system
```

### Step 2: Install Dependencies

```bash
mvn clean install
```

This will:
- Download all project dependencies
- Compile source code
- Run test suite
- Create JAR package

### Step 3: Create Required Directories

```bash
# Windows
mkdir data
mkdir uploads

# Linux/macOS
mkdir -p data uploads
```

**Directory purposes:**
- `data/` - H2 database file storage
- `uploads/` - User profile pictures and uploads

### Step 4: Build Project

```bash
mvn clean package
```

---

## Configuration

### Application Properties

Edit `src/main/resources/application.properties`:

```properties
# Server Configuration
server.port=7890
server.servlet.context-path=/

# Database Configuration (H2)
spring.datasource.url=jdbc:h2:file:./data/examdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=password

# JPA/Hibernate Configuration
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=false

# H2 Console (Development)
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console

# Thymeleaf Configuration
spring.thymeleaf.mode=HTML
spring.thymeleaf.cache=false

# File Upload
file.upload-dir=uploads/

# Logging
logging.level.root=INFO
logging.level.com.example.exam=DEBUG
```

### MySQL Configuration (Alternative)

To use MySQL instead of H2:

**1. Update `application.properties`:**
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/exam_db
spring.datasource.driverClassName=com.mysql.cj.jdbc.Driver
spring.datasource.username=root
spring.datasource.password=your_password
spring.jpa.database-platform=org.hibernate.dialect.MySQL8Dialect
```

**2. Update `pom.xml`:**
```xml
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>8.0.33</version>
</dependency>
```

**3. Create database:**
```sql
CREATE DATABASE exam_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

---

## Running the Application

### Option 1: Maven (Recommended)

```bash
mvn spring-boot:run
```

### Option 2: IDE

1. Open in IntelliJ IDEA, Eclipse, or VS Code
2. Navigate to: `src/main/java/com/example/exam/OnlineExamApplication.java`
3. Right-click → Run
4. Wait for startup

### Option 3: JAR File

```bash
java -jar target/online-exam-0.0.1-SNAPSHOT.jar
```

**Access the application:**
```
http://localhost:7890
```

---

## Database

### H2 Console Access

```
URL: http://localhost:7890/h2-console

Credentials:
├── JDBC URL: jdbc:h2:file:./data/examdb
├── Username: sa
└── Password: password
```

### Default Admin Credentials

| Field | Value |
|-------|-------|
| **Username** | admin |
| **Password** | adminpass |

**⚠️ Important:** Change default credentials in production.

---

## Project Structure

```
online-exam-system/
│
├── src/main/java/com/example/exam/
│   ├── OnlineExamApplication.java      # Entry point
│   │
│   ├── config/
│   │   ├── SecurityConfig.java
│   │   └── CustomAuthSuccessHandler.java
│   │
│   ├── controller/                     # REST endpoints
│   │   ├── AdminController.java
│   │   ├── StudentController.java
│   │   └── AuthController.java
│   │
│   ├── service/                        # Business logic
│   │   ├── ExamService.java
│   │   ├── QuestionService.java
│   │   ├── StudentService.java
│   │   └── UserService.java
│   │
│   ├── repository/                     # Data access
│   │   ├── ExamRepository.java
│   │   ├── QuestionRepository.java
│   │   └── UserRepository.java
│   │
│   └── model/                          # JPA entities
│       ├── User.java
│       ├── Exam.java
│       ├── Question.java
│       └── Result.java
│
├── src/main/resources/
│   ├── application.properties
│   │
│   ├── templates/
│   │   ├── index.html
│   │   ├── login.html
│   │   ├── register.html
│   │   │
│   │   ├── admin/
│   │   │   ├── dashboard.html
│   │   │   ├── manage_exams.html
│   │   │   └── manage_questions.html
│   │   │
│   │   └── student/
│   │       ├── dashboard.html
│   │       ├── exam_page.html
│   │       └── my_results.html
│   │
│   └── static/
│       ├── css/
│       ├── js/exam-timer.js
│       └── images/
│
├── pom.xml                             # Maven config
├── mvnw / mvnw.cmd                     # Maven wrapper
└── README.md

```

---

## Usage Guide

### For Administrators

**Login:**
1. Visit `http://localhost:7890/login`
2. Enter: `admin` / `adminpass`
3. Access dashboard

**Dashboard Operations:**
- Monitor real-time statistics
- Track exam submissions
- View student performance

**Exam Management:**
- Create new exams
- Edit exam details
- Configure timing and instructions

**Question Management:**
- Add questions to exams
- Define answer options
- Mark correct answers

**Student Management:**
- View registered students
- Reset passwords
- Manage permissions

**Results Analysis:**
- View submission details
- Analyze performance metrics
- Generate reports

### For Students

**Registration:**
1. Visit `http://localhost:7890/register`
2. Complete form
3. Confirm email
4. Login

**Taking an Exam:**
1. Select exam from dashboard
2. Review instructions
3. Answer questions
4. Use palette for navigation
5. Submit before time expires

**View Results:**
- Check scores immediately
- Review correct answers
- Access exam history

---

## Troubleshooting

### Port 7890 Already in Use

```bash
# Windows
netstat -ano | findstr :7890
taskkill /PID <PID> /F

# Linux/macOS
lsof -ti:7890 | xargs kill -9
```

Or change port in `application.properties`:
```properties
server.port=8080
```

### Maven Command Not Found

Install Maven: https://maven.apache.org/download.cgi

Add to PATH:
- **Windows:** System Environment Variables
- **Linux/macOS:** `.bashrc` or `.zshrc`

Verify: `mvn -version`

### Java Version Error

```bash
java -version    # Check version
# Install Java 17+
```

### Database Connection Error

1. Verify `data/` directory exists
2. Check `application.properties` URL
3. Delete `data/examdb.mv.db`
4. Restart application

### Static Resources Not Loading

```bash
mvn clean install
# Clear browser cache
# Restart application
```

---

## License

This project is licensed under the **MIT License**. See [LICENSE](LICENSE) for details.

**You are free to:**
- Use commercially or privately
- Modify and distribute
- Use as template for other projects

---

## Support

For issues, questions, or contributions:

- **GitHub Issues:** [Report Issues](https://github.com/kumarianchal7279-cell/Online-examination-system/issues)
- **GitHub Discussions:** [Ask Questions](https://github.com/kumarianchal7279-cell/Online-examination-system/discussions)
- **Email:** Reach out through GitHub profile

---

<p align="center">
<strong>Built with ❤️ | Open Source & Free</strong>
</p>

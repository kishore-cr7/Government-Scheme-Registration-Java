# 🏛️ Government Scheme Registration System

> A Java Swing-based desktop application that enables citizens to discover, apply for, and track government schemes. Built with **Java**, **Swing GUI**, and **Oracle Database** using the **NetBeans IDE**.

---

## 📋 Table of Contents

- [About the Project](#-about-the-project)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Database Schema](#-database-schema)
- [Screenshots Flow](#-screenshots-flow)
- [Prerequisites](#-prerequisites)
- [Installation & Setup](#-installation--setup)
- [How to Run](#-how-to-run)
- [User Roles & Workflow](#-user-roles--workflow)
- [License](#-license)

---

## 📖 About the Project

The **Government Scheme Registration System** is a desktop application designed to digitize and streamline the process of government scheme registration for citizens. It provides a role-based portal where:

- **Citizens** can sign up, browse available government schemes, apply for schemes based on eligibility (age, gender, income, district, working status), and track their application status.
- **Scheme Providers** can manage scheme details, view registered users, and update scheme information.
- **Admins** have full control over user management, scheme management, application approval/rejection, and provider oversight.

The application is themed around the **Digital India** initiative and is branded with the tagline:  
*"Powered by Digital India Corporation (DIC), Ministry of Electronics & IT (MeitY), Government of India®"*

---

## ✨ Features

### 🔐 Authentication & Authorization
- Secure login system using **Aadhaar Number (ID) + Password**
- Role-based access control — `citizen`, `provider`, `admin`
- New user sign-up with detailed registration form

### 🏠 Citizen Portal
- Browse and search government schemes
- Filter schemes by **District**, **Age**, **Gender**, **Income**, and **Working Status**
- Apply for eligible schemes with one click
- Track application status (Pending / Approved / Rejected)
- Download approved scheme certificates

### 📋 Provider Portal
- View all available schemes
- Search and explore scheme details
- View registered citizen details

### 🛡️ Admin Portal
- **Manage Schemes** — Add, Update, and Delete government schemes
- **Manage Users** — View, Add, and manage citizen/provider accounts
- **Approve/Reject Applications** — Review and update scheme application statuses
- View provider details and scheme provider management

### 📜 Certificate Module
- Download scheme approval records for approved applications

### 📄 About Page
- Information about the application and the Digital India initiative

---

## 🛠️ Tech Stack

| Technology         | Purpose                          |
|--------------------|----------------------------------|
| **Java (JDK 8+)**  | Core programming language        |
| **Java Swing**      | GUI (Graphical User Interface)   |
| **Oracle Database (XE)** | Backend database storage   |
| **JDBC**            | Java Database Connectivity       |
| **NetBeans IDE**    | Development environment & form designer |
| **JUnit**           | Unit testing framework           |

---

## 📁 Project Structure

```
Government-Scheme-Registration/
├── nbproject/              # NetBeans project configuration files
├── photo/                  # Image assets (emblem, government logos, login image)
├── src/
│   └── gsr/                # Main source package
│       ├── login.java           # Login screen (Aadhaar + Password)
│       ├── homepage.java        # Citizen home page with image slider
│       ├── userdetails.java     # New user sign-up / registration form
│       ├── scheme.java          # Browse & apply for schemes (with filters)
│       ├── Schemedetails.java   # View scheme details in table
│       ├── status.java          # Track application status (citizen)
│       ├── certificate.java     # Download approved scheme certificates
│       ├── about.java           # About page
│       ├── adminpage.java       # Admin dashboard
│       ├── adminstatus.java     # Admin: approve/reject applications
│       ├── addscheme.java       # Admin: add new scheme
│       ├── updatescheme.java    # Admin: update existing scheme
│       ├── adduser.java         # Admin: add new user
│       ├── viewuser.java        # Admin: view user details
│       ├── manageuser.java      # Admin: manage user accounts
│       ├── providerpage.java    # Provider dashboard
│       └── providerdetails.java # Provider: view citizen details
├── test/
│   └── gsr/
│       └── loginTest.java       # JUnit test cases for login
├── acknowledgment.pdf      # Project acknowledgment document
├── build.xml               # Ant build configuration
├── manifest.mf             # JAR manifest file
└── README.md               # Project documentation
```

---

## 🗄️ Database Schema

The application uses **Oracle Database XE** with the following tables:

### `PEOPLE` (User Table)
| Column          | Type     | Description                |
|-----------------|----------|----------------------------|
| `id`            | NUMBER   | Aadhaar ID (Primary Key)   |
| `name`          | VARCHAR  | Full name                  |
| `age`           | NUMBER   | Age of the user            |
| `gender`        | VARCHAR  | Gender (Male/Female/Other) |
| `income`        | NUMBER   | Annual income              |
| `workingstatus` | VARCHAR  | Working status             |
| `district`      | VARCHAR  | District                   |
| `email`         | VARCHAR  | Email address              |
| `phone_number`  | VARCHAR  | Phone number               |
| `credential`    | VARCHAR  | Role (citizen/admin/provider) |
| `pass`          | VARCHAR  | Password                   |

### `SCHEME` (Government Schemes)
| Column           | Type     | Description              |
|------------------|----------|--------------------------|
| `id`             | NUMBER   | Scheme ID (Primary Key)  |
| `name`           | VARCHAR  | Scheme name              |
| `description`    | VARCHAR  | Scheme description       |
| `gender`         | VARCHAR  | Eligible gender          |
| `district`       | VARCHAR  | Eligible district        |
| `income`         | NUMBER   | Max eligible income      |
| `working_status` | VARCHAR  | Eligible working status  |
| `starting_age`   | NUMBER   | Minimum eligible age     |
| `ending_age`     | NUMBER   | Maximum eligible age     |

### `STATUS` (Application Tracking)
| Column        | Type     | Description                        |
|---------------|----------|------------------------------------|
| `userid`      | NUMBER   | Applicant's Aadhaar ID             |
| `user_name`   | VARCHAR  | Applicant's name                   |
| `scheme_name` | VARCHAR  | Name of the applied scheme         |
| `status`      | VARCHAR  | Application status (pending/approved/rejected) |

---

## 🖥️ Application Flow

```
Login Page
├── New User? → Sign Up (userdetails.java)
├── Citizen Login → Homepage
│   ├── Image Slider (Government Scheme Banners)
│   ├── Apply Schemes → Scheme List (Filter & Apply)
│   ├── Scheme Status → Track Applications
│   ├── Search Scheme → Scheme Details
│   └── About → About Page
├── Provider Login → Provider Page
│   ├── Scheme Provider Details
│   ├── Search Scheme → Scheme Details
│   └── Logout → Homepage
└── Admin Login → Admin Dashboard
    ├── Manage Users → View / Add Users
    ├── Add Scheme → Create New Scheme
    ├── Scheme Provider → View Providers
    ├── Manage Status → Approve / Reject Applications
    └── Logout → Homepage
```

---

## 📌 Prerequisites

Before running the project, ensure you have the following installed:

1. **Java Development Kit (JDK) 8** or higher  
   → [Download JDK](https://www.oracle.com/java/technologies/javase-downloads.html)

2. **NetBeans IDE** (Recommended: v8.2 or later)  
   → [Download NetBeans](https://netbeans.apache.org/download/)

3. **Oracle Database 11g Express Edition (XE)**  
   → [Download Oracle XE](https://www.oracle.com/database/technologies/xe-downloads.html)

4. **Oracle JDBC Driver** (`ojdbc8.jar` or `ojdbc6.jar`)  
   → Usually included with Oracle XE installation

---

## 🚀 Installation & Setup

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/kishore-cr7/Government-Scheme-Registration-Java.git
cd Government-Scheme-Registration-Java
```

### 2️⃣ Set Up Oracle Database

Open **SQL*Plus** or **Oracle SQL Developer** and run:

```sql
-- Create the PEOPLE table
CREATE TABLE people (
    id NUMBER PRIMARY KEY,
    name VARCHAR2(100),
    age NUMBER,
    gender VARCHAR2(10),
    income NUMBER,
    workingstatus VARCHAR2(50),
    district VARCHAR2(100),
    email VARCHAR2(100),
    phone_number VARCHAR2(15),
    credential VARCHAR2(20),
    pass VARCHAR2(50)
);

-- Create the SCHEME table
CREATE TABLE scheme (
    id NUMBER PRIMARY KEY,
    name VARCHAR2(200),
    description VARCHAR2(500),
    gender VARCHAR2(10),
    district VARCHAR2(100),
    income NUMBER,
    working_status VARCHAR2(50),
    starting_age NUMBER,
    ending_age NUMBER
);

-- Create the STATUS table
CREATE TABLE status (
    userid NUMBER,
    user_name VARCHAR2(100),
    scheme_name VARCHAR2(200),
    status VARCHAR2(20) DEFAULT 'pending'
);

-- Insert a default admin user
INSERT INTO people VALUES (100001, 'Admin', 30, 'Male', 100000, 'Government', 'All', 'admin@gov.in', '9999999999', 'admin', 'admin123');

COMMIT;
```

### 3️⃣ Configure Database Connection

The database connection string used in the project:
```
URL:      jdbc:oracle:thin:@localhost:1521:xe
Username: system
Password: 15-06-2005
```

> ⚠️ **Important:** Update the password in all `.java` files under `src/gsr/` to match your Oracle DB password. Search for `DriverManager.getConnection` in the source files and replace `"15-06-2005"` with your Oracle system password.

### 4️⃣ Open in NetBeans
1. Open **NetBeans IDE**
2. Go to **File → Open Project**
3. Navigate to the cloned repository folder and open it
4. Right-click the project → **Properties → Libraries**
5. Add the **Oracle JDBC driver** (`ojdbc8.jar`) to the project libraries

---

## ▶️ How to Run

### Option 1: Via NetBeans IDE
1. Open the project in NetBeans
2. Right-click on `src/gsr/homepage.java` (or `login.java`)
3. Click **Run File** (or press `Shift + F6`)

### Option 2: Via Command Line
```bash
# Compile
javac -cp ".;path/to/ojdbc8.jar" src/gsr/*.java

# Run
java -cp ".;path/to/ojdbc8.jar" gsr.homepage
```

### Option 3: Build JAR using Ant
```bash
ant -f build.xml
java -jar dist/GSR.jar
```

---

## 👥 User Roles & Workflow

| Role       | Access Level | Key Actions |
|------------|-------------|-------------|
| **Citizen**   | Basic    | Sign up, browse schemes, apply, check status, download certificates |
| **Provider**  | Medium   | View schemes, search details, view user data |
| **Admin**     | Full     | CRUD on schemes, user management, approve/reject applications |

### Sample Login Credentials (after DB setup)
| Role   | ID     | Password  |
|--------|--------|-----------|
| Admin  | 100001 | admin123  |

---

## 📝 License

This project is developed for academic/educational purposes as part of a **Software Engineering** course.

---

<p align="center">
  <b>🇮🇳 Powered by Digital India | Ministry of Electronics & IT (MeitY) | Government of India®</b>
</p>
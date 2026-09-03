# 📚 Library Management System

A desktop-based **Library Management System** developed using **Python, Tkinter, and SQLite**. The application provides a graphical interface for managing books, students, book issue/return operations, authentication, searching, and library records.

---

## 📌 Project Overview

The Library Management System is designed to simplify common library operations through an easy-to-use desktop application.

The system provides an authentication screen and a dashboard from which the library administrator can manage books and perform different library activities.

The application uses SQLite databases to store:

* Administrator login information
* Book information
* Student information
* Book issue and return details

---

## ✨ Features

### 🔐 Authentication

* User ID and password based login
* Invalid login validation
* Password change functionality
* Logout functionality

### 📖 Book Management

* Add new books
* Edit existing book details
* Delete books
* Search books using Book ID
* Display all available book records
* Store book ID, title, author, edition, and price

### 📤 Book Issue

* Verify student using ERP ID
* Display student information
* Verify requested book
* Issue books to registered students
* Set issue and return dates
* Limit the number of books issued to a student
* Email notification functionality for issued books

### 📥 Book Return

* Return books using student ERP ID
* Update student borrowing information
* Record submission date
* Calculate overdue charges/fines
* Update book availability after return

### 🗃️ Database Management

The application uses SQLite databases for persistent storage:

* `admin.db`
* `StoreBooks.db`
* `StudentsData.db`

---

## 🛠️ Technologies Used

| Technology   | Purpose                          |
| ------------ | -------------------------------- |
| Python       | Application development          |
| Tkinter      | Graphical User Interface         |
| SQLite       | Database management              |
| ttk          | Table and GUI components         |
| tkcalendar   | Date selection                   |
| Pillow (PIL) | Image handling                   |
| smtplib      | Email notification functionality |

---

## 🏗️ Application Structure

The main application is implemented in:

```text
dbms7.py
```

The project uses SQLite database files to maintain application data.

A typical project structure is:

```text
Library-Management-System/
│
├── dbms7.py
├── admin.db
├── StoreBooks.db
├── StudentsData.db
├── images/
└── README.md
```

> The exact files and folders may vary depending on the version of the project uploaded to the repository.

---

## 🗄️ Database Design

The system works with multiple SQLite databases.

### Admin Database

The administrator authentication system uses the `UserLogin` table.

It stores information such as:

* User ID
* Password

The application checks the entered credentials against the stored login information before opening the dashboard.

### Books Database

The `Books` table stores library book information.

Main fields used by the application include:

* Book ID
* Title
* Author
* Edition
* Price
* Issue status
* Student ID associated with an issued book

### Student Database

The `Students` table stores student information used during book issue and return operations.

The application uses student details such as:

* ERP ID
* Name
* Course
* Year
* Contact
* Email
* Number of issued books
* Issue date
* Return date
* Submission date
* Charges

---

## 🔄 Library Workflow

The general workflow of the application is:

```text
                    ┌──────────────────┐
                    │      Login       │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │    Dashboard     │
                    └────────┬─────────┘
                             │
          ┌──────────────────┼───────────────────┐
          │                  │                   │
          ▼                  ▼                   ▼
     Add Books          Issue Books         Search Books
          │                  │
          ▼                  ▼
     Edit Books          Return Books
          │                  │
          ▼                  ▼
     Delete Books       Update Records
          │
          ▼
     Show Books
```

---

## 🚀 Installation

### 1. Install Python

Download and install Python from the official Python website.

Make sure Python is added to your system PATH during installation.

Check the installation using:

```bash
python --version
```

---

### 2. Clone the Repository

```bash
git clone https://github.com/Aryan091203/Library-Management-System.git
```

Move into the project directory:

```bash
cd Library-Management-System
```

---

### 3. Install Required Python Packages

Install the external dependencies:

```bash
pip install pillow tkcalendar
```

The following libraries are included with standard Python installations:

```text
tkinter
sqlite3
smtplib
datetime
time
```

---

## ▶️ Running the Application

From the project directory, run:

```bash
python dbms7.py
```

The application will open the Library Management System login window.

---

## 🖥️ Main Dashboard

After successful authentication, the dashboard provides access to the major library operations:

* Add Books
* Issue Books
* Edit Books
* Return Books
* Delete Books
* Show Books
* Search Books
* Log Out

---

## 📚 Adding a Book

The **Add Books** section allows the administrator to enter:

```text
Book ID
Title
Author
Edition
Price
```

After submitting valid information, the book is stored in the SQLite book database.

---

## 📤 Issuing a Book

To issue a book:

1. Enter the student's ERP ID.
2. The system checks whether the student exists.
3. Student information is displayed.
4. Enter the Book ID.
5. The system verifies the book.
6. Select the expected return date.
7. Confirm the issue operation.

The system updates the book's issue status and the student's borrowing information.

---

## 📥 Returning a Book

To return a book:

1. Enter the student's ERP ID.
2. The system checks the student's borrowing record.
3. The issued book information is updated.
4. The book is marked as returned.
5. The submission date is recorded.
6. If the book is overdue, a fine is calculated.

The current implementation calculates an additional charge based on overdue days.

---

## 🔎 Searching Books

The **Search Books** functionality allows the administrator to search for a book using its Book ID.

If the book exists, the application displays information such as:

* Title
* Author
* Edition

If the book does not exist, an appropriate warning is displayed.

---

## 📋 Displaying Books

The **Show Books** section displays book records in a tabular interface using Tkinter's `Treeview`.

The table includes:

* Book ID
* Title
* Author
* Edition
* Price

---

## ✏️ Editing Books

Existing book records can be updated by searching for a Book ID.

The administrator can modify:

* Book ID
* Title
* Author
* Edition
* Price

The changes are then saved to the SQLite database.

---

## 🗑️ Deleting Books

Books can be removed from the library database by entering the corresponding Book ID.

The system first checks whether the book exists before deleting its record.

---

## 📧 Email Notification

The application contains functionality for sending an email notification when a book is issued.

It uses Python's `smtplib` library and Gmail's SMTP server.

> **Security Note:** Do not upload real email passwords, SMTP credentials, API keys, or other secrets to GitHub. Use environment variables or another secure configuration method for real deployments.

---

## ⚠️ Important Notes

This project was created as a **DBMS/academic desktop application** and demonstrates database connectivity and library management operations.

The source code currently contains hard-coded local image paths in some places. For example, paths such as:

```text
E:\downloads\back.png
```

may not work on another computer.

If you run the project on a different system, image paths may need to be updated to use paths relative to the project directory.

---

## 🔒 Security Considerations

For a production-ready application, the following improvements are recommended:

* Hash passwords instead of storing them directly
* Use parameterized SQL queries
* Avoid hard-coded credentials
* Store email credentials securely
* Use relative file paths
* Validate all user input
* Add role-based access control
* Protect sensitive student information

---

## 🔮 Future Improvements

Possible future improvements include:

* Modern responsive GUI
* Separate administrator and student accounts
* Secure password hashing
* Better database normalization
* Parameterized SQL queries
* Automatic email notifications
* Book category and genre management
* Book availability dashboard
* Student registration interface
* Advanced search and filtering
* Fine/payment history
* Database backup and restore
* Reports and statistics
* Improved error handling
* Cross-platform file-path support

---

## 🎓 Academic Project

This project demonstrates the practical implementation of **Database Management System concepts** through a Python desktop application.

It covers concepts including:

* Database connectivity
* CRUD operations
* Authentication
* Record management
* Data retrieval
* Data updates
* Data deletion
* Book issue/return transactions
* Student record management
* GUI-based database interaction

---


## 📂 Repository

GitHub Repository:

**Library Management System**

https://github.com/Aryan091203/Library-Management-System

---

## ⭐ Acknowledgement

This project was developed as an academic DBMS project to demonstrate how a graphical desktop application can interact with a relational database to manage library operations.

---

## 📜 License

This project is intended primarily for **educational and academic purposes**.

You may use and modify the project for learning purposes.

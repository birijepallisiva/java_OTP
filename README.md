# FileEnc OTP Authentication App

This project is a **Java console-based application** that allows users to **sign up, log in, and manage hidden files** securely with **OTP (One-Time Password) authentication**.

## 🚀 Features
- **User Signup & Login** using email verification.
- **OTP Authentication** via email (sent using Gmail SMTP).
- **File Hiding & Unhiding** functionality.
- **MySQL Database Integration** to store users and file metadata.
- **DAO Layer** for clean database interaction.
- **Modular MVC Architecture** (Models, Views, Services, DAO).

## 📂 Project Structure
```
src/
├── db/
│   └── MyConnection.java       # Handles MySQL connection
├── model/
│   ├── Data.java               # Represents file details
│   └── User.java               # Represents a user
├── service/
│   ├── SendOTPService.java     # Sends OTP via Gmail SMTP
│   ├── GenerateOTP.java        # Generates random OTPs
│   └── UserService.java        # Business logic for users
├── dao/
│   ├── UserDAO.java            # Handles user DB operations
│   └── DataDAO.java            # Handles file DB operations
├── views/
│   ├── Welcome.java            # Entry point for login/signup
│   └── UserView.java           # User dashboard (hide/unhide files)
```

## 🛠 Requirements
- **Java 17+**
- **MySQL 8+**
- **Maven/Gradle** (optional for dependency management)
- **Gmail Account** (with App Password enabled for SMTP)

## ⚙️ Setup Instructions
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/FileEncApp.git
   cd FileEncApp
   ```

2. Create MySQL database:
   ```sql
   CREATE DATABASE ytproject;
   ```

3. Update DB credentials in `MyConnection.java`:
   ```java
   connection = DriverManager.getConnection(
       "jdbc:mysql://localhost:3306/ytproject?useSSL=false",
       "root",
       "yourpassword"
   );
   ```

4. Configure Gmail credentials in `SendOTPService.java`:
   ```java
   String from = "yourgmail@gmail.com";
   return new PasswordAuthentication(from, "your-app-password");
   ```

5. Compile & Run the application:
   ```bash
   javac -d bin src/**/*.java
   java -cp bin views.Welcome
   ```

## 📌 Usage Flow
- On startup, you will see:
  ```
  Welcome to the app
  Press 1 to login
  Press 2 to signup
  Press 0 to exit
  ```
- **Signup**: Enter name & email → receive OTP via email → verify → account created.
- **Login**: Enter email → receive OTP → verify → access dashboard.
- **Dashboard Options**:
  - `1`: Show hidden files
  - `2`: Hide a file (store in DB & hide logic)
  - `3`: Unhide a file
  - `0`: Exit

## 🔐 Security Notes
- Gmail now requires **App Passwords** for third-party apps (not your normal password).
- Ensure `.gitignore` includes your credentials before pushing code.

## 📄 License
This project is open-source and available under the **MIT License**.

---
👨‍💻 Developed for learning secure file management with Java, MySQL, and OTP authentication.

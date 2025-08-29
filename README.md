# Lab-System-Monitoring

# 🔐 Login Management System with Tkinter & MySQL

This project is a **Login Management System** built with **Python (Tkinter)** and **MySQL**.
It provides authentication, session tracking, system monitoring, and administrative controls for lab/office environments.

## ✨ Features

✅ **Login System**

* Local users (`USER01 – USER04`) with predefined credentials
* Database-based user authentication (`user_details` table in MySQL)
* Admin login with elevated privileges

✅ **Admin Panel**

* View login/logout history
* Manage system MAC addresses
* Add new system entries
* Disable/Enable **Ctrl+Alt+Delete** (Task Manager lock)
* Open external monitoring software

✅ **User Panel**

* Personalized welcome page
* Secure logout with database update

✅ **System Features**

* Automatic **IP address, MAC address, and system ID** logging
* Prevents users from opening **Task Manager** or using restricted keys
* Shutdown button (updates DB before system shutdown)
* Persistent window always on top (cannot be closed normally)
* Displays **real-time clock**
* Scrolling header text

✅ **Password Management**

* Users can **change passwords** after successful login
* Secure validation against old password

✅ **Database Integration**

* Stores login/logout details in `log_details` table
* Maps MAC addresses to system IDs via `mac_address_details` table

---

## 🗂 Database Structure

### `user_details`

| Column     | Type    | Description          |
| ---------- | ------- | -------------------- |
| user\_name | VARCHAR | Username of the user |
| password   | VARCHAR | User’s password      |

### `log_details`

| Column       | Type     | Description                     |
| ------------ | -------- | ------------------------------- |
| ID           | INT (PK) | Auto-increment log ID           |
| user\_name   | VARCHAR  | Username of the logged-in user  |
| login\_time  | DATETIME | Time when user logged in        |
| logout\_time | DATETIME | Time when user logged out       |
| ip\_address  | VARCHAR  | System IP address               |
| mac\_address | VARCHAR  | MAC address of the system       |
| system\_id   | VARCHAR  | ID of system (from MAC mapping) |

### `mac_address_details`

| Column       | Type    | Description                  |
| ------------ | ------- | ---------------------------- |
| mac\_address | VARCHAR | Unique MAC address of system |
| system\_id   | VARCHAR | Identifier for the system    |

---

## ⚙️ Requirements

* Python **3.8+**

* MySQL Server (with database `project1`)

* Required Python modules:

  ```bash
  pip install mysql-connector-python getmac elevate keyboard
  ```

* External monitoring software (optional):
  `Net Monitor for Employees Pro` installed at:

  ```
  C:\Program Files (x86)\Net Monitor for Employees Pro\bin\nmep_console.exe
  ```

---

## 🚀 How to Run

1. Clone or download this project
2. Update **database credentials** in `db_config` inside the script:

   ```python
   db_config = {
       'host': '192.168.3.25',
       'user': 'root',
       'password': 'YOUR_PASSWORD',
       'database': 'project1'
   }
   ```
3. Place required **images** in the correct folder:

   ```
   C:\Users\CSELAB\labsystem\images\
   ├── login.png
   └── admin.png
   ```
4. Run the application:

   ```bash
   python main.py
   ```

---

## 🔑 Default Users

| Username | Password      | Role          |
| -------- | ------------- | ------------- |
| USER01   | CSEDEPT       | Local User    |
| USER02   | CSEDEPT       | Local User    |
| USER03   | CSEDEPT       | Local User    |
| USER04   | CSEDEPT       | Local User    |
| admin    | (DB password) | Administrator |

---

## 🛡 Security Notes

* Storing passwords in plain text is **not secure**. Use hashing (e.g., bcrypt) for production.
* Disabling **Ctrl+Alt+Delete** modifies Windows Registry → requires **Admin privileges**.
* Be careful when enabling shutdown, as it forces system power-off.

---

## 👨‍💻 Contributors

* Developed by students of **Batch 2020-2024** under the guidance of
  **Mr. M.S.R.S. Prasad (HOD, CSE Dept.)**

---


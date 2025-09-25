# 🚀 CRM Web Application

Welcome to the **CRM (Customer Relationship Management) Web App** — a robust enterprise-grade solution built with **Spring Boot MVC**, **Thymeleaf**, **Hibernate**, **MySQL**, and **Java 17**.

This app empowers teams to manage customers, leads, contracts, appointments, and communications efficiently — with powerful integrations like **Google Drive**, **Gmail**, and **Google Calendar**.

---

## 🔧 Prerequisites

Make sure your system has the following:

- ✅ Java 17 installed
- ✅ MySQL running and accessible
- ✅ Valid MySQL credentials (URL, username, password)
- ✅ Google API credentials (OAuth 2.0) for Drive, Gmail, and Calendar integration

---

## 📦 Installation Guide

### 1. Clone the Repository

```bash
git clone https://github.com/khushi036/Khushi-crm.git
cd Khushi-crm
```

---

### 2. Configure MySQL in `application.properties`

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/crm?createDatabaseIfNotExist=true
spring.datasource.username=YourUserName
spring.datasource.password=YourPassword
spring.jpa.hibernate.ddl-auto=none
spring.sql.init.mode=always
```

> Replace `YourUserName` and `YourPassword` with your actual MySQL credentials.

---

### 3. Set Up Google API Credentials

- Go to [Google Cloud Console](https://console.cloud.google.com/)
- Create or select a project
- Enable:
  - Google Drive API
  - Gmail API
  - Google Calendar API
- Go to **APIs & Services > Credentials**
  - Click **Create Credentials > OAuth Client ID**
  - Choose **Web Application**
  - Add the following Redirect URIs:
    - `http://localhost:8080/login/oauth2/code/google`
    - `http://localhost:8080/employee/settings/handle-granted-access`
  - Save the **Client ID** and **Client Secret**

---

### 4. Define Google OAuth Redirect URI

```properties
spring.security.oauth2.client.registration.google.redirect-uri={baseUrl}/login/oauth2/code/{registrationId}
```

---

### 5. Set Google OAuth Authorization and Token URIs

```properties
spring.security.oauth2.client.provider.google.authorization-uri=https://accounts.google.com/o/oauth2/auth
spring.security.oauth2.client.provider.google.token-uri=https://accounts.google.com/o/oauth2/token
```

---

### 6. Add Required Google API Scopes

| Service        | Scope URL                                     |
|----------------|-----------------------------------------------|
| Google Drive   | `https://www.googleapis.com/auth/drive`       |
| Gmail          | `https://www.googleapis.com/auth/gmail.readonly` |
| Google Calendar| `https://www.googleapis.com/auth/calendar`    |

Add these scopes when configuring your credentials in the Google Cloud Console.

---

### 7. Build the Application

```bash
mvn clean install
```

---

### 8. Run the Application

```bash
mvn spring-boot:run
```

---

### 9. Access the App

Open your browser and go to:

```
http://localhost:8080
```

---

## 🌟 Features Overview

### 🔐 Authentication & Authorization

- Secure login via username/password
- Google OAuth login (Drive, Gmail, Calendar integration)

---

### 📁 Google Drive Integration

- Create, delete, and share files/folders
- Auto-save ticket/lead attachments

---

### 📅 Google Calendar Integration

- Visual calendar via FullCalendar.js
- Create/edit/delete meetings with email notifications

---

### 📧 Gmail Integration

- View inbox, drafts, sent, and trash
- Send emails and save drafts directly from the app

---

### 👥 User Roles & Permissions

| Role     | Access Highlights |
|----------|-------------------|
| Manager  | Full access, user/role management, ticket/lead assignment |
| Employee | Handle assigned leads, contracts, and tickets |
| Customer | View/manage their own tickets, leads, contracts |

---

### 🎯 Leads Management

- Create, update, delete, view leads
- Auto-save lead files to Google Drive
- Schedule lead meetings with Google Calendar

---

### 🧾 Ticket Management

- Full CRUD support
- Attachments saved to Drive
- Integrated meeting scheduling

---

### 📄 Contracts

- Manage contracts with amount, dates, description, attachments
- Share via Google Drive

---

### ✉️ Email Templates & Campaigns

- Use drag-and-drop Unlayer editor
- Send personalized campaign emails

---

### ⚙️ User Settings

- Enable/disable Google integrations
- Customize email preferences
- Manage automatic notifications for updates

---

## 🤝 Contributing

Contributions are welcome!  
Feel free to open an issue or submit a pull request with improvements or bug fixes.

---

## 📄 License

This project is licensed under the **MIT License**.

---


Project Description
A complete full-stack authentication system that allows users to register accounts, log in securely, access protected profile/dashboard pages, and log out. The system implements proper access control to prevent unauthorized access to protected routes. It follows client-server architecture with separate frontend and backend components.

What the App Does:
Registration: New users can create accounts with email, username, and password

Login: Registered users can authenticate using credentials

Protected Access: Only authenticated users can view profile/dashboard pages

Session Management: JWT-based authentication with secure logout

Input Validation: Both client-side and server-side validation

Tech Stack
Backend: Java, Spring Boot, Spring Security, JWT, Spring Data JPA, MySQL

Frontend (Web): React.js, React Router, Axios, Context API, Tailwind CSS

Frontend (Mobile): React Native, Expo, AsyncStorage, React Navigation

Database: phpmyadmin

Build Tools: Maven (Backend), npm/yarn (Frontend)

How to Run Backend
Ensure Java 19 is installed

Clone the repository and navigate to backend directory

Create MySQL database named "lapina_lab1"

Update application.properties with your database credentials

Run mvn clean install followed by mvn spring-boot:run

Backend will start on http://localhost:8080

How to Run Web Application
Navigate to frontend/web directory

Install dependencies with npm install or yarn install

Create .env file with API base URL (http://localhost:8080/api)

Run npm start or yarn start

Application will open on http://localhost:3000



atabase Setup Instructions
Option 1: Using Spring Boot Auto-Creation
Set spring.jpa.hibernate.ddl-auto=update in application.properties

Spring Boot will automatically create tables on startup

Option 2: Manual SQL Import
Create database: CREATE DATABASE auth_system;

Run provided SQL script (schema.sql) to create users table

The users table stores: id, username, email, password (encrypted), timestamps, and enabled status

Environment Variables & Configuration
Backend (application.properties):
text

spring.datasource.url=jdbc:mysql://localhost:3306/auth_system
spring.datasource.username=your_username
spring.datasource.password=your_password

jwt.secret=your-jwt-secret-key-minimum-256-bits
jwt.expiration=86400000 

server.port=8080
spring.jpa.hibernate.ddl-auto=update
Frontend Web (.env):
text
REACT_APP_API_BASE_URL=http://localhost:8080/api
REACT_APP_JWT_STORAGE_KEY=auth_token
Frontend Mobile (.env):
text
EXPO_PUBLIC_API_BASE_URL=http://localhost:8080/api

API Endpoints List
Authentication Endpoints:
POST /api/auth/register - Register new user

Request: username, email, password, firstName, lastName

Response: User details + JWT token

POST /api/auth/login - User login

Request: username/email, password

Response: JWT token + user details

POST /api/auth/logout - User logout

Request: JWT token in header

Response: Success message

User Endpoints:
GET /api/users/profile - Get current user profile

Requires: Authentication

Response: User profile data

PUT /api/users/profile - Update user profile

Requires: Authentication

Request: Updated user data

Response: Updated profile

Health Check:
GET /api/health - Check backend status

Response: {"status": "Backend is running"}

Protected Routes:
All endpoints except /api/auth/register, /api/auth/login, and /api/health require valid JWT token in Authorization header.

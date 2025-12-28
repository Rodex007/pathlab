# PathLab Backend

A comprehensive Spring Boot backend application for managing pathology laboratory operations, including patient management, test bookings, sample tracking, test results, and offline payment processing.

## Project Overview

PathLab Backend provides a complete REST API solution for modern pathology laboratories.  It enables patients to book tests, facilitates lab technicians in managing samples and recording results, and allows administrators to oversee all operations through an intuitive dashboard.  The system handles end-to-end workflows from booking through result generation and PDF report generation.

**Who It Is For:**
- Pathology laboratories and diagnostic centers
- Patients seeking convenient test booking and result retrieval
- Lab technicians managing sample collection and testing
- Doctors monitoring patient test results
- Administrators overseeing lab operations

## Key Features

### Patient Management
- Patient registration and profile management
- Self-service patient dashboard
- Booking history and payment tracking
- Email-based account verification and password recovery

### Test & Sample Management
- Centralized test catalog with parametric definitions
- Flexible sample type tracking (blood, urine, tissue, etc.)
- Multi-status sample lifecycle management (collection pending, collected, in transit, received, tested, discarded)
- Sample collection tracking with lab technician assignment

### Booking System
- Create and manage patient test bookings
- Bulk test assignment per booking
- Real-time booking status tracking (pending, completed, cancelled)
- Automatic sample creation for each test in a booking

### Results Management
- Record test results with multiple parameters
- Support for updating results after initial entry
- PDF report generation with Freemarker templates
- Grouped results retrieval by test

### Payment Processing
- Offline payment tracking and management
- Automatic payment creation upon booking
- Invoice PDF generation for payments
- Payment status management (pending, paid)

### Dashboard & Analytics
- Admin dashboard with key statistics
- Monthly booking trends
- Test distribution analysis
- Recent activity logs
- Role-based access control

### Security
- JWT-based authentication and authorization
- Role-based access control (ADMIN, LAB_TECH, DOCTOR, PATIENT)
- Email verification for new accounts
- Password reset functionality
- Secure token invalidation on logout

### Additional Features
- Cloudinary integration for image storage
- PDF generation for reports and invoices
- Email notifications for verification and password recovery
- Caffeine caching for performance optimization
- Flyway database migrations
- Comprehensive input validation

## Architecture Overview

PathLab Backend follows a layered architecture pattern: 
```
Controller Layer
     ↓
Service Layer (Business Logic)
     ↓
Repository Layer (Data Access)
     ↓
Entity/Domain Models
     ↓
PostgreSQL Database
```

The application is organized into the following functional modules: 

- **Authentication**:  User registration, login, logout, email verification, password reset
- **Patient Management**:  Patient CRUD operations and profile management
- **Tests**: Test definition and parameter management
- **Bookings**:  Test booking lifecycle and management
- **Samples**: Sample collection and status tracking
- **Results**: Test result recording and retrieval
- **Payments**: Payment tracking and invoice generation
- **Dashboard**: Analytics and statistics for administrators
- **PDF Generation**: Report and invoice PDF rendering

## Tech Stack

### Backend
- Java 21
- Spring Boot 3.5.5
- Spring Security (JWT authentication)
- Spring Data JPA (Hibernate ORM)
- Spring Mail (Email support)
- Jakarta Servlet API (REST endpoints)

### Database
- PostgreSQL (primary relational database)
- Flyway (database version control and migrations)

### Libraries & Integrations
- Lombok (boilerplate code reduction)
- JJWT 0.11.5 (JWT token handling)
- Cloudinary HTTP5 (cloud image storage)
- Caffeine 3.1.8 (in-memory caching)
- OpenHTML2PDF with PDFBox (PDF generation)
- Freemarker (template engine for PDFs and emails)

### Tooling & DevOps
- Apache Maven 3.9.9 (build automation)
- Docker (containerization)
- Eclipse Temurin Java 21 (JDK)

## Project Structure
```
pathlab-backend/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/pathlab/
│   │   │       ├── config/                 # Application & security configuration
│   │   │       │   ├── SecurityConfig.java
│   │   │       │   ├── CorsConfig.java
│   │   │       │   └── FreemarkerConfig.java
│   │   │       │
│   │   │       ├── controller/             # REST API controllers
│   │   │       │   ├── AuthController.java
│   │   │       │   ├── PatientController.java
│   │   │       │   ├── BookingsController.java
│   │   │       │   ├── SampleController.java
│   │   │       │   ├── PaymentController.java
│   │   │       │   ├── BookingResultsController.java
│   │   │       │   └── DashboardController.java
│   │   │       │
│   │   │       ├── dto/                    # API request/response models
│   │   │       │   ├── auth/
│   │   │       │   ├── booking/
│   │   │       │   ├── patient/
│   │   │       │   ├── payment/
│   │   │       │   ├── result/
│   │   │       │   └── dashboard/
│   │   │       │
│   │   │       ├── entity/                 # JPA domain entities
│   │   │       │   ├── User.java
│   │   │       │   ├── Patient.java
│   │   │       │   ├── Booking.java
│   │   │       │   ├── Sample.java
│   │   │       │   ├── TestEntity.java
│   │   │       │   ├── TestResult.java
│   │   │       │   ├── Payment.java
│   │   │       │   └── enums/              # Domain enumerations
│   │   │       │
│   │   │       ├── repository/             # Spring Data JPA repositories
│   │   │       │   ├── UserRepository.java
│   │   │       │   ├── PatientRepository.java
│   │   │       │   ├── BookingRepository.java
│   │   │       │   ├── SampleRepository.java
│   │   │       │   ├── TestEntityRepository.java
│   │   │       │   └── PaymentRepository.java
│   │   │       │
│   │   │       ├── service/                # Business logic layer
│   │   │       │   ├── AuthService.java
│   │   │       │   ├── PatientService.java
│   │   │       │   ├── BookingService.java
│   │   │       │   ├── SampleService.java
│   │   │       │   ├── TestService.java
│   │   │       │   ├── TestResultService.java
│   │   │       │   ├── PaymentService.java
│   │   │       │   ├── DashboardService.java
│   │   │       │   ├── EmailService.java
│   │   │       │   └── PdfService.java
│   │   │       │
│   │   │       ├── security/               # JWT authentication & filters
│   │   │       │   └── JwtAuthenticationFilter.java
│   │   │       │
│   │   │       ├── exception/              # Global exception handling
│   │   │       │   └── GlobalExceptionHandler.java
│   │   │       │
│   │   │       ├── util/                   # Utility helpers
│   │   │       │   ├── JwtUtil.java
│   │   │       │   └── DateUtils.java
│   │   │       │
│   │   │       └── PathLabApplication.java # Spring Boot entry point
│   │   │
│   │   └── resources/
│   │       ├── application.properties     # Application configuration
│   │       ├── db/
│   │       │   └── migration/              # Flyway database migrations
│   │       │       └── V1__init.sql
│   │       └── templates/                  # Freemarker templates
│   │           ├── email/
│   │           │   ├── verification.html
│   │           │   └── report-template.html
│   │           ├── invoice.ftl
│   │           └── report.ftl
│
├── Dockerfile                             # Docker image configuration
├── pom.xml                                # Maven dependencies & build config
├── mvnw / mvnw.cmd                        # Maven wrapper
└── README.md

```

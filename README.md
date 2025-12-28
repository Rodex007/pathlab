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

## Getting Started

### Prerequisites

- Java 21 or later (Eclipse Temurin recommended)
- Maven 3.9.9 or later
- PostgreSQL 12 or later
- Git

### Environment Setup

1. **Install PostgreSQL and create a database:**

   ```bash
   createdb pathlab
   ```
2. **Clone the repository:**
   ```bash
   git clone https://github.com/CodeInn30/pathology-lab-backend-new.git
   cd pathology-lab-backend-new
   ```
3. **Create a .env file or set environment variables (see Environment Variables section)**

### Installation Steps

1. **Build the application using Maven:**
   ```bash
   ./mvnw clean package
   ```
   *On Windows:*
   ```bash
   mvnw. cmd clean package
   ```
2. **Run the application:**
   ```bash
   ./mvnw spring-boot:run
   ```
   *Or after packaging:*
   ```bash
   java -jar target/pathlab-0.0.1-SNAPSHOT. jar
   ```
3. **Access the API:**
   * Base URL: http://localhost:8080
   * API documentation available at: http://localhost:8080/swagger-ui.html (if Swagger is configured)
  
## Environment Variables
**Configure the following environment variables in application.properties or system environment:**

***Database Configuration***
```code
DB_URL=jdbc:postgresql://localhost:5432/pathlab
DB_USERNAME=postgres
DB_PASSWORD=your_password
```

***Cloudinary Configuration***
```code
CLOUDINARY_CLOUD_NAME=your-cloud-name
CLOUDINARY_API_KEY=your-api-key
CLOUDINARY_API_SECRET=your-api-secret
```

***Email Configuration***
```bash
MAIL_USERNAME=your-email@gmail.com
MAIL_PASSWORD=your-app-password
```

***Security & JWT***
```code
JWT_SECRET_BASE64=your-base64-encoded-secret
```

***Application URLs***
```code
PUBLIC_BASE_URL=http://localhost:5173
```

## Development Workflow

**Running Tests**
```bash
./mvnw test
```

**Building the Application**
```bash
./mvnw clean package -DskipTests
```

**Running Specific Services**
The application is a monolithic Spring Boot service. All modules run together, but you can test specific APIs:

***Authentication:***
```bash
POST /api/auth/register/patient
POST /api/auth/register/user
POST /api/auth/login
POST /api/auth/logout
GET /api/auth/verify-email? token=...
POST /api/auth/forgot-password
POST /api/auth/reset-password
```

***Patient Management:***
```bash
GET /api/patients
GET /api/patients/{id}
POST /api/patients
PUT /api/patients/{id}
DELETE /api/patients/{id}
```

***Bookings:***
```bash
GET /api/bookings
GET /api/bookings/{id}
POST /api/bookings
PUT /api/bookings/{id}
DELETE /api/bookings/{id}
```

***Test Results & PDF Generation:***
```bash
POST /api/bookings/{bookingId}/tests/{testId}/results
GET /api/bookings/{bookingId}/results
GET /api/bookings/{bookingId}/results/pdf
GET /api/payments/{id}/invoice/pdf
```

***Useful Commands***
```bash
# Clean build
./mvnw clean

# Compile
./mvnw compile

# Run tests
./mvnw test

# Package without tests
./mvnw package -DskipTests

# View dependency tree
./mvnw dependency:tree

# Format code
./mvnw spotless:apply
```

## Deployment Notes

**Docker Deployment**
The repository includes a multi-stage Dockerfile for containerization:

1. ***Build the Docker image:***
   
   ```bash
   docker build -t pathlab-backend: latest .
   ```
  
2. ***Run the container:***
   ```bash
   docker run -d \
        -p 8080:8080 \
        -e DB_URL=jdbc:postgresql://postgres:5432/pathlab \
        -e DB_USERNAME=postgres \
        -e DB_PASSWORD=your_password \
        -e MAIL_USERNAME=your-email@gmail.com \
        -e MAIL_PASSWORD=your-app-password \
        -e JWT_SECRET_BASE64=your-secret \
        pathlab-backend:latest
   ```
**Production Considerations**
* Use environment variables for sensitive configuration
* Configure proper PostgreSQL connection pooling
* Enable HTTPS/TLS for all endpoints
* Set up proper logging and monitoring
* Implement rate limiting for API endpoints
* Use a reverse proxy (Nginx/Apache) in front of the application
* Configure CORS appropriately for frontend integration
* Use a secrets management system for credentials
* Enable audit logging for patient data access

## Roadmap / Future Improvements
* SMS notifications for booking and result notifications
* Integration with payment gateways (Stripe, PayPal, etc.)
* Advanced reporting and analytics
* Multi-language support
* Mobile application integration
* Document storage for patient records
* Automated scheduling for sample collection
* Integration with external lab equipment APIs
* Real-time booking notifications via WebSockets
* Improved caching strategy with Redis

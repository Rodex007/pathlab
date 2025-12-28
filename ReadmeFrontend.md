# Pathology Lab Management System - Frontend

A modern, responsive React-based web application for streamlining pathology laboratory operations. This frontend enables patients, healthcare providers, and laboratory staff to efficiently manage test appointments, sample tracking, results viewing, and administrative tasks.

## 📋 Project Overview

The **Pathology Lab Management System Frontend** is a comprehensive digital solution that bridges the gap between patients, healthcare providers, and laboratory staff. It streamlines and automates pathology laboratory operations while improving patient experience through secure digital access to test results and appointment management.

### Who It's For

- **Patients**: Schedule appointments, browse tests, view results securely, and access medical history
- **Laboratory Staff**: Process samples, manage testing workflows, and generate reports
- **Administrative Personnel**: Manage inventory, handle billing, and monitor operations

### High-Level Goals

- Automate manual laboratory processes and reduce turnaround time
- Minimize human errors in result reporting and data management
- Improve patient experience with digital accessibility and transparency
- Enhance data security and HIPAA compliance
- Enable real-time tracking of sample and test status
- Provide comprehensive analytics and reporting capabilities

## ✨ Key Features

### Patient Portal
- User registration and secure authentication
- Appointment scheduling with calendar interface
- Browse comprehensive test catalog with pricing
- Online payment processing integration
- Secure digital report access and download
- Historical data and test result viewing
- Real-time notification system

### Laboratory Management
- Sample tracking with barcode generation
- Test processing workflow management
- Quality control measures and checkpoints
- Inventory management system
- Equipment maintenance tracking
- Staff scheduling and role-based access

### Administrative Dashboard
- Comprehensive user and staff management
- Financial reporting and analytics
- Business intelligence with charts and metrics
- Audit trail for compliance tracking
- System configuration management
- Document management and archiving

### Reporting System
- Customizable report templates
- Automated PDF and HTML report generation
- Digital signature support
- Bulk report processing capabilities
- Export and sharing functionality

## 🏗️ Architecture Overview

The frontend follows a modular, component-based architecture built with React and TypeScript:
```bash
Frontend Application
├── Pages (Route-based screens)
├── Components (Reusable UI components)
├── API Services (Backend integration)
├── Hooks (Custom React logic)
├── Contexts (State management)
└── Utilities (Helper functions)
```


### Major Directories

- **`src/pages/`** - Full-page components representing different routes and user workflows
- **`src/components/`** - Reusable React components built with Radix UI primitives and Tailwind CSS
- **`src/api/`** - API client utilities and service functions for backend communication
- **`src/hooks/`** - Custom React hooks for form handling, authentication, and data fetching
- **`src/contexts/`** - React Context API for global state management (authentication, user data)
- **`src/lib/`** - Utility functions and helper modules

## 🛠️ Tech Stack

### Frontend
- **Framework**: React 18.3.1 with TypeScript 5.5.3
- **Build Tool**: Vite 7.1.2 (fast HMR and optimized builds)
- **UI Components**: Radix UI (unstyled, accessible primitives)
- **Styling**: Tailwind CSS 3.4.13 with animations
- **Form Management**: React Hook Form 7.53.0 + Zod 3.23.8 (validation)
- **Routing**: React Router DOM 7.8.0
- **State Management**: React Context API
- **HTTP Client**: Fetch API with custom ApiClient wrapper
- **Charts & Analytics**: Recharts 3.1.2
- **Date Handling**: date-fns 3.6.0 + react-datepicker 8.7.0
- **PDF Export**: jsPDF 3.0.2 + html2canvas 1.4.1
- **Animations**: Framer Motion 12.23.12
- **Icons**: Lucide React 0.539.0 + Radix UI Icons
- **Toast Notifications**:  Sonner 1.5.0
- **Code Quality**: ESLint 9.11.1 with TypeScript support

### Development Tools
- **Package Manager**: npm (Node.js)
- **Linting**: ESLint with react-hooks and react-refresh plugins
- **PostCSS**: Autoprefixer and Tailwind CSS processing
- **TypeScript**:  Strict mode with path aliases

## 📁 Project Structure
```bash
pathlab-frontend/
├── src/
│ ├── pages/ # Route-based page components
│ ├── components/ # Reusable UI components
│ ├── api/ # API client and service functions
│ │ ├── index.ts # Base API client and endpoints
│ │ ├── tests.ts # Test management APIs
│ │ └── ... # Other API services
│ ├── hooks/ # Custom React hooks
│ ├── contexts/ # React Context providers
│ ├── lib/ # Utility functions
│ ├── App.tsx # Root component with routing
│ ├── main.tsx # Application entry point
│ ├── index.css # Global styles
│ └── vite-env.d.ts # Vite environment types
├── public/ # Static assets
├── vite.config.ts # Vite build configuration
├── tailwind.config.js # Tailwind CSS configuration
├── tsconfig.json # TypeScript configuration
├── package.json # Dependencies and scripts
├── eslint.config.js # ESLint configuration
└── netlify.toml # Netlify deployment config
```

## 🚀 Getting Started

### Prerequisites

- Node.js 18.x or higher
- npm 9.x or higher (or yarn)
- Backend API running at `https://pathology-lab-backend-new.onrender.com/api`

### Environment Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/CodeInn30/pathology-lab-frontend. git
   cd pathology-lab-frontend
   ```
2. **Install dependencies**
   ```bash
   npm install
   ```
3. **Create environment configuration (if needed)**
   ```bash
   # Copy example environment file
   cp .env. example .env. local
   ```

### Installation Steps

1. **Install all project dependencies**
   ```bash
   npm install
   ```
   
2. **Verify TypeScript compilation**
   ```bash
   npm run build
   ```
   
3. **Start development server**
   ```bash
   npm run dev
   ```

4. **Open in browser Navigate to `http://localhost:5173` (default Vite port)**

## 🔐 Environment Variables

**Create a `.env.local` file in the root directory with the following variables:**
```env
# Backend API Configuration
VITE_API_BASE_URL=https://pathology-lab-backend-new.onrender.com/api

# Authentication
VITE_AUTH_TIMEOUT=3600000

# Feature Flags
VITE_ENABLE_DEMO_MODE=false

# Notification Settings
VITE_TOAST_DURATION=3000

# Application Name
VITE_APP_NAME=Pathology Lab Management System
```

**Note:** All `VITE_` prefixed variables are available in the client-side code. Never expose secrets like API keys in frontend environment variables.

## 💻 Development Workflow

### Running the Development Server
```bash
# Start with hot module replacement
npm run dev
```
The application will be available at `http://localhost:5173` with automatic reload on file changes.

### Available Scripts
```bash
# Start development server with HMR
npm run dev

# Build for production
npm run build

# Preview production build locally
npm run preview

# Run ESLint checks
npm lint
```
### Project Scripts Explained
* dev - Starts Vite development server with fast refresh
* build - Compiles TypeScript and builds optimized production bundle
* lint - Analyzes code for errors and style issues using ESLint
* preview - Serves the built application locally for testing

### Code Quality Standards
* TypeScript strict mode enabled
* ESLint for code style and error detection
* React Hook Form for form validation
* Zod for runtime type checking
* Path aliases configured (@/ → src/)

## 🚢 Deployment Notes

### Frontend Deployment

**The application is configured for deployment on Netlify (see netlify.toml):**

1. Build Command: npm run build
2. Publish Directory: dist/
3. Node Version: 18.x or higher

### Environment Configuration

**Ensure backend API URL is properly configured for each environment:**

* Development: http://localhost:8000/api
* Staging: Backend staging URL
* Production: https://pathology-lab-backend-new.onrender.com/api

### Deployment Checklist

* [ ] Environment variables configured
* [ ] Backend API accessibility verified
* [ ] Production build tested locally (npm run build && npm run preview)
* [ ] TypeScript compilation successful (npm run build)
* [ ] ESLint passes (npm run lint)

## 🗺️ Roadmap & Future Improvements

### Planned Features

1. **Mobile Responsive Enhancements**
   * Progressive Web App (PWA) support
   * Offline functionality with service workers
   * Mobile-optimized dashboards
     
2. Advanced Features
   * Dark mode full implementation
   * Multi-language support (i18n)
   * Real-time notifications with WebSocket
   * Advanced filtering and search capabilities

3. Performance Optimization
   * Code splitting and lazy loading
   * Image optimization
   * API response caching strategies

4. User Experience
   * Interactive tutorials and onboarding
   * Customizable user preferences
   * Accessibility improvements (WCAG 2.1 AA compliance)

# DigitalBoost Pro - Marketing Agency Website

## Overview

This is a modern full-stack web application for DigitalBoost Pro, a digital marketing agency. The application showcases the company's services, portfolio, testimonials, and includes a contact form for lead generation. Built with React, TypeScript, Express.js, and PostgreSQL with Drizzle ORM.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter for client-side routing
- **State Management**: TanStack Query (React Query) for server state management
- **UI Framework**: Shadcn/ui components with Radix UI primitives
- **Styling**: Tailwind CSS with CSS variables for theming
- **Build Tool**: Vite for development and production builds

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **Database**: PostgreSQL with Drizzle ORM
- **Database Provider**: Neon Database (serverless PostgreSQL)
- **Validation**: Zod for schema validation
- **Session Management**: Ready for session-based authentication with PostgreSQL session store

### Development Environment
- **Runtime**: Node.js with ESM modules
- **Development**: tsx for TypeScript execution
- **Hot Reload**: Vite HMR in development mode
- **Error Handling**: Runtime error overlay for development

## Key Components

### Database Schema (shared/schema.ts)
- **Users Table**: Basic user management (id, username, password)
- **Contacts Table**: Lead capture (name, email, phone, service, message, timestamp)
- **Testimonials Table**: Customer testimonials (name, title, company, message, rating, image)

### API Routes (server/routes.ts)
- `POST /api/contact` - Contact form submission with validation
- `GET /api/contacts` - Retrieve all contacts (admin functionality)
- `GET /api/testimonials` - Public testimonials display

### Frontend Pages
- **Home Page**: Single-page application with multiple sections
  - Hero section with call-to-action
  - Services showcase (Web Development, Social Media, Google Business)
  - Portfolio examples
  - Customer testimonials
  - Pricing packages
  - About section
  - Contact form
  - Footer with social links

### Storage Layer
- **Production**: PostgreSQL with Drizzle ORM
- **Development**: In-memory storage implementation with pre-seeded data
- **Interface**: IStorage abstraction for easy switching between implementations

## Data Flow

1. **Contact Form Submission**:
   - Client validates form data using Zod schema
   - Data sent to `/api/contact` endpoint
   - Server validates and stores in database
   - Success/error response displayed via toast notifications

2. **Testimonials Display**:
   - Client fetches testimonials from `/api/testimonials`
   - React Query manages caching and loading states
   - Testimonials rendered with ratings and customer photos

3. **Navigation**:
   - Smooth scrolling between page sections
   - Responsive mobile navigation with hamburger menu
   - Fixed header with brand and navigation links

## External Dependencies

### UI Components
- Radix UI primitives for accessible components
- Lucide React for icons
- React Icons for additional icons (Google, social media)

### Form Management
- React Hook Form for form state management
- Hookform resolvers for Zod integration

### Database & Backend
- Neon Database for serverless PostgreSQL
- Drizzle ORM for type-safe database operations
- Connect-pg-simple for PostgreSQL session storage

### Development Tools
- Tailwind CSS for utility-first styling
- PostCSS for CSS processing
- ESBuild for production bundling

## Deployment Strategy

### Build Process
1. **Frontend**: Vite builds React app to `dist/public`
2. **Backend**: ESBuild bundles Express server to `dist/index.js`
3. **Database**: Drizzle migrations in `migrations/` directory

### Environment Configuration
- `DATABASE_URL` required for PostgreSQL connection
- `NODE_ENV` determines development vs production mode
- Vite serves frontend in development, Express serves static files in production

### Production Setup
- Express server serves both API routes and static frontend files
- Database migrations applied via `npm run db:push`
- Session-based authentication ready for implementation
- Error handling middleware for API routes

### Development Workflow
- `npm run dev` starts development server with hot reload
- Vite dev server proxies API requests to Express
- In-memory storage used when database not configured
- TypeScript checking via `npm run check`

The application is designed as a professional marketing website with lead generation capabilities, built with modern web technologies and ready for production deployment.
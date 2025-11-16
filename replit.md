# SpeedX Delivery App

## Overview

SpeedX is a hyperlocal delivery app focused on facilitating item transport between senders and receivers within defined urban areas, specifically designed for the Ugandan market with pricing in Ugandan Shillings (UGX). Unlike e-commerce platforms, SpeedX operates purely as a delivery logistics service, connecting users who need items delivered with verified drivers who provide the transportation. The application emphasizes security through mandatory driver verification including photo uploads, document verification, and AI-powered facial recognition to prevent fraud.

## User Preferences

Preferred communication style: Simple, everyday language.
Vehicle branding: Universal vehicle icons including motorcycle, motorbike, and car options for comprehensive delivery coverage.

## Recent Changes

**January 3, 2025**
- ✅ Added delivery scheduling functionality - senders can now schedule deliveries for future times
- ✅ Added driver pairing feature - senders can choose from previous drivers they've used
- Updated database schema with `scheduledFor` and `preferredDriverId` fields
- Enhanced delivery status tracking to include "scheduled" status
- Improved UI with scheduling controls and driver selection dropdown

## System Architecture

### Frontend Architecture
- **Framework**: React with TypeScript using Vite as the build tool
- **UI Library**: Shadcn/ui components built on Radix UI primitives
- **Styling**: Tailwind CSS with CSS variables for theming and dark mode support
- **State Management**: TanStack Query (React Query) for server state management
- **Routing**: Wouter for client-side routing
- **Forms**: React Hook Form with Zod validation
- **Design System**: Component-based architecture with consistent design tokens

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **Database ORM**: Drizzle ORM with PostgreSQL dialect
- **Session Management**: Express sessions with PostgreSQL store
- **File Handling**: Multer for file uploads (photos, documents)
- **API Design**: RESTful endpoints with JSON responses
- **Error Handling**: Centralized error middleware with structured responses

### Authentication & Authorization
- **Provider**: Replit OpenID Connect (OIDC) integration
- **Session Storage**: PostgreSQL-backed sessions with configurable TTL
- **Role-Based Access**: Users differentiated by roles (sender, driver, admin)
- **Security**: Passport.js strategy with automatic session management

### Database Schema Design
- **Users Table**: Core user profiles with role-based differentiation
- **Drivers Table**: Extended driver profiles with verification data and status tracking
- **Deliveries Table**: Delivery requests with status tracking, pricing, scheduling, and driver pairing
  - Added `scheduledFor` timestamp field for future delivery scheduling
  - Added `preferredDriverId` field for driver pairing requests
  - Enhanced status field to include "scheduled" for future deliveries
- **Driver Locations**: Real-time location tracking for active drivers
- **Sessions**: Secure session storage for authentication state

### File Upload & Storage
- **Upload Handling**: Multer middleware with file type validation (JPEG, PNG, PDF)
- **Storage Strategy**: Local file system with configurable upload directory
- **Validation**: File size limits (5MB) and MIME type checking
- **Security**: File extension validation to prevent malicious uploads

### Payment Integration
- **Provider**: Stripe payment processing configured for Ugandan Shillings (UGX)
- **Currency**: All pricing and payments in UGX with conversion rate ~3700 UGX = 1 USD
- **Architecture**: Client-side payment collection with server-side confirmation
- **Components**: React Stripe.js components for secure payment forms
- **Flow**: Payment intent creation, client confirmation, and webhook handling

### AI & Automation Features
- **Facial Recognition**: Planned integration for driver photo verification
- **Route Optimization**: Map API integration for delivery route planning
- **Chatbot**: OpenAI API integration for customer support automation
- **GPS Photo Tracking**: Location data captured with delivery photos for verification
- **Camera Integration**: In-app photo capture with device camera for before/after delivery documentation

## External Dependencies

### Database & Storage
- **Neon PostgreSQL**: Serverless PostgreSQL database with connection pooling
- **Drizzle Kit**: Database migration and schema management tools

### Authentication
- **Replit Auth**: OpenID Connect provider for user authentication
- **Passport.js**: Authentication middleware with strategy pattern

### Payment Processing
- **Stripe**: Payment processing with React components and webhook support
- **Payment Methods**: Credit cards and mobile payment integration

### UI & Styling
- **Radix UI**: Accessible component primitives for complex UI patterns
- **Tailwind CSS**: Utility-first CSS framework with design system integration
- **Lucide React**: Icon library for consistent iconography

### Development Tools
- **Vite**: Fast build tool with HMR and development server
- **TypeScript**: Type safety across frontend and backend
- **ESBuild**: Production bundling for server-side code
- **PostCSS**: CSS processing with Tailwind integration

### File & Media Handling
- **Multer**: Multipart form data and file upload handling
- **File System**: Node.js fs promises for file operations

### Future Integrations
- **Map Services**: Google Maps or Mapbox for location and routing
- **AI Services**: OpenAI API for chatbot functionality
- **Image Recognition**: Face comparison libraries for driver verification
- **Push Notifications**: Real-time delivery updates and notifications
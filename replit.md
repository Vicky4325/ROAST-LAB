# Resume Roaster - AI-Powered Resume Feedback Application

## Overview

Resume Roaster is a full-stack web application that provides AI-powered resume feedback with a humorous twist. Instead of traditional constructive criticism, the application "roasts" resumes to provide entertaining yet valuable feedback across different intensity levels (mild, medium, savage). The system analyzes documents section by section and provides detailed feedback with scoring and improvement suggestions.

## User Preferences

Preferred communication style: Simple, everyday language.

## Recent Changes (January 2025)

- **Google API Integration**: Successfully integrated GOOGLE_API_KEY for Gemini AI service
- **Session Management**: Fixed TypeScript session errors and added PostgreSQL session storage
- **Document Management**: Implemented auto-selection of documents and improved sidebar functionality
- **Auto-save System**: Fixed content synchronization and real-time saving
- **Production Ready**: Added comprehensive README, deployment guide, and environment setup files
- **GitHub Integration**: Created complete documentation for repository setup and deployment

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript and JSX
- **Routing**: Wouter for lightweight client-side routing
- **UI Components**: Shadcn/ui components built on Radix UI primitives
- **Styling**: Tailwind CSS with CSS custom properties for theming
- **State Management**: React Context for authentication + TanStack Query for server state
- **Build Tool**: Vite with ES modules and hot module replacement
- **File Structure**: Organized with clear separation between components, pages, hooks, and utilities

### Backend Architecture
- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript with ES modules
- **Database**: PostgreSQL with Drizzle ORM for type-safe queries
- **Authentication**: Session-based authentication using express-session with PostgreSQL session storage
- **AI Integration**: Google Gemini AI for document analysis and feedback generation
- **File Processing**: Base64 encoding for document content storage

## Key Components

### Database Schema
The application uses four main tables:
- **Users**: Stores user authentication and profile information
- **Documents**: Contains user documents with metadata and Base64-encoded content
- **Document Sections**: Granular section-level content for detailed editing
- **Roast Sessions**: AI analysis results with feedback, scoring, and roast content

### AI Service Integration
- **Multi-level Analysis**: Supports mild, medium, and savage feedback intensities
- **Section-by-Section Analysis**: Individual scoring and feedback for each document section
- **Structured Feedback**: Categorized feedback types (success, warning, error, suggestion)
- **Comprehensive Scoring**: Overall document scoring with detailed breakdowns

### Authentication System
- Session-based authentication with secure HTTP-only cookies
- Password hashing using bcryptjs
- Session storage in PostgreSQL using connect-pg-simple
- Protected routes with middleware authentication checks

## Data Flow

1. **User Authentication**: Session-based login with secure cookie management
2. **Document Management**: CRUD operations for user documents with auto-save functionality
3. **Content Editing**: Real-time document editing with debounced auto-save
4. **AI Analysis**: Document content sent to Google Gemini API for analysis
5. **Feedback Display**: Structured feedback presentation with visual indicators
6. **State Management**: TanStack Query for optimistic updates and efficient caching

## External Dependencies

### Core Dependencies
- **@google/genai**: Google Gemini AI integration for document analysis
- **@neondatabase/serverless**: PostgreSQL database driver optimized for serverless environments
- **drizzle-orm**: Type-safe database ORM with migration support
- **express-session**: Session management middleware
- **bcryptjs**: Password hashing and verification
- **@tanstack/react-query**: Server state management and caching
- **wouter**: Lightweight React router

### UI Dependencies
- **@radix-ui/***: Accessible UI primitives for complex components
- **tailwindcss**: Utility-first CSS framework
- **class-variance-authority**: Type-safe variant handling for components
- **lucide-react**: Icon library

## Deployment Strategy

### Development Environment
- **Platform**: Replit with Node.js 20, Web, and PostgreSQL 16 modules
- **Development Server**: Vite dev server with HMR and middleware integration
- **Database Management**: Drizzle Kit for schema migrations and management
- **Environment Variables**: DATABASE_URL, SESSION_SECRET, GEMINI_API_KEY

### Build Configuration
- **Frontend Build**: Vite builds React app to dist/public
- **Backend Build**: ESBuild bundles server code to dist/index.js
- **Database**: PostgreSQL with automatic migration support
- **Session Storage**: PostgreSQL-backed session storage for scalability

### Key Features
- **Auto-save**: Debounced content saving with visual status indicators
- **Dark Mode**: System-wide dark mode support with localStorage persistence
- **Responsive Design**: Mobile-first responsive layout
- **Real-time Feedback**: Live document preview and AI feedback integration
- **Type Safety**: End-to-end TypeScript with shared schema definitions
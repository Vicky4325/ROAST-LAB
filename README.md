# ROAST-LAB
# Resume Roasting Lab - Full-Stack Application

## Overview

This is a full-stack web application that provides AI-powered resume feedback with a humorous twist. Instead of traditional constructive criticism, the application "roasts" resumes to provide entertaining yet helpful feedback to improve professional documents. The system supports multiple document types (resumes, cover letters, LinkedIn profiles, GitHub READMEs) and offers different levels of feedback intensity.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter for client-side routing
- **UI Components**: Shadcn/ui components with Radix UI primitives
- **Styling**: Tailwind CSS with custom CSS variables
- **State Management**: React Context + TanStack Query for server state
- **Build Tool**: Vite with ESM modules

### Backend Architecture
- **Runtime**: Node.js 20 with Express.js
- **Language**: TypeScript with ES modules
- **Database**: PostgreSQL with Drizzle ORM
- **Authentication**: Session-based (connect-pg-simple for session storage)
- **AI Integration**: Google Gemini AI (@google/genai) for document analysis
- **File Processing**: Base64 encoding for document storage

### Development Environment
- **Platform**: Replit with Node.js 20, Web, and PostgreSQL 16 modules
- **Hot Reload**: Vite development server with HMR
- **Database Migrations**: Drizzle Kit for schema management

## Key Components

### Database Schema
- **Users Table**: User authentication and profile management
- **Documents Table**: Stores user documents with metadata and content
- **Document Sections Table**: Granular section-level content and feedback
- **Roast Sessions Table**: AI analysis sessions with feedback and scoring

### AI Service Integration
- **Multi-level Roasting**: Mild, Medium, and Savage feedback modes
- **Section Analysis**: Individual section scoring and feedback
- **Document Analysis**: Comprehensive document evaluation
- **Structured Feedback**: Categorized feedback (success, warning, error, suggestion)

### Frontend Features
- **Document Type Selector**: Support for multiple document types
- **Section Navigator**: Hierarchical document editing interface
- **Live Preview**: Real-time document rendering
- **Feedback Panel**: AI-generated feedback display with visual indicators
- **Auto-save**: Automatic content persistence with status indicators

## Data Flow

1. **User Authentication**: Session-based authentication with PostgreSQL session storage
2. **Document Upload**: Base64 encoding and storage in PostgreSQL
3. **Section Parsing**: Document content split into editable sections
4. **AI Analysis**: Real-time AI feedback using Google Gemini API
5. **Live Updates**: TanStack Query for optimistic updates and caching
6. **Auto-save**: Debounced content saving with visual feedback

## External Dependencies

### Core Dependencies
- **@google/genai**: AI analysis and feedback generation
- **@neondatabase/serverless**: PostgreSQL database driver
- **drizzle-orm**: Type-safe database queries and migrations
- **@tanstack/react-query**: Server state management and caching
- **connect-pg-simple**: PostgreSQL session storage

### UI Dependencies
- **@radix-ui/***: Accessible UI primitives (30+ components)
- **tailwindcss**: Utility-first CSS framework
- **class-variance-authority**: Type-safe component variants
- **lucide-react**: Icon library

### Development Dependencies
- **vite**: Build tool and development server
- **tsx**: TypeScript execution for Node.js
- **esbuild**: Fast JavaScript bundler for production

## Deployment Strategy

### Development
- **Command**: `npm run dev` - Runs Express server with Vite middleware
- **Port**: 5000 (mapped to external port 80)
- **Hot Reload**: Enabled via Vite HMR and server restart

### Production Build
- **Frontend**: Vite builds React app to `dist/public`
- **Backend**: ESBuild bundles Node.js server to `dist/index.js`
- **Database**: Drizzle migrations via `npm run db:push`

### Environment Configuration
- **Database**: PostgreSQL connection via `DATABASE_URL`
- **AI Service**: Google Gemini API key via `GEMINI_API_KEY`
- **Sessions**: PostgreSQL-based session storage

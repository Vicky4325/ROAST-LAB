# Resume Roaster 🔥

An AI-powered resume feedback application that provides humorous yet constructive criticism to help improve your professional documents. Built with React, Express, PostgreSQL, and Google Gemini AI.

## Features

- **AI-Powered Feedback**: Get detailed resume analysis with three intensity levels (mild, medium, savage)
- **Real-time Editing**: Live document editing with auto-save functionality
- **Section-by-Section Analysis**: Detailed feedback for each resume section
- **Multiple Document Types**: Support for resumes, cover letters, LinkedIn profiles, and GitHub READMEs
- **Dark Mode**: Full dark mode support with system preference detection
- **User Authentication**: Secure session-based authentication
- **Responsive Design**: Mobile-first responsive layout

## Tech Stack

### Frontend
- **React 18** with TypeScript
- **Tailwind CSS** for styling
- **Shadcn/ui** components
- **Wouter** for routing
- **TanStack Query** for state management
- **Vite** for build tooling

### Backend
- **Node.js 20** with Express
- **TypeScript** with ES modules
- **PostgreSQL** with Drizzle ORM
- **Google Gemini AI** for document analysis
- **Session-based authentication**

## Getting Started

### Prerequisites

- Node.js 20 or higher
- PostgreSQL database
- Google Gemini API key

### Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/resume-roaster.git
cd resume-roaster
```

2. Install dependencies:
```bash
npm install
```

3. Set up environment variables:
```bash
cp .env.example .env
```

Edit `.env` with your configuration:
```
DATABASE_URL=your_postgresql_connection_string
GOOGLE_API_KEY=your_google_gemini_api_key
SESSION_SECRET=your_session_secret_key
```

4. Set up the database:
```bash
npm run db:push
```

5. Start the development server:
```bash
npm run dev
```

The application will be available at `http://localhost:5000`

## API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user
- `POST /api/auth/logout` - Logout user
- `GET /api/auth/me` - Get current user

### Documents
- `GET /api/documents` - Get user documents
- `POST /api/documents` - Create new document
- `GET /api/documents/:id` - Get specific document
- `PUT /api/documents/:id` - Update document
- `DELETE /api/documents/:id` - Delete document

### AI Feedback
- `POST /api/documents/:id/roast` - Generate AI feedback
- `GET /api/documents/:id/roasts` - Get feedback history

## Project Structure

```
├── client/                 # React frontend
│   ├── src/
│   │   ├── components/     # UI components
│   │   ├── hooks/          # Custom React hooks
│   │   ├── lib/            # Utility functions
│   │   └── pages/          # Page components
├── server/                 # Express backend
│   ├── services/           # External service integrations
│   ├── db.ts              # Database configuration
│   ├── routes.ts          # API routes
│   └── storage.ts         # Database operations
├── shared/                 # Shared types and schemas
│   └── schema.ts          # Database schema and types
└── package.json
```

## Development

### Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run db:push` - Push database schema changes
- `npm run db:studio` - Open database studio

### Database Schema

The application uses four main tables:
- **users** - User authentication and profiles
- **documents** - Document storage with metadata
- **document_sections** - Granular content sections
- **roast_sessions** - AI feedback results

## Deployment

### Environment Variables
Ensure these are set in your production environment:
- `DATABASE_URL` - PostgreSQL connection string
- `GOOGLE_API_KEY` - Google Gemini API key
- `SESSION_SECRET` - Session encryption key

### Build Commands
```bash
npm run build
npm start
```

## Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Make your changes
4. Commit: `git commit -m 'Add some feature'`
5. Push: `git push origin feature-name`
6. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

If you encounter any issues or have questions, please open an issue on GitHub.
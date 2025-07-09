# Deployment Guide

This guide covers deploying the Resume Roaster application to various platforms.

## GitHub Repository Setup

### 1. Create a New Repository

1. Go to GitHub and create a new repository
2. Name it `resume-roaster` or your preferred name
3. Keep it public or private based on your preference
4. Don't initialize with README (we have one)

### 2. Push to GitHub

```bash
# Initialize git repository
git init

# Add all files
git add .

# Initial commit
git commit -m "Initial commit: Resume Roaster application"

# Add remote origin
git remote add origin https://github.com/yourusername/resume-roaster.git

# Push to GitHub
git push -u origin main
```

## Environment Variables

Make sure to set these in your deployment environment:

```bash
DATABASE_URL=postgresql://username:password@host:port/database
GOOGLE_API_KEY=your_google_gemini_api_key
SESSION_SECRET=your_session_secret_key
NODE_ENV=production
PORT=5000
```

## Platform-Specific Deployment

### Vercel Deployment

1. Install Vercel CLI:
```bash
npm i -g vercel
```

2. Deploy:
```bash
vercel --prod
```

3. Configure environment variables in Vercel dashboard
4. Add PostgreSQL database (Vercel Postgres or external)

### Railway Deployment

1. Install Railway CLI:
```bash
npm install -g @railway/cli
```

2. Login and deploy:
```bash
railway login
railway init
railway add --service postgresql
railway deploy
```

3. Set environment variables in Railway dashboard

### Docker Deployment

1. Create Dockerfile:
```dockerfile
FROM node:20-alpine

WORKDIR /app

COPY package*.json ./
RUN npm ci --only=production

COPY . .
RUN npm run build

EXPOSE 5000

CMD ["npm", "start"]
```

2. Build and run:
```bash
docker build -t resume-roaster .
docker run -p 5000:5000 -e DATABASE_URL=your_db_url -e GOOGLE_API_KEY=your_key resume-roaster
```

### Heroku Deployment

1. Install Heroku CLI and login
2. Create app:
```bash
heroku create your-app-name
heroku addons:create heroku-postgresql:hobby-dev
```

3. Set environment variables:
```bash
heroku config:set GOOGLE_API_KEY=your_key
heroku config:set SESSION_SECRET=your_secret
```

4. Deploy:
```bash
git push heroku main
```

## Database Setup

### PostgreSQL Setup

1. Create database and user
2. Run migrations:
```bash
npm run db:push
```

3. Verify tables are created:
- users
- documents
- document_sections
- roast_sessions
- sessions

### Database Migrations

The application uses Drizzle ORM. To update schema:

1. Modify `shared/schema.ts`
2. Run: `npm run db:push`
3. Verify changes in database

## Production Considerations

### Security
- Use strong SESSION_SECRET
- Enable HTTPS in production
- Set secure cookie flags
- Implement rate limiting

### Performance
- Enable compression
- Use CDN for static assets
- Implement caching
- Monitor API usage

### Monitoring
- Set up error tracking (Sentry)
- Monitor database performance
- Track API response times
- Set up health checks

## Troubleshooting

### Common Issues

1. **Database Connection**
   - Check DATABASE_URL format
   - Verify database is accessible
   - Check firewall settings

2. **API Key Issues**
   - Verify GOOGLE_API_KEY is correct
   - Check API quota limits
   - Ensure API is enabled

3. **Session Issues**
   - Check SESSION_SECRET is set
   - Verify session table exists
   - Check cookie settings

### Logs

Check application logs for errors:
```bash
# Heroku
heroku logs --tail

# Railway
railway logs

# Docker
docker logs container_name
```

## Backup Strategy

### Database Backup
```bash
# PostgreSQL backup
pg_dump $DATABASE_URL > backup.sql

# Restore
psql $DATABASE_URL < backup.sql
```

### Automated Backups
Set up automated database backups based on your hosting provider's options.
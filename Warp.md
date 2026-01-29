# Warp Configuration - Acquisitions API

This is a Node.js/Express API project for acquisitions management with authentication, using Drizzle ORM and PostgreSQL.

## Project Overview

- **Framework**: Express.js (v5.2.1)
- **Language**: JavaScript (ES6 modules)
- **Database**: PostgreSQL with Drizzle ORM
- **Authentication**: JWT with bcrypt
- **Logging**: Winston + Morgan
- **Linting**: ESLint + Prettier
- **Package Manager**: npm

## Quick Start Commands

### Development
```bash
# Start development server with auto-reload
npm run dev

# Database operations
npm run db:generate    # Generate migrations
npm run db:migrate     # Run migrations
npm run db:studio      # Open Drizzle Studio

# Code quality
npm run lint           # Run ESLint
npm run lint:fix       # Fix ESLint issues
npm run format         # Format with Prettier
npm run format:check   # Check formatting
```

### Environment Setup
```bash
# Copy environment template
cp .env.example .env

# Edit environment variables
nano .env
```

## Project Structure

```
src/
├── app.js                 # Express app configuration
├── index.js               # Entry point
├── server.js              # Server startup
├── config/
│   ├── database.js        # Database connection
│   └── logger.js          # Winston logger config
├── controllers/
│   └── auth.controller.js # Authentication endpoints
├── middleware/            # Custom middleware
├── models/
│   └── user.model.js      # User model (Drizzle)
├── routes/
│   └── auth.routes.js     # Authentication routes
├── services/
│   └── auth.service.js    # Authentication business logic
├── utils/
│   ├── cookies.js         # Cookie utilities
│   ├── format.js          # Formatting utilities
│   └── jwt.js             # JWT utilities
└── validations/
    └── auth.validation.js # Zod validation schemas
```

## Import Aliases

The project uses Node.js import maps for clean imports:

- `#config/*` → `./src/config/*`
- `#controllers/*` → `./src/controllers/*`
- `#middleware/*` → `./src/middleware/*`
- `#models/*` → `./src/models/*`
- `#routes/*` → `./src/routes/*`
- `#services/*` → `./src/services/*`
- `#utils/*` → `./src/utils/*`
- `#validations/*` → `./src/validations/*`

## API Endpoints

### Health & Status
- `GET /` - Welcome message
- `GET /health` - Health check with uptime
- `GET /api` - API status

### Authentication
- `POST /api/auth/*` - Authentication endpoints (see `src/routes/auth.routes.js`)

## Key Dependencies

### Runtime
- `express` - Web framework
- `@neondatabase/serverless` - Neon PostgreSQL driver
- `drizzle-orm` - Type-safe ORM
- `jsonwebtoken` - JWT authentication
- `bcrypt` - Password hashing
- `zod` - Runtime validation
- `winston` + `morgan` - Logging
- `helmet` - Security headers
- `cors` - CORS handling
- `cookie-parser` - Cookie parsing

### Development
- `eslint` + `prettier` - Code quality
- `drizzle-kit` - Database migrations

## Common Development Tasks

### Database
```bash
# Reset database (if needed)
npm run db:generate && npm run db:migrate

# View database in browser
npm run db:studio
```

### Debugging
```bash
# Start with Node.js inspector
node --inspect --watch src/index.js

# View logs
tail -f logs/*.log
```

### Code Quality
```bash
# Full code quality check
npm run lint && npm run format:check

# Auto-fix issues
npm run lint:fix && npm run format
```

## Environment Variables

Required variables (see `.env.example`):
- `PORT` - Server port (default: 3000)
- `NODE_ENV` - Environment (development/production)
- `LOG_LEVEL` - Logging level
- `DATABASE_URL` - PostgreSQL connection string

## Logging

- **Development**: Console + file logging
- **Production**: Structured JSON logs
- **HTTP**: Morgan logs all requests
- **Location**: `logs/` directory

## Security Features

- Helmet.js for security headers
- CORS configuration
- JWT authentication
- Password hashing with bcrypt
- Input validation with Zod

## Testing

No test framework currently configured. Consider adding:
- Jest for unit testing
- Supertest for API testing
- Test database setup

## Deployment Considerations

- Uses ES6 modules (`"type": "module"`)
- Environment-based configuration
- PostgreSQL database required
- Node.js 18+ recommended
- Consider PM2 for production process management

## Git Configuration

- Main branch: `main`
- Ignored: `node_modules/`, `.env.*`, `logs/`, `drizzle/`
- ESLint ignores same directories
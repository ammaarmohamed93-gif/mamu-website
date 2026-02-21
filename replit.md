# MAMU - Muslim Association of Meru University

## Overview

MAMU is a full-stack web application for the Muslim Association of Meru University. It serves as a community platform for Muslim students, providing features for membership management, event scheduling, and resource sharing. The application uses a modern React frontend with an Express backend, PostgreSQL database, and Replit's OpenID Connect authentication system.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter (lightweight React router)
- **State Management**: TanStack Query (React Query) for server state
- **Styling**: Tailwind CSS with shadcn/ui components (New York style)
- **Animations**: Framer Motion for page transitions and UI effects
- **Forms**: React Hook Form with Zod validation
- **Build Tool**: Vite with custom plugins for Replit integration

The frontend follows a page-based architecture with shared components. Key pages include Home, About, Members, Events, and Resources. The UI uses a custom "Modern Fluid" theme with cream backgrounds and dark green accents, featuring the Amiri display font and Outfit body font.

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **Database ORM**: Drizzle ORM with PostgreSQL
- **Authentication**: Replit OpenID Connect (OIDC) with Passport.js
- **Session Management**: express-session with connect-pg-simple for PostgreSQL session storage
- **API Design**: RESTful endpoints defined in shared/routes.ts with Zod schema validation

The backend uses a storage abstraction layer (DatabaseStorage class) for data access operations. Routes are registered in server/routes.ts with authentication middleware where needed.

### Data Models
- **Users**: Managed by Replit Auth (id, email, firstName, lastName, profileImageUrl)
- **Profiles**: Extended user data (course, phoneNumber, isAdmin) linked to users
- **Events**: Community events with title, description, date, and location
- **Resources**: Shared materials with type (pdf/link) and URL

### Shared Code
The `shared/` directory contains code used by both frontend and backend:
- `schema.ts`: Drizzle table definitions and Zod schemas
- `routes.ts`: API route definitions with input/output types
- `models/auth.ts`: Authentication-related table definitions

### Build System
Custom build script using esbuild for server bundling and Vite for client. The build process bundles specific server dependencies to reduce cold start times on Replit.

## External Dependencies

### Database
- **PostgreSQL**: Primary database via `DATABASE_URL` environment variable
- **Drizzle Kit**: Database migrations stored in `/migrations`

### Authentication
- **Replit OIDC**: OpenID Connect authentication via `ISSUER_URL`
- **Session Secret**: `SESSION_SECRET` environment variable required

### Key NPM Packages
- `@tanstack/react-query`: Server state management
- `drizzle-orm` / `drizzle-zod`: Database ORM and validation
- `passport` / `openid-client`: Authentication
- `framer-motion`: Animations
- `date-fns`: Date formatting
- Full shadcn/ui component library (Radix UI primitives)

### Development Tools
- `@replit/vite-plugin-runtime-error-modal`: Error overlay
- `@replit/vite-plugin-cartographer`: Replit integration
- TypeScript with strict mode enabled
# Campbell Biology Study Tracker

## Overview

This is a full-stack study progress tracking application designed to help students work through the Campbell Biology textbook curriculum. The application presents a hierarchical structure of units, chapters, concepts, and topics that students can mark as complete to track their learning progress.

The core functionality allows users to:
- Browse the curriculum organized by units and chapters
- View concepts and their associated study topics
- Toggle topic completion status with progress tracking
- See visual progress indicators at multiple levels (unit, chapter, concept)

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter (lightweight router)
- **State Management**: TanStack React Query for server state
- **UI Components**: shadcn/ui component library built on Radix UI primitives
- **Styling**: Tailwind CSS with CSS variables for theming
- **Animations**: Framer Motion for smooth transitions
- **Build Tool**: Vite

The frontend follows a component-based architecture with:
- Pages in `client/src/pages/` (Home, NotFound)
- Reusable components in `client/src/components/`
- Custom hooks in `client/src/hooks/` for data fetching and utilities
- UI primitives from shadcn/ui in `client/src/components/ui/`

### Backend Architecture
- **Runtime**: Node.js with TypeScript
- **Framework**: Express.js
- **Database ORM**: Drizzle ORM
- **Database**: PostgreSQL
- **API Pattern**: RESTful endpoints defined in shared route contracts

The server uses a layered architecture:
- `server/index.ts` - Express app setup and middleware
- `server/routes.ts` - API route handlers
- `server/storage.ts` - Data access layer with database operations
- `server/db.ts` - Database connection pool

### Data Model
The curriculum is organized in a four-level hierarchy:
1. **Units** - Top-level groupings (e.g., "Chemistry of Life")
2. **Chapters** - Subdivisions of units
3. **Concepts** - Key learning objectives within chapters
4. **Topics** - Individual study items that can be marked complete

### Shared Code
- `shared/schema.ts` - Drizzle table definitions and TypeScript types
- `shared/routes.ts` - API contract definitions with Zod validation

### Key Design Decisions

**Type-Safe API Contracts**: The `shared/routes.ts` file defines API endpoints with input/output schemas using Zod, enabling type safety across the full stack.

**Optimistic UI**: The frontend uses React Query mutations with query invalidation for consistent state after topic toggles.

**Seeding Strategy**: The database is seeded with curriculum data on server startup if tables are empty, defined inline in `server/storage.ts`.

## External Dependencies

### Database
- **PostgreSQL** - Primary data store accessed via `DATABASE_URL` environment variable
- **Drizzle ORM** - Type-safe database queries and migrations
- **drizzle-kit** - Migration tooling (run `npm run db:push` to sync schema)

### Frontend Libraries
- **@tanstack/react-query** - Async state management
- **@radix-ui/*** - Accessible UI primitives
- **framer-motion** - Animation library
- **wouter** - Client-side routing
- **lucide-react** - Icon library

### Development Tools
- **Vite** - Development server and build tool
- **TypeScript** - Type checking across the stack
- **Tailwind CSS** - Utility-first styling

### Replit-Specific
- **@replit/vite-plugin-runtime-error-modal** - Error overlay for development
- **@replit/vite-plugin-cartographer** - Development tooling
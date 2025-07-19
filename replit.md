# Multiplayer Game Application

## Overview

This is a real-time multiplayer game application built with React frontend and Express backend. The application appears to be a "Who's the Killer?" style game where players join rooms and play together. It uses WebSockets for real-time communication, Drizzle ORM for database operations, and shadcn/ui components for the user interface.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite for development and production builds
- **UI Framework**: shadcn/ui components built on Radix UI primitives
- **Styling**: Tailwind CSS with custom CSS variables for theming
- **State Management**: TanStack Query for server state management
- **Routing**: Wouter for client-side routing
- **Real-time Communication**: WebSocket connection with custom hook

### Backend Architecture
- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript with ES modules
- **Real-time Communication**: WebSocket Server (ws library)
- **Database**: PostgreSQL with Drizzle ORM (Persistent Database)
- **Database Provider**: Neon serverless database
- **Session Management**: Session storage using connect-pg-simple
- **Storage**: DatabaseStorage class for persistent data (replaced MemStorage)

### Key Components

#### Database Schema
- **Rooms**: Store game room information with codes, host details, and status
- **Players**: Track player information, roles, and connection status
- **Messages**: Handle chat messages and system notifications
- **Users**: User authentication and profile management

#### Real-time Game Features
- Room creation and joining with unique codes
- Player role assignment (killer vs civilian)
- Real-time chat messaging
- Connection status tracking
- Game state synchronization

#### UI Components
- Comprehensive shadcn/ui component library
- Custom game-specific styling with dark theme
- Responsive design with mobile support
- Toast notifications for user feedback

## Data Flow

1. **Room Creation**: Host creates a room, gets unique code, becomes room host
2. **Player Joining**: Players join using room codes, get assigned to room
3. **Game Setup**: When minimum players join, roles are randomly assigned
4. **Real-time Updates**: WebSocket broadcasts game state changes to all players
5. **Chat System**: Messages are stored in database and broadcast to room members

## External Dependencies

### Core Dependencies
- **@neondatabase/serverless**: Serverless PostgreSQL database connection
- **drizzle-orm**: Type-safe database ORM
- **@tanstack/react-query**: Server state management
- **@radix-ui/***: Headless UI components
- **ws**: WebSocket server implementation

### Development Tools
- **Vite**: Build tool and development server
- **TypeScript**: Type safety and development experience
- **Tailwind CSS**: Utility-first CSS framework
- **drizzle-kit**: Database migrations and schema management

## Deployment Strategy

### Build Process
- **Frontend**: Vite builds React app to `dist/public`
- **Backend**: ESBuild bundles server code to `dist/index.js`
- **Database**: Drizzle migrations in `migrations/` directory

### Environment Configuration
- **DATABASE_URL**: PostgreSQL connection string (required)
- **NODE_ENV**: Environment mode (development/production)
- Development includes Vite middleware for hot reloading
- Production serves static files from dist directory

### Development Workflow
- `npm run dev`: Start development server with hot reloading
- `npm run build`: Build both frontend and backend for production
- `npm run db:push`: Push database schema changes
- `npm start`: Start production server

The application follows a monorepo structure with shared schema between frontend and backend, enabling type safety across the full stack. The WebSocket implementation provides real-time game functionality while the PostgreSQL database ensures persistent game state and chat history across server restarts.

## Recent Changes (January 2025)
- **Database Migration**: Replaced in-memory storage with persistent PostgreSQL database
- **Storage Implementation**: Created DatabaseStorage class using Drizzle ORM
- **Data Persistence**: All game rooms, players, messages, votes, and game rounds now persist across server restarts
- **Database Schema**: Successfully pushed schema to production database with all required tables
- **UptimeRobot Integration**: Added /api/ping and /api/health endpoints for continuous uptime monitoring
- **Error Handling**: Enhanced WebSocket and database error handling for production stability
- **Deployment Ready**: App configured for production deployment with proper API routing
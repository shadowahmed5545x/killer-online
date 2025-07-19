# Arabic Multiplayer Killer Game

A real-time multiplayer social deduction game "Who is the Killer?" with Arabic language support.

## Features

🎮 **Real-time Multiplayer Gaming**
- WebSocket-based real-time communication
- Room-based gameplay with unique codes
- Role assignment (Killer vs Civilians)
- Voting and elimination system

🗣️ **Arabic Language Support**
- Complete Arabic interface
- Right-to-left text support
- Arabic system messages and notifications

🗄️ **Persistent Database**
- PostgreSQL database with Drizzle ORM
- Persistent game rooms and player data
- Chat history and game state preservation

🔄 **UptimeRobot Integration**
- `/api/ping` and `/api/health` endpoints
- Continuous uptime monitoring
- No-sleep functionality

## Technology Stack

- **Frontend**: React 18 + TypeScript + Vite
- **Backend**: Node.js + Express + WebSocket
- **Database**: PostgreSQL with Drizzle ORM
- **UI**: Tailwind CSS + shadcn/ui components
- **Real-time**: WebSocket Server (ws library)

## Getting Started

### Prerequisites
- Node.js 18+
- PostgreSQL database
- npm or yarn

### Installation

1. **Install dependencies**
   ```bash
   npm install
   ```

2. **Set up environment variables**
   Create a `.env` file:
   ```
   DATABASE_URL=your_postgresql_connection_string
   PORT=5000
   ```

3. **Push database schema**
   ```bash
   npm run db:push
   ```

4. **Start development server**
   ```bash
   npm run dev
   ```

5. **Open in browser**
   Navigate to `http://localhost:5000`

## Game Rules

### Setup
- Players join rooms using unique codes
- Host can start the game with minimum 3 players
- Roles are randomly assigned (1 Killer, rest Civilians)

### Gameplay
- **Day Phase**: Players discuss and vote to eliminate suspects
- **Night Phase**: Killer eliminates one civilian
- **Win Conditions**:
  - Civilians win by eliminating the killer
  - Killer wins by reducing civilians to equal their number

### Features
- Real-time chat during gameplay
- Voting system with majority rules
- Player elimination and role reveal
- Game state persistence across sessions

## API Endpoints

- `GET /api/ping` - Keep-alive endpoint for monitoring
- `GET /api/health` - Health check with database status
- `WebSocket /ws` - Real-time game communication

## UptimeRobot Setup

1. Deploy your app and get the public URL
2. Create UptimeRobot monitor:
   - **URL**: `https://your-app-url.com/api/ping`
   - **Interval**: Every 5 minutes
   - **Type**: HTTP(s)

## Deployment

### Replit Deployment
1. Push code to Replit
2. Click "Deploy" in Replit workspace
3. Configure environment variables
4. App will be available at `yourname.replit.app`

### Manual Deployment
1. **Build the project**
   ```bash
   npm run build
   ```

2. **Start production server**
   ```bash
   npm start
   ```

## Development

### Project Structure
```
├── client/src/           # React frontend
│   ├── components/       # UI components
│   ├── hooks/           # Custom React hooks
│   ├── pages/           # Page components
│   └── lib/             # Utility functions
├── server/              # Express backend
│   ├── routes.ts        # API routes & WebSocket
│   ├── storage.ts       # Database operations
│   └── db.ts           # Database connection
├── shared/              # Shared TypeScript types
└── README.md           # This file
```

### Available Scripts
- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm start` - Start production server
- `npm run db:push` - Push database schema

## Contributing

1. Fork the repository
2. Create feature branch
3. Make your changes
4. Test thoroughly
5. Submit pull request

## License

MIT License - feel free to use this project for your own games!

## Support

For issues or questions, please create an issue in the repository or contact the maintainers.

---

**Happy Gaming! 🎮**
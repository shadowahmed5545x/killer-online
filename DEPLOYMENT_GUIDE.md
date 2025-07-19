# Deployment Guide - Arabic Killer Game

## Quick Deploy Options

### Option 1: Replit Deployment (Recommended)
1. **Upload to Replit**
   - Create new Replit project
   - Upload this ZIP file
   - Wait for automatic setup

2. **Configure Database**
   - Replit will auto-provision PostgreSQL
   - No manual setup needed

3. **Deploy**
   - Click "Deploy" button in Replit
   - Get permanent URL: `yourname.replit.app`
   - App runs 24/7 automatically

### Option 2: Manual Server Deployment

#### Prerequisites
- Node.js 18+
- PostgreSQL database
- Domain/hosting service

#### Steps
1. **Extract files** to your server
2. **Install dependencies**
   ```bash
   npm install
   ```
3. **Configure environment**
   ```bash
   # Create .env file
   DATABASE_URL=postgresql://username:password@host:port/database
   PORT=5000
   NODE_ENV=production
   ```
4. **Setup database**
   ```bash
   npm run db:push
   ```
5. **Build project**
   ```bash
   npm run build
   ```
6. **Start server**
   ```bash
   npm start
   ```

## UptimeRobot Configuration

### After Deployment
1. **Get your app URL** (e.g., `https://yourname.replit.app`)
2. **Create UptimeRobot account** at https://uptimerobot.com
3. **Add New Monitor**:
   - **Monitor Type**: HTTP(s)
   - **Friendly Name**: Arabic Killer Game
   - **URL**: `https://your-app-url.com/api/ping`
   - **Monitoring Interval**: Every 5 minutes
   - **Monitor Timeout**: 30 seconds
   - **HTTP Method**: GET

### Expected Response
```json
{
  "status": "alive",
  "message": "Arabic Killer Game is running",
  "timestamp": "2025-01-18T15:04:00.000Z",
  "uptime": 3600,
  "players_online": 0
}
```

## Environment Variables

### Required
- `DATABASE_URL` - PostgreSQL connection string
- `PORT` - Server port (default: 5000)

### Optional
- `NODE_ENV` - Environment mode (development/production)

## Database Schema

The app uses these tables:
- `users` - User authentication
- `rooms` - Game rooms
- `players` - Player data
- `messages` - Chat messages
- `votes` - Voting data
- `gameRounds` - Game round tracking

Schema is automatically created on first run with `npm run db:push`.

## SSL/HTTPS

For production deployment:
- Use HTTPS for secure WebSocket connections
- Configure SSL certificates
- Update WebSocket URLs in client code if needed

## Performance Tips

1. **Database Connection Pooling**
   - Configured automatically with Neon serverless
   - No manual tuning needed

2. **WebSocket Optimization**
   - Connection cleanup on disconnect
   - Automatic reconnection logic

3. **Memory Management**
   - Persistent database storage
   - Efficient client connection tracking

## Troubleshooting

### Common Issues

1. **Database Connection Error**
   - Check `DATABASE_URL` format
   - Verify database server is running
   - Test connection: `npm run db:push`

2. **WebSocket Connection Failed**
   - Check firewall settings
   - Verify port 5000 is open
   - Test with curl: `curl http://localhost:5000/api/ping`

3. **Build Errors**
   - Clear node_modules: `rm -rf node_modules && npm install`
   - Check Node.js version: `node --version`

### Logs
- Server logs: Console output shows all requests
- Database logs: Check PostgreSQL logs
- WebSocket logs: Connection/disconnection events

## Security Considerations

1. **Environment Variables**
   - Never commit `.env` files
   - Use secure database passwords
   - Restrict database access

2. **Rate Limiting**
   - Consider adding rate limiting for API endpoints
   - Monitor unusual traffic patterns

3. **Input Validation**
   - All inputs are validated with Zod schemas
   - WebSocket messages are sanitized

## Monitoring

### Health Endpoints
- `/api/health` - Database status
- `/api/ping` - Keep-alive with stats

### Metrics to Monitor
- Response times
- Database connection status
- Active player count
- WebSocket connections
- Memory usage

---

**Your Arabic killer game is ready to deploy! 🚀**
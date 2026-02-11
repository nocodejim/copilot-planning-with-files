# Findings: Multi-Feature Web Application

*Last Updated: 2026-02-11*

## Requirements

### Core Requirements
- User registration and authentication
- Real-time chat with multiple rooms
- File upload and storage
- Responsive web interface
- Scalable architecture

### Non-Functional Requirements
- Support 1000+ concurrent users
- Sub-second message latency
- 99.9% uptime
- Secure file storage

## Tech Stack Decisions

### Backend: Node.js + Express
**Chosen:** Express.js
**Why:**
- Team has 2+ years experience
- Large ecosystem of middleware
- Good performance for I/O-bound tasks
- Easy to integrate Socket.io

**Alternatives Considered:**
- FastAPI (Python) — Rejected: Team less familiar
- NestJS — Rejected: Overkill for project scope

### Database: PostgreSQL
**Chosen:** PostgreSQL
**Why:**
- Need ACID transactions (user accounts, payments)
- Complex relationships (users, rooms, messages, files)
- JSON support for flexible data where needed
- Excellent TypeScript support (Prisma ORM)

**Alternatives Considered:**
- MongoDB — Rejected: No transactions, eventual consistency issues
- MySQL — Considered: PostgreSQL has better JSON support

### Authentication: JWT
**Chosen:** JWT (JSON Web Tokens)
**Why:**
- Stateless (no server-side session storage)
- Works across multiple servers (horizontal scaling)
- Mobile-friendly
- Standard: RFC 7519

**Implementation:**
```js
const token = jwt.sign(
  {userId: user.id, email: user.email},
  process.env.JWT_SECRET,
  {expiresIn: '24h'}
);
```

### Real-Time: Socket.io
**Chosen:** Socket.io over raw WebSockets
**Why:**
- Automatic reconnection
- Room/namespace support built-in
- Fallback to long-polling
- Better error handling

**Message Flow:**
1. Client connects → Socket.io handshake
2. Client joins room → Server tracks connection
3. Message sent → Broadcast to room
4. Message persisted → PostgreSQL for history

### File Storage: AWS S3
**Chosen:** AWS S3
**Why:**
- Virtually unlimited storage
- 99.999999999% durability
- CDN integration (CloudFront)
- Pay-per-use pricing

**Upload Flow:**
1. Client requests signed URL
2. Server generates S3 presigned URL (expiry: 5min)
3. Client uploads directly to S3
4. Client notifies server → Save metadata to DB

### Frontend: React
**Chosen:** React
**Why:**
- Component-based architecture
- Large ecosystem (React Router, Material-UI)
- Good TypeScript support
- Team familiar with React hooks

## Architecture Design

```
Client (React)
    ↓
Load Balancer
    ↓
API Server (Express)  ←→  PostgreSQL
    ↓
Socket.io Server  ←→  Redis (pub/sub)
    ↓
AWS S3 (file storage)
```

### Key Patterns
- **Authentication**: JWT in Authorization header
- **Real-time**: Socket.io with Redis adapter for multi-server
- **File uploads**: Direct S3 upload with presigned URLs
- **API**: RESTful endpoints, versioned (/api/v1/)

## Security Considerations

1. **Passwords**: bcrypt with salt rounds = 12
2. **JWT Secret**: 256-bit random key in .env
3. **S3 Access**: IAM roles, not hardcoded keys
4. **SQL Injection**: Parameterized queries (Prisma)
5. **File Uploads**: Whitelist MIME types, scan for malware

## Performance Optimizations

1. **Database**: Connection pooling (max: 20)
2. **Caching**: Redis for session data
3. **File uploads**: Streaming to avoid memory issues
4. **Socket.io**: Redis adapter for horizontal scaling

## Resources & References
- [Express.js docs](https://expressjs.com/)
- [Socket.io docs](https://socket.io/docs/)
- [JWT.io](https://jwt.io/)
- [AWS S3 presigned URLs](https://docs.aws.amazon.com/AmazonS3/latest/userguide/PresignedUrlUploadObject.html)
- [PostgreSQL docs](https://www.postgresql.org/docs/)

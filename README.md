# Full Stack Authentication App

A production-ready authentication system built with React, Node.js, Express, and PostgreSQL.

## 🚀 Features

- **Secure Authentication**: JWT-based authentication with bcrypt password hashing
- **User Management**: Registration, login, profile management
- **Security Features**: Rate limiting, CORS protection, helmet security headers
- **Responsive Design**: Mobile-first design with Tailwind CSS
- **Production Ready**: Optimized for deployment on Vercel
- **Database**: PostgreSQL with connection pooling
- **Error Handling**: Comprehensive error handling and validation

## 📁 Project Structure

```
├── frontend/          # React application
│   ├── src/
│   │   ├── components/    # React components
│   │   ├── utils/         # Utility functions
│   │   ├── context/       # React context
│   │   └── App.js         # Main app component
│   ├── public/            # Static assets
│   └── package.json       # Frontend dependencies
├── backend/           # Node.js API server
│   ├── routes/            # API routes
│   ├── middleware/        # Custom middleware
│   ├── config/            # Configuration files
│   └── server.js          # Main server file
└── README.md
```

## 🛠 Tech Stack

### Frontend
- **React 18** - UI framework
- **React Router** - Client-side routing
- **Tailwind CSS** - Utility-first CSS framework
- **Axios** - HTTP client
- **Vercel** - Hosting platform

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **PostgreSQL** - Database
- **JWT** - Authentication tokens
- **bcryptjs** - Password hashing
- **Helmet** - Security middleware
- **Express Rate Limit** - Rate limiting

## 🚀 Quick Start

### Prerequisites
- Node.js (v16 or higher)
- npm or yarn
- PostgreSQL database

### 1. Clone the repository
```bash
git clone <your-repo-url>
cd auth-app
```

### 2. Backend Setup
```bash
cd backend
npm install

# Create .env file with your configuration
cp .env.example .env

# Update .env with your database URL and JWT secret
DATABASE_URL=your_postgresql_url
JWT_SECRET=your_super_secret_jwt_key
```

### 3. Database Setup
Your PostgreSQL database should have this table:
```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    username VARCHAR(50) UNIQUE NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 4. Frontend Setup
```bash
cd ../frontend
npm install

# Create .env.local file
echo "REACT_APP_API_URL=http://localhost:5000" > .env.local
```

### 5. Run the Application
```bash
# Terminal 1: Start backend
cd backend
npm run dev

# Terminal 2: Start frontend
cd frontend
npm start
```

The app will be available at:
- Frontend: http://localhost:3000
- Backend: http://localhost:5000

## 🚀 Deployment on Vercel

### Deploy Backend

1. Push your backend code to a Git repository
2. Go to [Vercel Dashboard](https://vercel.com/dashboard)
3. Click "New Project" and import your backend repository
4. Configure environment variables:
   - `DATABASE_URL`: Your PostgreSQL connection string
   - `JWT_SECRET`: A secure random string (min 32 characters)
   - `NODE_ENV`: production
   - `FRONTEND_URL`: Your frontend domain (after deploying frontend)

### Deploy Frontend

1. Push your frontend code to a Git repository
2. Go to [Vercel Dashboard](https://vercel.com/dashboard)
3. Click "New Project" and import your frontend repository
4. Configure environment variables:
   - `REACT_APP_API_URL`: Your backend API URL from previous step

### Environment Variables Setup

**Backend (.env):**
```env
DATABASE_URL=postgresql://username:password@host:port/database?sslmode=require
JWT_SECRET=your_super_secret_jwt_key_make_it_long_and_random
NODE_ENV=production
FRONTEND_URL=https://your-frontend-domain.vercel.app
```

**Frontend (.env.production):**
```env
REACT_APP_API_URL=https://your-backend-domain.vercel.app
```

## 🔒 Security Features

- **Password Hashing**: bcrypt with salt rounds of 12
- **JWT Tokens**: Secure token-based authentication with expiration
- **Rate Limiting**: 
  - Auth endpoints: 5 attempts per 15 minutes
  - API endpoints: 100 requests per 15 minutes
- **CORS Protection**: Configured for specific origins
- **Security Headers**: Helmet.js for security headers
- **Input Validation**: Server-side validation for all inputs
- **SQL Injection Protection**: Parameterized queries

## 📝 API Endpoints

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `POST /api/auth/verify` - Verify JWT token
- `POST /api/auth/logout` - User logout

### User Management
- `GET /api/user/profile` - Get user profile
- `PUT /api/user/profile` - Update user profile
- `GET /api/user/stats` - Get user statistics

### System
- `GET /health` - Health check endpoint
- `GET /api/status` - API status

## 🔧 Configuration

### Backend Environment Variables
| Variable | Description | Required |
|----------|-------------|----------|
| DATABASE_URL | PostgreSQL connection string | Yes |
| JWT_SECRET | Secret key for JWT tokens | Yes |
| NODE_ENV | Environment (development/production) | No |
| PORT | Server port (default: 5000) | No |
| FRONTEND_URL | Frontend URL for CORS | No |

### Frontend Environment Variables
| Variable | Description | Required |
|----------|-------------|----------|
| REACT_APP_API_URL | Backend API URL | Yes |

## 🚨 Error Handling

The application includes comprehensive error handling:
- **Client-side**: Error boundaries and try-catch blocks
- **Server-side**: Global error middleware
- **Database**: Connection error handling
- **Network**: Request timeout and retry logic

## 🧪 Testing

```bash
# Backend tests
cd backend
npm test

# Frontend tests
cd frontend
npm test
```

## 📊 Monitoring

### Health Checks
- Backend: `GET /health`
- Database connectivity check included

### Logging
- Development: Detailed console logs
- Production: Structured logging with timestamps

## 🔄 Updates and Maintenance

### Updating Dependencies
```bash
# Backend
cd backend
npm update
npm audit fix

# Frontend
cd frontend
npm update
npm audit fix
```

### Database Migrations
For future schema changes, implement migration scripts in `/backend/migrations/`

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License.

## 🆘 Support

If you encounter any issues:
1. Check the console for error messages
2. Verify environment variables are set correctly
3. Ensure database connectivity
4. Check network requests in browser dev tools

## 🔗 Useful Links

- [React Documentation](https://reactjs.org/docs)
- [Express.js Documentation](https://expressjs.com/)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
- [Vercel Documentation](https://vercel.com/docs)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)

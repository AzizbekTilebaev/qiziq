# Qaraqalpaq Til Platforması - Local Setup Guide

## 🚀 Quick Start

### Backend Setup (Terminal 1)

```powershell
# Navigate to backend folder
cd "C:\Users\aziz\Desktop\projects 2\proyekt\backend"

# Install dependencies
npm install

# Ensure .env file exists
node scripts/ensure-env.js

# Generate Prisma Client
npm run prisma:generate

# Run database migrations
npx prisma migrate dev --name init

# Seed database with test data
npm run prisma:seed

# Start backend server (runs on port 5000)
npm run dev
```

**Backend will run on:** `http://localhost:5000`

**Test credentials:**
- Admin: `admin@qaraqalpaq.uz` / `admin123`
- User: `user@test.uz` / `user123`

### Frontend Setup (Terminal 2)

```powershell
# Navigate to frontend folder
cd "C:\Users\aziz\Desktop\projects 2\proyekt\frontend"

# Install dependencies
npm install

# Start frontend dev server (runs on port 5173)
npm run dev
```

**Frontend will run on:** `http://localhost:5173`

## ✅ Verification Steps

### 1. Test Backend API

Open browser and visit:
- `http://localhost:5000/` - Should show API info
- `http://localhost:5000/api/quizzes` - Should return quiz list
- `http://localhost:5000/api/dictionary` - Should return dictionary entries
- `http://localhost:5000/api/ebooks` - Should return ebook list

### 2. Test Frontend

1. Open `http://localhost:5173` in browser
2. Click "Ro'yxatdan o'tish" (Register)
3. Create account or login with test credentials
4. Navigate to Dashboard
5. Test Quiz, Dictionary, and E-books modules

## 🔧 Troubleshooting

### Backend not starting?

1. Check if port 5000 is available:
   ```powershell
   netstat -ano | findstr :5000
   ```

2. Verify .env file exists:
   ```powershell
   cd backend
   node scripts/ensure-env.js
   ```

3. Check database exists:
   ```powershell
   Test-Path backend\prisma\dev.db
   ```

### Frontend can't connect to backend?

1. Verify backend is running on port 5000
2. Check `frontend/src/services/api.js` has correct API URL:
   ```javascript
   const API_URL = import.meta.env.VITE_API_URL || 'http://localhost:5000/api';
   ```

3. Check browser console for CORS errors
4. Verify backend CORS is enabled (should be in server.js)

### Database errors?

1. Reset database:
   ```powershell
   cd backend
   npm run prisma:reset
   npm run prisma:migrate
   npm run prisma:seed
   ```

## 📁 Project Structure

```
proyekt/
├── backend/
│   ├── src/
│   │   ├── controllers/
│   │   ├── routes/
│   │   ├── middleware/
│   │   └── server.js
│   ├── prisma/
│   │   ├── schema.prisma
│   │   └── seed.js
│   └── package.json
│
└── frontend/
    ├── src/
    │   ├── pages/
    │   ├── components/
    │   ├── services/
    │   └── App.jsx
    └── package.json
```

## 🎯 API Endpoints

### Auth
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user
- `GET /api/auth/profile` - Get user profile (requires JWT)

### Quizzes
- `GET /api/quizzes` - Get all quizzes
- `GET /api/quizzes/:id` - Get quiz by ID
- `POST /api/quizzes/:id/submit` - Submit quiz answers
- `POST /api/quizzes` - Create quiz (Admin only)

### Dictionary
- `GET /api/dictionary` - Get all dictionary entries
- `GET /api/dictionary/search?word=` - Search dictionary
- `POST /api/dictionary` - Add entry (Admin only)

### Ebooks
- `GET /api/ebooks` - Get all ebooks
- `GET /api/ebooks/:id` - Get ebook by ID
- `POST /api/ebooks` - Add ebook (Admin only)

## 📝 Notes

- Backend must be running before starting frontend
- Both servers can run simultaneously
- Database is SQLite (file-based, no separate server needed)
- JWT tokens stored in localStorage
- All API calls include error handling


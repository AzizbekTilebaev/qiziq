# 🚀 Quick Start Guide - Qaraqalpaq Til Platforması

## One-Command Setup (Recommended)

### Option 1: Start Both Servers Automatically
```powershell
.\START_ALL.ps1
```
This will open two PowerShell windows - one for backend, one for frontend.

### Option 2: Manual Setup (Two Terminals)

**Terminal 1 - Backend:**
```powershell
cd backend
.\start-backend.ps1
```

**Terminal 2 - Frontend:**
```powershell
cd frontend
.\start-frontend.ps1
```

## Step-by-Step Manual Setup

### 1️⃣ Backend Setup

```powershell
# Navigate to backend
cd "C:\Users\aziz\Desktop\projects 2\proyekt\backend"

# Install dependencies (if not already installed)
npm install

# Ensure .env file exists
node scripts/ensure-env.js

# Generate Prisma Client
npm run prisma:generate

# Run database migrations
npx prisma migrate dev --name init

# Seed database
npm run prisma:seed

# Start server
npm run dev
```

**Backend runs on:** `http://localhost:5000`

### 2️⃣ Frontend Setup

```powershell
# Navigate to frontend (in a NEW terminal)
cd "C:\Users\aziz\Desktop\projects 2\proyekt\frontend"

# Install dependencies (if not already installed)
npm install

# Start dev server
npm run dev
```

**Frontend runs on:** `http://localhost:5173`

## ✅ Verify Setup

### Test Backend API
```powershell
cd backend
.\test-api.ps1
```

Or manually test in browser:
- `http://localhost:5000/` - API info
- `http://localhost:5000/api/quizzes` - Quiz list
- `http://localhost:5000/api/dictionary` - Dictionary entries
- `http://localhost:5000/api/ebooks` - Ebook list

### Test Frontend
1. Open `http://localhost:5173` in browser
2. Click "Ro'yxatdan o'tish" (Register)
3. Create account or login:
   - **Admin:** `admin@qaraqalpaq.uz` / `admin123`
   - **User:** `user@test.uz` / `user123`
4. Navigate through Quiz, Dictionary, E-books modules

## 🔑 Test Credentials

- **Admin:** `admin@qaraqalpaq.uz` / `admin123`
- **User:** `user@test.uz` / `user123`

## 📋 Requirements Checklist

- ✅ Node.js installed
- ✅ Backend dependencies installed (`npm install` in backend folder)
- ✅ Frontend dependencies installed (`npm install` in frontend folder)
- ✅ Database created and seeded
- ✅ Backend running on port 5000
- ✅ Frontend running on port 5173
- ✅ No port conflicts

## 🐛 Troubleshooting

### Port Already in Use
```powershell
# Check what's using port 5000
netstat -ano | findstr :5000

# Check what's using port 5173
netstat -ano | findstr :5173
```

### Backend Won't Start
1. Check `.env` file exists: `node scripts/ensure-env.js`
2. Check database exists: `Test-Path prisma\dev.db`
3. Regenerate Prisma: `npm run prisma:generate`

### Frontend Can't Connect to Backend
1. Verify backend is running: `curl http://localhost:5000/`
2. Check API URL in `frontend/src/services/api.js`
3. Check browser console for errors

### Database Issues
```powershell
cd backend
# Reset database
Remove-Item prisma\dev.db -ErrorAction SilentlyContinue
npx prisma migrate dev --name init
npm run prisma:seed
```

## 📁 Project Structure

```
proyekt/
├── backend/
│   ├── src/              # Backend source code
│   ├── prisma/           # Database schema and migrations
│   ├── scripts/          # Setup scripts
│   ├── start-backend.ps1 # Backend startup script
│   └── test-api.ps1      # API test script
│
├── frontend/
│   ├── src/              # Frontend source code
│   ├── start-frontend.ps1 # Frontend startup script
│   └── vite.config.js    # Vite configuration
│
├── START_ALL.ps1         # Start both servers
└── QUICK_START.md        # This file
```

## 🎯 Next Steps

1. ✅ Backend running on port 5000
2. ✅ Frontend running on port 5173
3. ✅ Test authentication (login/register)
4. ✅ Test Quiz module
5. ✅ Test Dictionary module
6. ✅ Test E-books module

**Everything should be working now!** 🎉


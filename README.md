# Qaraqalpaq Til Platforması

Qaraqalpaq tilini o'rganish uchun to'liq ishlaydigan web-platforma.

## 🎯 Xususiyatlar

- 📘 **E-kitoblar** - Onlayn kitoblarni o'qish
- 🧠 **Quiz va Test** - Bilimingizni sinab ko'rish
- 📖 **Tushuntirma So'zlik** - So'zlarni qidirish va o'rganish
- 👤 **Foydalanuvchi tizimi** - Ro'yxatdan o'tish va kirish
- 🔐 **JWT Authentication** - Xavfsiz autentifikatsiya
- 👨‍💼 **Admin paneli** - Ma'lumotlar qo'shish

## 🛠️ Texnologiyalar

### Backend
- Node.js + Express
- Prisma ORM
- SQLite Database
- JWT Authentication

### Frontend
- React + Vite
- Tailwind CSS
- React Router
- Axios

## 📦 O'rnatish

### Backend

```bash
cd backend
npm install
npm run prisma:generate
npm run prisma:migrate
npm run prisma:seed
npm run dev
```

Backend `http://localhost:5000` da ishga tushadi.

### Frontend

```bash
cd frontend
npm install
npm run dev
```

Frontend `http://localhost:3000` da ishga tushadi.

## 🔑 Test Foydalanuvchilar

- **Admin**: admin@qaraqalpaq.uz / admin123
- **User**: user@test.uz / user123

## 📡 API Endpoints

### Auth
- `POST /api/auth/register` - Ro'yxatdan o'tish
- `POST /api/auth/login` - Kirish
- `GET /api/auth/profile` - Profil (JWT kerak)

### Quizzes
- `GET /api/quizzes` - Barcha quizlar
- `GET /api/quizzes/:id` - Quiz ma'lumotlari
- `POST /api/quizzes/:id/submit` - Quiz javoblarini yuborish
- `POST /api/quizzes` - Yangi quiz yaratish (Admin)

### Dictionary
- `GET /api/dictionary` - Barcha so'zlar
- `GET /api/dictionary/search?word=` - So'z qidirish
- `POST /api/dictionary` - Yangi so'z qo'shish (Admin)

### Ebooks
- `GET /api/ebooks` - Barcha kitoblar
- `GET /api/ebooks/:id` - Kitob ma'lumotlari
- `POST /api/ebooks` - Yangi kitob qo'shish (Admin)

## 🚀 Deploy

### Backend (Render / Railway)
1. GitHub'ga push qiling
2. Render yoki Railway'da yangi service yarating
3. Environment variables qo'shing
4. Build command: `npm install && npm run prisma:generate && npm run prisma:migrate`
5. Start command: `npm start`

### Frontend (Vercel)
1. GitHub'ga push qiling
2. Vercel'da yangi project yarating
3. Environment variable: `VITE_API_URL=your-backend-url/api`
4. Deploy!

## 📝 Litsenziya

MIT


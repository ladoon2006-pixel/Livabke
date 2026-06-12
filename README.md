# Livabke - Random Chat Application

یک برنامه چت وب ساده که کاربران را به طور تصادفی با هم متصل می‌کند.

## ✨ فیچرها

- 👤 ثبت نام با نام کاربری
- 🎲 اتصال تصادفی به کاربران آنلاین
- 💬 چت실time با WebSocket
- 💾 ذخیره پیام‌ها در پایگاه داده
- 🔌 اتصال خودکار و قطع اتصال

## 🛠️ تکنولوژی

- **Frontend**: React 18 + Vite
- **Backend**: Node.js + Express + WebSocket
- **Database**: Supabase (PostgreSQL)
- **Real-time**: WebSocket

## 📋 نیازمندی‌ها

- Node.js 16+
- npm یا yarn
- Supabase Account

## ⚙️ نصب و راه‌اندازی

### 1. Clone Repository
```bash
git clone https://github.com/ladoon2006-pixel/Livabke.git
cd Livabke
```

### 2. Setup Supabase

1. به [supabase.com](https://supabase.com) بروید
2. یک پروژه جدید بسازید
3. SQL Query زیر را اجرا کنید:

```sql
-- Create users table
CREATE TABLE users (
  id TEXT PRIMARY KEY,
  name TEXT NOT NULL,
  online BOOLEAN DEFAULT TRUE,
  created_at TIMESTAMP DEFAULT NOW()
);

-- Create chat_sessions table
CREATE TABLE chat_sessions (
  id TEXT PRIMARY KEY,
  user1 TEXT NOT NULL,
  user2 TEXT NOT NULL,
  user1_name TEXT,
  user2_name TEXT,
  created_at TIMESTAMP DEFAULT NOW()
);

-- Create messages table
CREATE TABLE messages (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  session_id TEXT NOT NULL,
  sender_id TEXT NOT NULL,
  content TEXT NOT NULL,
  created_at TIMESTAMP DEFAULT NOW()
);
```

### 3. Install Dependencies
```bash
npm install
```

### 4. Setup Environment Variables

کپی `.env.example` به `.env` و مقادیر را تنظیم کنید:

```bash
cp .env.example .env
```

تکمیل کنید:
```
VITE_SUPABASE_URL=your_supabase_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
VITE_API_URL=http://localhost:3001

SUPABASE_URL=your_supabase_url
SUPABASE_KEY=your_supabase_service_role_key
PORT=3001
```

### 5. Run Development Server

```bash
npm run dev
```

سرور WebSocket در `http://localhost:3001`
برنامه React در `http://localhost:5173`

## 🚀 استفاده

1. برنامه را باز کنید
2. نام کاربری خود را وارد کنید
3. دکمه "Start Random Chat" را بزنید
4. منتظر اتصال به یک کاربر تصادفی بمانید
5. چت کنید! 💬

## 📁 ساختار پروژه

```
Livabke/
├── server/
│   └── index.js          # WebSocket Server
├── src/
│   ├── App.jsx           # Main App Component
│   ├── App.css           # Styles
│   └── main.jsx          # React Entry Point
├── package.json
├── vite.config.js
├── index.html
└── .env.example
```

## 📝 قابلیت‌های آینده

- [ ] صوت و ویدیو
- [ ] سیستم بند کردن کاربران
- [ ] رتینگ کاربران
- [ ] اتاق‌های گروهی
- [ ] فیلتر محتوا

## 📄 لایسنس

MIT

## 🤝 مشارکت

Pull requests خوش‌آمد!

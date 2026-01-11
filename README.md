ABC FunLand - Aplikasi Edukasi Interaktif untuk Anak
https://img.shields.io/badge/Next.js-15.0-black?style=for-the-badge&logo=next.js
https://img.shields.io/badge/TypeScript-5.0-blue?style=for-the-badge&logo=typescript
https://img.shields.io/badge/Tailwind-CSS-06B6D4?style=for-the-badge&logo=tailwindcss
https://img.shields.io/badge/Prisma-ORM-purple?style=for-the-badge&logo=prisma
https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white

📖 Tentang Proyek
ABC FunLand adalah aplikasi web edukasi interaktif yang dirancang untuk membantu anak-anak belajar mengenal huruf, suku kata, dan kata dengan cara yang menyenangkan. Aplikasi ini menggabungkan konsep gamifikasi dengan pembelajaran untuk menciptakan pengalaman belajar yang engaging.

✨ Fitur Utama
🎯 Sistem Kuis Interaktif

Kuis Huruf - Belajar mengenal huruf A-Z dengan audio dan visual

Kuis Suku Kata - Mengenal pola suku kata dasar (ba, bi, bu, dll.)

Kuis Kata - Belajar kata-kata sederhana dalam Bahasa Indonesia

Pertanyaan Acak - Setiap sesi mendapatkan 7 soal acak yang berbeda

🏆 Sistem Gamifikasi

Sistem Poin - Dapatkan poin untuk jawaban benar, kurangi untuk jawaban salah

Sistem Nyawa - Mulai dengan 3 nyawa, habis jika skor di bawah 70%

Leaderboard - Lihat peringkat berdasarkan total poin

Toko Virtual - Beli nyawa tambahan dengan poin yang dikumpulkan

🎨 Pengalaman Pengguna

UI/UX Responsif - Berjalan lancar di desktop dan mobile

Audio Feedback - Suara untuk setiap huruf/kata dan feedback benar/salah

Visual Menarik - Gambar ilustrasi untuk setiap materi pembelajaran

Animasi Interaktif - Transisi dan efek yang menyenangkan

🔐 Manajemen Pengguna

Autentikasi Lengkap - Login/Register dengan sistem yang aman

Profil Pengguna - Lihat statistik dan riwayat kuis

Progress Tracking - Pantau perkembangan belajar anak

🚀 Mulai Cepat
Prasyarat
Node.js 18.17 atau lebih baru

PostgreSQL database

npm, yarn, pnpm, atau bun

Langkah 1: Clone Repository
bash
git clone https://github.com/utrhmaa/ABCFunLand.git
cd ABCFunLand
Langkah 2: Install Dependencies
bash
npm install
# atau
yarn install
# atau
pnpm install
# atau
bun install
Langkah 3: Setup Environment Variables
Buat file .env di root direktori:

env
# Database
DATABASE_URL="postgresql://username:password@localhost:5432/abcfunland"

# Authentication (sesuaikan dengan provider Anda)
NEXTAUTH_SECRET="your-secret-key-here"
NEXTAUTH_URL="http://localhost:3000"

# Next.js
NEXT_PUBLIC_APP_URL="http://localhost:3000"
Langkah 4: Setup Database
bash
# Generate Prisma client
npx prisma generate

# Jalankan migrasi database
npx prisma db push
# atau
npx prisma migrate dev
Langkah 5: Seed Database (Opsional)
bash
# Isi data awal untuk kuis
npm run seed
Langkah 6: Jalankan Server Development
bash
npm run dev
# atau
yarn dev
# atau
pnpm dev
# atau
bun dev
Buka http://localhost:3000 di browser untuk melihat aplikasi.

🏗️ Struktur Proyek
text
abcfunland/
├── app/                    # Next.js App Router
│   ├── (auth)/            # Halaman autentikasi
│   ├── (loginUser)/       # Halaman setelah login
│   │   ├── quiz/          # Halaman kuis
│   │   │   ├── huruf/     # Kuis huruf
│   │   │   ├── suku-kata/ # Kuis suku kata
│   │   │   └── kata/      # Kuis kata
│   │   ├── shop/          # Toko virtual
│   │   └── profile/       # Profil pengguna
│   ├── api/               # API Routes
│   │   ├── quiz/          # API untuk kuis
│   │   ├── user/          # API untuk user
│   │   └── shop/          # API untuk shop
│   ├── layout.tsx         # Root layout
│   └── page.tsx           # Homepage
├── components/            # Komponen React
│   ├── quiz/             # Komponen kuis
│   ├── ui/               # UI components
│   └── shared/           # Shared components
├── lib/                  # Utility functions
│   ├── db.ts             # Prisma client
│   └── utils.ts          # Helper functions
├── prisma/               # Prisma schema
│   └── schema.prisma     # Database schema
├── public/               # Static assets
│   ├── audio/            # File audio
│   └── images/           # Gambar dan ilustrasi
├── types/                # TypeScript type definitions
└── styles/               # Global styles
🛠️ Teknologi yang Digunakan
Framework: Next.js 15 dengan App Router

Bahasa: TypeScript

Styling: Tailwind CSS

Database: PostgreSQL dengan Prisma ORM

Authentication: NextAuth.js atau Clerk

Deployment: Vercel (direkomendasikan)

📦 Script NPM
json
{
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint",
    "prisma:generate": "prisma generate",
    "prisma:push": "prisma db push",
    "prisma:studio": "prisma studio",
    "seed": "tsx prisma/seed.ts"
  }
}
🎮 Cara Menggunakan Aplikasi
Untuk Pengguna Baru:
Register/Login - Buat akun baru atau login

Pilih Jenis Kuis - Pilih antara huruf, suku kata, atau kata

Pelajari Aturan - Baca aturan permainan sebelum mulai

Mulai Kuis - Jawab 7 soal dengan mendengarkan audio dan memilih jawaban

Lihat Hasil - Periksa skor dan statistik Anda

Ulangi atau Coba Jenis Lain - Tingkatkan skill Anda!

Fitur Khusus:
Audio Guide: Dengarkan pengucapan setiap huruf/kata

Sistem Poin: +10 untuk benar, -10 untuk salah

Sistem Nyawa: Kehilangan nyawa jika skor akhir < 70%

Toko: Beli nyawa ekstra dengan poin yang terkumpul

📊 Model Database
prisma
model User {
  id        String   @id @default(cuid())
  email     String   @unique
  name      String?
  points    Int      @default(0)
  lives     Int      @default(3)
  image     String?
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
}

model Quiz {
  id       String   @id @default(cuid())
  question String
  answer   String
  options  String[]
  point    Int      @default(10)
  type     String   // "HURUF", "SUKU_KATA", "KATA"
}

model QuizAttempt {
  id             String   @id @default(cuid())
  userId         String
  quizId         String
  selectedAnswer String
  correct        Boolean
  pointsEarned   Int
  createdAt      DateTime @default(now())
}
🚀 Deployment di Vercel
https://vercel.com/button

Untuk deploy ke Vercel:

Push kode ke GitHub

Import ke Vercel

Konfigurasi Environment Variables

Deploy!

Environment Variables yang diperlukan di Vercel:

DATABASE_URL - Connection string PostgreSQL

NEXTAUTH_SECRET - Secret untuk NextAuth

NEXTAUTH_URL - URL aplikasi Anda

🤝 Berkontribusi
Kontribusi sangat diterima! Ikuti langkah-langkah berikut:

Fork repository

Buat branch fitur (git checkout -b feature/AmazingFeature)

Commit perubahan (git commit -m 'Add some AmazingFeature')

Push ke branch (git push origin feature/AmazingFeature)

Buat Pull Request

Panduan Kontribusi
Gunakan TypeScript untuk semua kode baru

Ikuti konvensi kode yang sudah ada

Tambahkan komentar untuk kode yang kompleks

Update dokumentasi sesuai kebutuhan

📄 Lisensi
Proyek ini dilisensikan di bawah MIT License - lihat file LICENSE untuk detail.

🙏 Ucapan Terima Kasih
Tim Next.js untuk framework yang luar biasa

Komunitas Tailwind CSS untuk utilitas CSS yang produktif

Prisma Team untuk ORM yang developer-friendly

Semua kontributor yang telah membantu pengembangan proyek ini

📞 Kontak & Support
Issues: GitHub Issues

Discussions: GitHub Discussions

Email: utrhmaa@example.com

🌟 Dukungan
Jika Anda menyukai proyek ini, berikan ⭐ di GitHub!

Dibuat dengan ❤️ untuk pendidikan anak Indonesia yang lebih baik

© 2024 ABC FunLand. Semua hak dilindungi undang-undang.

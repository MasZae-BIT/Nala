# Nalarku.ai

Platform belajar berbasis web yang dilengkapi asisten kecerdasan buatan personal bernama **Nala AI**. Nalarku.ai membantu proses belajar mandiri menjadi lebih personal, interaktif, dan terukur — dilengkapi gamifikasi, Pomodoro timer, kuis adaptif, leaderboard, dan plagiarism checker.

> Status: 🚧 Under active development

---

## ✨ Fitur Utama

- **Nala AI** — asisten belajar personal yang memahami konteks dan progres belajar tiap pengguna, bukan sekadar chatbot generik
- **Kuis Adaptif** — soal latihan yang dihasilkan AI sesuai materi yang sedang dipelajari
- **Pomodoro Timer** — sesi belajar terjadwal yang bisa dipicu langsung oleh Nala AI
- **Gamifikasi** — sistem XP, level, dan leaderboard untuk memotivasi belajar konsisten
- **Plagiarism Checker** — pemeriksaan orisinalitas tulisan pengguna
- **Onboarding Flow** — alur pengenalan platform untuk pengguna baru

## 🧠 Cara Kerja Nala AI (Singkat)

Nalarku.ai **tidak melatih atau menghosting model AI sendiri**. Kecerdasan Nala AI diakses melalui API milik penyedia model bahasa besar (LLM) pihak ketiga, dengan pendekatan **multi-provider**: tugas berbeda (chat tutor, generate soal, plagiarism check) dapat dirutekan ke provider yang paling sesuai dari segi kualitas, kecepatan, dan biaya.

```
Pengguna → Frontend (React) → Backend (Node.js/Express) → AI Router → Provider API AI
                                      │
                                      └── Database (progres, riwayat, XP)
```

"Kepribadian" Nala AI dibentuk lewat lapisan **system prompt** dan konteks personal yang disisipkan backend di setiap permintaan — bukan model terpisah.

📄 Dokumentasi arsitektur lengkap (termasuk diagram, alur request, dan pertimbangan keamanan/biaya) tersedia di [`/docs`](./docs).

## 🛠️ Tech Stack

| Layer | Teknologi |
|---|---|
| Frontend | React (SPA) |
| Backend | Node.js + Express |
| AI Engine | Multi-provider LLM API (lihat `/docs/arsitektur.md`) |
| Database | _TBD_ |
| Deployment | Vercel / GitHub |

## 📦 Instalasi

### Prasyarat
- Node.js ≥ 18.x
- npm atau yarn
- API key dari provider AI yang digunakan (lihat `.env.example`)

### Setup

```bash
# Clone repository
git clone https://github.com/<username>/nalarku-ai.git
cd nalarku-ai

# Install dependencies (frontend & backend)
npm install

# Salin file environment variable
cp .env.example .env
```

Isi `.env` dengan kredensial yang dibutuhkan:

```env
# AI Provider
AI_PROVIDER_PRIMARY_API_KEY=
AI_PROVIDER_SECONDARY_API_KEY=

# Database
DATABASE_URL=

# Auth
JWT_SECRET=
```

### Menjalankan secara lokal

```bash
# Jalankan backend
npm run dev:server

# Jalankan frontend (terminal terpisah)
npm run dev:client
```

Aplikasi akan berjalan di `http://localhost:3000` (frontend) dan `http://localhost:5000` (backend), atau sesuaikan dengan konfigurasi proyek.

## 📁 Struktur Proyek

```
nalarku-ai/
├── client/                 # Frontend React
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   └── ...
│   └── package.json
├── server/                  # Backend Node.js/Express
│   ├── routes/
│   ├── services/
│   │   └── aiRouter.js      # Logika routing multi-provider AI
│   ├── prompts/
│   │   └── nalaPersona.js   # System prompt & persona Nala AI
│   └── package.json
├── docs/                    # Dokumentasi teknis & akademik
├── .env.example
└── README.md
```

> Struktur di atas adalah acuan awal dan dapat menyesuaikan implementasi aktual repo.

## 🔐 Keamanan

- API key penyedia AI **hanya disimpan di backend** (environment variable), tidak pernah terekspos ke frontend
- Seluruh komunikasi ke API eksternal melalui HTTPS
- File `.env` tidak di-commit ke repository (lihat `.gitignore`)

## 🗺️ Roadmap

- [ ] Finalisasi pemilihan provider AI utama & cadangan
- [ ] Implementasi sistem leaderboard
- [ ] Implementasi plagiarism checker
- [ ] Onboarding flow untuk pengguna baru
- [ ] Deployment produksi (Vercel)

## 🤝 Kontribusi

Proyek ini masih dalam tahap pengembangan aktif. Saran, isu, dan kontribusi sangat terbuka — silakan buat *issue* atau *pull request*.

## 📄 Lisensi

_Belum ditentukan._

## 👤 Disusun oleh

Hamba Allah

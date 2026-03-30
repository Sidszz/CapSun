# 🃏 Capsa Susun Online

Game Capsa Susun multiplayer real-time, bisa dimainkan 2–4 pemain dari berbagai device via browser.

**Live demo:** `https://<username>.github.io/<repo-name>/`

---

## 🚀 Setup (5–10 menit)

### Langkah 1 — Buat Firebase Project (gratis)

1. Buka **[console.firebase.google.com](https://console.firebase.google.com)**
2. Klik **"Add project"** → beri nama (misal: `capsa-susun`)
3. Matikan Google Analytics (opsional) → **Create project**

### Langkah 2 — Aktifkan Realtime Database

1. Di sidebar Firebase, klik **Build → Realtime Database**
2. Klik **"Create Database"**
3. Pilih region: **us-central1** (atau yang terdekat)
4. Pilih mode: **"Start in test mode"** → Next → Done

### Langkah 3 — Set Security Rules

1. Di Realtime Database, klik tab **"Rules"**
2. Salin isi dari file `database.rules.json` dan paste ke sana
3. Klik **"Publish"**

### Langkah 4 — Dapatkan Firebase Config

1. Di Firebase Console, klik ikon ⚙️ → **Project Settings**
2. Scroll ke bawah ke bagian **"Your apps"**
3. Klik **"</> Web"** → beri nama app → **Register**
4. Salin objek `firebaseConfig` yang muncul

### Langkah 5 — Edit `firebase-config.js`

Buka file `firebase-config.js` dan ganti semua nilai `YOUR_...` dengan nilai dari Firebase:

```js
const firebaseConfig = {
  apiKey:            "AIzaSy...",
  authDomain:        "capsa-susun.firebaseapp.com",
  databaseURL:       "https://capsa-susun-default-rtdb.firebaseio.com",
  projectId:         "capsa-susun",
  storageBucket:     "capsa-susun.appspot.com",
  messagingSenderId: "123456789",
  appId:             "1:123456789:web:abc123"
};
```

### Langkah 6 — Push ke GitHub & Aktifkan GitHub Pages

```bash
# Clone repo (jika belum)
git clone https://github.com/<username>/<repo>.git
cd <repo>

# Copy file-file game ke sini, lalu:
git add .
git commit -m "Add Capsa Susun online multiplayer"
git push origin main
```

Lalu di GitHub:
1. Buka **Settings → Pages**
2. Source: **Deploy from a branch**
3. Branch: `main` / `(root)` → **Save**
4. Tunggu ~1 menit → game live di `https://<username>.github.io/<repo>/`

---

## 🎮 Cara Bermain

| Langkah | Deskripsi |
|---------|-----------|
| 1 | Buka link game → masukkan nama → **Buat Game Baru** |
| 2 | Salin link/kode room → kirim ke teman |
| 3 | Teman buka link → masukkan nama → otomatis masuk room |
| 4 | Host klik **"Mulai Game!"** (min. 2 pemain) |
| 5 | Susun 13 kartu ke 3 baris dalam 2 menit |
| 6 | Klik **"Kunci"** saat selesai |
| 7 | Semua kartu dibuka → skor dihitung otomatis |

### Aturan Susunan
- **Atas** (3 kartu): Paling lemah
- **Tengah** (5 kartu): Lebih kuat dari Atas
- **Bawah** (5 kartu): Paling kuat

Kekuatan harus **Bawah ≥ Tengah ≥ Atas** — kalau tidak valid = **FOUL** (-6 poin)!

### Sistem Poin
- +1 per baris yang menang head-to-head
- +3 bonus jika sweep semua 3 baris (total jadi +6)
- FOUL = -6 poin

---

## 🗂️ Struktur File

```
├── index.html          # Game utama (satu file)
├── firebase-config.js  # Konfigurasi Firebase (edit ini!)
├── database.rules.json # Security rules untuk Firebase
└── README.md           # Panduan ini
```

---

## 🆓 Firebase Free Tier

Firebase Spark Plan (gratis) sudah lebih dari cukup:
- **100 koneksi simultan**
- **1 GB storage**
- **10 GB/bulan download**

---

## 🛠️ Tech Stack

- **Frontend:** Vanilla JS + HTML/CSS (single file, no build step)
- **Database:** Firebase Realtime Database (real-time sync via WebSocket)
- **Hosting:** GitHub Pages
- **Font:** Cinzel + DM Sans (Google Fonts)

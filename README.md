# 🎓 Portal Informasi TF23C

Sistem Informasi Akademik untuk mahasiswa **Teknologi Informasi - TF23C** — mengelola jadwal kuliah, tugas, notifikasi tenggat, dan progres akademik dalam satu dashboard modern bertema dark-mode.

> **Live Demo:** [https://rensftr30-hue.github.io/informasiTF23C/](https://rensftr30-hue.github.io/informasiTF23C/)

---

## ✨ Fitur

| Fitur | Status |
|-------|--------|
| ✅ Login dengan autentikasi NIM & Password | ✅ Aktif |
| ✅ Jadwal kuliah per hari (Senin–Jumat) | ✅ Aktif |
| ✅ Manajemen tugas (Tambah, Edit, Selesai, Hapus) | ✅ Aktif |
| ✅ Hitung mundur tenggat (Circle Countdown) | ✅ Aktif |
| ✅ Notifikasi tugas H-1 mendesak | ✅ Aktif |
| ✅ Search & filter tugas | ✅ Aktif |
| ✅ Progress bar penyelesaian tugas | ✅ Aktif |
| ✅ Dashboard metrik dinamis | ✅ Aktif |
| ✅ Penyimpanan data di localStorage | ✅ Aktif |
| ✅ Tampilan mobile responsive | ✅ Aktif |
| ✅ Auto-deploy ke GitHub Pages | ✅ Aktif |

---

## 🛠️ Teknologi

| Teknologi | Kegunaan |
|-----------|----------|
| **React 18** | Library UI |
| **TypeScript** | Type safety |
| **Vite 6** | Build tool & dev server |
| **Tailwind CSS v4** | Utility-first CSS |
| **Lucide React** | Icon library |
| **GitHub Actions** | CI/CD auto-deploy ke Pages |

---

## 🚀 Cara Menjalankan

### Prasyarat

- [Node.js](https://nodejs.org/) versi 18+ atau 22+
- npm (sudah termasuk Node.js)

### Instalasi

```bash
# Clone repo
git clone https://github.com/rensftr30-hue/informasiTF23C.git
cd informasiTF23C

# Install dependencies
npm install

# Jalankan development server
npm run dev
```

Buka **http://localhost:5173** di browser.

### Build Produksi

```bash
npm run build
```

Hasil build ada di folder `dist/`.

---

## 🔐 Login

| Field | Value |
|-------|-------|
| **NIM** | `101230072` |
| **Password** | `TF23C` |

> Credential ini bisa diubah di `src/app/App.tsx` bagian `VALID_CREDENTIALS`.

---

## 📁 Struktur Proyek

```
informasiTF23C/
├── .github/workflows/   # GitHub Actions auto-deploy
├── dist/                # Hasil build (siap deploy)
├── src/
│   ├── app/
│   │   ├── App.tsx      # Komponen utama (839 baris)
│   │   └── components/  # (kosong - semua di App.tsx)
│   ├── styles/
│   │   ├── fonts.css    # Font Google (Exo 2, Inter, JetBrains Mono)
│   │   ├── index.css    # Entry point CSS
│   │   ├── tailwind.css # Tailwind + tw-animate-css
│   │   └── theme.css    # CSS variables tema dark
│   └── main.tsx         # Entry point React
├── index.html           # Template HTML
├── package.json         # Dependencies & scripts
├── vite.config.ts       # Konfigurasi Vite
└── README.md
```

---

## 📸 Halaman

| Halaman | Deskripsi |
|---------|-----------|
| **Login** | Form login dengan NIM & Password, validasi error |
| **Dashboard** | Metrik (MK, SKS, progres), jadwal hari ini, tugas terdekat, motivasi harian |
| **Jadwal** | Jadwal kuliah lengkap Senin–Jumat dengan ruangan & warna per MK |
| **Tugas** | Daftar tugas dengan filter (Semua/Belum/Selesai), tambah/edit/hapus, countdown |
| **Notifikasi** | Notifikasi tugas yang mendekati tenggat (H-3, H-1, lewat) |
| **Pengaturan** | Informasi akun & tombol keluar |

---

## 🌐 Deployment

Otomatis deploy ke **GitHub Pages** setiap push ke branch `main` via GitHub Actions.

### Manual

```bash
npm run build
```

Upload isi folder `dist/` ke hosting statis (Vercel, Netlify, atau GitHub Pages).

---

## 👩‍🎓 Identitas

- **Nama:** Reni Safitri
- **NIM:** 101230072
- **Program Studi:** Teknologi Informasi
- **Semester:** 6
- **Email:** reni.safitri@student.utn.ac.id

---

## 📄 Lisensi

Proyek ini dibuat untuk keperluan akademik. Didasarkan pada desain Figma: [Desain UI Portal Mahasiswa](https://www.figma.com/design/PEFQg2N06gKlaKrJLmTLW0/Desain-UI-Portal-Mahasiswa).
  
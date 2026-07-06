# Development Guide — Portal Informasi TF23C

## Arsitektur Aplikasi

Aplikasi ini adalah **Single Page Application (SPA)** menggunakan React + Vite. Seluruh komponen ditulis dalam satu file utama `src/app/App.tsx`.

### Alur Data

```
Login → Dashboard
         ├── Dashboard (metrik, jadwal hari ini, tugas, motivasi)
         ├── Jadwal (jadwal lengkap per hari)
         ├── Tugas (CRUD tugas, filter, search)
         ├── Notifikasi (peringatan deadline)
         └── Pengaturan (info akun, logout)
```

### State Management

Semua state dikelola menggunakan `useState` dan `useEffect` dari React:

| State | Lokasi | Fungsi |
|-------|--------|--------|
| `page` | `App` | "login" atau "dashboard" |
| `tasks` | `DashboardPage` | Daftar tugas, persist ke localStorage |
| `activeSection` | `DashboardPage` | Navigasi halaman |
| `searchQuery` | `DashboardPage` | Pencarian tugas |

### localStorage

Data tugas otomatis tersimpan ke `localStorage` setiap kali ada perubahan menggunakan custom hook `useTasks`:

```typescript
function useTasks(initial: Task[]) {
  const [tasks, setTasks] = useState<Task[]>(() => {
    const saved = localStorage.getItem("tasks");
    return saved ? JSON.parse(saved) : initial;
  });
  useEffect(() => {
    localStorage.setItem("tasks", JSON.stringify(tasks));
  }, [tasks]);
  return [tasks, setTasks] as const;
}
```

### Komponen

| Komponen | Deskripsi |
|----------|-----------|
| `GlassCard` | Wrapper card dengan efek glassmorphism |
| `DeadlineToast` | Notifikasi floating untuk tugas H-1 |
| `CircleCountdown` | SVG circular countdown timer |
| `AddTaskModal` | Modal form tambah/edit tugas |
| `Sidebar` | Navigasi sidebar (desktop) |
| `BottomNav` | Navigasi bottom tab (mobile) |
| `MetricCard` | Kartu metrik dashboard |
| `TaskCard` | Kartu tugas dengan aksi toggle/edit/hapus |

### Styling

- **Tailwind CSS v4** untuk utility classes
- **CSS Variables** di `theme.css` untuk tema dark
- **Google Fonts**: Exo 2 (heading), Inter (body), JetBrains Mono (monospace)
- **Lucide React** untuk ikon SVG

### Autentikasi

Login menggunakan validasi sederhana dengan credential tetap:

```typescript
const VALID_CREDENTIALS = { nim: "101230072", password: "TF23C" };
```

Untuk production, ganti dengan autentikasi backend (Supabase, Firebase, atau REST API).

---

## Cara Menambahkan Fitur Baru

### 1. Tambah halaman/section baru

1. Tambahkan key baru ke tipe `ActiveSection`
2. Tambahkan entry ke array `NAV` untuk sidebar
3. Buat fungsi komponen section baru
4. Tambahkan case di `renderContent()`

### 2. Tambah jadwal baru

Edit object `SCHEDULE` di `App.tsx`:

```typescript
const SCHEDULE: Record<string, ClassItem[]> = {
  Senin: [
    { name: "Nama MK", time: "08.00 – 09.45", room: "Ruang", color: "cyan" },
  ],
  // ...
};
```

### 3. Integrasi backend (Supabase)

1. Buat project di [supabase.com](https://supabase.com)
2. Install: `npm install @supabase/supabase-js`
3. Ganti `useTasks` hook dengan query Supabase
4. Ganti `VALID_CREDENTIALS` dengan autentikasi Supabase

---

## Deployment

### GitHub Actions (otomatis)

Push ke branch `main` → workflow di `.github/workflows/deploy.yml` akan:
1. Install dependencies
2. Build project
3. Upload ke GitHub Pages

### Manual ke Vercel

```bash
npm run build
npx vercel --prod
```

### Manual ke Netlify

```bash
npm run build
# Upload folder dist/ ke Netlify
```

---

## Troubleshooting

| Masalah | Solusi |
|---------|--------|
| Build error `tw-animate-css` | `npm install tw-animate-css` |
| Blank page setelah deploy | Periksa `base` di `vite.config.ts` |
| Data tugas hilang | Cek localStorage di browser (F12 → Application → Local Storage) |
| Login tidak bisa | Gunakan credential: NIM `101230072`, Password `TF23C` |

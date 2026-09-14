# Cek Coverage DP — FTTH

Aplikasi statis (HTML tunggal, tanpa backend/build step) untuk mengecek apakah
titik-titik data pelanggan berada dalam radius tertentu (default 350 m) dari
titik DP FTTH. Semua pemrosesan (baca Excel, hitung jarak, geocoding, export)
berjalan di browser pengguna.

## Isi folder
- `index.html` — seluruh aplikasi (HTML + CSS + JS jadi satu file)
- `vercel.json` — konfigurasi minimal untuk Vercel

## Cara deploy ke Vercel

### Opsi A — lewat Vercel CLI (paling cepat)
```bash
npm install -g vercel
cd folder-ini
vercel
```
Ikuti prompt-nya (login, pilih scope/project). Setelah selesai, Vercel akan
kasih URL live. Untuk deploy ke production langsung:
```bash
vercel --prod
```

### Opsi B — lewat Vercel Dashboard (drag & drop, tanpa CLI)
1. Buka https://vercel.com/new
2. Pilih **"Deploy a folder"** / drag folder ini ke area upload
   (atau upload lewat Git jika sudah kamu push ke GitHub/GitLab/Bitbucket)
3. Framework preset: pilih **"Other"** (bukan Next.js dkk) — Vercel akan
   otomatis mendeteksi `index.html` sebagai static site
4. Klik **Deploy**

### Opsi C — lewat GitHub
1. Push folder ini ke repo GitHub baru
2. Di Vercel dashboard: **New Project** → **Import Git Repository** → pilih repo itu
3. Framework preset: **Other** → Deploy

## Catatan
- Tidak ada environment variable atau API key yang perlu diatur — semua
  layanan yang dipakai (SheetJS via CDN, Nominatim untuk geocoding alamat)
  publik dan gratis.
- Data DP (359 titik) sudah tertanam langsung di dalam `index.html`. Kalau
  data DP berubah di kemudian hari, file `index.html` perlu diupdate ulang.

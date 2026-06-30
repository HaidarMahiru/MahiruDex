# MahiruDex - Backend & Frontend Manga Reader

MahiruDex adalah backend dan frontend custom yang lengkap dan cepat untuk membaca manga menggunakan **MangaDex API**.

## Fitur Utama

- **Pencarian Manga**: Cari manga favorit Anda dengan pencarian berbasis judul.
- **Filter Genre**: Eksplorasi manga berdasarkan tag/genre populer (Action, Comedy, Romance, Isekai, dll.).
- **Detail Manga Lengkap**: Menampilkan deskripsi, status manga (Ongoing/Completed), tahun rilis, cover, penulis, artis, dan daftar chapter.
- **Filter Bahasa Chapter**: Filter daftar chapter berdasarkan bahasa yang Anda inginkan (misal: Bahasa Indonesia, Inggris, atau semua bahasa).
- **Membaca Manga yang Interaktif**:
  - **Mode Webtoon (Long Strip)**: Halaman disusun menurun secara vertikal untuk digulir (scroll) dengan lancar.
  - **Mode Single Page**: Membaca satu per satu halaman dengan tombol navigasi atau tombol panah keyboard (kiri/kanan).
  - **Lebar Halaman Fleksibel**: Pilihan lebar tampilan halaman (600px, 800px, 1000px, hingga Full Width).
  - **Kualitas Gambar**: Pilih kualitas original (HQ) atau mode kompresi data (Data Saver) untuk hemat kuota.
- **Image Proxy**: Menggunakan server backend sebagai proxy gambar untuk menghindari kendala CORS dan pemblokiran hotlinking dari server MangaDex.

## Struktur Project

```text
MahiruDex/
├── public/
│   ├── index.html              # Halaman Utama (Daftar manga & pencarian)
│   ├── manga.html              # Halaman Detail Manga & Daftar Chapter
│   ├── reader.html             # Halaman Membaca Manga
│   ├── style.css               # Desain UI tema gelap bergaya MangaDex
│   └── placeholder-cover.jpg   # Gambar fallback jika cover tidak ditemukan
├── package.json                # Dependensi proyek & konfigurasi module
└── server.js                   # Backend Express server & API client MangaDex
```

## Prasyarat

- Node.js versi 18 atau yang lebih baru (disarankan Node.js v25+ yang digunakan saat pengujian).

## Cara Menjalankan

1. Masuk ke direktori `MahiruDex`:
   ```bash
   cd /data/data/com.termux/files/home/MahiruDex
   ```

2. Jalankan aplikasi menggunakan npm:
   ```bash
   npm start
   ```

3. Buka peramban (browser) Anda dan akses:
   ```text
   http://localhost:3000
   ```

## API Endpoints (Backend)

- `GET /api/manga` - Mencari/memuat manga populer (mendukung query parameter `title`, `limit`, `offset`, `includedTags`).
- `GET /api/manga/:id` - Memuat detail manga spesifik.
- `GET /api/manga/:id/feed` - Memuat daftar chapter manga (mendukung parameter `lang` untuk filter bahasa).
- `GET /api/chapter/:id` - Memuat detail halaman chapter (mendukung parameter `quality` untuk data/dataSaver).
- `GET /api/proxy?url=<url>` - Proxy gambar untuk memotong pembatasan CORS.

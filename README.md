# Rinso Laundry — Sistem Laundry (Web React TypeScript + REST API Node.js)

Proyek UTS PBAD 2026/2027. Domain: **Laundry** (Pelanggan, Layanan, Pesanan). Web client berkomunikasi dua arah dengan API server (CRUD) dan database SQLite terpusat.

## Struktur

```
server/   REST API (Node.js + Express + SQLite) + tes
web/      Web client (React 18 + TypeScript + Vite)
```

## Prasyarat

- **Node.js 22.13 atau lebih baru** (memakai `node:sqlite` bawaan, tanpa kompilasi native) dan npm.

## Menjalankan

Web: http://localhost:5173 (mode dev, proxy ke API) · API: http://localhost:3001/api

```sh
npm install
npm run dev
```

Mode produksi (satu server, web ikut disajikan Express):

```sh
npm start
```

Perintah lain: `npm test` (tes API), `npm run build` (type-check + build web), `npm run seed` (isi data awal bila database kosong).

Database tersimpan di `server/data/laundry.db` dan otomatis berisi data contoh saat pertama kali dijalankan. Hapus berkas itu untuk mengatur ulang. Variabel opsional: `PORT`, `DB_FILE`.

## Fitur

- CRUD Pelanggan, Layanan, dan Pesanan dengan validasi server dan pesan error per kolom
- Total harga otomatis, kode pesanan otomatis (`LDR-YYYYMMDD-NNN`), harga dikunci saat pesanan dibuat
- Alur status pesanan + pembatalan, penanda pembayaran
- Pencarian, filter, dan pagination; dashboard statistik dengan grafik
- Tema terang/gelap otomatis, responsif, status loading/error/kosong, toast

## Ringkasan API (`/api`)

| Resource | Endpoint |
|----------|----------|
| Pelanggan | `GET/POST /pelanggan`, `GET/PUT/DELETE /pelanggan/:id` |
| Layanan | `GET/POST /layanan`, `GET/PUT/DELETE /layanan/:id` |
| Pesanan | `GET/POST /pesanan`, `GET/PUT/DELETE /pesanan/:id`, `PATCH /pesanan/:id/status`, `PATCH /pesanan/:id/bayar` |
| Lainnya | `GET /stats`, `GET /health` |



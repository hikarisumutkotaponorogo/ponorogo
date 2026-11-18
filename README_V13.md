# V13 — Pemeriksaan integrasi yang bisa direproduksi

V13 meneruskan seluruh file V12. Penambahan: `tools/audit_v13.py` memeriksa referensi controller/action pada routes, `tools/environment_v13.sh` memeriksa kesiapan PHP/Composer, dan installer sekarang menjalankan audit V13 sebelum membuat proyek.

## Pemeriksaan tanpa Composer
```bash
python3 tools/audit_v11.py
python3 tools/audit_routes_v12.py
python3 tools/audit_v13.py
bash tools/environment_v13.sh
bash -n tools/integrate_laravel12.sh
```

## Instalasi pengujian lokal (hanya saat Composer + internet tersedia)
```bash
bash tools/integrate_laravel12.sh /lokasi/folder-baru/hikari-app
```
Installer membuat proyek Laravel 12 baru, menggabungkan source, menyiapkan SQLite lokal, menjalankan migrasi, seeder, `route:list`, dan `artisan test`. **Jangan jalankan di hosting produksi atau folder berisi data penting.** Tidak ada akun admin yang dibuat otomatis; buat akun secara aman setelah tes integrasi. Jangan gunakan kata sandi default.

## Batasan dan temuan
- Source tetap **overlay**, bukan paket Laravel mandiri; Composer belum ada pada lingkungan pembuatan V13.
- Lolos audit statis **tidak membuktikan** login, formulir, migrasi, dan dashboard berjalan.
- Sebelum produksi: pengujian Laravel sungguhan, verifikasi kebijakan akses, backup/restore, pemeriksaan perlindungan data, dan peninjauan semua konten/foto legalitas wajib dilakukan.
- Informasi lembaga yang belum terkonfirmasi tetap harus diverifikasi sebelum dipublikasikan.

# V11 — Audit integrasi offline dan perbaikan installer

Paket kumulatif V1–V11 adalah **source overlay**, bukan Laravel terinstal. Tidak ada `vendor/` atau framework lengkap.

## Perubahan V11
- Menambahkan `tools/audit_v11.py` untuk memeriksa keberadaan controller, model, dan Blade view yang direferensikan.
- Memperbaiki `tools/integrate_laravel12.sh`: path target instalasi dibuat absolut sebelum perintah migrasi dan pengujian, sehingga path SQLite tidak salah jika input relatif.
- Menambahkan laporan audit statis; ini bukan pengujian browser, database, atau autentikasi runtime.

## Jalankan
```bash
python3 tools/audit_v11.py
bash tools/preflight_v9.sh
bash tools/integrate_laravel12.sh /lokasi/baru/hikari-app
```

Installer membutuhkan Composer 2, PHP 8.3+, internet untuk mengunduh Laravel, dan ekstensi PHP yang sesuai. Jalankan di lingkungan pengembangan dahulu. Setelah selesai, lakukan pengujian formulir, login, izin admin, upload, privasi, dan database secara manual dan otomatis. Jangan deploy ke production sebelum berhasil.

## Batasan
Pada lingkungan pembuatan V11 Composer tidak tersedia, sehingga `php artisan test` belum dapat dijalankan. Dokumen legalitas, nomor WA, dan ID pixel tetap menunggu verifikasi. Jangan publikasikan foto identitas peserta tanpa redaksi dan izin.

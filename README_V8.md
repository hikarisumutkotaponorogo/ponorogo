# LPK Hikari Sumut — V8: Integrasi dan pemeriksaan

**Status:** Laravel 12 source overlay (bukan instalasi framework lengkap). V8 mengoreksi dua regresi V7: `/program` dan `/artikel` semula keliru mensyaratkan izin editor, sehingga pengunjung umum tidak bisa melihatnya.

## Perubahan
- Memperbaiki akses publik pada daftar program dan artikel.
- Menambahkan `tests/Feature/PublicRoutesV8Test.php` sebagai regression test (harus dijalankan pada Laravel dengan database/konfigurasi yang sesuai).
- Menambahkan `tools/integrate_laravel12.sh` untuk membuat instalasi Laravel 12 baru, menyalin source overlay, mendaftarkan authorization provider, lalu menjalankan `route:list` dan `artisan test`.
- Menambahkan `tools/check_routes.py` sebagai tes statis yang dapat dijalankan tanpa Laravel.

## Cara integrasi
Pada Linux/macOS dengan PHP 8.3+, Composer 2, internet dan SQLite/MySQL yang tersedia:

```bash
bash tools/integrate_laravel12.sh /path/to/new/hikari-laravel-app
```

**Penting:** Script berhenti jika direktori tujuan sudah ada; tidak menimpa proyek. Setelah integrasi, periksa `.env`, siapkan database, jalankan `php artisan migrate`, `php artisan db:seed --class=HikariSeeder` (sesuaikan namespace), dan tes ulang. Jangan gunakan di produksi sebelum security review dan end-to-end test.

## Batasan pemeriksaan
Lingkungan pembuatan V8 memiliki PHP CLI tetapi **tidak memiliki Composer**. Karena itu `composer create-project`, `php artisan route:list`, migrasi database, dan `php artisan test` **belum dapat dieksekusi di sini**. PHP lint dan static route check bukan pengganti pengujian aplikasi berjalan. Tidak ada klaim bahwa V8 sudah siap deploy.

## Perhatian privasi
Jangan menerbitkan snapshot HTML lama yang menampilkan paspor, COE, atau identitas peserta tanpa redaksi dan izin yang memadai.

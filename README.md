# LPK Hikari Sumut — Laravel V1 (source overlay)

**Status:** source code awal, belum diinstal/deploy. Paket ini bukan vendor Laravel lengkap; Composer belum tersedia di lingkungan pembuatan. Tidak ada klaim bahwa sistem sudah berjalan di hosting.

## Persyaratan
PHP 8.3+, Composer 2, MySQL 8/MariaDB kompatibel, Laravel 12 (sesuaikan dukungan hosting), ekstensi PDO/MySQL, mbstring, openssl, tokenizer, xml, ctype, fileinfo. PHP CLI dan database harus diuji di hosting. 

## Instalasi di mesin pengembangan / hosting yang kompatibel
1. `composer create-project laravel/laravel hikari-app "^12.0"`
2. Salin seluruh isi direktori `app/`, `routes/`, `database/`, `resources/`, `public/` dari paket ini ke proyek Laravel yang baru dibuat, dengan mempertahankan file bawaan Laravel yang tidak diganti.
3. `cp .env.example .env` (jika belum ada), `php artisan key:generate`; atur `APP_URL`, `DB_CONNECTION=mysql`, `DB_HOST`, `DB_DATABASE`, `DB_USERNAME`, `DB_PASSWORD`.
4. `php artisan migrate`; `php artisan db:seed --class="Database\\Seeders\\HikariSeeder"`; `php artisan storage:link`; `php artisan serve` untuk pengujian lokal.
5. Buat admin pertama: `php artisan hikari:create-admin admin@example.com` lalu masukkan password aman ketika diminta. Perintah tidak tersedia sebelum file paket disalin.
6. Jalankan `php artisan test` dan pengujian browser sebelum produksi.
7. Document root domain HARUS menunjuk ke direktori `public/`, bukan root proyek.

## Halaman
- `/` beranda website
- `/program` daftar program
- `/program/{slug}` detail program
- `/tentang-kami`, `/informasi-orang-tua`, `/alumni`, `/kontak`
- `/lp/kerja-jepang` landing page iklan
- `/admin/login` login dashboard
- `/admin` ringkasan leads; `/admin/leads` CRM; `/admin/settings` pengaturan; `/admin/programs` pengelolaan program
- `/referensi-landing/index.html` snapshot HTML terakhir (belum terhubung ke backend Laravel; referensi visual saja)

## Batasan yang disengaja
- Tracking GTM/GA4/Meta/TikTok **belum aktif**: ID dan persetujuan perlu disiapkan; tidak ada pixel yang mengirim data diam-diam.
- WhatsApp memakai nomor bawaan yang ada di HTML lama dan dapat diganti di dashboard; verifikasi nomor sebelum publikasi.
- Dokumen legalitas tidak diisi sampai diterima.
- Formulir mengirim lead ke server; membuka WhatsApp tidak membuktikan pesan telah dikirim.
- Belum ada modul pembayaran/penagihan otomatis, upload dokumen sensitif, notifikasi WhatsApp API, atau CMS drag-and-drop.
- Admin menggunakan autentikasi Laravel session, bukan Filament; panel dapat ditingkatkan ke Filament setelah dependency versi dipastikan.
- Foto paspor/COE di HTML referensi dapat mengandung data pribadi. Jangan publikasikan snapshot tersebut tanpa menutupi identitas dan memperoleh izin.
- Sediakan pemberitahuan privasi yang memadai sebelum mengumpulkan data publik; tidak disembunyikan demi desain.

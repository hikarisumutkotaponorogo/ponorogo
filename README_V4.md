# LPK Hikari Sumut — V4 Source Overlay

Melanjutkan V3 dengan pembaruan tampilan website publik, landing page fokus konsultasi, dan galeri media yang sudah disetujui admin. **Ini overlay source code, bukan aplikasi Laravel lengkap/vendor.**

## Perubahan V4
- Layout responsif baru, CTA konsultasi, daftar program dinamis, informasi orang tua, tahapan konsultasi.
- Landing page `/lp/kerja-jepang` memakai navigasi lebih ringkas.
- Galeri alumni hanya menampilkan media `is_public=true` dan `consent_verified=true`.
- Tidak menyertakan foto dokumen identitas dari HTML referensi.
- Seeder nomor WhatsApp diubah menjadi kosong hingga admin mengonfirmasi nomor resmi. Jika nomor WA belum valid, lead tetap disimpan dan pengguna diarahkan ke halaman penerimaan, bukan ke nomor rekaan.
- Tidak ada pixel pihak ketiga aktif, klaim keberangkatan baru, harga rekaan, atau janji penempatan kerja.

## Instalasi
1. Buat proyek Laravel 12 baru dengan `composer create-project laravel/laravel hikari` pada lingkungan yang memenuhi syarat.
2. Salin semua folder overlay V4 ke proyek Laravel baru, gabungkan dengan file bawaan Laravel (jangan hapus file framework).
3. Atur `.env`, `APP_KEY`, koneksi DB, SMTP dan nomor WA resmi melalui dashboard.
4. Jalankan `php artisan migrate`, `php artisan db:seed --class=HikariSeeder`, `php artisan storage:link`, `php artisan route:list`, `php artisan test`.
5. Buat admin dengan command yang disediakan V1, uji pengisian lead, galeri, dan izin akses pada database staging.

## Belum selesai
- Integrasi frontend HTML lama secara penuh; media lama tidak disalin karena memuat dokumen pribadi.
- Analytics/pixel dengan consent manager; editor media dan CMS visual penuh.
- Pengujian runtime, keamanan menyeluruh, aksesibilitas dan deployment produksi.
- Validasi nomor WhatsApp resmi, legalitas, biaya dan alamat oleh pemilik.

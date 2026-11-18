# LPK Hikari Sumut — Laravel V5 (Source Overlay)

V5 melanjutkan V4; **bukan instalasi Laravel lengkap**. Tidak termasuk `vendor`, framework, database nyata, maupun konfigurasi produksi.

## Penambahan
- Migrasi `faqs` dan `testimonials`.
- Admin `/admin/trust-content`: buat/edit/hapus FAQ dan testimoni; publikasi opsional.
- Testimoni tidak bisa dipublikasikan tanpa centang persetujuan terverifikasi. **Centang bukan bukti hukum**; pengelola tetap wajib menyimpan bukti izin yang valid secara terpisah.
- FAQ dan testimoni hanya muncul di beranda/landing page bila sudah diterbitkan; tidak ada konten atau klaim rekaan.
- Judul dan deskripsi hero beranda/landing page dapat diubah dari pengaturan admin.
- Tes fitur tambahan disiapkan tetapi **belum dijalankan pada Laravel runtime**.

## Cara memasang
1. Buat proyek Laravel 12 dengan Composer pada PHP yang kompatibel, lalu gabungkan folder overlay ini ke root Laravel (jangan menimpa file inti secara membabi buta).
2. Konfigurasikan `.env`, database, `APP_KEY`, dan storage sesuai README versi sebelumnya.
3. Jalankan `php artisan migrate`, `php artisan db:seed --class=HikariSeeder`, `php artisan route:list`, dan `php artisan test`.
4. Buat akun admin memakai perintah di `app/Console/Commands/CreateHikariAdmin.php`.
5. Verifikasi tampilan, validasi input, izin akses, upload, lead, dan database pada staging sebelum produksi.

## Catatan keamanan / keterbatasan
- Belum ada editor visual rich-text, audit keamanan menyeluruh, maupun consent manager analytics.
- Untuk testimoni, jangan memuat data pribadi tanpa izin dan jangan mengarang keberangkatan/hasil kerja.
- Source ini belum diuji secara runtime. Tidak ada jaminan siap deployment produksi.
- HTML referensi lama yang berpotensi memuat dokumen identitas pribadi tidak disertakan.

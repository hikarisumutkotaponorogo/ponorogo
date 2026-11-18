# LPK Hikari Sumut — Upgrade V2 (source overlay)

V2 meneruskan V1, menambahkan CMS halaman, artikel publik, jadwal follow-up, dan ekspor leads CSV. Semua data belum nyata; proyek **belum siap produksi**.

## Cara instalasi
1. Siapkan proyek Laravel 12 lengkap menggunakan Composer (lihat README.md V1).
2. Salin file overlay ini ke proyek Laravel, jangan menaruh root aplikasi di public_html.
3. Konfigurasikan .env, MySQL, APP_KEY dan HTTPS.
4. Jalankan `php artisan migrate` dan `php artisan db:seed --class="Database\Seeders\HikariSeeder"`.
5. Buat admin menggunakan `php artisan hikari:create-admin email@domain.tld`.
6. Uji `php artisan route:list`, `php artisan test`, form konsultasi, dan akses `/admin`.

## Yang baru
- `/admin/halaman`: tambah/edit konten halaman dengan ID, status draft/publikasi.
- `/admin/artikel`: tambah/edit artikel, tampil di `/artikel`.
- `/admin/follow-ups`: jadwal tindak lanjut leads.
- `/admin/leads/export`: CSV data leads (akses admin saja).
- `/halaman/{slug}`: halaman konten yang dipublikasikan.

## Catatan penting
- Form edit CMS V2 masih sederhana; mengedit dilakukan dengan memasukkan ID dan konten penuh. Belum ada media library, editor visual, maupun approval workflow.
- Foto referensi asli memuat dokumen identitas; **jangan publikasikan** sebelum izin dan penyamaran data sensitif.
- Jangan menyertakan file HTML referensi di folder publik hosting.
- Belum ada integrasi pixel, manajemen persetujuan cookie, dashboard pendaftaran terverifikasi, maupun pengujian runtime Laravel.
- Laravel/framework/vendor tidak dibundel. Source ini overlay untuk proyek Laravel 12, bukan aplikasi standalone yang dapat langsung dijalankan.

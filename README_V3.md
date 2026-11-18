# LPK Hikari Sumut — V3 Source Overlay

Paket ini melanjutkan V2. **Belum termasuk framework Laravel/vendor** dan **belum siap produksi**. Salin overlay ke instalasi Laravel 12 yang sesuai. Migrasi dan pengujian runtime wajib dijalankan sebelum digunakan.

## Tambahan V3
- `registrations`: pencatatan pendaftaran internal dengan status pending / verified / rejected / cancelled, verifikasi manual, dan log aktivitas lead.
- `media_assets`: unggah gambar JPG/PNG/WebP hingga 5 MB, awalnya draft, pemeriksaan izin publikasi dan konfirmasi sebelum status publik.
- Menu dashboard `/admin/registrations` dan `/admin/media`.
- Tidak ada klaim pembayaran otomatis atau penempatan kerja.

## Instalasi dan pengujian
1. Buat proyek Laravel 12 baru via Composer dan pasang file overlay V1–V3.
2. Pastikan autentikasi, tabel users, dan konfigurasi database sudah tersedia.
3. Jalankan `php artisan migrate`, `php artisan route:list`, `php artisan test`.
4. Jalankan `php artisan storage:link`. Draft disimpan di disk lokal privat; salinan baru dibuat di disk publik hanya setelah admin menyetujui publikasi.
5. Uji CRUD pendaftaran, penolakan duplikasi, upload, CSRF, dan hak akses dengan database uji.

## Keterbatasan yang harus diselesaikan
- Tinjau keamanan akses media, kebijakan privasi, validasi berkas sebenarnya, dan proses review oleh petugas sebelum go-live.
- Belum ada integrasi pixel, consent manager, visual editor, penagihan/pembayaran, maupun pengujian end-to-end.
- Foto asli dari HTML lama tidak disertakan karena memuat dokumen identitas. Penggunaan ulang harus melalui review privasi.
- Halaman publik masih template awal, belum setara desain HTML referensi.

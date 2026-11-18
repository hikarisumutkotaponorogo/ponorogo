# LPK Hikari Sumut — Laravel V6 (Source Overlay)

V6 melanjutkan V5. Paket **bukan aplikasi Laravel mandiri**: gunakan overlay ini di atas instalasi Laravel 12 yang kompatibel. `vendor/`, `.env`, `artisan`, framework dan database runtime tidak disertakan.

## Perubahan
- Dashboard `/admin/tracking`: pengaturan GA4, GTM, Meta Pixel, TikTok Pixel; semua ID opsional dan tervalidasi formatnya.
- Banner persetujuan tracking: **tidak memuat tag analytics/marketing sebelum pengunjung memilih setuju**. Pilihan tolak tidak memuat tag; tautan footer memungkinkan mengubah pilihan. Pilihan disimpan di localStorage browser.
- Integrasi page view untuk GA4, GTM, Meta dan TikTok setelah opt-in. Jangan menyalakan GA4 langsung dan GA4 melalui GTM sekaligus (duplikasi).
- Ringkasan sumber UTM dan jumlah leads 7 hari terakhir di dashboard; filter tanggal/sumber pada CRM.
- Tidak mengirim nama, nomor telepon atau data peserta ke analytics.

## Batasan / hal yang harus diuji
- **Belum menjalankan Laravel runtime, database, atau tes otomatis**; pemeriksaan PHP syntax saja.
- Validasi kepatuhan privasi, konfigurasi Consent Mode v2, kebijakan penyimpanan, CSP, cookies pihak ketiga, dan parameter konversi perlu ditinjau sebelum produksi.
- Persetujuan analytics dan marketing masih digabung menjadi satu kategori, untuk versi produksi sebaiknya dipisahkan.
- Tombol konsultasi WhatsApp bukan bukti pesan terkirim. Jangan mengekspor data peserta ke pixel.
- Kode ini belum menyediakan role-based permissions; route admin memakai `auth` seperti versi sebelumnya. Tambahkan otorisasi sebelum dipakai multi-petugas.
- Untuk pengujian, jalankan `php artisan migrate`, `php artisan route:list`, `php artisan test` dan uji browser di staging.
- Pastikan `.env` dan data dokumen identitas tidak disajikan di web root.

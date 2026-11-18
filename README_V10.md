# V10 — Hardening dan kesiapan pengujian

Paket ini adalah **source overlay kumulatif V1–V10**, bukan Laravel lengkap. Tidak ada klaim pengujian runtime berhasil.

## Perubahan
- CSV ekspor leads: teks berawalan `=`, `+`, `-`, `@` (termasuk setelah whitespace) diawali apostrof agar tidak dieksekusi sebagai rumus spreadsheet. Periksa kebijakan impor CSV aplikasi tujuan.
- Login: pengguna yang sudah login diarahkan ke dashboard; kegagalan login hanya mengembalikan email, tidak password.
- Pendaftaran: status `verified` tidak bisa diubah kembali ke `pending` tanpa prosedur koreksi khusus.
- Installer: koneksi SQLite lokal dicatat dalam `.env` agar migrasi dan pengujian tidak berbeda konfigurasi.
- Tes regresi baru untuk akses tanpa login, honeypot, dan nomor WA.

## Penggunaan
1. Siapkan PHP 8.3+, Composer 2 dan akses internet pada komputer pengembangan.
2. `bash tools/preflight_v9.sh`
3. `bash tools/integrate_laravel12.sh /path/baru/hikari-laravel-app`
4. Pastikan `php artisan test` benar-benar sukses dan audit error log.
5. Jangan deploy ke production sebelum seluruh tes, konfigurasi privasi, backup dan permission diverifikasi.

## Keterbatasan
Belum ada instalasi Laravel/vendor, database hidup, maupun pengujian browser dalam paket ini. Script integrasi adalah langkah persiapan, bukan bukti aplikasi siap pakai. Dokumen identitas peserta tidak boleh dipublikasikan tanpa redaksi dan izin.

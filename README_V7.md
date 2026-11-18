# Laravel V7 — Otorisasi & audit (source overlay)

V7 meneruskan V6. Tambahan: role `super_admin`, `director`, `marketing`, `enrollment`, `editor`, `viewer` dengan prinsip deny-by-default; audit login/logout, perubahan lead, settings, program dan publikasi/penghapusan media; halaman `/admin/audit`.

## Instalasi pada Laravel 12
1. Pasang Laravel 12 standar, salin overlay ini ke root proyek, **jangan timpa file framework secara membabi buta**.
2. Daftarkan `App\Providers\HikariAuthorizationServiceProvider::class` pada `bootstrap/providers.php` Laravel 12.
3. Pastikan model `App\Models\User` bawaan Laravel mengizinkan field `role` dalam `$fillable` jika hendak mengubah role via model; command create-admin memakai role.
4. Jalankan `php artisan migrate` setelah backup; buat akun awal dengan `php artisan hikari:create-admin email@domain.test`.
5. Akun yang sudah dibuat sebelum V7 akan mendapat role `viewer` (akses sangat terbatas); naikkan role secara aman via database/admin console oleh pemilik, bukan lewat form publik.
6. Uji `php artisan route:list`, `php artisan test`, setiap peran, login/logout, audit, dan upload media di staging.

## Batasan
- Belum menjalankan framework Laravel penuh, database, dan integration test. Lolos lint PHP **bukan** bukti fitur bekerja.
- Audit saat ini mencatat sejumlah aksi penting, **belum semua mutasi** (artikel, FAQ, follow-up, registrasi, tracking); perlu diperluas sebelum produksi.
- Log audit belum immutable dan belum punya kebijakan retensi.
- Tinjau risiko file unggahan, consent, ID dokumen, CSRF, session, error handling, dan backup sebelum produksi.
- Untuk V8, prioritas: membangun instalasi Laravel lengkap dan pengujian nyata, bukan menambah fitur yang belum teruji.

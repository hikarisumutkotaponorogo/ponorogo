# V12 — Audit named routes dan kesiapan integrasi

## Perubahan
- `tools/audit_routes_v12.py`: memeriksa nama route di Blade terhadap deklarasi route, termasuk prefix grup `admin.`. Menggantikan peringatan palsu audit V11.
- Installer sekarang menjalankan audit named routes **sebelum** membuat proyek Laravel.
- Audit V11 tetap tersedia untuk pemeriksaan controller, model, dan view.

## Pemeriksaan offline
```bash
python3 tools/audit_v11.py
python3 tools/audit_routes_v12.py
python3 tools/check_routes.py
bash -n tools/integrate_laravel12.sh
```

## Integrasi runtime (belum dijalankan)
```bash
bash tools/integrate_laravel12.sh /path/baru/hikari-app
```
Memerlukan Composer 2, PHP 8.3+, koneksi internet, dan ekstensi PHP yang sesuai. Installer membuat Laravel 12 baru, menyalin overlay, menggunakan SQLite untuk tes lokal, dan menjalankan migrasi, seeder, route:list, serta tes. **Jangan menjalankannya di folder produksi.**

## Batasan
Paket masih source overlay, belum instalasi Laravel siap pakai. Audit ini hanya statis; hasilnya bukan bukti aplikasi berjalan. Belum ada pengujian database, browser, keamanan menyeluruh, atau deployment.

# V14 — Uji alur konsultasi dan audit database

V14 adalah kelanjutan source overlay V13. Penambahan utama adalah empat feature test untuk alur formulir konsultasi, validasi, pencatatan lead dan aktivitas, halaman konfirmasi, serta redirect WhatsApp. Ada pula audit statis untuk tabel migration dan pemeriksaan ekstensi PHP sebelum installer berjalan.

## Pemeriksaan tanpa Composer

```bash
python3 tools/audit_routes_v12.py
python3 tools/audit_v13.py
python3 tools/audit_migrations_v14.py
bash -n tools/integrate_laravel12.sh
find app database routes tests -name '*.php' -print0 | xargs -0 -n1 php -l
```

## Pengujian runtime (memerlukan Composer dan internet)

```bash
bash tools/integrate_laravel12.sh /path/ke/folder-baru/hikari-app
```

Installer hanya untuk mesin pengembangan dan menolak folder tujuan yang sudah ada. Pengujian tidak dijalankan saat membangun paket ini karena Composer tidak tersedia. Jangan gunakan pada hosting produksi sebelum semua tes berhasil.

**Batasan:** Source masih overlay, belum menyertakan Laravel/vendor. Data legalitas, program, foto, harga, dan nomor kontak harus diverifikasi sebelum publikasi. Jangan mengunggah dokumen pribadi tanpa penyamaran informasi sensitif.

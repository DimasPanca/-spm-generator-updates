# SPM Generator — Saluran Update

Repo ini hanya menyimpan berkas update untuk aplikasi **SPM Generator**.
Kode sumber aplikasinya tidak ada di sini.

| Berkas | Fungsi |
|---|---|
| `manifest.json` | Dicek aplikasi tiap kali dibuka, berisi nomor versi terbaru |
| `update.zip` | Paket update (~18 MB) yang diunduh client |

Aplikasi client membaca kedua berkas ini lewat `raw.githubusercontent.com`.
Jangan mengubah nama berkasnya — alamat itu sudah tertanam di aplikasi
yang sudah tersebar.

## Yang ikut dalam update

Hanya berkas program: hasil build (`.next`), kode dan template (`src`),
serta schema + migrasi database (`prisma`).

Data sekolah **tidak pernah** ikut dan tidak pernah tersentuh oleh update:
database (`dev.db`), logo yang diunggah (`public/uploads`), dan dokumen
yang sudah digenerate (`storage`).

## Cara merilis versi baru

Dari folder proyek aplikasi:

```bash
npm run build
node scripts/make-update.mjs 1.1.0 "Keterangan singkat perubahan"
```

Lalu salin `release/manifest.json` dan `release/update.zip` ke repo ini,
commit, dan push.

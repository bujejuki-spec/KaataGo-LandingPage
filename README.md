# KaataGo Web

Landing page promosi + halaman unduh APK untuk **KaataGo**, aplikasi kasir &
self-order untuk resto Indonesia.

Repo ini sengaja **terpisah** dari repo aplikasi Flutter-nya. Keduanya punya
siklus rilis yang berbeda — halaman ini bisa diubah kapan saja tanpa menyentuh
aplikasi, dan sebaliknya — dan hosting statis tidak perlu menarik seluruh
source code aplikasi hanya untuk menayangkan satu halaman.

## Isi

| File | Keterangan |
| --- | --- |
| `index.html` | Seluruh halaman: markup, CSS, dan JS jadi satu file, tanpa dependensi eksternal |
| `kaata-icon.png` | Logo KaataGo, dipakai untuk brand, favicon, dan preview share |

## Menjalankan lokal

Tidak perlu build step apa pun. Buka `index.html` langsung di browser, atau:

```bash
python3 -m http.server 8000
```

## Deploy

Karena halamannya statis penuh, folder ini bisa langsung di-drop ke hosting
statis mana pun:

- **Netlify** — tarik foldernya ke [app.netlify.com/drop](https://app.netlify.com/drop)
- **Vercel** — `vercel deploy`
- **GitHub Pages** — Settings → Pages → deploy dari branch `main`
- **cPanel / shared hosting** — upload isi folder ke `public_html`

## Dua nilai yang perlu diisi

Keduanya ada di blok `<script>` paling bawah `index.html`:

| Variabel | Fungsi |
| --- | --- |
| `APK_URL` | Alamat unduh APK. Untuk Google Drive gunakan bentuk `drive.usercontent.google.com/download?id=<ID>&export=download&confirm=t` — link `/view` hanya membuka pratinjau, dan `uc?export=download` masih menyisipkan halaman peringatan virus untuk file sebesar ini. |
| `WA_NUMBER` | Nomor WhatsApp tim sales untuk tombol "Tanya harga & promo". Format internasional tanpa `+`, contoh `6281234567890`. Kalau kosong, tombolnya memberi tahu bahwa nomornya belum dipasang. |

Nomor versi APK ditulis manual di bagian download (`Versi <code>…</code>`) —
perbarui saat merilis versi baru.

## Catatan

Kode QR pada animasi HP di hero **digambar, bukan QR asli** dan tidak bisa
dipindai. Ini disengaja: QR yang benar-benar bisa dipindai di halaman promosi
berisiko dikira tautan pembayaran sungguhan oleh pengunjung.

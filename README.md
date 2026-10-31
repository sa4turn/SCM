# ManuLink — Prototipe SCM Mobile

## Langsung buka

1. Ekstrak ZIP terlebih dahulu (Extract All / Ekstrak semua).
2. Buka folder SCM_Mobile.
3. Klik dua kali index.html untuk membuka di Chrome, Edge, atau Firefox terbaru.

Tidak perlu npm, instalasi library, server, atau koneksi internet. Pastikan index.html, style.css, dan app.js tetap dalam folder yang sama. Tampilan di komputer dibatasi selebar layar handphone. Di browser handphone, layout mengikuti lebar layar.

## Edit di VS Code

Gunakan File > Open Folder lalu pilih SCM_Mobile. Edit index.html (kerangka), style.css (tampilan), atau app.js (data dan interaksi). Simpan lalu refresh browser. Live Server opsional; bukan syarat untuk menjalankan demo.

## Yang bisa dicoba

- Dashboard dengan jumlah PO aktif, pengiriman terlambat, dan stok kritis yang dihitung dari data.
- Empat modul: pengadaan, persediaan, pemasok, dan pesanan pelanggan.
- Pencarian dan filter; halaman detail tiap modul.
- Form PO baru dengan validasi jumlah, pemasok sesuai material, dan tanggal.
- Pencatatan penerimaan sebagian atau seluruh barang; stok fisik bertambah otomatis.
- Pembaruan stok fisik disertai alasan.
- Risiko berbasis aturan: pengiriman melewati tanggal janji dengan barang belum lengkap, atau stok di bawah minimum.
- Catatan dan status tindak lanjut; riwayat penerimaan dan perubahan stok.
- Pemasok alternatif dan draf pesan / koordinasi. Tidak ada pesan sungguhan yang dikirim.
- Tema Material Light dan mode gelap yang terinspirasi Drafting Blue dari Codex Material Themes.
- Ekspor data simulasi ke JSON dan reset demo dengan konfirmasi.

## Skenario presentasi

1. Beranda > Tinjau risiko > Baut M8.
2. Cek stok 80 unit, batas minimum 100 unit, dan kebutuhan produksi 200 unit. Kekurangan produksi = 120 unit.
3. Cek PO-024: 500 unit, tanggal janji 28 Oktober 2026, terlambat tiga hari pada tanggal skenario.
4. Buka pemasok alternatif > PT Mitra Fastener > Buat PO. Simpan pembelian baru; stok fisik belum bertambah.
5. Kembali ke risiko Baut M8, isi catatan tindak lanjut, ubah status ke Diproses.
6. Buka PO-024 lalu Catat penerimaan barang: 500 unit. Stok Baut M8 menjadi 580 unit, PO diterima lengkap, risiko material terselesaikan karena kedua pemicunya hilang.
7. Buka Pemantauan risiko > Selesai untuk melihat riwayat. Reset melalui Akun bila ingin mengulang.

## Batasan demo

- Tanggal perhitungan dikunci ke 31 Oktober 2026 di konstanta NOW dalam app.js, bukan tanggal komputer. Ini menjaga skenario konsisten.
- Seluruh nama, email, jumlah, lead time, dan pesanan adalah simulasi. Estimasi lead time tidak menjamin ketersediaan pemasok.
- Ini prototipe frontend, bukan aplikasi produksi. Tidak ada autentikasi, backend, sinkronisasi multiuser, pengiriman email, AI, ataupun pemesanan sungguhan.
- localStorage menyimpan perubahan apabila diizinkan browser. Perilaku penyimpanan untuk file lokal dapat berbeda antar-browser; aplikasi tetap berjalan dalam memori bila penyimpanan diblokir. Ekspor JSON untuk menyimpan salinan data (belum ada fitur impor).
- Stok belum dialokasikan antar-pesanan. Status Siap material berarti kecukupan material contoh, bukan produksi selesai.
- Risiko Selesai ditentukan dari pemicu aktual, bukan ditandai selesai manual ketika masalah masih ada.
- Drafting Blue dipakai sebagai inspirasi palet aplikasi; tidak mengubah tema Codex atau VS Code.

## Referensi teknis dan warna

- MDN Web Docs — localStorage dan batasan file URL: https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage
- Codex Material Themes — Drafting Blue: surface #163A52, ink #DCE8EC, accent #E0B85C, dari katalog plugin yang dipilih pengguna.

Semua ikon dibuat dengan SVG inline; tidak ada aset atau font dari CDN.

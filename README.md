# ManuLink — SCM Mobile / Material Panels Edition (V3)

## Buka langsung

1. Ekstrak ZIP ke folder baru.
2. Masuk ke folder SCM_Mobile.
3. Klik dua kali index.html untuk membuka di Chrome, Edge, atau Firefox terbaru.

Tanpa npm, server, koneksi internet, atau aset CDN. index.html, style.css, dan app.js harus tetap berada di folder yang sama. Di komputer, tampilan dibatasi selebar handphone; di HP, mengikuti lebar layar.

Untuk mengedit: buka folder SCM_Mobile di VS Code, ubah file, simpan, lalu refresh browser. Live Server opsional.

## Tampilan dan navigasi

Susunan kembali ke empat modul utama: Pengadaan, Persediaan, Pemasok, dan Pesanan. Tiap modul menggunakan panel berwarna dan ringkasan data, bukan teks di atas halaman putih.

- Pengadaan: biru; progres jumlah barang diterima dan hitung mundur jadwal tiba.
- Persediaan: hijau; stok fisik, batas minimum, dan kebutuhan produksi.
- Pemasok: emas; profil, material, lead time estimasi, dan alternatif.
- Pesanan pelanggan: ungu; kecukupan bahan untuk pesanan masuk.
- Risiko: kartu merah muda untuk keterlambatan, emas untuk stok, dan biru untuk pemantauan jadwal dekat.
- Beranda: dashboard, empat modul, ringkasan pengiriman, dan tab Aktivitas Tim.
- Tombol lingkaran setengah di header: ganti mode terang / Drafting Blue.
- Panduan empat langkah tersedia dari beranda dan Akun.

Palet mode gelap diambil dari Drafting Blue pada katalog Codex Material Themes: surface #163A52, ink #DCE8EC, accent #E0B85C. Tema tidak mengubah Codex atau VS Code; seluruh komponen app dibuat khusus untuk prototipe ini.

## Interaksi yang bisa dicoba

- Cari dan filter pembelian, material, pemasok, pesanan, dan risiko.
- Tambah PO; pemasok difilter sesuai material yang dipilih.
- Catat konfirmasi pengiriman dengan informasi yang diterima dari pemasok.
- Catat penerimaan sebagian / penuh; stok bertambah sesuai jumlah yang diterima.
- Perbarui stok fisik dengan alasan perubahan.
- Cek pemasok alternatif dan draf pesan koordinasi; tidak ada pesan sungguhan yang dikirim.
- Simpan tindak lanjut risiko dan lihat aktivitas tim.
- Ekspor data ke JSON atau reset demo melalui Akun.

## Aturan pemantauan untuk RQ2

Tanggal skenario tetap: 31 Oktober 2026, didefinisikan dalam konstanta NOW.

1. Mendekati jatuh tempo: jadwal tiba 0–2 hari lagi dan barang belum diterima lengkap. Ini peringatan pemantauan awal, bukan prediksi pasti terlambat.
2. Perlu konfirmasi: kondisi nomor 1 ditambah belum ada konfirmasi pengiriman yang tercatat.
3. Sudah terlambat: tanggal janji sudah lewat dan penerimaan belum lengkap.
4. Stok kritis: stok fisik di bawah batas minimum. Kondisi ini terpisah dari indikator keterlambatan supplier.

Konfirmasi pengiriman tidak menambah stok atau menghapus peringatan jadwal dekat. PO perlu dipantau sampai barang diterima. Peringatan untuk suatu material selesai ketika tidak ada lagi pemicu aktif. Jumlah PO dan material dipantau tidak sama, karena satu material bisa memiliki lebih dari satu PO.

## Contoh demonstrasi

A. Keterlambatan yang sudah terjadi:
1. Beranda > Risiko > Baut M8.
2. Lihat stok 80 unit, minimum 100 unit, kebutuhan produksi 200 unit: kekurangan produksi 120 unit.
3. Cek PO-024: pembelian 500 unit, janji 28 Oktober 2026, telat 3 hari.
4. Cek pemasok / alternatif dan simpan catatan tindak lanjut.
5. Pada simulasi barang sudah tiba, buka PO-024 > Catat penerimaan barang > 500 unit.
6. Stok menjadi 580 unit. Risiko Baut M8 selesai; material lain bisa tetap dalam pemantauan.

B. Peringatan sebelum tanggal janji:
1. Pengadaan > Mendekati jatuh tempo > PO-026 (Kemasan).
2. Jadwal tiba 1 November 2026; belum ada konfirmasi pengiriman.
3. Catat konfirmasi dengan informasi dari pemasok. Stok tidak berubah.
4. Peringatan Perlu konfirmasi hilang dari ringkasan, tetapi jadwal dekat tetap dipantau sampai barang diterima.

## Batasan prototipe

Data, identitas, email, lead time, dan seluruh transaksi bersifat simulasi. Ini frontend tanpa backend, autentikasi, sinkronisasi multiuser, AI, pengiriman pesan, atau pemesanan sungguhan. Stok belum dialokasikan antar-pesanan; Siap material bukan berarti produksi selesai.

Perubahan disimpan di localStorage jika diizinkan browser. Perilaku penyimpanan untuk file lokal dapat berbeda antar-browser; aplikasi tetap berfungsi dalam memori bila diblokir. Ekspor JSON untuk menyimpan salinan (fitur impor belum tersedia). V3 memakai ruang penyimpanan demo terpisah agar perubahan skenario tidak menimpa demo versi lama.

Pengecekan logika mencakup 15 halaman, validasi form, penerimaan sebagian/penuh, pembaruan stok, konfirmasi pemasok, ambang 0–2 hari, filter, catatan, tema, dan tab dashboard. Pengujian visual menggunakan browser otomatis belum berhasil dijalankan di lingkungan pembuatan.

Referensi localStorage: https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage

# Kalkulator HPP & Harga Jual UMKM

Alat bantu **gratis** untuk menghitung Harga Pokok Produksi/Penjualan (HPP) per unit dan merancang harga jual. Berjalan di browser, tanpa daftar, tanpa mengirim angka ke server.

Dibuat [Tim LarisHQ](https://larishq.com). Lisensi MIT.

**Buka kalkulator:** buka `index.html` di browser, atau (setelah Pages aktif) unduh/jalankan dari GitHub Pages repo ini.

## Yang bisa dihitung

- **Mode Produksi:** bahan baku + kemasan + tenaga kerja + overhead, dibagi jumlah unit yang layak jual.
- **Mode Reseller / dropship:** harga beli + ongkir masuk + kemasan + biaya lain, dibagi jumlah yang layak jual. Untuk dropship, isi jumlah unit 1.
- **Harga saran margin** (dari harga jual) dan **harga saran markup** (dari HPP), bersebelahan, supaya keduanya tidak tertukar.
- **Potongan marketplace (opsional):** Anda sendiri yang mengisi persentase dan biaya tetap per pesanan. Alat ini tidak menyimpan tarif resmi, karena angkanya berubah per kategori dan per periode.

Semua input adalah angka Anda. Tombol "Isi contoh" hanya mengisi contoh produksi keripik agar rumusnya mudah dicek, bukan data penjualan.

## Rumus

```
HPP per unit = total biaya satu batch (atau satu belanja stok) ÷ jumlah unit yang layak jual
```

HPP dibulatkan ke atas, ke rupiah penuh.

```
Harga (margin)  = HPP ÷ (1 − margin)
Harga (markup)  = HPP × (1 + markup)
```

Margin dihitung dari harga jual. Markup dihitung dari HPP. Target 30% pada kedua cara ini **tidak** menghasilkan harga yang sama.

Kalau ada potongan kanal:

```
Uang diterima ≈ harga jual − (harga jual × potongan %) − biaya tetap per pesanan

Harga minimum = (HPP + biaya tetap) ÷ (1 − margin − potongan %)
```

Syarat: (margin + potongan %) < 100%. Isi potongan sesuai Seller Centre toko Anda, bukan dari ingatan.

Biaya admin, biaya program, iklan, dan ongkir ke pembeli **bukan** komponen HPP. Itu biaya penjualan, dihitung terpisah saat menentukan harga jual.

## Cara menjalankan

Tidak perlu instal apa pun.

```bash
git clone https://github.com/larishq/kalkulator-hpp-umkm.git
cd kalkulator-hpp-umkm
```

Lalu buka `index.html` (klik dua kali, atau seret ke jendela browser). Bisa juga dilayani secara lokal:

```bash
python3 -m http.server 8080
```

Setelah GitHub Pages diaktifkan, alamat publiknya: `https://larishq.github.io/kalkulator-hpp-umkm/` (usulan; cek halaman repo jika berbeda).

## Rumus siap tempel di Google Sheets

| Isi | Rumus |
|---|---|
| Total biaya | `=Bahan+Kemasan+Tenaga+Overhead` |
| HPP per unit (ke atas) | `=IF(Unit<=0;"";ROUNDUP(Total/Unit;0))` |
| Harga saran margin | `=IF(OR(Unit<=0;Margin>=1);"";ROUNDUP(HPP/(1-Margin);0))` |
| Harga saran markup | `=IF(Unit<=0;"";ROUNDUP(HPP*(1+Markup);0))` |
| Harga min. setelah potongan | `=IF((Margin+Potongan)>=1;"";ROUNDUP((HPP+BiayaTetap)/(1-Margin-Potongan);0))` |

Ganti nama sel sesuai sheet Anda. Di locale Indonesia, pemisah argumen adalah titik koma (`;`). Kalau Sheet Anda berlocale English, ganti menjadi koma.

## Privasi

Hitungan berjalan di perangkat Anda. Tidak ada cookie, pixel, atau pengiriman formulir.

## Kontribusi

Masalah rumus, aksesibilitas, atau terjemahan boleh dibuka lewat issue/pull request. Mohon jangan menambahkan pelacak, iklan, atau tautan afiliasi.

## Lisensi dan atribusi

[MIT](LICENSE). © 2026 Tim LarisHQ.

Versi yang sama, dengan panduan langkah demi langkah, ada di [larishq.com/kalkulator-hpp](https://larishq.com/kalkulator-hpp). Repo ini berdiri sendiri dan bisa dipakai tanpa membuka situs itu.

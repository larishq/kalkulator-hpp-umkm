# Kalkulator HPP UMKM

Alat bantu **gratis** untuk menghitung Harga Pokok Produksi/Penjualan (HPP) per unit. Berjalan di browser, tanpa daftar, tanpa mengirim angka ke server.

Dibuat [Tim LarisHQ](https://larishq.com). Lisensi MIT.

**Buka kalkulator:** buka `index.html` di browser, atau (setelah Pages aktif) unduh/jalankan dari GitHub Pages repo ini.

## Yang bisa dihitung

- **Mode Produksi:** bahan baku + kemasan + tenaga kerja + overhead, dibagi jumlah unit yang layak jual.
- **Mode Reseller / dropship:** harga beli + ongkir masuk + kemasan + biaya lain, dibagi jumlah yang layak jual. Untuk dropship, isi jumlah unit 1.

Semua input adalah angka Anda. Tombol "Isi contoh" hanya mengisi contoh produksi keripik agar rumusnya mudah dicek, bukan data penjualan.

Alat ini berhenti di HPP per unit. Harga jual minimum setelah potongan marketplace (Shopee, Tokopedia, TikTok Shop, WA) tidak dihitung di sini; itu ada di [Kalkulator Harga Jual Anti Rugi](https://lynk.id/radagon99/g39xk0wnq4x9) (Rp39.000).

## Rumus

```
HPP per unit = total biaya satu batch (atau satu belanja stok) ÷ jumlah unit yang layak jual
```

HPP dibulatkan ke atas, ke rupiah penuh.

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

Versi yang sama, dengan panduan langkah demi langkah, ada di [larishq.com/kalkulator-hpp](https://larishq.com/kalkulator-hpp).

## Rumus siap tempel di Google Sheets

| Isi | Rumus |
|---|---|
| Total biaya | `=Bahan+Kemasan+Tenaga+Overhead` |
| HPP per unit (ke atas) | `=IF(Unit<=0;"";ROUNDUP(Total/Unit;0))` |

Ganti nama sel sesuai sheet Anda. Di locale Indonesia, pemisah argumen adalah titik koma (`;`). Kalau Sheet Anda berlocale English, ganti menjadi koma.

## Privasi

Hitungan berjalan di perangkat Anda. Tidak ada cookie, pixel, atau pengiriman formulir.

## Kontribusi

Masalah rumus, aksesibilitas, atau terjemahan boleh dibuka lewat issue/pull request. Mohon jangan menambahkan pelacak, iklan pihak ketiga, atau tautan afiliasi. Tautan ke produk Tim LarisHQ yang sudah ada di halaman ini biarkan utuh.

## Lisensi dan atribusi

[MIT](LICENSE). © 2026 Tim LarisHQ.

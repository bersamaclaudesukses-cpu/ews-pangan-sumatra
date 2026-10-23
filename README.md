# Prototipe EWS Ketahanan Pangan Sumatra

Dashboard WebGIS untuk mengeksplorasi risiko ketahanan pangan pada 154 kabupaten/kota di sepuluh provinsi Sumatra. Font antarmuka Times New Roman.

## Buka dashboard

Buka situs GitHub Pages pada menu **Settings → Pages → Visit site** setelah publikasi selesai. Untuk penggunaan offline, unduh `index.html` dan buka dengan browser yang mendukung JavaScript. Tidak memerlukan instalasi Python atau backend untuk memakai dashboard.

## Fitur

- Peta interaktif dan filter wilayah.
- Pilihan baseline IKP tahun sebelumnya, Random Forest, dan LightGBM.
- Rekomendasi model berdasarkan validasi 2022–2023, terpisah dari hasil evaluasi akhir.
- Pilihan aturan peringatan: ambang skor, prioritas deteksi, daftar pantau terbatas, atau eksplorasi ambang.
- Perbandingan MAE, RMSE, R², precision, recall, dan kesalahan peringatan.
- Simulator model 2024, indikator perbedaan keputusan antarmodel, serta unduhan CSV.

## Status penelitian

**Ini prototipe penelitian, belum EWS operasional yang mengambil data terbaru secara otomatis.** Periode yang disajikan adalah evaluasi historis 2024 dan snapshot provisional 2025. Prediksi IKP tidak sama dengan prediksi kejadian shortage pangan. Angka simulasi tidak menunjukkan dampak kausal suatu intervensi.

Pengunjung dapat menyalin seluruh data agregat, parameter model, dan kode yang dikirim ke browser. Repositori dan situs ini ditujukan untuk publikasi; tidak memuat mikrodata individu/rumah tangga, kredensial, atau berkas model Python.

## Arsitektur

Dashboard bersifat statis. Prediksi historis sudah dihitung sebelumnya, lalu disematkan dalam HTML. Simulator menjalankan pohon model di browser. Filter, peta, dan ekspor CSV juga bekerja di browser. Tidak ada server Python, basis data, akun pengguna, atau API privat dalam versi ini.

Untuk pembaruan berkala, pengelola perlu menjalankan pipeline data dan model yang telah divalidasi, membangun ulang HTML, kemudian memperbarui `index.html` di repositori. Backend bukan syarat untuk pola pembaruan batch tersebut. Jika diperlukan data dinamis, login, penyimpanan input, atau log keputusan terpusat, lihat [IMPLEMENTASI.md](IMPLEMENTASI.md).

## Publikasi GitHub Pages

1. Buat repositori publik khusus dashboard pada akun pemilik penelitian.
2. Unggah isi folder publikasi ini ke akar repositori, termasuk `index.html`.
3. Buka **Settings → Pages → Build and deployment**.
4. Pilih **Deploy from a branch**, branch **main**, folder **/(root)**, lalu **Save**.
5. Tunggu deployment Pages berhasil, lalu buka tautan **Visit site**. Jangan membagikan tautan sebelum situs selesai diuji.

Repositori ini tidak memerlukan workflow GitHub Actions khusus, build command, secret, atau dependency. GitHub menangani publikasi Pages dari branch yang dipilih. HTTPS disediakan GitHub Pages.

## Menguji sebelum dibagikan

- Peta menampilkan 154 wilayah pada seluruh Sumatra.
- Evaluasi 2024 dengan aturan IKP <60,5 menghasilkan 15 peringatan baseline, 11 Random Forest, dan 10 LightGBM.
- Daftar pantau 20 menghasilkan tepat 20 peringatan se-Sumatra.
- Pencarian, pergantian model, detail wilayah, simulator dan unduhan CSV berfungsi.
- Pengguna memahami label 2024 historis dan 2025 provisional.

## Reproduksi dan pengembangan

Halaman ini adalah keluaran deployment. Kode pelatihan, data mentah dan notebook pengembangan tidak disertakan. Untuk pengembangan, gunakan pipeline penelitian yang diaudit terpisah; jangan mengubah prediksi langsung di HTML untuk meningkatkan metrik. Setiap pembaruan sebaiknya mencatat periode data, versi model, hasil validasi, dan keterbatasannya.

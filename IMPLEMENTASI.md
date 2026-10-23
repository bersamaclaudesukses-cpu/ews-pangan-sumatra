# Panduan implementasi dan kebutuhan backend

## Yang dapat dilakukan versi ini

Juri atau peninjau dapat membuka URL, membandingkan tiga model, memeriksa prediksi historis per wilayah, mengubah aturan peringatan, menjalankan simulasi, dan mengunduh hasil tampilan. Tidak ada konfigurasi server atau akun aplikasi bagi pengunjung.

## Yang belum tersedia

- Pengambilan data terbaru otomatis dan prediksi operasional untuk periode mendatang.
- Login aplikasi dan pemisahan kewenangan pengguna.
- Penyimpanan perubahan input, hasil pemeriksaan lapangan, atau catatan keputusan antar pengguna.
- Integrasi API dinas, basis data dinamis dan audit log server.
- Validasi prediksi IKP tingkat kecamatan atau prediksi kejadian shortage.

## Tahap implementasi yang disarankan

1. Tetapkan pemilik data dan frekuensi pembaruan. Verifikasi tanggal rilis, kode wilayah, definisi indikator, dan kualitas target.
2. Lengkapi audit pipeline, termasuk kehilangan data hujan Tanjungbalai dan keselarasan kode antar sumber. Perbaikan data harus disertai pelatihan ulang dan evaluasi.
3. Pilih model dan aturan peringatan memakai data validasi. Uji pada waktu yang belum digunakan untuk memilih model; jangan memakai kinerja satu tahun sebagai jaminan.
4. Jalankan pilot dengan verifikasi lapangan. Catat peringatan benar, peringatan keliru, kejadian terlewat, dan waktu tindak lanjut.
5. Untuk pembaruan batch, jalankan pipeline Python di lingkungan terkontrol lalu unggah ulang hasil HTML. GitHub Pages tetap dapat digunakan tanpa backend aplikasi.
6. Jika perlu pembaruan dinamis atau log keputusan bersama, pisahkan antarmuka statis, API autentikasi/prediksi, basis data, dan proses pembaruan terjadwal. GitHub Pages hanya melayani antarmuka statis; backend ditempatkan di layanan lain.

## Publikasi dan akses

Repositori publik dan GitHub Pages membuat berkas yang disajikan dapat diakses orang lain. Menyembunyikan tombol unduh tidak melindungi data yang sudah dikirim ke browser. Untuk model atau data yang harus dirahasiakan, proses prediksi perlu dipindahkan ke layanan server dengan kontrol akses, dan keluaran browser dibatasi sesuai kebutuhan.

Jangan mengunggah mikrodata survei, token, berkas `.env`, atau materi berlisensi terbatas ke repositori ini. Berkas `index.html` publik hanya memuat data agregat dan model yang memang digunakan antarmuka.

## Pemeriksaan setelah deployment

Pastikan URL memakai HTTPS, seluruh menu berfungsi, tidak ada permintaan aset ke localhost, dan unduhan CSV bekerja. Gunakan URL situs Pages untuk juri, bukan URL repositori atau alamat localhost pengembangan.

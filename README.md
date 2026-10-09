# Homework 6 — My First Compose App

## Task 3: Colour and Spacing
Colour used: Color.LightGray
Padding kept: 48.dp
What changed / what stayed the same: Saat padding diubah dari 8 dp ke 48 dp,
jarak antara tepi layar dan isi Column berubah. Dengan 8 dp, teks dan gambar
menempel dekat ke tepi, sedangkan dengan 48 dp isinya bergeser ke dalam dan ruang
kosong di sekelilingnya jauh lebih besar. Warna abu-abu Surface, isi teks, ukuran
gambar, dan urutan elemen tidak berubah. Padding ini mirip dengan margin
bergaris kuning di Module M06 Figure 13, yaitu ruang kosong di sekitar isi Column.

## Task 4: Build Error
First error message:
'M' is not a valid file-based resource name character: File-based resource names
must contain only lowercase a-z, 0-9, or underscore
(file: app/src/main/res/drawable/My-Picture.png, task :app:packageDebugResources)

Cause: Nama file resource hanya boleh berisi huruf kecil a-z, angka 0-9, dan
underscore. "My-Picture.png" memakai huruf besar (M dan P) dan tanda hubung (-),
jadi pelanggaran pertama yang terdeteksi adalah huruf besar "M".

Why other errors appear: Karena file tidak valid, Android tidak membuat ID
R.drawable.my_picture. Kode yang memanggil R.drawable.my_picture lalu menjadi
"unresolved reference". Itu error turunan dari error pertama.

Fix: Nama file dikembalikan menjadi my_picture.png, lalu project di-build ulang
dan berhasil.

## Task 5: Explore the Project
(a) MainActivity: path app/src/main/java/com/example/myfirstcomposeapp/MainActivity.kt
— file yang berisi class MainActivity, titik masuk aplikasi yang memanggil setContent.
(b) Gradle file: path app/build.gradle.kts — mengatur konfigurasi modul app
seperti versi SDK, dependency, dan fitur Compose.
(c) Launcher image line: painter = painterResource(id = R.drawable.ic_launcher_foreground)
— baris di MyFirstScreen yang memuat gambar ikon peluncur bawaan.

## Task 6: Preview vs Run
Aku mengubah teks pertama menjadi "Hi! I am Parid, Informatics UII." lalu
menekan Build & Refresh di Preview. Teks di Preview langsung berubah, tetapi
aplikasi di emulator masih menampilkan teks lama. Itu karena Preview hanya
menggambar ulang composable di dalam Android Studio, sedangkan aplikasi di
emulator adalah hasil build sebelumnya yang sudah terpasang. Agar perubahan
muncul di emulator, aku harus menekan Run supaya kode di-build ulang dan
dipasang (install) lagi ke perangkat.

## Task 7: Views vs Compose
1. Pada Views (imperatif), aku membuat tampilan lebih dulu (biasanya di XML),
   lalu mengubahnya lewat perintah, misalnya mengambil sebuah TextView dan mengatur
   teksnya dengan kode. Pada Compose (deklaratif), aku cukup mendeskripsikan seperti
   apa tampilan itu. Di fungsi MyFirstScreen, aku menulis Column yang berisi dua Text
   dan satu Image, dan Compose yang menggambarnya. Kalau aku mengubah teks di dalam
   Text lalu menjalankan ulang, tampilannya mengikuti deskripsi yang baru tanpa aku
   perlu memberi perintah untuk mengubah elemen tertentu.
2.

| Composable | Package | Library layer |
|---|---|---|
| Column | androidx.compose.foundation.layout | Foundation |
| Text | androidx.compose.material3 | Material |
| Image | androidx.compose.foundation | Foundation |
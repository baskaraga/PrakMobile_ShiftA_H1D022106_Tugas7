# PrakMobile_ShiftA_H1D022106_Tugas7
# Aplikasi Login Ionic dengan Auth Guards

## Penjelasan Cara Kerja

Aplikasi ini menerapkan autentikasi berbasis API menggunakan kombinasi **Angular**, **Ionic**, dan **PHP API** untuk memastikan bahwa hanya pengguna yang berhasil login dapat mengakses halaman tertentu. Berikut adalah prosesnya secara rinci:

1. **Database dan API**  
   - Database bernama `coba-ionic` memiliki tabel `user` untuk menyimpan data seperti `username` dan `password`, yang dienkripsi menggunakan **MD5**.
   - API berbasis PHP dibuat untuk menangani permintaan login dari aplikasi. Jika `username` dan `password` sesuai dengan data di database, API mengembalikan respons berupa **token** dan status `berhasil`.

2. **Authentication Service**  
   - Aplikasi Ionic menggunakan `services/authentication.service.ts` untuk menangani login, menyimpan token, dan mengelola status autentikasi melalui **Capacitor Preferences**.
   - Service ini mencakup fungsi untuk menyimpan token, memverifikasi status login, dan menyediakan notifikasi terkait autentikasi.

3. **Halaman Login**  
   - Di `login.page.ts`, pengguna memasukkan `username` dan `password` lalu menekan tombol login.
   - Data login dikirim ke API menggunakan metode **POST**. Jika API merespons dengan status `berhasil`, token dan data pengguna disimpan, dan pengguna diarahkan ke halaman `Home`. Jika gagal, aplikasi menampilkan pesan kesalahan.

4. **Auth Guards**  
   - **Auth Guard** (`guards/auth.guard.ts`): Melindungi halaman `Home` agar hanya pengguna yang sudah login dapat mengaksesnya. Pengguna yang belum login akan diarahkan ke halaman login.
   - **Auto Login Guard** (`guards/auto-login.guard.ts`): Mencegah pengguna yang sudah login mengakses kembali halaman login. Mereka akan diarahkan langsung ke halaman `Home`.

5. **Proses Logout**  
   - Pada halaman `Home`, fungsi `logout()` di `home.page.ts` memungkinkan pengguna keluar dari aplikasi. Fungsi ini menghapus token dan status login dari penyimpanan lokal dan mengarahkan pengguna kembali ke halaman login.

## Screenshot Tampilan
![image](https://github.com/user-attachments/assets/100e0fae-bb4f-4584-b9fb-6eedb01d6d55)
![image](https://github.com/user-attachments/assets/aa1a81ce-af4e-49b0-bcbd-ea804a7dca61)
![image](https://github.com/user-attachments/assets/81acca84-eb1f-477e-b499-500bff95ee82)

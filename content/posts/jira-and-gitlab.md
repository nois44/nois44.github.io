+++
title = 'Jira dan Gitlab'
date = 2024-02-29T16:17:05+07:00
author = 'Gabriel Edgar'
draft = false
+++
Artikel hari ini akan membahas mengenai penggunaan Gitlab dan Jira sebagai developer di sebuah tim. Sebelum memulai, diperlukan sedikit pengetahuan mengenai apa itu Gitlab dan Jira. Pengetahuan tersebut akan membantu dalam menggunakan kedua tools tersebut.

## Apa itu Gitlab?
GitLab adalah repositori Git berbasis web yang menawarkan wiki, kemampuan mengikuti masalah, dan repositori terbuka dan pribadi gratis. Ini adalah platform DevOps lengkap yang memungkinkan profesional melakukan semua pekerjaan yang berkaitan dengan proyek, mulai dari perencanaan proyek dan manajemen kode sumber hingga keamanan dan pemantauan. Ini juga memungkinkan tim bekerja sama dan membuat perangkat lunak yang lebih baik. Dengan bantuan GitLab, tim dapat meningkatkan produktivitas dan mengurangi siklus hidup produk, sehingga menghasilkan nilai bagi pelanggan. Tidak ada kebutuhan bagi pengguna untuk mengelola otorisasi untuk setiap alat dalam aplikasi ini. Setelah izin diberikan, setiap anggota organisasi memiliki akses ke setiap bagian.

## Keuntungan dalam menggunakan Gitlab
GitLab menawarkan beberapa keuntungan penting bagi developer. Berikut adalah beberapa keuntungan terpenting dari Gitlab:
- Sangat mudah untuk dipasang
- UI dan alat yang ramah pengguna
- Mengizinkan repositori pribadi gratis dalam jumlah tak terbatas
- Dapat mengintegrasikan banyak API dan layanan pihak ketiga
- Memiliki uptime yang sangat andal

## Pembuatan Proyek Gitlab
Sebelum memulai diharapkan telah memiliki akun Gitlab, jika anda belum memiliki akun Gitlab, maka anda bisa melakukan registrasi dengan memilih tombol "Register Now" pada halaman login. Nah, setelah memiliki akun Gitlab, sekarang kita dapat memulai membuat proyek Gitlab pertama anda.
#### Step 1 : Pilih menu atau tombol "Create New Project"
#### Step 2 : Pilih Create Black Project
#### Step 3 : Isi Data untuk Proyek yang ingin dibuat
#### Step 4 : Setelah proyek dibuat, disarankan untuk melakukan konfigurasi nama dan email dengan GitBash
```GitBash
$ Git config --global user.name "First"
$ Git config --global user.email gabrieledgarfn@gmail.com
```
#### Step 5 : Lalu, kalian dapat melakukan cloning repository melalui https yang didapatkan dengan menekan dropdown "Code" dan pilih Copy URL dibawah "Clone with HTTPS"
```Terminal
PS C:\User\gabri> git clone https://gitlab.com/GEdgar/first.git
Cloning into 'first'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.
PS C:\Users\gabri> 
```
#### Step 6 : Nah, sekarang kalian dapat mengerjakan proyek di repository yang telah kalian clone. Dengan masuk ke directory dari repository tadi.
```Terminal
PS C:\Users\gabri> cd first
PS C:\Users\gabri\first>
```
#### Step 7 : Setelah selesai membuat file dan anda perlu mengunggah file atau perubahan tersebut ke repositori
```Terminal
PS C:\Users\gabri\first> git add .
PS C:\Users\gabri\first> git commit -m "Pembuatan index.html"
PS C:\Users\gabri\first> git push origin main
```

## Apa itu Jira?
Untuk merencanakan, melacak, dan merilis proyek perangkat lunak, JIRA adalah alat developeran perangkat lunak yang populer untuk manajemen proyek dan pelacakan masalah. JIRA adalah alat terintegrasi dengan alat developeran perangkat lunak lainnya dan menyediakan platform terpusat untuk mengelola tugas, bug, dan jenis masalah lainnya serta membantu tim mengatur dan memprioritaskan pekerjaan mereka. Selain itu, JIRA memiliki berbagai fitur dan alur kerja yang dapat disesuaikan yang memungkinkan tim untuk menyesuaikannya dengan kebutuhan khusus mereka. Selain itu, JIRA memiliki banyak fitur pelaporan dan dasbor yang membantu tim terus melakukan pekerjaan mereka.


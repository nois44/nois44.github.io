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
#### Step 2 : Pilih Create Blank Project
![Step2](https://github.com/nois44/nois44.github.io/assets/94152526/4c835c3e-639d-4c36-af57-734484d2d991)
#### Step 3 : Isi Data untuk Proyek yang ingin dibuat
![Step3](https://github.com/nois44/nois44.github.io/assets/94152526/54201776-fdb5-4013-a4cd-9f854c6cac5d)
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
Untuk merencanakan, melacak, dan merilis proyek perangkat lunak, JIRA adalah alat developer perangkat lunak yang populer untuk manajemen proyek dan pelacakan masalah. JIRA adalah alat terintegrasi dengan alat developer perangkat lunak lainnya dan menyediakan platform terpusat untuk mengelola tugas, bug, dan jenis masalah lainnya serta membantu tim mengatur dan memprioritaskan pekerjaan mereka. Selain itu, JIRA memiliki berbagai fitur dan alur kerja yang dapat disesuaikan yang memungkinkan tim untuk menyesuaikannya dengan kebutuhan khusus mereka. Selain itu, JIRA memiliki banyak fitur pelaporan dan dasbor yang membantu tim terus melakukan pekerjaan mereka.

## Keuntungan dalam menggunakan Gitlab
- Dibangun untuk manajemen Agile dan Scrum
- Manajemen masalah yang sangat baik untuk pelacakan bug dan masalah
- Kemampuan tiket instan untuk menyederhanakan pemecahan masalah

## 7 Langkah untuk memulai di Jira
#### Step 1: Buat sebuah Proyek.
Masuk ke situs Perangkat Lunak Jira Anda. Di navigasi atas, pilih tarik-turun “Projectek” dan pilih “Create Project”.
#### Step 2: Pilih sebuah Template untuk Pengerjaan proyek tersebut.
Ada lusinan template di Jira Family, yang masing-masing dirancang untuk membantu tim memulai dengan cepat dan sukses. Saat ini, Jira Software menawarkan tiga template:
![image](https://github.com/nois44/nois44.github.io/assets/94152526/bf50751f-eb63-4112-9e6a-b0cc4cf0332e)
![image](https://github.com/nois44/nois44.github.io/assets/94152526/f3fc8bc1-9779-4c22-b999-93d604497671)
![image](https://github.com/nois44/nois44.github.io/assets/94152526/6a8ba199-36d6-4500-8f90-daf73ac1956b)

Pilih template yang sesuai dengan kebutuhan tim. Hanya untuk template scrum dan kanban, Anda juga akan diminta untuk memilih jenis proyek. Perbedaan mendasar antara kedua jenis proyek ini adalah cara pengelolaannya, dan apakah hal tersebut terjadi di tingkat tim atau di tingkat perusahaan/admin Jira. Proyek yang dikelola tim cocok untuk tim independen yang ingin mengontrol proses dan praktik kerja mereka sendiri dalam ruang mandiri. Proyek yang dikelola perusahaan disiapkan dan dikelola oleh admin Jira. Jenis proyek ini dirancang untuk tim yang ingin menstandardisasi cara kerja di banyak tim, seperti berbagi alur kerja.
#### Step 3: Set up kolom milikmu
Di Jira Software, boards menampilkan pilihan masalah dalam kolom, dengan setiap kolom mewakili langkah dalam alur kerja tim Anda untuk menyelesaikan pekerjaan. Meskipun ada banyak hal yang dapat Anda konfigurasikan di board Anda, kami sarankan untuk menyiapkan kolom saja untuk saat ini. Saat Anda memulai proyek Jira Software baru, penting untuk membuat dewan Anda mencerminkan cara kerja tim Anda. Cara Anda mengatur kolom di board Anda di templat scrum dan kanban bergantung pada apakah Anda berada dalam proyek yang dikelola tim atau proyek yang dikelola perusahaan. 
##### Dalam proyek yang dikelola tim:
- Pergi ke board Anda. Pilih (•••) di kanan atas dan klik Konfigurasikan board.
- Tambahkan kolom baru, ubah nama kolom, hapus kolom, atau pindahkan kolom seperlunya.
##### Dalam proyek yang dikelola perusahaan:
- Pergi ke board Anda. Pilih (•••) di kanan atas dan klik Pengaturan board.
- Klik tab Kolom.
- Tambahkan kolom baru, ubah nama kolom, hapus kolom, atau pindahkan kolom seperlunya.
![image](https://github.com/nois44/nois44.github.io/assets/94152526/417b6320-c380-4321-878d-46469baa8b8b)
#### Step 4: Buatlah sebuah Issue
Issue adalah landasan proyek Perangkat Lunak Jira Anda. Suatu masalah dapat mewakili sebuah cerita, epik, bug, fitur yang akan dibangun, atau tugas lainnya dalam proyek Anda. Pilih "Create" di navigasi. Masalah Anda akan muncul di backlog atau board proyek.
![image](https://github.com/nois44/nois44.github.io/assets/94152526/1be22b43-d223-4b24-882d-b19771cec780)
#### Step 5; Integrasikan Jira dengan software lain, sebagai proyek GitLab tadi yang telah dibuat.
- Pilih Roda Gigi di sudut kanan navigasi atas > Aplikasi.
- Klik "Find New App".
- Cari berdasarkan nama aplikasi, atau pilih kategori.
- Ikuti petunjuk untuk menginstal, beli sekarang, ataupun memulai uji coba gratis.
#### Step 6: Undang tim Anda
Setelah Anda memiliki cukup banyak pekerjaan yang terwakili di dewan Anda, mulailah mengundang anggota tim.
![image](https://github.com/nois44/nois44.github.io/assets/94152526/64bfeab3-ebe7-4ddc-ad9b-92433f4f79fe)
#### Step 7: Pindahkan pekerjaan ke depan (To Do, In Progress, Testing, Done)
Kini setelah tim Anda bergabung dengan situs Jira Software, Anda siap berkolaborasi dan melacak pekerjaan bersama. Jika Anda berada dalam proyek scrum, Anda harus membuat dan memulai sprint untuk mulai melacak pekerjaan. Jika Anda berada dalam proyek kanban, Anda dapat mulai melacak pekerjaan di board tulis. Untuk melacak item pekerjaan, pindahkan masalah dari satu kolom ke kolom lainnya seiring perkembangannya dalam alur kerja tim Anda.
![image](https://github.com/nois44/nois44.github.io/assets/94152526/5425afbe-6071-4d8e-b9c2-b4fd522456ef)

## Kesimpulan
Integrasi antara GitLab dan JIRA telah membawa manfaat signifikan bagi tim developer perangkat lunak. Keterpaduan kolaborasi antara kedua platform ini memungkinkan anggota tim untuk bekerja secara terpadu, mengkoordinasikan developer kode dengan manajemen proyek dan pelacakan isu. Dengan pelacakan progres yang lebih baik, pembaruan status dan kemajuan proyek dapat disinkronkan secara otomatis antara GitLab dan JIRA, memastikan anggota tim tetap terinformasi tanpa harus beralih antar platform. Manajemen isu yang efisien juga menjadi ciri penting dari integrasi ini, dengan kemampuan untuk membuat, memperbarui, dan menugaskan isu langsung dari GitLab ke JIRA, dan sebaliknya. Ini mengurangi kerumitan administratif dan memastikan isu-isu terkait dengan developer dapat diurutkan, dilacak, dan ditangani dengan cepat. Transparansi dan akuntabilitas ditingkatkan, karena setiap perubahan kode yang terkait dengan isu akan terlihat dalam riwayat isu di JIRA, menciptakan pemahaman yang lebih baik tentang konteks perubahan yang diusulkan dan memastikan kualitas kode yang lebih tinggi. Secara keseluruhan, integrasi antara GitLab dan JIRA memungkinkan tim developer untuk bekerja lebih efisien, terkoordinasi, dan fokus pada pengiriman nilai tambah bagi pelanggan mereka.

+++
title = 'Panduan GIT Tingkat Lanjut'
date = 2024-05-06T12:14:12+07:00
author = 'Gabriel Edgar'
draft = false
+++

Banyak pengembang tidak tahu mengenai beberapa command git, namun command-command tersebut sangatlah berguna dan dapat menyelesaikan banyak masalah. Anda dapat menghindari situasi sulit dengan mengikuti command-command ini. Saya akan membahas 3 dari sekian command git ini di media artikel terkait.  

## 1. Rebase
Pertama, ***rebasing*** adalah command Git yang kuat yang berfungsi sebagai alternatif _pull request_. Ini memungkinkan untuk menarik semua commit baru yang Anda buat setelah divergensi branch ke dalam branch baru dan menempatkan perubahan di ujung basis. Ini akan berguna jika Anda ingin memasukkan perubahan dari branch lain tanpa membuat commit gabungan karena alasan apa pun.
Ketika Anda sedang mengerjakan branch dari sebuah fitur dan ingin memasukkan perubahan dari branch utama tanpa membuat commit gabungan, rebasing biasanya digunakan. Ini membantu menjaga catatan proyek Anda tetap bersih, meskipun prosesnya mungkin lebih lama dan mungkin menemukan lebih banyak kesalahan selama penggabungan.

Sebagai alternatif dari _merge_, Anda dapat melakukan rebase branch fitur ke branch utama menggunakan command berikut:
```terminal
git checkout fitur
git rebase main
```
Ini memindahkan seluruh branch fitur ke ujung branch utama, secara efektif menggabungkan semua commit baru di main. Namun, rebasing menulis ulang riwayat proyek dengan membuat commit baru untuk setiap commit di branch asli, alih-alih menggunakan commit gabungan.


![image](https://github.com/nois44/nois44.github.io/assets/94152526/1aed4acb-fc83-4e06-be70-26024b5b9226)


Manfaat utama dari rebasing adalah Anda mendapatkan riwayat proyek yang jauh lebih bersih. Pertama, ini menghilangkan commit penggabungan yang tidak perlu yang diperlukan oleh git merge. Kedua, seperti yang Anda lihat pada diagram di atas, rebasing juga menghasilkan riwayat proyek yang linier sempurna—Anda dapat mengikuti ujung fitur hingga awal proyek tanpa perbranchan apa pun.


## 2. Amend
Setelah Anda melakukan banyak commit, akan ada kemungkinan bahwa Anda menyadari bahwa Anda lupa memasukkan sesuatu yang penting. Anda dapat dengan mudah mengubah commit untuk memasukkan perubahan yang hilang dengan Git.
Untuk melakukan hal ini, ikuti langkah-langkah berikut:

1. Pertama, buat perubahan pada file apa pun yang Anda perlukan untuk proyek tersebut.
2. Lakukan staging seperti biasa menggunakan **git add**.
3. Lakukan commit ulang perubahan tersebut di staging area menggunakan command berbeda untuk melakukan commit:
   ```terminal
   git commit --amend -m "Pesan yang diedit dengan command amend"
   ```


## 3. Cherry-Pick
git cherry-pick adalah command kuat yang memungkinkan commit Git sewenang-wenang diambil dengan referensi dan ditambahkan ke HEAD yang berfungsi saat ini. 
_Cherry-Picking_ adalah tindakan mengambil commit dari branch dan menerapkannya ke branch lain. git cherry-pick dapat berguna untuk membatalkan perubahan. 
Misalnya, commit secara tidak sengaja dibuat ke branch yang salah. Anda dapat beralih ke branch yang benar dan memilih commit di tempat yang seharusnya.

### Kapan dapat menggunakan git cherry-pick
1. Di saat anda memerlukan Kolaborasi antar developer di sebuah tim
2. Ketika bug ditemukan, penting untuk memberikan perbaikan kepada pengguna akhir secepat mungkin
3. Terkadang branch fitur menjadi basi atau rusak dan tidak digabungkan ke dalam branch utama. Terkadang _pull request_ mungkin ditutup tanpa penggabungan. Git tidak pernah kehilangan commit tersebut dan melalui perintah seperti **git log** dan **git reflog** commit tersebut dapat ditemukan dan dihidupkan kembali.

### Berikut Demonstrasi penggunaan git cherry-pick
Untuk mendemonstrasikan cara menggunakan git cherry-pick mari kita asumsikan kita memiliki repositori dengan status branch berikut:

```text
    a - b - c - d   Main
         \
           e - f - g Feature
```

git cherry-pick usage is straight forward and can be executed like:

```text
    git cherry-pick commitSha
```

di contoh, commitSha ini adalah referensi commit. Anda dapat menemukan referensi commit dengan menggunakan git log. Dalam contoh ini kita telah membuat katakanlah kita ingin menggunakan commit `f` di main. Pertama kita pastikan bahwa kita sedang mengerjakan branch utama.

```text
    git checkout main
```

Kemudian kita jalankan cherry-pick dengan perintah berikut:

```text
    git cherry-pick f
```

Setelah command tersebut dijalankan, maka Git history akan terlihat seperti berikut:

```text
    a - b - c - d - f   Main
         \
           e - f - g Feature
```

commit f telah berhasil di-_picked_ ke branch utama


## Kesimpulan
dengan memahami dan menggunakan command-command ini, pengembang dapat mengelola riwayat proyek dengan lebih efisien dan menjaga kebersihan serta keteraturan commit. Selain itu, penguasaan command-command ini dapat meningkatkan kolaborasi antar pengembang dan mempermudah perbaikan bug secara cepat. Dengan riwayat yang bersih, debugging menjadi lebih mudah dan proyek lebih mudah dipelihara. Pemahaman mendalam mengenai Git juga akan membuat developer lebih baik dalam mengelola kode yang dibuatnya.

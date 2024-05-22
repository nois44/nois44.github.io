+++
title = 'Platform Monitoring'
date = 2024-05-14T12:14:12+07:00
author = 'Gabriel Edgar'
draft = false
+++

Baik kita sedang membangun web app, mobile app, atau jenis software lainnya, tidak dapat dipungkiri bahwa kita akan menghadapi situasi di mana terjadi kesalahan. 
Pada saat inilah Sentry berperan, manajemen kesalahan yang kuat dan alat pemantauan di real-time. 
Pada artikel ini, kami akan menjelaskan cara kerjanya dan manfaatnya. Sebelum itu, mari mengenal apa itu Error Monitoring.

## Apa itu Error Monitoring?
Seperti namanya, Pemantauan kesalahan adalah proses memantau dan mengidentifikasi segala jenis informasi mengenai aplikasi perangkat lunak kami, seperti kesalahan, kerusakan, pengecualian, atau perilaku tak terduga apa pun yang terjadi dalam perangkat lunak saat sedang beroperasi. Meskipun aplikasi perangkat lunak tidak diharuskan untuk mengintegrasikannya ke sistemnya, sebenarnya ada satu hal yang tidak boleh diabaikan oleh pengembang, yaitu melacak anomali dalam perangkat lunak untuk mencegah pengalaman pengguna yang buruk.

Sebenarnya ada lebih banyak manfaat dari "**Error Monitoring**" daripada yang kita duga. 
Salah satu bagian terpentingnya adalah sebagian besar Sistem Application Performance Management (APM) yang umumnya menangani pemantauan kesalahan. 
Sistem ini menyediakan data mengenai kinerja perangkat lunak secara berkala yang berarti developer dapat mengantisipasi kesalahan apa pun yang akan terjadi di masa mendatang melalui identifikasi pola apa pun yang dapat menyebabkannya. untuk crash atau kesalahan yang tidak diinginkan di masa depan, atau mungkin sistem itu sendiri bahkan dapat memprediksinya sendiri.

Jadi apa itu Application Performance Management (APM)? Ya, tidak ada yang rumit. Ini adalah sistem yang melakukan semua pemantauan kinerja sistem perangkat lunak kami secara real-time, termasuk semua sistem yang kompleks. Artinya, ia juga harus melakukan pemantauan kesalahan.
Karena proyek yang saya gunakan saat ini berada dalam Framework Django, maka saya akan menggunakan Sentry untuk artikel kali ini.

![image](https://github.com/nois44/nois44.github.io/assets/94152526/3c63fe0f-ca1e-445a-9ad2-a6e8ba1f4b96)

## Sentry
Sentry adalah sistem pemantauan kesalahan perangkat lunak yang melakukan manajemen kinerja aplikasi perangkat lunak kami, dan memiliki sistem integrasi Django sendiri melalui penggunaan paket python yang dapat kami impor ke program kami.
Di halaman web, disediakan bagaimana Anda dapat melakukannya:

#### 1. Install python SDK melalui terminal menggunakan pip
```terminal
pip install --upgrade sentry-sdk
```

#### 2. Inisialisasi paket python SDK ke sistem Django di dalam file settings.py
```python
import sentry_sdk
from sentry_sdk.integrations.django import DjangoIntegration

sentry_sdk.init(
    dsn="https://<key>@sentry.io/<project>",
    integrations=[DjangoIntegration()],

    # Set traces_sample_rate to 1.0 to capture 100%
    # of transactions for performance monitoring.
    # We recommend adjusting this value in production,
    traces_sample_rate=1.0,

    # If you wish to associate users to errors (assuming you are using
    # django.contrib.auth) you may enable sending PII data.
    send_default_pii=True
)
```

Nah itulah cara mengintegrasikan Sentry ke sistem aplikasi software kita, untuk informasi lebih lanjut bisa merujuk pada dokumentasi resmi Sentry di link ini: https://docs.sentry.io/platforms/python/integrations/django/

Jadi, setelah Sentry bekerja di sistem kami, apa yang terjadi sekarang? Berikut adalah hal-hal yang Sentry dapat lakukan untuk kami di sistem kami yang sudah beroperasi:

1. Software Performance Monitoring

![image](https://github.com/nois44/nois44.github.io/assets/94152526/ee0deaf3-1f4d-4e90-96e2-6abaab441299)

Seperti gambar di atas, developer kini dapat melacak kinerja software melalui dashboard Sentry yang terintegrasi dengan sistem yang telah dilakukan sebelumnya. Jadi seseorang dapat menggunakan beberapa optimasi jika sesuatu harus dilakukan untuk meningkatkan pengalaman pengguna.

Pada gambar tersebut terlihat bahwa seorang user melakukan atau mencoba untuk login pada web app tersebut. Saat user mencoba untuk login, hal tersebut men-_trigger_ **/api/0/projects/ep/login_page**. 
Rinciannya menunjukkan bahwa bagian paling lambat dari proses login terkait dengan **platform.middlewareviews.messages**. Hal ini dapat disebabkan oleh beberapa alasan, seperti:
- Inefisiensi dalam kode yang menangani pesan.
- Layanan pesan kelebihan beban pada saat upaya login.
- Latensi jaringan antara browser pengguna dan server.

2. Error Tracking

![image](https://github.com/nois44/nois44.github.io/assets/94152526/226998c7-0073-4a1d-ac8b-08b0cf33f44a)

Sudah pasti bahwa penjaga (Sentry) harus memiliki sistem pelacakan kesalahannya, seperti yang ditunjukkan pada gambar di atas. segala jenis kesalahan dan pengecualian yang terjadi akan dilacak dan dicatat di bagian ini untuk ditangani oleh pengembang agar tidak terjadi lagi.
Berikut rincian informasi pada gambar:
- Saat ini ada sembilan masalah yang belum terselesaikan.
- Terlihat ada masalah terkait dengan kesalahan di Axios, sebuah library JavaScript populer yang biasa digunakan untuk membuat request HTTP dari browser. Pesan kesalahan spesifiknya adalah **XMLHttpRequest.handleError** yang menunjukkan masalah pada cara browser menangani permintaan HTTP.
- Kesalahan selanjuutnya adalah TypeError, yang merupakan istilah umum untuk kesalahan yang terjadi ketika variabel atau ekspresi digunakan dengan cara yang tidak diperbolehkan oleh JavaScript. Dalam kasus ini, ada inisialisasi variabel yang tidak terjadi atau objek yang diharapkan tidak ada sehingga tidak terdefinisi.
- Lalu ada kesalahan terhadap variable karena tidak atau belum didefinisikan, yang mnyebabkan pemanggilan error _Reference Error_

3. Profiling

![image](https://github.com/nois44/nois44.github.io/assets/94152526/4b3ed11b-2d91-4488-94b1-ee6eff177043)

Fitur profiling Sentry dibangun berdasarkan kemampuan Pemantauan Kinerja kami yang telah ada untuk memberikan visibilitas tingkat kode yang tepat ke dalam eksekusi aplikasi di lingkungan produksi. 
Profiling memberikan konteks pada tingkat yang lebih dalam dibandingkan penelusuran tradisional, memungkinkan Anda memvisualisasikan detail stack panggilan secara tepat tanpa memerlukan alat khusus.

Profiling tersebut berfokus pada fungsi yang paling lambat dan fungsi yang paling mengalami kemunduran dalam proyek yang tidak ditentukan.
Fungsi paling lambat:
- Fungsi paling lambat berdasarkan total waktu yang dihabiskan adalah product_info, yang memakan waktu 869,34 milidetik (ms).
- Ini diikuti oleh get_products pada 318,58 md dan get_iterator pada 342,91 md.

Fungsi yang paling mengalami kemunduran
- Fungsi yang paling mengalami kemunduran adalah Specialized EmpowerPlantViewController.perf yang mengalami peningkatan waktu eksekusi dari 1,06 detik menjadi lebih dari 2 detik.

Hal-hal yang memungkinkan:
- Fungsi _product_info_ kemungkinan besar merupakan hambatan dalam kinerja aplikasi, sehingga menghabiskan sebagian besar waktu untuk dijalankan. Mengoptimalkan fungsi ini dapat meningkatkan kecepatan aplikasi secara keseluruhan secara signifikan.
- Regresi di _Specialized EmpowerPlantViewController.perf_ menunjukkan bahwa perubahan kode terkini telah memperlambat fungsi ini. Mengidentifikasi perubahan kode dan mengevaluasi dampaknya dapat membantu meningkatkan kinerja.

## Kesimpulan
Error Monitoring adalah proses memantau dan mengidentifikasi kesalahan, kerusakan, pengecualian, atau perilaku tak terduga dalam perangkat lunak. Sentry, sebagai sistem pemantauan kesalahan, menyediakan manajemen kinerja aplikasi dan integrasi dengan framework Django melalui paket Python. Dengan menggunakan Sentry, pengembang dapat melacak kinerja perangkat lunak, mendeteksi dan mencatat kesalahan, serta melakukan profiling untuk visibilitas eksekusi aplikasi yang lebih mendalam.

### Referensi
1. https://docs.sentry.io/platforms/python/performance/#configure
2. https://www.mytaskpanel.com/when-to-use-sentry/#:~:text=Sentry%20provides%20instant%20visibility%20of,error%20occurs%20in%20the%20application.

+++
title = 'Panduan GIT Tingkat Lanjut'
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
Seperti gambar di atas, developr kini dapat melacak kinerja software melalui dashboard Sentry yang terintegrasi dengan sistem yang telah dilakukan sebelumnya. Jadi seseorang dapat menggunakan beberapa optimasi jika sesuatu harus dilakukan untuk meningkatkan pengalaman pengguna.

2. Error Tracking

![image](https://github.com/nois44/nois44.github.io/assets/94152526/226998c7-0073-4a1d-ac8b-08b0cf33f44a)
Sudah pasti bahwa penjaga (Sentry) harus memiliki sistem pelacakan kesalahannya, seperti yang ditunjukkan pada gambar di atas. segala jenis kesalahan dan pengecualian yang terjadi akan dilacak dan dicatat di bagian ini untuk ditangani oleh pengembang agar tidak terjadi lagi.

3. Profiling

![image](https://github.com/nois44/nois44.github.io/assets/94152526/4b3ed11b-2d91-4488-94b1-ee6eff177043)
Fitur profiling Sentry dibangun berdasarkan kemampuan Pemantauan Kinerja kami yang telah ada untuk memberikan visibilitas tingkat kode yang tepat ke dalam eksekusi aplikasi di lingkungan produksi. 
Profiling memberikan konteks pada tingkat yang lebih dalam dibandingkan penelusuran tradisional, memungkinkan Anda memvisualisasikan detail stack panggilan secara tepat tanpa memerlukan alat khusus.

## Kesimpulan
Error Monitoring adalah proses memantau dan mengidentifikasi kesalahan, kerusakan, pengecualian, atau perilaku tak terduga dalam perangkat lunak. Sentry, sebagai sistem pemantauan kesalahan, menyediakan manajemen kinerja aplikasi dan integrasi dengan framework Django melalui paket Python. Dengan menggunakan Sentry, pengembang dapat melacak kinerja perangkat lunak, mendeteksi dan mencatat kesalahan, serta melakukan profiling untuk visibilitas eksekusi aplikasi yang lebih mendalam.

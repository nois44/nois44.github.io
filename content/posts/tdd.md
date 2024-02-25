+++
title = 'Test-Driven Development'
date = 2024-02-26T04:21:30+07:00
author = 'Gabriel Edgar'
draft = false
+++
Di artikel ini akan membahas mengenai Test-Driven Development atau TDD. Sebelum masuk pada implementasi TDD, diperlukan pengetahuan mengenai apa itu TDD, keuntungan dari TDD, siklus pengerjaan, dan lain-lain.

## Apa itu Test-Driven Development?
TDD adalah sebuah metode pengembangan perangkat lunak yang menekankan pengujian atau  sebelum menulis kode sebenarnya. TDD Ini memiliki siklus tertentu dalam menulis tes, menjalankannya, dan kemudian menulis kode agar tes tersebut berhasil. TDD melakukan pendekatan disiplin terhadap pengembangan perangkat lunak dan dapat menghasilkan kode yang lebih dapat diandalkan, mudah dipelihara (maintainable), dan terancang dengan baik.

## Keuntungan TDD
- Peningkatan Kualitas Kode
- Debugging dan Pemeliharaan Lebih Mudah
- Perkembangan Lebih Cepat
- Kolaborasi dan Komunikasi yang Lebih Baik
- Refactoring dan Evolusi Kode yang Lebih Mudah

## Siklus Pengerjaan menggunakan TDD
Siklus TDD biasanya terdiri dari langkah-langkah berikut:
1. Menulis tes: Mulailah dengan menulis tes yang mendefinisikan perilaku yang diharapkan dari fungsionalitas tertentu. Tes ini sering kali ditulis sebagai fungsi atau metode yang menegaskan kondisi atau hasil tertentu.
2. Jalankan pengujian: Jalankan pengujian untuk memverifikasi bahwa pengujian gagal. Ini merupakan langkah penting karena memastikan bahwa pengujian tersebut valid dan perilaku yang diharapkan belum diterapkan.
3. Tulis kodenya: Terapkan kode dalam jumlah minimal yang diperlukan agar tes lulus. Fokus pada pemecahan masalah spesifik yang diatasi oleh pengujian, daripada menambahkan fungsionalitas yang tidak perlu.
4. Jalankan pengujian lagi: Jalankan pengujian lagi untuk memeriksa apakah perubahan kode telah berhasil membuat pengujian berhasil. Jika pengujian gagal, ulangi dan ubah kode hingga pengujian berhasil.
5. Memfaktorkan ulang kode: Setelah pengujian berhasil, Anda dapat memfaktorkan ulang kode untuk meningkatkan desain, struktur, atau kinerjanya sekaligus menjaga agar pengujian tetap berjalan. Pemfaktoran ulang memastikan kode tetap bersih dan dapat dipelihara.
6. Ulangi siklusnya: Pindah ke fitur atau fungsi berikutnya dan ulangi prosesnya. Tulis tes baru, jalankan (yang seharusnya gagal pada awalnya), tulis kode agar berhasil, dan lanjutkan siklusnya.

## Contoh implementasi TDD
#### Step 1: Dimulai dari pembuatan tes. Contoh yang digunakan adalah untuk mencoba mengintegrasikan backend dengan html. Hal ini terjadi pada file test.py
```python
from django.test import TestCase

class NewPageTest(TestCase):
    def test_new_page(self):
        response = self.client.get('/<URL yang akan dituju>/')

        self.assertTemplateUsed(response, '<Nama HTML yang digunakan>.html')
        self.assertEqual(response.status_code, 200)
```
#### Step2: Jalankan tesnya pada terminal.
```python
#Karena python yang digunakan lebih spesifik ke Django, maka di terminal hanya perlu menjalankan command berikut:
$ python manage.py test

#Jika berhasil maka tidak akan ada indikasi error, namun jika ada error indikasi/warning akan terlihat melalui terminal
```
#### Step 3: Buat kode yang dapat menyelesaikan permasalahan tersebut. Bisa dimulai pada file views.py
```python
#views.py
def render_new_page(request):
    return render(request, '<Nama HTML yang digunakan>.html')

#urls.py
from django.urls import path
from .views import *

urlpatterns = [
    path('', views.render_new_page, name='render_new_page'),
]

```
#### Step 4: Jalankan pengujian atau tesnya lagi. sama seperti langkah kedua.
#### Step 5: Melakukan refactor, namun pada kesempatan kali ini tidak diperlukan karena pengujian ataupun algoritma/logic dari kode tersebut tidaklah rumit.
#### Step 6: Ulangi lagi dari step 1 jika telah berhasil dan perlu melanjutkan ke tugas selanjutnya. Jika masih ada kegagalan maka ulangi mulai dari langkah ke 3.

## Kesimpulan
Metodologi pengujian pertama TDD menghadirkan keandalan kode, deteksi bug yang efisien, dan pengurangan biaya pemeliharaan jangka panjang. Pengujian terstruktur dengan serangkaian kasus uji ekspresif yang komprehensif mengoptimalkan proses pengembangan perangkat lunak dan meningkatkan kualitas kode.

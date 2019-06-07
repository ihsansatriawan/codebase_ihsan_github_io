---
title: "Perbedaan Defer dan Async dalam load Javascript"
date: 2019-06-08T06:21:32+07:00
draft: false
---

![](https://cdn-images-1.medium.com/max/2600/0*Z7_9TMRi48crzzfM)
<span class="figcaption_hack">Photo by [Markus
Spiske](https://unsplash.com/@markusspiske?utm_source=medium&utm_medium=referral)
on [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral)</span>

Berawal dari pengalaman melakukan proses interview untuk menyeleksi calon
karyawan di kantor untuk *frontend engineer *(FE)*. *Dari beberapa pertanyaan
yang saya tanyakan, ada satu pertanyaan yang harus nya cukup umum untuk para FE
namun ternyata masih ada yang kurang bisa menjawab dengan baik. Pertanyaan nya
adalah

    Apa perbedaan 
     dan 
     di dalam tag 
     ?

Cukup sederhana bukan ? :D

### Async dan Defer

Kita membicarakan ini dalam kondisi ketika kita perlu *load *suatu script di
halaman HTML. Jika kita asal pasang maka akan sangat mempengaruhi performa dari
website kita. Cara biasa untuk *load *suatu script bisa dengan:

![](https://cdn-images-1.medium.com/max/2400/1*q0cat_DEfrDLJ2RB3Z6C1Q.png)
<span class="figcaption_hack">Load External Script</span>

Ketika HTML menemukan baris ini, maka browser akan mengunduh`external.js` dan
meng-eksekusi script tersebut. Hal ini mengakibatkan halaman kita akan terdelay
saat meload `external.js`. Terdapat solusi untuk menangani masalah tersebut,
yakni menggunakan `async` atau `defer`. Cara menggunakan nya seperti gambar
dibawah:

![](https://cdn-images-1.medium.com/max/2400/1*U7E_rXvcR3xJvlfK0GdJmg.png)
<span class="figcaption_hack">Cara penggunaan async dan defer</span>

Namun tidak semua versi browser dapat mensupport tag ini, versi browser mana
saja yang support dapat dilihat di

> [https://caniuse.com/#feat=script-async](https://caniuse.com/#feat=script-async)<br>
> [https://caniuse.com/#feat=script-defer](https://caniuse.com/#feat=script-defer)

2 hal ini dapat menjadi solusi dalam meload external script dikarenakan proses
nya yang tidak memblock proses `parse HTML`. Namun kedua hal tersebut memiliki
perbedaan, berikut ini akan dijelaskan lebih detail

### **Tanpa Defer atau Async**

Berikut ini diberikan gambar proses meload sebuah page tanpa menggunakan defer
atau async

![](https://cdn-images-1.medium.com/max/2400/1*ngaqDXorCwwqq9H_1KjjyQ.png)

![](https://cdn-images-1.medium.com/max/2400/1*R2VMs79nWWhrxpl1eA3n3A.png)

### Dengan Async dan Defer di `<Head>`

Berikut ini diberikan gambar proses meload sebuah page menggunakan defer async

![](https://cdn-images-1.medium.com/max/2400/1*xeGCmltgI-pEW3SP1OOOFg.png)

Terlihat dari gambar bahwa proses mendownload script external nya tidak memblock
proses parse HTML, lalu beda nya apa dengan `defer` ? Berikut ini gambaran
proses ketika menggunakan `defer`.

![](https://cdn-images-1.medium.com/max/2400/1*4bdjTh739EIdNy6xlmu--Q.png)

Terlihat menggunakan `defer` ini merupakan opsi yang paling baik, karena proses
download script dan execute nya dilakukan setelah browser selesai melakukan
parse HTML nya, sehingga tidak memblock proses render halaman tersebut.

* [JavaScript](https://medium.com/tag/javascript?source=post)
* [Asynchronous](https://medium.com/tag/asynchronous?source=post)
* [Performance](https://medium.com/tag/performance?source=post)



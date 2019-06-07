---
title: "Cara Mudah Deploy Create-React-App"
date: 2019-06-08T06:11:54+07:00
draft: false
---

![](https://cdn-images-1.medium.com/max/1600/1*N_6DIrFp3b3qv3WTDohqxg.png)

Halo semuanya, kali ini kita akan belajar mengenai bagaimana men-deploy React
app yang telah kita buat ke server sehingga teman-teman kita dapat mengakses
melalui browser masing-masing. Sebenarnya banyak cara dan layanan yang dapat
kita gunakan, namun pada artikel kali ini akan menggunakan:

1.  [Create React App](https://github.com/facebookincubator/create-react-app) (CRA)
1.  [Surge.sh](https://surge.sh/)
1.  [Heroku](http://heroku.com/)

*****

### Create React App (CRA)

Keluhan yang pernah saya dengar ketika orang lain mencoba react adalah begitu
banyak hal yang perlu di setup, mulai dari `babel` `webpack` dll. Facebook
akhirnya mengeluarkan semacam boilerplate untuk react dengan slogan `no build
configuration`. untuk menggunaan menggunakan CRA cara nya sangat lah mudah,
kalian hanya perlu mengetikkan perintah berikut di dalam command line kalian




![](https://cdn-images-1.medium.com/max/1600/1*aAfJYUI0o_annhYWVHAzpQ.png)
<span class="figcaption_hack">Jika sukses membuat React App menggunakan CRA</span>

Dengan menggunakan CRA ini kita tinggal fokus dalam membangun feature dari app
yang ingin kita buat. Kita bisa menggunakan `yarn start`saat melakukan
development di local dan menggunakan `yarn build`untuk melakukan deployment. CRA
pun dapat kita custom configuration-nya sesuai keinginan kita, dengan cara
melalukan `yarn eject`, perlu diperhatikan sekali kita menggunakannya perintah
ini, kita tidak dapat mengembalikannya (pada artikel selanjutnya akan saya
jelaskan lebih detail mengenai config react app menggunakan `yarn eject` )

![](https://cdn-images-1.medium.com/max/1600/1*iWFXWflE-eS6bC3C9VortQ.png)
<span class="figcaption_hack">Tampilan Default dari CRA</span>

*****

### Surge.sh

Jika sebelumnya kita telah berhasil membuat React app menggunakan CRA, kali ini
kita akan mencoba melakukan deployment menggunakan surge.sh. Surge.sh merupakan

> Static web publishing for Front-End Developers

Langkah pertama kita perlu meng-install package surge.sh secara global


langkah selanjutnya, kita perlu melakukan persiapan dari React app yang telah
kita, yakni dengan `yarn build` . Dengan perintah tersebut, kita membuat React
app kita dalam bentuk static sehingga dapat diserve oleh server surge

![](https://cdn-images-1.medium.com/max/1600/1*yXVSjmXwkwG6zD5USbi-pA.png)
<span class="figcaption_hack">Sukses deploy menggunakan surge.sh</span>

Yang perlu diperhatikan adalah, ketika diminta memasukkan path dari project kita
adalah, kita perlu mengarahkan kepada folder `build` dari React app yang kita
buat.

*****

### Heroku

Heroku merupakan salah satu perusahaan penyedia layanan *Platform as a Service
(PaaS). *Untuk dapat menggunakan layanan heroku, kita perlu melakukan:

* [Sign Up](https://signup.heroku.com/)
* Install [command-lint tools
(CLI)](https://devcenter.heroku.com/articles/heroku-cli) Heroku

![](https://cdn-images-1.medium.com/max/1600/1*BhGIGjEx1aQFuYFP1n1UoQ.png)
<span class="figcaption_hack">Tampilan ketika kita sukses install Heroku CLI</span>

Selanjutnya kita dapat menggunakan React app yang telah kita buat sebelumnya
untuk dideploy ke Heroku dengan cara sebagai berikut:

    git init

    # Membuat Heroku app, membutuhkan akun gratis di Heroku.com
    heroku create -b 

    # Mengarahkan root dari directory kita ke folder build
    echo '{ "root": "build/" }' > static.json

    # Menghapus folder build dari .gitignore
    sed '/build/d' .gitignore > .gitignore.new && mv .gitignore.new .gitignore

    # Build, commit, deploy!
    yarn build
    git add .
    git commit -m "Deploy to Heroku!"
    git push heroku master

![](https://cdn-images-1.medium.com/max/1600/1*f9BECNOhME8Q9onfXtGreg.png)
<span class="figcaption_hack">Gagal deploy</span>

Jika ada yang mengalami gagal seperti yang diatas, kita perlu masuk ke dalam
halaman Dashboard akun Heroku. Masuk kedalam nama apps yang kita buat dan ada di
tab Deploy

![](https://cdn-images-1.medium.com/max/1600/1*lRfLgYdF6y8r6WNMI7PQJA.png)
<span class="figcaption_hack">Dashboard Heroku tab Deploy</span>

![](https://cdn-images-1.medium.com/max/1600/1*_DLlO9XxHnUmDyxtHr-Qew.png)
<span class="figcaption_hack">Sukses Deploy ke Heroku!</span>

* [React](https://medium.com/tag/react?source=post)
* [Heroku](https://medium.com/tag/heroku?source=post)
* [Surge](https://medium.com/tag/surge?source=post)
* [Deploy](https://medium.com/tag/deploy?source=post)
* [JavaScript](https://medium.com/tag/javascript?source=post)



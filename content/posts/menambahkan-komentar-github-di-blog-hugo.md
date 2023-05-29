---
title: 'Cara Menambahkan Komentar GitHub di Hugo'
date: 2023-05-29
draft: false
author: ["Rico Ardiansyah"]
categories:
- Tutorial
- Hugo
tags:
- Hugo
- GitHub Comments
cover:
    image: "/img/github-comments.png"
---
Halo semuanya, semoga sehat selalu ya pada kesempatan kali ini saya akan buat tutorial cara menambahkan GitHub Comments pake [utterances](https://utteranc.es/) ke Hugo, utterances sangat cocok dipakai di blog yang pakai cms Hugo karena gratis, sangat ringan, responsive, dan juga open source
## Cara instalasi
1. Kamu harus punya repo GitHub Public, Jika Kamu sudah menggunakan Github untuk meng-host situs web kamu seperti saya, maka cukup untuk menggunakan yang itu.
2. Login ke github, kemudian klik https://github.com/apps/utterances dan install aplikasi utterances tersebut
![Install utterances](/img/IMG_6309.png)
3. Kemudian pilih repositori yang ingin kamu tambahkan komentar dan klik install
![Pilih repo](/img/IMG_6310.png)
4. Buka web [utterances](https://utteranc.es/) dan isi:
    - Isi repo yang dipilih tanpa url ``https://github.com/`` sebagai contoh saya disini akan pakai repo 0xricoard/hugo-blog
      ![repo](/img/repo.png)
    - Mapping: saya memilih mapping dengan Issue title contains page title yang artinya Utterances akan mencari isu yang judulnya mengandung judul postingan blog. Jika isu yang cocok tidak ditemukan, Utterances akan secara otomatis membuat isu baru saat pertama kali seseorang mengomentari postingan Anda. atau kamu bisa pilih yang lainnya.
![mapping](/img/mapping.png)
    - Issue Label: Saya tidak memberi label untuk isu komentarnya, kamu bisa memberi nama label dengan sesuka hati
    - Theme: Saya memilih tema Preffered Color Scheme dikarenaka template Hugo saya dapat mendeteksi otomatis mode gelap atau mode terang pada perangkat, Kamu bisa pilih tema yang lainnya
    ![Tema](/img/theme.png)
5. Copy hasil kode JavaScript yang telah dibuat
   ![Kode](/img/kodescript.png)
6. Tempel kode ke Hugo, Sebagian besar tema blog Hugo memiliki file ``comments.html`` di dalamnya (di bagian ``layout/partial`` misalnya). Tergantung pada pengaturan tema yang kamu pakai
   ![comments.html](/img/commentshtml.png)
7. Dan ini khusus untuk tema PaperMod yang saya gunakan, saya perlu mengubah parameter "comments" menjadi "true" di config.yml. Sekali lagi, Baca dokumentasi tema yang kamu gunakan!
    ![set ke true](/img/commentstrue.png)
 
Dan setelah semua konfigurasi diatas, kamu dapat melihat kolom komentar GitHub di bawah postingan. Ini akan mengharuskan pembaca kamu untuk masuk ke akun Github mereka sebelum berkomentar.
![tampilan komen](/img/github-comments.png)
Setelah komentar ditambahkan, Kamu akan melihat Issue terkait ditambahkan di repo GitHub.
![issues](/img/issues.png)

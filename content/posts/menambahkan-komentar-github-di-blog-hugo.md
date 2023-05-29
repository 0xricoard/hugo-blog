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
- Comments
cover:
    image: "/img/github-comments.png"
---
Oke kali ini saya akan buat tutorial cara menambahkan GitHub Comments pake [utterances](https://utteranc.es/) ke Hugo, utterances sangat cocok dipakai di blog yang pakai cms Hugo karena gratis, sangat ringan, responsive, dan juga open source
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
5. 

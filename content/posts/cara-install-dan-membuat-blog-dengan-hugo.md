---
title: 'Cara Install dan Membuat Blog dengan Hugo'
date: 2023-04-30
draft: false
author: ["Rico Ardiansyah"]
categories:
- Hugo
- Blogging
cover:
    image: "https://upload.wikimedia.org/wikipedia/commons/thumb/a/af/Logo_of_Hugo_the_static_website_generator.svg/640px-Logo_of_Hugo_the_static_website_generator.svg.png"
---
![Hugo Logo](https://upload.wikimedia.org/wikipedia/commons/thumb/a/af/Logo_of_Hugo_the_static_website_generator.svg/640px-Logo_of_Hugo_the_static_website_generator.svg.png)
## Instalasi Hugo di Ubuntu
Berikut adalah cara untuk menginstal Hugo di Ubuntu:

1. Buka terminal di Ubuntu Anda.
2. Pastikan sistem Anda telah terupdate dengan menjalankan perintah `sudo apt-get update`.
3. Install dependensi yang diperlukan dengan perintah `sudo apt-get install -y golang-go git`.
4. Buat direktori baru untuk menginstal Hugo dengan menjalankan perintah `mkdir ~/hugo`.
5. Pindah ke direktori yang baru dibuat dengan menjalankan perintah `cd ~/hugo`.
6. Unduh file biner Hugo dari situs web Hugo dengan perintah `wget https://github.com/gohugoio/hugo/releases/download/v0.84.3/hugo_extended_0.84.3_Linux-64bit.deb`.
7. Instal Hugo dengan menjalankan perintah `sudo dpkg -i hugo_extended_0.84.3_Linux-64bit.deb`.
8. Periksa apakah Hugo telah terinstal dengan menjalankan perintah `hugo version`.

## Membuat Blog dengan Hugo di Ubuntu
Setelah Hugo telah terinstal di Ubuntu, berikut adalah cara untuk membuat blog dengan Hugo:

1. Buka terminal dan buat direktori baru untuk situs Hugo dengan menjalankan perintah `mkdir namasitus`. Ganti "namasitus" dengan nama situs yang diinginkan.
2. Masuk ke direktori situs dengan menjalankan perintah `cd namasitus`.
3. Buat situs Hugo baru dengan menjalankan perintah `hugo new site .`.
4. Pilih tema untuk situs Anda dengan mengunjungi situs web HugoThemes. Unduh tema yang Anda inginkan dan ekstrak ke folder `themes` di direktori situs Anda.
5. Tambahkan tema yang dipilih ke situs Anda dengan menjalankan perintah `echo 'theme = "namatema"' >> config.toml`. Ganti "namatema" dengan nama tema yang Anda pilih.
6. Buat konten untuk situs Anda dengan membuat direktori `content` di direktori situs Anda dan tambahkan file markdown untuk setiap artikel atau halaman yang Anda inginkan.
7. Tambahkan menu navigasi ke situs Anda dengan mengedit file `config.toml`. Anda bisa menambahkan tautan ke halaman atau artikel yang telah Anda buat sebelumnya.
8. Jalankan situs Anda dengan menggunakan perintah `hugo server -D`. Halaman situs Anda akan di-generate dan tersedia di `http://localhost:1313/`.
9. Setelah situs Anda siap untuk dipublikasikan, Anda dapat melakukan generate situs dengan perintah `hugo`. Halaman situs Anda akan di-generate ke folder `public`. Anda dapat memindahkan isi folder `public` ke server web Anda untuk mempublikasikan situs Anda.

## Kesimpulan
Itulah panduan instalasi dan pembuatan blog dengan Hugo di Ubuntu menggunakan format markdown. Dengan mengikuti langkah-langkah ini, Anda akan dapat membuat situs web statis menggunakan Hugo dengan mudah dan cepat. Selamat mencoba!

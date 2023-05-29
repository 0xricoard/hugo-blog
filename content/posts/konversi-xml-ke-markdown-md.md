---
title: 'Cara Ubah File XML Ke Format Markdown(MD)'
date: 2023-05-29
draft: false
author: ["Rico Ardiansyah"]
categories:
- Tutorial
- Hugo
tags:
- Hugo
cover:
    image: "/img/xmltomd.png"
---
XML (Extensible Markup Language) dan MD (Markdown) adalah dua format file yang berbeda. XML biasanya digunakan untuk menyimpan dan mengirim data secara terstruktur, sementara MD digunakan untuk menyusun teks dengan markup yang sederhana. Meskipun begitu, ada beberapa alasan mengapa seseorang mungkin ingin mengonversi file XML ke MD, seperti untuk mengubah dokumen XML yang tidak terstruktur menjadi teks yang lebih mudah dibaca dan dipahami, atau untuk mengekstrak konten dari file XML untuk digunakan dalam aplikasi atau situs web. Salah satunya jika ingin migrasi dari Wordpress/Blogger ke cms SSG seperti Hugo, Jekyll dan lainnya, maka perlu mengubah postingan xml tersebut kedalam format Markdown(MD)
Berikut ini adalah cara konversi file XML ke MD yang dapat dilakukan dengan beberapa langkah sederhana:
Salah satu cara untuk convert/mengubah xml ke md bisa dengan NodeJS menggunakan script github [ini](https://github.com/palaniraja/blog2md)
## Install NodeJS
Hal pertama yang harus dilakukan adalah install NodeJS disini

## Download Scriptnya
Kemudian download scriptnya dengan cara
```
git clone https://github.com/palaniraja/blog2md.git
```
atau bisa download manual dengan klik code->download zip
![download zip](/img/downloadzip.png)

## Jalankan Script
Berikut ini usage script tersebut
```
node index.js b|w <BLOGGER BACKUP XML> <OUTPUT DIR>
```
Untuk impor Blogger, postingan blog dan komentar (sebagai file terpisah <postname>-comments.md) akan dibuat di direktori "out"
```
node index.js b your-blogger-backup-export.xml out
```


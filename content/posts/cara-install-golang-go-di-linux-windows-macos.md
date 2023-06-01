---
title: 'Cara Install Golang di Windows, Linux dan MacOS'
date: 2023-06-01
draft: false
author: ["Rico Ardiansyah"]
categories:
- Tutorial
- Golang
tags:
- Golang
cover:
    image: "https://go.dev/blog/go-brand/Go-Logo/PNG/Go-Logo_Blue.png"
---
# Cara Install Go di Windows, Linux, dan MacOS

Go atau disebut juga Golang adalah bahasa pemrograman open source yang dikembangkan oleh Google. Go mempunyai fitur-fitur seperti bahasa pemrograman C yang menjadikannya bahasa pemrograman yang sangat efisien untuk pengembangan aplikasi berbasis web, mobile, desktop, dan bahkan IoT. Untuk mulai menggunakan bahasa pemrograman Go, kita harus melakukan instalasi pada sistem operasi yang digunakan. Pada artikel ini, kita akan membahas cara instalasi Go pada sistem operasi Windows, Linux, dan MacOS.

## Instalasi Go di Windows

### Langkah 1: Unduh Paket Instalasi Go

Untuk instalasi Go di Windows, pertama-tama kita harus mengunduh paket instalasi Go terlebih dahulu. Buka [halaman unduh resmi Go](https://golang.org/dl/) dan unduh file instalasi Go terbaru untuk Windows. Pilih sesuai dengan jenis sistem operasi yang digunakan, apakah 32-bit atau 64-bit.

![Download Go for Windows](https://i.imgur.com/p9is0IH.png)

### Langkah 2: Instalasi Go

Setelah file instalasi Go untuk Windows berhasil diunduh, kita dapat membuka file tersebut dengan mengklik dua kali pada file tersebut. Maka akanmuncul jendela seperti di bawah ini:

![Go Installer](https://i.imgur.com/3J8Uk7v.png)

Klik tombol "Next" untuk memulai proses instalasi.

### Langkah 3: Konfigurasi Instalasi Go

Setelah itu, kita akan diminta untuk memilih direktori tempat instalasi Go. Pilih direktori yang diinginkan atau gunakan direktori default yang sudah terisi.

![Select Installation Directory](https://i.imgur.com/tt4uC1e.png)

Selanjutnya, pilih komponen yang akan diinstal. Jika tidak yakin, biarkan pilihan default dan klik "Next".

![Select Components](https://i.imgur.com/8O0y3wL.png)

Pada langkah selanjutnya, kita akan diminta untuk memilih folder untuk menginstal Tools Go. Pilih direktori yang diinginkan atau gunakan direktori default. Kemudian, klik "Install" untuk memulai proses instalasi.

![Select Tools Directory](https://i.imgur.com/vb8xT3u.png)

### Langkah 4: Instalasi Selesai

Setelah proses instalasi selesai, klik "Finish" untuk menyelesaikan instalasi.

![Finish Installation](https://i.imgur.com/7G8nZL9.png)

Kita telah berhasil menginstal Go di Windows.

## Instalasi Go di Linux

### Langkah 1: Unduh Paket Instalasi Go

Untuk instalasi Go di Linux, kita dapat mengunduh paket instalasi Go terbaru dari [halaman unduh resmi Go](https://golang.org/dl/). Pilih paket instalasi Go yang sesuai dengan arsitektur sistem operasi Linux yang digunakan.

### Langkah 2: Instalasi Go

Setelah file instalasi Go berhasil diunduh, kita dapat melakukan instalasi dengan menggunakan terminal. Buka terminal dan lakukan proses instalasi dengan menjalankan perintah di bawah ini:

```
$ sudo tar -C /usr/local -xzf go1.16.4.linux-amd64.tar.gz
```

Pastikan untuk mengganti versi Go dan nama file Go yang telah diunduh dengan nama file yang sesuai.

### Langkah 3: Konfigurasi Lingkungan

Setelah instalasi selesai, kita perlu mengkonfigurasi lingkungan Go. Tambahkan konfigurasi Go ke file `.bashrc` dengan menjalankan perintah di bawah ini:

```
$ echo "export PATH=$PATH:/usr/local/go/bin" >> ~/.bashrc
```

Setelah itu, jalankan perintah di bawah ini untuk memuat ulang file `.bashrc` dan menerapkan konfigurasi baru:

```
$ source ~/.bashrc
```

### Langkah 4: Verifikasi Instalasi

Setelah proses instalasi selesai, kita dapat memverifikasi instalasi Go dengan menjalankan perintah di bawah ini pada terminal:

```
$ go version
```

Jika Go telah terinstal dengan benar, maka akan muncul versi Go yang terinstal.

## Instalasi Go di MacOS

### Langkah 1: Unduh Paket Instalasi Go

Untuk instalasi Go di MacOS, kita dapat mengunduh paket instalasi Go terbaru dari [halaman unduh resmi Go](https://golang.org/dl/). Pilih paket instalasi Go sesuai dengan arsitektur sistem operasi MacOS yang digunakan.

### Langkah 2: Instalasi Go

Setelah file instalasi Go berhasil diunduh, kita dapat melakukan instalasi dengan menggunakan terminal. Buka terminal dan lakukan proses instalasi dengan menjalankan perintah di bawah ini:

```
$ sudo tar -C /usr/local -xzf go1.16.4.darwin-amd64.tar.gz
```

Pastikan untuk mengganti nama file Go yang telah diunduh dengan nama file yang sesuai.

### Langkah 3: Konfigurasi LingkunganSetelah instalasi selesai, kita perlu mengkonfigurasi lingkungan Go. Tambahkan konfigurasi Go ke file `.bash_profile` dengan menjalankan perintah di bawah ini:

```
$ echo "export PATH=$PATH:/usr/local/go/bin" >> ~/.bash_profile
```

Setelah itu, jalankan perintah di bawah ini untuk memuat ulang file `.bash_profile` dan menerapkan konfigurasi baru:

```
$ source ~/.bash_profile
```

### Langkah 4: Verifikasi Instalasi

Setelah proses instalasi selesai, kita dapat memverifikasi instalasi Go dengan menjalankan perintah di bawah ini pada terminal:

```
$ go version
```

Jika Go telah terinstal dengan benar, maka akan muncul versi Go yang terinstal.

## Kesimpulan

Go adalah bahasa pemrograman yang sangat efisien dan cepat. Instalasinya pun cukup mudah untuk dilakukan pada sistem operasi Windows, Linux, dan MacOS. Pada artikel ini, kita telah membahas cara instalasi Go pada ketiga sistem operasi tersebut. Setelah instalasi selesai, kita dapat mulai belajar bahasa pemrograman Go dan membangun aplikasi yang efisien dan handal.

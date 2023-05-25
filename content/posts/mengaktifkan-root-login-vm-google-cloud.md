---
title: 'Cara Mengaktifkan Login Root di VM Google Cloud'
date: 2023-05-25
draft: false
author: ["Rico Ardiansyah"]
categories:
- Tutorial
- Linux
cover:
    image: "https://upload.wikimedia.org/wikipedia/commons/thumb/5/51/Google_Cloud_logo.svg/640px-Google_Cloud_logo.svg.png"
---
## Cara Mengaktifkan Login Root pada VM Google Cloud

![Google Compute Engine logo](https://raw.githubusercontent.com/0xricoard/hugo-blog/main/static/img/IMG_6270.png)
Secara default, Google Cloud Platform (GCP) tidak mengizinkan login langsung sebagai root user pada instance VM. Namun, Anda dapat menggunakan akun dengan hak akses sudo untuk memperoleh akses root. Berikut ini adalah langkah-langkah untuk mengaktifkan login root pada VM Google Cloud.

### Langkah 1 - Membuat Instance VM

Langkah pertama yang harus dilakukan adalah membuat sebuah instance VM baru pada Google Cloud. Anda bisa mengikuti panduan dari Google Cloud untuk membuat VM baru. 

### Langkah 2 - Login ke Console SSH

Setelah instance VM selesai dibuat, Klik tulisan SSH disamping daftar instance VM.
![SSH](https://raw.githubusercontent.com/0xricoard/hugo-blog/main/static/img/IMG_6272.jpeg)

### Langkah 3 - Mengubah Password Root

Setelah masuk ke konsol SSH, Anda harus mengubah password root terlebih dahulu dengan menggunakan perintah berikut:

```
sudo passwd root
```

Setelah memasukkan perintah ini, Anda diminta memasukkan password baru untuk akun root.

### Langkah 4 - Mengaktifkan Akses Root untuk SSH

Selanjutnya, Anda perlu mengaktifkan akses root untuk SSH dengan mengedit file konfigurasi SSH. Anda bisa menggunakan editor teks seperti nano atau vi untuk mengedit file konfigurasi SSH. Berikut ini adalah contoh menggunakan nano:

```
sudo nano /etc/ssh/sshd_config
```

Cari baris berikut dalam file konfigurasi:

```
#PermitRootLogin prohibit-password
```

Dan ubah baris tersebut menjadi:

```
PermitRootLogin yes
```

Kemudian simpan perubahan dengan menekan tombol `Ctrl+X`, diikuti dengan `Y` untuk menyimpan, dan `Enter` untuk keluar dari editor.

### Langkah 5 - Restart Layanan SSH

Terakhir, restart layanan SSH untuk mengaktifkan perubahan:

```
sudo service ssh restart
```

Setelah restart, Anda dapat menggunakan akun root untuk masuk ke instance VM melalui SSH.

### Catatan Keamanan

Perlu diingat bahwa memberikan akses root pada sebuah instance VM dapat meningkatkan risiko keamanan. Oleh karena itu, disarankan untuk menggunakan akses root hanya jika diperlukan dan selalu mengamankan instance VM dengan cara yang tepat.

### Cara Cepat Mengedit Konfigurasi SSH

Untuk mengedit konfigurasi SSH dengan cepat, Anda bisa menggunakan perintah berikut:

```
sudo sed -i 's#PermitRootLogin prohibit-password/PermitRootLogin yes/g' /etc/ssh/sshd_config && sudo service ssh restart
```

Perintah di atas akan mengedit file konfigurasi SSH dan mengganti baris yang mengandung `#PermitRootLogin prohibit-password` menjadi `PermitRootLogin yes`. Setelah itu, perintah tersebut akan merestart layanan SSH untuk mengaktifkan perubahan. Dengan menggunakan perintah ini, Anda dapat menghemat waktu dan menghindari kesalahan saat mengedit file konfigurasi SSH. Namun, pastikan untuk selalu melakukan backup file konfigurasi sebelum melakukan perubahan apa pun untuk menghindari kehilangan data.

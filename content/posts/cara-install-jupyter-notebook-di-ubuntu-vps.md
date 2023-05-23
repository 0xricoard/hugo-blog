---
title: 'Cara Install Jupyter Notebook di Ubuntu dan VPS'
date: 2023-05-22
draft: false
author: ["Rico Ardiansyah"]
categories:
- Tutorial
cover:
    image: "https://i0.wp.com/learn.onemonth.com/wp-content/uploads/2019/07/image3-1.png?w=756&ssl=1"
---

# Apa itu Jupyter Notebook
![Jupyter Logo](https://upload.wikimedia.org/wikipedia/commons/thumb/3/38/Jupyter_logo.svg/207px-Jupyter_logo.svg.png)

Jupyter Notebook adalah aplikasi web yang digunakan untuk membuat, menjalankan, dan membagikan kode secara interaktif. Aplikasi ini sangat berguna bagi para data scientist dan programmer yang ingin membagikan dan mengembangkan kode dengan mudah. Di artikel ini, kita akan membahas langkah-langkah cara install Jupyter Notebook di Ubuntu 18, 20.04, dan 22

## Langkah-langkah installasi

**Sangat disarankan menggunakan user non-root**
Pastikan Ubuntu Anda sudah terupdate dengan menjalankan perintah berikut di terminal:

```
sudo apt-get update
sudo apt-get upgrade
```

### Instalasi Python dan pip

Untuk menjalankan Jupyter Notebook, kita perlu menginstal Python dan pip. Python adalah bahasa pemrograman yang digunakan untuk menulis kode di Jupyter Notebook, sedangkan pip adalah manajer paket untuk Python yang memudahkan instalasi paket-paket yang dibutuhkan.

Untuk menginstal Python dan pip, jalankan perintah berikut di terminal:

```
sudo apt-get install python3 python3-pip
```

### Instalasi virtualenv

Untuk mengisolasi lingkungan Python dan paket-paket yang digunakan oleh Jupyter Notebook dari lingkungan Python sistem, kita akan menggunakan virtualenv.

Untuk menginstal virtualenv, jalankan perintah berikut di terminal:

```
sudo apt-get install python3-venv
```

### Membuat virtualenv

Setelah virtualenv terinstal, kita dapat membuat virtual environment baru untuk Jupyter Notebook. Untuk membuat virtualenv, jalankan perintah berikut di terminal:

```
python3-m venv myenv
```

Perintah ini akan membuat virtualenv dengan nama "myenv" di direktori saat ini.

### Aktivasi virtualenv

Setelah virtualenv terbuat, aktifkan virtualenv dengan menjalankan perintah berikut:

```
source myenv/bin/activate
```

Setelah berhasil diaktifkan, prompt terminal akan berubah menjadi seperti berikut:

```
(myenv) user@host:~$
```

### Instalasi Jupyter Notebook

Setelah virtualenv aktif, kita dapat menginstal Jupyter Notebook dengan menggunakan pip. Jalankan perintah berikut di terminal:

```
pip install jupyter
```

Setelah proses instalasi selesai, Jupyter Notebook sudah dapat digunakan dalam virtualenv.

### Menggunakan Jupyter Notebook dalam virtualenv

Untuk menggunakan Jupyter Notebook dalam virtualenv, pastikan virtualenv sudah aktif, kemudian jalankan perintah berikut di terminal:

```
jupyter notebook
```

Setelah itu, Jupyter Notebook akan terbuka di browser default Anda dengan tampilan seperti berikut:

![Jupyter Notebook Homepage](https://docs.jupyter.org/en/latest/_images/tryjupyter_file.png)

Anda dapat membuat notebook baru dan menulis kode di dalamnya seperti biasa. Setelah selesai menggunakan Jupyter Notebook, jangan lupa untuk menonaktifkan virtualenv dengan menjalankan perintah:

```
deactivate
```

> **Catatan:**  Jika anda install di VPS dan ingin mengaksesnya dengan jaringan internet/remot jupyter notebooknya agar online maka harus melakukan konfigurasi tambahan dibawah ini:

## Instalasi di VPS

![default](https://raw.githubusercontent.com/0xricoard/hugo-blog/main/static/img/defaultjupyter.png)
Secara default web server jupyter menyediakan aplikasi antarmukanya berjalan pada jaringan lokal/localhost, Jika memakai VPS maka VPS tersebut harus diinstal GUI dan dengan protokol RDP, sangat tidak efisien mengingat GUI itu agak berat jika diinstall di ram 1gb. Nah cara solusi agar jupyter notebooknya dapat diakses lewat IP VPS/Domainnya(jika ada) maka kita perlu sedikit konfigurasi di bawah ini.

### Membuat file konfigurasi

Hal pertama yang harus dilakukan adalah kita perlu membuat file konfigurasi dengan perintah
```
jupyter notebook --generate-config
```
File konfigurasi Jupyter Notebook akan terletak di ~/.jupyter

### Edit Konfigurasi
Selanjutnya edit konfigurasi agar Jupyter notebook dapat berjalan di luar localhost dengan perintah
```
nano ~/.jupyter/jupyter_notebook_config.py
```
![Jupyter Config](https://raw.githubusercontent.com/0xricoard/hugo-blog/main/static/img/jupyter%20config.png)
Kemudian cari baris `# c.NotebookApp.ip = 'localhost'` dan hapus tanda pagar (#) pada awal baris dan ubah nilai localhost menjadi 0.0.0.0. Ini akan menjadikan Jupyter berjalan disemua jaringan yang terhubung tidak localhost saja.
Atau dapat melakukan cara cepat tanpa perlu edit manual lagi dengan cara
```
sed -i "s/# c.NotebookApp.ip = 'localhost'/c.NotebookApp.ip = '0.0.0.0'/" ~/.jupyter/jupyter_notebook_config.py
```
Perintah diatas akan otomatis mengganti tulisan localhost ke 0.0.0.0
Save dan jalankan Jupyter lagi,
Maka kita dapat mengakses Jupyter dengan IP/Domain VPSnya.
## Kesimpulan

Dalam artikel ini, kita telah membahas cara instalasi Jupyter Notebook dalam virtualenv di Ubuntu. Dengan menggunakan virtualenv, Anda dapat mengisolasi lingkungan Python dan paket-paket yang digunakan oleh Jupyter Notebook dari lingkungan Python sistem, sehingga membuat instalasi dan penggunaan Jupyter Notebook lebih mudah dan aman. Pastikan untuk mengaktifkan virtualenv sebelum menggunakan Jupyter Notebook, dan menonaktifkannya setelah selesai menggunakan.

---
title: 'Cara Install Docker di Linux, Windows, MacOS'
date: 2023-06-04
draft: false
author: ["Rico Ardiansyah"]
categories:
- Tutorial
tags:
- Docker
cover:
    image: "https://upload.wikimedia.org/wikipedia/commons/7/79/Docker_%28container_engine%29_logo.png"
---
# Cara Install Docker di Linux

Docker dapat diinstal di berbagai distribusi Linux seperti Ubuntu, Debian, CentOS, dan lain-lain. Berikut adalah panduan instalasi Docker di dua distribusi Linux yang paling umum digunakan, yaitu Ubuntu dan CentOS.

## Instalasi Docker di Ubuntu

### Tahap 1: Update Repositori

Pertama-tama, buka terminal dan jalankan perintah berikut untuk mengupdate list paket:

```
sudo apt-get update
```

### Tahap 2: Install Docker

Setelah repositori diupdate, jalankan perintah berikut untuk menginstal Docker:

```
sudo apt-get install docker.io
```

### Tahap 3: Start Docker

Jika instalasi berhasil, jalankan perintah berikut untuk memulai Docker:

```
sudo systemctl start docker
```

## Instalasi Docker di CentOS

### Tahap 1: Update Repositori

Buka terminal dan jalankan perintah berikut untuk mengupdate list paket:

```
sudo yum update
```

### Tahap 2: Install Docker

Selanjutnya, jalankan perintah berikut untuk menginstal Docker:

```
sudo yum install docker
```

### Tahap 3: Start Docker

Setelah instalasi selesai, jalankan perintah berikut untuk memulai Docker:

```
sudo systemctl start docker
```

# Cara Install Docker di Windows

Docker dapat diinstal di Windows 10 Pro, Enterprise, dan Home. Berikut adalah panduan instalasi Docker di ketiga versi Windows tersebut.

## Instalasi Docker di Windows 10 Pro or Enterprise

### Tahap 1: Unduh Installer

Kunjungi [Docker Hub](https://hub.docker.com/editions/community/docker-ce-desktop-windows/) dan klik tombol "Get Docker Desktop for Windows (stable)" untuk mengunduh installer.

### Tahap 2: Jalankan Installer

Setelah file installer selesai diunduh, klik dua kali untuk memulai instalasi. Ikuti langkah-langkah pada layar untuk menyelesaikan instalasi.

## Instalasi Docker di Windows 10 Home

### Tahap 1: Unduh Installer

Kunjungi [Docker Toolbox](https://github.com/docker/toolbox/releases) dan unduh file installer yang sesuai dengan versi Windows Anda.

### Tahap 2: Jalankan Installer

Setelah file installer selesai diunduh, klik dua kali untuk memulai instalasi. Ikuti langkah-langkah pada layar untuk menyelesaikan instalasi.

# Cara Install Docker di MacOS

Docker dapat diinstal di MacOS dengan mudah. Berikut adalah panduan instalasi Docker di MacOS.

### Tahap 1: Unduh Installer

Kunjungi [Docker Hub](https://hub.docker.com/editions/community/docker-ce-desktop-mac/) dan klik tombol "Get Docker Desktop for Mac (stable)" untuk mengunduh installer.

### Tahap 2: Jalankan Installer

Setelah file installer selesai diunduh, klik dua kali untuk memulai instalasi. Ikuti langkah-langkah pada layar untuk menyelesaikan instalasi.

# Kesimpulan

Docker adalah platform yang sangat berguna bagi pengembang software untuk membuat, menguji, dan menjalankan aplikasi di berbagai lingkungan. Proses instalasi Docker di Linux, Windows, dan MacOS sangat mudah dan dapat diikuti dengan langkah-langkah yang jelas. Dengan mengikuti panduan ini, Anda akan dapat menginstal Docker dengan mudah di platform pilihan Anda.

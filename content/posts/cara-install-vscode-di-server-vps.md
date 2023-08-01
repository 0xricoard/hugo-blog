---
title: 'Cara Install VSCode di Server VPS'
date: 2023-08-01
draft: false
author: ["Rico Ardiansyah"]
categories:
- Tutorial
tags:
- VSCode Server
- VPS
cover:
    image: "/img/vscodeserver.png"
---
![ilustrasi](/img/vscodeserver.png)
## Apa itu VSCode Server
VS Code Server adalah komponen dari Visual Studio Code yang memungkinkan Anda menjalankan dan mengakses VS Code melalui browser web atau melalui koneksi jarak jauh. Dalam konteks ini, VS Code Server berfungsi sebagai backend yang menjalankan inti dari VS Code di server atau mesin yang terpisah, sementara antarmuka pengguna (UI) VS Code diakses melalui browser web.

Pada artikel kali ini saya akan membuat tutorial Cara install VSCode di VPS yang kemudian dapat diakses melalui browser web. Dalam tutorial ini saya menggunakan VSCode Server dari repository GitHub [Coder.com](https://github.com/coder/code-server).

## Cara Install
Ada banyak cara untuk install VSCode server ini yang tercantum pada dokumentasinya https://coder.com/docs/code-server/latest/install. Namun pada kali ini saya hanya akan menggunakan 2 metode populer instalasinya yaitu dengan Script **install.sh** dan **Docker**. 

### Persyaratan
Anda memerlukan mesin tempat Anda dapat menjalankan server kode. Anda dapat menggunakan mesin fisik yang Anda miliki, atau menggunakan VM di GCP/AWS atau yang lainnya. Dengan minimun spesifikasi:

- 1 GB RAM
- 2 CPU CORE

### Menggunakan install.sh
Cara termudah untuk menginstal code-server adalah dengan menggunakan skrip instalasi untuk Linux, macOS dan FreeBSD. Skrip penginstalan mencoba menggunakan manajer paket sistem jika memungkinkan.

#### Untuk menggunkan install.sh, jalankan perintah ini
```
curl -fsSL https://code-server.dev/install.sh | sh
```
Setelah selesai, skrip instal mencetak instruksi untuk menjalankan dan memulai server kode.

#### Untuk menjalankan code-server ketik
```
code-server
```
![install.sh output](/img/installshoutput.png)
terlihat beberapa keterangan mengenai VSCode server yang sedang dijalankan untuk cek/ganti password silahkan buka file ``~/.config/code-server/config.yaml``

![Config](/img/configvscode.png)
Secara default VSCode Server berjalan di interface localhost dan dengan port 8080, Untuk dapat mengakses VSCode server dari perangkat anda maka edit **bind-addr** nya dengan mengganti 127.0.0.1 ke 0.0.0.0 dengan demikian dapat diakses dengan ``http://ipvps:8080`` 

### Menggunakan Docker
Untuk menggunakan VSCode Server menggunakan Docker silakan install Docker minimum versi 20.10 dulu [disini](https://muhammadri.co/posts/install-docker-linux-windows-macos/)

#### Setelah install Docker jalankan perintah ini 
```
docker pull codercom/code-server
```
perintah diatas digunakan untuk mendownload images code-server versi terbaru dari Docker Hub, Silakan tunggu sampai selesai, proses mendownload dan mengekstrak images tergantung dari kecepatan internet dan spesifikasi VPS yang digunakan.
#### Buat container code-server
```
docker container create --name my-code-server -p 0.0.0.0:8080:8080 \
  -v "$HOME/.config:/root/.config" \
  -v "$PWD:/home/coder/project" \
  -u "$(id -u):$(id -g)" \
  -e "DOCKER_USER=$USER" \
  codercom/code-server:latest
```
![Docker Create Container](/img/dockercreatecontainer.png)
Jika belum ada folder .config bisa buat dengan ```mkdir -p ~/.config``` 

**Keterangan:**
Perintah diatas akan membuat Container dengan nama **my-code-server** dan mengekspos port 8080 disemua interface.
#### Jalankan container
Setelah container code-server dibuat, jalankan container dengan cara
```
docker start my-code-server
```
Ubah nama container dengan nama container yang sudah dibuat


## Selesai
Jika proses instalasi sudah selesai kemudian ketik http://ipvps:8080 di browser dan masukkan password yang sudah ditentukan di file config
![tampilan vscode server](/img/tampilan.jpeg)

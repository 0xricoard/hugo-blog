---
title: 'Script Auto Install Xray&V2ray Multipath di VPS'
date: 2023-05-20
draft: false
author: ["Rico Ardiansyah"]
categories:
- Script
cover:
    image: "https://i.ibb.co/nfBGYXF/IMG-6219.jpg"
---
Halo semua kali ini saya akan share script auto install xray v2ray buat kalian yang lagi cari script auto install ini bagus banget gw udah pake 4 bulanan dan lancar banget kok, walaupun gratisan tapi fiturnya lengkap.
Oke berikut gw jabarin fitur-fitur scriptnya

# X-ray Autoscript 

|  SERVICE  |  NETWORK PORT  |
|---------- |--------|
| Vmess WS TLS (multipath)  | 443 |
| Vless WS TLS  | 443 |
| Trojan WS TLS  | 443 |
| Socks5 WS TLS  | 443 |
| Shadowsocks WS TLS (aes-256-gcm)  | 443 |
| Shadowsocks 2022 WS TLS (2022-blake3-aes-256-gcm)  | 443 |
| Vmess WS (multipath)  | 80 |
| Vless WS  | 80 |
| Trojan WS  | 80 |
| Socks5 WS  | 80 |
| Shadowsocks WS (aes-256-gcm)  | 80 |
| Shadowsocks 2022 WS (2022-blake3-aes-256-gcm)  | 80 |
| Vmess gRPC  | 443 |
| Vless gRPC  | 443 |
| Trojan gRPC  | 443 |
| Socks5 gRPC  | 443 |
| Shadowsocks gRPC (aes-256-gcm)  | 443 |
| Shadowsocks 2022 gRPC (2022-blake3-aes-256-gcm)  | 443 |
| Nginx Webserver | 8000 |
| Auto Delete Expired Account | ✅ |
| DNS Setting | ✅ |

|  ALTERNATIF PORT  |  NETWORK PORT  |
|-------------------|--------|
| HTTPS  | 2053, 2083, 2087, 2096, 8443 |
| HTTP  | 8080, 8880, 2052, 2082, 2086, 2095 |

## Cara install
Script ini khusus untuk Debian 10 sama Ubuntu 20 keatas
dan minim speknya sudah gw tes ram 512mb bisa jalan
oh ya kalian juga harus punya domain ya, bisa beli di idcloudhost atau yg lainnya paling harganya 10-15ribu untuk domain my.id nya

### Setup Cloudflare
nah yang pertama hubungin dulu domainmu ke cloudflare, kalau sudah lanjut setup DNS nya, Untuk caranya bisa dilihat pada gambar
![cf](https://raw.githubusercontent.com/dugong-lewat/autoscript/main/cf.jpg)

### Download scriptnya
Kemudian kalian download scriptnya dan paste ke vps rootnya dengan cURL atau Wget
via wget
```
bash -c "$(wget -qO- https://s.id/xraysc)"
```
via cURL
```
bash -c "$(curl -fsSL https://s.id/xraysc)"
```
Tunggu sampai selesai

## Screenshot
Berikut adalah tampilan jika sudah selesai install scriptnya, kalian bisa pilih menu-menunya
![Tampilan awal](https://i.ibb.co/nfBGYXF/IMG-6219.jpg)

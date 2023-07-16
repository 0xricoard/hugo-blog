---
title: 'Cara Download File Google Drive lewat Wget'
date: 2023-07-16
draft: false
author: ["Rico Ardiansyah"]
categories:
- Tutorial
tags: 
- wget
- Google Drive
cover:
    image: "/img/IMG_6820.jpeg"
---
![Wget dan Google Drive](/img/IMG_6820.jpeg)
Buat kalian yang biasa pakai Linux pasti gak asing lagi kan sama tool wget ini. Sebenarnya wget bisa loh buat download file di Google Drive tanpa harus buka browser, sangat membantu buat kalian yang punya Server Linux yang notabenenya gak diinstall Desktop Environment atau GUInya, Nah kalian bisa download file dari Google Drive lewat wget di terminal dengan cara berikut:
## Buka Terminal/SSH/CMD/Powershell dll
Langkah pertama silakan buka Terminal/SSH/CMD/Powershell.

## Copy link url google drivenya
Contoh: https://drive.google.com/file/d/1MOAyxDAzOMe3seKzNwTmQC1sXkxQEwiZ/view?usp=drivesdk

## Ambil id Filenya
id file google drive dapat ditemukan setelah url /d dari url google drive diatas yaitu 
``
1MOAyxDAzOMe3seKzNwTmQC1sXkxQEwiZ
``

## Jika file berukuran kecil < 100MB
Jika file google drive tersebut berukuran kurang dari 100mb maka jalankan perintah ini:
```
wget --no-check-certificate 'https://docs.google.com/uc?export=download&id=FILEID' -O FILENAME
```
Silakan ubah **FILEID** dengan ID yang sudah diketahui diatas dan ubah **FILENAME** dengan nama file sesuka hati kalian.

## Jika file berukuran lebih dari 100MB
Jika file google drive tersebut berukuran lebih dari 100mb maka jalankan perintah ini:
```
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=FILEID' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=FILEID" -O FILENAME && rm -rf /tmp/cookies.txt
```
Sama seperti diatas, Silakan ubah **FILEID** dengan ID yang sudah diketahui diatas dan ubah **FILENAME** dengan nama file sesuka hati kalian.

## Hasil
Setelah perintah dieksekusi maka hasilnya sebagai berikut
![hasil](/img/IMG_6818.jpeg)
## Penutup
Sekian tutorial tentang Cara Download File Google Drive lewat Wget.
Semoga membantu!

---
title: 'Cara Garap & Mining Testnet GagaNode'
date: 2023-01-03
draft: false
tags: ['Gaga Node', 'Testnet Guides']
categories:
- Gaga Node
- Testnet Guides
images: 
    - "https://raw.githubusercontent.com/0xricoard/hugo-blog/main/static/img/0B1AA8E8-F9FE-45F7-BD90-604F8C557C65.jpeg"
cover:
    image: "https://raw.githubusercontent.com/0xricoard/hugo-blog/main/static/img/8A651455-A9A7-4035-A2B3-C8F6D169F070.jpeg"
---

![](https://raw.githubusercontent.com/0xricoard/hugo-blog/main/static/img/0B1AA8E8-F9FE-45F7-BD90-604F8C557C65.jpeg)

Testnet Node sekarang lagi rame banget. Buat yang gak tau **Node** itu apa ya simpelnya gini kita itu ikut berpartisipasi di jaringan _Blockchain_ mereka dengan berkontribusi jadi _validator_, Tugasnya si _validator_ itu mengamankan setiap block transaksi di *blockchain*nya tersebut biar gak ada yang ngehack,_ nge*scam*, atau apalah yang illegal pokoknya(jangan main illegalan ya dosa). Oh ya sedikit sharing aja biasanya airdrop node tuh kalau pas _landing_(kamus bahasa airdropper wkwk) bisa dapet puluhan bahkan ratusan juta(tapi ini gak semuanya ya) contohnya dulu gw cair $2k pas ikut testnet nodenya Forta Network di bulan Juni terus juga Aptos yang rame banget dulu dikalangan airdropper itu juga gw ikut nodenya cair $3k bahkan yang garap cuman *claim NFTnya juga dapet.

Nah kali ini gua akan share cara garap testnet nodenya project Gaga Node. Gak tau Gaga Node?, **Gaga Node** adalah pasar tempat tinggal terdesentralisasi berikutnya untuk IP + Bandwidth, bertujuan untuk mengurangi kekurangan alamat IPv4 secara global dengan teknologi Web3.0. Saat postingan ini dibuat project Gaga Node ini lagi ngadain testnetnya yaitu dengan mining tokennya ntar dapat Gaga credit gitu. Oke langsung aja nih gw jabarin caranya.

## Cara Mining Gaga Node

Gaga Node ini bisa dijalanin di Windows, Linux, Mac, dan Android. Login dulu ke web gaga nodenya di https://dashboard.gaganode.com, Kalau belum daftar bisa daftar [disini](https://dashboard.gaganode.com/register?referral_code=ikkmmyouxz) 

## Linux

Gw rekomendasiin pake distro Ubuntu/Debian kalau buat spek minimum ram 1gb sama bandwidth kalau bisa minim 100mbps soalnya gaga node ini kalau speed bandwidthmu gede bisa nambah reward Gaga Creditnya

### 1.Pastikan izin sudo dapat digunakan

kalau sudo belum keinstall bisa pake command ini _apt-get install sudo_ buat Debian/Ubuntu

### 2.Download dan install

Download dan install dulu aplikasi Gaga Nodenya copy command dibawah ini ke terminal

Untuk linux 64 bit

```
curl -o app-linux-amd64.tar.gz https://assets.coreservice.io/public/package/22/app/1.0.3/app-1_0_3.tar.gz && tar -zxf app-linux-amd64.tar.gz && rm -f app-linux-amd64.tar.gz && cd ./app-linux-amd64 && sudo ./app service install 
```

linux 32 bit

```
curl -o app-linux-386.tar.gz https://assets.coreservice.io/public/package/21/app/1.0.3/app-1_0_3.tar.gz && tar -zxf app-linux-386.tar.gz && rm -f app-linux-386.tar.gz && cd ./app-linux-386 && sudo ./app service install 
```

**Tip:** untuk cek linuxmu 32 bit atau 64 bit ketik ini di terminal _uname -a_ kalau muncul kaya gini _Linux cs-713268424755-default 5.10.147+ #1 SMP Sat Dec 10 09:54:06 UTC 2022 **x86\_64** GNU/Linux_ berarti linuxmu 64 bit kalau selain itu ya 32 bit

### 3.Start service Gaga Node

Setelah keinstall langkah berikutnya jalankan servicenya dengan command ini

```
sudo ./app service start
```

### 4.Cek status

Cek status service gaga nodenya

```
./app status
```

Pastiin statusnya running kayak gini

![](https://raw.githubusercontent.com/0xricoard/hugo-blog/main/static/img/appstatus.png)

### 5.Set token

nah ini yang paling penting kalau nodenya udah running biar nodemu dapat reward Gaga Creditnya lu harus set token dulu, Untuk liat tokenmu bisa di menu Install & Run di paling atas ada tokenmu seperti di ss ini

![](https://raw.githubusercontent.com/0xricoard/hugo-blog/main/static/img/installrun.png)

Copy tokennya ya terus paste command ini

```
sudo ./apps/gaganode/gaganode config set --token=tokenmu
```

Ganti tulisan **tokenmu** dengan token yang udah dicopy tadi, kalau udah tekan enter

### 6.Restart Gaga Node

Abis set token lu harus restart nodenya dengan command ini

```
./app restart
```

Terus cek status nodenya _error_ apa kagak pake command di no 4 _./app status_ kalau RUNNING ya berarti dah jalan kalau error ya gw gak tau wkwk

### 7.Cek node diweb Gaga Node

Buat ngecek node lu udah sukses mining apa belum bisa dicek di menu **Nodes**

![](https://raw.githubusercontent.com/0xricoard/hugo-blog/main/static/img/E903155C-1E1A-4CE3-90B3-93A9F7FBFE8A.png)

Disitu keliatan semua nodemu yang lagi aktif mining.

Oke itu aja cara miningnya gampang kan?

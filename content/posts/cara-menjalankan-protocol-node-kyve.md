---
title: 'Cara Menjalankan Protocol Node di KYVE Network'
date: 2023-05-08
draft: false
author: ["Rico Ardiansyah"]
categories:
- Node
cover:
    image: "https://i.ibb.co/7gd9QJg/IMG-6090.jpg"
---
# Apa itu protocol node KYVE?
![KYVE Web App dashboard](https://raw.githubusercontent.com/0xricoard/hugo-blog/main/static/img/kyve%20protocol.png)
Protocol node kyve adalah tulang punggung kumpulan penyimpanan KYVE. Mereka bertanggung jawab untuk mengumpulkan data dari sumber data, menggabungkan dan mengunggahnya ke penyedia penyimpanan Web3 seperti Arweave dan memverifikasinya. Ini memungkinkan KYVE untuk menyimpan aliran data apa pun secara permanen dan dengan cara terdesentralisasi.

## Instalasi
Spesifikasi minimum untuk menjalankan protocol node adalah:
- 2 or more physical CPU cores
- 16 GB RAM
- 512 GB DISK
- 50mbps network bandwidth
### Membuat wallet Arweave
Buat wallet arweave [disini](https://arweave.app/add) setelah itu simpan keystore anda berbentuk .json itu jangan sampai hilang.
### Membuat wallet Bundlr
Bundlr membutuhkan nodejs maka dari itu install dulu nodejsnya dengan perintah:
```
sudo apt-get update
```
```
curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash -
```
```
sudo apt-get install -y nodejs
```
kemudian cek apakah nodejs berhasil diinstall
```
node -v
```
Untuk menyiapkan dompet Bundlr, ikuti langkah-langkah yang sama persis seperti di Menyiapkan dompet Arweave. Setelah menyelesaikan langkah-langkah di atas, cara termudah untuk mengatur dompet Bundlr adalah dengan menginstal Bundlr CLI:
```
npm install -g @bundlr-network/client
```
stelah selesai danai wallet bundlrnya dengan perintah ini, perlu dicatat silahkan upload keystore arweave anda (.json) ke dalam vps root anda menggunakan WinSCP atau Mobaxterm dll
```
bundlr fund 1000000000000 -h https://node1.bundlr.network -w arweave.json -c arweave
```
Dalam contoh ini gw mendanai Bundlr dengan 1 $AR yang seharusnya lebih dari cukup, untuk beli arweave bisa dibinance atau bybit. Setelah sekitar ~30 menit, Anda dapat melihat saldo Anda:
```
bundlr balance gantidenganwalletarweavemu -h https://node1.bundlr.network -c arweave
```
### Install KYSOR
Install binari terbaru kysor dengan cara
```
wget https://github.com/KYVENetwork/kyvejs/releases/download/%40kyve%2Fkysor%401.0.0-beta.20/kysor-linux-x64.zip
unzip kysor-linux-x64.zip
mv kysor-linux-x64 kysor
chmod 700 kysor
```
setelah selesai install cek versi kysor dengan
./kysor version
### Inisialisasi KYSOR
Setelah instalasi KYSOR berhasil, sekarang perlu diinisialisasi. Pada kali ini saya akan menginisialisasinya pada jaringan testnet (KAON) dan pada pool Cosmoshub kalian bisa lihat semua pool yang tersedia di [https://app.kaon.kyve.network/#/pools](https://app.kaon.kyve.network/#/pools)
```
./kysor init \
--chain-id 'kaon-1' \
--autoDownloadBinaries = true \
--rpc 'https://rpc-eu-1.kaon.kyve.network' \
--rest 'https://api-eu-1.kaon.kyve.network'
```
Instalasi kysor akan terletak pada folder .kysor
### Membuat Valaccount
Setelah KYSOR diinisialisasi, kita lanjutkan ke langkah berikutnya. Untuk setiap pool yang Anda jalankan, sebuah valaccount harus dibuat. Sebuah valaccount baru dengan mnemonic baru dapat dibuat dengan cara berikut:
```
./kysor valaccounts create \
--name 'cosmoshub' \
--pool 0 \
--storage-priv "$(cat root/arweave.json)" \
--metrics
```
silahkan sesuaikan letak dari keystore arweave anda disini saya meletakkannya di folder root.
perintah diatas akan membuat file cosmoshub.toml di bawah direktori home KYSOR di ~/.kysor/valaccounts/ di mana semua valaccounts lainnya disimpan. Di sana Anda dapat melihat konfigurasi valaccount Anda.
## Start Node
Catatan: Untuk Pool cosmoshub kita perlu membuat file .env dengan cara
```
echo 'KYVEJS_TENDERMINT_BSYNC_RPC="https://cosmos-rpc.polkachu.com/"' > .env
``` 
kemudian start nodenya
```
./kysor start --valaccount 'cosmoshub' --env-file="/root/.env"
```
Setelah node berhasil dimulai, Anda akan melihat log berikut ini:
```
2023-02-13 08:46:00.618  INFO  Starting node ...

2023-02-13 08:46:00.624  INFO  Starting metric server on: http://localhost:8080/metrics
2023-02-13 08:46:00.828  INFO  Checking account balance on StorageProvider:Bundlr
2023-02-13 08:46:00.872  INFO  Account has available funds on StorageProvider:Bundlr

2023-02-13 08:46:00.873  INFO  Chain ID = kyve-kaon
2023-02-13 08:46:00.873  INFO  Pool ID = 0
2023-02-13 08:46:00.873  INFO  Runtime = @kyvejs/tendermint-bsync
2023-02-13 08:46:00.873  INFO  Valaddress = kyve1887l27uwn5r6u9gxw7dg9wt0kqh7uk23suumzc

2023-02-13 08:46:00.873  INFO  @kyvejs/tendermint-bsync = v1.0.0-beta.9
2023-02-13 08:46:00.873  INFO  @kyvejs/protocol = v1.0.0-beta.14

2023-02-13 08:46:00.876  INFO  Valaccount has not joined the pool with id 0 yet
2023-02-13 08:46:00.876  INFO  Visit https://app.kyve.network and join the pool from your validator account:

2023-02-13 08:46:00.876  INFO  Valaddress:    kyve1887l27uwn5r6u9gxw7dg9wt0kqh7uk23suumzc
2023-02-13 08:46:00.876  INFO  Valname:       causal-chocolate-sparrow

2023-02-13 08:46:00.876  INFO  The node will not continue until the account is authorized
```
setelah itu buka web kyve di [https://app.kaon.kyve.network/#/validators?status=1](https://app.kaon.kyve.network/#/validators?status=1) konek walletmu dan klik Become a Validator di pojok kanan atas
silahkan isi data Valaddress dan Valname sesuai log yang muncul di nodemu

Itulah tutorial cara menjalankan protocol node kyve. Semoga Membantu!

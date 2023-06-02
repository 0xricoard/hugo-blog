---
title: 'Cara Membuat dan Menjalankan Node di Forta Network'
date: 2023-06-02
draft: false
author: ["Rico Ardiansyah"]
categories:
- Tutorial
- Node
tags:
- Forta Network
- Node
cover:
    image: "https://forta.org/wp-content/uploads/2022/06/og-img.jpg"
---
![Forta Network](https://forta.org/wp-content/uploads/2022/06/og-img.jpg)
Pada artikel ini saya akan membuat tutorial Cara Membuat dan Menjalankan Node di Forta Network, Tutorial ini agak panjang jadi jangan di skip-skip ya agar nantinya tidak ada error. Sebelumnya apa sih Forta Network dan kegunaan Nodenya itu?
# Apa itu Forta Network
![Forta Home](/img/fortahome.png)
Forta adalah jaringan deteksi waktu nyata untuk keamanan & pemantauan operasional aktivitas blockchain. Forta adalah jaringan pemantauan berbasis komunitas yang terdesentralisasi untuk mendeteksi ancaman dan anomali pada DeFi, NFT, tata kelola, jembatan, dan sistem Web3 lainnya secara real-time. Dengan adanya peringatan yang tepat waktu dan relevan tentang keamanan dan kesehatan sistem yang dimiliki atau bergantung, protokol dan investor dapat bereaksi dengan cepat untuk menetralisir ancaman dan mencegah atau meminimalkan hilangnya dana. Forta terdiri dari jaringan terdesentralisasi dari operator node independen yang memindai semua transaksi dan perubahan status blok demi blok untuk transaksi dan ancaman yang mencolok. Ketika sebuah masalah terdeteksi, operator node mengirimkan peringatan kepada pelanggan tentang potensi risiko, yang memungkinkan mereka untuk mengambil tindakan. Dengan memanfaatkan Forta, para pengembang dapat membangun bot pendeteksi dan model pembelajaran mesin, dan menjalankannya di jaringan Forta yang terdesentralisasi untuk mengungkap aktivitas anomali pada setiap transaksi blockchain. Forta akan diamankan dan diatur oleh kontrak pintar dan penggunaan utilitas FORT dan token tata kelola.

## Apa itu Scan Node
Scan Node adalah bagian penting dari infrastruktur Forta karena membantu menjalankan bot dan membagikan peringatan apa pun. Cara terbaik untuk memperluas jaringan adalah dengan menjalankan node pemindaian Anda sendiri dan membuat bandwidth untuk menjalankan lebih banyak bot.

## Cara membuat dan menjalankan Scan Node
Berikut saya jabarkan langkah-langkah bagaimana cara membuat node di forta network dan menjalankan agar dapat reward staking $FORT nantinya.

### Minimum spesifikasi
Pada dokumentasi official dari Forta Network tercantum bahwa Minimum spesifikasi untuk menjalankan node yaitu:
- 64-bit Linux distribution
- CPU with 4+ cores
- 16GB RAM
- Connection to Internet
- Docker v20.10+
- 100GB SSD (in addition to full node requirements)
- Recommended: Full node (any chain)

### Menyinkronkan waktu sistem
Untuk menghasilkan stempel waktu yang benar pada peringatan dan menghindari masalah otorisasi pada saat menerbitkan peringatan, **Anda harus memastikan bahwa waktu sistem sudah benar**. Jika waktu sistem tidak benar, node Anda akan gagal menerbitkan peringatan dan mungkin tidak menghasilkan reward.

Saya menyarankan untuk menggunakan ``systemd-timesyncd`` yang tersedia secara luas dan memadai sebagai daemon sinkronisasi waktu. Setelah dijalankan, ia akan menyinkronkan waktu sistem secara berkala di latar belakang.

Untuk mengaktifkan, ``systemd-timesyncd`` dan memeriksa hasilnya, Anda dapat melakukannya:
```
sudo systemctl enable systemd-timesyncd
sudo systemctl start systemd-timesyncd
```
Kemudian cek apakah waktu sudah berhasil disinkronkan dengan
```
timedatecl status
```
Jika muncul output seperti ini dan NTPnya sudah aktif berarti waktu sudah berhasil disinkronkan
```
Local time: Tue 2022-01-01 17:00:00 -03
           Universal time: Tue 2022-01-01 20:00:00 UTC
                 RTC time: Tue 2022-01-01 20:00:00
                Time zone: America/Argentina/Buenos_Aires (-03, -0300)
System clock synchronized: yes
              NTP service: active  <------------------- (it worked)
          RTC in local TZ: no
```
### Install dan konfigurasi Docker
Instal Docker (minimal v20.10)

Tambahkan file bernama ``daemon.json`` ke direktori ``/etc/docker`` Anda dengan konten berikut:
```
{
   "default-address-pools": [
        {
            "base":"172.17.0.0/12",
            "size":16
        },
        {
            "base":"192.168.0.0/16",
            "size":20
        },
        {
            "base":"10.99.0.0/16",
            "size":24
        }
    ]
}
```
![Daemon.json](/img/daemonjson.png)

## Install Forta
Software Forta scan node tersedia untuk distribusi Linux 64-bit yang populer menggunakan repositori resmi Forta. Metode instalasi paket dapat diverifikasi (diverifikasi otomatis selama instalasi) dan membantu Anda menginstal dependensi yang diperlukan.

### Install via YUM (CentOS, Fedora, Red Hat Enterprise Linux dll.)
```
sudo curl https://dist.forta.network/repositories/yum/Forta.repo -o /etc/yum.repos.d/Forta.repo -s
sudo yum install forta
```
### Install via APT (Ubuntu, Debian dll.)
```
sudo curl https://dist.forta.network/pgp.public -o /usr/share/keyrings/forta-keyring.asc -s
echo 'deb [signed-by=/usr/share/keyrings/forta-keyring.asc] https://dist.forta.network/repositories/apt stable main' | sudo tee -a /etc/apt/sources.list.d/forta.list
sudo apt-get update
sudo apt-get install forta
```

## Pengaturan Awal
CLI Forta scan node memungkinkan Anda untuk mengatur direktori konfigurasi Forta pertama Anda bersama dengan membuat dan mengelola kunci privat node pemindaian Anda.

### Inisialisasi Direktori Forta
Inisialisasi membuat kunci pribadi yang akan menandatangani alert dari Scan node Anda. Anda harus mengatur variabel lingkungan ``FORTA_PASSPHRASE`` atau memberikan flag --passphrase pada perintah ``init``.

Inisialisasi Forta menggunakan perintah forta init
```
forta init --passphrase <your_passphrase>
```
> **Catatan!:** Silahkan ganti ``<your_passphrase>`` dengan passphrase/password yang Anda inginkan.

![Forta init](/img/fortainit.png)
Perintah diatas akan menghasilkan direktori config, Sebuah private key baru dan address Anda.
> **Catatan!:** Download dan simpan baik-baik private key anda dengan cara mendownload semua file di dalam folder ``.forta``

## Konfigurasi systemd
Systemd digunakan untuk menjalankan Scan Node Forta di latar belakang dan apabila terhenti akan merestart secara otomatis. Buat file ``env.conf`` di direktori ``/etc/systemd/system/forta.service.d`` dan masukkan kode ini

```
[Service]
Environment="FORTA_DIR=<direktori_forta_mu>"
Environment="FORTA_PASSPHRASE=<passphrase_mu>"
```
![Env Config](/img/envconfig.png)
**Catatan:** Silahkan ganti ``<direktori_forta_mu>`` dengan direktori config fortamu dan ``<passphrase_mu>`` dengan passhphrase yang sudah ditentukan.

## Konfigurasi Chain API
Di dalam direktori Forta Anda, sekarang terdapat file config.yml. Anda harus mengonfigurasi file tersebut agar Scan Node Anda mengetahui cara mendapatkan data blockchain.

Scan Node Anda akan didaftarkan untuk memindai satu blockchain. Untuk mengizinkan scan node Anda mendapatkan data blockchain, Anda harus menyediakan scan.jsonRpc.url yang valid.

Berikut adalah contoh konfigurasi untuk scan Ethereum Mainnet menggunakan Alchemy Growth plan dan endpoint HTTP:
```
chainId: 1

# The scan settings are used to retrieve the transactions that are analyzed
scan:
  jsonRpc:
    url: https://eth-mainnet.alchemyapi.io/v2/KEY

# This is needed only for scanning Ethereum Mainnet and Fantom
trace:
  jsonRpc:
    url: https://eth-mainnet.alchemyapi.io/v2/KEY

# Optional: Bots make extra requests to check the chain state. You can point
# them to a different reliable API by using this. This defaults to `scan.jsonRpc.url`. 
jsonRpcProxy:
  jsonRpc:
    url: http://different-api:8545
```
Forta saat ini hanya support EVM Chain yaitu BSC, Polygon, Avalanche, Arbitrum, Optimism, Fantom.

Dibawah ini adalah kode selain ETH:
### BSC
```
chainId: 56

scan:
  jsonRpc:
    url: https://bscrpc.com/

trace:
  enabled: false
  ```
### Polygon
```
chainId: 137

scan:
  jsonRpc:
    url: https://polygon-rpc.com/

trace:
  enabled: false
```
### Avalanche
```
chainId: 43114

scan:
  jsonRpc:
    url: https://rpc.ankr.com/avalanche

trace:
  enabled: false
```
### Arbitrum
```
chainId: 42161

scan:
  jsonRpc:
    url: https://rpc.ankr.com/arbitrum

trace:
  enabled: false
```
### Optimism
```
chainId: 10

scan:
  jsonRpc:
    url: https://rpc.ankr.com/optimism

trace:
  enabled: false
```
### Fantom
```
chainId: 250

scan:
  jsonRpc:
    url: https://rpc.ftm.tools/

trace:
  jsonRpc:
    url: https://rpcapi-tracing.fantom.network/
```
## Register Scan Node
**Pastikan Anda telah mengatur chainId di ``config.yml`` dengan benar sebelum mendaftarkan node Anda**. Scan Node Anda hanya dapat didaftarkan **satu kali** dan untuk memindai chain tertentu.

Anda harus membuat Node Pool terlebih dahulu dengan cara buka [Forta App](https://app.forta.network/) dan konek wallet anda kemudian klik **My Node Pools** dan klik **Add Scanner Pool** pilih Chain yang ingin diregister kemudian klik **Register Scan Node Pool** dan Approve transaksi pada wallet.
![Create Node Pool](/img/createnodepool.png)

Selanjutnya Anda dapat register node anda dengan:
- melakukan ``forta authorize pool --passphrase <passphrasemu> --id <pool-id-mu>``
- menyalin token ke Forta App seperti yang dijelaskan di halaman [scanner pool management](https://docs.forta.network/en/latest/scanner-pools/) pada dokumen.

kemudian paste output dari forta register untuk mendaftarkan scan node tersebut
![tempel output](/img/pasteoutput.png)

## Stake token FORT
Anda harus stake FORT miinimal 2500 untuk mengaktifkan node dan mendapatkan reward, kalian bisa pergi ke Forta App [disini](https://app.forta.network/) dan klik My Node Pools
![add stake](/img/addstake.png)

# Jalankan Scan Node
Setelah semua konfigurasi diatas selesai selanjutnya kita dapat menjalankan node Forta dengan

## Start Forta via systemd
Jalankan Systemd yang telah dibuat tadi
```
sudo systemctl daemon-reload
sudo systemctl enable forta
sudo systemctl start forta
```

## Start Forta dengan Manual
anda bisa menjalankan forta dengan manual tetapi saya tidak merekomendasikan dikarenakan ketika VPS anda me-restart maka node forta tidak akan berjalan secara otomatis ketika booting.
```
forta run --passphrase <passphrase_mu>
```
## Cek Log dan Status Forta
Setelah start node forta, kita dapat memverifikasi apakah node forta berjalan dengan baik dan tidak ada error dengan cara

### Cek Log Docker
kita dapat melihat log docker dari container forta-scanner dengan realtime dengan cara
```
docker logs -f forta-scanner --tail 100
```

### Cek Status Forta
Anda dapat mengecek status dari node forta tersebut apakah berjalan dengan baik atau tidak dengan perintah berikut
```
forta status
```
![Forta status](/img/fortastatus.png)
**Pastikan statusnya hijau semua** yang artinya semua service forta berjalan dengan baik tanpa ada kesalahan.

## Penutup
Selamat! Sekarang anda sudah selesai membuat dan menjalankan node forta anda, Selanjutnya Anda tinggal menunggu reward $FORT dari node anda, Reward Forta akan didistribusikan tiap minggu.

Itulah tutorial Cara Membuat dan Menjalankan Node di Forta Network. Semoga membantu!

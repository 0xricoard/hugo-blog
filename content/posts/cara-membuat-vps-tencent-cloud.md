---
title: 'Cara Membuat VPS di Tencent Cloud'
date: 2023-06-06
draft: false
author: ["Rico Ardiansyah"]
categories:
- Tutorial
- Server
tags:
- Tencent Cloud
- Cloud Computing
- VPS
cover:
    image: "/img/tencentcloudlogo.png"
---
Tencent Cloud saat ini penyedia layanan cloud computing yang sangat populer di Indonesia. Didirikan pada tahun 2013 Tencent Cloud dengan cepat berkembang pesat, Pada akhir tahun 2021 perusahaan asal China tersebut mendirikan datacenternya yang berlokasi di Indonesia

## Cara Membuat VPS di Tencent Cloud
Untuk cara membuat VPS linux di Tencent Cloud sangatlah gampang, Berikut ini langkah-langkah Cara Membuat VPS Linux di Tencent Cloud
1. Buka halaman produk Cloud Virtual Machine [disini](https://console.tencentcloud.com/cvm/instance/index) dan klik Create
    ![Tencent Cloud Virtual Machine](/img/tencentdash.png)
2. Pilih mode Billing Silakan pilih Billing Pay as You Go atau spot instances
    ![Tencent Billing Mode](/img/tencentbilling.png)
3. Pilih Region dan Zone, Pilih Lokasi dan Zona VPS sesuai yang diinginkan
   ![Region and Zone](/img/tencentregion.png)
4. Pilih Spesifikasi, Silakan pilih spesifikasi CPU, RAM, Network, dan lainnya pada VPS yang anda butuhkan 
   ![Pilih spek](/img/tencentspek.png)
5. Pilih OS, Versi OS dan Storage Disk yang diperlukan, Kemudian klik **Next: Configure networ and host**
   ![Pilih OS dan Disk](/img/tencentosstorage.png)
6. Pada halaman Network and Bandwidth silakan pilih Default VPC dan Default Subnet dan tentukan kecepatan bandwidth
   ![network bandwidth](/img/tencentnetworkbandwidth.png)
7. Pada Menu Security Group, Pilih **New security group** dan **centang semua port**
   ![security group](/img/tencentsecuritygroup.png)
8. Dibagian menu Other settings, Pilih **Set password** pada login method dan masukkan password yang diinginkan.
   ![Set password](/img/tencentsetpassword.png)
9. Klik **Next: confirm configuration**
10. Pada halaman Confirm configuration tertera beberapa informasi instance VPS yang telah dikonfigurasi pada langkah-langkah diatas, Cek kembali konfigurasi VPS disini, Apabila dirasa sudah benar maka centang Terms and Agreement dan klik **Enable** maka VPS akan dibuat tunggu hingga selesai
    ![confirm configuration](/img/tencentconfirmconfiguration.png)

### Mengecek VPS
Untuk mengecek daftar VPS, Silakan klik [disini](https://console.tencentcloud.com/cvm/instance), Pada halaman instances terlihat beberapa informasi VPS yang telah dibuat mulai dari Nama, Status, Spek instance, Alamat IP dan billing.

Anda dapat login menggunakan IP yang tertera pada halaman tersebut dan dengan kredensial yang sudah dibuat tadi.

## Penutup
Itulah langkah-langkah Cara Membuat VPS di Tencent Cloud. Semoga membantu

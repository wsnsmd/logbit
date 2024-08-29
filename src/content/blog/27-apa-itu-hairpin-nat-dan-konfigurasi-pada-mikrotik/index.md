---
title: "Apa itu Hairpin NAT dan Konfigurasi pada Mikrotik"
description: "Memahami Hairpin NAT dan cara konfigurasinya."
date: "2024-08-29"
---

***Apa itu Hairpin NAT dan Konfigurasi pada Mikrotik***

## Pengenalan Hairpin NAT

Hairpin NAT, juga dikenal sebagai NAT Loopback, adalah sebuah fitur yang memungkinkan perangkat di dalam jaringan lokal untuk mengakses layanan atau server lain di dalam jaringan lokal menggunakan alamat IP publik. Dengan demikian, perangkat di jaringan lokal dapat mengakses server atau layanan yang berada di dalam jaringan lokal melalui alamat IP publik, bukan melalui alamat IP lokal.

## Masalah yang Dihadapi

Ketika Anda memiliki server atau layanan yang berada di dalam jaringan lokal dan ingin diakses dari jaringan lokal menggunakan alamat IP publik, Anda mungkin akan mengalami masalah. Misalnya, jika Anda memiliki server web yang berada di dalam jaringan lokal dan ingin diakses menggunakan alamat IP publik, perangkat di jaringan lokal akan mengirimkan permintaan ke server web menggunakan alamat IP publik. Namun, server web akan mengirimkan respons dengan alamat IP lokal, sehingga perangkat di jaringan lokal tidak dapat menerima respons tersebut.

## Solusi dengan Hairpin NAT

Untuk mengatasi masalah tersebut, Anda dapat menggunakan fitur Hairpin NAT pada router Mikrotik. Berikut adalah langkah-langkah konfigurasi Hairpin NAT pada Mikrotik:

1. **Konfigurasi Dasar Mikrotik**
   - **Login ke Mikrotik**: Gunakan WinBox untuk login ke router Mikrotik.
   - **Reset Konfigurasi**: Jika perlu, reset konfigurasi Mikrotik untuk memulai dari awal.
   - **Set Nama Router**: Set nama router Mikrotik.
   - **Set Nama Interface**: Set nama interface.
   - **Konfigurasi PPPoE Client**: Konfigurasi PPPoE client pada interface WAN.
   - **Konfigurasi DNS**: Konfigurasi DNS untuk memudahkan akses ke internet.
   - **Konfigurasi NAT untuk LAN**: Konfigurasi source NAT untuk mengubah alamat IP lokal menjadi alamat IP publik[^2].

2. **Konfigurasi Hairpin NAT**
   - **Buat Alamat-List**: Buat alamat-list untuk LAN dan WAN.
     ```plaintext
     /ip firewall address-list add address=192.168.10.0/24 comment=Management list=LANs
     /ip firewall address-list add address=192.168.11.0/24 comment=Work list=LANs
     /ip firewall address-list add address=192.168.12.0/24 comment=Security list=LANs
     /ip firewall address-list add address=192.168.13.0/24 comment=Home list=LANs
     /ip firewall address-list add address=192.168.14.0/24 comment=Guest list=LANs

     /ip firewall address-list add address=123.123.123.123 list=WANs
     ```

   - **Mark Connections**: Mark connections dari LAN ke WAN.
     ```plaintext
     /ip firewall mangle add action=mark-connection chain=prerouting comment="Mark connections for hairpin NAT" dst-address-list=WANs new-connection-mark="Hairpin NAT" passthrough=yes src-address-list=LANs
     ```

   - **Konfigurasi Hairpin NAT**: Konfigurasi hairpin NAT dengan menambahkan rule NAT.
     ```plaintext
     /ip firewall nat add action=masquerade chain=srcnat comment="Hairpin NAT" connection-mark="Hairpin NAT" place-before=0
     ```

3. **Port Forwarding**: Jika perlu, konfigurasi port forwarding untuk mengarahkan lalu lintas ke server tertentu.
   ```plaintext
   /ip firewall nat add action=dst-nat chain=dstnat comment="Port forward: something1" dst-address-list=WANs dst-port=5001 protocol=tcp to-addresses=192.168.0.8 to-ports=5001
   ```

## Contoh Konfigurasi

Misalkan Anda memiliki server web yang berada di jaringan lokal dengan alamat IP 10.0.0.3 dan ingin diakses menggunakan alamat IP publik 123.123.123.123. Berikut adalah contoh konfigurasi hairpin NAT:

1. **Buat Alamat-List**:
   ```plaintext
   /ip firewall address-list add address=10.0.0.0/24 comment=LAN list=LANs
   /ip firewall address-list add address=123.123.123.123 list=WANs
   ```

2. **Mark Connections**:
   ```plaintext
   /ip firewall mangle add action=mark-connection chain=prerouting comment="Mark connections for hairpin NAT" dst-address-list=WANs new-connection-mark="Hairpin NAT" passthrough=yes src-address-list=LANs
   ```

3. **Konfigurasi Hairpin NAT**:
   ```plaintext
   /ip firewall nat add action=masquerade chain=srcnat comment="Hairpin NAT" connection-mark="Hairpin NAT" place-before=0
   ```

Dengan demikian, perangkat di jaringan lokal dapat mengakses server web menggunakan alamat IP publik 123.123.123.123, dan server web akan mengirimkan respons dengan alamat IP lokal yang telah diubah oleh router Mikrotik.

## Kesimpulan

Hairpin NAT adalah fitur yang sangat berguna dalam mengatasi masalah akses ke server atau layanan di dalam jaringan lokal menggunakan alamat IP publik. Dengan konfigurasi yang tepat pada router Mikrotik, Anda dapat memungkinkan perangkat di jaringan lokal untuk mengakses server atau layanan tersebut dengan mudah. Dengan demikian, Hairpin NAT menjadi salah satu solusi yang efektif dalam mengelola jaringan lokal yang kompleks.

Referensi:
[^1]: https://citraweb.com/artikel/75/
[^2]: https://www.youtube.com/watch?v=daGs-P-ROj4
[^3]: https://www.youtube.com/watch?v=1I5FywY6opQ
[^4]: https://help.mikrotik.com/docs/display/ROS/NAT
[^5]: https://forum.mikrotik.com/viewtopic.php?t=172380
[^6]: https://github.com/misterkrittin/Scripts-MikroTik/blob/main/%5BScript-MikroTik%5D%20Hairpin%20NAT.txt
[^7]: https://forum.mikrotik.com/viewtopic.php?t=196996
[^8]: https://betweenmeandlinux.wordpress.com/2017/05/23/mikrotik-hairpin-nat-akses-ke-2-server-dari-lokal-dan-internet/

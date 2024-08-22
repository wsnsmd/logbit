---
title: "Deployment Next.js pada Ubuntu dan Nginx"
description: "Panduan deployment Next.js di Ubuntu dengan Nginx reverse proxy"
date: "2024-08-21"
---

***Deployment Next.js pada Ubuntu dan Nginx***

Next.js adalah framework React yang sangat populer untuk membangun aplikasi web modern. Salah satu keuntungan utama Next.js adalah kemampuannya untuk melakukan server-side rendering, yang meningkatkan performa dan SEO. Setelah menyelesaikan pengembangan aplikasi Next.js, langkah berikutnya adalah melakukan deployment ke server. Artikel ini akan membahas langkah-langkah untuk melakukan deployment aplikasi Next.js pada Ubuntu menggunakan Nginx sebagai reverse proxy.

## Prasyarat

Sebelum memulai, pastikan Anda sudah menyiapkan beberapa hal berikut:

1. **Server Ubuntu**: Bisa berupa server fisik atau virtual, baik di cloud (seperti AWS, DigitalOcean, atau Vultr) maupun di lokal.
2. **Akses SSH ke Server**: Anda harus memiliki akses SSH ke server Ubuntu Anda.
3. **Domain**: Jika Anda ingin mengakses aplikasi melalui domain, pastikan domain Anda sudah dikonfigurasi dan diarahkan ke server.
4. **Node.js dan NPM**: Pastikan Node.js dan NPM sudah terpasang di server.

## Langkah 1: Menyiapkan Server

Pertama, pastikan server Ubuntu Anda up-to-date. Masukkan perintah berikut:

```bash
sudo apt update && sudo apt upgrade -y
```

Kemudian, pastikan Node.js dan NPM terpasang. Jika belum, Anda bisa memasangnya dengan perintah berikut:

```bash
curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
sudo apt install -y nodejs
```

Verifikasi instalasi Node.js dan NPM:

```bash
node -v
npm -v
```

## Langkah 2: Clone Repository Aplikasi Next.js

Jika Anda menyimpan kode sumber di GitHub atau GitLab, clone repository ke server Anda. Misalnya, jika aplikasi Anda ada di GitHub:

```bash
git clone https://github.com/username/reponame.git
cd reponame
```

Setelah repository berhasil di-clone, instal dependensi yang diperlukan:

```bash
npm install
```

## Langkah 3: Build Aplikasi Next.js

Sebelum menjalankan aplikasi di server, Anda perlu membuild aplikasi Next.js Anda agar siap untuk produksi. Jalankan perintah berikut:

```bash
npm run build
```

Setelah build selesai, jalankan aplikasi dengan perintah:

```bash
npm start
```

Aplikasi Anda sekarang berjalan pada port default 3000. Namun, untuk membuatnya dapat diakses melalui domain atau IP server, kita akan menggunakan Nginx sebagai reverse proxy.

## Langkah 4: Konfigurasi Nginx

Pasang Nginx di server jika belum terpasang:

```bash
sudo apt install nginx -y
```

Setelah Nginx terpasang, buat file konfigurasi baru untuk aplikasi Anda. Misalnya, jika domain Anda adalah `example.com`, Anda bisa membuat file konfigurasi di `/etc/nginx/sites-available/` dengan nama `example.com`:

```bash
sudo nano /etc/nginx/sites-available/example.com
```

Tambahkan konfigurasi berikut:

```nginx
server {
    listen 80;
    server_name example.com www.example.com;

    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

Simpan file tersebut, lalu aktifkan konfigurasi dengan membuat symlink ke direktori `sites-enabled`:

```bash
sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/
```

Periksa konfigurasi Nginx untuk memastikan tidak ada kesalahan:

```bash
sudo nginx -t
```

Jika semua berjalan lancar, restart Nginx:

```bash
sudo systemctl restart nginx
```

## Langkah 5: Mengaktifkan HTTPS dengan Let's Encrypt

Untuk meningkatkan keamanan, Anda bisa menambahkan SSL pada domain Anda menggunakan Let's Encrypt. Install `certbot`:

```bash
sudo apt install certbot python3-certbot-nginx -y
```

Kemudian jalankan certbot untuk mengkonfigurasi SSL:

```bash
sudo certbot --nginx -d example.com -d www.example.com
```

Ikuti petunjuk yang diberikan untuk menyelesaikan instalasi SSL. Setelah selesai, Nginx akan secara otomatis diperbarui untuk menggunakan HTTPS.

## Kesimpulan

Dengan mengikuti langkah-langkah di atas, Anda telah berhasil melakukan deployment aplikasi Next.js pada server Ubuntu menggunakan Nginx sebagai reverse proxy. Anda sekarang bisa mengakses aplikasi melalui domain Anda dengan keamanan SSL. Langkah-langkah ini dapat diterapkan pada berbagai jenis aplikasi Next.js dengan penyesuaian minimal. Deployment ini memastikan aplikasi Anda berjalan dengan baik di lingkungan produksi dengan performa yang optimal.

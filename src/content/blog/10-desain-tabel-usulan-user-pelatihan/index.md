---
title: "Desain Tabel Usulan Pelatihan"
description: "Contoh desain tabel dan relasinya untuk usulan pelatihan."
date: "2024-08-13"
time: "10:00:00"
---

Untuk membangun database yang mendukung skenario dimana user dapat menginput usulan pelatihan, melihat usulan mereka sendiri, dan admin dapat melihat semua usulan serta melakukan verifikasi, persetujuan, atau penolakan, kita perlu beberapa tabel utama untuk menyimpan data yang relevan. Berikut adalah desain tabel yang saya rekomendasikan:

## 1. Tabel `Users`
Tabel ini digunakan untuk menyimpan informasi tentang pengguna, baik itu admin maupun user biasa.

| Field           | Type          | Description                       |
|-----------------|---------------|-----------------------------------|
| `user_id`       | INT           | Primary key, ID unik pengguna     |
| `username`      | VARCHAR(255)  | Nama pengguna                     |
| `password`      | VARCHAR(255)  | Kata sandi pengguna               |
| `email`         | VARCHAR(255)  | Email pengguna                    |
| `role`          | ENUM('admin', 'user') | Peran pengguna dalam sistem |

## 2. Tabel `TrainingProposals`
Tabel ini menyimpan semua usulan pelatihan yang diajukan oleh user.

| Field           | Type          | Description                       |
|-----------------|---------------|-----------------------------------|
| `proposal_id`   | INT           | Primary key, ID unik usulan       |
| `user_id`       | INT           | Foreign key dari tabel `Users`    |
| `title`         | VARCHAR(255)  | Judul usulan pelatihan            |
| `description`   | TEXT          | Deskripsi usulan pelatihan        |
| `status`        | ENUM('submitted', 'approved', 'rejected') | Status usulan |
| `created_at`    | DATETIME      | Waktu usulan dibuat               |
| `updated_at`    | DATETIME      | Waktu usulan terakhir diupdate    |

## 3. Tabel `AdminActions`
Tabel ini mencatat tindakan yang diambil oleh admin terhadap usulan pelatihan.

| Field           | Type          | Description                       |
|-----------------|---------------|-----------------------------------|
| `action_id`     | INT           | Primary key, ID unik aksi         |
| `proposal_id`   | INT           | Foreign key dari tabel `TrainingProposals` |
| `admin_id`      | INT           | ID admin yang bertindak           |
| `action_type`   | ENUM('approve', 'reject') | Tipe aksi yang diambil   |
| `action_date`   | DATETIME      | Tanggal aksi diambil              |
| `note`          | TEXT          | Catatan dari admin                |

## Relasi antar Tabel
- Tabel `Users` berelasi dengan `TrainingProposals` melalui `user_id` untuk mengidentifikasi siapa yang mengajukan usulan.
- Tabel `TrainingProposals` berelasi dengan `AdminActions` melalui `proposal_id` untuk melacak keputusan yang diambil oleh admin terhadap usulan pelatihan tersebut.

Dengan desain ini, sistem dapat mendukung fungsionalitas dimana user dapat melihat hanya usulan mereka sendiri, sedangkan admin dapat melihat semua usulan dan mengambil keputusan terkait dengan mereka. Relasi yang dibuat juga memastikan bahwa semua informasi penting terkait usulan dan tindakan yang diambil terhadapnya tersimpan dengan baik dalam database.

---
title: "Hukum Rekayasa Perangkat Lunak"
description: "Kompilasi dari beberapa pendapat ahli dalam rekayasa perangkat lunak."
date: "2024-08-13"
---

Berikut adalah 50 hukum dalam rekayasa perangkat lunak (software engineering) yang merangkum prinsip-prinsip dan aturan yang sering diakui di dalam industri ini:

## Hukum Umum dalam Rekayasa Perangkat Lunak

1. **Hukum Brooks**: Menambahkan tenaga kerja pada proyek perangkat lunak yang terlambat hanya akan membuatnya semakin terlambat.
   
2. **Hukum Conway**: Struktur sistem perangkat lunak cenderung mencerminkan struktur organisasi yang mengembangkannya.

3. **Hukum Pareto (80/20 Rule)**: 80% masalah perangkat lunak biasanya disebabkan oleh 20% dari bug atau komponen yang ada.

4. **Hukum Boehm**: Kesalahan perangkat lunak lebih mahal untuk diperbaiki semakin lama mereka tetap ada dalam proses pengembangan.

5. **Hukum Lehman tentang Evolusi Perangkat Lunak**: Perangkat lunak yang digunakan dalam lingkungan nyata harus terus-menerus berkembang atau akan menjadi usang.

6. **Hukum Ketiga Levenshtein**: Kompleksitas perangkat lunak cenderung meningkat kecuali tindakan aktif dilakukan untuk menguranginya.

7. **Hukum Wirth**: Perangkat lunak menjadi lebih lambat lebih cepat daripada perangkat keras menjadi lebih cepat.

8. **Hukum Parkinson**: Kompleksitas perangkat lunak berkembang hingga memenuhi semua sumber daya yang tersedia.

9. **Hukum Murphy**: Apa pun yang dapat salah, akan salah, terutama dalam pengembangan perangkat lunak.

10. **Hukum Parnas**: Desain modular memungkinkan penundaan keputusan, yang dapat meningkatkan fleksibilitas.

## Hukum Pengujian dan Pemeliharaan

11. **Hukum Meyers tentang Pengujian**: Tidak mungkin menemukan semua bug dalam perangkat lunak.

12. **Hukum Belady dan Lehman**: Saat perangkat lunak berkembang, kompleksitas cenderung meningkat, kecuali jika langkah-langkah aktif diambil untuk menguranginya.

13. **Hukum Humphrey**: Kualitas perangkat lunak hanya bisa terjamin jika diukur dan dikelola secara konsisten.

14. **Hukum Wohlin**: Pengujian yang lebih intensif biasanya hanya menghasilkan penemuan bug yang kurang signifikan.

15. **Hukum Libes**: Semakin banyak orang yang menguji perangkat lunak, semakin besar kemungkinan mereka akan melewatkan bug yang sama.

16. **Hukum Brooks tentang Debugging**: Debugging sangat sulit sehingga program apa pun yang telah terdebug harus dicurigai mengandung bug baru.

17. **Hukum Lipow tentang Keandalan**: Tidak mungkin membuat perangkat lunak yang 100% bebas bug.

18. **Hukum Coplien**: Penemuan bug sering kali disebabkan oleh perubahan yang tidak terduga.

19. **Hukum Glass tentang Pengujian**: Tidak ada jumlah pengujian yang bisa membuktikan bahwa perangkat lunak bebas dari bug.

20. **Hukum Adams**: Sebuah program yang memiliki sedikit bug mungkin memiliki banyak bug yang belum ditemukan.

## Hukum Desain dan Arsitektur

21. **Hukum Liskov**: Subtipe harus dapat menggantikan tipe dasarnya tanpa mempengaruhi kebenaran program.

22. **Hukum Demeter**: Komponen dalam perangkat lunak sebaiknya tidak terlalu banyak mengetahui struktur internal dari komponen lain.

23. **Hukum Occam**: Pilihlah solusi yang paling sederhana dari beberapa solusi yang sama-sama efektif.

24. **Hukum Hick**: Waktu yang dibutuhkan untuk membuat keputusan meningkat dengan jumlah dan kompleksitas pilihan yang tersedia.

25. **Hukum Moore**: Jumlah transistor pada chip akan berlipat ganda setiap dua tahun, meningkatkan kemampuan perangkat keras untuk mendukung perangkat lunak yang lebih kompleks.

26. **Hukum Gall**: Sebuah sistem yang sukses selalu berkembang dari sistem yang sederhana.

27. **Hukum Parnas tentang Abstraksi**: Abstraksi yang baik adalah kunci untuk menciptakan perangkat lunak yang fleksibel dan dapat dipelihara.

28. **Hukum YAGNI (You Ain't Gonna Need It)**: Jangan tambahkan fungsionalitas sampai benar-benar diperlukan.

29. **Hukum SOLID**: Prinsip-prinsip desain yang dirumuskan oleh Robert C. Martin untuk membuat perangkat lunak lebih mudah dipelihara dan dikembangkan.

30. **Hukum KISS (Keep It Simple, Stupid)**: Solusi paling sederhana adalah yang terbaik.

## Hukum Manajemen Proyek dan Pengembangan

31. **Hukum Boehm tentang Estimasi**: Estimasi dalam pengembangan perangkat lunak biasanya salah karena orang cenderung terlalu optimis.

32. **Hukum McCabe**: Kompleksitas siklomatis dari sebuah modul seharusnya tidak lebih besar dari 10.

33. **Hukum Gilb**: Jika sesuatu tidak bisa diukur, maka tidak bisa ditingkatkan.

34. **Hukum Paretto (Lainnya)**: 80% dari pekerjaan proyek perangkat lunak biasanya dihabiskan pada 20% dari komponen yang paling kritis.

35. **Hukum Brook tentang Pengelolaan**: Komunikasi adalah faktor kunci dalam keberhasilan proyek pengembangan perangkat lunak.

36. **Hukum Basili**: Pengumpulan dan analisis data adalah dasar untuk pengambilan keputusan yang baik dalam rekayasa perangkat lunak.

37. **Hukum DeMarco**: Anda tidak bisa mengontrol apa yang tidak bisa Anda ukur.

38. **Hukum Feathers**: Codebases yang tidak dirawat akan menumpuk utang teknis, yang membuat perubahan dan perbaikan lebih sulit dari waktu ke waktu.

39. **Hukum Jones**: Semakin lama proyek perangkat lunak berlangsung, semakin besar kemungkinan anggaran dan jadwal akan melampaui batas.

40. **Hukum Larman**: Menambahkan proses formal sering kali menambah biaya dan birokrasi tanpa meningkatkan kualitas.

## Hukum Penggunaan dan Pengalaman Pengguna (UX)

41. **Hukum Fitts**: Waktu yang dibutuhkan untuk mencapai target tertentu adalah fungsi dari jarak ke target dan ukuran target.

42. **Hukum Hick (Lainnya)**: Menambahkan lebih banyak pilihan kepada pengguna dapat memperlambat keputusan dan mengurangi kepuasan.

43. **Hukum Nielsen**: Pengguna biasanya hanya akan memahami sekitar setengah dari apa yang ada di layar.

44. **Hukum Amdahl**: Percepatan yang diperoleh dari peningkatan bagian sistem tergantung pada seberapa besar bagian tersebut mempengaruhi keseluruhan sistem.

45. **Hukum Tesler**: Setiap aplikasi memiliki kompleksitas yang tidak bisa dihilangkan, hanya bisa dipindahkan.

46. **Hukum Norman**: Jika pengguna melakukan kesalahan, kesalahan itu seringkali disebabkan oleh desain sistem yang buruk.

47. **Hukum Schneiderman**: Konsistensi dalam desain antarmuka pengguna meningkatkan pembelajaran dan meminimalkan kesalahan.

48. **Hukum Cooper**: Pengguna tidak mengerti apa yang mereka inginkan sampai mereka melihat sesuatu yang mereka tidak inginkan.

49. **Hukum Tognazzini**: Perangkat lunak harus memberi pengguna umpan balik yang cepat dan dapat dipahami pada setiap tindakan yang mereka lakukan.

50. **Hukum Miller**: Pengguna bisa memegang antara 5 hingga 9 unit informasi dalam ingatan jangka pendek mereka pada waktu tertentu.

Hukum-hukum ini mencakup berbagai aspek pengembangan perangkat lunak, dari desain dan arsitektur hingga manajemen proyek dan pengalaman pengguna. Mereka memberikan panduan yang berharga bagi pengembang perangkat lunak untuk menciptakan produk yang efektif, efisien, dan mudah dipelihara.

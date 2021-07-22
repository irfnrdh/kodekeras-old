---
layout: post
title: Fakta Dibalik Gunain SSD NVME
date: 2021-04-09 19:42
category: Experience
author: irfnrdh
tags: []
summary: 
---

Taulah kalau hari ini hampir sudah sangat ramai orang membahas tentang storage SSD atau tempat penyimpanan yang digunakan di komputer, laptop, server dan apa aja deh.

Padahal SSD ini sudah diperkenalkan 30 tahun lalu dan sudah diakui 43 tahun yang lalu. 

dan pada 2019 kapasitasnya sudah mencapai 60 - 100TB dan pastinya sekarang sudah jauh lebih dari itu.

## Perbedaan SSD dan Hardisk
Hal yang paling jelas terlihat perbedaannya adalah pada cara kerjanya yang sangat jauh berbeda. SSD bekerja dengan menggunakan sistem memori dan sejenisnya sedangkan hardisk jelas menggunakan disk atau piringan. 

Proses pembacaan hardisk dilakukan dengan pemutaran piringan dengan magnetik sedangkan SSD bekerja dengan flash memori yang diterima oleh controller. coba lihat gambar dibawah ini:

![picture 2](../images/1d3db48af3e728b3332580b8f2432ea546c2054487174139fe89823910627803.png)  


jelas terlihat bedanya. Untuk proses pencarian data sendiri pada SSD terdapat cache semua data tersisi dalam block-block memori.

berikut perbedaan yang jelas dari [tirto](https://tirto.id/membandingkan-kinerja-perangkat-penyimpan-data-ssd-vs-hdd-crSk).

![picture 3](../images/21eeb3bfbfa1313d0d37587504787651c53cbb46111570bebdd8ebdb4ca7db41.png)  

Saya sendiri tidak begitu jelas melihat data diatas. hal ini dikarenakan akan ada perbedaan yang cukup terasa dari beberapa brand yang ada dipasaran saat ini. Data diatas bisa dijadikan data acuan dasar untuk melihat jauh lebih dalam lagi tapi jangan 100% langsung berfikir bahwa itu adalah sepenuhnya yang terjadi.

## Jenis SSD

Ada dua jenis SSD yang ada dan paling sering dijumpai dipasaran saat ini.
### 1. mSATA (Mini-SATA)
Portnya biasa seperti hardisk yang ada di laptop biasa dijumpai. Seperti ini:
![picture 4](../images/0d06381dcd266e1b28cb6450987768c28824bb326af9c1052316d6be98f31260.png)  

### 2. M.2 
Portnya seperti PCI Express yang ada di Komputer PC
![picture 5](../images/91879b554c8644270ee6d4c278666c2cf0931d87aa3348d94e4cd14e5865740d.png)  

Coba deh lihat ini

<iframe width="560" height="315" src="https://www.youtube.com/embed/AoNxDe1a-X8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Yang saya gunakan

Okeh yang saya gunakan saat ini itu adalah nvme m.2 di komputer PC. Untuk performa tidak diragukan lagi karena saya hanya menunggu beberapa detik untuk menyalakan komputer. 

Terkadang komputernya kecepatan hidup dari pada posisi saya siap menggunakan komputer.

Untuk harganya sendiri saya lupa berapa detailnya tapi di bawah 500rb untuk "240gb".

sayangnya saya jadi sering lihat beginian

![picture 1](../images/2447b22756783bf6edf843af0e21e454609e18434274e7c605d903d9f32addeb.png)  

sakit mata merah mulu. karena harganya yang masih sangat mahal seharusnya tidak memaksakan untuk menggunakan tapi memang harus digunakan akhirnya jadinya merah semua.

Alternatif lain adalah menggunakan tambahan hardisk atau yang benarnya adalah Hard disk drive. 

ya saya punya 2TB hardisk external dan beberapa hardisk buangan laptop yang sudah rusak.

Faktanya jika menggunakan dua hal yang berbeda akan terjadi sebuah insiden 

> # Bottleneck

jika dulu problemnya hardisk selalu 100% sekarang malah beda lagi. Ketidak seimbangan ini terjadi karena yang satu memiliki kecapatan yang tinggi yang satunya lagi berjalan biasa aja. 

Pada akhirnya mobil lamborgini yang seharusnya bisa jalan diatas 100km/jam dalam beberapa detik eh ini malah ngikut mobil truk yang berjalan lambat didepannya.

Tidak hanya sampai disitu proses pemindahan data juga berlaku sama jika kita memindahkan data pada komputer yang menggunakan SSD tersebut ke Flashdrive.

okeh kasusnya gini.

Flashdrivenya udah USB 3.0, Komputernya udah pakai SSD M.2 tapi sayangnya yang dicolokin di port depan komputer yang support USB 2.0. Pada akhirnya semuanya berjalan di kecepatan USB 2.0 walaupun M.2 Bisa jauh lebih kencang.

Nah disinilah saya mencari jawaban apa yang seharusnya digunakan agar berjalan dengan baik dan seimbang.

![picture 6](../images/e3b9d2765e40713b5070839d56c4bb658c8d8897f8281a8975c1a39e7ef9c68b.png)  

Walaupun begitu ada beberapa hal yang membuat ini berbeda

![picture 7](../images/53c23aed29329fd6fefb7d6337fcf62d89d6a1f9fe9f54d1bfe5e11a3057d007.png)  

tapi sejauh ini thunderbolt 3 jauh lebih unggul.

Maka dari itu Infrastruktur yang digunakan seharusnya NVME M.2 itu di sandingkan dengan Thunderbolt3.

## Kesimpulan untuk problem warna merah

Ada uang, Ada teknologi.  
Gak ada uang, Jangan paksain kali.  
Pakai aja apa yang ada.  

sekian dulu semoga membingungkan.

Oh ya terakhir juga SSD itu ada banyak jenis cara kerja memorinya,  
diantaranya yang baru terlihat seperti dibawah ini

![picture 8](../images/e110e367d9f4384f378e70e37fe6a11b36e904c46f6c59e571366833af2e45a8.png)  

![picture 9](../images/b701c334eaafa5080b6116deba81a691f8f1e128acf8a035e9ddbe16169276d7.png)  


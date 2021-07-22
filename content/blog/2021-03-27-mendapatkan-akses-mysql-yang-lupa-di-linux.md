---
layout: post
title: Mendapatkan Akses MySQL yang Lupa Password di Linux
date: 2021-03-27 09:17
category: Linux
author: 
tags: [MySQL]
summary: 
---

Pertama sekali kita harus bisa akses ke user atau root yang bisa menjalankan service mysql. Ini penting sekali karena dengan bisa akses artinya kita bisa rubah start servicenya.

Teknikalnya seperti berikut:

1. Kita buka dulu editor favorit `micro mysql-hack` saya letakkan di home user atau `~`
2. Masukkan perintah berikut kedalamnya 
```sql
ALTER USER 'root'@'localhost' IDENTIFIED BY 'PassWordBaru';
ALTER USER 'namauser'@'localhost' IDENTIFIED BY 'PassWordBaru';
```
Usahakan masukkan kedua baris tersebut.
3. Matikan service mysql yang berjalan `sudo /etc/init.d/mysql stop` atau gunakan htop juga boleh dengan `kill`
4. Jalankan MySQL dengan beberapa baris SQL diatas dengan `sudo mysqld --init-file=/home/user/mysql-hack`
Tambahan: kalau di windows `cd "C:\Program Files\MySQL\MySQL Server 8.0\bin"` lalu `mysqld --init-file=C:\\mysql-hack.txt`
5. Masuk ke PHPMyAdmin nya `https://127.0.0.1/phpmyadmin` lalu masukkan username dan password diatas. 
6. Hapus aja file mysql-hack buat hilangkan jejak ya :v (tahap awal)

Oh ya untuk root defaultnya emang kosong sedangkan setingan bawaan phpmyadmin gak boleh masuk kalau password kosong itu yang biasanya jadi masalah. Solusinya dengan nambah user baru diatas atau replace password diatas untuk masuk akses ke PHPMyAdminnya dan gitu lah. 

Kamu bisa gunakan juga DBeaver untuk coba akses ke mysqlnya atau gak dari terminal juga bisa sih `mysql -u root -p` atau gunakan user lain selain root. 

Tambahan lagi:  
Jika ada ` Login without a password is forbidden by configuration (see AllowNoPassword)` itu artinya kamu bisa rubah di setingan PHPMyAdminnya dengan `vim /etc/phpmyadmin/config.inc.php` lalu buang komentar pada 
```// $cfg['Servers'][$i]['AllowNoPassword'] = TRUE;```
 terakhir jangan lupa simpan `:wq`

Oh ya ada lagi untuk di shell
```bash
echo "Setting MySQL password..."
echo "Whoami: " && whoami

# buat folder mysqld untuk yang baru install
mkdir /var/run/mysqld

# hapus file mysql.sock.lock
rm -rf /var/lib/mysql/mysql.sock.lock

# Jalankan mysqld dengan pengguna root dan membuat user 'johndoe' dengan md5 password 'johndoe'
# Grant all privileges
/usr/sbin/mysqld --user=root &
sleep 10
echo "CREATE USER 'johndoe'@'%' IDENTIFIED BY '6579e96f76baa00787a28653876c6127'; GRANT ALL PRIVILEGES ON *.* TO 'johndoe'@'%' IDENTIFIED BY '6579e96f76baa00787a28653876c6127'; GRANT ALL ON *.* TO root@'%' IDENTIFIED BY 'root' WITH GRANT OPTION; FLUSH PRIVILEGES;" | mysql --user=root
```


Sampai disini dulu selamat mencoba!

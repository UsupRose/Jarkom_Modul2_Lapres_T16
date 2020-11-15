# **LAPRES_MODUL 2_JARKOM** 
-----------------------------------
## **KELOMPOK T_16**
## Bagus Farhan Abdillah (05311840000016)
## I Gede Pradhana Indra Widnyana (05311840000031)

-----------------------------------
### Soal 1 :
### Membuat web utama dengan alamat ```http://semerut16.pw```.

- Membuat domain pada UML Malang sebagai DNS Server Master dengan cara ``nano /etc/bind/named.conf.local``.

![picture](https://cdn.discordapp.com/attachments/767120480167133215/777144444054667264/1.1_buat_domain_conf_local.JPG)

- Copykan file db.local pada path /etc/bind ke dalam folder /jarkom/semerut16.pw dengan cara ``cp /etc/bind/db.local /etc/bind/jarkom/jarkom2020.com``.

![picture](https://cdn.discordapp.com/attachments/767120480167133215/777146451162955836/1.2_cp_file.JPG)

- Kemudian buka file yang baru saja dicopy dan isikan seperti berikut.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777146892462718996/1.3_setting_semerut16.JPG)

- Setelah itu lakukan restart dengan cara ``service bind9 restart``. dan restart telah berhasil seperti gambar dibawah ini.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777148753953030174/1.4_restart_berhasil.JPG)

- Setting Domain nameserver dan arahkan menuju IP Malang agar domain yang kita buat dapat dikenali oleh client. Setting pada client gresik dengan cara ``nano /etc/resolv.conf``.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777150869338587136/1.5_setting_nameserver_gresik.JPG)

- Setting Domain nameserver dan arahkan menuju IP Malang agar domain yang kita buat dapat dikenali oleh client. Setting pada client sidoarjo dengan cara ``nano /etc/resolv.conf``.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777152490365124638/1.6_setting_nameserver_sidoarjo.JPG)

- Dan coba lakukan ping pada client gresik dan sidoarjo, dan jika berhasil akan seperti gambar pada dibawah ini.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777154437260902430/1.6_sukses_gresik.JPG)
<br />
![picture](https://cdn.discordapp.com/attachments/777146787336290354/777154449364746271/1.7_sukses_sidoarjo.JPG)

### Soal 2 :
### Membuat alias ```http://www.semerut16.pw```.

- Membuka file pada server malang dengan cara ``nano /etc/bind/jarkom/semerut16.pw`` dan tambahkan konfigurasi seperti dibawah ini.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777234383177383956/2.1_alias_semeru_setting_file.JPG)

- Kemudian lakukan testing dengan cara ``host -t CNAME http://www.semerut16.pw`` seperti gambar dibawah ini. Dan hasilnya seperti dibawah ini.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777234897772740618/2.2_sukses_ping_alias.JPG)

### Soal 3 :
### Membuat subdomain ```http://penanjakan.semerut16.pw``` yang diatur DNS-nya pada MALANG dan mengarah ke IP Server PROBOLINGGO.

- Membuka dan mengedit file pada server malang dengan cara ``nano /etc/bind/jarkom/semerut16.pw`` lalu tambahkan subdomain yang mengarah ke IP MALANG. Tambahkan konfigurasi seperti gambar dibawah.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777243038807883816/3.1_subdomain_penanjakan.JPG)

- Kemudian lakukan restart service bind dengan perintah ``service bind9 restart``. Setelah itu lakukan ping ke subdomain dengan perintah ``ping penanjakan.semerut16.pw`` atau dengan ``host -t A penanjakan.semerut16.pw``. Dan hasil dari perintah tersebut seperti gambar dibawah.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777249397385068615/3.2_sukses_ping_subdomain.JPG)

### Soal 4 :
### Membuat reverse domain untuk domain utama.

- Buka dan edit file /etc/bind/named.conf.local pada MALANG dengan perintah ``nano /etc/bind/named.conf.local``. 

- Lalu tambahkan konfigurasi seperti ini. 
``` zone "77.151.10.in-addr.arpa" {
    type master;
    file "/etc/bind/jarkom/77.151.10.in-addr.arpa";
 }; 
 ```
 
![picture](https://cdn.discordapp.com/attachments/777146787336290354/777260448994689024/4.1_setting_conf_local_malang.JPG)

- Kemudian copykan file db.local pada path /etc/bind/jarkom/77.151.10.in-addr.arpa dengan perintah ``nano /etc/bind/jarkom/77.151.10.in-addr.arpa`` dan edit sesuai gambar dibawah.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777262191966552105/4.2_setting_in_addr_arpa.JPG)

- Kemudian lakukan restart dengan perintah ``service bind9 restart``. Setelah itu pastikan nameserver telah dikembalikan seperti settingan awal seperti pada gambar dibawah ini.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777405777601495040/4.3_mengembalikan_dns.JPG)

- Untuk mengecek apakah konfigurasi sudah benar atau belum, lakukan install package dnsutils perintah berikut pada client GRESIK seperti pada gambar dibawah ini.
```
apt-get update
apt-get install dnsutils
```

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777407674902904842/4.4_sukses_update.JPG)
<br />
![picture](https://cdn.discordapp.com/attachments/777146787336290354/777407694126055464/4.5_sukses_dnsutil.JPG)

- Kemudian kembalikan nameserver agar tersambung dengan MALANG dengan perintah ``host -t PTR "IP MALANG"`` seperti gambar dibawah ini.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777408531934478336/4.6_sukses_pointing_host_ptr.JPG)

### Soal 5 :
### Membuat DNS Server Slave pada MOJOKERTO.

- Membuka dan mengedit file pada server malang dengan perintah ``nano /etc/bind/named.conf.local``. dan sesuaikan dengan syntax dan gambar dibawah ini dibawah ini.
```
zone "semerut16.pw" {
    type master;
    notify yes;
    also-notify { 10.151.77.179; }; // Masukkan IP MOJOKERTO
    allow-transfer { 10.151.77.179; }; // Masukkan IP MOJOKERTO
    file "/etc/bind/jarkom/semerut16.pw";
};
```

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777411258961625088/5.1_setting_malang_slave.JPG)

- Kemudian Buka MOJOKERTO dan update package lists dengan menjalankan command ``apt-get update`` Setelah melakukan update silahkan install aplikasi bind9 pada MOJOKERTO dengan perintah ``apt-get install bind9 -y`` seperti gambar dibawah ini.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777412013039157279/5.2_install_bind9_mojokerto.JPG)

- Kemudian buka file /etc/bind/named.conf.local pada MOJOKERTO dengan perintah ``nano /etc/bind/named.conf.local``, dan tambahkan syntax seperti dibawah ini.
```
zone "semerut16.pw" {
    type slave;
    masters { 10.151.77.178; }; // Masukan IP MALANG 
    file "/var/lib/bind/semerut16.pw";
};
```

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777413040080945162/5.3_setting_slave_mojokerto.JPG)

- Setelah proses diatas selesai jangan lupan untuk melakukan restart dengan perintah ``service bind9 restart``

- Pada server MALANG silahkan matikan service bind9 dengan command ``service bind9 stop``. Pastikan pengaturan nameserver mengarah ke IP MALANG dan IP MOJOKERTO pada client gresik.
- Lakukan ping ke ``semerut16.pw`` pada client GRESIK. Jika ping berhasil maka konfigurasi DNS slave telah berhasil.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777423567214084096/5.4_sukses_slave.JPG)

### Soal 6 :
### Membuat subdomain dengan alamat http://gunung.semerut16.pw yang didelegasikan pada server MOJOKERTO dan mengarah ke IP Server PROBOLINGGO.

- Buka dan edit file /etc/bind/jarkom/semerut16.pw dengan perintah ``nano /etc/bind/jarkom/semerut16.pw`` lalu tambahkan subdomain seperti pada gambar dibawah ini.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777424654867890176/6.1_setting_subdomain_gunung.JPG)

- 










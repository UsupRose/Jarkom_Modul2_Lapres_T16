# **LAPRES_MODUL 2_JARKOM** 
-----------------------------------
## **KELOMPOK T_16**
## Bagus Farhan Abdillah (05311840000016)
## I Gede Pradhana Indra Widnyana (05311840000031)

-----------------------------------
### Soal 1 :
### Membuat web utama dengan alamat ```http://semerut16.pw```.

>Membuat domain pada UML Malang sebagai DNS Server Master dengan cara ``nano /etc/bind/named.conf.local``.

![picture](https://cdn.discordapp.com/attachments/767120480167133215/777144444054667264/1.1_buat_domain_conf_local.JPG)

>Copykan file db.local pada path /etc/bind ke dalam folder /jarkom/semerut16.pw dengan cara ``cp /etc/bind/db.local /etc/bind/jarkom/jarkom2020.com``.

![picture](https://cdn.discordapp.com/attachments/767120480167133215/777146451162955836/1.2_cp_file.JPG)

>Kemudian buka file yang baru saja dicopy dan isikan seperti berikut.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777146892462718996/1.3_setting_semerut16.JPG)

>Setelah itu lakukan restart dengan cara ``service bind9 restart``. dan restart telah berhasil seperti gambar dibawah ini.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777148753953030174/1.4_restart_berhasil.JPG)

>Setting Domain nameserver dan arahkan menuju IP Malang agar domain yang kita buat dapat dikenali oleh client. Setting pada client gresik dengan cara ``nano /etc/resolv.conf``.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777150869338587136/1.5_setting_nameserver_gresik.JPG)

>Setting Domain nameserver dan arahkan menuju IP Malang agar domain yang kita buat dapat dikenali oleh client. Setting pada client sidoarjo dengan cara ``nano /etc/resolv.conf``.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777152490365124638/1.6_setting_nameserver_sidoarjo.JPG)

>Dan coba lakukan ping pada client gresik dan sidoarjo, dan jika berhasil akan seperti gambar pada dibawah ini.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777154437260902430/1.6_sukses_gresik.JPG)
<br />
![picture](https://cdn.discordapp.com/attachments/777146787336290354/777154449364746271/1.7_sukses_sidoarjo.JPG)

### Soal 2 :
### Membuat alias ```http://www.semerut16.pw```.

>Membuka file pada server malang dengan cara ``nano /etc/bind/jarkom/semerut16.pw`` dan tambahkan konfigurasi seperti dibawah ini.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777234383177383956/2.1_alias_semeru_setting_file.JPG)

>Kemudian lakukan testing dengan cara ``host -t CNAME http://www.semerut16.pw`` seperti gambar dibawah ini. Dan hasilnya seperti dibawah ini.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777234897772740618/2.2_sukses_ping_alias.JPG)

### Soal 3 :
### Membuat subdomain ```http://penanjakan.semerut16.pw``` yang diatur DNS-nya pada MALANG dan mengarah ke IP Server PROBOLINGGO.

>Membuka dan mengedit file pada server malang dengan cara ``nano /etc/bind/jarkom/jarkom2020.com`` lalu tambahkan subdomain yang mengarah ke IP MALANG. Tambahkan konfigurasi seperti gambar dibawah.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777243038807883816/3.1_subdomain_penanjakan.JPG)

>Kemudian lakukan restart service bind dengan perintah ``restart service bind9``. Setelah itu lakukan ping ke subdomain dengan perintah ``ping penanjakan.semerut16.pw`` atau dengan ``host -t A penanjakan.semerut16.pw``. Dan hasil dari perintah tersebut seperti gambar dibawah.

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777249397385068615/3.2_sukses_ping_subdomain.JPG)

### Soal 4 :
### Membuat reverse domain untuk domain utama.

>Buka dan edit file /etc/bind/named.conf.local pada MALANG dengan perintah ``nano /etc/bind/named.conf.local`` 
>Lalu tambahkan konfigurasi seperti ini.










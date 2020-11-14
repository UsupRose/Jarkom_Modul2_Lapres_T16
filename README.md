# **LAPRES_MODUL 2_JARKOM** 
-----------------------------------
## **KELOMPOK T_16**
## Bagus Farhan Abdillah (05311840000016)
## I Gede Pradhana Indra Widnyana (05311840000031)

-----------------------------------
### Soal 1 :
### Membuat web utama dengan alamat ```http://semerut16.pw```

>Membuat domain pada UML Malang sebagai DNS Server Master dengan cara ``nano /etc/bind/named.conf.local``

![picture](https://cdn.discordapp.com/attachments/767120480167133215/777144444054667264/1.1_buat_domain_conf_local.JPG)

>Copykan file db.local pada path /etc/bind ke dalam folder /jarkom/semerut16.pw dengan cara ``cp /etc/bind/db.local /etc/bind/jarkom/jarkom2020.com``

![picture](https://cdn.discordapp.com/attachments/767120480167133215/777146451162955836/1.2_cp_file.JPG)

>Kemudian buka file yang baru saja dicopy dan isikan seperti berikut

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777146892462718996/1.3_setting_semerut16.JPG)

>Setelah itu lakukan restart dengan cara ``service bind9 restart``. dan restart telah berhasil seperti gambar dibawah ini

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777148753953030174/1.4_restart_berhasil.JPG)

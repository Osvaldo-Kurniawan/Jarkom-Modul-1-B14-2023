# Jarkom-Modul-1-B14-2023

## Kontributor

| Nama Kontributor | NRP |
|------------------|-----|
| Muhammad Arkan Karindra Darvesh | 5025211236 |
| Gabrielle Immanuel Osvaldo Kurniawan | 5025211135 |

# Soal 1
User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah mengunggah suatu file.

  a. Berapakah sequence number (raw) pada packet yang menunjukkan aktivitas tersebut? 
  
  b. Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut? 
  
  c. Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?
  
  d. Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?

## Jawab

Untuk mencari paket-paket yang menunjukkan aktivitas pengungahan file terlebih dahulu dicari paket dengan tanda pengungahan file dengan melihat perintah yang dikirimkan dalam sesi FTP, seperti 'STOR'. Filter yang digunakan dalam kasus ini adalah 
```
ftp contains"STOR"
```

Dalam file pcap yang diperoleh terdapat 1 file yang memiliki kode 'STOR' sebagai berikut :

### Paket aktivitas user  
<img width="732" alt="image" src="https://github.com/Osvaldo-Kurniawan/Jarkom-Modul-1-B14-2023/assets/108170210/ca6e6265-df65-48e7-a311-e07cd431b6bb">
  
Dari paket yang berdekatan juga didapatkan paket yang merespon pengungahan file tersebut. Kemudian untuk mencari sequence number (raw) serta acknowledge number (raw) dapat dilihat pada bagian transmision control protocol dengan mengklik file paket yang dimaksud :

### Paket pengungahan
<img width="717" alt="image" src="https://github.com/Osvaldo-Kurniawan/Jarkom-Modul-1-B14-2023/assets/108170210/3a22e7d3-14dc-45b4-812d-115b209d057a">

### Paket response
<img width="724" alt="image" src="https://github.com/Osvaldo-Kurniawan/Jarkom-Modul-1-B14-2023/assets/108170210/dbaa9c72-b887-4617-a6c1-3c2540194d2a">

# Soal 2
Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!

## Jawab

Untuk mencari server maka harus dilakukan pengecekkan pada protokol https, pada wireshark dapat menggunakan fitur follow http dengan terlebih dahulu mencari komunikasi client-server yang berkaitan. Dalam kasus ini digunakan filter
```
http contains "Praktikum"
```
### Hasil pencarian
<img width="485" alt="image" src="https://github.com/Osvaldo-Kurniawan/Jarkom-Modul-1-B14-2023/assets/108170210/9d7a8aa2-a3fa-4b07-84c5-ae2b8846fa93">

# Soal 3
Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:

a. Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702?

b. Hitung jumlah dari ip tersebut

c. Protokol layer transport apa yang digunakan?

## Jawab

# Soal 4
Berapa nilai checksum yang didapat dari header pada paket nomor 130?

## Jawab

# Soal 5
Elshe menemukan suatu file packet capture yang menarik. Bantulah Elshe untuk menganalisis file packet capture tersebut.

a. Berapa banyak packet yang berhasil di capture dari file pcap tersebut?

b. Port berapakah pada server yang digunakan untuk service SMTP?

c. Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP?

## Jawab
SMTP adalah protokol pengiriman email. Konten dari email ini diperlukan untuk mengakses protokol nc dari soal untuk melihat isi email maka dapat digunakan filter
'''
smtp
'''
Dari filter display akan ditampilkan keseluruhan protokol tersebut kemudian dapat dilakukan follow untuk mengakses konten email sebagai berikut :

<img width="472" alt="image" src="https://github.com/Osvaldo-Kurniawan/Jarkom-Modul-1-B14-2023/assets/108170210/c8a79663-fe0d-4d98-8d2b-aec04854a636">

Kode dari email tersebut akan didecode dan passwordnya adalah ```5implePas5word```

Jumlah paket dapat dilihat dari nomer paket terakhir yaitu 60 paket atau dapat dilihat pada bagian kanan bawah wireshark

<img width="442" alt="image" src="https://github.com/Osvaldo-Kurniawan/Jarkom-Modul-1-B14-2023/assets/108170210/150cb725-0d80-4c1e-850a-fbef36d3f2cc">

Sedangkan port untuk smpt deafult adalah ```port 25``` dan dapat dipastikan dengan membuka salah satu paket smpt yaitu :

<img width="604" alt="image" src="https://github.com/Osvaldo-Kurniawan/Jarkom-Modul-1-B14-2023/assets/108170210/8293dfec-3bc1-4db1-8f8d-27ae097ce744">

IP publik adalah ip non private. Adapun range ip publik dan private sebagai berikut :

<img width="487" alt="image" src="https://github.com/Osvaldo-Kurniawan/Jarkom-Modul-1-B14-2023/assets/108170210/0cf146da-4fb5-42f9-abcc-bde62d12331a">

Satu satunya ip publik yang ada adalah ```74.53.140.153```

# Soal 6
Seorang anak bernama Udin Berteman dengan Slamet yang merupakan seorang penggemar film detektif. sebagai Teman yang baik, Ia selalu mengajak slamet untuk bermain valorant bersama. suatu malam, Terjadi sebuah hal yang tak terduga. ketika Udin mereka membuka game tersebut, laptop udin menunjukkan sebuah field text dan Sebuah kode Invalid bertuliskan "server SOURCE ADDRESS 7812 is invalid". ketika ditelusuri di google, hasil pencarian hanya menampilkan a1 e5 u21. jiwa detektif slamet pun bergejolak. bantulah udin dan slamet untuk menemukan solusi kode error tersebut.

## Jawab
Dari soal terdapat clue "server SOURCE ADDRESS 7812 is invalid", maka kita gunakan filter untuk mencari paket no 7812 sebagai berikut
```
frame.number == 7821
```

### Hasil filter
<img width="1280" alt="image" src="https://github.com/Osvaldo-Kurniawan/Jarkom-Modul-1-B14-2023/assets/108170210/b055dc98-65e4-401e-9a3a-86eec2612d37">

Didapat ```ip 104.18.14.101``` dari ip ini pada soal ada clue untuk melakukan subtitusi dengan abjad, clue tersebut adalah "a1 e5 u21" yaitu angka mewakili urutan abjad

10 - 4 - 18 - 14 - 10 - 1 -> jdrnja

## Kesulitan
Pada soal ini kami tidak memiliki clue apapun sehingga tidak dapat mengerti kebutuhan filter yang dapat dipakai, sehingga saat akhirpun tidak dapat solve soal ini

# Soal 7
Berapa jumlah packet yang menuju IP 184.87.193.88?

## Jawab
Untuk mendapatkan hasil paket yang dimaksud dapat digunakan filter sebagai berikut 
```
ip.dst == 184.87.193.88
```

### Hasil filter
<img width="730" alt="image" src="https://github.com/Osvaldo-Kurniawan/Jarkom-Modul-1-B14-2023/assets/108170210/ee051103-78a4-439b-b71e-5c8bf994ba04">

Ketika dihitung diperoleh 6 buah paket jumlahnya 

# Soal 8
Berikan kueri filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80! (Jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad)

## Jawab

# Soal 9
Berikan kueri filter sehingga wireshark hanya mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34!

## Jawab
Solusi filter yang dapat digunakan adalah
```
ip.src == 10.51.40.1 && ip.dst == 10.39.55.34
```

Hasil filter pada query ini sayangnya tidak menunjukkan adanya paket yang dimaksud pada soal no 6-9

# Soal 10
Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet

## Jawab
Telnet adalah protokol yang tidak memiliki enkripsi sehingga data dapat langsung dicek pada paket yang dikomunikasikan. Filter yang dapat digunakan adalah
```
telnet contains "Password"
```

### Hasil filter
<img width="1280" alt="image" src="https://github.com/Osvaldo-Kurniawan/Jarkom-Modul-1-B14-2023/assets/108170210/f03fb0fe-7dc7-4c6d-901a-d7bc370b4368">

Paket yang ditemukan dapat dilihat datanya menggunakan fitur follow tcp khususnya data paket dari client di wireshark dengan hasil sebagai berikut :

<img width="848" alt="image" src="https://github.com/Osvaldo-Kurniawan/Jarkom-Modul-1-B14-2023/assets/108170210/a7f611dc-7596-4cba-a0de-7d37397b0e36">


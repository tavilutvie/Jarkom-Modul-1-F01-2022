# Jarkom-Modul-1-F01-2022

## Anggota Kelompok

| No.  | NRP            | NAMA                       |
| ---  | -------------- | -------------------------- |
| 1.   | 5025201213     | Eldenabih Tavirazin Lutvie |
| 2.   | 5025201030     | Mohammad Nouval Bachrezi   |
| 3.   | 05111940000220 | Marsa Aushaf Rafi          |

## Soal 1-2
1. Sebutkan web server yang digunakan pada "monta.if.its.ac.id"! <br>
2. Ishaq sedang bingung mencari topik ta untuk semester ini , lalu ia datang ke website monta dan menemukan detail topik pada website “monta.if.its.ac.id” , judul TA apa yang dibuka oleh ishaq ? <br>

## No 1
Filter http dengan host 'monta.if.its.ac.id'.
```
http.host == monta.if.its.ac.id
```
![1 1111111](https://user-images.githubusercontent.com/85897222/192103949-dd6934be-259b-40f5-a51e-abcf60a8aefe.png)

Follow tcp stream untuk melihat detail.
![1 2222222](https://user-images.githubusercontent.com/85897222/192103959-2c2c4f6a-185c-4d61-95a5-0fe3ea372313.png)

## No 2
Filter http yang mengandung 'detailTopik'.
```
http.request.uri contains "detailTopik"
```
![1 333](https://user-images.githubusercontent.com/85897222/192103966-5273c778-d517-48a1-920d-87ab624233ca.png)

Export dan buka html 194, disana kita akan menemukan judul topiknya.
![1 4444444444](https://user-images.githubusercontent.com/85897222/192103972-b911dbbb-3dc5-43e2-b50c-2dfa09df875e.png)


## Soal 3-7
3. Filter sehingga wireshark hanya menampilkan paket yang menuju port 80! <br>
4. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 21! <br>
5. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 443! <br>
6. Filter sehingga wireshark hanya menampilkan paket yang menuju ke lipi.go.id ! <br>
7. Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian! <br>

## No 3
Filter udp dan tcp dengan destination port 80
```
udp.dstport == 80 || tcp.dstport == 80
```
![image](https://user-images.githubusercontent.com/85897222/192104005-4262005c-049f-4188-a356-4b89fdc90f64.png)

## No 4
Filter udp dan tcp dengan source port 21
```
udp.srcport == 21 || tcp.srcport == 21
```
![image](https://user-images.githubusercontent.com/85897222/192104024-229a7c3a-139e-4d46-b44b-64cc3939b1ff.png)

## No 5
Filter udp dan tcp dengan source port 443
```
udp.srcport == 443 || tcp.srcport == 443
```
![image](https://user-images.githubusercontent.com/85897222/192104036-c8a7df64-c572-436a-a6aa-b85c26045820.png)

## No 6
Filter udp dan tcp yang mengandung lipi.go.id
```
udp contains lipi.go.id || tcp contains lipi.go.id
```
![image](https://user-images.githubusercontent.com/85897222/192104040-f001d84d-1456-4095-ae15-a4fce899e583.png)

## No 7
Filter ip dengan source ip sendiri
```
ip.src == 125.167.32.175
```

## Soal 8-10
Di sebuah planet bernama Viltrumite, terdapat Kementerian Komunikasi dan Informatika yang baru saja menetapkan kebijakan baru. Dalam kebijakan baru tersebut, pemerintah dapat mengakses data pribadi masyarakat secara bebas jika memang dibutuhkan, baik dengan maupun tanpa persetujuan pihak yang bersangkutan. Sebagai mahasiswa yang sedang melaksanakan program magang di kementerian tersebut, kalian mendapat tugas berupa penyadapan percakapan mahasiswa yang diduga melakukan tindak kecurangan dalam kegiatan Praktikum Komunikasi Data dan Jaringan Komputer 2022. Selain itu, terdapat sebuah password rahasia (flag) yang diduga merupakan milik sebuah organisasi bawah tanah yang selama ini tidak sejalan dengan pemerintahan Planet Viltrumite. Tunggu apa lagi, segera kerjakan tugas magang tersebut agar kalian bisa mendapatkan pujian serta kenaikan jabatan di kementerian tersebut!
<br>
8. Telusuri aliran paket dalam file .pcap yang diberikan, cari informasi berguna berupa percakapan antara dua mahasiswa terkait tindakan kecurangan pada kegiatan praktikum. Percakapan tersebut dilaporkan menggunakan protokol jaringan dengan tingkat keandalan yang tinggi dalam pertukaran datanya sehingga kalian perlu menerapkan filter dengan protokol yang tersebut.
<br>
9. Terdapat laporan adanya pertukaran file yang dilakukan oleh kedua mahasiswa dalam percakapan yang diperoleh, carilah file yang dimaksud! Untuk memudahkan laporan kepada atasan, beri nama file yang ditemukan dengan format [nama_kelompok].des3 dan simpan output file dengan nama “flag.txt”.
<br>
10. Temukan password rahasia (flag) dari organisasi bawah tanah yang disebutkan di atas!


## No 8
Filter tcp yang mengandung kata "soal".
```
tcp contains soal
```
<br>

![1111111](https://user-images.githubusercontent.com/85897222/192097628-da644849-9406-428a-8d5f-c5dedfb8eb76.png)

<br>
Untuk mendapatkan percakapan, langkah yang harus dikerjakan adalah follow tcp stream.
<br>

![2222222222222](https://user-images.githubusercontent.com/85897222/192097643-718b9b19-4c99-4c25-868e-e521cad17a78.png)

<br>
Kata-kata kunci yang terkandung pada percakapan tersebut:
openssl, des3, file: salt, port: 9002, clue password: karakter anime kembar lima

## No 9
Filter tcp dengan port 9002
```
tcp.srcport == 9002
```
<br>

![33333333333](https://user-images.githubusercontent.com/85897222/192097650-3ec1f50d-2f74-45f0-9262-de43da4b7a92.png)

<br>
Follow tcp stream
<br>

![4444444444](https://user-images.githubusercontent.com/85897222/192097656-68039619-6bb6-4941-8f90-2c53b5d439f4.png)

<br>
File di download dan di ekstrak
```
openssl des3 -d -salt -in F01.des3 -out flag.txt -k nakano
```
<br>

![5555555555555](https://user-images.githubusercontent.com/85897222/192097660-04c7e3ea-d0d9-40d0-8f91-f300603d4af2.png)


## No 10
Buka file flag.txt
<br>
![image](https://user-images.githubusercontent.com/85897222/192097063-817288fa-a75a-4785-ab93-01e5467c17da.png)
<br>
Jawaban: JaRkOm2022{8uK4N_CtF_k0k_h3h3h3}

## Kendala
Susah menemukan kata kunci untuk password untuk mendecrypt
<br>
Susah menemukan cara mendecrypt menggunakan openssl

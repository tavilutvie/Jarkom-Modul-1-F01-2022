# Jarkom-Modul-1-F01-2022

## Anggota Kelompok

| No.  | NRP        | NAMA                       |
| ---  | ---------- | -------------------------- |
| 1.   | 5025201213 | Eldenabih Tavirazin Lutvie |
| 2.   |  |      |
| 3.   |  |      |

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
![image](https://user-images.githubusercontent.com/85897222/192097359-2b4ceea8-310c-422d-b0a7-2f07543370f1.png)

<br>
Untuk mendapatkan percakapan, langkah yang harus dikerjakan adalah follow tcp stream.
<br>
![image](https://user-images.githubusercontent.com/85897222/192097370-aac6ca82-3069-445a-b914-1d941b57fe3c.png)

<br>
Kata-kata kunci yang terkandung pada percakapan tersebut:
openssl, des3, file: salt, port: 9002, clue password: karakter anime kembar lima

## No 9
Filter tcp dengan port 9002
```
tcp.srcport == 9002
```
<br>
![image](https://user-images.githubusercontent.com/85897222/192097408-b434f9e9-ec8e-456a-8cf4-7f7a6454b917.png)
<br>
Follow tcp stream
<br>
![image](https://user-images.githubusercontent.com/85897222/192097439-05760327-554c-47a1-92c0-9320db58d964.png)

<br>
File di download dan di ekstrak
```
openssl des3 -d -salt -in F01.des3 -out flag.txt -k nakano
```
<br>
![image](https://user-images.githubusercontent.com/85897222/192097470-aa75bf4b-7925-46c4-99a1-ae9ddd1816e9.png)


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

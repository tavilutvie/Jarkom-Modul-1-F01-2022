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
<br>

## 8
Filter tcp yang mengandung kata "soal".
```
tcp contains soal
```
![image](https://user-images.githubusercontent.com/85897222/192096472-19d0743c-0462-46dd-a8d0-113bab6bfe74.png)
Untuk mendapatkan percakapan, langkah yang harus dikerjakan adalah follow tcp stream.
![image](https://user-images.githubusercontent.com/85897222/192096561-8f884e58-7b86-4713-a41c-42ef79ff1f88.png)

Kata-kata kunci yang terkandung pada percakapan tersebut:
openssl, des3, file: salt, port: 9002, clue password: karakter anime kembar lima

## 9
Filter tcp dengan port 9002
```
tcp.srcport == 9002
```
![image](https://user-images.githubusercontent.com/85897222/192096793-ff1bf818-df8f-4f89-abfc-6033ac68d3b3.png)

Follow tcp stream
![image](https://user-images.githubusercontent.com/85897222/192096849-78c71434-0768-47a6-b761-6b94ea577cb5.png)

File di download dan di ekstrak
```
openssl des3 -d -salt -in F01.des3 -out flag.txt -k nakano
```
![image](https://user-images.githubusercontent.com/85897222/192096940-015e8a0a-8f4e-4971-a734-fad30a604310.png)

## 10
Buka file flag.txt
![image](https://user-images.githubusercontent.com/85897222/192097063-817288fa-a75a-4785-ab93-01e5467c17da.png)
Jawaban: JaRkOm2022{8uK4N_CtF_k0k_h3h3h3}

## Kendala
Susah menemukan kata kunci untuk password untuk mendecrypt
Susah menemukan cara mendecrypt menggunakan openssl

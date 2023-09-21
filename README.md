# Jarkom-Modul-1-IT05-2023
Yohannes Hasahatan Tua Alexandro - 5027211022

Arkan Hendri Abdul Ghani Burhan - 5027211026

## Soal 1
User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah mengunggah suatu file.

a. Berapakah sequence number (raw) pada packet yang menunjukkan aktivitas tersebut? 

b. Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut? 

c. Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?

d. Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?

## Jawaban Soal 1
Gunakan kueri filter pada wireshark guna untuk hanya menampilkan aktivitas user ketika menggunakan protokal FTP
```
ftp || ftp-data
```
Carilah packet yang berisikan request STOR yang menandakan pengunggahan file yang dimaksud pada soal yaitu pengunggahan file zip. Untuk menjawab pertanyaan a dan b, carilah sequence number (raw) dan acknowledge number (raw) pada TCP, seperti gambar berikut.

Paket Request STOR

![soal1_STOR](https://github.com/WatShitTooYaa/Jarkom-Modul-1-IT05-2023/assets/50076171/a02ac908-7711-44e6-a233-8618a61b4d57)

TCP Pada Paket Request STOR

![soal1_TCP-STOR](https://github.com/WatShitTooYaa/Jarkom-Modul-1-IT05-2023/assets/50076171/023bb1ab-fbbc-4105-99cd-15c9f6f07c4f)


Kemudian, carilah response atas pengunggahan file yaitu paket atas response 150 binary yang berisikan pengunggahan file zip. Untuk menjawab pertanyaan c dan d, carilah sequence number (raw) dan acknowledge number (raw) pada TCP, seperti gambar berikut.

![soal1_TCP-150Binary](https://github.com/WatShitTooYaa/Jarkom-Modul-1-IT05-2023/assets/50076171/5d27c498-660a-49e9-8b8d-d19b4c5642ae)


Setelah mendapatkan jawaban untuk seluruh pertanyaan, sambungkan ke nc pada soal itu 
```
nc 10.21.78.111 12345
```

Maka, akan mendapatkan flag seperti gambar berikut.

![soal1_Flag](https://github.com/WatShitTooYaa/Jarkom-Modul-1-IT05-2023/assets/50076171/5406f6f1-1604-4a7d-bfb5-9ee0c5ab789b)

## Soal 2

## Jawaban Soal 2

## Soal 3
Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:

a. Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702?

b. Protokol layer transport apa yang digunakan?


## Jawaban Soal 3
Gunakan kueri filter pada wireshark guna untuk hanya menampilkan paket yang tercapture dengan IP source maupun destination address adalah  239.255.255.250 dengan port 3702
```
ip.addr == 239.255.255.250 and udp.port == 3702
```
Lalu hitung paket yang tersedia, atau dapat melihat pada pojok kanan bawah yang menandakan paket yang ditampilkan sebanyak 21 paket untuk menjawab pertanyaan a, seperti gambar berikut.
![soal3_stream](https://github.com/WatShitTooYaa/Jarkom-Modul-1-IT05-2023/assets/50076171/81d71460-8304-4251-9091-e9798db98912)


Pada gambar diatas, dapat dilihat juga protocol yang digunakan adalah UDP untuk menjawab pertanyaan b.

Setelah mendapatkan jawaban untuk seluruh pertanyaan, sambungkan ke nc pada soal itu 
```
nc 10.21.78.111 13590
```

Maka, akan mendapatkan flag seperti gambar berikut.

![soal1_Flag](https://github.com/WatShitTooYaa/Jarkom-Modul-1-IT05-2023/assets/50076171/ad818b73-e070-46ab-b498-a9af87a0407c)

## Soal 4

## Jawaban Soal 4

## Soal 5 (Revisi)
Elshe menemukan suatu file packet capture yang menarik. Bantulah Elshe untuk menganalisis file packet capture tersebut.

a. Berapa banyak packet yang berhasil di capture dari file pcap tersebut?

b. Port berapakah pada server yang digunakan untuk service SMTP?

c. Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP?


## Jawaban Soal 5 (Revisi)
Gunakan tools follow TCP stream pada wireshark untuk mendapatkan password untuk membuka folder yang dikunci. Kemudian didapatkan password yang harus dilakukan decode terlebih dahulu dengan menggunakan Base64 yaitu
```
NWltcGxlUGFzNXdvcmQ=
```
Seperti gambar berikut:

![soal5_tcpStream](https://github.com/WatShitTooYaa/Jarkom-Modul-1-IT05-2023/assets/50076171/19963f9e-3306-4f64-816c-5b4ce821988f)


Kemudian dilakukan decode menggunakan base64 yang akan menghasilkan password
```
5implePas5word
```
Seperti gambar berikut:

![soal5_decode](https://github.com/WatShitTooYaa/Jarkom-Modul-1-IT05-2023/assets/50076171/92ebaf55-6266-4155-abfc-2f8522f6c591)



Kemudian, buka folder yang dikunci dan inputkan password tersebut. Maka akan mendapatkan file .txt yang berisikan nc berikut
```
nc 10.21.78.111 13590
```
Seperti gambar berikut: 

![soal5_getnc](https://github.com/WatShitTooYaa/Jarkom-Modul-1-IT05-2023/assets/50076171/ab9f63b0-02a7-48f3-a776-e89d28e02f21)


Amati paket pada wireshark, jumlah paket yang tersedia sebanyak 60 paket yang dapat dilihat pada pojok kanan bawah untuk menjawab pertanyaan a. Kemudian, lihatlah TCP pada protocol SMTP yang berisikan port yaitu port 25 untuk menjawab pertanyaan b. Dan, dari seluruh IP, terdapat IP publik yaitu 74.53.140.153 untuk menjawab pertanyaan c. Dapat dilihat dari gambar berikut:

![soal5_portSMTP](https://github.com/WatShitTooYaa/Jarkom-Modul-1-IT05-2023/assets/50076171/0ca8db86-9344-45f6-b5ce-6047b52f2b53)


Setelah menyambukan nc yang telah didapatkan dan menjawab seluruh pertanyaan, akan mendapatkan flag seperti gambar berikut.

![soal5_flag](https://github.com/WatShitTooYaa/Jarkom-Modul-1-IT05-2023/assets/50076171/8deade6d-2988-48f2-a358-636170367033)

## Soal 6 (Revisi)

## Jawaban Soal 6 (Revisi)

## Soal 7
Berapa jumlah packet yang menuju IP 184.87.193.88?


## Jawaban Soal 7
Gunakan kueri filter pada wireshark guna untuk hanya menampilkan paket yang menuju IP 184.87.193.88
```
ip.dst == 184.87.193.88
```
Kemudian hitunglah paket yang tersedia atau dapat dilihat pada bagian kanan bawah yang menunjukan paket yang tersedia yaitu sebanyak 6 paket, seperti gambar berikut:

![soal7_paket](https://github.com/WatShitTooYaa/Jarkom-Modul-1-IT05-2023/assets/50076171/ad7949d1-cd2b-43a8-abaf-76159c12b578)


Kemudian, sambungkan nc pada soal yaitu 
```
nc 10.21.78.111 6565
```

Maka, akan mendapatkan flag seperti gambar berikut.

![soal7_flag](https://github.com/WatShitTooYaa/Jarkom-Modul-1-IT05-2023/assets/50076171/49c3c30b-231a-4705-aa95-85ef52ae9254)

## Soal 8

## Jawaban Soal 8

## Soal 9
Berikan kueri filter sehingga wireshark hanya mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34!


## Jawaban Soal 9
Gunakan kueri filter pada wireshark guna untuk hanya menampilkan  paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34
```
ip.src == 10.51.40.1 && ip.dst != 10.39.55.34
```

Kemudian, sambungkan nc pada soal yaitu 
```
nc 10.21.78.111 13590
```

Maka, akan mendapatkan flag seperti gambar berikut.

![soal9_flag](https://github.com/WatShitTooYaa/Jarkom-Modul-1-IT05-2023/assets/50076171/7336896b-d597-4e3a-b4dd-9dab3ad8036e)

## Soal 10

## Jawaban Soal 10

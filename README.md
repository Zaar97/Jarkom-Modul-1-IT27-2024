# Jarkom-Modul-1-IT27-2024

| Nama | NRP |
| ---------------------- | ---------- |
| Azzahra Sekar Rahmadina | 5027221035 |
| Zulfa Hafizh Kusuma | 5027221038 |

## List of Contents
- [Soal 1](#soal-1) 
- [Soal 2](#soal-2)
- [Soal 3](#soal-3)
- [Soal 4](#soal-4)
- [Soal 5](#soal-5)
- [Soal 6](#soal-6)
- [Soal 7](#soal-7)
- [Soal 8](#soal-8)
- [Soal 9](#soal-9)


## Soal 1
**ATM or ATP or FTP ?**

> Pradityo mencoba mengembangkan server ftp, tetapi seseorang mencoba melakukan bruteforce login, bisakah Anda menganalisis apa yang terjadi?

1. Gunakan filter ftp.response.code == 230 untuk mendapatkan paket yang mengandung paket response "Response: 230 Login successful"

![image](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/assets/128958228/f4d4cd40-b0e8-4573-8de8-15655d62e3a2)

2. Klik follow dan terlihat user dan password yang berhasil didapatkan oleh hacker setelah melakukan bruteforce login

![image](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/assets/128958228/aad49d59-7301-4e74-bcc9-cc68b625f007)

3. Input password ke terminal

![image](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/assets/128958228/fe92a8fa-6f45-4f65-881d-8c261eb0848c)

## Soal 2
**evidence**

> Perusahaan nanomate baru saja kebobolan. Mereka menyewamu untuk mencari tahu bagaimana caranya pelaku bisa masuk.

1. Cari yang menggunakan protocol HTTP, kemudian klik follow. Dapat dilihat terdapat host dengan nama nanomate-solutions.com yang mana itu adalah nama perusahaan yang sedang kebobolan. Dapat dilihat jga web server yang digunakan adalah apache versi 2.4.56

![Evidence1](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image26.png)

2. Gunakan filter http dan ip.src==192.168.1.7 untuk mendapatkan paket yang mengirim request ke server. Metode request method POST dan endpoint yang mengandung process_login menunjukkan bahwa endpoint tersebut merupakan endpoint yang digunakan untuk login.

![Evidence2](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image10.png)

3. Klik follow untuk melihat apakah username dan password valid. Di sini terlihat bahwa username dan password tidak valid, tetapi kita mendapat informasi baru

![Evidence3](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image29.png)

4. Di sini terlihat bahwa respons server memiliki panjang +-400

![Evidence4](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image22.png)

5. Terdapat informasi line-based text data di tiap respons server sehingga tidak perlu melakukan follow satu persatu untuk melihat kredensial yang valid

![Evidence5](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image2.png)

6. Gunakan filter len(frame)>400. Saat sampai di paket yang memiliki panjang 485 didapati proses login berhasil, klik follow untuk melihat kredensial yang valid.

![Evidence6](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image29.png)

7. Input ke terminal

![Evidence7](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image5.png)

	 
## Soal 3
**How Many packets?**

> Sebagai kewajiban untuk laporan, aku diminta untuk mencari tahu berapa kali attempt login yang dilakukan oleh hacker. Dapatkah kamu membantuku untuk menganalisanya?

1. Gunakan statistics pada bagian packet lengths. Apply filter frame.len == 94 (saat di scroll, semua response login memiliki length >=94. Terlihat bahwa jumlah packets adalah 934

![image](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/assets/128958228/91809bb0-ad68-433f-b146-904cb539209c)

2. Input jumlah paket ke terminal

![image](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/assets/128958228/1799f843-5065-4b5a-95a5-7cc1e2dad6cd)

## Soal 4
**trace him**

> Selain menghitung jumlah packet, coba lacak juga ip penyerang tersebut!

1. Dapat diamati, bahwa source IP 10.15.40.20 mengirimkan response "Response: 530 Login Incorrect" kepada IP destination 10.30.3.4 . Ini menunjukkan bahwa IP 10.30.3.4 adalah IP yang melakukakan percobaan login ke source

![image](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/assets/128958228/253b9eab-a2b3-4bcf-998f-cf3dd82ae02d)

2. Input IP ke terminal

![image](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/assets/128958228/755f61d9-1160-487b-b210-978370cee6d0)


## Soal 5
**creds**

> Attacker menyadari jika dia bisa membuat clone ftp server dari target, temukan kredensialn dari server ftp yang dibuat oleh attacker

1. Gunakan filter ftp kemudian scroll, temukan paket yang berisikan informasi login berhasil

![Creds1](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image11.png)

2. Klik follow dan terlihat kredensial yang digunakan

![Creds2](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image27.png)

3. Input kredensial ke terminal

![Creds3](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image34.png)

## Soal 6
**malwleowleo**

> Dapatkah kamu menemukan file malware yang dikirim oleh attacker melalui ftp?

1. Gunakan filter ftp dan ip.src == 10.30.3.1. Kenapa ip tersebut karena ip tersebut yang didapati mengirim request (username&pw) ke server. Jadi bisa dianggap itu client/attacker. Setelah dicek ternyata dia juga mengirim malware dengan nama m4L1c10us_W4re.c (STOR m4L1c10us_w4re.c)

![malwleowleo1](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image24.png)

2. Input terminal

![malwleowleo1\2](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image3.png)

## Soal 7
**whoami**

> Dapatkah kamu menemukan siapa identitas attacker?

1. Saya mencoba melakukan pencarian dengan menggunakan filter tcp.stream, hingga tcp.stream eq 7 dan saya menemukan protocol ftp-data yang menurut saya asing

![whoami1](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image30.png)

2.  kemudian saya klik follow dan file c seperti di bawah ini

![whoami2](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image8.png)

3.  Tanda sama dengan 2x (==) merupakan ciri umum yang menunjukkan string tersebut diencode dengan base64, kemudian saya lakukan decode dan hasilnya seperti ini

![whoami3](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image28.png)

4. Karena pesannya mengatakan nama, saya mencurigai ini nama penyerang. Jadi saya coba inputkan ke terminal

![whoami4](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image20.png)

## Soal 8
**secret**

> Temukan pesan rahasia dari attacker

1. Gunakan filter ftp dan ip.src==10.30.3.1 di mana ip tersebut adalah ip attacker didapat dari soal sebelumnya. Terlihat attacker juga mengirimkan file mirza.jpg

![Secret1](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image15.png)

2. Lakukan ekspor objek terhadap paket tersebut, jangan lupa save

![Secret2](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image31.png)

3. Buka file mirza.jpg. Terlihat ada pesan yang dikutip yaitu “MIO MIRZA”

![Secret3](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image23.png)

4. Inputkan ke terminal

![Secret4](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image12.png)

## Soal 9
**Fuzz**

> My website got hacked. Can you analyze this network traffic to help me track the attacker?

1. Gunakan filter http dan cari yang menggunakan method POST karena method yang digunakan untuk login biasanya menggunakan POST. Lihat ip source yang mengirimkan request method POST, dapat dianggap pengirim request adalah attacker/client.

![Fuzz1](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image4.png)

2. Di sini dapat dilihat bahwa port destination dari request yang dikirimkan adalah 80, port tersebut dapat dianggap web server dari korban. Dapat dilihat juga bahwa endpoint yang digunakan untuk login hanya / 

![Fuzz2](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image1.png)

3. Paket ini memiliki panjang paling besar, dan berisi informasi found. Mari coba klik follow

![Fuzz3](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image33.png)

4. Setelah discroll ditemukan kredensial yang berhasil menampilkan html website

![Fuzz4](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image16.png)

5. input ke terminal

![Fuzz5](https://github.com/Zaar97/Jarkom-Modul-1-IT27-2024/blob/main/image/image13.png)

# UTS APBO A KELOMPOK 14

## Dosen Pengampu
Adi Wahyu Pribadi, S.Si., M.Kom

## Anggota Kelompok  
1. Adjie Firmansyah **[4523210004]**
2. Anavalis Ridho Abdee Nugroho **[4523210012]**
3. Muhammad Kezban Ramadzan **[4523210116]**
4. Muhamad Rahul Sani **[4519210011]**

## Percetakan Anavalis
Bisnis yang kami pilih untuk dianalisis dalam pembuatan sistem informasi berikutnya adalah usaha Percetakan milik dari salah satu anggota kami.  Percetakan ini berskala mini & melayani beberapa kebutuhan cetak, mulai berdasarkan undangan, brosur, stiker, banner, sampai print dokumen. Lokasi bisnis berada di Cibinong, Kab. Bogor.

Seluruh proses pemesanan waktu ini dilakukan secara manual melalui WhatsApp dan Gmail. Pelanggan mengirim arsip desain, berukuran cetak, & jumlah pesanan secara eksklusif melalui chat. Proses komunikasi berlangsung 2 arah untuk konfirmasi, revisi, dan ketika pengambilan atau pengiriman output cetakan. Lantaran pemilik bisnis kurang tahu sistem digital yg lebih kompleks, belum terdapat sistem pencatatan digital otomatis ataupun integrasi menggunakan sistem pembayaran online. Semua pembayaran bisa dilakukan secara tunai (cash) ataupun secara non-tunai waktu pengambilan barang.

Alur usaha percetakan ini dimulai berdasarkan proses pemasaran sederhana melalui status WhatsApp atau kenaikan pangkat berdasarkan ekspresi ke ekspresi. Apabila terdapat pemesanan masuk, pemilik akan mempelajari arsip, mencetak sinkron kebutuhan, kemudian menginformasikan kapan output cetakan mampu diambil. Produksi dilakukan menggunakan mesin printer skala rumahan. Dalam masalah cetakan besar, percetakan ini akan bekerja sama menggunakan vendor percetakan lain. Hasil cetakan yg sudah terselesaikan umumnya diambil eksklusif sang pelanggan, atau pada beberapa masalah diantar sang pemilik bisnis.

![image](https://github.com/user-attachments/assets/57e52483-4838-417d-9e58-dc133fe85d9c)


## 1. Aktor/Role
Aktor/Role

A.  Penjual berperan sebagai megelola pesanan dari pembeli yang memesan sesuai dengan apa yang mereka inginkan, pihak penjual akan melakukan pengerjaan setelah pembeli melakukan transaksi Down Payment. Setelah pesanan selesai pihak penjual akan menginformasikan pembeli untuk segera melakukan pengambilan pesanan dan melakukan Full Payment atau bisa juga melalui pengiriman.

B.  Pelanggan berperan sebagai memesan sesuai apa yang mereka inginkan setelah melakukan Down Payment, hingga akhirnya diberitahukan oleh pihak penjual dan dapat mengambil pesanan setelah melakukan Full Payment.

C.  Admin berperan sebagai mengelola pesanan pelanggan dan mengelola produk.


## 2. Use Case Diagram
![image](https://github.com/user-attachments/assets/afcfcca0-7a38-4067-8d11-a978ed2fbe8d)

### 3. Entitas Utama

#### A. Pembeli

| Atribut         | Tipe Data                     | Keterangan                        |
| --------------- | ----------------------------- | --------------------------------- |
| id_pelanggan   | INT (PK)                      | ID unik pelanggan, auto increment |
| nama            | VARCHAR(100)                  | Nama lengkap pelanggan            |
| alamat          | TEXT                          | Alamat pelanggan                  |
| email           | VARCHAR(100)                  | Email aktif pelanggan             |
| no_telepon     | VARCHAR(20)                   | Nomor telepon/HP                  |
| tipe_pelanggan | ENUM('Individu','Perusahaan') | Jenis p |

### B. Produk
| Atribut         | Tipe Data     | Keterangan                            |
| --------------- | ------------- | ------------------------------------- |
| id_produk      | INT (PK)      | ID unik produk cetak                  |
| nama_produk    | VARCHAR(100)  | Nama produk (misalnya brosur, poster) |
| deskripsi       | TEXT          | Penjelasan singkat tentang produk     |
| harga_satuan   | DECIMAL(12,2) | Harga per unit produk                 |
| waktu_estimasi | INT           | Estimasi hari produksi (dalam hari)   |

### C. Pesanan
| Atribut         | Tipe Data                                         | Keterangan                |
| --------------- | ------------------------------------------------- | ------------------------- |
| id_pesanan     | INT (PK)                                          | ID unik pesanan           |
| id_pelanggan   | INT (FK)                                          | Relasi ke tabel Pelanggan |
| tanggal_pesan  | DATE                                              | Tanggal pemesanan         |
| status_pesanan | ENUM('Diproses','Selesai','Dikirim','Dibatalkan') | Status pesanan            |
| total_harga    | DECIMAL(12,2)                                     | Total keseluruhan pesanan |

### D. Detail pesanan
| Atribut       | Tipe Data     | Keterangan                       |
| ------------- | ------------- | -------------------------------- |
| id_detail    | INT (PK)      | ID unik detail pesanan           |
| id_pesanan   | INT (FK)      | Relasi ke tabel Pesanan          |
| id_produk    | INT (FK)      | Relasi ke tabel Produk           |
| jumlah        | INT           | Jumlah unit produk dipesan       |
| harga_satuan | DECIMAL(12,2) | Harga satuan pada saat pemesanan |
| subtotal      | DECIMAL(12,2) | Jumlah harga_satuan x jumlah    |

### E. Pembayaran
| Atribut            | Tipe Data                        | Keterangan                    |
| ------------------ | -------------------------------- | ----------------------------- |
| id_pembayaran     | INT (PK)                         | ID unik pembayaran            |
| id_pesanan        | INT (FK)                         | Relasi ke tabel Pesanan       |
| tanggal_bayar     | DATE                             | Tanggal pembayaran            |
| jumlah_dibayar    | DECIMAL(12,2)                    | Total nominal yang dibayarkan |
| metode_pembayaran | ENUM('Transfer','Tunai','QRIS')  | Jenis metode pembayaran       |
| status_pembayaran | ENUM('Lunas','Belum Lunas','DP') | Status pelunasan              |

### F. Karyawan
| Atribut      | Tipe Data    | Keterangan                                |
| ------------ | ------------ | ----------------------------------------- |
| id_karyawan | INT (PK)     | ID unik karyawan                          |
| nama         | VARCHAR(100) | Nama lengkap karyawan                     |
| posisi       | VARCHAR(50)  | Posisi dalam perusahaan (Admin, Operator) |
| no_telepon  | VARCHAR(20)  | Nomor kontak                              |
| email        | VARCHAR(100) | Email aktif                               |

### G. Pengiriman
| Atribut        | Tipe Data                                   | Keterangan                     |
| -------------- | ------------------------------------------- | ------------------------------ |
| id_pengiriman | INT (PK)                                    | ID unik pengiriman             |
| id_pesanan    | INT (FK)                                    | Relasi ke tabel Pesanan        |
| tanggal_kirim | DATE                                        | Tanggal pengiriman dilakukan   |
| kurir          | VARCHAR(100)                                | Nama kurir atau jasa ekspedisi |
| no_resi       | VARCHAR(100)                                | Nomor resi pengiriman          |
| status_kirim  | ENUM('Dalam Pengiriman','Terkirim','Gagal') | Status kirim                   |

## 4. Relasi
![image](https://github.com/user-attachments/assets/019e3b26-97f5-4e34-b5ba-5b38715d8478)

## 5. Class Diagram
![image](https://github.com/user-attachments/assets/08ab7acd-7371-45ed-b368-0a2059a625a1)

## 6. Mock up/Wireframe

### a. Login Page
![image](https://github.com/user-attachments/assets/2a106471-8d7d-4b89-a90c-14fc1c5bfe4d)

![image](https://github.com/user-attachments/assets/efcfe0e3-2518-4ed8-9b00-49ac5e142f1c)

![image](https://github.com/user-attachments/assets/06d82ef5-bf04-479c-a1b6-d98832c37aed)

### b. Karyawan Page
![Karyawan Page](https://github.com/user-attachments/assets/a541fe12-5b21-40ab-9d6b-5ed7fcca7875)

### c. Pesanan Page
![Pesanan page](https://github.com/user-attachments/assets/8589acf3-6a0d-476a-b2fd-8d04e810cae7)

### d. Product Page
![image](https://github.com/user-attachments/assets/cb345fa5-3bfe-47d9-a915-e3270de7b1f7)


![image](https://github.com/user-attachments/assets/037872ac-d06d-4117-8f3a-9a1b7007c169)


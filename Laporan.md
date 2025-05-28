# UTS APBO A KELOMPOK 14

## Dosen Pengampu
Adi Wahyu Pribadi, S.Si., M.Kom

## Anggota Kelompok  
1. Adjie Firmansyah **[4523210004]**
2. Anavalis Ridho Abdee Nugroho **[4523210012]**
3. Muhammad Kezban Ramadzan **[4523210116]**
4. Muhamad Rahul Sani **[4519210011]**

## Percetakan Anavalis

## 1. Aktor/Role

## 2. Use Case Diagram

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
![image](https://github.com/user-attachments/assets/ccb059f0-9781-4917-bb67-92acfab40773)

## 5. Class Diagram
![image](https://github.com/user-attachments/assets/d4563524-7c32-4ca0-a5eb-d1d0198baa88)

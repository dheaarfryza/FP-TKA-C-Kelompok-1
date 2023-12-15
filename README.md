# FP-TKA-C-Kelompok-1

## Anggota
| Nama | NRP |
|---------------------------|------------|
|Oktavia Anggraeni P. | 5027211001 |
|Muhammad Azril Fathoni | 5027211002 |
|Rendy Anfi Yudha| 5027211006 |
|Aqil Sulthan Yuki M. | 5027211007 |
|Dyas Amorita R. N. | 5027211009 |
|Dhea Arfryza Ananda P. | 5027211013 |


## i. Introduction


### Problem
Saat kami melakukan testing, ada beberapa error not found pada endpoint, padahal order_id tersebut ada pada collection di 

![Gambar WhatsApp 2023-12-13 pukul 11 17 40_51352f67](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/4c5e69ec-9ff9-46f3-aaa1-a5ea40c6ad5e)


## ii. Arsitektur Komputasi Awan dan Tabel Harga

### Case 1
| No. | Nama | Spesifikasi | Fungsi | Harga/bulan |
|---|------------|-----------------|-------|----|
| 1 | worker-1 | 1 vCPU, 2 GB Memory | App Worker | $12 |
| 2 | worker-2 | 1 vCPU, 2 GB Memory | App Worker | $12 |
| 3 | worker-3 | 1 vCPU, 2 GB Memory | App Worker | $12 |
| 4 | db-server-1 | 2 vCPU, 2 GB Memory | Database Server | $18 |
| 5 | load-balancer | 1 vCPU, 1 GB Memory | Load Balancer | $6 |
| 6 | storage-tka-1 | - | Space Storage | $5 |
| Total | | | | $65 |

Berikut merupakan gambaran diagram Arsitektur Komputasi yang telah ditentukan.

![fp-Halaman-2 drawio](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/c78fe2f9-ab92-4dda-95d6-1798ee52fea0)

### Case 2

Berikut merupakan Rancangan Arsitektur Komputasi Awan beserta Spesifikasi dan Harga nya.

| No. | Nama | Spesifikasi | Fungsi | Harga/bulan |
|---|------------|-----------------|-------|----|
| 1 | worker-1 | 1 vCPU, 1 GB Memory | App Worker | $6 |
| 2 | worker-2 | 1 vCPU, 1 GB Memory | App Worker | $6 |
| 3 | worker-3 | 1 vCPU, 1 GB Memory | App Worker | $6 |
| 4 | worker-4 | 1 vCPU, 1 GB Memory | App Worker | $6 |
| 5 | worker-5 | 1 vCPU, 1 GB Memory | App Worker | $6 |
| 6 | worker-6 | 1 vCPU, 1 GB Memory | App Worker | $6 |
| 7 | worker-7 | 1 vCPU, 1 GB Memory | App Worker | $6 |
| 8 | load-balancer | 1 vCPU, 2 GB Memory | Load Balancer | $16 |
| 9 | db-server | 2 vCPU, 2 GB Memory | Database Server | $6 |
|  | |  | Total | $64 |

Berikut merupakan gambaran diagram Arsitektur Komputasi yang telah ditentukan.

![clouddddddd-Halaman-2 drawio](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/a15285ff-d4be-4486-abb0-7ae0830ac1d1)


## iii. Langkah-langkah Implementasi dan Konfigurasi

Untuk memudahkan deployment kita menggunakan Docker di setiap droplets, untuk config selengkapnya dapat diakses melalui source code berikut:

- Database
[Database](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/tree/main/database)
- App
[App](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/tree/main/app)
- Loadbalancer
[Loadbalancer](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/tree/main/load-balancer)

## iv. Hasil Pengujian Endpoint setiap API

Berikut adala hasil pengujian setiap endpoint menggunakan postman:

**GET**
![get orders](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/479ad013-9300-4a8b-aa41-a9dd3300eea2)

**POST**
![post orders](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/41acf460-d601-4977-a314-c403fa66769b)

## v. Hasil Pengujian dan Analisis Loadtesting Dengan Locust


## vi. Kesimpulan dan Saran

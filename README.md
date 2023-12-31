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

Dalam Final Project ini, kami diminta untuk mendesain arsitektur cloud terbaik yang sesuai dengan kebutuhan sebuah aplikasi berbasis API. Dimana dana maksimal yang diberikan adalah 1 juta rupiah per bulan (65 US$). Spesifikasi aplikasi yang diminta adalah sebagai berikut:
## Endpoints:

1. **Get All Orders**
   - **Endpoint:** `GET /orders`
   - **Description:** Retrieve a list of all orders.
   - **Response:**
     ```json
     {
       "orders": [
         {"_id": "order_id_1", "product": "Product1", "quantity": 5, "customer_name": "John Doe", "customer_address": "123 Main St"},
         {"_id": "order_id_2", "product": "Product2", "quantity": 3, "customer_name": "Jane Smith", "customer_address": "456 Oak St"},
         // ...
       ]
     }
     ```

2. **Get a Specific Order by ID**
   - **Endpoint:** `GET /orders/<order_id>`
   - **Description:** Retrieve details of a specific order by its ID.
   - **Response:**
     ```json
     {
       "order": {"_id": "order_id", "product": "ProductX", "quantity": 8, "customer_name": "Alice Johnson", "customer_address": "789 Elm St"}
     }
     ```

3. **Create a New Order**
   - **Endpoint:** `POST /orders`
   - **Description:** Create a new order.
   - **Request:**
     ```json
     {
       "product": "ProductY",
       "quantity": 2,
       "customer_name": "Bob Anderson",
       "customer_address": "101 Pine St"
     }
     ```
   - **Response:**
     ```json
     {
       "message": "Order created successfully",
       "order": {"_id": "new_order_id", "product": "ProductY", "quantity": 2, "customer_name": "Bob Anderson", "customer_address": "101 Pine St"}
     }
     ```

4. **Update an Order by ID**
   - **Endpoint:** `PUT /orders/<order_id>`
   - **Description:** Update an existing order by its ID.
   - **Request:**
     ```json
     {
       "quantity": 10,
       "customer_address": "Updated Address"
     }
     ```
   - **Response:**
     ```json
     {
       "message": "Order updated successfully",
       "order": {"_id": "order_id", "product": "Updated Product", "quantity": 10, "customer_name": "Existing Name", "customer_address": "Updated Address"}
     }
     ```

5. **Delete an Order by ID**
   - **Endpoint:** `DELETE /orders/<order_id>`
   - **Description:** Delete an existing order by its ID.
   - **Response:**
     ```json
     {
       "message": "Order deleted successfully"
     }
     ```

    ### MongoDB Configuration:

    - **Database:** `orders_db`
    - **Connection URI:** `mongodb://localhost:27017/orders_db`

---


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
| 9 | db-server | 1 vCPU, 2 GB Memory | Database Server | $6 |
|  | |  | Total | $64 |

Berikut merupakan gambaran diagram Arsitektur Komputasi yang telah ditentukan.

![clouddddddd-Halaman-2 drawio](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/a15285ff-d4be-4486-abb0-7ae0830ac1d1)

### Problem
Saat kami melakukan testing, ada beberapa error not found pada endpoint, padahal order_id tersebut ada pada collection di database

![Gambar WhatsApp 2023-12-13 pukul 11 17 40_51352f67](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/4c5e69ec-9ff9-46f3-aaa1-a5ea40c6ad5e)

Berdasarkan uji coba dari topologi 1 dengan htop, ditemukan bahwa ketiga worker mendapakan beban yang besar seperti yang ditunjukkan oleh gambar berikut, 

![Gambar WhatsApp 2023-12-12 pukul 22 10 38_1a98c749](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/bda7f517-4e2d-4193-9e8b-42b4b414ecb3)

Kemudian dari gambar berikut juga terlihat jika terdapat overkill pada database

![Gambar WhatsApp 2023-12-12 pukul 22 11 44_37bf0e38](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/deb0ba2e-cff6-479d-a27c-5b3857241288)


## iii. Langkah-langkah Implementasi dan Konfigurasi

Pada komputasi awan kami menggunakan platform DigitalOcean, dengan langkah-langkah sebagai berikut.

1. Create Droplet

Untuk membuat droplet dari Worker klik `Create` lalu pilih `Droplets`
![droplet1](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/02f010fb-6c9f-425f-97f1-0e0177358a30)

- Pilih Region

Memilih region, yaitu `Singapore`

![droplet2](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/c3b6b100-2199-42b6-9692-8d2356f21900)

- Pilih Image

Selanjutnya memilih image OS yang diinginkan, dari kami memilih `Ubuntu`

![droplet3](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/dd470147-1111-4e00-82ed-3980e2899e08)

- Pilih Size CPU

Pilih `Regular` dan `$6/mo` dengan ukuran 1 GB

![droplet4](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/e4ce3db9-a8f3-429b-9cd0-fdc029f74891)

- Pilih Metode Autentifikasi

Kami memilih `Password` sebagai metode autentifikasi kami untuk dihubungkan ke Droplet sebagai 'root'

![droplet5](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/c4736299-ad14-46b7-b213-6cb3e60c98b0)

- Menentukan Hostname dll

Menentukan jumlah Droplets yang ingin dibuat dan juga Hostname nya. Setelah semua selesai, klik `Create Droplet`

![droplet6](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/c92719fc-4540-4889-985e-29a2ccb2c963)


2. Create Database

Untuk membuat database, klik `Create` dan pilih `Database`

![image](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/1f114b50-7e08-4095-bd7a-0a87202d976f)

- Pilih Region

Sama seperti saat membuat Droplet, kami memilih `Singapore` sebagai region

![image](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/4fafa3b5-687f-41c0-911e-918df2d29973)

- Pilih Jenis Database 

Untuk Database, kami memakai `mongoDB` sebagai Database

![image](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/45a367c9-f182-437e-b0a0-f24f56f3aa70)

- Pilih Konfigurasi Database

![image](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/ce9ec152-45ad-4b8f-98c6-3d113ec8e7b5)

- Menentukan Nama Cluster

Setelah itu, pilih nama unik database cluster nya dan klik `Create Database Cluster` setelah semua selesai

![image](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/1296a8ae-05b8-47be-8fe1-7172e13229f0)


3. Create Load Balancers

Klik `Create` dan pilih `Load Balancer`

![image](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/67fe732e-bdfa-44fb-b388-ed34e37551ea)

- Pilih Region Data Center

Memilih region `Singapore`

![image](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/da7611ce-986a-4a02-918f-743147e2bf84)

- Tentukan Konfigurasi Scaling

Pilih berapa node yang diinginkan, dari kami hanya butuh `1` dengan total cost `$12`

![image](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/95bfcfc8-f34c-4e4e-ae03-fb90f8845260)

- Tentukan Droplet dan HTTP Forward

Untuk Droplet maka kami akan menghubungkan ke 7 Droplet AppWorker yang sudah dibuat dan untuk Protokol Load Balancer dan Droplet menggunakan `HTTP` dan Port kedua nya `80`

![image](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/722d9f0f-13e0-47bf-a35e-950dd78a948f)

- Pilih nama Load Balancer dan Finalisasi

Menentukan nama dari Load Balancer yaitu `load-balancer` dan klik `Create Load Balancer`

![image](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/bc2c5c83-ad31-4bef-a452-28c0a879315b)

4. Docker

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

1. Hasil RPS saat durasi waktu load testing 60 detik

![Gambar WhatsApp 2023-12-15 pukul 15 05 17_2bb4b594](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/fb2ed283-2503-4711-b393-7d3b8d9b88e3)

Hasil RPS topologi 2 berdasarkan pengujian tersebut adalah `1413.4`

2. Spawn rate 25 dan durasi waktu load testing 60 detik

![Gambar WhatsApp 2023-12-15 pukul 15 14 32_43019490](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/89828723/0104e8ff-3591-4c48-8a22-a16aedb76c3d)

Hasil RPS berdasarkan pengujian tersebut adalah `843.9`

3. spawn rate 50 dan durasi waktu load testing 60 detik

![WhatsApp Image 2023-12-17 at 19 55 42_a3b195f4](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/107184933/81534911-e85a-485d-bc8b-f6125a085bbd)

Hasil RPS berdasarkan pengujian tersebut adalah `1250.6`

5. spawn rate 100 dan durasi waktu load testing 60 detik

![WhatsApp Image 2023-12-17 at 19 55 52_b3ab5941](https://github.com/dheaarfryza/FP-TKA-C-Kelompok-1/assets/107184933/2221316d-4d40-44a7-ae43-5645037c3a36)

Hasil RPS berdasarkan pengujian tersebut adalah `1411.9`

## vi. Kesimpulan dan Saran

Berdasarkan uji coba dari topologi 1 dengan htop, ditemukan bahwa ketiga worker mendapakan beban yang berat, selain itu penyimpanan pada storage tidak terpakai, sehingga jadi terbuang.

Hal tersebut tentu dapat mempengaruhi kinerja dari sistem. Untuk mengatasinya, maka kami menambahkan jumlah worker yang tadinya 3 menjadi 7 worker. Spesifikasi dan jenis worker juga disesuaikan supaya idak melibihi budget yang diberikan, spesifikasi worker pada topologi baru adalah 1 vCPU, 1 GB Memory dengan harga $6 untuk tiap worker. Hasilnya adalah pembagian kerja yang rata.

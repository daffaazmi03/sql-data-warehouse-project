# Data Catalog Untuk Gold Layer

## Overview
Gold Layer adalah representasi data pada tingkat bisnis, yang disusun untuk mendukung kasus penggunaan analisis dan pelaporan. Lapisan ini terdiri dari tabel dimensi dan tabel fakta untuk metrik bisnis tertentu.

---

### 1. **gold.dim_customers**
- **Purpose:** Menyimpan detail pelanggan yang diperkaya dengan data demografis dan geografis
- **Columns:**

| Column Name      | Data Type     | Description                                                                                   |
|------------------|---------------|-----------------------------------------------------------------------------------------------|
| customer_key     | INT           | Kunci pengganti (surrogate key) yang secara unik mengidentifikasi setiap catatan pelanggan dalam tabel dimensi.             |
| customer_id      | INT           | Pengenal numerik unik yang diberikan kepada setiap pelanggan.                                        |
| customer_number  | NVARCHAR(50)  | Pengenal alfanumerik yang mewakili pelanggan, digunakan untuk pelacakan dan referensi.        |
| first_name       | NVARCHAR(50)  | Nama depan pelanggan seperti yang tercatat dalam sistem.                                        |
| last_name        | NVARCHAR(50)  | Nama belakang atau nama keluarga pelanggan.                                                     |
| country          | NVARCHAR(50)  | Negara tempat tinggal pelanggan (misalnya, 'Australia').                               |
| marital_status   | NVARCHAR(50)  | Status pernikahan pelanggan (misalnya,  'Married', 'Single').                             |
| gender           | NVARCHAR(50)  | The gender of the customer (e.g., 'Male', 'Female', 'n/a').                                  |
| birthdate        | DATE          | Tanggal lahir pelanggan, yang sudah diformat. as YYYY-MM-DD (misalnya, 1971-10-06).               |
| create_date      | DATE          | Tanggal dan waktu saat data pelanggan dibuat dalam sistem.|

---

### 2. **gold.dim_products**
- **Purpose:** Menyediakan informasi tentang produk dan atributnya.
- **Columns:**

| Column Name         | Data Type     | Description                                                                                   |
|---------------------|---------------|-----------------------------------------------------------------------------------------------|
| product_key         | INT           | Kunci pengganti yang secara unik mengidentifikasi setiap data produk dalam tabel dimensi produk.         |
| product_id          | INT           | Pengenal unik yang diberikan kepada produk untuk pelacakan dan referensi internal.          |
| product_number      | NVARCHAR(50)  | Kode alfanumerik terstruktur yang mewakili produk, sering digunakan untuk kategorisasi atau inventaris. |
| product_name        | NVARCHAR(50)  | Nama deskriptif produk, termasuk detail utama seperti tipe, warna, dan ukuran.         |
| category_id         | NVARCHAR(50)  | Pengenal unik untuk kategori produk, menghubungkan dengan klasifikasi tingkat tinggi.     |
| category            | NVARCHAR(50)  | Klasifikasi umum produk (misalnya, Bikes, Components) untuk mengelompokkan item terkait.   |
| subcategory         | NVARCHAR(50)  | Klasifikasi lebih rinci dari produk dalam kategori, seperti jenis produk.      |
| maintenance_required| NVARCHAR(50)  | Menunjukkan apakah produk memerlukan perawatan (misalnya, 'Yes', 'No').                       |
| cost                | INT           | Biaya atau harga dasar produk, diukur dalam satuan mata uang.                            |
| product_line        | NVARCHAR(50)  | Jalur produk atau seri khusus tempat produk tersebut termasuk (misalnya, Road, Mountain).      |
| start_date          | DATE          | Tanggal ketika produk mulai tersedia untuk dijual atau digunakan.|

---

### 3. **gold.fact_sales**
- **Purpose:** Menyimpan data transaksi penjualan untuk keperluan analisis.
- **Columns:**

| Column Name     | Data Type     | Description                                                                                   |
|-----------------|---------------|-----------------------------------------------------------------------------------------------|
| order_number    | NVARCHAR(50)  | Pengenal alfanumerik unik untuk setiap pesanan penjualan (misalnya, 'SO54496').                      |
| product_key     | INT           | Kunci pengganti yang menghubungkan pesanan dengan tabel dimensi produk.                               |
| customer_key    | INT           | Kunci pengganti yang menghubungkan pesanan dengan tabel dimensi pelanggan.                              |
| order_date      | DATE          | Tanggal saat pesanan dibuat.                                                          |
| shipping_date   | DATE          | Tanggal saat pesanan dikirimkan ke pelanggan.                                          |
| due_date        | DATE          | Tanggal jatuh tempo pembayaran pesanan.                                                      |
| sales_amount    | INT           | Total nilai uang dari penjualan untuk item tersebut, dalam satuan mata uang penuh (misalnya, 25).   |
| quantity        | INT           | Jumlah unit produk yang dipesan untuk item tersebut (misalnya, 1).                      |
| price           | INT           | Harga per unit produk untuk item tersebut, dalam satuan mata uang penuh (misalnya, 25).
      |

# Praktikum 8: PHP dan Database MySQL
NAMA : ANDREAN PUTRA ARYA

NIM : 312410341

KELAS : TI.24.A.4

# Membuat Database

```
CREATE DATABASE latihan1;
```
# Membuat Tabel
```
CREATE TABLE data_barang (
 id_barang int(10) auto_increment Primary Key,
 kategori varchar(30),
 nama varchar(30),
 gambar varchar(100),
 harga_beli decimal(10,0),
 harga_jual decimal(10,0),
 stok int(4)
);
```
# Menampilkan Tabel Di terminal
![gambar](https://github.com/andreanbadeh/Lab8Web/blob/5909785a87915a34b44d5d9e41fc91659c272e17/image/Screenshot%20from%202025-11-19%2014-44-24.png)

# Membuat file koneksi database
```
<?php
$host = "localhost";
$user = "root";
$pass = "12345";
$db   = "latihan1";

$conn = mysqli_connect($host, $user, $pass, $db);

if (!$conn) {
    die("Koneksi ke database gagal: " . mysqli_connect_error());
} echo "Koneksi Berhasil!";
?>
```
OUTPOUT 


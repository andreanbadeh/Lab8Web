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

# Membuat file koneksi database koneksi.php
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
HASILNYA:

![gambar](https://github.com/andreanbadeh/Lab8Web/blob/80515fa92c0379f3c15bed668cf706c89898eb53/image/Screenshot%20from%202025-11-19%2014-55-15.png)

# Membuat file index untuk menampilkan data (Read) index.php
```
<?php 
include 'koneksi.php';

$sql = "SELECT * FROM data_barang";
$result = mysqli_query($conn, $sql);
?>
<!DOCTYPE html>
<html>
<head>
    <title>Data Barang</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

<div class="container">
    <h1>Data Barang</h1>

    <a href="tambah.php" class="btn">+ Tambah Barang</a>

    <table>
        <tr>
            <th>Gambar</th>
            <th>Nama</th>
            <th>Kategori</th>
            <th>Harga Beli</th>
            <th>Harga Jual</th>
            <th>Stok</th>
            <th>Aksi</th>
        </tr>

        <?php while ($row = mysqli_fetch_assoc($result)) : ?>
            <tr>
                <td>
                    <?php if ($row["gambar"] != ""): ?>
                        <img src="gambar/<?php echo $row["gambar"]; ?>" class="thumb">
                    <?php else: ?>
                        -
                    <?php endif; ?>
                </td>
                <td><?= $row["nama"] ?></td>
                <td><?= $row["kategori"] ?></td>
                <td><?= number_format($row["harga_beli"]) ?></td>
                <td><?= number_format($row["harga_jual"]) ?></td>
                <td><?= $row["stok"] ?></td>
                <td>
                    <a class="link" href="ubah.php?id=<?= $row['id_barang'] ?>">Ubah</a> |
                    <a class="link" href="hapus.php?id=<?= $row['id_barang'] ?>" onclick="return confirm('Hapus data?')">Hapus</a>
                </td>
            </tr>
        <?php endwhile; ?>

    </table>

</div>

</body>
</html>
```

HASILNYA:

![gambar](

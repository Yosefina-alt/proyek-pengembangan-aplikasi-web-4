Sistem Manajemen Inventaris

Analisis Kebutuhan/Fitur Aplikasi
1.Fitur Utama:
=>Pengelolaan produk (CRUD: Create, Read, Update, Delete)
=>Pengelolaan kategori produk
=>Pencarian produk
=>Laporan inventaris
2.Kebutuhan Pengguna:
=>Admin dapat menambahkan, mengedit, dan menghapus produk.
=>Admin dapat mengelola kategori produk.
=>Pengguna dapat mencari produk berdasarkan nama atau kategori.
3.Tahapan Implementasi
=>Persiapan Database:
  * Buat database di server lokal atau web host.
  * Buat tabel berikut:
    1)Tabel Produk:
      >id_produk (INT, Primary Key, Auto Increment)
      >nama_produk (VARCHAR)
      >deskripsi (TEXT)
      >harga (DECIMAL)
      >id_kategori (INT, Foreign Key)
    2)Tabel Kategori:
      >id_kategori (INT, Primary Key, Auto Increment)
      >nama_kategori (VARCHAR)
=>Isi Tabel dengan Data Contoh:
sql
Salin kode
INSERT INTO kategori (nama_kategori) VALUES ('Elektronik'), ('Furniture'), ('Pakaian');

INSERT INTO produk (nama_produk, deskripsi, harga, id_kategori) VALUES
('Laptop', 'Laptop gaming', 15000000, 1),
('Kursi', 'Kursi nyaman', 750000, 2),
('Kaos', 'Kaos cotton', 150000, 3);

=>Uji Relasi dengan SQL:
sql
Salin kode
SELECT p.nama_produk, k.nama_kategori
FROM produk p
JOIN kategori k ON p.id_kategori = k.id_kategori;

=>Koneksi Database Menggunakan PHP:
php
Salin kode
<?php
$host = 'localhost';
$username = 'root';
$password = '';
$database = 'nama_database';

$conn = new mysqli($host, $username, $password, $database);

if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}
echo "Connected successfully";
?>

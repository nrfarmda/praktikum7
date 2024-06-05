# Praktikum 7
## Show tables 
### Struktur
```sql
show tables;
```
### Hasil
![[mada6.png]]
## Odproducts
### Struktur
```sql
SELECT * FROM order_details;
```
### Hasil
![[mada7.png]]
### Analisis
- `CREATE VIEW odproduct`: Untuk membuat tabel virtual dengan nama odproducts.
- `AS SELECT`: Untuk memilih kolom-kolom mana saja yang ingin dipilih untuk dimasukkan ke tabel virtual.
- `od.orderID, od.ProductID, od.unitPrice, od.quantity`: Kolom orderID, ProductID, UnitPrice dan Quantity dari tabel od(orderdetails) dipilih untuk dimasukkan.
- `P.ProductName`: Kolom ProductName dari tabel P(Products) dipilih untuk dimasukkan 
- `FROM orderdetails od,Products P`: Untuk memilih dari tabel mana saja yang kolomnya dipilih untuk dimasukkan. orderdetails dan products adalah nama tabek yang dipilih.
- `WHERE`: Kondisi yang harus dipenuhi oleh suatu data agar bisa dimasukkan ke dalam tabel virtual.
- `(P. ProductID=od. ProductID)`: Data pada kolom ProductID dari tabel P(Product) harus sama dengan kolom ProductID dari tabel od(orderdetails), agar bisa dimasukkan.
- `Hasilnya`: Tabel virtual yang bernama odproducts yang terbuat dari kolom dalam 2 tabel, orderdetails dan products.
## Orderdetails
### Struktur
```sql
SELECT * FROM orderdetails;
```
### Hasil
![[mada8.png]]
### Analisis
- `SELECT`: Untuk memilih kolom mana saja yang ingin ditampilkan dan dihitung.
- `c.customerID, c.companyName`: Kolom costumerID dan companyName dari tabel c(customers) dipilih untuk ditampilkan.
- `o.orderID`: Kolom orderID dari tabel o(orders) dipilih untuk ditampilkan.
- `od. ProductID, od.unitPrice, od.quantity, od.Discount`: Kolom ProductId, UnitPrice, Quantity dan Discount dari tabel od(orderdetails) dipilih untuk ditampilkan dan dibulatkan.
- `ROUND (od.UnitPrice,2)`: Untuk membulatkan bilangan dari kolom unitPrice sampai jumlah digit tertentu sesuai dengan pilihan yang dibuat yaitu 2.
- `ROUND(((1-od.Discount)*od.unitPrice* od.Quantity),2) AS Jumlah`: Untuk membulatkan bilangan dari kolom hasil dari (1 dikurang kolom discount) lalu dikali unitPrice dan kali Quantity) sampai jumlah digit yaitu 2. AS jumlah untuk mengubah kolom hasil tersebut nama sementaranya jadi jumlah.
- `FROM customers c,orders o,orderdetails od`: Untuk memilih dari tabel nama saja yang kolomnya dipilih untuk ditampilkan dan dibulatkan customers. orders, orderdetails merupakan nama-nama tabel yang dipilih.
- `WHERE`: Kondisi yang harus dipenuhi oleh suatu data agar bisa ditampilkan.
- `(c.customersID=o.custID)`: Data pada kolom customers dari tabel c(customers) harus sama dengan data pada kolom custID dari tabel o(orders).
- `AND`: Untuk menyeleksi dua data atau lebih pada kondisi WHERE.
- `(o.orderID=od.orderID)`: Data pada kolom orderID dari tabel od(orderdetails).
- `ORDER BY c.customerID`: Untuk mengurut data berdasarkan kolom customers dari tabel c(customers).
- `Hasil`: Akan tampil hasil pembulatan dari kolom-kolom yang telah memenuhi kondisi dari WHERE.
## Costumerid
### Struktur
```sql
SELECT * FROM costumerid;
```
### Hasil
![[mada9.png]]
### Analisis
- `SELECT`: Untuk memilih kolom mana saja yang ingin ditampilkan dan dibulatkan.
- `C.customerID, C.companyName`: Kolom customeID dan companyName dari tabel c(customers) dipilih untuk ditampilkan.
- `ROUND (SUM((1-od.discount) *od.unitprice* od.quantity),2) AS Total jumlah`: Untuk membulatkan hasil SUM dari ((1 dikurang kolom Discount) dikali unitprice kali Quantity) sampai 2 digit. Dan nama kolom hasilnya di ubah sementara jadi total jumlah.
- `FROM customers c,orders o, orderdetails od`: Untuk memilih dari tabel mana saja yang kolomnya dipilih untuk ditampilkan dan dibulatkan. customers orders dan orderdetails adalah nama tabel yang dipilih.
- `WHERE`: Kondisi yang harus dipenuhi oleh suatu data agar bisa ditampilkan.
- `(c.customerID=o.custID)`: Data pada kolom customerID dari tabel c(customers) harus sama dengan data pada kolom custID dari tabel o(orders).
- `AND`: Untuk menyeleksi dua data atau lebih pada kondisi WHERE.
- `(o.orderID=od.orderID)`: Data pada kolom orderID dari tabel o(orders), harus sama dengan data pada kolom orderID dari tabel od(orderdetails).
- `GROUP BY c.customerID, c.companyName`:Untuk mengelompokkan data sesuai dengan kolom customerID dan companyName dari tabel c(customers).
- `ORDER BY c.customerID`:Untuk mengurut data berdasarkan kolom customerID dari tabel c(customers).
- `Hasil`:Jadi, kolom yang dikelompokkan adalah customerID dan companyName dan data tampilannya diurutkan berdasarkan kolom customerID.
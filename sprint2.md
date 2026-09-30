DIGITAL TWIN
============

Objek: kamar kos

Suhu       : 28°C
Kelembapan : 65%
Lampu      : MENYALA
AC         : MENYALA
Orang      : 25

Status Ruangan:
NORMAL

--------------------
Data diperbarui...
--------------------

DIGITAL TWIN SMART ROOM

[SENSOR]
Suhu       = 28°C
Kelembapan = 65%

[PERANGKAT]
Lampu = ON
AC    = ON

[STATUS]
Ruangan Normal


```mermaid
erDiagram
  USER ||--o{ KAMAR : memiliki
  USER ||--o{ SEWA : mengajukan
  KAMAR ||--o{ SEWA : disewa
  SEWA ||--o{ PEMBAYARAN : memiliki
  USER { int id string nama string email string role }
  KAMAR { int id int pemilik_id string nama int harga string status }
  SEWA { int id int user_id int kamar_id date mulai date selesai }
  PEMBAYARAN { int id int sewa_id int jumlah date tanggal string status }
```


DIGITAL TWIN
============

Objek: kamar kos

Suhu       : 28°C

Kelembapan : 65%

Lampu      : MENYALA


Orang      : 1

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


[STATUS]

Ruangan Normal


```mermaid
## 2. Dokumen Desain & Arsitektur (Project Setup & UX Design)

### 2.1 Rancangan UX/UI

Tautan Figma: [Wireframe Digital Twin Kamar Kos](https://www.figma.com/GANTI-DENGAN-TAUTAN-KALIAN)

Daftar layar:

| No | Layar | Fungsi |
|----|-------|--------|
| 1 | Login | Masuk ke aplikasi |
| 2 | Dashboard Kamar | Menampilkan suhu, kelembapan, dan status lampu |
| 3 | Digital Twin | Visual kamar dengan indikator real-time |
| 4 | Kontrol Lampu | Tombol ON/OFF lampu |
| 5 | Grafik Riwayat | Grafik suhu dan kelembapan |
| 6 | Pengaturan | Perangkat dan notifikasi |

Sketsa wireframe layar Dashboard Kamar:

```text
+--------------------------------+
|  Kamar Kos A-01        [Menu]  |
+--------------------------------+
|  +-----------+  +-----------+  |
|  |  SUHU     |  | KELEMBAPAN|  |
|  |  28 C     |  |  65 %     |  |
|  +-----------+  +-----------+  |
|  +--------------------------+  |
|  |  LAMPU        [ ON | OFF ]|  |
|  +--------------------------+  |
|  +--------------------------+  |
|  |  Grafik 24 jam terakhir  |  |
|  +--------------------------+  |
+--------------------------------+
| Home | Twin | Riwayat | Atur   |
+--------------------------------+
```

### 2.2 Rancangan Sistem

#### Arsitektur Sistem

```mermaid
flowchart LR
  S1["Sensor suhu & kelembapan<br/>DHT22"] --> M["Mikrokontroler<br/>ESP32"]
  L["Lampu + relay"] <--> M
  M -- "MQTT / HTTP" --> B["Backend API"]
  B --> D[("Database")]
  B --> T["Digital Twin<br/>model virtual kamar"]
  T --> U["Dashboard web / mobile"]
  U -- "perintah lampu" --> B
```

#### Flowchart Alur Data

```mermaid
flowchart TD
  A["Sensor membaca suhu & kelembapan"] --> B["ESP32 mengirim data"]
  B --> C["Backend menerima & menyimpan"]
  C --> D["Digital twin memperbarui status kamar"]
  D --> E["Dashboard menampilkan data real-time"]
  E --> F{"Pengguna mengubah lampu?"}
  F -- Ya --> G["Kirim perintah ON/OFF"]
  G --> H["ESP32 menyalakan / mematikan lampu"]
  H --> D
  F -- Tidak --> A
```

#### ERD (Struktur Database)

```mermaid
erDiagram
  USER ||--o{ KAMAR : menghuni
  KAMAR ||--o{ PERANGKAT : memiliki
  PERANGKAT ||--o{ DATA_SENSOR : menghasilkan
  PERANGKAT ||--o{ LOG_LAMPU : dikontrol
  USER ||--o{ LOG_LAMPU : memberi_perintah

  USER {
    int id PK
    string nama
    string email
    string role
  }
  KAMAR {
    int id PK
    int user_id FK
    string nama
    string lantai
  }
  PERANGKAT {
    int id PK
    int kamar_id FK
    string jenis
    string status
  }
  DATA_SENSOR {
    int id PK
    int perangkat_id FK
    float suhu
    float kelembapan
    datetime waktu
  }
  LOG_LAMPU {
    int id PK
    int perangkat_id FK
    int user_id FK
    string status
    datetime waktu
  }
```


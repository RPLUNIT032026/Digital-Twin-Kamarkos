## 3. INISIALISASI PROYEK (PROJECT SETUP)

### Kerangka Dasar (Boilerplate/Starter )

Struktur awal proyek Digital Twin Kamar Kos dibuat untuk menampilkan
informasi kondisi ruangan berdasarkan tiga parameter utama, yaitu
suhu ruangan, kelembapan ruangan, dan status lampu.

### Parameter Sistem

| No | Parameter | Nilai Awal | Satuan | Keterangan |
|---|---|---:|---|---|
| 1 | Suhu Ruangan | 28 | °C | Kondisi normal |
| 2 | Kelembapan Ruangan | 65 | % | Kondisi normal |
| 3 | Status Lampu | AKTIF| - | Lampu menyala |

### Perhitungan Kondisi Ruangan

| Parameter | Batas Kondisi | Nilai | Hasil |
|---|---|---:|---|
| Suhu | < 20 °C = Dingin | 28 °C | Normal |
| Suhu | 20 - 30 °C = Normal | 28 °C | Normal |
| Suhu | > 30 °C = Panas | 28 °C | Normal |
| Kelembapan | < 40 % = Kering | 65 % | Normal |
| Kelembapan | 40 - 70 % = Normal | 65 % | Normal |
| Kelembapan | > 70 % = Lembap | 65 % | Normal |
| Lampu | ON = Menyala | AKTIF | Menyala |
| Lampu | OFF = Mati | AKTIF | Menyala |

### Hasil Project Setup

| No | Fitur | Status |
|---|---|---|
| 1 | Menampilkan suhu ruangan | Selesai |
| 2 | Menampilkan kelembapan ruangan | Selesai |
| 3 | Menampilkan status lampu | Selesai |
| 4 | Menentukan kondisi suhu | Selesai |
| 5 | Menentukan kondisi kelembapan | Selesai |
| 6 | Menentukan kondisi keseluruhan kamar | Selesai |

### Kesimpulan

Berdasarkan data awal, suhu ruangan sebesar **28 °C** termasuk
kategori **normal**, kelembapan sebesar **65 %** termasuk kategori
**normal**, dan lampu dalam kondisi **AKTIF atau menyala**.

Project setup ini menjadi kerangka awal untuk pengembangan
Digital Twin Kamar Kos pada tahap berikutnya.

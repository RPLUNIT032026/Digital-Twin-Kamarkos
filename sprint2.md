## 2. Alur MDA Sederhana

Diagram ini memperlihatkan bagaimana satu model sistem dapat
dikembangkan untuk beberapa platform.

```mermaid
flowchart TD
    A["PIM<br/>Model Digital Twin Kamar Kos"]

    A --> B["Transformasi ke Web"]
    A --> C["Transformasi ke Android"]

    B --> D["PSM Web"]
    C --> E["PSM Android"]

    D --> F["Pembuatan Kode Web"]
    E --> G["Pembuatan Kode Android"]

    F --> H["Aplikasi Kamar Kos Web"]
    G --> I["Aplikasi Kamar Kos Android"]

    classDef model fill:#e1f5fe,stroke:#03a9f4,stroke-width:2px,color:#111
    classDef output fill:#e8f5e9,stroke:#4caf50,stroke-width:2px,color:#111
    class A,D,E model
    class H,I output
```




Dengan pendekatan ini, rancangan sistem dapat dibuat terlebih dahulu
sebelum diimplementasikan menjadi aplikasi.

**Catatan:** Diagram ini merupakan ilustrasi proses MDA. Transformasi
model dan pembuatan kode otomatis memerlukan alat atau generator
yang sesuai; diagram saja tidak otomatis menghasilkan program.

## Context Model — DIGITAL TWIN KAMAR KOS

```mermaid id="q8m2vn"
flowchart TB
    A["Sistem Monitoring Kamar"]
    B["Sistem Notifikasi"]
    C["Penghuni Kos"]
    D["Sensor Lingkungan"]
    E["Sistem Kontrol Perangkat"]
    F["Database Riwayat"]
    G["DIGITAL TWIN KAMAR KOS"]

    A --- G
    B --- G
    C --- G
    D --- G
    G --- E
    G --- F

    style G fill:#d9f2ff,stroke:#168aad,stroke-width:3px,color:#111
    style A fill:#ffffff,stroke:#168aad,stroke-width:2px,color:#111
    style B fill:#ffffff,stroke:#168aad,stroke-width:2px,color:#111
    style C fill:#ffffff,stroke:#168aad,stroke-width:2px,color:#111
    style D fill:#ffffff,stroke:#168aad,stroke-width:2px,color:#111
    style E fill:#ffffff,stroke:#168aad,stroke-width:2px,color:#111
    style F fill:#ffffff,stroke:#168aad,stroke-width:2px,color:#111
```

### Keterangan

1. **Sistem Monitoring Kamar:** menampilkan suhu dan kelembapan.
2. **Sistem Notifikasi:** memberikan pemberitahuan jika kondisi kamar tidak normal.
3. **Penghuni Kos:** memantau kondisi dan mengatur perangkat.
4. **Sensor Lingkungan:** mengirim data kondisi kamar.
5. **Sistem Kontrol Perangkat:** mengatur lampu dan perangkat lain.
6. **Database Riwayat:** menyimpan catatan kondisi kamar.

### Kesimpulan

Context Model ini menggambarkan hubungan Digital Twin Kamar Kos dengan enam sistem atau pihak yang mendukung pemantauan dan pengendalian kamar.


## 3. Use Case Diagram

Diagram ini menunjukkan interaksi antara aktor (penghuni kost, pemilik kost, dan sensor IoT)
dengan fungsi-fungsi utama pada sistem Digital Twin Kamar Kos.

```mermaid
flowchart LR
    P["Penghuni Kost"]
    S["Sensor IoT"]
    O["Pemilik Kost"]

    subgraph SYS["Sistem Digital Twin Kamar Kos"]
        UC1(["Lihat kondisi kamar"])
        UC2(["Kontrol perangkat kamar"])
        UC3(["Pantau konsumsi listrik"])
        UC4(["Terima notifikasi anomali"])
        UC5(["Kirim data sensor"])
        UC6(["Kelola data kamar"])
    end

    P --- UC1
    P --- UC2
    P --- UC3
    P --- UC4

    S --- UC5

    UC1 --- O
    UC3 --- O
    UC4 --- O
    UC6 --- O

    classDef actor fill:#fff3e0,stroke:#ff9800,stroke-width:2px,color:#111
    classDef usecase fill:#e1f5fe,stroke:#03a9f4,stroke-width:2px,color:#111
    class P,S,O actor
    class UC1,UC2,UC3,UC4,UC5,UC6 usecase
```

## 4. Deskripsi Use Case

Detail interaksi dijabarkan dalam tabel. Berikut contoh untuk use case Kontrol perangkat kamar.

| Digital Twin Kamar Kos: Kontrol perangkat kamar | |
|---|---|
| Aktor | Penghuni kost, perangkat IoT (AC, lampu) |
| Deskripsi | Penghuni mengirim perintah dari aplikasi, misalnya menyalakan AC atau mematikan lampu. Perintah diproses oleh model digital twin, diteruskan ke perangkat fisik, lalu status terbaru ditampilkan kembali di aplikasi. |
| Data | Perintah kontrol, status perangkat, suhu dan kelembapan ruangan |
| Stimulus | Perintah yang diberikan penghuni melalui aplikasi |
| Respons | Konfirmasi bahwa perangkat sudah berubah dan model digital twin sudah diperbarui |
| Komentar | Penghuni harus login dan terdaftar sebagai penyewa kamar tersebut. Perangkat harus terhubung ke jaringan. |

## 5. Sequence Diagram

### 5.1 Kontrol perangkat kamar

Diagram ini menunjukkan urutan pesan saat penghuni menyalakan AC.
Garis putus-putus adalah pesan balasan.

```mermaid
sequenceDiagram
    actor P as Penghuni
    participant A as Aplikasi
    participant DT as Digital Twin
    participant IoT as Perangkat IoT

    P->>A: Nyalakan AC
    A->>DT: Kirim perintah
    DT->>IoT: Teruskan perintah
    IoT-->>DT: Konfirmasi status
    DT-->>A: Perbarui model
    A-->>P: Tampilkan status AC
```

### 5.2 Notifikasi anomali

Diagram ini menunjukkan alur saat sensor mengirim data dan sistem mendeteksi kondisi tidak wajar.

```mermaid
sequenceDiagram
    participant IoT as Sensor IoT
    participant DT as Digital Twin
    participant A as Aplikasi
    actor P as Penghuni
    actor O as Pemilik Kost

    IoT->>DT: Kirim data sensor
    DT->>DT: Perbarui model kamar
    DT->>DT: Periksa ambang batas

    alt Suhu atau daya melebihi batas
        DT->>A: Buat notifikasi anomali
        A-->>P: Tampilkan notifikasi
        A-->>O: Tampilkan notifikasi
    else Kondisi normal
        DT-->>IoT: Data diterima
    end
```

## 6. State Diagram

State diagram menunjukkan perubahan status suatu objek selama siklus hidupnya. Pada sistem
Digital Twin Kamar Kos, dua objek yang statusnya berubah-ubah adalah pesanan kamar dan review.

### 6.1 Status Pesanan Kamar

Diagram ini menunjukkan perjalanan pesanan sejak penghuni memesan kamar sampai masa sewa selesai.

```mermaid
stateDiagram-v2
    direction LR

    state "Menunggu pembayaran" as MenungguBayar
    state "Menunggu konfirmasi" as MenungguKonfirmasi
    state "Sewa aktif" as Aktif

    [*] --> MenungguBayar: Penghuni memesan kamar
    MenungguBayar --> MenungguKonfirmasi: Bukti bayar diunggah
    MenungguBayar --> Dibatalkan: Batas waktu habis atau dibatalkan

    MenungguKonfirmasi --> Aktif: Pemilik mengonfirmasi
    MenungguKonfirmasi --> Ditolak: Pemilik menolak

    Aktif --> Selesai: Masa sewa berakhir

    Dibatalkan --> [*]
    Ditolak --> [*]
    Selesai --> [*]
```

| Status | Keterangan |
|---|---|
| Menunggu pembayaran | Pesanan dibuat, penghuni belum membayar |
| Menunggu konfirmasi | Bukti pembayaran sudah diunggah, menunggu pemeriksaan pemilik |
| Sewa aktif | Pembayaran dikonfirmasi, kamar dipakai dan digital twin kamar aktif |
| Selesai | Masa sewa berakhir dan kamar kembali tersedia |
| Dibatalkan | Pesanan dibatalkan penghuni atau melewati batas waktu pembayaran |
| Ditolak | Pemilik menolak pesanan |

### 6.2 Status Review

Diagram ini menunjukkan alur review dari penulisan oleh penghuni sampai terbit atau dihapus.

```mermaid
stateDiagram-v2
    state "Menunggu moderasi" as Moderasi

    [*] --> Draft: Penghuni menulis review
    Draft --> Moderasi: Review dikirim
    Draft --> [*]: Draft dihapus

    Moderasi --> Terbit: Disetujui
    Moderasi --> Ditolak: Melanggar aturan

    Ditolak --> Draft: Penghuni merevisi

    Terbit --> Ditanggapi: Pemilik membalas
    Terbit --> Dilaporkan: Dilaporkan pengguna lain
    Ditanggapi --> Dilaporkan: Dilaporkan pengguna lain

    Dilaporkan --> Terbit: Laporan tidak terbukti
    Dilaporkan --> Dihapus: Laporan terbukti

    Dihapus --> [*]
```

| Status | Keterangan |
|---|---|
| Draft | Review sedang ditulis dan belum dikirim |
| Menunggu moderasi | Review dikirim dan sedang diperiksa |
| Terbit | Review tampil untuk umum |
| Ditanggapi | Pemilik kost sudah membalas review |
| Dilaporkan | Review dilaporkan dan sedang ditinjau |
| Ditolak | Review tidak lolos moderasi dan bisa direvisi |
| Dihapus | Review dihapus dari sistem |

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

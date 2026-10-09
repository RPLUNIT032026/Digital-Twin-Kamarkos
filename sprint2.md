# 🏠 DIGITAL TWIN KAMAR KOS

Selamat datang di proyek Digital Twin Kamar Kos!
Sistem ini digunakan untuk memantau kondisi kamar secara digital.
> Maaf kami masih pemula, Bu. Mohon maaf jika masih banyak kesalahan.


## 🌡️ Contoh Data Kamar

| Informasi | Nilai |
|---|---|
| Suhu | 28°C |
| Kelembapan | 65% |
| Lampu | HIDUP |
| Status | Normal |

## 📊 Diagram Alur Sistem

```mermaid
flowchart TD
    A([Mulai]) --> B[Masuk Aplikasi]
    B --> C[Dashboard Kamar Kos]
    C --> D[Baca Data Suhu]
    C --> E[Baca Data Kelembapan]
    C --> F[Lihat Status Lampu]
    D --> G[Tampilkan Kondisi Kamar]
    E --> G
    F --> G
    G --> H{Pilih Kontrol Lampu}
    H -->|ON| I[Lampu Menyala]
    H -->|OFF| J[Lampu Mati]
    I --> K[Perbarui Status]
    J --> K
    K --> C
```

## 💡 Diagram Status Lampu

```mermaid
stateDiagram-v2
    [*] --> Mati
    Mati --> Menyala: Tombol ON
    Menyala --> Mati: Tombol OFF
```

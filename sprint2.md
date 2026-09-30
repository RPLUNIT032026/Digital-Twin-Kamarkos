<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Rekayasa Perangkat Lunak</title>

    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: Arial, sans-serif;
            background-color: #f4f6f8;
            color: #333;
        }

        header {
            background-color: #24292f;
            color: white;
            text-align: center;
            padding: 40px 20px;
        }

        header h1 {
            font-size: 35px;
            margin-bottom: 10px;
        }

        header p {
            font-size: 18px;
        }

        nav {
            background-color: #b23b3b;
            text-align: center;
            padding: 15px;
        }

        nav a {
            color: white;
            text-decoration: none;
            margin: 0 15px;
            font-weight: bold;
        }

        nav a:hover {
            text-decoration: underline;
        }

        .container {
            width: 90%;
            max-width: 1000px;
            margin: 30px auto;
        }

        .card {
            background-color: white;
            padding: 25px;
            margin-bottom: 25px;
            border-radius: 10px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
        }

        .card h2 {
            color: #b23b3b;
            margin-bottom: 15px;
        }

        .card p {
            line-height: 1.7;
        }

        ul {
            margin-left: 25px;
            line-height: 2;
        }

        .steps {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
        }

        .step {
            background-color: #f8f9fa;
            padding: 20px;
            border-left: 5px solid #b23b3b;
            border-radius: 5px;
        }

        .step h3 {
            margin-bottom: 8px;
        }

        .project {
            background-color: #fff3cd;
            border: 1px solid #ffe69c;
            padding: 20px;
            border-radius: 8px;
        }

        footer {
            background-color: #24292f;
            color: white;
            text-align: center;
            padding: 20px;
            margin-top: 40px;
        }

        @media (max-width: 600px) {
            header h1 {
                font-size: 28px;
            }

            nav a {
                display: block;
                margin: 8px;
            }

            .steps {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>

<body>

    <!-- HEADER -->
    <header>
        <h1>Rekayasa Perangkat Lunak</h1>
        <p>Software Engineering - RPL</p>
    </header>

    <!-- NAVIGASI -->
    <nav>
        <a href="#pengertian">Pengertian</a>
        <a href="#tujuan">Tujuan</a>
        <a href="#proses">Proses</a>
        <a href="#project">Project</a>
    </nav>

    <div class="container">

        <!-- PENGERTIAN -->
        <section class="card" id="pengertian">
            <h2>📚 Pengertian RPL</h2>

            <p>
                Rekayasa Perangkat Lunak atau RPL adalah bidang ilmu
                yang mempelajari proses pengembangan perangkat lunak
                secara sistematis, terstruktur, dan terorganisasi.
                RPL bertujuan menghasilkan perangkat lunak yang
                sesuai dengan kebutuhan pengguna serta memiliki
                kualitas yang baik.
            </p>
        </section>

        <!-- TUJUAN -->
        <section class="card" id="tujuan">
            <h2>🎯 Tujuan Rekayasa Perangkat Lunak</h2>

            <ul>
                <li>Menghasilkan perangkat lunak yang berkualitas.</li>
                <li>Memenuhi kebutuhan pengguna.</li>
                <li>Mengurangi kesalahan dalam pengembangan software.</li>
                <li>Membuat proses pengembangan lebih terstruktur.</li>
                <li>Mempermudah pemeliharaan perangkat lunak.</li>
            </ul>
        </section>

        <!-- PROSES -->
        <section class="card" id="proses">
            <h2>⚙️ Proses Pengembangan Perangkat Lunak</h2>

            <div class="steps">

                <div class="step">
                    <h3>1. Analisis Kebutuhan</h3>
                    <p>
                        Mengidentifikasi kebutuhan dan masalah
                        yang harus diselesaikan oleh sistem.
                    </p>
                </div>

                <div class="step">
                    <h3>2. Perancangan</h3>
                    <p>
                        Membuat rancangan sistem, database,
                        tampilan, dan alur aplikasi.
                    </p>
                </div>

                <div class="step">
                    <h3>3. Implementasi</h3>
                    <p>
                        Mengubah rancangan menjadi program
                        menggunakan bahasa pemrograman.
                    </p>
                </div>

                <div class="step">
                    <h3>4. Pengujian</h3>
                    <p>
                        Memeriksa sistem untuk menemukan
                        kesalahan dan memastikan fitur berjalan.
                    </p>
                </div>

                <div class="step">
                    <h3>5. Pemeliharaan</h3>
                    <p>
                        Melakukan perbaikan dan pengembangan
                        sistem setelah digunakan.
                    </p>
                </div>

                <div class="step">
                    <h3>6. Pengembangan</h3>
                    <p>
                        Menambahkan fitur baru sesuai kebutuhan
                        pengguna dan perkembangan teknologi.
                    </p>
                </div>

            </div>
        </section>

        <!-- CONTOH PROJECT -->
        <section class="card" id="project">
            <h2>💻 Contoh Project RPL</h2>

            <div class="project">
                <h3>Sistem Informasi Perpustakaan</h3>

                <p>
                    Project ini merupakan contoh penerapan RPL
                    untuk membuat sistem yang membantu proses
                    pengelolaan data buku, anggota, peminjaman,
                    pengembalian, dan laporan perpustakaan.
                </p>
            </div>
        </section>

        <!-- KESIMPULAN -->
        <section class="card">
            <h2>📝 Kesimpulan</h2>

            <p>
                Rekayasa Perangkat Lunak sangat penting dalam
                pengembangan aplikasi karena membantu tim membuat
                perangkat lunak secara terencana dan sistematis.
                Dengan menerapkan konsep RPL, perangkat lunak
                dapat dikembangkan sesuai kebutuhan pengguna
                dan lebih mudah untuk dipelihara.
            </p>
        </section>

    </div>

    <!-- FOOTER -->
    <footer>
        <p>© 2026 | Rekayasa Perangkat Lunak</p>
    </footer>

</body>
</html>

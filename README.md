<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Undangan Pernikahan - Farid & Hanisa</title>
    <!-- Meta Tags untuk Preview WhatsApp -->
    <meta property="og:title" content="Undangan Pernikahan Farid & Hanisa">
    <meta property="og:description" content="Merupakan suatu kehormatan dan kebahagiaan bagi kami apabila Bapak/Ibu/Saudara/i berkenan hadir untuk memberikan doa restu.">
    <meta property="og:image" content="https://faridmaulana470-del.github.io/Farid-Hanisa/Gambar%201.png">
    <meta property="og:url" content="https://faridmaulana470-del.github.io/Farid-Hanisa/">
    <meta property="og:type" content="website">
    <style>
        /* CSS Styling Dasar */
        body, html {
            margin: 0;
            padding: 0;
            background-color: #f6efe9; /* Warna latar belakang senada dengan gambar */
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            scroll-behavior: smooth;
        }
        
        /* Container utama dibatasi lebarnya agar menyerupai tampilan HP/Buku */
        #invitation-container {
            max-width: 500px;
            margin: 0 auto;
            background-color: #fff;
            box-shadow: 0 0 20px rgba(0,0,0,0.15);
            display: none; /* Disembunyikan sampai tombol ditekan */
        }

        /* Styling untuk Gambar */
        .page-img {
            width: 100%;
            display: block;
            opacity: 0;
            transform: translateY(30px);
            transition: opacity 1s ease-out, transform 1s ease-out;
        }

        .page-img.visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* Halaman Sampul Depan (Overlay) */
        #cover-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('Gambar 1.png');
            background-size: cover;
            background-position: center;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 9999;
        }

        /* Latar belakang gelap agar teks dan tombol terbaca */
        .overlay-bg {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.6);
            z-index: 1;
        }

        .cover-content {
            z-index: 2;
            text-align: center;
            color: #fff;
        }

        .cover-content h1 {
            font-size: 2.5rem;
            margin-bottom: 5px;
            letter-spacing: 2px;
        }

        .cover-content p {
            font-size: 1.2rem;
            margin-bottom: 30px;
        }

        .btn-open {
            background-color: #a87b64;
            color: #fff;
            border: none;
            padding: 12px 30px;
            font-size: 16px;
            border-radius: 30px;
            cursor: pointer;
            box-shadow: 0 4px 10px rgba(0,0,0,0.3);
            transition: background-color 0.3s;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .btn-open:hover {
            background-color: #8a624d;
        }

        /* Tombol Kontrol Musik */
        #music-control {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background-color: rgba(168, 123, 100, 0.9);
            color: white;
            width: 45px;
            height: 45px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            z-index: 1000;
            display: none;
            box-shadow: 0 2px 10px rgba(0,0,0,0.2);
            font-size: 20px;
        }
    </style>
</head>
<body>

    <!-- Audio Player (Ganti src dengan nama file musik Anda) -->
    <audio id="bg-music" loop>
        <source src="musik.mp3" type="audio/mpeg">
    </audio>

    <!-- Halaman Pembuka -->
    <div id="cover-overlay">
        <div class="overlay-bg"></div>
        <div class="cover-content">
            <h1>Farid & Hanisa</h1>
            <p>29 Agustus 2026</p>
            <button class="btn-open" onclick="openInvitation()">Buka Undangan</button>
        </div>
    </div>

    <!-- Kontainer Gambar Undangan -->
    <div id="invitation-container">
        <img src="Gambar 1.png" alt="Halaman 1" class="page-img">
        <img src="Gambar 2.png" alt="Halaman 2" class="page-img">
        <img src="Gambar 3.png" alt="Halaman 3" class="page-img">
        <img src="Gambar 4.png" alt="Halaman 4" class="page-img">
        <img src="Gambar 5.png" alt="Halaman 5" class="page-img">
        <img src="Gambar 6.png" alt="Halaman 6" class="page-img">
        <img src="Gambar 7.png" alt="Halaman 7" class="page-img">
        <img src="Gambar 8.png" alt="Halaman 8" class="page-img">
    </div>

    <!-- Tombol Musik -->
    <div id="music-control" onclick="toggleMusic()">🎵</div>

    <script>
        // Fungsi untuk membuka undangan, menghilangkan cover, dan memutar musik
        function openInvitation() {
            document.getElementById('cover-overlay').style.display = 'none';
            document.getElementById('invitation-container').style.display = 'block';
            document.getElementById('music-control').style.display = 'flex';
            
            let music = document.getElementById('bg-music');
            music.play().catch(error => {
                console.log("Browser memblokir pemutaran otomatis:", error);
            });
            
            // Cek elemen yang terlihat saat pertama dibuka
            checkVisibility();
        }

        // Fungsi untuk play/pause musik
        function toggleMusic() {
            let music = document.getElementById('bg-music');
            let btn = document.getElementById('music-control');
            if (music.paused) {
                music.play();
                btn.style.opacity = "1";
            } else {
                music.pause();
                btn.style.opacity = "0.6";
            }
        }

        // Skrip untuk animasi fade-in saat di-scroll
        const images = document.querySelectorAll('.page-img');
        
        function checkVisibility() {
            const triggerBottom = window.innerHeight * 0.85; // Gambar muncul saat mencapai 85% layar
            images.forEach(img => {
                const imgTop = img.getBoundingClientRect().top;
                if(imgTop < triggerBottom) {
                    img.classList.add('visible');
                }
            });
        }

        window.addEventListener('scroll', checkVisibility);
    </script>
</body>
</html>

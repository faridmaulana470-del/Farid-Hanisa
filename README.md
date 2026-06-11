<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Undangan Pernikahan Farid & Hanisa</title>
    <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Montserrat:wght@300;400;600&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        :root {
            --primary-color: #d4af37;
            --bg-dark: #1a1a1a;
            --text-light: #ffffff;
            --text-dark: #333333;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; }
        body { font-family: 'Montserrat', sans-serif; background-color: #f9f9f9; color: var(--text-dark); overflow: hidden; }

        /* --- COVER OVERLAY --- */
        #cover {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            /* Memanggil file foto-cover.png yang Anda upload */
            background: linear-gradient(rgba(0,0,0,0.6), rgba(0,0,0,0.6)), url('foto-cover.png') no-repeat center center/cover;
            display: flex; flex-direction: column; justify-content: center; align-items: center;
            color: var(--text-light); z-index: 9999; text-align: center; transition: transform 1s ease-in-out; padding: 20px;
        }

        #cover.opened { transform: translateY(-100%); }
        .cover-title { font-family: 'Great Vibes', cursive; font-size: 3.5rem; color: var(--primary-color); margin-bottom: 10px; }
        .guest-box { background: rgba(255, 255, 255, 0.1); padding: 15px 25px; border-radius: 8px; backdrop-filter: blur(5px); margin: 20px 0; border: 1px solid rgba(255, 255, 255, 0.2); }
        .btn-open { background-color: var(--primary-color); color: white; border: none; padding: 12px 30px; font-size: 1rem; font-weight: 600; border-radius: 25px; cursor: pointer; box-shadow: 0 4px 15px rgba(0,0,0,0.2); transition: 0.3s; }

        /* --- MAIN CONTENT & MEMPELAI --- */
        .section { padding: 60px 20px; text-align: center; max-width: 800px; margin: 0 auto; }
        .mempelai-container { display: flex; justify-content: space-around; flex-wrap: wrap; margin: 40px 0; gap: 20px; }
        .mempelai-card { flex: 1; min-width: 250px; padding: 20px; }
        .mempelai-img { width: 150px; height: 150px; border-radius: 50%; object-fit: cover; border: 3px solid var(--primary-color); margin-bottom: 15px; }
        .mempelai-title { font-family: 'Great Vibes', cursive; font-size: 2.5rem; color: var(--primary-color); margin: 10px 0; }

        /* --- AUDIO CONTROLLER --- */
        #audio-control { position: fixed; bottom: 20px; right: 20px; background: var(--primary-color); color: white; width: 50px; height: 50px; border-radius: 50%; display: flex; justify-content: center; align-items: center; cursor: pointer; z-index: 1000; }
    </style>
</head>
<body>

    <audio id="bg-music" loop>
        <source src="audio-undangan.mp3" type="audio/mpeg">
    </audio>

    <div id="audio-control" onclick="toggleMusic()"><i id="audio-icon" class="fas fa-music"></i></div>

    <div id="cover">
        <p>UNDANGAN PERNIKAHAN</p>
        <h1 class="cover-title">Farid & Hanisa</h1>
        <div class="guest-box">
            <p style="font-size: 0.9rem; letter-spacing: 1px;">KEPADA YTH.</p>
            <h2 id="guest-name">-</h2>
        </div>
        <button class="btn-open" onclick="openInvitation()"><i class="fas fa-envelope-open-text"></i> Buka Undangan</button>
    </div>

    <main>
        <section class="section">
            <p style="font-style: italic; margin-bottom: 20px;">"Dan di antara tanda-tanda kekuasaan-Nya ialah Dia menciptakan untukmu isteri-isteri dari jenismu sendiri..."</p>
            
            <div class="mempelai-container">
                <div class="mempelai-card">
                    <img src="mempelai-pria.png" alt="Farid" class="mempelai-img">
                    <h2 class="mempelai-title">Farid</h2>
                    <p>Putra dari Bpk. X & Ibu Y</p>
                </div>
                <div class="mempelai-card">
                    <img src="mempelai-wanita.png" alt="Hanisa" class="mempelai-img">
                    <h2 class="mempelai-title">Hanisa</h2>
                    <p>Putri dari Bpk. A & Ibu B</p>
                </div>
            </div>
        </section>
    </main>

    <script>
        const urlParams = new URLSearchParams(window.location.search);
        const guest = urlParams.get('to');
        document.getElementById('guest-name').innerText = guest ? guest.replace(/\+/g, ' ') : "Tamu Undangan";

        const music = document.getElementById('bg-music');
        function openInvitation() {
            document.getElementById('cover').classList.add('opened');
            document.body.style.overflow = 'auto';
            music.play().catch(err => console.log("Autoplay blocked"));
        }

        function toggleMusic() {
            const icon = document.getElementById('audio-icon');
            if (music.paused) { music.play(); icon.className = "fas fa-music"; } 
            else { music.pause(); icon.className = "fas fa-pause"; }
        }
    </script>
</body>
</html>

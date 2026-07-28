<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Manchester United - Red Devils Era</title>
    <style>
        :root {
            --mu-red: #DA291C;
            --mu-dark-red: #990000;
            --mu-black: #111111;
            --mu-card-bg: #1c1c1c;
            --mu-gold: #FBE122;
            --mu-white: #ffffff;
            --mu-gray: #aaaaaa;
        }

        /* Light Mode overrides */
        body.light-mode {
            --mu-black: #f4f5f7;
            --mu-card-bg: #ffffff;
            --mu-white: #1a1a1a;
            --mu-gray: #555555;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--mu-black);
            color: var(--mu-white);
            overflow-x: hidden;
            transition: background-color 0.3s ease, color 0.3s ease;
        }

        /* Navbar */
        header {
            background-color: var(--mu-black);
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 5%;
            position: sticky;
            top: 0;
            z-index: 1000;
            border-bottom: 2px solid var(--mu-red);
            transition: background-color 0.3s ease;
        }

        .logo-container {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .logo-container img {
            height: 45px;
            width: auto;
        }

        .logo-container h1 {
            font-size: 1.2rem;
            color: var(--mu-white);
            font-weight: 800;
            letter-spacing: 1px;
        }

        .logo-container h1 span {
            color: var(--mu-red);
        }

        nav a {
            color: var(--mu-white);
            text-decoration: none;
            margin-left: 20px;
            font-weight: 600;
            transition: 0.3s;
        }

        nav a:hover {
            color: var(--mu-gold);
        }

        /* Hero Section */
        .hero {
            position: relative;
            background: linear-gradient(135deg, rgba(218, 41, 28, 0.2) 0%, rgba(17, 17, 17, 0.95) 100%);
            padding: 80px 5% 60px;
            text-align: center;
            border-bottom: 1px solid #333;
        }

        .hero-watermark {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 300px;
            opacity: 0.05;
            pointer-events: none;
        }

        .hero h2 {
            font-size: 2.8rem;
            color: var(--mu-gold);
            margin-bottom: 15px;
            text-transform: uppercase;
            letter-spacing: 2px;
            text-shadow: 0 0 10px rgba(251, 225, 34, 0.3);
        }

        .hero p {
            font-size: 1.1rem;
            color: var(--mu-gray);
            max-width: 600px;
            margin: 0 auto 30px;
        }

        .hero-btns {
            display: flex;
            justify-content: center;
            gap: 15px;
        }

        .btn {
            padding: 12px 24px;
            border-radius: 25px;
            font-weight: 700;
            text-decoration: none;
            cursor: pointer;
            transition: 0.3s;
            border: none;
            display: inline-block;
        }

        .btn-primary {
            background-color: var(--mu-red);
            color: var(--mu-white);
        }

        .btn-primary:hover {
            background-color: var(--mu-dark-red);
            transform: translateY(-2px);
        }

        .btn-secondary {
            background-color: transparent;
            color: var(--mu-gold);
            border: 2px solid var(--mu-gold);
        }

        .btn-secondary:hover {
            background-color: var(--mu-gold);
            color: var(--mu-black);
            transform: translateY(-2px);
        }

        /* Section Commons */
        section {
            padding: 60px 5%;
        }

        .section-title {
            text-align: center;
            font-size: 2rem;
            margin-bottom: 30px;
            text-transform: uppercase;
            color: var(--mu-white);
            position: relative;
        }

        .section-title::after {
            content: '';
            display: block;
            width: 60px;
            height: 3px;
            background-color: var(--mu-red);
            margin: 10px auto 0;
        }

        /* Filter Controls */
        .filter-container {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-bottom: 30px;
            flex-wrap: wrap;
        }

        .filter-btn {
            background-color: var(--mu-card-bg);
            color: var(--mu-white);
            border: 1px solid #333;
            padding: 8px 16px;
            border-radius: 20px;
            cursor: pointer;
            transition: 0.3s;
            font-size: 0.95rem;
        }

        .filter-btn:focus-visible,
        .btn:focus-visible {
            outline: 2px solid var(--mu-gold);
            outline-offset: 2px;
        }

        .filter-btn.active, .filter-btn:hover {
            background-color: var(--mu-red);
            border-color: var(--mu-red);
        }

        /* Skuad Grid */
        .squad-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
            gap: 20px;
        }

        .player-card {
            background-color: var(--mu-card-bg);
            border-radius: 12px;
            overflow: hidden;
            border: 1px solid #2a2a2a;
            transition: 0.3s;
            text-align: center;
            position: relative;
        }

        .player-card:hover {
            transform: translateY(-5px);
            border-color: var(--mu-red);
            box-shadow: 0 5px 15px rgba(218, 41, 28, 0.3);
        }

        .player-img-wrapper {
            width: 100%;
            height: 240px;
            background: linear-gradient(to bottom, #2b2b2b, #1c1c1c);
            overflow: hidden;
            display: flex;
            align-items: flex-end;
            justify-content: center;
        }

        .player-img-wrapper img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            object-position: top center;
            transition: 0.3s;
        }

        .player-card:hover .player-img-wrapper img {
            transform: scale(1.05);
        }

        .player-info {
            padding: 15px;
        }

        .player-name {
            font-size: 1.1rem;
            font-weight: 700;
            color: var(--mu-white);
            margin-bottom: 5px;
        }

        .player-pos {
            font-size: 0.85rem;
            color: var(--mu-gold);
            text-transform: uppercase;
            font-weight: 600;
        }

        /* Honours / Prestasi */
        .honours-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
            gap: 20px;
        }

        .honour-card {
            background-color: var(--mu-card-bg);
            border: 1px solid #2a2a2a;
            border-top: 4px solid var(--mu-red);
            border-radius: 8px;
            padding: 20px;
            text-align: center;
            transition: 0.3s;
        }

        .honour-card:hover {
            border-top-color: var(--mu-gold);
            background-color: #252525;
        }

        .honour-count {
            font-size: 2.5rem;
            font-weight: 800;
            color: var(--mu-gold);
        }

        .honour-title {
            font-size: 0.9rem;
            color: var(--mu-gray);
            margin-top: 5px;
            font-weight: 600;
        }

        /* Chant Interactive Box */
        .chant-box {
            background: linear-gradient(90deg, #1f0504 0%, #111111 100%);
            border: 1px solid var(--mu-red);
            border-radius: 12px;
            padding: 30px;
            text-align: center;
            margin-top: 40px;
        }

        /* Footer */
        footer {
            background-color: var(--mu-black);
            text-align: center;
            padding: 30px 5%;
            border-top: 1px solid #222;
            transition: background-color 0.3s ease;
        }

        .quote {
            font-style: italic;
            color: var(--mu-gold);
            margin-bottom: 15px;
        }

        .copyright {
            font-size: 0.8rem;
            color: var(--mu-gray);
        }

        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.8);
            justify-content: center;
            align-items: center;
            z-index: 2000;
        }

        .modal-content {
            background: var(--mu-card-bg);
            padding: 30px;
            border-radius: 10px;
            border: 2px solid var(--mu-red);
            max-width: 400px;
            text-align: center;
            position: relative;
        }

        .close-btn {
            position: absolute;
            top: 10px; right: 15px;
            color: white; font-size: 1.5rem;
            cursor: pointer;
            background: none;
            border: none;
            line-height: 1;
        }

        @media (max-width: 480px) {
            .hero h2 { font-size: 2rem; }
            .hero-btns { flex-direction: column; align-items: center; }
        }

        @media (prefers-reduced-motion: reduce) {
            * { transition: none !important; }
        }

        /* Stats Modal (scoped so it doesn't clash with the chant modal) */
        #statsModal.modal {
            backdrop-filter: blur(5px);
        }

        #statsModal .modal-content {
            background: var(--mu-card-bg);
            padding: 24px;
            border-radius: 16px;
            width: 90%;
            max-width: 380px;
            border: 1px solid #2a2a32;
            box-shadow: 0 10px 25px rgba(0,0,0,0.5);
            animation: popup 0.3s ease-out;
        }

        @keyframes popup {
            from { transform: scale(0.8); opacity: 0; }
            to { transform: scale(1); opacity: 1; }
        }

        #statsModal img {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid var(--mu-red);
            margin-bottom: 12px;
        }

        .role-badge {
            display: inline-block;
            background: var(--mu-red);
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 12px;
            margin-bottom: 16px;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 12px;
        }

        .stat-box {
            background: #2a2a32;
            padding: 12px;
            border-radius: 10px;
        }

        .stat-value {
            display: block;
            font-size: 20px;
            font-weight: bold;
            color: var(--mu-gold);
        }

        .stat-label {
            font-size: 12px;
            color: #ccc;
        }

        .player-card {
            cursor: pointer;
        }

        /* Theme Toggle Button */
        .theme-btn {
            background-color: var(--mu-card-bg);
            color: var(--mu-white);
            border: 2px solid var(--mu-red);
            padding: 8px 16px;
            border-radius: 20px;
            cursor: pointer;
            font-weight: bold;
            font-size: 0.85rem;
            margin-left: 15px;
            transition: all 0.3s ease;
        }

        .theme-btn:hover {
            background-color: var(--mu-red);
            color: #fff;
        }
    </style>
</head>
<body>

    <!-- Header / Navbar -->
    <header>
        <div class="logo-container">
            <img src="https://upload.wikimedia.org/wikipedia/en/7/7a/Manchester_United_FC_crest.svg" alt="Manchester United Crest">
            <h1>MANCHESTER <span>UNITED</span></h1>
        </div>
        <nav>
            <a href="#squad">Skuad</a>
            <a href="#honours">Prestasi</a>
            <a href="#chant">Chant</a>
            <button id="themeToggle" class="theme-btn" onclick="toggleTheme()">🌙 Mode Gelap</button>
        </nav>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <img src="https://upload.wikimedia.org/wikipedia/en/7/7a/Manchester_United_FC_crest.svg" class="hero-watermark" alt="" aria-hidden="true">
        <h2>THE RED DEVILS ERA</h2>
        <p>United We Stand. Menyongsong masa depan penuh kejayaan bersama pilar-pilar baru dan tradisi pantang menyerah.</p>
        <div class="hero-btns">
            <a href="#squad" class="btn btn-primary">Lihat Skuad Utama</a>
            <a href="#honours" class="btn btn-secondary">Museum Prestasi</a>
        </div>
    </section>

    <!-- Section Skuad -->
    <section id="squad">
        <h3 class="section-title">Skuad Utama</h3>

        <div class="filter-container" role="group" aria-label="Filter posisi pemain">
            <button class="filter-btn active" data-filter="all">Semua</button>
            <button class="filter-btn" data-filter="gk">Kiper</button>
            <button class="filter-btn" data-filter="df">Bek</button>
            <button class="filter-btn" data-filter="mf">Gelandang</button>
            <button class="filter-btn" data-filter="fw">Penyerang</button>
        </div>

        <div class="squad-grid" id="squadGrid">
            <!-- Player Cards generated via JS -->
        </div>
    </section>

    <!-- Section Prestasi -->
    <section id="honours">
        <h3 class="section-title">Rekor & Kejayaan</h3>
        <div class="honours-grid">
            <div class="honour-card">
                <div class="honour-count">20</div>
                <div class="honour-title">Liga Inggris</div>
            </div>
            <div class="honour-card">
                <div class="honour-count">13</div>
                <div class="honour-title">FA Cup</div>
            </div>
            <div class="honour-card">
                <div class="honour-count">6</div>
                <div class="honour-title">EFL League Cup</div>
            </div>
            <div class="honour-card">
                <div class="honour-count">3</div>
                <div class="honour-title">UEFA Champions League</div>
            </div>
            <div class="honour-card">
                <div class="honour-count">1</div>
                <div class="honour-title">UEFA Europa League</div>
            </div>
            <div class="honour-card">
                <div class="honour-count">1</div>
                <div class="honour-title">UEFA Cup Winners' Cup</div>
            </div>
        </div>
    </section>

    <!-- Section Interactive Chant -->
    <section id="chant">
        <div class="chant-box">
            <h3 style="color: var(--mu-gold); margin-bottom: 10px;">Nyanyikan Semangat Red Devils!</h3>
            <p style="color: var(--mu-gray); margin-bottom: 20px;">Dengarkan dan pelajari chant legendaris Manchester United.</p>
            <button class="btn btn-primary" id="openChantBtn">🎵 Play Chant Lyrics</button>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <p class="quote">"Never give up, that's the United way." - Sir Alex Ferguson</p>
        <p class="copyright">&copy; GGMU Promo Page - Built for Red Devils Fanbase.</p>
        <p class="copyright">Created By: @Cooolz_boyy</p>
    </footer>

    <!-- Chant Modal -->
    <div class="modal" id="chantModal" role="dialog" aria-modal="true" aria-labelledby="chantTitle">
        <div class="modal-content">
            <button class="close-btn" id="closeChantBtn" aria-label="Tutup">&times;</button>
            <h3 id="chantTitle" style="color: var(--mu-gold); margin-bottom: 15px;">Glory Glory Manchester United</h3>
            <p style="line-height: 1.6; color: #ddd;">
                Glory, glory, Man United,<br>
                Glory, glory, Man United,<br>
                Glory, glory, Man United,<br>
                As the reds go marching on, on, on!
            </p>
        </div>
    </div>

    <!-- Pop-up Modal Statistik -->
    <div id="statsModal" class="modal">
        <div class="modal-content">
            <button class="close-btn" onclick="closeStatsModal()" aria-label="Tutup">&times;</button>
            <img id="modalImg" src="" alt="Foto Pemain">
            <h2 id="modalName">Nama Pemain</h2>
            <p id="modalRole" class="role-badge">Role</p>

            <div class="stats-grid">
                <div class="stat-box">
                    <span class="stat-value" id="statApp">0</span>
                    <span class="stat-label">Main</span>
                </div>
                <div class="stat-box">
                    <span class="stat-value" id="statGoal">0</span>
                    <span class="stat-label">Gol / CS</span>
                </div>
                <div class="stat-box">
                    <span class="stat-value" id="statAssist">0</span>
                    <span class="stat-label">Assist / Tackle</span>
                </div>
                <div class="stat-box">
                    <span class="stat-value" id="statRating">0.0</span>
                    <span class="stat-label">Rating</span>
                </div>
            </div>
        </div>
    </div>

    <script>
        const players = [
            { name: "Senne Lammens", pos: "gk", role: "Kiper", img: "https://ichef.bbci.co.uk/ace/standard/2560/cpsprodpb/2a9e/live/3eec98d0-b64f-11f0-ba64-f52e2f7918c2.jpg", stats: { app: 32, cleanSheets: 8, tackles: 0, rating: "7.11" } },
            { name: "Matthijs de Ligt", pos: "df", role: "Center Back", img: "https://img.allfootballapp.com/www1/M00/01/A9/720x-/-/-/rBAAN2iti4CASAVlAAFC6r8SVm4568.jpg.webp", stats: { app: 13, cleanSheets: 1, tackles: 19, rating: "6.80" } },
            { name: "Leny Yoro", pos: "df", role: "Center Back", img: "https://assets.goal.com/images/v3/blt06325d0378004df6/GettyImages-2162800058.jpg?auto=webp&format=pjpg&width=3840&quality=60", stats: { app: 31, cleanSheets: 5, tackles: 22, rating: "6.60" } },
            { name: "Kobbie Mainoo", pos: "mf", role: "Gelandang", img: "https://akcdn.detik.net.id/community/media/visual/2025/08/25/kobbie-mainoo-1756138432397.jpeg?w=600&q=90", stats: { app: 28, goals: 1, assists: 2, rating: "7.01" } },
            { name: "Bruno Fernandes", pos: "mf", role: "Kapten & Gelandang", img: "https://cdn.antaranews.com/cache/1200x800/2025/06/03/bruno.jpeg.webp", stats: { app: 35, goals: 9, assists: 21, rating: "8.03" } },
            { name: "Bryan Mbeumo", pos: "fw", role: "Winger Kanan", img: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR2O90gjkHFuzl3_G0FhyIpepgeLDxsYYd7ZpJDKnUQysnD1mTIAf75YPE1&s=10", stats: { app: 33, goals: 11, assists: 3, rating: "7.19" } },
            { name: "Matheus Cunha", pos: "fw", role: "Penyerang / Striker", img: "https://asset.tribunnews.com/vSNiMduJiwsdRfe6s6jpuQz5HJQ=/1200x675/filters:upscale():quality(30):format(webp):focal(0.5x0.5:0.5x0.5)/tribunnews/foto/bank/originals/Matheus-Cunha-tersenyum-saat-sesi-foto-di-Old-Trafford.jpg", stats: { app: 33, goals: 10, assists: 2, rating: "7.29" } },
            { name: "Benjamin Šeško", pos: "fw", role: "Striker Utama", img: "https://cdn.antaranews.com/cache/1200x800/2026/03/27/IMG_20260327_191531.jpg.jpeg", stats: { app: 30, goals: 11, assists: 1, rating: "7.05" } },
            { name: "Joshua Zirkzee", pos: "fw", role: "Penyerang", img: "https://cms.disway.id/uploads/dfb8424a2d59ed7535b1f1007aaa347d.jpg", stats: { app: 22, goals: 2, assists: 1, rating: "6.50" } },
            { name: "Amad Diallo", pos: "fw", role: "Winger", img: "https://blue.kumparan.com/image/upload/fl_progressive,fl_lossy,c_fill,f_auto,q_auto:best,w_640/v1634025439/01jhv6pfbzwzdk3ahyk1rdb0e3.jpg", stats: { app: 32, goals: 2, assists: 3, rating: "7.19" } }
        ];

        function avatarUrl(name) {
            return `https://ui-avatars.com/api/?name=${encodeURIComponent(name)}&background=DA291C&color=FBE122&size=250&bold=true&font-size=0.4`;
        }

        function renderSquad(filter) {
            const grid = document.getElementById('squadGrid');
            grid.innerHTML = '';

            const filtered = filter === 'all' ? players : players.filter(p => p.pos === filter);

            filtered.forEach(p => {
                const realIndex = players.indexOf(p);
                const card = document.createElement('div');
                card.className = 'player-card';
                card.onclick = () => showStats(realIndex);
                card.innerHTML = `
                    <div class="player-img-wrapper">
                        <img src="${p.img || avatarUrl(p.name)}" alt="${p.name}" loading="lazy" onerror="this.onerror=null; this.src='${avatarUrl(p.name)}';">
                    </div>
                    <div class="player-info">
                        <div class="player-name">${p.name}</div>
                        <div class="player-pos">${p.role}</div>
                    </div>
                `;
                grid.appendChild(card);
            });
        }

        document.querySelectorAll('.filter-btn').forEach(btn => {
            btn.addEventListener('click', () => {
                document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
                btn.classList.add('active');
                renderSquad(btn.dataset.filter);
            });
        });

        function openChantModal() {
            document.getElementById('chantModal').style.display = 'flex';
        }

        function closeChantModal() {
            document.getElementById('chantModal').style.display = 'none';
        }

        document.getElementById('openChantBtn').addEventListener('click', openChantModal);
        document.getElementById('closeChantBtn').addEventListener('click', closeChantModal);
        document.getElementById('chantModal').addEventListener('click', (e) => {
            if (e.target.id === 'chantModal') closeChantModal();
        });
        document.addEventListener('keydown', (e) => {
            if (e.key === 'Escape') closeChantModal();
        });

        // Fungsi untuk membuka pop-up statistik pemain
        function showStats(index) {
            const player = players[index];

            document.getElementById("modalImg").src = player.img || avatarUrl(player.name);
            document.getElementById("modalName").innerText = player.name;
            document.getElementById("modalRole").innerText = player.role;

            document.getElementById("statApp").innerText = player.stats.app || 0;
            document.getElementById("statGoal").innerText = player.stats.goals ?? player.stats.cleanSheets ?? 0;
            document.getElementById("statAssist").innerText = player.stats.assists ?? player.stats.tackles ?? 0;
            document.getElementById("statRating").innerText = player.stats.rating || "0.0";

            document.getElementById("statsModal").style.display = "flex";
        }

        // Fungsi menutup pop-up statistik
        function closeStatsModal() {
            document.getElementById("statsModal").style.display = "none";
        }

        // Tutup pop-up statistik jika user klik di luar kotak modal
        document.getElementById("statsModal").addEventListener('click', (e) => {
            if (e.target.id === 'statsModal') closeStatsModal();
        });
        document.addEventListener('keydown', (e) => {
            if (e.key === 'Escape') closeStatsModal();
        });

        // Fungsi untuk ganti tema
        function toggleTheme() {
            const body = document.body;
            const btn = document.getElementById("themeToggle");

            body.classList.toggle("light-mode");

            if (body.classList.contains("light-mode")) {
                btn.innerHTML = "☀️ Mode Terang";
                localStorage.setItem("theme", "light");
            } else {
                btn.innerHTML = "🌙 Mode Gelap";
                localStorage.setItem("theme", "dark");
            }
        }

        // Cek pilihan tema terakhir saat web pertama kali dibuka
        window.addEventListener("DOMContentLoaded", () => {
            const savedTheme = localStorage.getItem("theme");
            const btn = document.getElementById("themeToggle");

            if (savedTheme === "light") {
                document.body.classList.add("light-mode");
                if (btn) btn.innerHTML = "☀️ Mode Terang";
            }
        });

        // Initial Load
        renderSquad('all');
    </script>
</body>
</html>

</body>
</html>

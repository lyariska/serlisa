<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portal Sastra Serli SA</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700;900&family=Crimson+Text:wght@400;600&display=swap');

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Crimson Text', serif;
            background: #f8f5f0;
            color: #2c2416;
            min-height: 100vh;
            -webkit-user-select: none;
            -moz-user-select: none;
            -ms-user-select: none;
            user-select: none;
            background-image: 
                radial-gradient(circle at 20% 50%, rgba(212, 175, 55, 0.03) 0%, transparent 50%),
                radial-gradient(circle at 80% 80%, rgba(139, 90, 43, 0.03) 0%, transparent 50%);
        }

        .protected-content {
            -webkit-user-select: none;
            -moz-user-select: none;
            -ms-user-select: none;
            user-select: none;
            pointer-events: auto;
        }

        header {
            background: linear-gradient(to bottom, #2c2416, #3d3026);
            padding: 4rem 2rem;
            text-align: center;
            box-shadow: 0 4px 12px rgba(0,0,0,0.15);
            border-bottom: 4px solid #8b5a2b;
            position: relative;
        }

        header::after {
            content: '';
            position: absolute;
            bottom: -4px;
            left: 50%;
            transform: translateX(-50%);
            width: 200px;
            height: 4px;
            background: #d4af37;
        }

        header h1 {
            font-family: 'Playfair Display', serif;
            color: #d4af37;
            font-size: 4rem;
            margin-bottom: 1.5rem;
            letter-spacing: 4px;
            font-weight: 900;
            text-shadow: 3px 3px 6px rgba(0, 0, 0, 0.5);
        }

        header p {
            color: #e8dcc8;
            font-style: italic;
            font-size: 1.4rem;
            letter-spacing: 1px;
        }

        nav {
            background: #3d3026;
            padding: 0;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
            position: sticky;
            top: 0;
            z-index: 100;
            border-bottom: 2px solid #8b5a2b;
        }

        nav ul {
            list-style: none;
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            max-width: 1200px;
            margin: 0 auto;
        }

        nav button {
            background: transparent;
            color: #d4af37;
            border: none;
            border-bottom: 3px solid transparent;
            padding: 1.5rem 2.5rem;
            cursor: pointer;
            font-size: 1.1rem;
            font-family: 'Crimson Text', serif;
            font-weight: 600;
            transition: all 0.3s ease;
            letter-spacing: 2px;
            text-transform: uppercase;
        }

        nav button:hover, nav button.active {
            background: rgba(212, 175, 55, 0.1);
            border-bottom-color: #d4af37;
            color: #f8f5f0;
        }

        .container {
            max-width: 900px;
            margin: 4rem auto;
            padding: 4rem;
            background: #ffffff;
            box-shadow: 
                0 0 0 1px #e8dcc8,
                0 10px 40px rgba(0, 0, 0, 0.1);
        }

        .page {
            display: none;
        }

        .page.active {
            display: block;
            animation: fadeIn 0.6s ease;
        }

        @keyframes fadeIn {
            from { 
                opacity: 0; 
                transform: translateY(20px); 
            }
            to { 
                opacity: 1; 
                transform: translateY(0); 
            }
        }

        h2 {
            font-family: 'Playfair Display', serif;
            color: #2c2416;
            text-align: center;
            padding-bottom: 1rem;
            margin-bottom: 3rem;
            font-size: 2.8rem;
            letter-spacing: 2px;
            font-weight: 700;
            position: relative;
        }

        h2::after {
            content: '❦';
            display: block;
            color: #8b5a2b;
            font-size: 1.5rem;
            margin-top: 1rem;
        }

        .welcome {
            text-align: center;
            padding: 2rem 0;
        }

        .welcome p {
            font-size: 1.3rem;
            line-height: 2.2;
            color: #4a3f2f;
            margin: 1.5rem 0;
            text-align: justify;
        }

        /* Daftar karya dengan style minimalis */
        .karya-list {
            margin-top: 3rem;
        }

        .karya-item {
            padding: 2.5rem 0;
            border-bottom: 1px solid #e8dcc8;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .karya-item:last-child {
            border-bottom: none;
        }

        .karya-item:hover {
            padding-left: 1rem;
            background: #fdfcfa;
        }

        .karya-item h3 {
            font-family: 'Playfair Display', serif;
            color: #2c2416;
            font-size: 1.8rem;
            margin-bottom: 0.8rem;
            font-weight: 700;
            letter-spacing: 1px;
        }

        .karya-item p {
            color: #6d5d4b;
            font-size: 1.1rem;
            line-height: 1.8;
            font-style: italic;
        }

        .karya-item:hover h3 {
            color: #8b5a2b;
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(44, 36, 22, 0.95);
            z-index: 1000;
            overflow-y: auto;
        }

        .modal.active {
            display: flex;
            align-items: center;
            justify-content: center;
            animation: fadeIn 0.4s;
        }

        .modal-content {
            background: #ffffff;
            max-width: 800px;
            width: 90%;
            margin: 2rem;
            padding: 4rem;
            position: relative;
            max-height: 85vh;
            overflow-y: auto;
            box-shadow: 
                0 0 0 1px #e8dcc8,
                0 20px 60px rgba(0, 0, 0, 0.3);
        }

        .close-modal {
            position: absolute;
            top: 2rem;
            right: 2rem;
            background: transparent;
            color: #8b5a2b;
            border: 2px solid #8b5a2b;
            padding: 0.8rem 1.5rem;
            cursor: pointer;
            font-size: 1rem;
            font-family: 'Crimson Text', serif;
            font-weight: 600;
            transition: all 0.3s;
            letter-spacing: 1px;
            text-transform: uppercase;
        }

        .close-modal:hover {
            background: #8b5a2b;
            color: #ffffff;
        }

        .modal-content h3 {
            font-family: 'Playfair Display', serif;
            color: #2c2416;
            margin-bottom: 2rem;
            font-size: 2.5rem;
            padding-right: 5rem;
            letter-spacing: 1px;
            font-weight: 700;
            text-align: center;
        }

        .modal-content h3::after {
            content: '❦';
            display: block;
            color: #8b5a2b;
            font-size: 1.3rem;
            margin-top: 1rem;
        }

        .modal-content .content-text {
            color: #2c2416;
            line-height: 2.2;
            font-size: 1.25rem;
            white-space: pre-wrap;
            margin-top: 2rem;
            text-align: justify;
        }

        .tentang-section {
            padding: 2rem 0;
            text-align: center;
        }

        .tentang-section p {
            font-size: 1.3rem;
            line-height: 2;
            color: #4a3f2f;
            margin: 1rem 0;
        }

        .tentang-section strong {
            color: #8b5a2b;
            font-size: 1.8rem;
            letter-spacing: 2px;
            font-family: 'Playfair Display', serif;
        }

        .saweran-section {
            text-align: center;
            padding: 2rem 0;
        }

        .saweran-section p {
            font-size: 1.3rem;
            line-height: 2;
            color: #4a3f2f;
            margin: 2rem 0;
            text-align: justify;
        }

        .saweria-btn {
            display: inline-block;
            background: #8b5a2b;
            color: #ffffff;
            padding: 1.5rem 4rem;
            text-decoration: none;
            font-size: 1.3rem;
            font-weight: 600;
            margin: 3rem 0;
            transition: all 0.3s;
            border: 2px solid #8b5a2b;
            letter-spacing: 2px;
            text-transform: uppercase;
            font-family: 'Crimson Text', serif;
        }

        .saweria-btn:hover {
            background: #6d4821;
            border-color: #6d4821;
            box-shadow: 0 5px 20px rgba(139, 90, 43, 0.3);
            transform: translateY(-2px);
        }

        .divider {
            width: 100px;
            height: 2px;
            background: #8b5a2b;
            margin: 3rem auto;
            position: relative;
        }

        .divider::before,
        .divider::after {
            content: '◆';
            position: absolute;
            color: #8b5a2b;
            font-size: 0.8rem;
            top: 50%;
            transform: translateY(-50%);
        }

        .divider::before {
            left: -20px;
        }

        .divider::after {
            right: -20px;
        }

        @media (max-width: 768px) {
            header h1 {
                font-size: 2.5rem;
            }

            nav ul {
                flex-direction: column;
            }

            nav button {
                width: 100%;
                text-align: center;
                border-bottom: 1px solid rgba(212, 175, 55, 0.2);
            }

            .container {
                margin: 2rem 1rem;
                padding: 2rem;
            }

            h2 {
                font-size: 2rem;
            }

            .modal-content {
                padding: 2.5rem 1.5rem;
            }

            .modal-content h3 {
                font-size: 1.8rem;
                padding-right: 3rem;
            }

            .welcome p,
            .tentang-section p,
            .saweran-section p {
                text-align: left;
            }
        }

        ::-webkit-scrollbar {
            width: 10px;
        }

        ::-webkit-scrollbar-track {
            background: #f8f5f0;
        }

        ::-webkit-scrollbar-thumb {
            background: #8b5a2b;
            border-radius: 5px;
        }

        ::-webkit-scrollbar-thumb:hover {
            background: #6d4821;
        }
    </style>
</head>
<body>
    <script>
        document.addEventListener('contextmenu', event => event.preventDefault());
        document.addEventListener('keydown', function(e) {
            if (e.keyCode == 123 || 
                (e.ctrlKey && e.shiftKey && e.keyCode == 73) ||
                (e.ctrlKey && e.shiftKey && e.keyCode == 67) ||
                (e.ctrlKey && e.keyCode == 85)) {
                e.preventDefault();
                return false;
            }
        });
    </script>

    <header>
        <h1>Portal Sastra Serli SA</h1>
        <p>"Menulis adalah Merawat Jiwa dengan Kata"</p>
    </header>

    <nav>
        <ul>
            <li><button onclick="showPage('home')" class="active">Home</button></li>
            <li><button onclick="showPage('cerpen')">Cerpen</button></li>
            <li><button onclick="showPage('puisi')">Puisi</button></li>
            <li><button onclick="showPage('tentang')">Tentang</button></li>
            <li><button onclick="showPage('saweran')">Saweran</button></li>
        </ul>
    </nav>

    <div class="container">
        <!-- HOME PAGE -->
        <div id="home" class="page active">
            <div class="welcome">
                <h2>Selamat Datang</h2>
                <p>Portal ini adalah ruang berbagi karya sastra berupa cerpen dan puisi karya Serli SA. Setiap karya yang tersaji di sini adalah serpihan jiwa yang dituangkan dalam untaian kata, lahir dari pergulatan pemikiran dan perasaan yang mendalam.</p>
                <div class="divider"></div>
                <p style="font-style: italic; color: #8b5a2b; font-size: 1.4rem;">
                    "Setiap karya adalah jejak jiwa yang tertulis"
                </p>
            </div>
        </div>

        <!-- CERPEN PAGE -->
        <div id="cerpen" class="page">
            <h2>Kumpulan Cerpen</h2>
            <div class="karya-list">
                <div class="karya-item protected-content" onclick="openModal('cerpen1')">
                    <h3>Hujan di Sore Hari</h3>
                    <p>Sebuah kisah tentang kenangan masa lalu yang terus hidup dalam ingatan, diiringi alunan tetes hujan yang tak pernah berhenti...</p>
                </div>
                <div class="karya-item protected-content" onclick="openModal('cerpen2')">
                    <h3>Jejak Langkah</h3>
                    <p>Perjalanan panjang seorang jiwa yang mencari makna, meninggalkan zona nyaman demi menemukan jati diri sejati...</p>
                </div>
                <div class="karya-item protected-content" onclick="openModal('cerpen3')">
                    <h3>Cahaya di Ujung Jalan</h3>
                    <p>Tentang harapan yang tak pernah padam, meski jalan yang dilalui gelap dan penuh lika-liku kehidupan...</p>
                </div>
            </div>
        </div>

        <!-- PUISI PAGE -->
        <div id="puisi" class="page">
            <h2>Kumpulan Puisi</h2>
            <div class="karya-list">
                <div class="karya-item protected-content" onclick="openModal('puisi1')">
                    <h3>Rindu yang Terpendam</h3>
                    <p>Puisi tentang kerinduan yang tak terucap, tersimpan dalam diam...</p>
                </div>
                <div class="karya-item protected-content" onclick="openModal('puisi2')">
                    <h3>Sepotong Senja</h3>
                    <p>Keindahan senja yang fana, dalam untaian kata yang abadi...</p>
                </div>
                <div class="karya-item protected-content" onclick="openModal('puisi3')">
                    <h3>Pelukis Mimpi</h3>
                    <p>Tentang mimpi yang terus diperjuangkan meski badai menghadang...</p>
                </div>
                <div class="karya-item protected-content" onclick="openModal('puisi4')">
                    <h3>Bintang Malam</h3>
                    <p>Harapan kecil yang bersinar terang di tengah kegelapan...</p>
                </div>
            </div>
        </div>

        <!-- TENTANG PAGE -->
        <div id="tentang" class="page">
            <div class="tentang-section">
                <h2>Tentang Penulis</h2>
                <p><strong>Serli SA</strong></p>
                <p>📅 Lahir: 20 Desember 2004</p>
                <p>📍 Menetap di Palangka Raya</p>
                <p>✍️ Menempuh sastra sejak kelas 3 MTs</p>
                <div class="divider"></div>
                <p style="margin-top: 2rem; line-height: 2.2; text-align: justify;">
                    Menulis bagi saya adalah cara untuk mendengar suara jiwa. Setiap kata yang tertulis adalah jejak perjalanan hidup, pengalaman, dan perasaan yang ingin saya bagikan kepada dunia. Sejak menempuh pendidikan sastra dari kelas 3 MTs, saya percaya bahwa setiap kata memiliki kekuatan untuk menyembuhkan, menginspirasi, dan menghubungkan jiwa-jiwa yang terpisah oleh jarak dan waktu.
                </p>
            </div>
        </div>

        <!-- SAWERAN PAGE -->
        <div id="saweran" class="page">
            <div class="saweran-section">
                <h2>Dukung Karya Saya</h2>
                <p>Jika karya-karya saya berkenan di hati Anda dan ingin mendukung perjalanan saya dalam menulis, Anda dapat memberikan dukungan melalui platform Saweria.</p>
                <p style="font-style: italic;">Setiap dukungan sangat berarti dan akan terus menyemangati saya untuk berkarya lebih baik lagi.</p>
                <a href="https://saweria.co/serlisa20" target="_blank" class="saweria-btn">
                    💝 Sawer via Saweria
                </a>
                <div class="divider"></div>
                <p style="margin-top: 2rem; color: #8b5a2b; font-size: 1.3rem; text-align: center;">Terima kasih atas dukungan dan apresiasi Anda! 🙏</p>
            </div>
        </div>
    </div>

    <!-- MODAL -->
    <div id="modal" class="modal">
        <div class="modal-content protected-content">
            <button class="close-modal" onclick="closeModal()">✕ Tutup</button>
            <h3 id="modalTitle"></h3>
            <div class="content-text" id="modalContent"></div>
        </div>
    </div>

    <script>
        function showPage(pageId) {
            document.querySelectorAll('.page').forEach(page => {
                page.classList.remove('active');
            });
            
            document.getElementById(pageId).classList.add('active');
            
            document.querySelectorAll('nav button').forEach(btn => {
                btn.classList.remove('active');
            });
            event.target.classList.add('active');
        }

        function openModal(contentId) {
            const modal = document.getElementById('modal');
            const title = document.getElementById('modalTitle');
            const content = document.getElementById('modalContent');
            
            const contents = {
                'cerpen1': {
                    title: 'Hujan di Sore Hari',
                    text: `Hujan turun membasahi jalanan kota. Aku duduk di teras rumah tua ini, mengingat wajahmu yang selalu tersenyum. 

Sore itu, tepat lima tahun yang lalu, kita berjanji akan bertemu lagi di tempat ini. Tapi takdir berkata lain. Kau pergi meninggalkan jejak kenangan yang tak pernah pudar.

Setiap tetes hujan mengingatkanku pada tawa renyahmu. Setiap guntur mengingatkanku pada suaramu yang lantang. Dan di sore ini, aku kembali menunggu, berharap keajaiban akan membawamu pulang.

Namun hujan terus turun, dan aku tahu, beberapa kenangan memang harus tetap menjadi kenangan.

— Serli SA —`
                },
                'cerpen2': {
                    title: 'Jejak Langkah',
                    text: `Langkahku terus melaju di jalan setapak ini. Tidak ada yang tahu ke mana aku akan pergi, bahkan diriku sendiri.

Perjalanan ini dimulai ketika aku memutuskan untuk meninggalkan zona nyaman. Banyak yang mengatakan aku gila, melepaskan segala yang sudah pasti demi sesuatu yang belum tentu.

Tapi bukankah hidup ini tentang mencari makna? Tentang menjelajah dan menemukan siapa diri kita sebenarnya?

Di setiap langkah, aku belajar. Di setiap pertemuan, aku tumbuh. Dan di setiap perpisahan, aku mengerti bahwa tidak semua yang kita cintai bisa kita miliki.

Jejak langkahku mungkin akan terhapus oleh waktu, tapi kenangan dan pelajaran yang kudapat akan tetap abadi.

— Serli SA —`
                },
                'cerpen3': {
                    title: 'Cahaya di Ujung Jalan',
                    text: `Jalan ini gelap dan panjang. Berkali-kali aku tersandung, jatuh, dan meragukan pilihan yang telah kubuat.

Ada masanya aku ingin menyerah, berbalik arah, dan kembali ke tempat yang aman. Tapi sesuatu dalam diriku terus berbisik, "Teruslah melangkah."

Dan malam ini, setelah perjalanan yang melelahkan, aku melihatnya. Cahaya kecil di ujung jalan. Mungkin itu rumah, mungkin itu harapan, atau mungkin itu sekadar ilusi.

Tapi tidak masalah. Karena cahaya itu cukup untuk membuatku percaya bahwa setiap perjalanan pasti ada ujungnya. Setiap perjuangan pasti ada hasilnya.

Dan aku akan terus berjalan menuju cahaya itu, apapun yang menunggu di sana.

— Serli SA —`
                },
                'puisi1': {
                    title: 'Rindu yang Terpendam',
                    text: `Di keheningan malam
Rindu datang menjelang
Membawa wajahmu
Yang tak pernah sirna

Ku genggam kenangan
Yang perlahan memudar
Berharap waktu bisa
Membawa kita kembali

Tapi rindu hanya bisa
Terpendam dalam hati
Seperti bunga yang layu
Sebelum sempat mekar

— Serli SA —`
                },
                'puisi2': {
                    title: 'Sepotong Senja',
                    text: `Senja menawarkan
Keindahan yang fana
Semburat jingga
Mewarnai langit senja

Seperti hidup
Yang penuh warna
Kadang terang
Kadang redup

Ku duduk di sini
Menyaksikan senja
Mengajariku tentang
Keindahan yang tak abadi

— Serli SA —`
                },
                'puisi3': {
                    title: 'Pelukis Mimpi',
                    text: `Dengan kanvas kosong
Aku melukis mimpi
Warna-warni harapan
Membentuk masa depan

Goresan demi goresan
Adalah langkah menuju
Mimpi yang terus
Kuperjuangkan

Meski badai datang
Mengancam lukisanku
Aku terus melukis
Karena mimpi tak boleh mati

— Serli SA —`
                },
                'puisi4': {
                    title: 'Bintang Malam',
                    text: `Di langit malam
Bintang bersinar terang
Memberikan cahaya
Di kegelapan yang pekat

Seperti harapan
Yang tak pernah padam
Meski dunia gelap
Ada cahaya yang menuntun

Bintang mengajariku
Bahwa sekecil apapun cahaya
Bisa menerangi
Kegelapan yang luas

— Serli SA —`
                }
            };

            if (contents[contentId]) {
                title.textContent = contents[contentId].title;
                content.textContent = contents[contentId].text;
                modal.classList.add('active');
                document.body.style.overflow = 'hidden';
            }
        }

        function closeModal() {
            const modal = document.getElementById('modal');
            modal.classList.remove('active');
            document.body.style.overflow = 'auto';
        }

        document.getElementById('modal').addEventListener('click', function(e) {
            if (e.target === this) {
                closeModal();
            }
        });
    </script>
</body>
</html>

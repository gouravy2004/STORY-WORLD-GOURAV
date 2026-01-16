
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GouravShayariHub - By Gaurav</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&family=Dancing+Script:wght@700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://html2canvas.hertzen.com/dist/html2canvas.min.js"></script>
    
    <style>
        /* --- CORE STYLES --- */
        :root {
            --bg-dark: #0f172a;
            --glass-bg: rgba(255, 255, 255, 0.05);
            --glass-border: rgba(255, 255, 255, 0.1);
            --accent-color: #8b5cf6;
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background-color: var(--bg-dark);
            color: var(--text-main);
            margin: 0;
            padding: 0;
            min-height: 100vh;
            overflow-x: hidden;
            display: flex;
            flex-direction: column;
        }

        /* Background Animation */
        .bg-blob {
            position: fixed;
            width: 50vw;
            height: 50vw;
            background: radial-gradient(circle, #ec4899, transparent 70%);
            opacity: 0.3;
            filter: blur(80px);
            z-index: -1;
            animation: moveBlob 10s infinite alternate;
        }
        .bg-blob:nth-child(2) {
            background: radial-gradient(circle, #8b5cf6, transparent 70%);
            right: 0; bottom: 0; animation-delay: -5s;
        }
        @keyframes moveBlob {
            0% { transform: translate(0, 0); }
            100% { transform: translate(30px, 30px); }
        }

        /* Header */
        header { text-align: center; padding: 40px 20px; }
        header h1 { 
            font-size: 3rem; margin: 0; 
            background: linear-gradient(to right, #fff, #a78bfa);
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
        }
        header p { color: var(--text-muted); }

        /* Search & Categories */
        .controls { text-align: center; margin-bottom: 40px; padding: 0 20px; }
        #searchInput {
            padding: 12px 20px; width: 100%; max-width: 400px;
            background: var(--glass-bg); border: 1px solid var(--glass-border);
            border-radius: 50px; color: white; outline: none; margin-bottom: 20px;
            backdrop-filter: blur(5px);
        }
        .categories button {
            background: var(--glass-bg); border: 1px solid var(--glass-border);
            color: var(--text-muted); padding: 8px 20px; border-radius: 20px;
            cursor: pointer; margin: 5px; transition: 0.3s;
        }
        .categories button.active, .categories button:hover {
            background: var(--accent-color); color: white; border-color: var(--accent-color);
        }

        /* Grid */
        .container {
            max-width: 1000px; margin: 0 auto; padding: 20px;
            display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            flex: 1; /* Pushes footer down */
        }

        /* Cards */
        .card {
            background: linear-gradient(145deg, rgba(255,255,255,0.08), rgba(255,255,255,0.02));
            border: 1px solid var(--glass-border); border-radius: 20px; padding: 25px;
            backdrop-filter: blur(10px); transition: 0.4s; position: relative;
        }
        .card:hover { transform: translateY(-5px); border-color: rgba(255,255,255,0.3); }

        .shayari-content {
            font-size: 1.1rem; line-height: 1.6; text-align: center; margin: 20px 0; color: #e2e8f0;
        }

        .card-actions {
            display: flex; justify-content: space-between; align-items: center;
            border-top: 1px solid var(--glass-border); padding-top: 15px; margin-top: 15px;
        }
        .tag { font-size: 0.8rem; text-transform: uppercase; color: #a78bfa; font-weight: bold; }
        
        .btn-group button {
            background: none; border: none; color: var(--text-muted);
            font-size: 1.1rem; margin-left: 10px; cursor: pointer; transition: 0.3s;
        }
        .btn-group button:hover { color: white; transform: scale(1.2); }
        .btn-image { color: #facc15 !important; }

        /* --- MODAL (POPUP) --- */
        .modal {
            display: none; position: fixed; z-index: 1000; left: 0; top: 0;
            width: 100%; height: 100%; background-color: rgba(0,0,0,0.8);
            backdrop-filter: blur(5px);
            align-items: center; justify-content: center; flex-direction: column;
        }

        #captureArea {
            width: 320px; height: 320px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            display: flex; flex-direction: column; justify-content: center; align-items: center;
            padding: 30px; box-sizing: border-box; text-align: center;
            border-radius: 10px; box-shadow: 0 0 20px rgba(0,0,0,0.5);
            position: relative;
        }
        
        .theme-love { background: linear-gradient(to top, #fbc2eb 0%, #a6c1ee 100%) !important; color: #333 !important; }
        .theme-sad { background: linear-gradient(to top, #cfd9df 0%, #e2ebf0 100%) !important; color: #333 !important; }
        .theme-dark { background: linear-gradient(45deg, #000000, #434343) !important; color: #fff !important; }

        #imgShayariText { font-size: 1.4rem; font-weight: 600; line-height: 1.5; }
        .watermark { margin-top: 20px; font-family: 'Dancing Script', cursive; font-size: 1.2rem; opacity: 0.8; }

        .modal-actions { margin-top: 20px; display: flex; gap: 10px; }
        .modal-btn { padding: 10px 20px; border: none; border-radius: 5px; cursor: pointer; font-weight: bold; }
        .btn-download { background: #22c55e; color: white; }
        .btn-close { background: #ef4444; color: white; }

        /* --- FOOTER BY GAURAV --- */
        footer {
            text-align: center; padding: 30px 20px; margin-top: 50px;
            border-top: 1px solid var(--glass-border); background: rgba(0, 0, 0, 0.2);
            backdrop-filter: blur(5px);
        }
        footer p { margin: 0; font-size: 1rem; color: var(--text-muted); }
        .designer-name {
            color: var(--accent-color); font-weight: 700; text-transform: uppercase;
            letter-spacing: 2px; text-shadow: 0 0 15px rgba(139, 92, 246, 0.6);
            animation: glow 2s infinite alternate;
        }
        @keyframes glow {
            from { text-shadow: 0 0 10px rgba(139, 92, 246, 0.4); }
            to { text-shadow: 0 0 20px rgba(139, 92, 246, 0.9), 0 0 10px #fff; }
        }

    </style>
</head>
<body>

    <div class="bg-blob"></div>
    <div class="bg-blob"></div>

    <header>
        <h1>GouravShayari Hub</h1>
        <p>Select. Create. Share.</p>
    </header>

    <div class="controls">
        <input type="text" id="searchInput" placeholder="Search Feelings..." onkeyup="searchShayari()">
        <div class="categories">
            <button class="active" onclick="filterShayari('all')">All</button>
            <button onclick="filterShayari('Love')">❤️ Love</button>
            <button onclick="filterShayari('Sad')">💔 Sad</button>
            <button onclick="filterShayari('Attitude')">😎 Attitude</button>
            <button onclick="filterShayari('Friendship')">🤝 Friendship</button>
        </div>
    </div>

    <div class="container" id="shayariContainer"></div>

    <div class="modal" id="imageModal">
        <div id="captureArea">
            <i class="fas fa-quote-left" style="opacity:0.5; margin-bottom:10px;"></i>
            <div id="imgShayariText">Loading...</div>
            <div class="watermark">- Designed by Gaurav -</div>
        </div>
        <div class="modal-actions">
            <button class="modal-btn" onclick="changeTheme()">🎨 Change Color</button>
            <button class="modal-btn btn-download" onclick="downloadImage()"><i class="fas fa-download"></i> Save</button>
            <button class="modal-btn btn-close" onclick="closeModal()">Close</button>
        </div>
    </div>

    <footer>
        <p>Designed with <i class="fas fa-heart" style="color: #ef4444; animation: pop 1s infinite;"></i> by <span class="designer-name">Gauravyadav</span></p>
    </footer>

    <script>
        const shayaris = [
            { id: 1, text: "Mohabbat mein jhukna koi ajeeb baat nahi,<br>Chamakta suraj bhi dhalta hai chand ke liye.", category: "Love" },
            { id: 2, text: "Na pesh-e-nazar, na nigah-e-shauq,<br>Tera milna bhi ek khwab lagta hai.", category: "Love" },
            { id: 3, text: "Tum sirf mere ho, ab ise haq samjho<br>Ya kabza... baat khatam.", category: "Love" },
            { id: 4, text: "Suno..!! Zyada baat nahi karni,<br>Bas gale lag kar rona hai tumhare.", category: "Love" },
            { id: 5, text: "Ishq wo khel nahi jo chhote dil wale khele,<br>Rooh tak kaanp jaati hai, sadme sahte sahte.", category: "Love" },
            { id: 6, text: "Meri har saans mein tu hai,<br>Meri har khushi mein tu hai,<br>Tere bina zindagi kuch nahi.", category: "Love" },
            { id: 7, text: "Hum to bane hi the tabah hone ke liye,<br>Tera milna to bas ek bahana ban gaya.", category: "Sad" },
            { id: 8, text: "Kaash tum maut hoti,<br>Toh ek din zaroor meri hoti.", category: "Sad" },
            { id: 9, text: "Tumhare baad hum jiske bhi honge,<br>Us rishte ka naam majboori hoga.", category: "Sad" },
            { id: 10, text: "Badi himmat di hai uski judai ne,<br>Na kisi ko khone ka darr hai, na kisi ko paane ki chahat.", category: "Sad" },
            { id: 11, text: "Sher khud apni takat se raja kahlata hai,<br>Jungle mein chunav nahi hote.", category: "Attitude" },
            { id: 12, text: "Log kehte hain ki mera dil patthar ka hai,<br>Lekin kuch log aise bhi the jo ise bhi tod gaye.", category: "Attitude" },
            { id: 13, text: "Hum wahan khade hote hain,<br>Jahan matter bade hote hain.", category: "Attitude" },
            { id: 14, text: "Na block kiya hai, na block karenge,<br>Tujhe to apni tarakki se jalayenge.", category: "Attitude" },
            { id: 15, text: "Waqt ki yaari to har koi karta hai mere dost,<br>Mazaa to tab hai jab waqt badle par yaar na badle.", category: "Friendship" }
        ];

        const container = document.getElementById('shayariContainer');
        const modal = document.getElementById('imageModal');
        const captureArea = document.getElementById('captureArea');
        const imgText = document.getElementById('imgShayariText');

        // Render Cards
        function displayShayaris(data) {
            container.innerHTML = '';
            data.forEach(item => {
                const card = document.createElement('div');
                card.className = 'card';
                card.innerHTML = `
                    <div class="shayari-content" id="text-${item.id}">${item.text}</div>
                    <div class="card-actions">
                        <span class="tag">${item.category}</span>
                        <div class="btn-group">
                            <button class="btn-image" onclick="openGenerator('${item.text.replace(/'/g, "\\'")}')" title="Create Image"><i class="fas fa-image"></i></button>
                            <button onclick="copyText('text-${item.id}')"><i class="far fa-copy"></i></button>
                            <button class="btn-whatsapp" onclick="shareWhatsapp('${item.text}')"><i class="fab fa-whatsapp"></i></button>
                        </div>
                    </div>
                `;
                container.appendChild(card);
            });
        }

        // --- IMAGE GENERATOR LOGIC ---
        function openGenerator(text) {
            modal.style.display = 'flex';
            imgText.innerHTML = text;
        }

        function closeModal() {
            modal.style.display = 'none';
        }

        const themes = ['', 'theme-love', 'theme-sad', 'theme-dark'];
        let currentTheme = 0;
        function changeTheme() {
            currentTheme = (currentTheme + 1) % themes.length;
            captureArea.className = '';
            if(themes[currentTheme]) captureArea.classList.add(themes[currentTheme]);
        }

        function downloadImage() {
            html2canvas(captureArea, { scale: 2, backgroundColor: null }).then(canvas => {
                const link = document.createElement('a');
                link.download = 'shayari-by-gaurav.png';
                link.href = canvas.toDataURL();
                link.click();
            });
        }

        // --- UTILS ---
        function filterShayari(category) {
            document.querySelectorAll('.categories button').forEach(b => b.classList.remove('active'));
            event.target.classList.add('active');
            category === 'all' ? displayShayaris(shayaris) : displayShayaris(shayaris.filter(s => s.category === category));
        }

        function searchShayari() {
            const q = document.getElementById('searchInput').value.toLowerCase();
            displayShayaris(shayaris.filter(s => s.text.toLowerCase().includes(q) || s.category.toLowerCase().includes(q)));
        }

        function shareWhatsapp(text) {
            window.open(`https://wa.me/?text=${encodeURIComponent(text.replace(/<br>/g, "\n") + "\n\n- Via ShayariHub")}`, '_blank');
        }

        function copyText(id) {
            navigator.clipboard.writeText(document.getElementById(id).innerText);
            alert("Copied!");
        }

        displayShayaris(shayaris);
    </script>
</body>
</html>

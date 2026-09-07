# test
test your love
<!DOCTYPE html>
<html lang="uz">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tungi Ehtiros ✨ Secret Pair Game</title>
    <style>
        :root {
            --card-bg: rgba(15, 8, 18, 0.94);
            --accent-red: #a8002a;
            --accent-gold: #e6c675;
            --text-color: #f8f9fa;
        }
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
        }
        body {
            background: linear-gradient(rgba(10, 3, 12, 0.85), rgba(10, 3, 12, 0.9)), 
                        url('https://images.unsplash.com/photo-1518199266791-5375a83190b7?q=80&w=1000&auto=format&fit=crop') no-repeat center center fixed;
            background-size: cover;
            color: var(--text-color);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 15px;
        }
        .container {
            width: 100%;
            max-width: 440px;
            background: var(--card-bg);
            border: 1px solid rgba(230, 198, 117, 0.35);
            border-radius: 24px;
            padding: 24px 20px;
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.9), 0 0 25px rgba(168, 0, 42, 0.4);
            text-align: center;
            backdrop-filter: blur(10px);
        }
        h1 {
            font-size: 24px;
            color: var(--accent-gold);
            margin-bottom: 6px;
            letter-spacing: 1.5px;
        }
        p.subtitle {
            font-size: 13px;
            color: #d1b8d9;
            margin-bottom: 20px;
        }
        .gender-select {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }
        .gender-btn {
            flex: 1;
            padding: 12px;
            border-radius: 14px;
            border: 1px solid rgba(230, 198, 117, 0.3);
            background: rgba(255, 255, 255, 0.05);
            color: #fff;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
        }
        .gender-btn.active-male {
            background: linear-gradient(45deg, #1c2541, #3a506b);
            border-color: #5bc0be;
        }
        .gender-btn.active-female {
            background: linear-gradient(45deg, var(--accent-red), #610017);
            border-color: var(--accent-gold);
        }
        input[type="text"], textarea {
            width: 100%;
            padding: 12px;
            border-radius: 12px;
            border: 1px solid rgba(230, 198, 117, 0.4);
            background: rgba(0, 0, 0, 0.6);
            color: #fff;
            outline: none;
            font-size: 14px;
        }
        textarea {
            height: 90px;
            resize: none;
            margin-top: 10px;
            margin-bottom: 15px;
            text-align: left;
        }
        .card-box {
            min-height: 140px;
            background: linear-gradient(145deg, rgba(35, 12, 38, 0.95), rgba(15, 5, 20, 0.98));
            border: 1px solid rgba(230, 198, 117, 0.4);
            border-radius: 18px;
            padding: 18px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            margin-bottom: 15px;
        }
        .card-text {
            font-size: 15px;
            line-height: 1.5;
            color: #fff;
        }
        .main-btn {
            width: 100%;
            padding: 14px;
            border: none;
            border-radius: 50px;
            background: linear-gradient(45deg, var(--accent-gold), #c49a33);
            color: #0d030c;
            font-size: 15px;
            font-weight: bold;
            cursor: pointer;
            box-shadow: 0 4px 20px rgba(230, 198, 117, 0.35);
        }
        .screen { display: none; }
        .screen.active { display: block; }
        .link-box {
            background: rgba(0,0,0,0.6);
            padding: 12px;
            border-radius: 12px;
            font-size: 11px;
            word-break: break-all;
            margin: 15px 0;
            border: 1px dashed var(--accent-gold);
            color: var(--accent-gold);
        }
        .progress {
            font-size: 12px;
            color: var(--accent-gold);
            margin-bottom: 10px;
            font-weight: bold;
        }
        .result-card {
            background: rgba(0, 0, 0, 0.5);
            border: 1px solid rgba(230, 198, 117, 0.3);
            border-radius: 14px;
            padding: 12px;
            margin-bottom: 12px;
            text-align: left;
        }
        .result-q {
            font-size: 12px;
            color: var(--accent-gold);
            margin-bottom: 5px;
            font-weight: bold;
        }
        .result-a {
            font-size: 13.5px;
            color: #fff;
            line-height: 1.4;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- 1-EKRAN: KIRISH -->
        <div id="startScreen" class="screen active">
            <h1>Tungi Ehtiros ✨</h1>
            <p class="subtitle" id="introSubtitle">Masofaviy juftliklar uchun 8 ta maxfiy va ehtirosli savollar</p>
            <div class="gender-select">
                <button class="gender-btn active-male" id="btnMale" onclick="selectGender('male')">Erkak 👨</button>
                <button class="gender-btn" id="btnFemale" onclick="selectGender('female')">Ayol 👩</button>
            </div>
            <input type="text" id="userName" placeholder="Ismingizni kiriting..." style="margin-bottom: 20px;">
            <button class="main-btn" onclick="startGame()">O'yinni Boshlash 🔥</button>
        </div>
        <!-- 2-EKRAN: SAVOL VA JAVOB YOZISH -->
        <div id="gameScreen" class="screen">
            <div class="progress" id="cardProgress">1 / 8 SAVOL</div>
            <div class="card-box">
                <div class="card-text" id="cardContent">Savol yuklanmoqda...</div>
            </div>          
            <textarea id="userAnswer" placeholder="Javobingizni yoki his-tuyg'ularingizni shu yerga yozing..."></textarea>          
            <button class="main-btn" onclick="nextCard()">Send (Yuborish) 📩</button>
        </div>
        <!-- 3-EKRAN: LINKNI JUFTIGA YUBORISH -->
        <div id="linkScreen" class="screen">
            <h1>Barcha javoblar saqlandi! 🔥</h1>
            <p class="subtitle">Endi ushbu linkni juftingizga yuboring. U ham javob berganidan so'ng, javoblaringiz bir-biringizga ko'rinadi.</p>           
            <div class="link-box" id="shareLink">Link tayyorlanmoqda...</div>
            <button class="main-btn" onclick="copyLink()">Linkni Nusxalash 📋</button>
        </div>
        <!-- 4-EKRAN: IKKALA TARAF JAVOBLARI (YAKUNIY) -->
        <div id="finalScreen" class="screen">
            <h1 id="finalTitle">Juftlik Natijalari 💋</h1>
            <p class="subtitle">Siz va juftingiz bergan ehtirosli javoblar:</p>
            <div id="answersContainer" style="max-height: 380px; overflow-y: auto; padding-right: 5px;"></div>
        </div>
    </div>
    <script>
        // Erkak kishi uchun 8 ta savol
        const maleCards = [
            "1. Hozir uzoqda bo'lsam ham, mening qaysi xislatim yoki harakatim sizda eng kuchli ehtirosni uyg'otadi?",
            "2. Videocall'da yoki suratlarda men kiygan qaysi kiyimim sizga eng ko'p yoqadi va nima uchun?",
            "3. Ikkimiz birinchi bor yolg'iz qolganimizda, mening qayerimdan birinchi bo'lib o'pgan bo'lardingiz?",
            "4. Menga pichirlab aytishni xohlagan, lekin shu paytgacha aytishga tortingan bitta yashirin xayolingiz?",
            "5. Ovozimda yoki gapirishimda sizni nazoratni yo'qotish darajasiga olib keladigan narsa nima?",
            "6. Birga o'tkaziladigan eng ehtirosli va unutilmas kechamizni qanday tasavvur qilasiz?",
            "7. Hozir yonimda paydo bo'lib qolganingizda, birinchi 60 soniya ichida nima qilgan bo mezonini yozing.",
            "8. Menga hozir aytishingiz mumkin bo'lgan eng issiq va samimiy ehtirosli so'zingiz qaysi?"
        ];
        // Ayol kishi uchun 8 ta savol
        const femaleCards = [
            "1. Hozir kiyib turgan kiyimingiz va tanangizdagi his-tuyg'ularni unga qanchalik jozibali tasvirlab bera olasiz?",
            "2. Juftingizning qaysi qarashi, nigohi yoki ovoz toni sizni hayajonga soladi?",
            "3. U sizga yaqin kelib bo'yningizdan o'psa, qanday his-tuyg'ularni boshdan kechirasiz?",
            "4. Unga aytishga ozgina tortingan, lekin ichingizda saqlab yurgan bitta ehtirosli istagingiz?",
            "5. Videocall paytida u sizga qanday tikilib tursa, o'zingizni eng jozibali his qilasiz?",
            "6. U bilan bog'liq tushingizda ko'rgan eng esda qolarli va sirli vaziyatni yozing.",
            "7. U sizga kutilmagan qanday romantik va ehtirosli syurpriz qilishini xohlardingiz?",
            "8. Unga hozir audio yoki matn orqali yo'llashingiz mumkin bo'lgan eng erkalovchi so'zingiz?"
        ];
        let selectedGender = 'male';
        let currentCards = [];
        let currentIndex = 0;
        let myAnswers = [];
        let isPartner = false;
        let p1Data = null;
        window.onload = function() {
            const urlParams = new URLSearchParams(window.location.search);
            const ref = urlParams.get('ref');
            if (ref) {
                try {
                    p1Data = JSON.parse(decodeURIComponent(escape(atob(ref))));
                    isPartner = true;
                    document.getElementById('introSubtitle').innerText = `${p1Data.name} sizga 8 ta ehtirosli savol yubordi! Javob berish uchun jinsingizni tanlang.`;
                } catch(e){}
            }
        };
        function selectGender(g) {
            selectedGender = g;
            document.getElementById('btnMale').className = 'gender-btn' + (g === 'male' ? ' active-male' : '');
            document.getElementById('btnFemale').className = 'gender-btn' + (g === 'female' ? ' active-female' : '');
        }
        function startGame() {
            const name = document.getElementById('userName').value.trim();
            if(!name) {
                alert("Iltimos, ismingizni kiriting!");
                return;
            }
            currentCards = selectedGender === 'male' ? maleCards : femaleCards;
            currentIndex = 0;
            myAnswers = [];
            showScreen('gameScreen');
            loadCard();
        }
        function loadCard() {
            document.getElementById('cardProgress').innerText = `${currentIndex + 1} / 8 SAVOL`;
            document.getElementById('cardContent').innerText = currentCards[currentIndex];
            document.getElementById('userAnswer').value = '';
        }
        function nextCard() {
            const ans = document.getElementById('userAnswer').value.trim();
            if(!ans) {
                alert("Iltimos, yuborishdan oldin javob yozing!");
                return;
            }
            myAnswers.push({
                q: currentCards[currentIndex],
                a: ans
            });
            currentIndex++;
            if(currentIndex < currentCards.length) {
                loadCard();
            } else {
                const name = document.getElementById('userName').value.trim();             
                if(!isPartner) {
                    // Birinchi odam (P1)
                    const data = {
                        name: name,
                        gender: selectedGender,
                        answers: myAnswers
                    };
                    const encoded = btoa(unescape(encodeURIComponent(JSON.stringify(data))));
                    const shareUrl = window.location.origin + window.location.pathname + '?ref=' + encoded;                    
                    document.getElementById('shareLink').innerText = shareUrl;
                    showScreen('linkScreen');
                } else {
                    // Ikkinchi odam (P2) - Natijalarni ko'rsatish
                    showResults(p1Data, { name: name, gender: selectedGender, answers: myAnswers });
                }
            }
        }
        function showResults(p1, p2) {
            showScreen('finalScreen');
            const container = document.getElementById('answersContainer');
            container.innerHTML = '';
            document.getElementById('finalTitle').innerText = `${p1.name} 💕 ${p2.name}`;
            // P1 Javoblari
            let html = `<h3 style="color:var(--accent-gold); margin:15px 0 10px; font-size:15px;">🔥 ${p1.name} ning Javoblari (${p1.gender === 'male' ? 'Erkak' : 'Ayol'}):</h3>`;
            p1.answers.forEach((item) => {
                html += `
                    <div class="result-card">
                        <div class="result-q">${item.q}</div>
                        <div class="result-a">👉 ${item.a}</div>
                    </div>
                `;
            });
            // P2 Javoblari
            html += `<h3 style="color:var(--accent-gold); margin:20px 0 10px; font-size:15px;">🔥 ${p2.name} ning Javoblari (${p2.gender === 'male' ? 'Erkak' : 'Ayol'}):</h3>`;
            p2.answers.forEach((item) => {
                html += `
                    <div class="result-card">
                        <div class="result-q">${item.q}</div>
                        <div class="result-a">👉 ${item.a}</div>
                    </div>
                `;
            });
            container.innerHTML = html;
        }
        function copyLink() {
            const linkText = document.getElementById('shareLink').innerText;
            navigator.clipboard.writeText(linkText);
            alert("Link nusxalandi! Buni juftingizga yuboring ✨");
        }
        function showScreen(id) {
            document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
            document.getElementById(id).classList.add('active');
        }
    </script>
</body>
</html>

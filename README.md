<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PC MASTER | International Tech</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&family=Roboto:wght@300;400;700&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --primary: #00d4ff;
            --bg-dark: #05070a;
            --card-bg: #11141d;
        }

        body {
            font-family: 'Roboto', sans-serif;
            margin: 0;
            background-color: var(--bg-dark);
            color: #ffffff;
            scroll-behavior: smooth;
        }

        .lang-switcher {
            background: #000;
            padding: 10px;
            text-align: center;
            border-bottom: 1px solid #222;
            position: sticky;
            top: 0;
            z-index: 101;
        }

        .lang-btn {
            background: transparent;
            border: 1px solid #444;
            color: #aaa;
            padding: 5px 12px;
            margin: 0 4px;
            cursor: pointer;
            font-size: 0.8rem;
            border-radius: 4px;
            transition: 0.3s;
            font-family: 'Orbitron', sans-serif;
        }

        .lang-btn.active {
            border-color: var(--primary);
            color: var(--primary);
            box-shadow: 0 0 10px rgba(0, 212, 255, 0.3);
        }

        nav {
            background: rgba(17, 20, 29, 0.95);
            padding: 15px;
            position: sticky;
            top: 45px;
            z-index: 100;
            text-align: center;
            border-bottom: 1px solid var(--primary);
        }

        nav a {
            color: white;
            text-decoration: none;
            margin: 0 20px;
            font-family: 'Orbitron', sans-serif;
            font-size: 0.8rem;
            letter-spacing: 1px;
        }

        header {
            background: linear-gradient(rgba(0,0,0,0.8), rgba(0,0,0,0.8)), url('https://images.unsplash.com/photo-1593640408182-31c70c8268f5?w=1500');
            background-size: cover;
            background-position: center;
            padding: 100px 20px;
            text-align: center;
        }

        header h1 {
            font-family: 'Orbitron', sans-serif;
            font-size: clamp(2.5rem, 8vw, 4rem);
            background: linear-gradient(to right, #fff, var(--primary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin: 0;
            letter-spacing: 5px;
        }

        .container { max-width: 1200px; margin: 0 auto; padding: 40px 20px; }

        .section-title {
            text-align: center;
            font-family: 'Orbitron', sans-serif;
            color: var(--primary);
            margin-bottom: 50px;
            letter-spacing: 3px;
        }

        .pc-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 30px;
        }

        .pc-card {
            background: var(--card-bg);
            border-radius: 20px;
            padding: 25px;
            border: 1px solid #222;
            transition: 0.4s;
            display: flex;
            flex-direction: column;
        }

        .pc-card:hover { border-color: var(--primary); transform: translateY(-5px); }

        .pc-card img { width: 100%; height: 220px; object-fit: cover; border-radius: 12px; margin-bottom: 15px; }

        .price { font-size: 2.2rem; color: #00ff88; margin: 15px 0; font-weight: bold; }

        .details {
            max-height: 0;
            overflow: hidden;
            background: #0a0c12;
            transition: 0.5s ease-out;
            font-size: 0.9rem;
            line-height: 1.6;
        }

        .details.show {
            max-height: 500px;
            padding: 15px;
            margin-bottom: 15px;
            border: 1px dashed var(--primary);
        }

        .btn-group { display: flex; gap: 10px; margin-top: auto; }

        .btn {
            flex: 1;
            padding: 14px;
            text-align: center;
            border-radius: 8px;
            font-family: 'Orbitron', sans-serif;
            font-size: 0.75rem;
            font-weight: bold;
            cursor: pointer;
            border: none;
            text-decoration: none;
            transition: 0.3s;
        }

        .btn-primary { background: var(--primary); color: #000; }
        .btn-outline { border: 1px solid var(--primary); color: var(--primary); background: transparent; }
        .btn:hover { opacity: 0.8; letter-spacing: 1px; }

        .about-section { 
            background: #0d1117; 
            padding: 60px 40px; 
            border-radius: 25px; 
            margin-top: 60px; 
            border-left: 6px solid var(--primary);
            line-height: 1.8;
        }

        .contact-box {
            text-align: center;
            padding: 60px;
            background: #000;
            border-radius: 25px;
            margin-top: 40px;
            border: 1px solid var(--primary);
        }

        .contact-box a { color: var(--primary); text-decoration: none; font-weight: bold; font-size: 1.2rem; }

        footer { text-align: center; padding: 50px; color: #444; font-size: 0.85rem; }

        .modal {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.96);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }
        .modal.active { display: flex; }
        .modal-content {
            background: #1c222d;
            padding: 50px;
            border-radius: 25px;
            text-align: center;
            border: 2px solid var(--primary);
            max-width: 500px;
        }
    </style>
</head>
<body>

    <div class="lang-switcher">
        <button class="lang-btn active" onclick="changeLang('ru', this)">РУС</button>
        <button class="lang-btn" onclick="changeLang('en', this)">ENG</button>
        <button class="lang-btn" onclick="changeLang('ua', this)">UKR</button>
        <button class="lang-btn" onclick="changeLang('lv', this)">LAT</button>
        <button class="lang-btn" onclick="changeLang('fi', this)">FIN</button>
    </div>

    <nav>
        <a href="#catalog" id="nav-catalog">КАТАЛОГ</a>
        <a href="#about" id="nav-about">ИСТОРИЯ УСПЕХА</a>
        <a href="#contact" id="nav-contact">КОНТАКТЫ</a>
    </nav>

    <header>
        <h1>PC MASTER</h1>
        <p id="header-sub">ИНЖЕНЕРНОЕ ИСКУССТВО В КАЖДОЙ ДЕТАЛИ</p>
    </header>

    <div class="container">
        <h2 class="section-title" id="cat-title">НАШИ ПРОЕКТЫ</h2>
        <div class="pc-grid" id="catalog">
            
            <div class="pc-card">
                <img src="https://images.unsplash.com/photo-1587202372775-e229f172b9d7?w=500" alt="PC">
                <h3 id="pc1-title">STARTER EDITION</h3>
                <p id="pc1-desc">Оптимальный вход в мир гейминга.</p>
                <span class="price">€ 649</span>
                <div class="details" id="det1"></div>
                <div class="btn-group">
                    <button onclick="toggleDetails('det1')" class="btn btn-outline" id="btn-spec-1">СОСТАВ СБОРКИ</button>
                    <button onclick="showModal()" class="btn btn-primary" id="btn-buy-1">КУПИТЬ</button>
                </div>
            </div>

            <div class="pc-card">
                <img src="https://images.unsplash.com/photo-1591488320449-011701bb6704?w=500" alt="PC">
                <h3 id="pc2-title">GAMER PRO</h3>
                <p id="pc2-desc">Бескомпромиссный 2K гейминг.</p>
                <span class="price">€ 1,690</span>
                <div class="details" id="det2"></div>
                <div class="btn-group">
                    <button onclick="toggleDetails('det2')" class="btn btn-outline" id="btn-spec-2">СОСТАВ СБОРКИ</button>
                    <button onclick="showModal()" class="btn btn-primary" id="btn-buy-2">КУПИТЬ</button>
                </div>
            </div>

            <div class="pc-card">
                <img src="https://images.unsplash.com/photo-1547082299-de196ea013d6?w=500" alt="PC">
                <h3 id="pc3-title">ULTIMATE BEAST</h3>
                <p id="pc3-desc">Ультимативная станция 4K.</p>
                <span class="price">€ 4,500</span>
                <div class="details" id="det3"></div>
                <div class="btn-group">
                    <button onclick="toggleDetails('det3')" class="btn btn-outline" id="btn-spec-3">СОСТАВ СБОРКИ</button>
                    <button onclick="showModal()" class="btn btn-primary" id="btn-buy-3">КУПИТЬ</button>
                </div>
            </div>
        </div>

        <div class="about-section" id="about">
            <h2 id="about-title" style="color:var(--primary); font-family:Orbitron;">ИСТОРИЯ УСПЕХА</h2>
            <div id="about-text"></div>
        </div>

        <div class="contact-box" id="contact">
            <h2 id="contact-title" style="font-family:Orbitron; color:var(--primary);">КОНТАКТЫ</h2>
            <p>📧 Email: <a href="mailto:ivanlaponogov426@gmail.com">ivanlaponogov426@gmail.com</a></p>
            <p>📞 Tel: <a href="tel:+358466185815">+358 46 618 5815</a></p>
        </div>
    </div>

    <div id="buyModal" class="modal">
        <div class="modal-content">
            <h2 id="modal-title" style="color:var(--primary); font-family:Orbitron;">СЕРВИС ПЕРЕГРУЖЕН</h2>
            <p id="modal-text"></p>
            <button onclick="closeModal()" class="btn btn-primary" id="modal-btn">OK</button>
        </div>
    </div>

    <script>
        const translations = {
            ru: {
                nav_cat: "КАТАЛОГ", nav_abt: "ИСТОРИЯ УСПЕХА", nav_con: "КОНТАКТЫ",
                h_sub: "ИНЖЕНЕРНОЕ ИСКУССТВО В КАЖДОЙ ДЕТАЛИ", cat_t: "НАШИ ПРОЕКТЫ",
                spec_btn: "СОСТАВ СБОРКИ", buy_btn: "КУПИТЬ",
                pc1_t: "STARTER EDITION", pc1_d: "Идеальный баланс для онлайн-игр и учебы.",
                pc2_t: "GAMER PRO", pc2_d: "Мощная станция для 2K гейминга на ультра-настройках.",
                pc3_t: "ULTIMATE BEAST", pc3_d: "Вершина технологий для 4K и тяжелого рендеринга.",
                spec1: "<b>ДЕТАЛИ:</b><br>• i3-12100F (4.3GHz)<br>• RTX 3050 8GB<br>• 16GB DDR4 3200MHz<br>• 500GB NVMe SSD<br>• 600W 80+ Bronze",
                spec2: "<b>ДЕТАЛИ:</b><br>• i5-13600K (5.1GHz)<br>• RTX 4070 Super 12GB<br>• 32GB DDR5 6000MHz<br>• 1TB Gen4 SSD<br>• СЖО 240mm RGB",
                spec3: "<b>ДЕТАЛИ:</b><br>• i9-14900K (6.0GHz)<br>• RTX 4090 24GB FE<br>• 64GB DDR5 6400MHz<br>• 2TB + 2TB SSD RAID<br>• БП 1200W Platinum",
                abt_t: "КАК МЫ ЭТОГО ДОБИЛИСЬ",
                abt_p: "Все началось в 2018 году с мечты о идеальном ПК. Мы видели, как рынок заполняют дешевые готовые сборки, которые перегреваются и шумят. Мы решили, что качество важнее экономии. Каждый наш компьютер проходит 24-часовой тест на стабильность. Мы используем только проверенные бренды и лучший кабель-менеджмент в индустрии. Сегодня PC MASTER — это стандарт надежности в Европе.",
                m_t: "СЕРВИС ПЕРЕГРУЖЕН", m_p: "К сожалению, сейчас все наши мастера заняты. Оформление через сайт временно недоступно. Пожалуйста, свяжитесь с нами напрямую по телефону.", m_b: "ПОНЯТНО", con_t: "СВЯЗАТЬСЯ С НАМИ"
            },
            en: {
                nav_cat: "CATALOG", nav_abt: "SUCCESS STORY", nav_con: "CONTACT",
                h_sub: "ENGINEERING ART IN EVERY DETAIL", cat_t: "OUR PROJECTS",
                spec_btn: "PC SPECS", buy_btn: "BUY NOW",
                pc1_t: "STARTER EDITION", pc1_d: "Perfect balance for online gaming and study.",
                pc2_t: "GAMER PRO", pc2_d: "Powerful station for 2K gaming at ultra settings.",
                pc3_t: "ULTIMATE BEAST", pc3_d: "Top-tier technology for 4K and heavy rendering.",
                spec1: "<b>SPECS:</b><br>• i3-12100F (4.3GHz)<br>• RTX 3050 8GB<br>• 16GB DDR4 3200MHz<br>• 500GB NVMe SSD<br>• 600W 80+ Bronze",
                spec2: "<b>SPECS:</b><br>• i5-13600K (5.1GHz)<br>• RTX 4070 Super 12GB<br>• 32GB DDR5 6000MHz<br>• 1TB Gen4 SSD<br>• 240mm AIO Liquid Cooling",
                spec3: "<b>SPECS:</b><br>• i9-14900K (6.0GHz)<br>• RTX 4090 24GB FE<br>• 64GB DDR5 6400MHz<br>• 2TB + 2TB SSD RAID<br>• 1200W Platinum PSU",
                abt_t: "HOW WE ACHIEVED THIS",
                abt_p: "It all started in 2018 with a dream of the perfect PC. We saw the market filled with cheap pre-builts that overheat and make noise. We decided that quality matters more than savings. Every one of our computers undergoes a 24-hour stability test. We use only trusted brands and the best cable management in the industry. Today, PC MASTER is the standard for reliability in Europe.",
                m_t: "SERVICE OVERLOADED", m_p: "Unfortunately, all our engineers are busy. Website orders are temporarily disabled. Please contact us directly by phone.", m_b: "UNDERSTOOD", con_t: "GET IN TOUCH"
            },
            ua: {
                nav_cat: "КАТАЛОГ", nav_abt: "ІСТОРІЯ УСПІХУ", nav_con: "КОНТАКТИ",
                h_sub: "ІНЖЕНЕРНЕ МИСТЕЦТВО В КОЖНІЙ ДЕТАЛІ", cat_t: "НАШІ ПРОЄКТИ",
                spec_btn: "СКЛАД ЗБІРКИ", buy_btn: "КУПИТИ",
                pc1_t: "STARTER EDITION", pc1_d: "Оптимальний вибір для онлайн-ігор та навчання.",
                pc2_t: "GAMER PRO", pc2_d: "Потужна станція для 2K геймінгу на ультра-налаштуваннях.",
                pc3_t: "ULTIMATE BEAST", pc3_d: "Вершина технологій для 4K та важкого рендерингу.",
                spec1: "<b>ДЕТАЛІ:</b><br>• i3-12100F (4.3GHz)<br>• RTX 3050 8GB<br>• 16GB DDR4 3200MHz<br>• 500GB NVMe SSD<br>• 600W 80+ Bronze",
                spec2: "<b>ДЕТАЛІ:</b><br>• i5-13600K (5.1GHz)<br>• RTX 4070 Super 12GB<br>• 32GB DDR5 6000MHz<br>• 1TB Gen4 SSD<br>• Рідинне охолодження 240mm",
                spec3: "<b>ДЕТАЛІ:</b><br>• i9-14900K (6.0GHz)<br>• RTX 4090 24GB FE<br>• 64GB DDR5 6400MHz<br>• 2TB + 2TB SSD RAID<br>• БЖ 1200W Platinum",
                abt_t: "ЯК МИ ЦЬОГО ДОСЯГЛИ",
                abt_p: "Все почалося у 2018 році з мрії про ідеальний ПК. Ми бачили ринок, заповнений дешевими збірками, що гріються та шумлять. Ми вирішили, що якість важливіша за економію. Кожен наш комп'ютер проходить 24-годинний стрес-тест. Сьогодні PC MASTER — це символ надійності в Європі.",
                m_t: "СЕРВІС ПЕРЕВАНТАЖЕНИЙ", m_p: "Наразі всі наші майстри зайняті. Замовлення через сайт тимчасово недоступні. Зв'яжіться з нами телефоном.", m_b: "ЗРОЗУМІЛО", con_t: "ЗВ'ЯЗАТИСЯ З НАМИ"
            },
            lv: {
                nav_cat: "KATALOGS", nav_abt: "VEIKSMES STĀSTS", nav_con: "KONTAKTI",
                h_sub: "INŽENIERZINĀTNE KATRĀ DETAĻĀ", cat_t: "MŪSU PROJEKTI",
                spec_btn: "KOMPONENTES", buy_btn: "PIRKT",
                pc1_t: "STARTER EDITION", pc1_d: "Ideāls līdzsvars tiešsaistes spēlēm un mācībām.",
                pc2_t: "GAMER PRO", pc2_d: "Jaudīga stacija 2K spēlēšanai ultra iestatījumos.",
                pc3_t: "ULTIMATE BEAST", pc3_d: "Tehnoloģiju virsotne 4K un smagam darbam.",
                spec1: "<b>DETAĻAS:</b><br>• i3-12100F<br>• RTX 3050 8GB<br>• 16GB RAM<br>• 500GB SSD",
                spec2: "<b>DETAĻAS:</b><br>• i5-13600K<br>• RTX 4070 S<br>• 32GB DDR5<br>• 1TB SSD",
                spec3: "<b>DETAĻAS:</b><br>• i9-14900K<br>• RTX 4090<br>• 64GB DDR5<br>• 4TB SSD RAID",
                abt_t: "KĀ MĒS TO SASNIEDZĀM",
                abt_p: "Viss sākās 2018. gadā ar sapni par perfektu datoru. Mēs redzējām lētus gatavos datorus, kas pārkarst. Mēs izvēlējāmies kvalitāti. Šodien PC MASTER ir uzticamības standarts Eiropā.",
                m_t: "SERVISS PĀRSLODZĒTS", m_p: "Pašlaik visi meistari ir aizņemti. Lūdzu, sazinieties ar mums pa tālruni.", m_b: "SAPRATU", con_t: "SAZINIETIES AR MUMS"
            },
            fi: {
                nav_cat: "LUETTELO", nav_abt: "TARINA", nav_con: "YHTEYSTIEDOT",
                h_sub: "INSINÖÖRITAIDETTA JOKAISESSA YKSITYISKOHDASSA", cat_t: "MEIDÄN PROJEKTIMME",
                spec_btn: "KOKOONPANO", buy_btn: "OSTA",
                pc1_t: "STARTER EDITION", pc1_d: "Täydellinen tasapaino peleihin ja opiskeluun.",
                pc2_t: "GAMER PRO", pc2_d: "Tehokas asema 2K-pelaamiseen ultra-asetuksilla.",
                pc3_t: "ULTIMATE BEAST", pc3_d: "Huipputeknologiaa 4K-pelaamiseen ja editointiin.",
                spec1: "<b>TIEDOT:</b><br>• i3-12100F<br>• RTX 3050 8GB<br>• 16GB RAM<br>• 500GB SSD",
                spec2: "<b>TIEDOT:</b><br>• i5-13600K<br>• RTX 4070 S<br>• 32GB DDR5<br>• 1TB SSD",
                spec3: "<b>TIEDOT:</b><br>• i9-14900K<br>• RTX 4090<br>• 64GB DDR5<br>• 4TB SSD RAID",
                abt_t: "MITEN SAAVUTIMME TÄMÄN",
                abt_p: "Kaikki alkoi vuonna 2018 unelmasta täydellisestä tietokoneesta. Halusimme tarjota laatua halpojen ja kuumenevien pakettikoneiden sijaan. Tänään PC MASTER on luotettavuuden standardi Euroopassa.",
                m_t: "PALVELU RUUHKAUTUNUT", m_p: "Kaikki rakentajamme ovat tällä hetkellä varattuja. Ota yhteyttä puhelimitse.", m_b: "YMMÄRRÄN", con_t: "OTA YHTEYTTÄ"
            }
        };

        function changeLang(lang, btn) {
            document.querySelectorAll('.lang-btn').forEach(b => b.classList.remove('active'));
            btn.classList.add('active');

            const t = translations[lang];
            
            // Навигация и заголовки
            document.getElementById('nav-catalog').innerText = t.nav_cat;
            document.getElementById('nav-about').innerText = t.nav_abt;
            document.getElementById('nav-contact').innerText = t.nav_con;
            document.getElementById('header-sub').innerText = t.h_sub;
            document.getElementById('cat-title').innerText = t.cat_t;
            document.getElementById('about-title').innerText = t.abt_t;
            document.getElementById('about-text').innerText = t.abt_p;
            document.getElementById('contact-title').innerText = t.con_t;

            // Карточки
            document.getElementById('pc1-title').innerText = t.pc1_t;
            document.getElementById('pc1-desc').innerText = t.pc1_d;
            document.getElementById('pc2-title').innerText = t.pc2_t;
            document.getElementById('pc2-desc').innerText = t.pc2_d;
            document.getElementById('pc3-title').innerText = t.pc3_t;
            document.getElementById('pc3-desc').innerText = t.pc3_d;

            // Спецификации
            document.getElementById('det1').innerHTML = t.spec1;
            document.getElementById('det2').innerHTML = t.spec2;
            document.getElementById('det3').innerHTML = t.spec3;

            // Кнопки
            for(let i=1; i<=3; i++) {
                document.getElementById('btn-spec-'+i).innerText = t.spec_btn;
                document.getElementById('btn-buy-'+i).innerText = t.buy_btn;
            }

            // Модалка
            document.getElementById('modal-title').innerText = t.m_t;
            document.getElementById('modal-text').innerText = t.m_p;
            document.getElementById('modal-btn').innerText = t.m_b;
        }

        function toggleDetails(id) { document.getElementById(id).classList.toggle('show'); }
        function showModal() { document.getElementById('buyModal').classList.add('active'); }
        function closeModal() { document.getElementById('buyModal').classList.remove('active'); }

        // Инициализация при загрузке (на русском)
        window.onload = () => changeLang('ru', document.querySelector('.lang-btn.active'));
    </script>
</body>
</html>

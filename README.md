<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Devartsx | Custom Handmade Artwork</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <style>
        :root {
            --bg-color: #fcfcfd;
            --text-color: #1a1a1a;
            --primary-yellow: #ffd700;
            --gold-glow: rgba(255, 215, 0, 0.4);
            --card-bg: rgba(255, 255, 255, 0.9);
            --shadow: 0 20px 40px rgba(0, 0, 0, 0.08);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
            scroll-behavior: smooth;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-color);
            overflow-x: hidden;
            position: relative;
        }

        /* Ambient Animated Background Orbs */
        .ambient-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            z-index: -1;
            overflow: hidden;
            pointer-events: none;
        }

        .orb {
            position: absolute;
            border-radius: 50%;
            filter: blur(80px);
            opacity: 0.45;
            animation: orbFloat 12s infinite alternate ease-in-out;
        }

        .orb-1 {
            width: 350px;
            height: 350px;
            background: #ffe566;
            top: -50px;
            left: -50px;
        }

        .orb-2 {
            width: 400px;
            height: 400px;
            background: #fff099;
            bottom: -100px;
            right: -50px;
            animation-delay: -6s;
        }

        @keyframes orbFloat {
            0% { transform: translate(0, 0) scale(1); }
            100% { transform: translate(60px, 80px) scale(1.15); }
        }

        /* Header */
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 18px 8%;
            background: rgba(255, 255, 255, 0.85);
            backdrop-filter: blur(15px);
            box-shadow: 0 4px 30px rgba(0,0,0,0.05);
            position: sticky;
            top: 0;
            z-index: 1000;
            border-bottom: 1px solid rgba(255, 215, 0, 0.2);
        }

        .logo-container {
            display: flex;
            align-items: center;
            gap: 15px;
            animation: fadeInDown 1s ease;
        }

        .logo-container img {
            width: 52px;
            height: 52px;
            object-fit: cover;
            border-radius: 14px;
            box-shadow: 0 8px 20px var(--gold-glow);
            transform: perspective(500px) rotateY(15deg);
            transition: transform 0.4s ease, box-shadow 0.4s ease;
        }

        .logo-container img:hover {
            transform: perspective(500px) rotateY(0deg) scale(1.12);
            box-shadow: 0 12px 25px rgba(255, 215, 0, 0.7);
        }

        .logo-container h1 {
            font-size: 26px;
            font-weight: 800;
            letter-spacing: 1px;
        }

        /* Animated Gold Shimmer Text */
        .shimmer-text {
            background: linear-gradient(90deg, #b8970b 0%, #ffd700 50%, #b8970b 100%);
            background-size: 200% auto;
            color: transparent;
            -webkit-background-clip: text;
            animation: shimmer 3s linear infinite;
        }

        @keyframes shimmer {
            to { background-position: 200% center; }
        }

        nav {
            display: flex;
            gap: 30px;
        }

        nav a {
            text-decoration: none;
            color: var(--text-color);
            font-weight: 600;
            position: relative;
            transition: 0.3s;
        }

        nav a::after {
            content: '';
            position: absolute;
            width: 0;
            height: 3px;
            bottom: -5px;
            left: 0;
            background-color: var(--primary-yellow);
            border-radius: 2px;
            transition: width 0.3s ease;
        }

        nav a:hover::after { width: 100%; }
        nav a:hover { color: #b8970b; }

        /* 3D Hero Section */
        .hero {
            min-height: 85vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
            padding: 0 20px;
            position: relative;
        }

        .hero h2 {
            font-size: 3.8rem;
            margin-bottom: 20px;
            animation: fadeInUp 1s ease;
            line-height: 1.2;
            font-weight: 800;
        }

        .hero h2 span {
            display: inline-block;
            background: var(--primary-yellow);
            padding: 2px 16px;
            border-radius: 12px;
            box-shadow: 0 10px 25px var(--gold-glow);
            animation: pulseGlow 2.5s infinite alternate;
        }

        @keyframes pulseGlow {
            0% { box-shadow: 0 8px 20px rgba(255, 215, 0, 0.3); transform: translateY(0); }
            100% { box-shadow: 0 15px 35px rgba(255, 215, 0, 0.6); transform: translateY(-3px); }
        }

        .hero p {
            font-size: 1.25rem;
            color: #555;
            max-width: 650px;
            margin-bottom: 35px;
            animation: fadeInUp 1.2s ease;
        }

        .btn {
            background: linear-gradient(135deg, #ffd700, #ffcc00);
            color: #111;
            padding: 16px 42px;
            font-size: 1.15rem;
            font-weight: 700;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 10px 25px var(--gold-glow);
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 10px;
            position: relative;
            overflow: hidden;
        }

        .btn::after {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(60deg, transparent, rgba(255,255,255,0.4), transparent);
            transform: rotate(30deg);
            transition: 0.6s;
            opacity: 0;
        }

        .btn:hover::after {
            opacity: 1;
            left: 100%;
        }

        .btn:hover {
            transform: translateY(-7px) scale(1.05);
            box-shadow: 0 18px 38px rgba(255, 215, 0, 0.75);
        }

        /* Section Title */
        .section-title {
            text-align: center;
            font-size: 2.8rem;
            margin: 80px 0 40px;
            font-weight: 800;
        }

        /* 3D Pricing Cards with Tilt JS */
        .pricing-container {
            display: flex;
            justify-content: center;
            gap: 50px;
            padding: 20px 8%;
            flex-wrap: wrap;
        }

        .price-card {
            background: var(--card-bg);
            border-radius: 25px;
            padding: 50px 40px;
            width: 350px;
            max-width: 100%;
            text-align: center;
            box-shadow: var(--shadow);
            border-top: 8px solid var(--primary-yellow);
            border-left: 1px solid rgba(255,215,0,0.3);
            border-right: 1px solid rgba(255,215,0,0.3);
            transform-style: preserve-3d;
            transition: box-shadow 0.4s ease, border-color 0.4s ease;
        }

        .price-card:hover {
            box-shadow: 0 30px 60px rgba(255, 215, 0, 0.4);
            border-top-color: #ffcc00;
        }

        .price-card h3 {
            font-size: 2rem;
            margin-bottom: 15px;
            color: #222;
            transform: translateZ(30px);
        }

        .price-card .price {
            font-size: 3.2rem;
            color: #b8970b;
            margin-bottom: 25px;
            font-weight: 800;
            transform: translateZ(40px);
            text-shadow: 0 5px 15px rgba(255,215,0,0.3);
        }

        .price-card p {
            color: #666;
            margin-bottom: 30px;
            font-size: 1.05rem;
            transform: translateZ(20px);
        }

        .price-card .btn {
            transform: translateZ(35px);
        }

        /* 3D Order Form Box Section */
        .order-section {
            padding: 40px 8%;
            display: flex;
            justify-content: center;
        }

        .order-box {
            background: var(--card-bg);
            border-radius: 30px;
            padding: 50px;
            width: 100%;
            max-width: 600px;
            box-shadow: 0 25px 50px rgba(0,0,0,0.08);
            border: 2px solid #ffe875;
            transform-style: preserve-3d;
            transition: box-shadow 0.4s ease;
        }

        .order-box:hover {
            box-shadow: 0 30px 60px rgba(255, 215, 0, 0.3);
        }

        .order-box h3 {
            text-align: center;
            font-size: 2.2rem;
            margin-bottom: 25px;
            transform: translateZ(25px);
        }

        .form-group {
            margin-bottom: 20px;
            transform: translateZ(20px);
        }

        .form-group label {
            display: block;
            font-weight: 600;
            margin-bottom: 8px;
            color: #333;
        }

        .form-group input, .form-group select, .form-group textarea {
            width: 100%;
            padding: 14px 18px;
            border: 2px solid #e2e2e2;
            border-radius: 14px;
            font-size: 1rem;
            outline: none;
            transition: all 0.3s ease;
            background: #fafafa;
        }

        .form-group input:focus, .form-group select:focus, .form-group textarea:focus {
            border-color: var(--primary-yellow);
            background: #fff;
            box-shadow: 0 0 15px rgba(255, 215, 0, 0.4);
            transform: translateY(-2px);
        }

        .order-box .btn {
            width: 100%;
            margin-top: 10px;
            justify-content: center;
            transform: translateZ(30px);
        }

        /* 3D Portfolio Grid */
        .portfolio-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 35px;
            padding: 20px 8% 80px;
        }

        .portfolio-item {
            height: 360px;
            background: #fafafa;
            border-radius: 24px;
            overflow: hidden;
            box-shadow: 0 12px 30px rgba(0,0,0,0.07);
            border: 2px solid #f0e68c;
            position: relative;
            transform-style: preserve-3d;
            cursor: pointer;
        }

        .portfolio-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.6s cubic-bezier(0.165, 0.84, 0.44, 1);
        }

        .portfolio-item:hover img {
            transform: scale(1.12);
        }

        .portfolio-item::after {
            content: attr(data-title);
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            padding: 20px 15px;
            background: linear-gradient(to top, rgba(0,0,0,0.85), transparent);
            color: #fff;
            font-weight: 600;
            font-size: 1.05rem;
            text-align: center;
            transform: translateY(100%);
            transition: transform 0.4s ease;
        }

        .portfolio-item:hover::after {
            transform: translateY(0);
        }

        /* Scroll Entrance Animation Classes */
        .reveal {
            opacity: 0;
            transform: translateY(40px);
            transition: all 0.8s cubic-bezier(0.2, 0.8, 0.2, 1);
        }

        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }

        /* Footer */
        footer {
            background: #111;
            color: #fff;
            text-align: center;
            padding: 45px 20px;
            margin-top: 50px;
            border-top: 5px solid var(--primary-yellow);
        }

        footer h3 {
            font-size: 1.8rem;
            margin-bottom: 10px;
        }

        footer p {
            color: #aaa;
            font-size: 1rem;
            margin-top: 10px;
        }

        @keyframes fadeInDown {
            from { opacity: 0; transform: translateY(-30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Mobile Adjustments */
        @media (max-width: 768px) {
            header {
                flex-direction: column;
                gap: 15px;
                padding: 15px 5%;
            }

            nav { gap: 15px; flex-wrap: wrap; justify-content: center; }
            .hero h2 { font-size: 2.2rem; }
            .hero p { font-size: 1rem; }
            .section-title { font-size: 2rem; margin: 50px 0 25px; }
            .pricing-container { padding: 10px 5%; gap: 30px; }
            .price-card { padding: 35px 20px; }
            .order-section { padding: 20px 5%; }
            .order-box { padding: 25px 20px; }
            .portfolio-grid { padding: 10px 5% 50px; grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>

    <!-- Ambient Glowing Background -->
    <div class="ambient-bg">
        <div class="orb orb-1"></div>
        <div class="orb orb-2"></div>
    </div>

    <!-- Header Section -->
    <header>
        <div class="logo-container">
            <img src="logo.png" onerror="this.src='https://images.unsplash.com/photo-1579783902614-a3fb3927b675?w=100'" alt="Devartsx Logo">
            <h1>Devarts<span class="shimmer-text">x</span></h1>
        </div>
        <nav>
            <a href="#hero">Home</a>
            <a href="#portfolio">Portfolio</a>
            <a href="#pricing">Pricing</a>
            <a href="#order">Order Sketch</a>
        </nav>
    </header>

    <!-- 3D Hero Section -->
    <section class="hero" id="hero">
        <h2>Handmade Realistic <span>Sketches</span></h2>
        <p>Get custom graphite & charcoal portraits created with high precision. Perfect gift for your loved ones.</p>
        <a href="#order" class="btn"><i class="fa-solid fa-paintbrush"></i> Order Your Sketch</a>
    </section>

    <!-- 3D Portfolio Grid -->
    <h2 class="section-title reveal" id="portfolio">My <span class="shimmer-text">Portfolio</span></h2>
    <div class="portfolio-grid reveal">
        <div class="portfolio-item tilt-card" data-title="Shiv Parvati Sketch">
            <img src="shiva-parvati.jpg" onerror="this.src='https://images.unsplash.com/photo-1579783900882-c0d3dad7b119?w=600'" alt="Shiv Parvati Sketch">
        </div>
        <div class="portfolio-item tilt-card" data-title="Anime Art (Giyu Tomioka)">
            <img src="anime-giyu.jpg" onerror="this.src='https://images.unsplash.com/photo-1607604276583-eef5d076aa5f?w=600'" alt="Anime Art Giyu">
        </div>
        <div class="portfolio-item tilt-card" data-title="Lord Ganesha Portrait">
            <img src="ganesha.jpg" onerror="this.src='https://images.unsplash.com/photo-1578301978693-85fa9c0320b9?w=600'" alt="Lord Ganesha Artwork">
        </div>
        <div class="portfolio-item tilt-card" data-title="Hyper-Realistic Eye Study">
            <img src="eye-detail.jpg" onerror="this.src='https://images.unsplash.com/photo-1544717305-2782549b5136?w=600'" alt="Eye Sketch Artwork">
        </div>
    </div>

    <!-- 3D Pricing Cards -->
    <h2 class="section-title reveal" id="pricing">Sketch <span class="shimmer-text">Pricing</span></h2>
    <div class="pricing-container reveal">
        <div class="price-card tilt-card">
            <h3>A4 Size Sketch</h3>
            <div class="price">₹599</div>
            <p>Perfect choice for single face portraits & closeups with graphite shading.</p>
            <a href="#order" class="btn">Book A4 Size</a>
        </div>
        <div class="price-card tilt-card">
            <h3>A3 Size Sketch</h3>
            <div class="price">₹999</div>
            <p>Best for detailed couple portraits, religious art & deep charcoal work.</p>
            <a href="#order" class="btn">Book A3 Size</a>
        </div>
    </div>

    <!-- 3D Order Form Box Section -->
    <section class="order-section reveal" id="order">
        <div class="order-box tilt-card">
            <h3>Order <span class="shimmer-text">Your Sketch</span></h3>
            <form onsubmit="sendToWhatsApp(event)">
                <div class="form-group">
                    <label for="name">Your Name</label>
                    <input type="text" id="name" required placeholder="Enter your full name">
                </div>
                <div class="form-group">
                    <label for="phone">WhatsApp Phone Number</label>
                    <input type="tel" id="phone" required placeholder="Enter mobile number">
                </div>
                <div class="form-group">
                    <label for="size">Select Artwork Size</label>
                    <select id="size" required>
                        <option value="A4 Size Sketch (₹599)">A4 Size Sketch - ₹599</option>
                        <option value="A3 Size Sketch (₹999)">A3 Size Sketch - ₹999</option>
                    </select>
                </div>
                <div class="form-group">
                    <label for="notes">Special Instructions</label>
                    <textarea id="notes" rows="4" placeholder="Any specific requirements..."></textarea>
                </div>
                <button type="submit" class="btn"><i class="fa-brands fa-whatsapp" style="font-size:1.3rem;"></i> Order via WhatsApp</button>
            </form>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <h3>Devarts<span class="shimmer-text">x</span> Studio</h3>
        <p>&copy; 2026 Devartsx. All Rights Reserved.</p>
    </footer>

    <!-- Interactive JS Animations -->
    <script>
        // 1. Custom Smooth 3D Tilt Effect on Mouse Move
        const tiltCards = document.querySelectorAll('.tilt-card');

        tiltCards.forEach(card => {
            card.addEventListener('mousemove', (e) => {
                const rect = card.getBoundingClientRect();
                const x = e.clientX - rect.left;
                const y = e.clientY - rect.top;

                const centerX = rect.width / 2;
                const centerY = rect.height / 2;

                const rotateX = ((y - centerY) / centerY) * -12;
                const rotateY = ((x - centerX) / centerX) * 12;

                card.style.transform = `perspective(1000px) rotateX(${rotateX}deg) rotateY(${rotateY}deg) scale3d(1.02, 1.02, 1.02)`;
            });

            card.addEventListener('mouseleave', () => {
                card.style.transform = `perspective(1000px) rotateX(0deg) rotateY(0deg) scale3d(1, 1, 1)`;
                card.style.transition = 'transform 0.5s ease';
            });

            card.addEventListener('mouseenter', () => {
                card.style.transition = 'none';
            });
        });

        // 2. Scroll Reveal Entrance Animation
        const revealElements = document.querySelectorAll('.reveal');

        function checkReveal() {
            const windowHeight = window.innerHeight;
            revealElements.forEach(el => {
                const elementTop =

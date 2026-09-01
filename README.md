
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <style>
        :root {
            --bg-color: #fcfcfd;
            --text-color: #1a1a1a;
            --primary-yellow: #ffd700;
            --gold-glow: rgba(255, 215, 0, 0.4);
            --card-bg: rgba(255, 255, 255, 0.95);
            --shadow: 0 15px 35px rgba(0, 0, 0, 0.08);
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
            animation: fadeInBody 1.2s cubic-bezier(0.16, 1, 0.3, 1) forwards;
        }

        @keyframes fadeInBody {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Background Animated Orbs */
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
            opacity: 0.4;
            animation: orbFloat 12s infinite alternate ease-in-out;
        }

        .orb-1 {
            width: 350px;
            height: 350px;
            background: #ffe566;
            top: -40px;
            left: -40px;
        }

        .orb-2 {
            width: 400px;
            height: 400px;
            background: #fff099;
            bottom: -60px;
            right: -40px;
            animation-delay: -6s;
        }

        @keyframes orbFloat {
            0% { transform: translate(0, 0) scale(1); }
            100% { transform: translate(50px, 60px) scale(1.15); }
        }

        /* Header */
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 18px 8%;
            background: rgba(255, 255, 255, 0.85);
            backdrop-filter: blur(15px);
            box-shadow: 0 4px 20px rgba(0,0,0,0.05);
            position: sticky;
            top: 0;
            z-index: 1000;
            border-bottom: 2px solid rgba(255, 215, 0, 0.3);
            animation: slideDownHeader 0.8s cubic-bezier(0.16, 1, 0.3, 1) forwards;
        }

        @keyframes slideDownHeader {
            from { transform: translateY(-100%); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        .logo-container {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .logo-container img {
            width: 48px;
            height: 48px;
            object-fit: cover;
            border-radius: 12px;
            box-shadow: 0 6px 15px var(--gold-glow);
            transition: transform 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
        }

        .logo-container img:hover {
            transform: scale(1.12) rotate(3deg);
        }

        .logo-container h1 {
            font-size: 24px;
            font-weight: 800;
            letter-spacing: 0.5px;
        }

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
            gap: 25px;
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
            bottom: -4px;
            left: 0;
            background-color: var(--primary-yellow);
            border-radius: 2px;
            transition: width 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }

        nav a:hover::after { width: 100%; }
        nav a:hover { color: #b8970b; }

        /* Hero Section */
        .hero {
            min-height: 80vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
            padding: 40px 20px;
            animation: fadeZoomIn 1s cubic-bezier(0.16, 1, 0.3, 1) 0.2s forwards;
            opacity: 0;
        }

        @keyframes fadeZoomIn {
            from { opacity: 0; transform: scale(0.95) translateY(20px); }
            to { opacity: 1; transform: scale(1) translateY(0); }
        }

        .hero h2 {
            font-size: 3.5rem;
            margin-bottom: 20px;
            line-height: 1.2;
            font-weight: 800;
        }

        .hero h2 span {
            display: inline-block;
            background: var(--primary-yellow);
            padding: 4px 16px;
            border-radius: 12px;
            box-shadow: 0 8px 20px var(--gold-glow);
            animation: badgePulse 3s infinite ease-in-out;
        }

        @keyframes badgePulse {
            0%, 100% { transform: scale(1); box-shadow: 0 8px 20px var(--gold-glow); }
            50% { transform: scale(1.03); box-shadow: 0 12px 30px rgba(255, 215, 0, 0.6); }
        }

        .hero p {
            font-size: 1.2rem;
            color: #555;
            max-width: 600px;
            margin-bottom: 30px;
        }

        .btn {
            background: linear-gradient(135deg, #ffd700, #ffcc00);
            color: #111;
            padding: 16px 40px;
            font-size: 1.1rem;
            font-weight: 700;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 10px 25px var(--gold-glow);
            transition: all 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
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
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.4), transparent);
            transition: 0.5s;
        }

        .btn:hover::after {
            left: 100%;
        }

        .btn:hover {
            transform: translateY(-5px) scale(1.04);
            box-shadow: 0 18px 40px rgba(255, 215, 0, 0.75);
        }

        /* Section Titles */
        .section-title {
            text-align: center;
            font-size: 2.6rem;
            margin: 70px 0 35px;
            font-weight: 800;
            position: relative;
        }

        /* Portfolio Grid */
        .portfolio-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 30px;
            padding: 0 8% 60px;
        }

        .portfolio-item {
            height: 350px;
            background: #fafafa;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: var(--shadow);
            border: 2px solid #f0e68c;
            position: relative;
            cursor: pointer;
            transition: transform 0.5s cubic-bezier(0.16, 1, 0.3, 1), box-shadow 0.5s ease;
        }

        .portfolio-item:hover {
            transform: translateY(-12px) scale(1.02);
            box-shadow: 0 25px 50px rgba(255, 215, 0, 0.4);
        }

        .portfolio-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.6s cubic-bezier(0.16, 1, 0.3, 1);
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
            padding: 22px 15px;
            background: linear-gradient(to top, rgba(0,0,0,0.9), transparent);
            color: #fff;
            font-weight: 600;
            font-size: 1.05rem;
            text-align: center;
            transform: translateY(100%);
            transition: transform 0.4s cubic-bezier(0.16, 1, 0.3, 1);
        }

        .portfolio-item:hover::after {
            transform: translateY(0);
        }

        /* Pricing Cards */
        .pricing-container {
            display: flex;
            justify-content: center;
            gap: 40px;
            padding: 0 8% 40px;
            flex-wrap: wrap;
        }

        .price-card {
            background: var(--card-bg);
            border-radius: 24px;
            padding: 45px 35px;
            width: 340px;
            max-width: 100%;
            text-align: center;
            box-shadow: var(--shadow);
            border-top: 8px solid var(--primary-yellow);
            border-left: 1px solid rgba(255,215,0,0.3);
            border-right: 1px solid rgba(255,215,0,0.3);
            transition: transform 0.4s cubic-bezier(0.16, 1, 0.3, 1), box-shadow 0.4s ease;
        }

        .price-card:hover {
            transform: translateY(-12px) scale(1.03);
            box-shadow: 0 30px 60px rgba(255, 215, 0, 0.4);
        }

        .price-card h3 {
            font-size: 1.8rem;
            margin-bottom: 12px;
            color: #222;
        }

        .price-card .price {
            font-size: 3rem;
            color: #b8970b;
            margin-bottom: 20px;
            font-weight: 800;
            transition: transform 0.3s ease;
        }

        .price-card:hover .price {
            transform: scale(1.08);
        }

        .price-card p {
            color: #666;
            margin-bottom: 25px;
            font-size: 1rem;
        }

        /* Order Form Box */
        .order-section {
            padding: 30px 8% 60px;
            display: flex;
            justify-content: center;
        }

        .order-box {
            background: var(--card-bg);
            border-radius: 28px;
            padding: 45px;
            width: 100%;
            max-width: 580px;
            box-shadow: var(--shadow);
            border: 2px solid #ffe875;
            transition: transform 0.4s ease, box-shadow 0.4s ease;
        }

        .order-box:hover {
            transform: translateY(-5px);
            box-shadow: 0 30px 60px rgba(255, 215, 0, 0.3);
        }

        .order-box h3 {
            text-align: center;
            font-size: 2.1rem;
            margin-bottom: 25px;
        }

        .form-group {
            margin-bottom: 18px;
        }

        .form-group label {
            display: block;
            font-weight: 600;
            margin-bottom: 6px;
            color: #333;
        }

        .form-group input, .form-group select, .form-group textarea {
            width: 100%;
            padding: 14px 16px;
            border: 2px solid #e2e2e2;
            border-radius: 12px;
            font-size: 1rem;
            outline: none;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            background: #fafafa;
        }

        .form-group input:focus, .form-group select:focus, .form-group textarea:focus {
            border-color: var(--primary-yellow);
            background: #fff;
            box-shadow: 0 0 15px rgba(255, 215, 0, 0.4);
            transform: scale(1.01);
        }

        .order-box .btn {
            width: 100%;
            margin-top: 10px;
            justify-content: center;
        }

        /* Footer */
        footer {
            background: #111;
            color: #fff;
            text-align: center;
            padding: 40px 20px;
            margin-top: 40px;
            border-top: 5px solid var(--primary-yellow);
        }

        footer h3 {
            font-size: 1.8rem;
            margin-bottom: 8px;
        }

        footer p {
            color: #aaa;
            font-size: 0.95rem;
        }

        /* Mobile Responsive */
        @media (max-width: 768px) {
            header {
                flex-direction: column;
                gap: 12px;
                padding: 15px 5%;
            }

            nav { gap: 15px; flex-wrap: wrap; justify-content: center; }
            .hero h2 { font-size: 2.2rem; }
            .hero p { font-size: 1rem; }
            .section-title { font-size: 2rem; margin: 50px 0 25px; }
            .pricing-container { padding: 0 5% 30px; gap: 25px; }
            .price-card { padding: 35px 20px; }
            .order-section { padding: 20px 5% 40px; }
            .order-box { padding: 25px 20px; }
            .portfolio-grid { padding: 0 5% 40px; grid-template-columns: 1fr; }
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

    <!-- Hero Section -->
    <section class="hero" id="hero">
        <h2>Handmade Realistic <span>Sketches</span></h2>
        <p>Get custom graphite & charcoal portraits created with high precision. Perfect gift for your loved ones.</p>
        <a href="#order" class="btn"><i class="fa-solid fa-paintbrush"></i> Order Your Sketch</a>
    </section>

    <!-- Portfolio Grid -->
    <h2 class="section-title" id="portfolio">My <span class="shimmer-text">Portfolio</span></h2>
    <div class="portfolio-grid">
        <div class="portfolio-item" data-title="Shiv Parvati Sketch">
            <img src="shiva-parvati.jpg" onerror="this.src='https://images.unsplash.com/photo-1579783900882-c0d3dad7b119?w=600'" alt="Shiv Parvati Sketch">
        </div>
        <div class="portfolio-item" data-title="Anime Art (Giyu Tomioka)">
            <img src="anime-giyu.jpg" onerror="this.src='https://images.unsplash.com/photo-1607604276583-eef5d076aa5f?w=600'" alt="Anime Art Giyu">
        </div>
        <div class="portfolio-item" data-title="Lord Ganesha Portrait">
            <img src="ganesha.jpg" onerror="this.src='https://images.unsplash.com/photo-1578301978693-85fa9c0320b9?w=600'" alt="Lord Ganesha Artwork">
        </div>
        <div class="portfolio-item" data-title="Hyper-Realistic Eye Study">
            <img src="eye-detail.jpg" onerror="this.src='https://images.unsplash.com/photo-1544717305-2782549b5136?w=600'" alt="Eye Sketch Artwork">
        </div>
    </div>

    <!-- Pricing Section -->
    <h2 class="section-title" id="pricing">Sketch <span class="shimmer-text">Pricing</span></h2>
    <div class="pricing-container">
        <div class="price-card">
            <h3>A4 Size Sketch</h3>
            <div class="price">₹599</div>
            <p>Perfect choice for single face portraits & closeups with graphite shading.</p>
            <a href="#order" class="btn">Book A4 Size</a>
        </div>
        <div class="price-card">
            <h3>A3 Size Sketch</h3>
            <div class="price">₹999</div>
            <p>Best for detailed couple portraits, religious art & deep charcoal work.</p>
            <a href="#order" class="btn">Book A3 Size</a>
        </div>
    </div>

    <!-- Order Form Box Section -->
    <section class="order-section" id="order">
        <div class="order-box">
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
        <h3>Devarts<span class="shimmer-text">x</span> </h3>
        <p>&copy; 2026 Devartsx. All Rights Reserved.</p>
    </footer>

    <!-- WhatsApp Integration Script -->
    <script>
        function sendToWhatsApp(event) {
            event.preventDefault();
            const name = document.getElementById('name').value;
            const phone = document.getElementById('phone').value;
            const size = document.getElementById('size').value;
            const notes = document.getElementById('notes').value || 'None';

            const whatsappNumber = "917827417956";
            const message = `*NEW SKETCH ORDER - DEVARTSX*\n\n` +
                            `*Name:* ${name}\n` +
                            `*Phone:* ${phone}\n` +
                            `*Selected Size:* ${size}\n` +
                            `*Instructions:* ${notes}\n\n` +
                            `*(Please attach reference photo here)*`;

            window.location.href = `https://api.whatsapp.com/send?phone=${whatsappNumber}&text=${encodeURIComponent(message)}`;
        }
    </script>
</body>
</html>

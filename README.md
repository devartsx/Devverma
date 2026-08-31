<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Devartsx | Charcoal & Graphite Masterpieces</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-color: #ffffff;
            --primary-yellow: #FFD700;
            --dark-yellow: #f3c600;
            --text-color: #1a1a1a;
            --card-bg: rgba(255, 255, 255, 0.95);
            --shadow: 0 20px 40px rgba(0,0,0,0.08);
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
        }

        /* Header */
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 8%;
            background: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(10px);
            box-shadow: 0 4px 30px rgba(0,0,0,0.05);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .logo-container {
            display: flex;
            align-items: center;
            gap: 15px;
            animation: fadeInDown 1s ease;
        }

        .logo-container img {
            width: 50px;
            height: 50px;
            object-fit: cover;
            border-radius: 12px;
            box-shadow: 0 5px 15px rgba(255, 215, 0, 0.5);
            transform: perspective(500px) rotateY(15deg);
            transition: 0.4s;
        }

        .logo-container img:hover {
            transform: perspective(500px) rotateY(0deg) scale(1.1);
        }

        .logo-container h1 {
            font-size: 26px;
            font-weight: 700;
            letter-spacing: 1px;
        }

        .logo-container h1 span {
            color: #d4af37;
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
            height: 2px;
            bottom: -5px;
            left: 0;
            background-color: var(--primary-yellow);
            transition: width 0.3s;
        }

        nav a:hover::after {
            width: 100%;
        }

        nav a:hover {
            color: #b8970b;
        }

        /* 3D Hero Section */
        .hero {
            min-height: 85vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
            background: radial-gradient(circle, #fffdf0 0%, #ffffff 80%);
            padding: 0 20px;
            position: relative;
        }

        .hero h2 {
            font-size: 3.8rem;
            margin-bottom: 20px;
            animation: fadeInUp 1s ease;
            line-height: 1.2;
        }

        .hero h2 span {
            background: var(--primary-yellow);
            padding: 0 12px;
            border-radius: 10px;
            box-shadow: 0 10px 20px rgba(255, 215, 0, 0.3);
        }

        .hero p {
            font-size: 1.25rem;
            color: #555;
            max-width: 650px;
            margin-bottom: 35px;
            animation: fadeInUp 1.2s ease;
        }

        .btn {
            background: var(--primary-yellow);
            color: #111;
            padding: 16px 40px;
            font-size: 1.15rem;
            font-weight: 700;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 10px 25px rgba(255, 215, 0, 0.5);
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            text-decoration: none;
            display: inline-block;
        }

        .btn:hover {
            transform: translateY(-7px) scale(1.05);
            box-shadow: 0 15px 35px rgba(255, 215, 0, 0.8);
            background: #ffcc00;
        }

        /* Section Title */
        .section-title {
            text-align: center;
            font-size: 2.8rem;
            margin: 80px 0 40px;
            font-weight: 700;
        }

        .section-title span {
            color: #b8970b;
        }

        /* 3D Pricing Cards */
        .pricing-container {
            display: flex;
            justify-content: center;
            gap: 50px;
            padding: 20px 8%;
            flex-wrap: wrap;
        }

        .price-card {
            background: #fff;
            border-radius: 25px;
            padding: 50px 40px;
            width: 350px;
            text-align: center;
            box-shadow: var(--shadow);
            transition: all 0.5s ease;
            border-top: 10px solid var(--primary-yellow);
            transform: perspective(1000px) rotateX(8deg);
        }

        .price-card:hover {
            transform: perspective(1000px) rotateX(0deg) translateY(-15px);
            box-shadow: 0 30px 60px rgba(255, 215, 0, 0.35);
        }

        .price-card h3 {
            font-size: 2rem;
            margin-bottom: 15px;
            color: #222;
        }

        .price-card .price {
            font-size: 3rem;
            color: #b8970b;
            margin-bottom: 25px;
            font-weight: 700;
        }

        .price-card p {
            color: #666;
            margin-bottom: 30px;
            font-size: 1.05rem;
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
            box-shadow: 0 25px 50px rgba(0,0,0,0.1);
            border: 2px solid #ffe875;
            transform: perspective(1000px) rotateX(5deg);
            transition: transform 0.4s ease;
        }

        .order-box:hover {
            transform: perspective(1000px) rotateX(0deg);
        }

        .order-box h3 {
            text-align: center;
            font-size: 2.2rem;
            margin-bottom: 25px;
        }

        .order-box h3 span {
            color: #b8970b;
        }

        .form-group {
            margin-bottom: 20px;
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
            border: 2px solid #e0e0e0;
            border-radius: 12px;
            font-size: 1rem;
            outline: none;
            transition: 0.3s;
            background: #fafafa;
        }

        .form-group input:focus, .form-group select:focus, .form-group textarea:focus {
            border-color: var(--primary-yellow);
            background: #fff;
            box-shadow: 0 0 10px rgba(255, 215, 0, 0.3);
        }

        .order-box .btn {
            width: 100%;
            margin-top: 10px;
        }

        /* 3D Portfolio Grid */
        .portfolio-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            padding: 20px 8% 80px;
        }

        .portfolio-item {
            height: 350px;
            background: #fafafa;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0,0,0,0.06);
            transition: all 0.4s ease;
            border: 2px solid #f0e68c;
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .portfolio-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }

        .portfolio-item:hover img {
            transform: scale(1.1);
        }

        .portfolio-item::after {
            content: attr(data-title);
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            padding: 15px;
            background: linear-gradient(to top, rgba(0,0,0,0.8), transparent);
            color: #fff;
            font-weight: 600;
            text-align: center;
            transform: translateY(100%);
            transition: transform 0.3s ease;
        }

        .portfolio-item:hover::after {
            transform: translateY(0);
        }

        /* Footer */
        footer {
            background: #111;
            color: #fff;
            text-align: center;
            padding: 40px 20px;
            margin-top: 50px;
            border-top: 5px solid var(--primary-yellow);
        }

        footer h3 {
            font-size: 1.8rem;
            margin-bottom: 10px;
        }

        footer h3 span {
            color: var(--primary-yellow);
        }

        footer p {
            color: #aaa;
            font-size: 1.1rem;
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
    </style>
</head>
<body>

    <!-- Header -->
    <header>
        <div class="logo-container">
            <img src="logo.png" alt="Devartsx Logo">
            <h1>Devarts<span>x</span></h1>
        </div>
        <nav>
            <a href="#home">Home</a>
            <a href="#pricing">Pricing</a>
            <a href="#order">Order Now</a>
            <a href="#portfolio">Portfolio</a>
            <a href="#contact">Contact</a>
        </nav>
    </header>

    <!-- Hero Section -->
    <section class="hero" id="home">
        <h2>Realism Brought To Life With <span>Charcoal & Graphite</span></h2>
        <p>Welcome to Devartsx. Specializing in highly detailed, handmade professional charcoal and graphite pencil sketches.</p>
        <a href="#order" class="btn">Order Now</a>
    </section>

    <!-- Pricing Section -->
    <h2 class="section-title" id="pricing">Commission <span>Pricing</span></h2>
    <div class="pricing-container">
        <div class="price-card">
            <h3>A4 Size Sketch</h3>
            <div class="price">₹599</div>
            <p>Detailed single/couple portrait crafted carefully on premium A4 sheet using fine charcoal & graphite.</p>
            <a href="#order" class="btn">Order Now (A4)</a>
        </div>

        <div class="price-card">
            <h3>A3 Size Sketch</h3>
            <div class="price">₹999</div>
            <p>Large master portrait with extreme detailing on heavy professional A3 art paper.</p>
            <a href="#order" class="btn">Order Now (A3)</a>
        </div>
    </div>

    <!-- 3D Order Form Box Section -->
    <section class="order-section" id="order">
        <div class="order-box">
            <h3>Quick <span>Order Form</span></h3>
            <form id="whatsappForm" onsubmit="sendToWhatsApp(event)">
                <div class="form-group">
                    <label for="clientName">Your Name</label>
                    <input type="text" id="clientName" placeholder="Enter your full name" required>
                </div>

                <div class="form-group">
                    <label for="clientNumber">Your Mobile Number</label>
                    <input type="tel" id="clientNumber" placeholder="Enter your phone number" required>
                </div>

                <div class="form-group">
                    <label for="sketchSize">Select Size & Price</label>
                    <select id="sketchSize" required>
                        <option value="" disabled selected>Choose sketch size</option>
                        <option value="A4 Size - ₹599">A4 Size - ₹599</option>
                        <option value="A3 Size - ₹999">A3 Size - ₹999</option>
                    </select>
                </div>

                <div class="form-group">
                    <label for="customDetails">Customization & Instructions (Logo, Photo details etc.)</label>
                    <textarea id="customDetails" rows="4" placeholder="Mention any custom requirement, like adding a specific logo or text on sketch..."></textarea>
                </div>

                <button type="submit" class="btn">Send Order to WhatsApp 🚀</button>
            </form>
        </div>
    </section>

    <!-- Portfolio Section -->
    <h2 class="section-title" id="portfolio">Artistic <span>Portfolio</span></h2>
    <div class="portfolio-grid">
        <div class="portfolio-item" data-title="Shiv Parvati Ji Sketch">
            <img src="shiv-parvati.png" alt="Shiv Parvati Ji">
        </div>
        <div class="portfolio-item" data-title="Anime Sketch">
            <img src="anime.png" alt="Anime Sketch">
        </div>
        <div class="portfolio-item" data-title="Gojo Satoru Sketch">
            <img src="gojo.png" alt="Gojo Satoru">
        </div>
        <div class="portfolio-item" data-title="Realistic Eye Sketch">
            <img src="eye.png" alt="Realistic Eye">
        </div>
        <div class="portfolio-item" data-title="Ganpati Ji Sketch">
            <img src="ganpati.png" alt="Ganpati Ji">
        </div>
    </div>

    <!-- Footer / Contact Section -->
    <footer id="contact">
        <h3>Devarts<span>x</span></h3>
        <p>Charcoal & Graphite Sketch Artist</p>
        <p>📞 Direct Commission WhatsApp/Call: <strong>+91 7827417956</strong></p>
        <p style="font-size: 0.9rem; color: #777; margin-top: 20px;">© 2026 Devartsx. All Rights Reserved.</p>
    </footer>

    <!-- JavaScript for Direct WhatsApp Order Transmission -->
    <script>
        function sendToWhatsApp(event) {
            event.preventDefault();
            
            let name = document.getElementById('clientName').value;
            let number = document.getElementById('clientNumber').value;
            let size = document.getElementById('sketchSize').value;
            let custom = document.getElementById('customDetails').value;

            let phoneNumber = "917827417956";
            
            let message = `Hello Devartsx! I want to place a new sketch order.%0A%0A*Name:* ${name}%0A*Mobile:* ${number}%0A*Size:* ${size}%0A*Customization/Logo Details:* ${custom}`;
            
            let whatsappURL = `https://wa.me/${phoneNumber}?text=${message}`;
            
            window.open(whatsappURL, '_blank');
        }
    </script>

</body>
</html>

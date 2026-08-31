<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
    <title>Devsketches Studio</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-color: #ffffff;
            --text-color: #222222;
            --primary-yellow: #ffd700;
            --card-bg: #ffffff;
            --shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
        }

        *, *::before, *::after {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
            scroll-behavior: smooth;
            -webkit-tap-highlight-color: transparent;
        }

        html, body {
            width: 100%;
            max-width: 100%;
            overflow-x: hidden;
            background-color: var(--bg-color);
            color: var(--text-color);
        }

        img, video, canvas, svg {
            max-width: 100%;
            height: auto;
        }

        /* Header */
        header {
            width: 100%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 5%;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            box-shadow: 0 4px 30px rgba(0,0,0,0.05);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .logo-container {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .logo-container img {
            width: 45px;
            height: 45px;
            object-fit: cover;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(255, 215, 0, 0.5);
        }

        .logo-container h1 {
            font-size: 1.3rem;
            font-weight: 700;
            letter-spacing: 0.5px;
        }

        .logo-container h1 span {
            color: #d4af37;
        }

        nav {
            display: flex;
            gap: 15px;
        }

        nav a {
            text-decoration: none;
            color: var(--text-color);
            font-weight: 600;
            font-size: 0.95rem;
            position: relative;
            transition: 0.3s;
        }

        nav a::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: -4px;
            left: 0;
            background-color: var(--primary-yellow);
            transition: width 0.3s;
        }

        nav a:hover::after {
            width: 100%;
        }

        /* Hero Section */
        .hero {
            width: 100%;
            min-height: 75vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
            background: radial-gradient(circle, #fffdf0 0%, #ffffff 80%);
            padding: 40px 15px;
        }

        .hero h2 {
            font-size: clamp(1.8rem, 6vw, 3.5rem);
            margin-bottom: 15px;
            line-height: 1.25;
            word-break: break-word;
        }

        .hero h2 span {
            background: var(--primary-yellow);
            padding: 2px 10px;
            border-radius: 8px;
            box-shadow: 0 8px 18px rgba(255, 215, 0, 0.3);
            display: inline-block;
        }

        .hero p {
            font-size: clamp(0.95rem, 2.5vw, 1.2rem);
            color: #555;
            max-width: 600px;
            margin-bottom: 25px;
        }

        .btn {
            background: var(--primary-yellow);
            color: #111;
            padding: 12px 30px;
            font-size: 1rem;
            font-weight: 700;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 8px 20px rgba(255, 215, 0, 0.5);
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-block;
        }

        .btn:active, .btn:hover {
            transform: translateY(-2px);
            background: #ffcc00;
        }

        /* Section Title */
        .section-title {
            text-align: center;
            font-size: clamp(1.6rem, 5vw, 2.5rem);
            margin: 50px 0 25px;
            font-weight: 700;
            padding: 0 15px;
        }

        .section-title span {
            color: #b8970b;
        }

        /* Pricing Cards */
        .pricing-container {
            width: 100%;
            display: flex;
            justify-content: center;
            gap: 20px;
            padding: 10px 15px;
            flex-wrap: wrap;
        }

        .price-card {
            background: #fff;
            border-radius: 20px;
            padding: 30px 20px;
            width: 100%;
            max-width: 330px;
            text-align: center;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
            border-top: 6px solid var(--primary-yellow);
        }

        .price-card h3 {
            font-size: 1.5rem;
            margin-bottom: 10px;
            color: #222;
        }

        .price-card .price {
            font-size: 2.2rem;
            color: #b8970b;
            margin-bottom: 15px;
            font-weight: 700;
        }

        .price-card p {
            color: #666;
            margin-bottom: 20px;
            font-size: 0.95rem;
        }

        /* Order Form Box Section */
        .order-section {
            width: 100%;
            padding: 20px 15px;
            display: flex;
            justify-content: center;
        }

        .order-box {
            background: var(--card-bg);
            border-radius: 20px;
            padding: 25px 15px;
            width: 100%;
            max-width: 550px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.06);
            border: 2px solid #ffe875;
        }

        .order-box h3 {
            text-align: center;
            font-size: clamp(1.4rem, 4vw, 2rem);
            margin-bottom: 20px;
        }

        .order-box h3 span {
            color: #b8970b;
        }

        .form-group {
            margin-bottom: 15px;
        }

        .form-group label {
            display: block;
            font-weight: 600;
            margin-bottom: 6px;
            color: #333;
            font-size: 0.9rem;
        }

        .form-group input, .form-group select, .form-group textarea {
            width: 100%;
            padding: 12px 14px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 16px; /* Prevents auto-zoom on iOS Safari */
            outline: none;
            transition: 0.3s;
            background: #fafafa;
        }

        .form-group input:focus, .form-group select:focus, .form-group textarea:focus {
            border-color: var(--primary-yellow);
            background: #fff;
            box-shadow: 0 0 8px rgba(255, 215, 0, 0.3);
        }

        .order-box .btn {
            width: 100%;
            margin-top: 5px;
        }

        /* Portfolio Grid */
        .portfolio-grid {
            width: 100%;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(min(100%, 250px), 1fr));
            gap: 15px;
            padding: 10px 15px 50px;
        }

        .portfolio-item {
            height: 250px;
            background: #fafafa;
            border-radius: 16px;
            overflow: hidden;
            box-shadow: 0 8px 20px rgba(0,0,0,0.05);
            border: 2px solid #f0e68c;
            position: relative;
        }

        .portfolio-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .portfolio-item::after {
            content: attr(data-title);
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            padding: 12px;
            background: linear-gradient(to top, rgba(0,0,0,0.85), transparent);
            color: #fff;
            font-weight: 600;
            text-align: center;
            font-size: 0.9rem;
        }

        /* Footer */
        footer {
            width: 100%;
            background: #111;
            color: #fff;
            text-align: center;
            padding: 30px 15px;
            margin-top: 30px;
            border-top: 4px solid var(--primary-yellow);
        }

        footer h3 {
            font-size: 1.3rem;
            margin-bottom: 6px;
        }

        footer h3 span {
            color: var(--primary-yellow);
        }

        footer p {
            color: #aaa;
            font-size: 0.85rem;
            margin-top: 6px;
        }

        /* Mobile Layout Adjustments */
        @media (max-width: 600px) {
            header {
                flex-direction: column;
                gap: 10px;
                padding: 12px 10px;
            }
            
            nav {
                width: 100%;
                justify-content: center;
                gap: 12px;
                flex-wrap: wrap;
            }

            .hero {
                padding: 30px 10px;
                min-height: auto;
            }
        }

        /* Desktop 3D Effects */
        @media (min-width: 769px) {
            .logo-container img {
                transform: perspective(500px) rotateY(15deg);
            }
            .logo-container img:hover {
                transform: perspective(500px) rotateY(0deg) scale(1.1);
            }
            .price-card {
                transform: perspective(1000px) rotateX(8deg);
            }
            .price-card:hover {
                transform: perspective(1000px) rotateX(0deg) translateY(-15px);
            }
            .order-box {
                transform: perspective(1000px) rotateX(5deg);
            }
            .order-box:hover {
                transform: perspective(1000px) rotateX(0deg);
            }
        }
    </style>
</head>
<body>

    <header>
        <div class="logo-container">
            <img src="https://via.placeholder.com/50" alt="Logo">
            <h1>Devartsx<span>Studio</span></h1>
        </div>
        <nav>
            <a href="#hero">Home</a>
            <a href="#pricing">Pricing</a>
            <a href="#order">Order</a>
            <a href="#portfolio">Portfolio</a>
        </nav>
    </header>

    <section class="hero" id="hero">
        <h2>Bring Your Ideas To <span>Life</span></h2>
        <p>Custom drawings, artwork, and creative sketches designed for your brand and channels.</p>
        <a href="#order" class="btn">Order Now</a>
    </section>

    <h2 class="section-title" id="pricing">Our <span>Pricing</span></h2>
    <section class="pricing-container">
        <div class="price-card">
            <h3>Basic Sketch</h3>
            <div class="price">₹499</div>
            <p>Single subject pencil sketch with clean digital scan.</p>
            <a href="#order" class="btn">Select Plan</a>
        </div>
        <div class="price-card">
            <h3>Pro Artwork</h3>
            <div class="price">₹999</div>
            <p>Detailed artwork with shading and high resolution output.</p>
            <a href="#order" class="btn">Select Plan</a>
        </div>
    </section>

    <section class="order-section" id="order">
        <div class="order-box">
            <h3>Place Your <span>Order</span></h3>
            <form>
                <div class="form-group">
                    <label>Your Name</label>
                    <input type="text" placeholder="Enter your full name" required>
                </div>
                <div class="form-group">
                    <label>Email or Phone</label>
                    <input type="text" placeholder="Enter email or contact number" required>
                </div>
                <div class="form-group">
                    <label>Select Plan</label>
                    <select>
                        <option>A5 size Sketch (₹599)</option>
                        <option>A3 size Artwork (₹999)</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Details / Requirements</label>
                    <textarea rows="4" placeholder="Describe your sketch details..."></textarea>
                </div>
                <button type="submit" class="btn">Submit Order</button>
            </form>
        </div>
    </section>

    <h2 class="section-title" id="portfolio">Recent <span>Work</span></h2>
    <section class="portfolio-grid">
        <div class="portfolio-item" data-title="Pencil Portrait">
            <img src="https://via.placeholder.com/350" alt="Work 1">
        </div>
        <div class="portfolio-item" data-title="Digital Artwork">
            <img src="https://via.placeholder.com/350" alt="Work 2">
        </div>
        <div class="portfolio-item" data-title="Custom Sketch">
            <img src="https://via.placeholder.com/350" alt="Work 3">
        </div>
    </section>

    <footer>
        <h3>Devartsx <span>Studio</span></h3>
        <p>© 2026 All Rights Reserved.</p>
    </footer>

</body>
</html>

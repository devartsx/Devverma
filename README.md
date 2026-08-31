:root {
    --bg-color: #ffffff;
    --text-color: #222222;
    --primary-yellow: #ffd700;
    --card-bg: #ffffff;
    --shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Poppins', sans-serif;
    scroll-behavior: smooth;
    -webkit-tap-highlight-color: transparent;
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
    gap: 12px;
    animation: fadeInDown 1s ease;
}

.logo-container img {
    width: 45px;
    height: 45px;
    object-fit: cover;
    border-radius: 12px;
    box-shadow: 0 5px 15px rgba(255, 215, 0, 0.5);
    transition: 0.4s;
}

.logo-container h1 {
    font-size: 22px;
    font-weight: 700;
    letter-spacing: 1px;
}

.logo-container h1 span {
    color: #d4af37;
}

nav {
    display: flex;
    gap: 20px;
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

/* Hero Section */
.hero {
    min-height: 80vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    background: radial-gradient(circle, #fffdf0 0%, #ffffff 80%);
    padding: 40px 20px;
    position: relative;
}

.hero h2 {
    font-size: clamp(2.2rem, 6vw, 3.8rem);
    margin-bottom: 20px;
    animation: fadeInUp 1s ease;
    line-height: 1.25;
}

.hero h2 span {
    background: var(--primary-yellow);
    padding: 2px 12px;
    border-radius: 10px;
    box-shadow: 0 10px 20px rgba(255, 215, 0, 0.3);
    display: inline-block;
}

.hero p {
    font-size: clamp(1rem, 2.5vw, 1.25rem);
    color: #555;
    max-width: 650px;
    margin-bottom: 30px;
    animation: fadeInUp 1.2s ease;
}

.btn {
    background: var(--primary-yellow);
    color: #111;
    padding: 14px 35px;
    font-size: 1.05rem;
    font-weight: 700;
    border: none;
    border-radius: 50px;
    cursor: pointer;
    box-shadow: 0 10px 25px rgba(255, 215, 0, 0.5);
    transition: all 0.3s ease;
    text-decoration: none;
    display: inline-block;
}

.btn:active, .btn:hover {
    transform: translateY(-3px);
    box-shadow: 0 15px 35px rgba(255, 215, 0, 0.8);
    background: #ffcc00;
}

/* Section Title */
.section-title {
    text-align: center;
    font-size: clamp(2rem, 5vw, 2.8rem);
    margin: 60px 0 30px;
    font-weight: 700;
    padding: 0 15px;
}

.section-title span {
    color: #b8970b;
}

/* Pricing Cards */
.pricing-container {
    display: flex;
    justify-content: center;
    gap: 30px;
    padding: 20px 5%;
    flex-wrap: wrap;
}

.price-card {
    background: #fff;
    border-radius: 25px;
    padding: 40px 25px;
    width: 100%;
    max-width: 350px;
    text-align: center;
    box-shadow: var(--shadow);
    transition: all 0.4s ease;
    border-top: 8px solid var(--primary-yellow);
}

.price-card h3 {
    font-size: 1.8rem;
    margin-bottom: 15px;
    color: #222;
}

.price-card .price {
    font-size: 2.5rem;
    color: #b8970b;
    margin-bottom: 20px;
    font-weight: 700;
}

.price-card p {
    color: #666;
    margin-bottom: 25px;
    font-size: 1rem;
}

/* Order Form Box Section */
.order-section {
    padding: 30px 5%;
    display: flex;
    justify-content: center;
}

.order-box {
    background: var(--card-bg);
    border-radius: 25px;
    padding: 30px 20px;
    width: 100%;
    max-width: 600px;
    box-shadow: 0 15px 35px rgba(0,0,0,0.08);
    border: 2px solid #ffe875;
    transition: transform 0.3s ease;
}

.order-box h3 {
    text-align: center;
    font-size: clamp(1.6rem, 4vw, 2.2rem);
    margin-bottom: 20px;
}

.order-box h3 span {
    color: #b8970b;
}

.form-group {
    margin-bottom: 18px;
}

.form-group label {
    display: block;
    font-weight: 600;
    margin-bottom: 8px;
    color: #333;
    font-size: 0.95rem;
}

.form-group input, .form-group select, .form-group textarea {
    width: 100%;
    padding: 12px 15px;
    border: 2px solid #e0e0e0;
    border-radius: 12px;
    font-size: 16px; /* 16px text prevents iOS Safari zoom on focus */
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

/* Portfolio Grid */
.portfolio-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 20px;
    padding: 20px 5% 60px;
}

.portfolio-item {
    height: 280px;
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

.portfolio-item::after {
    content: attr(data-title);
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    padding: 15px;
    background: linear-gradient(to top, rgba(0,0,0,0.85), transparent);
    color: #fff;
    font-weight: 600;
    text-align: center;
    font-size: 0.95rem;
}

/* Footer */
footer {
    background: #111;
    color: #fff;
    text-align: center;
    padding: 35px 20px;
    margin-top: 40px;
    border-top: 5px solid var(--primary-yellow);
}

footer h3 {
    font-size: 1.5rem;
    margin-bottom: 8px;
}

footer h3 span {
    color: var(--primary-yellow);
}

footer p {
    color: #aaa;
    font-size: 0.95rem;
    margin-top: 8px;
}

@keyframes fadeInDown {
    from { opacity: 0; transform: translateY(-20px); }
    to { opacity: 1; transform: translateY(0); }
}

@keyframes fadeInUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
}

/* Mobile Layout Fixes */
@media (max-width: 768px) {
    header {
        flex-direction: column;
        gap: 12px;
        padding: 12px 15px;
    }
    
    nav {
        gap: 15px;
        flex-wrap: wrap;
        justify-content: center;
    }

    .hero {
        min-height: auto;
        padding: 50px 15px;
    }
}

/* 3D Tilt Effect - Desktop Only */
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
    .portfolio-item::after {
        transform: translateY(100%);
        transition: transform 0.3s ease;
    }
    .portfolio-item:hover::after {
        transform: translateY(0);
    }
    .portfolio-item:hover img {
        transform: scale(1.1);
    }
}

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Devartsx | Premium 3D Art Studio</title>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;600;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/vanilla-tilt/1.8.1/vanilla-tilt.min.js"></script>

    <style>
        :root {
            --bg-dark: #070a12;
            --card-bg: rgba(20, 27, 45, 0.65);
            --accent-blue: #38bdf8;
            --accent-purple: #818cf8;
            --accent-glow: rgba(56, 189, 248, 0.35);
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --border-color: rgba(255, 255, 255, 0.12);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Plus Jakarta Sans', sans-serif; scroll-behavior: smooth; }

        body {
            background-color: var(--bg-dark);
            color: var(--text-main);
            overflow-x: hidden;
            position: relative;
        }

        /* 3D WebGL Background Canvas */
        #webgl-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            z-index: -1;
            pointer-events: none;
        }

        /* Glassmorphic Navbar */
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 16px 8%;
            background: rgba(7, 10, 18, 0.85);
            backdrop-filter: blur(16px);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            border-bottom: 1px solid var(--border-color);
        }

        /* Logo and Brand Styling */
        .logo-container {
            display: flex;
            align-items: center;
            gap: 12px;
            text-decoration: none;
        }

        .logo-img {
            height: 42px;
            width: auto;
            object-fit: contain;
            filter: drop-shadow(0 0 8px var(--accent-glow));
        }

        .logo-text {
            font-size: 1.6rem;
            font-weight: 800;
            letter-spacing: 1px;
            color: #fff;
            text-shadow: 0 0 12px rgba(56, 189, 248, 0.3);
        }

        .logo-text span {
            color: var(--accent-blue);
        }

        .nav-links { display: flex; gap: 25px; list-style: none; }
        .nav-links a { color: var(--text-muted); text-decoration: none; font-weight: 500; transition: 0.3s; }
        .nav-links a:hover { color: var(--accent-blue); }

        /* Hero Section */
        .hero {
            padding: 170px 8% 90px;
            text-align: center;
            max-width: 900px;
            margin: 0 auto;
        }

        .badge {
            display: inline-block;
            padding: 8px 18px;
            background: rgba(56, 189, 248, 0.12);
            border: 1px solid rgba(56, 189, 248, 0.4);
            border-radius: 30px;
            color: var(--accent-blue);
            font-size: 0.85rem;
            font-weight: 600;
            margin-bottom: 25px;
            box-shadow: 0 0 20px var(--accent-glow);
        }

        .hero h1 { font-size: 3.6rem; font-weight: 800; line-height: 1.2; margin-bottom: 25px; }
        .hero h1 span {
            background: linear-gradient(135deg, #38bdf8 0%, #818cf8 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 0 30px rgba(56, 189, 248, 0.3);
        }

        .hero p { font-size: 1.15rem; color: var(--text-muted); margin-bottom: 40px; }

        .btn-primary {
            display: inline-flex;
            align-items: center;
            gap: 12px;
            padding: 16px 36px;
            background: linear-gradient(135deg, var(--accent-blue), var(--accent-purple));
            color: #070a12;
            text-decoration: none;
            font-weight: 800;
            border-radius: 50px;
            box-shadow: 0 10px 25px var(--accent-glow);
            transition: all 0.3s ease;
            position: relative;
            z-index: 5;
        }

        .btn-primary:hover { transform: translateY(-4px) scale(1.03); box-shadow: 0 15px 35px rgba(56, 189, 248, 0.5); }

        /* Sections */
        .section { 
            padding: 90px 8%; 
            max-width: 1200px; 
            margin: 0 auto; 
            scroll-margin-top: 80px; /* Fixes scroll position under navbar */
        }
        .section-header { text-align: center; margin-bottom: 60px; }
        .section-header h2 { font-size: 2.4rem; font-weight: 800; }
        .section-header p { color: var(--text-muted); margin-top: 10px; }

        /* 3D Gallery Grid */
        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(270px, 1fr));
            gap: 30px;
            perspective: 1000px;
        }

        .art-card {
            background: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 20px;
            overflow: hidden;
            backdrop-filter: blur(12px);
            transform-style: preserve-3d;
            box-shadow: 0 20px 40px rgba(0,0,0,0.4);
            transition: border-color 0.3s ease;
        }

        .art-card:hover { border-color: var(--accent-blue); }
        .art-card img { width: 100%; height: 380px; object-fit: cover; display: block; transform: translateZ(20px); }
        
        .art-info {
            padding: 20px;
            background: rgba(11, 15, 25, 0.95);
            border-top: 1px solid var(--border-color);
            transform: translateZ(30px);
        }
        .art-info h4 { font-size: 1.1rem; color: #fff; }
        .art-info p { font-size: 0.85rem; color: var(--text-muted); margin-top: 4px; }

        /* 3D Pricing Grid */
        .pricing-grid { 
            display: grid; 
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); 
            gap: 35px; 
            perspective: 1000px;
        }
        
        .price-card {
            background: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 24px;
            padding: 45px 35px;
            text-align: center;
            backdrop-filter: blur(12px);
            transform-style: preserve-3d;
            box-shadow: 0 20px 40px rgba(0,0,0,0.5);
            position: relative;
        }

        .price-card.popular {
            border-color: var(--accent-blue);
            box-shadow: 0 0 35px var(--accent-glow);
        }

        .price-card.popular::before {
            content: 'MOST POPULAR';
            position: absolute;
            top: -14px;
            left: 50%;
            transform: translateX(-50%) translateZ(40px);
            background: linear-gradient(135deg, var(--accent-blue), var(--accent-purple));
            color: #070a12;
            font-size: 0.75rem;
            font-weight: 800;
            padding: 6px 16px;
            border-radius: 20px;
        }

        .price-card h3 { font-size: 1.6rem; transform: translateZ(25px); }
        .price-card .price { font-size: 3.2rem; font-weight: 800; color: #fff; margin: 15px 0; transform: translateZ(35px); text-shadow: 0 0 20px var(--accent-glow); }
        .price-card ul { list-style: none; margin: 30px 0; text-align: left; transform: translateZ(20px); }
        .price-card ul li { padding: 12px 0; color: var(--text-muted); border-bottom: 1px solid rgba(255,255,255,0.06); }
        .price-card ul li i { color: var(--accent-blue); margin-right: 12px; }

        /* Form Styling (Touch-friendly & Layered) */
        .form-box {
            background: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 24px;
            padding: 45px;
            max-width: 650px;
            margin: 0 auto;
            backdrop-filter: blur(12px);
            box-shadow: 0 25px 50px rgba(0,0,0,0.6);
            position: relative;
            z-index: 10;
        }

        .form-group { margin-bottom: 24px; text-align: left; position: relative; z-index: 10; }
        .form-group label { display: block; margin-bottom: 8px; font-weight: 600; font-size: 0.9rem; color: #cbd5e1; }
        .form-group input, .form-group select, .form-group textarea {
            width: 100%;
            padding: 15px 18px;
            background: rgba(10, 14, 26, 0.95);
            border: 1px solid var(--border-color);
            border-radius: 12px;
            color: #fff;
            font-size: 1rem;
            outline: none;
            transition: 0.3s;
            position: relative;
            z-index: 10;
        }

        .form-group input:focus, .form-group select:focus, .form-group textarea:focus {
            border-color: var(--accent-blue);
            box-shadow: 0 0 15px var(--accent-glow);
        }

        .btn-submit {
            width: 100%;
            padding: 18px;
            background: linear-gradient(135deg, #25d366, #128c7e);
            color: #fff;
            border: none;
            border-radius: 12px;
            font-size: 1.1rem;
            font-weight: 800;
            cursor: pointer;
            transition: 0.3s;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 10px;
            box-shadow: 0 10px 25px rgba(37, 211, 102, 0.3);
            position: relative;
            z-index: 10;
        }

        .btn-submit:hover { opacity: 0.95; transform: translateY(-3px); box-shadow: 0 15px 35px rgba(37, 211, 102, 0.5); }

        /* Floating WhatsApp Button */
        .float-wa {
            position: fixed;
            bottom: 30px;
            right: 30px;
            background: #25d366;
            color: #fff;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 2rem;
            box-shadow: 0 10px 25px rgba(37, 211, 102, 0.5);
            text-decoration: none;
            z-index: 1000;
            transition: 0.3s;
        }
        .float-wa:hover { transform: scale(1.15) rotate(10deg); }

        footer { text-align: center; padding: 40px; border-top: 1px solid var(--border-color); color: var(--text-muted); font-size: 0.9rem; }

        @media (max-width: 768px) {
            .hero h1 { font-size: 2.4rem; }
            .nav-links { display: none; }
            .form-box { padding: 25px; }
        }
    </style>
</head>
<body>

    <canvas id="webgl-bg"></canvas>

    <nav>
        <a href="#" class="logo-container">
            <img src="logo.png" alt="Devartsx Logo" class="logo-img" id="main-logo">
            <span class="logo-text">Devartsx</span>
        </a>
        <ul class="nav-links">
            <li><a href="#gallery">Gallery</a></li>
            <li><a href="#pricing">Pricing</a></li>
            <li><a href="#order">Order Commission</a></li>
        </ul>
    </nav>

    <section class="hero">
        <span class="badge"><i class="fa-solid fa-cube"></i> Charcoal & Graphite 3D Art Studio</span>
        <h1>Bring Your Favorite Photos To Life With <span>Handmade Art</span></h1>
        <p>Get custom, highly-detailed pencil portraits drawn with premium graphite & charcoal. Perfect for personal keepsakes and memorable gifts.</p>
        <a href="#order" class="btn-primary"><i class="fa-solid fa-paper-plane"></i> Order Your Sketch Now</a>
    </section>

    <section class="section" id="gallery">
        <div class="section-header">
            <h2>Featured Artworks</h2>
            <p>100% Hand-drawn with Graphite & Charcoal Pencils</p>
        </div>
        <div class="gallery-grid">
            <div class="art-card" data-tilt data-tilt-max="15" data-tilt-speed="400" data-tilt-glare data-tilt-max-glare="0.2">
                <img src="shiva-parvati.jpg" alt="Divine Shiva Parvati Charcoal Sketch">
                <div class="art-info">
                    <h4>Shiv Parvati Sketch</h4>
                    <p>Charcoal & Graphite Medium</p>
                </div>
            </div>
            <div class="art-card" data-tilt data-tilt-max="15" data-tilt-speed="400" data-tilt-glare data-tilt-max-glare="0.2">
                <img src="anime-giyu.jpg" alt="Anime Sketch">
                <div class="art-info">
                    <h4>Anime Art (Giyu Tomioka)</h4>
                    <p>Graphite Pencil Artwork</p>
                </div>
            </div>
            <div class="art-card" data-tilt data-tilt-max="15" data-tilt-speed="400" data-tilt-glare data-tilt-max-glare="0.2">
                <img src="ganesha.jpg" alt="Lord Ganesha Artwork">
                <div class="art-info">
                    <h4>Lord Ganesha Portrait</h4>
                    <p>Detailed Charcoal Art</p>
                </div>
            </div>
            <div class="art-card" data-tilt data-tilt-max="15" data-tilt-speed="400" data-tilt-glare data-tilt-max-glare="0.2">
                <img src="eye-detail.jpg" alt="Hyperrealistic Eye Sketch">
                <div class="art-info">
                    <h4>Hyper-Realistic Eye Study</h4>
                    <p>Graphite Pencil Detail</p>
                </div>
            </div>
        </div>
    </section>

    <section class="section" id="pricing">
        <div class="section-header">
            <h2>Commission Pricing</h2>
            <p>Choose the size that best fits your room or gift requirements</p>
        </div>
        <div class="pricing-grid">
            <div class="price-card" data-tilt data-tilt-max="10" data-tilt-speed="400">
                <h3>A4 Portrait</h3>
                <p style="color:var(--text-muted); margin-top:5px;">Ideal for single faces & closeups</p>
                <div class="price">₹599</div>
                <ul>
                    <li><i class="fa-solid fa-check"></i> Size: 8.3 x 11.7 Inches</li>
                    <li><i class="fa-solid fa-check"></i> Premium Heavyweight Paper</li>
                    <li><i class="fa-solid fa-check"></i> Graphite & Charcoal Blend</li>
                    <li><i class="fa-solid fa-check"></i> Fixed Spray Protection Layer</li>
                </ul>
                <a href="#order" class="btn-primary" style="width:100%; justify-content:center;">Book A4 Size</a>
            </div>

            <div class="price-card popular" data-tilt data-tilt-max="12" data-tilt-speed="400">
                <h3>A3 Portrait</h3>
                <p style="color:var(--text-muted); margin-top:5px;">Best for full detail & couple portraits</p>
                <div class="price">₹999</div>
                <ul>
                    <li><i class="fa-solid fa-check"></i> Size: 11.7 x 16.5 Inches</li>
                    <li><i class="fa-solid fa-check"></i> High-Detail Charcoal Depth</li>
                    <li><i class="fa-solid fa-check"></i> Premium Archival Quality Paper</li>
                    <li><i class="fa-solid fa-check"></i> Fixed Spray Protection Layer</li>
                </ul>
                <a href="#order" class="btn-primary" style="width:100%; justify-content:center;">Book A3 Size</a>
            </div>
        </div>
    </section>

    <section class="section" id="order">
        <div class="section-header">
            <h2>Place Commission Request</h2>
            <p>Fill out the details below to initiate your portrait request</p>
        </div>
        <div class="form-box">
            <form onsubmit="sendToWhatsApp(event)">
                <div class="form-group">
                    <label for="name">Your Name</label>
                    <input type="text" id="name" required placeholder="Enter your full name">
                </div>
                <div class="form-group">
                    <label for="phone">WhatsApp Number</label>
                    <input type="tel" id="phone" required placeholder="Enter active mobile number">
                </div>
                <div class="form-group">
                    <label for="size">Artwork Size</label>
                    <select id="size" required>
                        <option value="A4 Size Portrait (₹599)">A4 Size Portrait - ₹599</option>
                        <option value="A3 Size Portrait (₹999)">A3 Size Portrait - ₹999</option>
                    </select>
                </div>
                <div class="form-group">
                    <label for="instructions">Custom Notes / Special Instructions</label>
                    <textarea id="instructions" rows="4" placeholder="Mention any extra details (e.g., date required, specific background requests)..."></textarea>
                </div>
                <button type="submit" class="btn-submit">
                    <i class="fa-brands fa-whatsapp" style="font-size:1.4rem;"></i> Continue Order on WhatsApp
                </button>
            </form>
        </div>
    </section>

    <a href="https://api.whatsapp.com/send?phone=917827417956" target="_blank" class="float-wa" title="Chat on WhatsApp">
        <i class="fa-brands fa-whatsapp"></i>
    </a>

    <footer>
        <p>&copy; 2026 Devartsx. All Rights Reserved. Crafted for Art Lovers.</p>
    </footer>

    <script>
        // Automatic White Background Removal Script for Logo
        window.addEventListener('DOMContentLoaded', () => {
            const logoImg = document.getElementById('main-logo');
            if (!logoImg) return;

            const removeWhiteBg = () => {
                try {
                    const canvas = document.createElement('canvas');
                    const ctx = canvas.getContext('2d');
                    canvas.width = logoImg.naturalWidth || logoImg.width;
                    canvas.height = logoImg.naturalHeight || logoImg.height;
                    
                    if (!canvas.width || !canvas.height) return;
                    
                    ctx.drawImage(logoImg, 0, 0);
                    const imgData = ctx.getImageData(0, 0, canvas.width, canvas.height);
                    const data = imgData.data;
                    
                    for (let i = 0; i < data.length; i += 4) {
                        if (data[i] > 200 && data[i + 1] > 200 && data[i + 2] > 200) {
                            data[i + 3] = 0; // Set White Pixels to 100% Transparent
                        }
                    }
                    ctx.putImageData(imgData, 0, 0);
                    logoImg.src = canvas.toDataURL('image/png');
                } catch (e) {
                    console.log("Canvas processing active");
                }
            };

            if (logoImg.complete) {
                removeWhiteBg();
            } else {
                logoImg.onload = removeWhiteBg;
            }
        });

        // Three.js Interactive 3D Canvas
        const canvas = document.getElementById('webgl-bg');
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer({ canvas: canvas, alpha: true, antialias: true });

        renderer.setSize(window.innerWidth, window.innerHeight);
        renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));

        const particlesCount = 200;
        const positions = new Float32Array(particlesCount * 3);

        for(let i = 0; i < particlesCount * 3; i++) {
            positions[i] = (Math.random() - 0.5) * 15;
        }

        const geometry = new THREE.BufferGeometry();
        geometry.setAttribute('position', new THREE.BufferAttribute(positions, 3));

        const material = new THREE.PointsMaterial({
            size: 0.04,
            color: 0x38bdf8,
            transparent: true,
            opacity: 0.7
        });

        const particlesMesh = new THREE.Points(geometry, material);
        scene.add(particlesMesh);

        const shapeGeometry = new THREE.IcosahedronGeometry(2, 1);
        const shapeMaterial = new THREE.MeshBasicMaterial({
            color: 0x818cf8,
            wireframe: true,
            transparent: true,
            opacity: 0.15
        });
        const shapeMesh = new THREE.Mesh(shapeGeometry, shapeMaterial);
        shapeMesh.position.set(2, 0, -3);
        scene.add(shapeMesh);

        camera.position.z = 4;

        let mouseX = 0, mouseY = 0;
        window.addEventListener('mousemove', (e) => {
            mouseX = (e.clientX / window.innerWidth - 0.5) * 0.5;
            mouseY = (e.clientY / window.innerHeight - 0.5) * 0.5;
        });

        const clock = new THREE.Clock();
        function animate() {
            const elapsedTime = clock.getElapsedTime();

            particlesMesh.rotation.y = elapsedTime * 0.05;
            particlesMesh.rotation.x = elapsedTime * 0.03;

            shapeMesh.rotation.x = elapsedTime * 0.2;
            shapeMesh.rotation.y = elapsedTime * 0.25;

            camera.position.x += (mouseX - camera.position.x) * 0.05;
            camera.position.y += (-mouseY - camera.position.y) * 0.05;

            renderer.render(scene, camera);
            requestAnimationFrame(animate);
        }
        animate();

        window.addEventListener('resize', () => {
            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();
            renderer.setSize(window.innerWidth, window.innerHeight);
        });

        function sendToWhatsApp(event) {
            event.preventDefault();
            const name = document.getElementById('name').value;
            const phone = document.getElementById('phone').value;
            const size = document.getElementById('size').value;
            const instructions = document.getElementById('instructions').value || 'None';
            
            const whatsappNumber = "917827417956"; 
            
            const rawMessage = `*NEW COMMISSION ORDER - DEVARTSX*\n\n` +
                               `*Customer Name:* ${name}\n` +
                               `*Contact Number:* ${phone}\n` +
                               `*Selected Size:* ${size}\n` +
                               `*Instructions:* ${instructions}\n\n` +
                               `*(Note: Please attach your reference photo in this WhatsApp chat now)*`;

            const encodedMessage = encodeURIComponent(rawMessage);
            window.location.href = `https://api.whatsapp.com/send?phone=${whatsappNumber}&text=${encodedMessage}`;
        }
    </script>
</body>
</html>

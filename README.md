<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Antony Ngugi // Visual Creator</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Archivo+Black&family=Montserrat:wght@300;400;700;900&family=Playfair+Display:ital,wght@0,600;1,600&display=swap');

        :root {
            --text-main: #ffffff;
            --text-muted: #aaaaaa;
            --accent-red: #d30000;
            --accent-gold: #ffc107;
            --accent-blue: #00bcd4;
        }

        /* Base & Typography */
        body { background-color: #050505; color: var(--text-main); font-family: 'Montserrat', sans-serif; margin: 0; padding: 0; line-height: 1.6; overflow-x: hidden; }
        h1, h2, h3, h4 { font-family: 'Archivo Black', sans-serif; text-transform: uppercase; margin: 0; }
        .container { max-width: 1200px; margin: 0 auto; padding: 0 20px; }

        /* HERO SECTION */
        .hero { display: flex; align-items: center; justify-content: space-between; min-height: 100vh; background: linear-gradient(135deg, #050505 40%, #3a1c0d 70%, #ff8c00 100%); padding: 50px 20px; }
        .welcome-text { font-size: 1.3rem; color: var(--accent-gold); font-weight: 700; text-transform: uppercase; letter-spacing: 3px; margin-bottom: 15px; }
        .hero-text h1 { font-family: 'Playfair Display', serif; text-transform: none; font-size: 6.5rem; line-height: 0.95; margin-bottom: 20px; letter-spacing: -2px; text-shadow: 2px 2px 10px rgba(0,0,0,0.5); }
        .hero-text .subtitle { font-size: 1.5rem; color: #ddd; letter-spacing: 3px; margin-top: 10px; text-transform: uppercase; }
        .hero-image { max-width: 45%; }
        .hero-image img { width: 100%; border: 2px solid #fff; box-shadow: 15px 15px 0px rgba(0,0,0,0.7); }

        /* DIVIDERS */
        .shutter-divider { position: relative; padding: 80px 0; text-align: center; background: repeating-linear-gradient(to bottom, #111111, #111111 8px, #000000 8px, #000000 10px); border-top: 2px solid #222; border-bottom: 2px solid #222; }
        .shutter-divider::before { content: ''; position: absolute; top: 0; bottom: 0; left: 50%; transform: translateX(-50%); width: 40px; border-left: 10px solid var(--accent-red); border-right: 10px solid var(--accent-red); z-index: 1; opacity: 0.8; }
        .shutter-content { position: relative; z-index: 2; }
        .shutter-content h2 { font-size: 4.5rem; text-shadow: 4px 4px 10px rgba(0,0,0,0.9); }
        .shutter-content .skill-tag { font-family: 'Montserrat', sans-serif; font-weight: 300; letter-spacing: 5px; font-size: 1.2rem; margin-bottom: 10px; }

        /* SECTION BACKGROUNDS */
        .section-photography { background: radial-gradient(circle at top center, #2c1a12 0%, #050505 60%); padding: 80px 0; overflow: hidden; }
        .section-videography { background: #ffffff; padding: 100px 0; color: #111; overflow: hidden; }
        
        .layout-wrapper { display: flex; flex-direction: column; align-items: center; gap: 20px; }
        .large-number { font-size: 12rem; color: transparent; -webkit-text-stroke: 2px #555; line-height: 0.8; margin-bottom: 10px; }
        .section-videography .large-number { -webkit-text-stroke: 2px #e0e0e0; }
        .side-info { width: 100%; max-width: 800px; text-align: center; margin: 0 auto 20px auto; }

        /* HORIZONTAL SCROLL CONTAINERS */
        .scroll-wrapper { width: 100%; position: relative; }
        .scroll-hint { text-align: center; color: var(--text-muted); margin-bottom: 15px; font-size: 0.9rem; font-style: italic; }
        
        .scroll-container {
            display: flex;
            overflow-x: auto;
            gap: 25px;
            width: 100%;
            padding-bottom: 20px;
            scroll-snap-type: x mandatory;
            -webkit-overflow-scrolling: touch;
            scrollbar-width: thin; 
            scrollbar-color: var(--accent-red) rgba(255, 255, 255, 0.05);
        }

        /* Custom Desktop Scrollbar */
        .scroll-container::-webkit-scrollbar { height: 10px; }
        .scroll-container::-webkit-scrollbar-track { background: rgba(255, 255, 255, 0.05); border-radius: 10px; }
        .scroll-container::-webkit-scrollbar-thumb { background: var(--accent-red); border-radius: 10px; cursor: pointer; }
        .scroll-container::-webkit-scrollbar-thumb:hover { background: #ff0000; }
        
        /* Videography specifically has a white background, invert track color */
        .section-videography .scroll-container::-webkit-scrollbar-track { background: rgba(0, 0, 0, 0.05); }
        .section-videography .scroll-container { scrollbar-color: var(--accent-blue) rgba(0, 0, 0, 0.05); }
        .section-videography .scroll-container::-webkit-scrollbar-thumb { background: var(--accent-blue); }

        /* SCROLL CARDS */
        .media-card { 
            flex: 0 0 320px; 
            scroll-snap-align: start; 
            background: rgba(0, 0, 0, 0.4); 
            padding: 10px; 
            border: 1px solid rgba(255,255,255,0.1); 
            border-radius: 8px; 
            transition: transform 0.3s ease, border-color 0.3s ease; 
        }
        .media-card:hover { transform: translateY(-5px); border-color: rgba(255,255,255,0.3); }
        .media-card img { width: 100%; border-radius: 4px; margin-bottom: 10px; display: block; }
        .media-card h3 { font-size: 1.1rem; font-family: 'Montserrat', sans-serif; font-weight: 700; margin-bottom: 5px; color: #fff; }
        .media-card p { font-size: 0.85rem; color: var(--text-muted); margin: 0; }

        .editorial-matte-card { 
            flex: 0 0 450px; 
            scroll-snap-align: start;
            background: #fdfdfd; 
            border-radius: 12px; 
            padding: 25px; 
            border: 2px solid var(--accent-blue); 
            box-shadow: 0 10px 25px rgba(0,188,212,0.15); 
            transition: transform 0.3s ease, box-shadow 0.3s ease, border-color 0.3s ease; 
        }
        .editorial-matte-card:hover { transform: translateY(-5px); box-shadow: 0 15px 35px rgba(0,188,212,0.3); border-color: var(--accent-red); }
        .editorial-matte-card img { width: 100%; border-radius: 6px; margin-bottom: 15px; border: 1px solid #eee; display: block; }
        .editorial-matte-card h3 { font-family: 'Archivo Black', sans-serif; font-size: 1.4rem; color: var(--accent-red); margin-bottom: 8px; }
        .editorial-matte-card p { font-size: 0.95rem; color: #444; font-weight: 500; line-height: 1.5; margin: 0; }

        /* CV & RESUME SECTION */
        .section-resume { background: #080808; padding: 80px 0; border-top: 1px solid #222; }
        .cv-grid { display: grid; grid-template-columns: 1fr 2fr; gap: 50px; }
        .cv-sidebar { background: #111; padding: 30px; border-radius: 8px; border: 1px solid #222; }
        .cv-sidebar h3 { color: var(--accent-red); margin-bottom: 15px; margin-top: 25px; }
        .cv-sidebar h3:first-child { margin-top: 0; }
        .cv-sidebar ul { list-style: none; padding: 0; }
        .cv-sidebar li { margin-bottom: 8px; font-size: 0.9rem; }
        
        .job-entry { background: #111; padding: 30px; border-radius: 8px; border: 1px solid #222; margin-bottom: 30px; }
        .job-entry h4 { font-size: 1.5rem; color: #fff; }
        .job-entry p.company { font-weight: 700; color: #ddd; margin: 5px 0; }
        .job-entry p.date { color: var(--accent-red); font-family: monospace; font-size: 1rem; margin-bottom: 15px; }

        /* FOOTER / CONTACT */
        footer { background: #000; padding: 100px 0; text-align: center; border-top: 2px solid #222; }
        .footer-photo img { width: 250px; height: 250px; object-fit: cover; border-radius: 50%; border: 3px solid var(--accent-red); margin-bottom: 30px; box-shadow: 0px 10px 30px rgba(211, 0, 0, 0.2); }

        /* RESPONSIVE MEDIA QUERIES */
        @media (max-width: 1024px) {
            .editorial-matte-card { flex: 0 0 60vw; }
        }
        @media (max-width: 900px) {
            .hero { flex-direction: column; text-align: center; }
            .hero-image { max-width: 80%; margin-top: 40px; }
            .cv-grid { grid-template-columns: 1fr; }
            .shutter-content h2 { font-size: 3rem; }
            .hero-text h1 { font-size: 4.5rem; }
        }
        @media (max-width: 768px) {
            .media-card { flex: 0 0 85vw; }
            .editorial-matte-card { flex: 0 0 85vw; padding: 20px; }
            .scroll-container { gap: 15px; }
            .large-number { font-size: 8rem; }
        }
    </style>
</head>
<body>

    <header class="hero">
        <div class="container" style="display: flex; align-items: center; justify-content: space-between; width: 100%; flex-wrap: wrap;">
            <div class="hero-text">
                <p class="welcome-text">Hey there! Welcome to my world.</p>
                <h1>Antony<br>Ngugi</h1>
                <p class="subtitle"><span style="color: var(--accent-red);">//</span> VISUAL CREATOR</p>
                <p style="max-width: 400px; margin-top: 20px; color: #ccc; font-size: 1.1rem;">
                    I'm thrilled you stopped by. I am a dynamic visual creator with over 3 years of dedicated experience in high-end photography, cinematic videography, and advanced digital imaging. Let's create something extraordinary together!
                </p>
            </div>
            <div class="hero-image">
                <img src="images/IMG_09560.png" alt="Antony Ngugi behind the lens">
            </div>
        </div>
    </header>

    <div class="shutter-divider">
        <div class="shutter-content">
            <p class="skill-tag">SKILL 1</p>
            <h2>PHOTOGRAPHY</h2>
            <p style="color: var(--accent-red); font-family: 'Script', cursive; font-size: 1.5rem; transform: rotate(-5deg); margin-top: -15px;">Lightroom Classic</p>
        </div>
    </div>

    <section class="section-photography">
        <div class="container layout-wrapper">
            <div class="side-info">
                <div class="large-number">01</div>
                <p style="color: #ccc; font-size: 0.9rem;">
                    These skills encompass studio and lifestyle composition, creative art direction, and meticulous high-end retouching.
                </p>
            </div>
            
            <div class="scroll-wrapper">
                <p class="scroll-hint">&larr; Scroll to view projects &rarr;</p>
                <div class="scroll-container">
                    <div class="media-card"><img src="images/IMG_9509.jpg" alt="Commercial Studio"><h3>Commercial &amp; Studio</h3><p>Low-key lighting setups.</p></div>
                    <div class="media-card"><img src="images/IMG_7740.jpg" alt="Commercial Studio 2"><h3>Art Direction</h3><p>Precise continuous lighting.</p></div>
                    <div class="media-card"><img src="images/IMG_9549.jpg" alt="Studio Detail"><h3>High-End Retouching</h3><p>Digital imaging.</p></div>
                    <div class="media-card"><img src="images/_MG_8766.jpg" alt="Event Lifestyle"><h3>Event &amp; Lifestyle</h3><p>Dynamic event coverage.</p></div>
                    <div class="media-card"><img src="images/_MG_8094.jpg" alt="Flash Photography"><h3>Dynamic Lighting</h3><p>Ambient and flash setups.</p></div>
                    <div class="media-card"><img src="images/_MG_8720.jpg" alt="Candid Capture"><h3>Visual Storytelling</h3><p>Authentic connections.</p></div>
                </div>
            </div>
        </div>
    </section>

    <div class="shutter-divider">
        <div class="shutter-content">
            <p class="skill-tag">SKILL 2</p>
            <h2>VIDEOGRAPHY</h2>
            <p style="color: var(--accent-red); font-family: 'Script', cursive; font-size: 1.5rem; transform: rotate(-5deg); margin-top: -15px;">Premiere Pro | After Effects</p>
        </div>
    </div>

    <section class="section-videography">
        <div class="container layout-wrapper">
            <div class="side-info">
                <div class="large-number">02</div>
                <p style="color: #555; font-size: 1rem; font-weight: 500;">
                    Elevating visual narratives through dynamic motion graphics, precise 3D compositing, and cinematic color grading.
                </p>
            </div>
            
            <div class="scroll-wrapper">
                <p class="scroll-hint">&larr; Scroll to view projects &rarr;</p>
                <div class="scroll-container">
                    <div class="editorial-matte-card">
                        <img src="images/blender-work.jpg" alt="Technical Workflow 3D">
                        <h3>3D MOTION &amp; COMPOSITING</h3>
                        <p>Advanced technical workflows utilizing Houdini &amp; Blender 3D to craft stunning visual effects and immersive motion graphics.</p>
                    </div>
                    <div class="editorial-matte-card">
                        <img src="images/premiere-work.jpg" alt="Cinematic Editing">
                        <h3>CINEMATIC POST-PRODUCTION</h3>
                        <p>High-end video editing and meticulous cinematic color grading driven by Adobe Premiere Pro and After Effects.</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section class="section-resume">
        <div class="container">
            <h2 style="margin-bottom: 40px; font-size: 3rem; text-align: center;">EXPERIENCE &amp; CV</h2>
            
            <div class="cv-grid">
                <div class="cv-sidebar">
                    <h3>SOFTWARE STACK</h3>
                    <ul>
                        <li>Adobe Premiere Pro &amp; After Effects</li>
                        <li>Photoshop &amp; Lightroom</li>
                        <li>Blender 3D &amp; Houdini</li>
                        <li>Unreal Engine (Training)</li>
                        <li>Canva</li>
                    </ul>

                    <h3>CERTIFICATIONS</h3>
                    <ul>
                        <li><strong>Google Data Analytics</strong></li>
                        <li><strong>Meta Social Media Marketing</strong></li>
                    </ul>

                    <h3>CORE SKILLS</h3>
                    <ul>
                        <li>Commercial Photography</li>
                        <li>Cinematic Videography</li>
                        <li>High-End Retouching</li>
                        <li>3D Compositing</li>
                        <li>Brand Identity Design</li>
                    </ul>

                    <h3>TECHNICAL PROFICIENCY</h3>
                    <ul>
                        <li><strong>Computer Skills:</strong> Proficient / Expert</li>
                        <li>Data Research &amp; Analytics</li>
                        <li>Information Technology Workflows</li>
                    </ul>

                    <h3>EDUCATION</h3>
                    <p><strong>Technical University of Kenya</strong><br>Electrical Engineering (09/2019)</p>
                    <p><strong>Kiranga Boys High School</strong><br>High School Diploma (11/2013)</p>
                </div>

                <div class="cv-main">
                    <div class="job-entry">
                        <h4>Photographer &amp; Videographer</h4>
                        <p class="company">Luxury Studio - Joska, Ruai</p>
                        <p class="date">2025 – Present</p>
                        <ul style="color: #ccc; padding-left: 20px;">
                            <li>Directed and executed premium commercial photography and videography, ensuring a clean, modern, and visually striking editorial aesthetic.</li>
                            <li>Managed comprehensive studio setups, utilizing advanced camera accessories, continuous lighting, and strobe configurations.</li>
                            <li>Handled end-to-end post-production workflows, including video editing, cinematic color grading, and high-end digital retouching.</li>
                        </ul>
                    </div>

                    <div class="job-entry">
                        <h4>Freelance Visual Creator &amp; Designer</h4>
                        <p class="company">Nairobi</p>
                        <p class="date">2022 – Present</p>
                        <ul style="color: #ccc; padding-left: 20px;">
                            <li>Develop complete brand identities and visual assets, including executing retro script logo designs.</li>
                            <li>Engineer comprehensive multi-scene visual narrative scripts, applying cinematic art direction to complex storytelling projects.</li>
                            <li>Integrate advanced digital imaging tools and 3D software (Blender, Houdini) to enhance visual narratives.</li>
                        </ul>
                    </div>

                    <div class="job-entry">
                        <h4>Associate</h4>
                        <p class="company">Sama Inc - Nairobi</p>
                        <p class="date">03/2021 - 09/2024</p>
                        <ul style="color: #ccc; padding-left: 20px;">
                            <li>Leveraged technical proficiency to research, collect, and organize complex datasets from a variety of sources.</li>
                            <li>Created detailed reports and presentations summarizing analytical findings to guide project insights.</li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <footer>
        <div class="container">
            <div class="footer-photo">
                <img src="images/IMG_0957.png" alt="Antony Ngugi Profile">
            </div>
            <h2 style="font-size: 4rem; line-height: 1; margin-bottom: 20px;">LET'S WORK<br>TOGETHER!</h2>
            <p style="font-size: 1.2rem; letter-spacing: 2px; color: #ccc; font-style: italic;">
                kushngugi01@gmail.com <span style="color: var(--accent-red); font-style: normal;">|</span> 0716448892
            </p>
        </div>
    </footer>

    <script>
        // Translates vertical mouse wheel scrolling to horizontal scrolling for the galleries
        document.querySelectorAll('.scroll-container').forEach(container => {
            container.addEventListener('wheel', (e) => {
                // Prevent default vertical scroll ONLY if the user is explicitly trying to scroll the container
                // e.deltaY checks the vertical scroll amount of the mouse wheel
                if (e.deltaY !== 0) {
                    e.preventDefault();
                    container.scrollLeft += e.deltaY;
                }
            });
        });
    </script>
</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pratyush Sharma - Founder & Developer</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;600;700&family=Space+Mono:wght@400;700&family=Syne:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #0a0e27;
            color: #e0e0e0;
            font-family: 'JetBrains Mono', monospace;
            line-height: 1.6;
            overflow-x: hidden;
        }

        @keyframes scanlines {
            0% { transform: translateY(0); }
            100% { transform: translateY(10px); }
        }

        .scanline {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 2px;
            background: rgba(255, 255, 255, 0.03);
            animation: scanlines 8s linear infinite;
            z-index: 1;
            pointer-events: none;
        }

        .container {
            display: grid;
            grid-template-columns: 300px 1fr;
            min-height: 100vh;
            gap: 50px;
            padding: 50px;
            max-width: 1500px;
            margin: 0 auto;
        }

        /* Left Sidebar */
        .sidebar {
            display: flex;
            flex-direction: column;
            gap: 50px;
            position: sticky;
            top: 50px;
            height: fit-content;
        }

        .profile-card {
            text-align: center;
            animation: slideInLeft 0.8s ease-out;
        }

        @keyframes slideInLeft {
            from {
                opacity: 0;
                transform: translateX(-40px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        .avatar-wrapper {
            position: relative;
            width: 200px;
            height: 200px;
            margin: 0 auto 25px;
            border-radius: 16px;
            overflow: hidden;
            border: 2px solid #4a90e2;
            box-shadow: 0 0 30px rgba(74, 144, 226, 0.3);
            animation: glow 3s ease-in-out infinite;
        }

        @keyframes glow {
            0%, 100% { box-shadow: 0 0 20px rgba(74, 144, 226, 0.3), inset 0 0 20px rgba(74, 144, 226, 0.1); }
            50% { box-shadow: 0 0 40px rgba(74, 144, 226, 0.5), inset 0 0 30px rgba(74, 144, 226, 0.2); }
        }

        .avatar {
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, #1a2744, #0f1b2e);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 100px;
            position: relative;
        }

        .avatar::before {
            content: '';
            position: absolute;
            inset: 0;
            background: radial-gradient(circle at 30% 30%, rgba(255,255,255,0.1), transparent);
        }

        .founder-badge {
            position: absolute;
            top: -10px;
            right: -10px;
            background: linear-gradient(135deg, #4a90e2, #ff6b6b);
            color: white;
            padding: 8px 12px;
            border-radius: 20px;
            font-size: 0.7rem;
            font-weight: 700;
            letter-spacing: 1px;
            box-shadow: 0 4px 15px rgba(255, 107, 107, 0.4);
        }

        .profile-name {
            font-size: 2rem;
            font-weight: 700;
            margin-bottom: 8px;
            color: #ffffff;
            letter-spacing: 1px;
            font-family: 'Syne', sans-serif;
        }

        .profile-title {
            color: #4a90e2;
            font-size: 0.95rem;
            margin-bottom: 8px;
            font-weight: 600;
            letter-spacing: 0.5px;
        }

        .profile-handle {
            color: #7a8ba8;
            font-size: 0.9rem;
            margin-bottom: 20px;
        }

        .profile-bio {
            color: #a8b8d8;
            font-size: 0.9rem;
            line-height: 1.6;
            margin-bottom: 25px;
            padding: 20px;
            border-left: 3px solid #4a90e2;
            background: rgba(74, 144, 226, 0.08);
            border-radius: 4px;
        }

        .founder-stats {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            padding: 20px 0;
            border-top: 1px solid #1f2d42;
            border-bottom: 1px solid #1f2d42;
            margin: 25px 0;
        }

        .stat {
            text-align: center;
        }

        .stat-value {
            font-size: 1.8rem;
            font-weight: 700;
            color: #4a90e2;
            display: block;
        }

        .stat-label {
            font-size: 0.75rem;
            color: #7a8ba8;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            margin-top: 5px;
        }

        .sidebar-section {
            padding-top: 20px;
            border-top: 1px solid #1f2d42;
        }

        .sidebar-label {
            font-size: 0.75rem;
            color: #7a8ba8;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            margin-bottom: 12px;
            display: flex;
            align-items: center;
            gap: 6px;
            font-weight: 600;
        }

        .sidebar-content {
            color: #a8b8d8;
            font-size: 0.9rem;
            line-height: 1.7;
        }

        .sidebar-content a {
            color: #4a90e2;
            text-decoration: none;
            transition: color 0.3s ease;
            font-weight: 500;
        }

        .sidebar-content a:hover {
            color: #6fa3ff;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 20px;
            flex-wrap: wrap;
        }

        .social-icon {
            width: 45px;
            height: 45px;
            border-radius: 8px;
            border: 1.5px solid #2a3f5f;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.3s ease;
            background: rgba(74, 144, 226, 0.08);
        }

        .social-icon:hover {
            border-color: #4a90e2;
            background: rgba(74, 144, 226, 0.2);
            box-shadow: 0 0 20px rgba(74, 144, 226, 0.4);
            transform: translateY(-4px);
        }

        .social-icon img {
            width: 22px;
            height: 22px;
            filter: brightness(0.95);
        }

        /* Main Content */
        .main {
            animation: slideInRight 0.8s ease-out;
        }

        @keyframes slideInRight {
            from {
                opacity: 0;
                transform: translateX(40px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        .section {
            margin-bottom: 70px;
            opacity: 0;
            animation: fadeInUp 0.6s ease-out forwards;
        }

        .section:nth-child(1) { animation-delay: 0.2s; }
        .section:nth-child(2) { animation-delay: 0.3s; }
        .section:nth-child(3) { animation-delay: 0.4s; }
        .section:nth-child(4) { animation-delay: 0.5s; }
        .section:nth-child(5) { animation-delay: 0.6s; }
        .section:nth-child(6) { animation-delay: 0.7s; }
        .section:nth-child(7) { animation-delay: 0.8s; }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Featured Product */
        .featured-product {
            padding: 40px;
            background: linear-gradient(135deg, rgba(74, 144, 226, 0.15), rgba(20, 40, 80, 0.25));
            border: 2px solid #4a90e2;
            border-radius: 12px;
            overflow: hidden;
            position: relative;
            margin-bottom: 60px;
        }

        .featured-product::before {
            content: 'FEATURED';
            position: absolute;
            top: 15px;
            right: 20px;
            background: linear-gradient(135deg, #4a90e2, #ff6b6b);
            color: white;
            padding: 6px 12px;
            border-radius: 4px;
            font-size: 0.65rem;
            font-weight: 700;
            letter-spacing: 1px;
        }

        .featured-title {
            font-size: 1.8rem;
            font-weight: 700;
            color: #4a90e2;
            margin-bottom: 12px;
            font-family: 'Syne', sans-serif;
        }

        .featured-subtitle {
            color: #a8b8d8;
            font-size: 0.95rem;
            margin-bottom: 20px;
            line-height: 1.7;
        }

        .featured-stats {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 15px;
            margin-top: 25px;
            padding-top: 25px;
            border-top: 1px solid rgba(74, 144, 226, 0.3);
        }

        .feat-stat {
            text-align: center;
        }

        .feat-stat-value {
            font-size: 1.5rem;
            font-weight: 700;
            color: #4a90e2;
        }

        .feat-stat-label {
            font-size: 0.75rem;
            color: #7a8ba8;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            margin-top: 5px;
        }

        .section-title {
            display: flex;
            align-items: center;
            gap: 12px;
            font-size: 1.4rem;
            font-weight: 700;
            margin-bottom: 30px;
            color: #ffffff;
            padding-bottom: 15px;
            border-bottom: 2px solid #2a3f5f;
            letter-spacing: 1px;
            font-family: 'Syne', sans-serif;
        }

        .section-title::before {
            content: '◆';
            color: #4a90e2;
            font-size: 1.2rem;
        }

        /* Tech Grid */
        .tech-section {
            margin-bottom: 40px;
        }

        .tech-section-title {
            font-size: 1.1rem;
            font-weight: 600;
            color: #4a90e2;
            margin-bottom: 18px;
            text-transform: uppercase;
            letter-spacing: 1px;
            padding-left: 10px;
            border-left: 3px solid #4a90e2;
        }

        .tech-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(130px, 1fr));
            gap: 12px;
        }

        .tech-item {
            padding: 12px;
            background: rgba(74, 144, 226, 0.1);
            border: 1px solid #2a3f5f;
            border-radius: 6px;
            text-align: center;
            transition: all 0.3s ease;
            cursor: pointer;
            font-size: 0.9rem;
            color: #a8b8d8;
            font-weight: 500;
        }

        .tech-item:hover {
            border-color: #4a90e2;
            background: rgba(74, 144, 226, 0.2);
            box-shadow: 0 0 20px rgba(74, 144, 226, 0.25);
            transform: translateY(-5px);
            color: #ffffff;
        }

        /* Contribution & Impact */
        .impact-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 20px;
        }

        .impact-card {
            padding: 25px;
            background: rgba(74, 144, 226, 0.08);
            border: 1px solid #2a3f5f;
            border-radius: 8px;
            transition: all 0.3s ease;
        }

        .impact-card:hover {
            border-color: #4a90e2;
            background: rgba(74, 144, 226, 0.15);
            box-shadow: 0 0 20px rgba(74, 144, 226, 0.2);
            transform: translateY(-5px);
        }

        .impact-icon {
            font-size: 2rem;
            margin-bottom: 12px;
        }

        .impact-title {
            font-size: 1rem;
            font-weight: 600;
            color: #ffffff;
            margin-bottom: 8px;
        }

        .impact-desc {
            color: #7a8ba8;
            font-size: 0.9rem;
            line-height: 1.5;
        }

        /* Links Grid */
        .links-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
        }

        .link-card {
            padding: 18px;
            background: rgba(74, 144, 226, 0.08);
            border: 1px solid #2a3f5f;
            border-radius: 6px;
            transition: all 0.3s ease;
        }

        .link-card:hover {
            border-color: #4a90e2;
            background: rgba(74, 144, 226, 0.15);
            box-shadow: 0 0 15px rgba(74, 144, 226, 0.25);
            transform: translateY(-4px);
        }

        .link-card a {
            color: #4a90e2;
            text-decoration: none;
            font-size: 0.95rem;
            display: flex;
            align-items: center;
            gap: 10px;
            font-weight: 600;
        }

        .link-card a:hover {
            color: #6fa3ff;
        }

        /* Footer */
        .footer {
            text-align: center;
            padding: 50px 0;
            border-top: 1px solid #1f2d42;
            margin-top: 80px;
            color: #7a8ba8;
        }

        .footer-text {
            margin-bottom: 15px;
            letter-spacing: 1px;
            font-size: 0.95rem;
        }

        /* Responsive */
        @media (max-width: 1024px) {
            .container {
                grid-template-columns: 1fr;
                gap: 40px;
                padding: 40px;
            }

            .sidebar {
                position: relative;
                top: 0;
            }

            .featured-stats {
                grid-template-columns: repeat(2, 1fr);
            }
        }

        @media (max-width: 768px) {
            .container {
                padding: 20px;
                gap: 30px;
            }

            .tech-grid {
                grid-template-columns: repeat(auto-fill, minmax(110px, 1fr));
            }

            .profile-name {
                font-size: 1.6rem;
            }

            .section-title {
                font-size: 1.2rem;
            }

            .featured-product {
                padding: 25px;
            }

            .featured-product::before {
                font-size: 0.6rem;
                padding: 5px 10px;
            }

            .featured-stats {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="scanline"></div>

    <div class="container">
        <!-- SIDEBAR -->
        <aside class="sidebar">
            <div class="profile-card">
                <div class="avatar-wrapper">
                    <div class="avatar">👨‍💻</div>
                    <div class="founder-badge">FOUNDER</div>
                </div>

                <div class="profile-name">Pratyush Sharma</div>
                <div class="profile-title">Founder & Full Stack Developer</div>
                <div class="profile-handle">@pratyushsharma27</div>
                
                <div class="profile-bio">
                    Building Tenimal - the future of creator-led education. Full stack web & mobile developer from Delhi.
                </div>

                <div class="founder-stats">
                    <div class="stat">
                        <span class="stat-value">1</span>
                        <span class="stat-label">Active Startup</span>
                    </div>
                    <div class="stat">
                        <span class="stat-value">18</span>
                        <span class="stat-label">Public Repos</span>
                    </div>
                    <div class="stat">
                        <span class="stat-value">1.2K+</span>
                        <span class="stat-label">Commits</span>
                    </div>
                    <div class="stat">
                        <span class="stat-value">47</span>
                        <span class="stat-label">Day Streak</span>
                    </div>
                </div>

                <div class="sidebar-section">
                    <div class="sidebar-label">📍 Based In</div>
                    <div class="sidebar-content">Delhi, India</div>
                </div>

                <div class="sidebar-section">
                    <div class="sidebar-label">🚀 Current Focus</div>
                    <div class="sidebar-content">Tenimal - EdTech Platform</div>
                </div>

                <div class="sidebar-section">
                    <div class="sidebar-label">🌐 Links</div>
                    <div class="sidebar-content">
                        <a href="https://tenimal.com" target="_blank">tenimal.com</a><br>
                        <a href="https://codepen.io/pratyush-sharma-2710" target="_blank">CodePen</a><br>
                        <a href="https://instagram.com/sharma.pratyush2710" target="_blank">Instagram</a>
                    </div>
                </div>

                <div class="sidebar-section">
                    <div class="sidebar-label">🔗 Connect</div>
                    <div class="social-links">
                        <a href="https://github.com/pratyushsharma27" target="_blank" class="social-icon" title="GitHub">
                            <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                                <path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"/>
                            </svg>
                        </a>
                        <a href="https://instagram.com/sharma.pratyush2710" target="_blank" class="social-icon" title="Instagram">
                            <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                                <rect x="2" y="2" width="20" height="20" rx="5" ry="5"/><path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37"/><circle cx="17.5" cy="6.5" r="1.5"/>
                            </svg>
                        </a>
                        <a href="https://twitter.com" target="_blank" class="social-icon" title="Twitter">
                            <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                                <path d="M23 3a10.9 10.9 0 0 1-3.14 1.53 4.48 4.48 0 0 0-7.86 3v1A10.66 10.66 0 0 1 3 4s-4 9 5 13a11.64 11.64 0 0 1-7 2s9 5 20 5a9.5 9.5 0 0 0-9-5.5c4.75 2.25 7-7 7-11.5a4.5 4.5 0 0 0-.08-.83A7.72 7.72 0 0 0 23 3"/>
                            </svg>
                        </a>
                        <a href="https://linkedin.com" target="_blank" class="social-icon" title="LinkedIn">
                            <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                                <path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2"/>
                            </svg>
                        </a>
                    </div>
                </div>
            </div>
        </aside>

        <!-- MAIN CONTENT -->
        <main class="main">
            <!-- Featured Product -->
            <section class="featured-product">
                <div class="featured-title">Tenimal</div>
                <div class="featured-subtitle">
                    The future of creator-led education. Combining short-form video (Blips) with a full Learning Management System. Empowering independent educators to own their platform and lead their people.
                </div>
                <div class="featured-stats">
                    <div class="feat-stat">
                        <div class="feat-stat-value">26+</div>
                        <div class="feat-stat-label">Screens Designed</div>
                    </div>
                    <div class="feat-stat">
                        <div class="feat-stat-value">30+</div>
                        <div class="feat-stat-label">DB Tables</div>
                    </div>
                    <div class="feat-stat">
                        <div class="feat-stat-value">Jan 2027</div>
                        <div class="feat-stat-label">Public Launch</div>
                    </div>
                </div>
            </section>

            <!-- About Section -->
            <section class="section">
                <div class="section-title">About</div>
                <div class="impact-grid">
                    <div class="impact-card">
                        <div class="impact-icon">🎯</div>
                        <div class="impact-title">Building Products</div>
                        <div class="impact-desc">Founder of Tenimal, an EdTech platform solving the creator economy. Focus on product-market fit and sustainable growth.</div>
                    </div>
                    <div class="impact-card">
                        <div class="impact-icon">💻</div>
                        <div class="impact-title">Full Stack Developer</div>
                        <div class="impact-desc">Expert in React, Flutter, Node.js, and modern web/mobile architectures. Building scalable systems from day one.</div>
                    </div>
                    <div class="impact-card">
                        <div class="impact-icon">📚</div>
                        <div class="impact-title">Content Creator</div>
                        <div class="impact-desc">Running "Code with Pratyush" YouTube channel and posting daily technical content. Teaching 1000+ aspiring developers.</div>
                    </div>
                    <div class="impact-card">
                        <div class="impact-icon">🚀</div>
                        <div class="impact-title">Serial Learner</div>
                        <div class="impact-desc">Constantly learning AI, System Design, and advanced backend patterns. Exploring adjacent SaaS opportunities.</div>
                    </div>
                </div>
            </section>

            <!-- Languages -->
            <section class="section">
                <div class="tech-section">
                    <div class="tech-section-title">Languages</div>
                    <div class="tech-grid">
                        <div class="tech-item">JavaScript</div>
                        <div class="tech-item">TypeScript</div>
                        <div class="tech-item">Python</div>
                        <div class="tech-item">Dart</div>
                        <div class="tech-item">Java</div>
                        <div class="tech-item">C++</div>
                        <div class="tech-item">Go</div>
                        <div class="tech-item">PHP</div>
                        <div class="tech-item">Swift</div>
                        <div class="tech-item">Kotlin</div>
                        <div class="tech-item">SQL</div>
                        <div class="tech-item">C</div>
                    </div>
                </div>
            </section>

            <!-- Frontend & Mobile -->
            <section class="section">
                <div class="tech-section">
                    <div class="tech-section-title">Frontend Frameworks</div>
                    <div class="tech-grid">
                        <div class="tech-item">React</div>
                        <div class="tech-item">Next.js</div>
                        <div class="tech-item">React Native</div>
                        <div class="tech-item">Vue.js</div>
                        <div class="tech-item">Angular</div>
                        <div class="tech-item">Svelte</div>
                        <div class="tech-item">Remix</div>
                        <div class="tech-item">HTML5</div>
                        <div class="tech-item">CSS3</div>
                        <div class="tech-item">SASS/SCSS</div>
                    </div>
                </div>

                <div class="tech-section">
                    <div class="tech-section-title">Mobile Development</div>
                    <div class="tech-grid">
                        <div class="tech-item">Flutter</div>
                        <div class="tech-item">React Native</div>
                        <div class="tech-item">Swift</div>
                        <div class="tech-item">Kotlin</div>
                        <div class="tech-item">iOS Dev</div>
                        <div class="tech-item">Android Dev</div>
                        <div class="tech-item">Expo</div>
                        <div class="tech-item">Firebase</div>
                    </div>
                </div>
            </section>

            <!-- Backend & Databases -->
            <section class="section">
                <div class="tech-section">
                    <div class="tech-section-title">Backend & Servers</div>
                    <div class="tech-grid">
                        <div class="tech-item">Node.js</div>
                        <div class="tech-item">Express.js</div>
                        <div class="tech-item">NestJS</div>
                        <div class="tech-item">Django</div>
                        <div class="tech-item">Flask</div>
                        <div class="tech-item">FastAPI</div>
                        <div class="tech-item">Spring Boot</div>
                        <div class="tech-item">Laravel</div>
                        <div class="tech-item">Ruby on Rails</div>
                        <div class="tech-item">Gin</div>
                    </div>
                </div>

                <div class="tech-section">
                    <div class="tech-section-title">Databases & Data</div>
                    <div class="tech-grid">
                        <div class="tech-item">PostgreSQL</div>
                        <div class="tech-item">MongoDB</div>
                        <div class="tech-item">MySQL</div>
                        <div class="tech-item">Redis</div>
                        <div class="tech-item">Supabase</div>
                        <div class="tech-item">Firebase</div>
                        <div class="tech-item">Prisma ORM</div>
                        <div class="tech-item">Sequelize</div>
                        <div class="tech-item">SQLAlchemy</div>
                        <div class="tech-item">DynamoDB</div>
                    </div>
                </div>
            </section>

            <!-- APIs & Tools -->
            <section class="section">
                <div class="tech-section">
                    <div class="tech-section-title">APIs & Real-time</div>
                    <div class="tech-grid">
                        <div class="tech-item">REST APIs</div>
                        <div class="tech-item">GraphQL</div>
                        <div class="tech-item">Socket.io</div>
                        <div class="tech-item">WebSockets</div>
                        <div class="tech-item">Stripe API</div>
                        <div class="tech-item">Agora SDK</div>
                        <div class="tech-item">Twilio</div>
                        <div class="tech-item">SendGrid</div>
                    </div>
                </div>

                <div class="tech-section">
                    <div class="tech-section-title">Cloud & DevOps</div>
                    <div class="tech-grid">
                        <div class="tech-item">AWS</div>
                        <div class="tech-item">GCP</div>
                        <div class="tech-item">Azure</div>
                        <div class="tech-item">Vercel</div>
                        <div class="tech-item">Netlify</div>
                        <div class="tech-item">Heroku</div>
                        <div class="tech-item">Docker</div>
                        <div class="tech-item">Kubernetes</div>
                        <div class="tech-item">CI/CD</div>
                        <div class="tech-item">GitHub Actions</div>
                    </div>
                </div>
            </section>

            <!-- Tools & Specialties -->
            <section class="section">
                <div class="tech-section">
                    <div class="tech-section-title">Tools & Utilities</div>
                    <div class="tech-grid">
                        <div class="tech-item">Git</div>
                        <div class="tech-item">GitHub</div>
                        <div class="tech-item">Tailwind CSS</div>
                        <div class="tech-item">Styled Comp.</div>
                        <div class="tech-item">npm/yarn</div>
                        <div class="tech-item">Webpack</div>
                        <div class="tech-item">Vite</div>
                        <div class="tech-item">Jest</div>
                        <div class="tech-item">Vitest</div>
                        <div class="tech-item">Postman</div>
                        <div class="tech-item">VS Code</div>
                        <div class="tech-item">Figma</div>
                    </div>
                </div>

                <div class="tech-section">
                    <div class="tech-section-title">AI & Advanced</div>
                    <div class="tech-grid">
                        <div class="tech-item">Machine Learning</div>
                        <div class="tech-item">TensorFlow</div>
                        <div class="tech-item">PyTorch</div>
                        <div class="tech-item">OpenAI API</div>
                        <div class="tech-item">LLMs</div>
                        <div class="tech-item">MediaPipe</div>
                        <div class="tech-item">CV</div>
                        <div class="tech-item">NLP</div>
                    </div>
                </div>
            </section>

            <!-- Featured Links -->
            <section class="section">
                <div class="section-title">Featured Projects & Links</div>
                <div class="links-grid">
                    <div class="link-card">
                        <a href="https://tenimal.com" target="_blank">
                            🚀 Tenimal
                        </a>
                    </div>
                    <div class="link-card">
                        <a href="https://github.com/pratyushsharma27" target="_blank">
                            🐙 GitHub Profile
                        </a>
                    </div>
                    <div class="link-card">
                        <a href="https://instagram.com/sharma.pratyush2710" target="_blank">
                            📸 Instagram
                        </a>
                    </div>
                    <div class="link-card">
                        <a href="https://codepen.io/pratyush-sharma-2710" target="_blank">
                            ✏️ CodePen
                        </a>
                    </div>
                </div>
            </section>

            <!-- Footer -->
            <footer class="footer">
                <div class="footer-text">🔥 Building • Learning • Scaling • Repeating</div>
                <div class="footer-text">Currently: Working on Tenimal | Learning: AI & System Design</div>
                <div class="footer-text" style="margin-top: 25px; font-size: 0.85rem;">Made with ❤️ by Pratyush Sharma © 2024</div>
            </footer>
        </main>
    </div>
</body>
</html>

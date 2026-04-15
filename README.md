# 2026Kova
Esports, Gaming , Entertainment • #FearKVR
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="KOVA REALITY - Competitive Gaming Organization">
    <title>KOVA REALITY</title>
    
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;700;900&amp;family=Press+Start+2P&amp;family=VT323&amp;family=Rajdhani:wght@300;400;500;600&amp;display=swap" rel="stylesheet">
    
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;700;900&amp;family=Press+Start+2P&amp;family=VT323&amp;family=Rajdhani:wght@300;400;500;600&amp;display=swap');
        
        :root {
            --neon-cyan: #00f0ff;
            --neon-magenta: #ff00aa;
        }
        
        body { font-family: 'Rajdhani', system-ui, sans-serif; }
        .font-orbitron { font-family: 'Orbitron', sans-serif; }
        .font-press { font-family: 'Press Start 2P', system-ui, sans-serif; }
        .font-vt { font-family: 'VT323', monospace; }
        
        .neon-cyan { text-shadow: 0 0 10px var(--neon-cyan), 0 0 20px var(--neon-cyan), 0 0 40px var(--neon-cyan); }
        .neon-magenta { text-shadow: 0 0 10px var(--neon-magenta), 0 0 20px var(--neon-magenta), 0 0 40px var(--neon-magenta); }
        
        .hero-banner {
            background-image: url('https://i.imgur.com/QyJDNsR.png'); /* ← Your Banner */
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
            height: 420px;
            position: relative;
        }
        
        .hero-banner::before {
            content: '';
            position: absolute;
            inset: 0;
            background: linear-gradient(to bottom, rgba(5,5,15,0.4), rgba(5,5,15,0.85));
            z-index: 1;
        }
        
        .glitch { animation: glitch 1s linear infinite alternate; }
        @keyframes glitch {
            0% { transform: translate(0); }
            20% { transform: translate(-3px, 3px); }
            40% { transform: translate(3px, -3px); }
            60% { transform: translate(-3px, 3px); }
            80% { transform: translate(3px, -3px); }
            100% { transform: translate(0); }
        }
        
        .nav-link { position: relative; }
        .nav-link:after {
            content: '';
            position: absolute;
            width: 0;
            height: 3px;
            bottom: -2px;
            left: 0;
            background: linear-gradient(to right, #00f0ff, #ff00aa);
        }
        .nav-link:hover:after { width: 100%; }
        
        .section-header:after {
            content: '';
            position: absolute;
            width: 80px;
            height: 4px;
            background: linear-gradient(to right, var(--neon-cyan), var(--neon-magenta));
            bottom: -8px;
            left: 50%;
            transform: translateX(-50%);
        }
        
        .card-hover:hover {
            transform: translateY(-12px) scale(1.05);
            box-shadow: 0 0 40px 15px rgba(0, 240, 255, 0.4);
        }
        
        .social-icon:hover {
            transform: scale(1.3) rotate(12deg);
            filter: brightness(1.5) drop-shadow(0 0 20px currentColor);
        }
        
        #particle-canvas {
            position: absolute; top: 0; left: 0;
            width: 100%; height: 100%;
            z-index: 1; pointer-events: none; opacity: 0.25;
        }
        
        .scanlines::after {
            content: '';
            position: absolute; top: 0; left: 0;
            width: 100%; height: 100%;
            background: linear-gradient(to bottom, transparent 50%, rgba(0, 240, 255, 0.08) 50%);
            background-size: 100% 6px;
            animation: scan 4s linear infinite;
            pointer-events: none; z-index: 10;
        }
        @keyframes scan { 0% { background-position: 0 0; } 100% { background-position: 0 100%; } }
        
        .kova-logo {
            width: 68px; height: 68px;
            filter: drop-shadow(0 0 15px #00f0ff);
        }
    </style>
</head>
<body class="bg-[#05050f] text-white overflow-x-hidden">

    <!-- NAVBAR -->
    <nav class="bg-black/80 backdrop-blur-lg border-b border-[#00f0ff]/30 fixed w-full z-50">
        <div class="max-w-screen-2xl mx-auto px-8 py-5 flex items-center justify-between">
            <div class="flex items-center gap-4">
                <img src="https://i.imgur.com/HPdPah.png" alt="KOVA REALITY Logo" class="kova-logo"> <!-- ← Your Logo -->
                <div class="hidden sm:block">
                    <h1 class="text-4xl font-orbitron tracking-[4px] neon-cyan">KOVA</h1>
                    <h1 class="text-4xl font-orbitron tracking-[4px] -mt-3 neon-magenta">REALITY</h1>
                </div>
            </div>
            
            <div class="hidden md:flex items-center gap-10 text-lg font-medium">
                <a onclick="navigateTo('home')" class="nav-link cursor-pointer uppercase tracking-widest hover:text-[#00f0ff]">HOME</a>
                <a onclick="navigateTo('about')" class="nav-link cursor-pointer uppercase tracking-widest hover:text-[#ff00aa]">ABOUT</a>
                <a onclick="navigateTo('socials')" class="nav-link cursor-pointer uppercase tracking-widest hover:text-[#9d00ff]">SOCIALS</a>
            </div>
            
            <div class="flex items-center gap-6">
                <button onclick="joinDiscord()" 
                        class="px-8 py-3 bg-gradient-to-r from-[#00f0ff] to-[#ff00aa] text-black font-bold uppercase tracking-widest rounded-2xl hover:scale-110 flex items-center gap-2">
                    <i class="fa-brands fa-discord"></i>
                    JOIN DISCORD
                </button>
                <button onclick="toggleMobileMenu()" class="md:hidden text-3xl">
                    <i class="fa-solid fa-bars"></i>
                </button>
            </div>
        </div>
        
        <div id="mobileMenu" class="hidden md:hidden bg-black/95 backdrop-blur-xl border-t border-[#00f0ff]/30 px-8 py-6">
            <div class="flex flex-col gap-6 text-xl text-center">
                <a onclick="navigateTo('home');toggleMobileMenu()" class="py-2">HOME</a>
                <a onclick="navigateTo('about');toggleMobileMenu()" class="py-2">ABOUT THE TEAM</a>
                <a onclick="navigateTo('socials');toggleMobileMenu()" class="py-2">SOCIALS</a>
            </div>
        </div>
    </nav>

    <!-- HERO BANNER (your new banner) -->
    <section id="home" class="hero-banner flex items-center relative scanlines">
        <canvas id="particle-canvas"></canvas>
        
        <div class="max-w-screen-2xl mx-auto px-8 relative z-20">
            <div class="flex flex-col md:flex-row items-center justify-between gap-12 pt-28">
                <div class="space-y-6 max-w-xl">
                    <div class="flex items-center gap-6">
                        <img src="https://i.imgur.com/HPdPah.png" alt="KOVA REALITY Logo" class="w-20 h-20"> <!-- ← Your Logo -->
                        <div>
                            <h1 class="text-7xl md:text-8xl font-orbitron font-black glitch neon-cyan tracking-[-4px]">KOVA</h1>
                            <h1 class="text-7xl md:text-8xl font-orbitron font-black glitch neon-magenta -mt-4">REALITY</h1>
                        </div>
                    </div>
                    
                    <p class="text-3xl font-light text-gray-200">
                        Competitive gaming organization.<br>
                        <span class="text-[#ff00aa]">Forged in competition. Built for victory.</span>
                    </p>
                    
                    <div class="flex flex-wrap gap-6">
                        <button onclick="navigateTo('about')" 
                                class="px-10 py-5 border-2 border-[#00f0ff] text-[#00f0ff] text-xl font-bold uppercase rounded-3xl hover:bg-[#00f0ff] hover:text-black">
                            MEET THE TEAM
                        </button>
                        <button onclick="navigateTo('socials')" 
                                class="px-10 py-5 bg-[#ff00aa] text-white text-xl font-bold uppercase rounded-3xl hover:scale-110">
                            CONNECT NOW
                        </button>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="absolute bottom-10 left-1/2 text-[#00f0ff] flex flex-col items-center z-20">
            <div class="text-xs font-vt tracking-widest">SCROLL TO ENTER THE REALITY</div>
            <i class="fa-solid fa-chevron-down text-4xl animate-bounce mt-2"></i>
        </div>
    </section>

    <!-- ABOUT THE TEAM (your team photo) -->
    <section id="about" class="py-24 bg-[#0a0a1f]">
        <div class="max-w-screen-2xl mx-auto px-8">
            <div class="text-center mb-16">
                <h2 class="section-header text-6xl font-orbitron">ABOUT KOVA REALITY</h2>
            </div>
            
            <div class="grid md:grid-cols-12 gap-12 items-center">
                <div class="md:col-span-7 space-y-8 text-xl leading-relaxed">
                    <p>KOVA REALITY is a competitive gaming organization built for dominance across multiple titles.</p>
                    <p>From intense battles to strategic gameplay, our players are elite competitors who live and breathe the game.</p>
                    <p class="text-sm font-mono text-[#00f0ff]/70">✦ Edit this text freely — your team story goes here</p>
                </div>
                <div class="md:col-span-5">
                    <div class="rounded-3xl overflow-hidden border border-[#00f0ff]/30">
                        <img src="https://i.imgur.com/n0haqEk.png" alt="KOVA REALITY Team" class="w-full"> <!-- ← Your Team Photo -->
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- SOCIALS -->
    <section id="socials" class="py-24 bg-[#0f0a1f]">
        <div class="max-w-screen-2xl mx-auto px-8">
            <h2 class="section-header text-6xl font-orbitron text-center mb-16">CONNECT WITH US</h2>
            
            <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
                <div class="card-hover bg-black border border-[#5865F2]/30 rounded-3xl p-8 text-center">
                    <i class="fa-brands fa-discord text-7xl text-[#5865F2] mb-6 social-icon"></i>
                    <h3 class="text-3xl font-orbitron">DISCORD</h3>
                    <a href="https://discord.gg/VPZ6QRRR5H" target="_blank" class="mt-8 block w-full py-4 bg-[#5865F2] rounded-2xl font-bold">JOIN SERVER</a>
                </div>
                
                <div class="card-hover bg-black border border-[#FF0000]/30 rounded-3xl p-8 text-center">
                    <i class="fa-brands fa-youtube text-7xl text-[#FF0000] mb-6 social-icon"></i>
                    <h3 class="text-3xl font-orbitron">YOUTUBE</h3>
                    <a href="https://youtube.com/@2026kova" target="_blank" class="mt-8 block w-full py-4 bg-[#FF0000] rounded-2xl font-bold">SUBSCRIBE</a>
                </div>
                
                <div class="card-hover bg-black border border-[#1DA1F2]/30 rounded-3xl p-8 text-center">
                    <i class="fa-brands fa-x-twitter text-7xl text-[#1DA1F2] mb-6 social-icon"></i>
                    <h3 class="text-3xl font-orbitron">X / TWITTER</h3>
                    <a href="https://x.com/kova2026" target="_blank" class="mt-8 block w-full py-4 bg-[#1DA1F2] rounded-2xl font-bold">FOLLOW</a>
                </div>
                
                <div class="card-hover bg-black border border-[#FF0050]/30 rounded-3xl p-8 text-center">
                    <i class="fa-brands fa-tiktok text-7xl text-[#FF0050] mb-6 social-icon"></i>
                    <h3 class="text-3xl font-orbitron">TIKTOK</h3>
                    <a href="https://www.tiktok.com/@2026kova" target="_blank" class="mt-8 block w-full py-4 bg-[#FF0050] rounded-2xl font-bold">FOLLOW</a>
                </div>
            </div>
        </div>
    </section>

    <script>
        // Particle background
        function createParticles() {
            const canvas = document.getElementById('particle-canvas');
            if (!canvas) return;
            const ctx = canvas.getContext('2d');
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            
            let particles = [];
            class Particle {
                constructor() {
                    this.x = Math.random() * canvas.width;
                    this.y = Math.random() * canvas.height;
                    this.size = Math.random() * 3 + 1;
                    this.speed = Math.random() * 0.6 + 0.3;
                }
                update() { this.y += this.speed; if (this.y > canvas.height) this.y = 0; }
                draw() {
                    ctx.fillStyle = '#00f0ff';
                    ctx.globalAlpha = 0.7;
                    ctx.beginPath();
                    ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                    ctx.fill();
                }
            }
            for (let i = 0; i < 90; i++) particles.push(new Particle());
            
            function animate() {
                ctx.clearRect(0, 0, canvas.width, canvas.height);
                particles.forEach(p => { p.update(); p.draw(); });
                requestAnimationFrame(animate);
            }
            animate();
        }
        
        window.onload = createParticles;
        
        function navigateTo(section) {
            document.getElementById(section).scrollIntoView({ behavior: 'smooth' });
        }
        
        function toggleMobileMenu() {
            document.getElementById('mobileMenu').classList.toggle('hidden');
        }
        
        function joinDiscord() {
            window.open('https://discord.gg/VPZ6QRRR5H', '_blank');
        }
    </script>
</body>
</html><img width="499" height="499" alt="1000003204-removebg-preview" src="https://github.com/user-attachments/assets/2f1adf26-2d30-4d50-9c3d-c3082d0c5e8a" />

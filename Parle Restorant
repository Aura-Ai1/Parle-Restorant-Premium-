<!doctype html>
<html lang="tr">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="theme-color" content="#030303">
<title>PARLE — Haute Gastronomie & Maison</title>

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;500;600;700&family=Plus+Jakarta+Sans:wght@200;300;400;500&display=swap" rel="stylesheet">

<style>
:root {
  --bg-dark: #030303;
  --bg-card: #090908;
  --gold-primary: #d4af37;
  --gold-light: #f3e5ab;
  --text-main: #f5f3ef;
  --text-muted: #8e8a82;
  --border-line: rgba(212, 175, 55, 0.18);
  --font-serif: 'Cinzel', serif;
  --font-sans: 'Plus Jakarta Sans', sans-serif;
  --ease: cubic-bezier(0.16, 1, 0.3, 1);
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; background: var(--bg-dark); }
body { width: 100%; height: 100%; color: var(--text-main); font-family: var(--font-sans); font-weight: 300; overflow-x: hidden; -webkit-font-smoothing: antialiased; }

/* Custom Cursor */
.cursor-dot, .cursor-ring { pointer-events: none; position: fixed; top: 0; left: 0; border-radius: 50%; z-index: 9999; transform: translate(-50%, -50%); }
.cursor-dot { width: 5px; height: 5px; background: var(--gold-primary); }
.cursor-ring { width: 36px; height: 36px; border: 1px solid rgba(212, 175, 55, 0.35); transition: width 0.3s var(--ease), height 0.3s var(--ease), border-color 0.3s; }
body:hover .cursor-ring.active { width: 70px; height: 70px; border-color: var(--gold-primary); background: rgba(212, 175, 55, 0.04); }

/* Noise Effect */
.noise-overlay { position: fixed; inset: 0; pointer-events: none; z-index: 900; opacity: 0.03; background: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.8' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E"); }

/* Preloader */
.preloader { position: fixed; inset: 0; z-index: 10000; background: #020202; display: flex; flex-direction: column; justify-content: center; align-items: center; transition: transform 1s var(--ease), opacity 0.8s ease; }
.preloader.completed { transform: translateY(-100%); opacity: 0; pointer-events: none; }
.preloader-title { font-family: var(--font-serif); font-size: clamp(36px, 8vw, 80px); letter-spacing: 0.35em; background: linear-gradient(135deg, #fff 0%, var(--gold-primary) 100%); -webkit-background-clip: text; -webkit-text-fill-color: transparent; }
.preloader-bar-wrap { width: 180px; height: 1px; background: rgba(255,255,255,0.08); margin-top: 40px; position: relative; overflow: hidden; }
.preloader-bar { position: absolute; left: 0; top: 0; height: 100%; width: 0%; background: var(--gold-primary); }

/* Header Navigation */
.header { position: fixed; top: 0; left: 0; width: 100%; z-index: 800; padding: 35px 6vw; display: flex; justify-content: space-between; align-items: center; transition: padding 0.5s var(--ease), background 0.5s; }
.header.scrolled { padding: 20px 6vw; background: rgba(3, 3, 3, 0.88); backdrop-filter: blur(20px); border-bottom: 1px solid var(--border-line); }
.brand-logo { font-family: var(--font-serif); font-size: 26px; font-weight: 600; letter-spacing: 0.25em; color: var(--text-main); text-decoration: none; }
.brand-logo span { color: var(--gold-primary); }
.nav-links { display: flex; gap: 40px; list-style: none; }
.nav-links a { font-size: 11px; letter-spacing: 0.25em; text-transform: uppercase; color: var(--text-muted); text-decoration: none; transition: color 0.3s; position: relative; }
.nav-links a:hover { color: var(--gold-primary); }

.btn-gold { border: 1px solid var(--gold-primary); padding: 14px 32px; font-size: 10px; letter-spacing: 0.25em; text-transform: uppercase; color: var(--gold-primary); background: transparent; cursor: pointer; position: relative; overflow: hidden; transition: color 0.4s; }
.btn-gold::before { content: ''; position: absolute; inset: 0; background: var(--gold-primary); transform: translateY(100%); transition: transform 0.4s var(--ease); z-index: -1; }
.btn-gold:hover { color: #000; }
.btn-gold:hover::before { transform: translateY(0); }

/* Hero Section */
.hero-section { position: relative; width: 100%; height: 100vh; min-height: 750px; display: flex; justify-content: center; align-items: center; overflow: hidden; }
#canvas-particles { position: absolute; inset: 0; z-index: 1; }
.hero-content { position: relative; z-index: 10; text-align: center; max-width: 900px; padding: 0 24px; }
.hero-subtitle { font-size: 10px; letter-spacing: 0.6em; text-transform: uppercase; color: var(--gold-primary); margin-bottom: 25px; }
.hero-title { font-family: var(--font-serif); font-size: clamp(64px, 13vw, 170px); font-weight: 400; line-height: 0.85; letter-spacing: 0.08em; margin-bottom: 35px; }
.hero-desc { font-size: 13px; line-height: 1.9; color: var(--text-muted); max-width: 500px; margin: 0 auto 45px; }

/* Parallax Stage Video */
.stage-section { position: relative; width: 100%; height: 160vh; background: #000; }
.stage-sticky { position: sticky; top: 0; width: 100%; height: 100vh; overflow: hidden; display: flex; justify-content: center; align-items: center; }
.stage-video { position: absolute; width: 100%; height: 100%; object-fit: cover; opacity: 0.45; transform: scale(1); transition: transform 0.1s linear; }
.stage-caption { position: relative; z-index: 5; text-align: center; max-width: 800px; padding: 0 20px; }
.stage-caption h2 { font-family: var(--font-serif); font-size: clamp(36px, 6vw, 84px); font-weight: 400; margin-bottom: 20px; color: var(--gold-light); }

/* Interactive Menu */
.menu-section { padding: 160px 6vw; background: var(--bg-dark); position: relative; z-index: 10; }
.section-header { display: flex; justify-content: space-between; align-items: flex-end; margin-bottom: 80px; border-bottom: 1px solid var(--border-line); padding-bottom: 30px; }
.section-title { font-family: var(--font-serif); font-size: clamp(38px, 5vw, 72px); font-weight: 400; }
.menu-grid { display: grid; grid-template-columns: repeat(12, 1fr); gap: 30px; }
.menu-card { grid-column: span 6; background: var(--bg-card); border: 1px solid var(--border-line); padding: 35px; position: relative; cursor: pointer; transition: border-color 0.4s, transform 0.4s var(--ease); }
.menu-card:hover { border-color: var(--gold-primary); transform: translateY(-8px); }
.menu-card-img { width: 100%; height: 320px; object-fit: cover; filter: grayscale(35%) contrast(105%); transition: filter 0.5s, transform 0.8s var(--ease); overflow: hidden; margin-bottom: 25px; }
.menu-card:hover .menu-card-img { filter: grayscale(0%) contrast(100%); transform: scale(1.03); }
.menu-card-header { display: flex; justify-content: space-between; align-items: baseline; margin-bottom: 12px; }
.menu-card-title { font-family: var(--font-serif); font-size: 26px; font-weight: 500; }
.menu-card-price { font-family: var(--font-serif); font-size: 20px; color: var(--gold-primary); }
.menu-card-desc { font-size: 13px; color: var(--text-muted); line-height: 1.7; }
.menu-card-pairing { margin-top: 20px; padding-top: 15px; border-top: 1px dashed rgba(212,175,55,0.2); font-size: 11px; color: var(--gold-light); letter-spacing: 0.08em; }

/* Sommelier Drawer */
.sommelier-drawer { position: fixed; inset: 0; z-index: 2000; background: rgba(3,3,3,0.92); backdrop-filter: blur(20px); display: flex; justify-content: center; align-items: center; opacity: 0; pointer-events: none; transition: opacity 0.4s var(--ease); }
.sommelier-drawer.active { opacity: 1; pointer-events: all; }
.drawer-content { max-width: 600px; width: 90%; background: var(--bg-card); border: 1px solid var(--gold-primary); padding: 45px; position: relative; transform: translateY(30px); transition: transform 0.4s var(--ease); }
.sommelier-drawer.active .drawer-content { transform: translateY(0); }
.drawer-close { position: absolute; top: 20px; right: 20px; background: none; border: none; color: var(--text-muted); font-size: 22px; cursor: pointer; }

/* Concierge Booking */
.booking-section { padding: 140px 6vw; background: #060605; text-align: center; position: relative; }
.booking-box { max-width: 760px; margin: 0 auto; border: 1px solid var(--border-line); padding: 60px 40px; background: linear-gradient(180deg, rgba(212,175,55,0.02) 0%, transparent 100%); }
.booking-form { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-top: 35px; text-align: left; }
.form-group { display: flex; flex-direction: column; gap: 8px; }
.form-group.full { grid-column: span 2; }
.form-group label { font-size: 10px; letter-spacing: 0.2em; text-transform: uppercase; color: var(--gold-primary); }
.form-group input, .form-group select { background: #000; border: 1px solid var(--border-line); padding: 15px; color: var(--text-main); font-family: var(--font-sans); font-size: 13px; outline: none; transition: border-color 0.3s; }
.form-group input:focus, .form-group select:focus { border-color: var(--gold-primary); }

@media(max-width: 900px) {
  .nav-links { display: none; }
  .menu-card { grid-column: span 12; }
  .booking-form { grid-template-columns: 1fr; }
  .form-group.full { grid-column: span 1; }
  .cursor-dot, .cursor-ring { display: none; }
}
</style>
</head>
<body>

<div class="noise-overlay"></div>
<div class="cursor-dot" id="cursorDot"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- Preloader -->
<div class="preloader" id="preloader">
  <div class="preloader-title">PARLE</div>
  <div class="preloader-bar-wrap"><div class="preloader-bar" id="preloaderBar"></div></div>
</div>

<!-- Header -->
<header class="header" id="header">
  <a href="#" class="brand-logo">PARLE<span>.</span></a>
  <ul class="nav-links">
    <li><a href="#stage">Atmosfer</a></li>
    <li><a href="#menu">Gastronomi</a></li>
    <li><a href="#booking">Rezervasyon</a></li>
  </ul>
  <button class="btn-gold" onclick="scrollToBooking()">Masa Seçimi</button>
</header>

<!-- Hero Section with Math Canvas -->
<section class="hero-section">
  <canvas id="canvas-particles"></canvas>
  <div class="hero-content">
    <div class="hero-subtitle">HAUTE GASTRONOMIE & MAISON</div>
    <h1 class="hero-title">PARLE</h1>
    <p class="hero-desc">Duyuların ötesinde bir lezzet mimarisi. Zamansız atmosfer, kusursuz detaylar ve unutulmayacak gastronomi tecrübesi.</p>
    <button class="btn-gold" onclick="scrollToMenu()">Menüyü Deneyimleyin</button>
  </div>
</section>

<!-- Parallax Video Stage -->
<section class="stage-section" id="stage">
  <div class="stage-sticky">
    <video class="stage-video" id="stageVideo" autoplay loop muted playsinline poster="https://images.unsplash.com/photo-1517248135467-4c7edcad34c4?auto=format&fit=crop&w=2000&q=80">
      <source src="https://assets.mixkit.co/videos/preview/mixkit-top-view-of-a-restaurant-table-with-food-41619-large.mp4" type="video/mp4">
    </video>
    <div class="stage-caption">
      <div style="font-size: 10px; letter-spacing: 0.4em; color: var(--gold-primary); margin-bottom: 15px;">ATMOSFER</div>
      <h2>Mekânın Ruhu, Mutfak Mimarisi İle Buluşuyor.</h2>
      <p style="color: var(--text-muted); max-width: 480px; margin: 0 auto; font-size: 13px; line-height: 1.8;">Loş ışıkların ritmi, açık mutfaktan yükselen gastronomi senfonisi.</p>
    </div>
  </div>
</section>

<!-- Menu Showcase -->
<section class="menu-section" id="menu">
  <div class="section-header">
    <div>
      <div style="font-size: 10px; letter-spacing: 0.3em; color: var(--gold-primary); margin-bottom: 10px;">SEÇKİN TADBİRLER</div>
      <h2 class="section-title">İmza Menü</h2>
    </div>
  </div>

  <div class="menu-grid">
    <div class="menu-card" onclick="openSommelier('Trüflü Wagyu Tartare', 'A5 Wagyu sığırı, taze siyah trüf mantarı, bıldırcın yumurtası sarısı ve altın yaprak dokunuşları.', 'Château Margaux 2015 eşleşmesi önerilir.')">
      <img src="https://images.unsplash.com/photo-1544025162-d76694265947?auto=format&fit=crop&w=1000&q=80" class="menu-card-img" alt="Tartare">
      <div class="menu-card-header">
        <div class="menu-card-title">Wagyu Tartare</div>
        <div class="menu-card-price">₺2,400</div>
      </div>
      <p class="menu-card-desc">Siyah trüf emülsiyonu, fermante sarımsak cipsi ve marine edilmiş bıldırcın sarısı.</p>
      <div class="menu-card-pairing">🍷 Sommelier Notu: Bordo Eşleşmesi</div>
    </div>

    <div class="menu-card" onclick="openSommelier('Brittany Istakozu & Safran', 'Brittany Istakozu, Safran infüzyonu, Parmigiano Reggiano 36 Ay ve taze otlar.', 'Dom Pérignon Vintage 2012 ile mükemmel uyum.')">
      <img src="https://images.unsplash.com/photo-1565299624946-b28f40a0ae38?auto=format&fit=crop&w=1000&q=80" class="menu-card-img" alt="Lobster">
      <div class="menu-card-header">
        <div class="menu-card-title">Brittany Lobster</div>
        <div class="menu-card-price">₺3,800</div>
      </div>
      <p class="menu-card-desc">Safranlı arborio pirinci, hafif tereyağı emülsiyonu ve karamelize ıstakoz bisque.</p>
      <div class="menu-card-pairing">🥂 Sommelier Notu: Şampanya Eşleşmesi</div>
    </div>
  </div>
</section>

<!-- Sommelier Drawer Overlay -->
<div class="sommelier-drawer" id="sommelierDrawer">
  <div class="drawer-content">
    <button class="drawer-close" onclick="closeSommelier()">✕</button>
    <div style="font-size: 10px; letter-spacing: 0.3em; color: var(--gold-primary); margin-bottom: 10px;">ŞEFİN NOTU & SOMMELIER SEÇİMİ</div>
    <h3 id="drawerTitle" style="font-family: var(--font-serif); font-size: 28px; margin-bottom: 15px;">-</h3>
    <p id="drawerDesc" style="color: var(--text-muted); font-size: 13px; line-height: 1.8; margin-bottom: 20px;">-</p>
    <div id="drawerPairing" style="padding: 15px; background: rgba(212,175,55,0.05); border: 1px solid var(--border-line); color: var(--gold-light); font-size: 12px;">-</div>
  </div>
</div>

<!-- Concierge Reservation -->
<section class="booking-section" id="booking">
  <div class="booking-box">
    <div style="font-size: 10px; letter-spacing: 0.4em; color: var(--gold-primary); margin-bottom: 12px;">CONCIERGE</div>
    <h2 style="font-family: var(--font-serif); font-size: 38px; margin-bottom: 15px;">Masa Rezerve Edin</h2>
    <p style="color: var(--text-muted); font-size: 13px; max-width: 420px; margin: 0 auto 25px;">Kişiselleştirilmiş gastronomi deneyiminiz için masanızı ayırtın.</p>

    <form class="booking-form" onsubmit="handleBooking(event)">
      <div class="form-group">
        <label>AD SOYAD</label>
        <input type="text" required placeholder="Sn. İsim Soyisim">
      </div>
      <div class="form-group">
        <label>MİSAFİR SAYISI</label>
        <select><option>2 Misafir (Özel Masa)</option><option>4 Misafir</option><option>Chef's Table (Özel Deneyim)</option></select>
      </div>
      <div class="form-group">
        <label>TARİH</label>
        <input type="date" required>
      </div>
      <div class="form-group">
        <label>SAAT</label>
        <select><option>19:30</option><option>20:30</option><option>21:30</option></select>
      </div>
      <div class="form-group full">
        <button type="submit" class="btn-gold" style="width: 100%; margin-top: 10px;">Rezervasyon Talebini Tamamla</button>
      </div>
    </form>
  </div>
</section>

<script>
// Preloader Progress
let progress = 0;
const bar = document.getElementById('preloaderBar');
const preloader = document.getElementById('preloader');

const interval = setInterval(() => {
  progress += Math.floor(Math.random() * 12) + 6;
  if(progress >= 100) {
    progress = 100;
    clearInterval(interval);
    setTimeout(() => preloader.classList.add('completed'), 300);
  }
  bar.style.width = progress + '%';
}, 50);

// Interactive Cursor
const dot = document.getElementById('cursorDot');
const ring = document.getElementById('cursorRing');
let mouseX = 0, mouseY = 0, ringX = 0, ringY = 0;

window.addEventListener('mousemove', e => {
  mouseX = e.clientX;
  mouseY = e.clientY;
  dot.style.left = mouseX + 'px';
  dot.style.top = mouseY + 'px';
});

function renderCursor() {
  ringX += (mouseX - ringX) * 0.15;
  ringY += (mouseY - ringY) * 0.15;
  ring.style.left = ringX + 'px';
  ring.style.top = ringY + 'px';
  requestAnimationFrame(renderCursor);
}
renderCursor();

document.querySelectorAll('button, a, .menu-card').forEach(el => {
  el.addEventListener('mouseenter', () => ring.classList.add('active'));
  el.addEventListener('mouseleave', () => ring.classList.remove('active'));
});

// Canvas Particle Engine
const canvas = document.getElementById('canvas-particles');
const ctx = canvas.getContext('2d');
let particles = [];

function resizeCanvas() {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
}
resizeCanvas();
window.addEventListener('resize', resizeCanvas);

class Particle {
  constructor() { this.reset(); }
  reset() {
    this.x = Math.random() * canvas.width;
    this.y = Math.random() * canvas.height;
    this.size = Math.random() * 1.5 + 0.2;
    this.vx = (Math.random() - 0.5) * 0.3;
    this.vy = (Math.random() - 0.5) * 0.3;
    this.alpha = Math.random() * 0.4 + 0.1;
  }
  update() {
    this.x += this.vx;
    this.y += this.vy;
    if(this.x < 0 || this.x > canvas.width || this.y < 0 || this.y > canvas.height) this.reset();
  }
  draw() {
    ctx.fillStyle = `rgba(212, 175, 55, ${this.alpha})`;
    ctx.beginPath();
    ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
    ctx.fill();
  }
}

for(let i = 0; i < 60; i++) particles.push(new Particle());

function animateParticles() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  particles.forEach(p => { p.update(); p.draw(); });
  requestAnimationFrame(animateParticles);
}
animateParticles();

// Scroll Video Stage Zoom
const stageVideo = document.getElementById('stageVideo');
const header = document.getElementById('header');

window.addEventListener('scroll', () => {
  const scrollY = window.scrollY;
  header.classList.toggle('scrolled', scrollY > 80);

  const stageSection = document.getElementById('stage');
  const rect = stageSection.getBoundingClientRect();
  if(rect.top <= 0 && rect.bottom >= 0) {
    const progress = Math.abs(rect.top) / (rect.height - window.innerHeight);
    stageVideo.style.transform = `scale(${1 + progress * 0.3})`;
  }
});

// Sommelier Drawer Functions
function openSommelier(title, desc, pairing) {
  document.getElementById('drawerTitle').innerText = title;
  document.getElementById('drawerDesc').innerText = desc;
  document.getElementById('drawerPairing').innerText = pairing;
  document.getElementById('sommelierDrawer').classList.add('active');
}

function closeSommelier() {
  document.getElementById('sommelierDrawer').classList.remove('active');
}

function scrollToMenu() { document.getElementById('menu').scrollIntoView({ behavior: 'smooth' }); }
function scrollToBooking() { document.getElementById('booking').scrollIntoView({ behavior: 'smooth' }); }

function handleBooking(e) {
  e.preventDefault();
  alert('Talebiniz VIP Concierge ekibimize iletilmiştir. Konfirme için sizinle iletişime geçilecektir.');
}
</script>
</body>
</html>

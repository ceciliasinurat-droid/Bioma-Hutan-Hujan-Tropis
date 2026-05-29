<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bioma Hutan Hujan Tropis</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;0,700;1,400;1,600&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
:root{--jungle:#0D2B1A;--deep:#071A0F;--canopy:#1A4A28;--mid:#2A6B3A;--leaf:#3A8C4A;--lime:#5AB840;--bright:#7ECC50;--mist:#B8DDB0;--fog:#D4EDD0;--cream:#F2F8EE;--gold:#D4A520;--amber:#C8840A;--rust:#A84820;--water:#2A6880;--river:#4A9CB8;--sky:#8ACCE0}
*{margin:0;padding:0;box-sizing:border-box}
body{font-family:'DM Sans',sans-serif;background:var(--cream);color:var(--jungle);overflow-x:hidden}
.hero{position:relative;height:100vh;min-height:650px;background:linear-gradient(180deg,#0A1F2E 0%,#0D2B1A 18%,#1A4A28 35%,#2A6B3A 52%,#1A4A28 65%,#0D2B1A 100%);overflow:hidden;display:flex;align-items:center;justify-content:center}
.rain-container{position:absolute;inset:0;pointer-events:none;z-index:2}
.raindrop{position:absolute;top:-20px;width:1.5px;background:linear-gradient(to bottom,transparent,rgba(180,230,255,0.5));border-radius:1px;animation:fall linear infinite}
@keyframes fall{0%{transform:translateY(0) translateX(0);opacity:0}10%{opacity:1}90%{opacity:.6}100%{transform:translateY(110vh) translateX(-30px);opacity:0}}
.mist-layer{position:absolute;left:-10%;width:120%;height:120px;border-radius:50%;background:rgba(200,230,210,.12);filter:blur(30px);animation:drift-mist ease-in-out infinite}
@keyframes drift-mist{0%,100%{transform:translateX(0) scaleX(1);opacity:.6}50%{transform:translateX(3%) scaleX(1.04);opacity:.9}}
.firefly{position:absolute;width:4px;height:4px;background:#CCFF88;border-radius:50%;box-shadow:0 0 8px 4px rgba(180,255,100,.6);animation:firefly-float ease-in-out infinite,firefly-blink ease-in-out infinite;z-index:3}
@keyframes firefly-float{0%{transform:translate(0,0)}25%{transform:translate(15px,-20px)}50%{transform:translate(-10px,-35px)}75%{transform:translate(20px,-15px)}100%{transform:translate(0,0)}}
@keyframes firefly-blink{0%,100%{opacity:1}40%,60%{opacity:.1}}
.hero-content{position:relative;z-index:10;text-align:center;color:white;padding:0 20px}
.hero-eyebrow{font-family:'DM Sans',sans-serif;font-weight:300;font-size:.75rem;letter-spacing:6px;text-transform:uppercase;color:var(--bright);margin-bottom:16px;opacity:0;animation:fade-up 1s .3s ease forwards}
.hero-title{font-family:'Cormorant Garamond',serif;font-size:clamp(3.5rem,9vw,7rem);font-weight:700;line-height:.9;color:white;opacity:0;animation:fade-up 1s .6s ease forwards}
.hero-title em{display:block;font-style:italic;color:var(--bright);font-size:.55em;line-height:1.4;font-weight:400}
.hero-desc{margin-top:24px;font-size:.92rem;color:rgba(255,255,255,.7);max-width:480px;margin-left:auto;margin-right:auto;line-height:1.8;font-weight:300;opacity:0;animation:fade-up 1s .9s ease forwards}
@keyframes fade-up{from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:translateY(0)}}
.scroll-cue{position:absolute;bottom:28px;left:50%;transform:translateX(-50%);z-index:10;display:flex;flex-direction:column;align-items:center;gap:8px;opacity:0;animation:fade-up 1s 1.5s ease forwards}
.scroll-line{width:1px;height:50px;background:linear-gradient(to bottom,rgba(100,255,100,.8),transparent);animation:grow-line 1.5s ease-in-out infinite}
@keyframes grow-line{0%{transform:scaleY(0);transform-origin:top}50%{transform:scaleY(1);transform-origin:top}51%{transform:scaleY(1);transform-origin:bottom}100%{transform:scaleY(0);transform-origin:bottom}}
.scroll-cue span{font-size:.65rem;letter-spacing:3px;text-transform:uppercase;color:rgba(255,255,255,.5)}
.stats-bar{background:var(--deep);display:flex;flex-wrap:wrap;justify-content:center}
.stat-block{flex:1;min-width:140px;max-width:200px;padding:32px 16px;text-align:center;border-right:1px solid rgba(255,255,255,.07);position:relative;overflow:hidden}
.stat-block::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:linear-gradient(90deg,transparent,var(--lime),transparent);opacity:0;transition:opacity .3s}
.stat-block:hover::before{opacity:1}
.stat-num{font-family:'Cormorant Garamond',serif;font-size:2.2rem;font-weight:700;color:var(--lime);line-height:1}
.stat-unit{font-size:.7rem;color:rgba(255,255,255,.4);text-transform:uppercase;letter-spacing:2px;margin-top:5px}
.layers-section{background:var(--deep);padding:90px 5%}
.section-tag{font-size:.7rem;letter-spacing:4px;text-transform:uppercase;color:var(--lime);margin-bottom:12px}
.section-heading{font-family:'Cormorant Garamond',serif;font-size:clamp(2rem,5vw,3.5rem);font-weight:700;color:white;margin-bottom:8px;line-height:1.1}
.section-heading em{font-style:italic;color:var(--bright)}
.green-rule{width:40px;height:2px;background:var(--lime);margin:20px 0 50px}
.layers-diagram{display:flex;flex-direction:column;max-width:900px}
.layer-row{display:grid;grid-template-columns:200px 1fr;gap:30px;align-items:stretch;cursor:pointer;transition:background .2s;border-bottom:1px solid rgba(255,255,255,.05)}
.layer-row:hover{background:rgba(255,255,255,.03)}
.layer-visual{position:relative;min-height:120px;display:flex;align-items:center;justify-content:center;overflow:hidden}
.layer-bar{position:absolute;left:0;top:0;bottom:0;width:4px}
.layer-info{padding:28px 0}
.layer-name{font-family:'Cormorant Garamond',serif;font-size:1.5rem;font-weight:600;color:white;margin-bottom:4px}
.layer-height{font-size:.7rem;letter-spacing:2px;text-transform:uppercase;margin-bottom:12px;font-weight:500}
.layer-desc{font-size:.84rem;color:rgba(255,255,255,.55);line-height:1.75;max-width:600px}
.layer-badge{display:inline-block;margin-top:12px;padding:4px 12px;border-radius:20px;font-size:.7rem;letter-spacing:1px;text-transform:uppercase;font-weight:500}
.flora-section{background:var(--cream);padding:90px 5%}
.flora-section .section-heading{color:var(--jungle)}
.flora-section .section-tag{color:var(--mid)}
.flora-section .green-rule{background:var(--mid)}
.flora-masonry{display:grid;grid-template-columns:repeat(auto-fill,minmax(240px,1fr));gap:16px;margin-top:10px}
.flora-card{background:white;overflow:hidden;position:relative;transition:transform .25s,box-shadow .25s;border-bottom:3px solid transparent}
.flora-card:hover{transform:translateY(-4px);box-shadow:0 16px 40px rgba(0,0,0,.12);border-bottom-color:var(--leaf)}
.flora-top{height:120px;display:flex;align-items:center;justify-content:center;font-size:3.5rem;position:relative;overflow:hidden}
.flora-body{padding:20px}
.flora-layer-tag{font-size:.62rem;text-transform:uppercase;letter-spacing:2px;color:var(--mid);font-weight:500;margin-bottom:6px}
.flora-card-name{font-family:'Cormorant Garamond',serif;font-size:1.25rem;font-weight:700;color:var(--jungle);margin-bottom:2px}
.flora-card-latin{font-style:italic;font-size:.78rem;color:var(--amber);margin-bottom:10px}
.flora-card-desc{font-size:.8rem;color:#555;line-height:1.65}
.fauna-section{background:#0F2016;padding:90px 5%}
.fauna-tabs{display:flex;gap:0;margin-bottom:40px;border-bottom:1px solid rgba(255,255,255,.1);flex-wrap:wrap}
.f-tab{padding:12px 22px;background:none;border:none;font-family:'DM Sans',sans-serif;font-size:.82rem;letter-spacing:1px;cursor:pointer;color:rgba(255,255,255,.4);border-bottom:2px solid transparent;margin-bottom:-1px;transition:all .2s;text-transform:uppercase}
.f-tab.active{color:var(--lime);border-bottom-color:var(--lime)}
.f-tab:hover:not(.active){color:rgba(255,255,255,.7)}
.f-panel{display:none}
.f-panel.active{display:grid;grid-template-columns:repeat(auto-fill,minmax(230px,1fr));gap:16px}
.f-card{background:rgba(255,255,255,.04);border:1px solid rgba(255,255,255,.07);padding:22px 18px;display:flex;gap:14px;align-items:flex-start;transition:background .2s,border-color .2s}
.f-card:hover{background:rgba(100,220,80,.07);border-color:rgba(100,220,80,.2)}
.f-emoji{font-size:2rem;flex-shrink:0}
.f-name{font-family:'Cormorant Garamond',serif;font-size:1.05rem;font-weight:700;color:white;margin-bottom:4px}
.f-status{display:inline-block;font-size:.6rem;padding:2px 8px;border-radius:20px;margin-bottom:7px;font-weight:600;letter-spacing:.5px;text-transform:uppercase}
.slc{background:rgba(80,200,80,.2);color:#70E070}
.svu{background:rgba(220,160,40,.2);color:#E0B040}
.sen{background:rgba(220,100,40,.2);color:#E07040}
.scr{background:rgba(220,60,60,.2);color:#E05050}
.f-fact{font-size:.78rem;color:rgba(255,255,255,.5);line-height:1.6}
.data-section{background:white;padding:90px 5%}
.data-section .section-heading{color:var(--jungle)}
.data-section .section-tag{color:var(--mid)}
.data-section .green-rule{background:var(--mid)}
.biome-compare{display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:20px;margin-top:10px}
.compare-card{border:1px solid #e0e8d8;padding:28px;position:relative;overflow:hidden}
.cc-title{font-family:'Cormorant Garamond',serif;font-size:1.3rem;font-weight:700;color:var(--jungle);margin-bottom:20px}
.metric-row{display:flex;align-items:center;gap:12px;margin-bottom:16px}
.metric-label{font-size:.75rem;color:#888;width:130px;flex-shrink:0;text-transform:uppercase;letter-spacing:1px}
.metric-track{flex:1;height:6px;background:#eee;border-radius:3px;overflow:hidden}
.metric-fill{height:100%;border-radius:3px;width:0;transition:width 1.2s cubic-bezier(.4,0,.2,1)}
.metric-val{font-size:.78rem;font-weight:500;color:var(--jungle);width:55px;text-align:right;flex-shrink:0}
.threats-section{background:#F5F0E8;padding:90px 5%}
.threats-section .section-heading{color:var(--jungle)}
.threat-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));gap:20px;margin-top:10px}
.t-card{background:white;padding:28px;border-left:3px solid var(--rust);transition:box-shadow .2s}
.t-card:hover{box-shadow:0 8px 30px rgba(0,0,0,.09)}
.t-icon{font-size:1.8rem;margin-bottom:12px;display:block}
.t-title{font-family:'Cormorant Garamond',serif;font-size:1.2rem;font-weight:700;margin-bottom:10px;color:var(--jungle)}
.t-text{font-size:.82rem;color:#555;line-height:1.7}
.hotspot-section{background:var(--jungle);padding:90px 5%}
.hotspot-section .section-tag{color:var(--bright)}
.hotspot-section .section-heading{color:white}
.hotspot-section .green-rule{background:var(--bright)}
.hotspot-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(220px,1fr));gap:16px;margin-top:10px}
.hotspot-card{border:1px solid rgba(255,255,255,.1);padding:24px;position:relative;overflow:hidden;transition:border-color .2s}
.hotspot-card:hover{border-color:var(--lime)}
.hotspot-num{font-family:'Cormorant Garamond',serif;font-size:3rem;font-weight:700;color:rgba(255,255,255,.06);position:absolute;top:10px;right:16px;line-height:1}
.hotspot-flag{font-size:1.5rem;margin-bottom:10px}
.hotspot-name{font-family:'Cormorant Garamond',serif;font-size:1.2rem;font-weight:700;color:white;margin-bottom:4px}
.hotspot-region{font-size:.7rem;text-transform:uppercase;letter-spacing:2px;color:var(--lime);margin-bottom:10px}
.hotspot-desc{font-size:.78rem;color:rgba(255,255,255,.5);line-height:1.6}
footer{background:var(--deep);color:rgba(255,255,255,.35);text-align:center;padding:32px;font-size:.78rem;letter-spacing:.5px;line-height:1.8}
footer strong{color:var(--lime)}
.indonesia-section{background:var(--deep);padding:90px 5%}
.indonesia-section .section-heading{color:white}
.indonesia-section .section-tag{color:var(--bright)}
.indonesia-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(320px,1fr));gap:24px;margin-top:30px}
.indonesia-card{background:rgba(255,255,255,.04);border:1px solid rgba(255,255,255,.08);border-radius:8px;overflow:hidden;transition:all .3s}
.indonesia-card:hover{background:rgba(90,184,64,.08);border-color:rgba(90,184,64,.2);transform:translateY(-4px)}
.indo-header{background:linear-gradient(135deg,var(--mid),var(--canopy));color:white;padding:16px 20px;font-size:1.1rem;font-weight:600;font-family:'Cormorant Garamond',serif}
.indo-content{padding:20px}
.indo-detail{font-size:.85rem;color:rgba(255,255,255,.7);line-height:1.7;margin-bottom:10px}
.indo-detail:last-child{margin-bottom:0}
.indo-detail strong{color:var(--lime);font-weight:600}
.resources-section{background:var(--cream);padding:90px 5%}
.resources-section .section-heading{color:var(--jungle)}
.resources-section .section-tag{color:var(--water)}
.resources-section .green-rule{background:var(--water)}
.resources-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));gap:28px;margin-top:40px}
.resource-card{background:white;border:1px solid rgba(45,122,92,.15);border-radius:8px;padding:32px;text-align:center;transition:all .3s;box-shadow:0 2px 8px rgba(0,0,0,.04)}
.resource-card:hover{transform:translateY(-8px);box-shadow:0 12px 32px rgba(45,122,92,.15);border-color:rgba(45,122,92,.3)}
.resource-icon{font-size:3rem;margin-bottom:16px;display:block}
.resource-title{font-family:'Cormorant Garamond',serif;font-size:1.3rem;font-weight:700;color:var(--jungle);margin-bottom:12px}
.resource-text{font-size:.9rem;color:#666;line-height:1.75}
</style>
</head>
<body>

<section class="hero">
  <div class="rain-container" id="rain"></div>
  <div id="fireflies"></div>

  <svg style="position:absolute;bottom:0;left:0;width:100%;height:70%;z-index:1;" viewBox="0 0 1440 500" preserveAspectRatio="none" xmlns="http://www.w3.org/2000/svg">
    <ellipse cx="100" cy="80" rx="80" ry="130" fill="#071A0F"/>
    <rect x="94" y="200" width="12" height="300" fill="#050F08"/>
    <ellipse cx="320" cy="50" rx="100" ry="160" fill="#0A1F12"/>
    <rect x="314" y="200" width="14" height="300" fill="#071509"/>
    <ellipse cx="550" cy="70" rx="90" ry="140" fill="#071A0F"/>
    <rect x="544" y="200" width="12" height="300" fill="#050F08"/>
    <ellipse cx="800" cy="40" rx="120" ry="170" fill="#0A1F12"/>
    <rect x="793" y="200" width="16" height="300" fill="#071509"/>
    <ellipse cx="1050" cy="60" rx="95" ry="150" fill="#071A0F"/>
    <rect x="1043" y="200" width="14" height="300" fill="#050F08"/>
    <ellipse cx="1280" cy="50" rx="110" ry="160" fill="#0A1F12"/>
    <rect x="1273" y="200" width="16" height="300" fill="#071509"/>
    <ellipse cx="200" cy="100" rx="70" ry="110" fill="#0D2B1A"/>
    <rect x="195" y="200" width="10" height="300" fill="#081510"/>
    <ellipse cx="450" cy="80" rx="85" ry="135" fill="#112A18"/>
    <rect x="444" y="200" width="12" height="300" fill="#091812"/>
    <ellipse cx="680" cy="70" rx="90" ry="145" fill="#0D2B1A"/>
    <rect x="674" y="200" width="12" height="300" fill="#081510"/>
    <ellipse cx="950" cy="50" rx="100" ry="160" fill="#112A18"/>
    <rect x="943" y="200" width="14" height="300" fill="#091812"/>
    <ellipse cx="1170" cy="80" rx="85" ry="130" fill="#0D2B1A"/>
    <rect x="1163" y="200" width="14" height="300" fill="#081510"/>
    <ellipse cx="0" cy="300" rx="120" ry="200" fill="#1A4A28"/>
    <ellipse cx="250" cy="320" rx="100" ry="180" fill="#163C22"/>
    <ellipse cx="500" cy="310" rx="130" ry="190" fill="#1A4A28"/>
    <ellipse cx="750" cy="300" rx="140" ry="200" fill="#163C22"/>
    <ellipse cx="1000" cy="310" rx="130" ry="195" fill="#1A4A28"/>
    <ellipse cx="1200" cy="300" rx="120" ry="190" fill="#163C22"/>
    <ellipse cx="1440" cy="320" rx="110" ry="180" fill="#1A4A28"/>
    <rect x="0" y="420" width="1440" height="80" fill="#0D2B1A"/>
  </svg>

  <!-- Mist layers -->
  <div class="mist-layer" style="top:35%;height:100px;animation-duration:8s;"></div>
  <div class="mist-layer" style="top:48%;height:90px;animation-duration:11s;animation-delay:-3s;opacity:0.5;"></div>
  <div class="mist-layer" style="top:60%;height:110px;animation-duration:14s;animation-delay:-6s;opacity:0.6;"></div>

  <div class="hero-content">
    <p class="hero-eyebrow">Bioma Bumi · Ekosistem Tropis</p>
    <h1 class="hero-title">
      Hutan Hujan<br>Tropis
      <em>Tropical Rainforest</em>
    </h1>
    <p class="hero-desc">Paru-paru dunia yang menyimpan lebih dari separuh keanekaragaman hayati bumi dalam kerapatan vegetasi tertinggi di planet ini.</p>
  </div>

  <div class="scroll-cue">
    <span>Jelajahi</span>
    <div class="scroll-line"></div>
  </div>
</section>

<!-- STATS -->
<div class="stats-bar">
  <div class="stat-block"><div class="stat-num">6%</div><div class="stat-unit">Luas Daratan Bumi</div></div>
  <div class="stat-block"><div class="stat-num">&gt;50%</div><div class="stat-unit">Spesies di Bumi</div></div>
  <div class="stat-block"><div class="stat-num">2000+</div><div class="stat-unit">mm Hujan / Tahun</div></div>
  <div class="stat-block"><div class="stat-num">25–30°C</div><div class="stat-unit">Suhu Sepanjang Tahun</div></div>
  <div class="stat-block"><div class="stat-num">4</div><div class="stat-unit">Lapisan Vegetasi</div></div>
  <div class="stat-block"><div class="stat-num">80%</div><div class="stat-unit">Kelembapan Udara</div></div>
</div>

<!-- LAYERS -->
<section class="layers-section">
  <div style="max-width:1100px;margin:0 auto;">
    <p class="section-tag">Struktur Vertikal</p>
    <h2 class="section-heading">Lapisan <em>Hutan</em></h2>
    <div class="green-rule"></div>
    <div class="layers-diagram">
      <div class="layer-row">
        <div class="layer-visual" style="background:linear-gradient(135deg,#0A3020,#1A6040);">
          <div class="layer-bar" style="background:#90E050;"></div>
          <span style="font-size:3rem;">🌳</span>
        </div>
        <div class="layer-info">
          <div class="layer-name">Lapisan Emergent (Mahkota)</div>
          <div class="layer-height" style="color:#90E050;">40 – 70 meter</div>
          <div class="layer-desc">Pohon-pohon raksasa yang menjulang menembus kanopi utama. Terpapar sinar matahari penuh, angin kencang, dan suhu ekstrem dibanding lapisan bawah. Dihuni oleh elang harpy, monyet laba-laba, dan kelelawar buah.</div>
          <span class="layer-badge" style="background:rgba(144,224,80,.15);color:#90E050;">Cahaya penuh · Angin kencang</span>
        </div>
      </div>
      <div class="layer-row">
        <div class="layer-visual" style="background:linear-gradient(135deg,#0D3825,#1A5035);">
          <div class="layer-bar" style="background:#60C840;"></div>
          <span style="font-size:3rem;">🌲</span>
        </div>
        <div class="layer-info">
          <div class="layer-name">Lapisan Kanopi</div>
          <div class="layer-height" style="color:#60C840;">20 – 40 meter</div>
          <div class="layer-desc">Atap utama hutan yang membentuk "laut hijau" tak terputus. Menyerap 80% cahaya matahari. Paling kaya biodiversitas — tempat tinggal burung-burung tropis, anggrek epifit, katak pohon, dan primata.</div>
          <span class="layer-badge" style="background:rgba(96,200,64,.15);color:#60C840;">Terkaya Biodiversitas</span>
        </div>
      </div>
      <div class="layer-row">
        <div class="layer-visual" style="background:linear-gradient(135deg,#0A2C1A,#153A22);">
          <div class="layer-bar" style="background:#3A9850;"></div>
          <span style="font-size:3rem;">🌿</span>
        </div>
        <div class="layer-info">
          <div class="layer-name">Lapisan Understory</div>
          <div class="layer-height" style="color:#3A9850;">5 – 20 meter</div>
          <div class="layer-desc">Zona teduh yang hanya menerima 2–5% cahaya matahari. Dihuni tanaman berukuran sedang seperti palem, pakis, dan liana. Harimau, jaguar, ular boa, dan berbagai serangga mendominasi lapisan ini.</div>
          <span class="layer-badge" style="background:rgba(58,152,80,.15);color:#3A9850;">Cahaya redup · Lembap</span>
        </div>
      </div>
      <div class="layer-row">
        <div class="layer-visual" style="background:linear-gradient(135deg,#071A0F,#0F2818);">
          <div class="layer-bar" style="background:#1A6830;"></div>
          <span style="font-size:3rem;">🍄</span>
        </div>
        <div class="layer-info">
          <div class="layer-name">Lapisan Lantai Hutan</div>
          <div class="layer-height" style="color:#1A6830;">0 – 5 meter</div>
          <div class="layer-desc">Hampir tanpa cahaya. Serasah daun terurai sangat cepat oleh jamur, bakteri, dan invertebrata. Tanah kaya aktivitas mikroba. Dihuni gorila, tapir, cacing tanah, kaki seribu, dan semut rangrang.</div>
          <span class="layer-badge" style="background:rgba(26,104,48,.15);color:#1A6830;">Gelap · Pengurai aktif</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- FLORA -->
<section class="flora-section">
  <div style="max-width:1100px;margin:0 auto;">
    <p class="section-tag">Keanekaragaman Tumbuhan</p>
    <h2 class="section-heading">Flora <em style="color:var(--mid)">Hutan Tropis</em></h2>
    <div class="green-rule"></div>
    <div class="flora-masonry">
      <div class="flora-card"><div class="flora-top" style="background:linear-gradient(135deg,#1a4a20,#2a7030);">🌺</div><div class="flora-body"><div class="flora-layer-tag">Kanopi · Epifit</div><div class="flora-card-name">Anggrek Hutan</div><div class="flora-card-latin">Dendrobium & Vanda spp.</div><div class="flora-card-desc">Tumbuh menempel di dahan pohon tanpa parasit. Akar udara menyerap embun dan hujan langsung. Indonesia memiliki 5.000+ spesies anggrek liar.</div></div></div>
      <div class="flora-card"><div class="flora-top" style="background:linear-gradient(135deg,#2a1a10,#4a3020);">🌸</div><div class="flora-body"><div class="flora-layer-tag">Lantai Hutan</div><div class="flora-card-name">Rafflesia arnoldii</div><div class="flora-card-latin">Rafflesia arnoldii</div><div class="flora-card-desc">Bunga tunggal terbesar di dunia (1 meter). Parasit akar liana, tidak punya daun atau batang. Mekar hanya 5–7 hari dengan bau busuk menarik lalat.</div></div></div>
      <div class="flora-card"><div class="flora-top" style="background:linear-gradient(135deg,#1a3a10,#2a6020);">🌴</div><div class="flora-body"><div class="flora-layer-tag">Emergent</div><div class="flora-card-name">Pohon Meranti</div><div class="flora-card-latin">Shorea spp.</div><div class="flora-card-desc">Pohon raksasa khas Asia Tenggara, tinggi hingga 70m. Kayu keras bernilai tinggi. Berbunga massal sekali setiap beberapa tahun (mast seeding).</div></div></div>
      <div class="flora-card"><div class="flora-top" style="background:linear-gradient(135deg,#103010,#204a20);">🌱</div><div class="flora-body"><div class="flora-layer-tag">Understory</div><div class="flora-card-name">Rotan</div><div class="flora-card-latin">Calamus spp.</div><div class="flora-card-desc">Palem memanjat terpanjang di dunia (hingga 200m). Duri pengait memungkinkannya merambat ke kanopi. Bahan baku furnitur dan kerajinan penting.</div></div></div>
      <div class="flora-card"><div class="flora-top" style="background:linear-gradient(135deg,#0a2a18,#154030);">🌿</div><div class="flora-body"><div class="flora-layer-tag">Lantai Hutan</div><div class="flora-card-name">Pakis Raksasa</div><div class="flora-card-latin">Cyathea contaminans</div><div class="flora-card-desc">Tumbuhan purba yang belum banyak berubah sejak zaman dinosaurus. Tinggi hingga 15m. Spora berkembang di kondisi lembap ekstrem lantai hutan.</div></div></div>
      <div class="flora-card"><div class="flora-top" style="background:linear-gradient(135deg,#1a2a08,#2a4010);">🍃</div><div class="flora-body"><div class="flora-layer-tag">Kanopi · Liana</div><div class="flora-card-name">Liana Kayu</div><div class="flora-card-latin">Bauhinia & Entada spp.</div><div class="flora-card-desc">Tanaman merambat berkayu yang menghubungkan pohon-pohon hutan. Jembatan bagi primata. Biji liana laut bisa hanyut ribuan km sebelum berkecambah.</div></div></div>
      <div class="flora-card"><div class="flora-top" style="background:linear-gradient(135deg,#201808,#3a2810);">🌰</div><div class="flora-body"><div class="flora-layer-tag">Emergent</div><div class="flora-card-name">Pohon Kapok / Randu</div><div class="flora-card-latin">Ceiba pentandra</div><div class="flora-card-desc">Pohon sakral suku Maya. Akar banir raksasa menstabilkan tanah di lapisan dangkal. Biji diselimuti serat kapas alami untuk penyebaran benih oleh angin.</div></div></div>
      <div class="flora-card"><div class="flora-top" style="background:linear-gradient(135deg,#081810,#104028);">🎍</div><div class="flora-body"><div class="flora-layer-tag">Understory</div><div class="flora-card-name">Bambu Tropis</div><div class="flora-card-latin">Dendrocalamus asper</div><div class="flora-card-desc">Tanaman berbatang berongga paling cepat tumbuh (90cm/hari). Membentuk rumpun padat di tepi sungai hutan. Pangan dan material konstruksi vital bagi komunitas lokal.</div></div></div>
    </div>
  </div>
</section>

<!-- FAUNA -->
<section class="fauna-section">
  <div style="max-width:1100px;margin:0 auto;">
    <p class="section-tag">Satwa Liar</p>
    <h2 class="section-heading" style="color:white;">Fauna <em style="color:var(--bright);">Hutan Tropis</em></h2>
    <div class="green-rule"></div>
    <div class="fauna-tabs">
      <button class="f-tab active" onclick="switchTab('mamalia',this)">🦁 Mamalia</button>
      <button class="f-tab" onclick="switchTab('burung',this)">🦜 Burung</button>
      <button class="f-tab" onclick="switchTab('reptil',this)">🐍 Reptil & Amfibi</button>
      <button class="f-tab" onclick="switchTab('serangga',this)">🦋 Serangga</button>
    </div>
    <div class="f-panel active" id="fp-mamalia">
      <div class="f-card"><div class="f-emoji">🦧</div><div><div class="f-name">Orangutan</div><span class="f-status scr">Kritis</span><div class="f-fact">Primata Asia tertinggi kecerdasannya. 97% DNA sama dengan manusia. Membangun sarang baru setiap malam di kanopi.</div></div></div>
      <div class="f-card"><div class="f-emoji">🐯</div><div><div class="f-name">Harimau Sumatera</div><span class="f-status scr">Kritis</span><div class="f-fact">Harimau terkecil di dunia, predator puncak hutan Sumatera. Diperkirakan hanya &lt;400 ekor liar tersisa.</div></div></div>
      <div class="f-card"><div class="f-emoji">🐆</div><div><div class="f-name">Jaguar</div><span class="f-status svu">Rentan</span><div class="f-fact">Predator puncak hutan Amazon. Rahang terkuat di antara kucing besar, mampu menembus cangkang kura-kura.</div></div></div>
      <div class="f-card"><div class="f-emoji">🦍</div><div><div class="f-name">Gorila Gunung</div><span class="f-status sen">Terancam</span><div class="f-fact">Hidup di hutan pegunungan Kongo. Hirarki sosial kompleks. Jantan dewasa (silverback) bisa seberat 200 kg.</div></div></div>
      <div class="f-card"><div class="f-emoji">🦏</div><div><div class="f-name">Badak Sumatera</div><span class="f-status scr">Kritis</span><div class="f-fact">Badak berbulu satu-satunya yang masih hidup. &lt;80 ekor tersisa. Herbivora penjelajah hutan lebat.</div></div></div>
      <div class="f-card"><div class="f-emoji">🐘</div><div><div class="f-name">Gajah Kalimantan</div><span class="f-status sen">Terancam</span><div class="f-fact">Subspesies gajah Asia terkecil dan paling jinak. Populasi ~1.500 ekor di hutan Sabah dan Kalimantan Utara.</div></div></div>
      <div class="f-card"><div class="f-emoji">🦦</div><div><div class="f-name">Tapir Malaya</div><span class="f-status sen">Terancam</span><div class="f-fact">Berpenampilan hitam-putih unik sebagai kamuflase di bawah cahaya bulan. Penyebar benih pohon-pohon besar.</div></div></div>
      <div class="f-card"><div class="f-emoji">🐒</div><div><div class="f-name">Owa Jawa</div><span class="f-status sen">Terancam</span><div class="f-fact">Primata monogami sejati. Nyanyian duet pasangan jantan-betina bergema setiap subuh menandai teritorinya.</div></div></div>
    </div>
    <div class="f-panel" id="fp-burung">
      <div class="f-card"><div class="f-emoji">🦜</div><div><div class="f-name">Kakatua Raja</div><span class="f-status svu">Rentan</span><div class="f-fact">Burung terbesar dari keluarga kakaktua. Jambul hitam dramatis, hidup berpasangan seumur hidup di hutan Papua.</div></div></div>
      <div class="f-card"><div class="f-emoji">🦅</div><div><div class="f-name">Elang Harpy</div><span class="f-status svu">Rentan</span><div class="f-fact">Elang terkuat di Amerika Selatan. Cakar sepanjang beruang grizzly. Berburu monyet dan sloth di kanopi Amazon.</div></div></div>
      <div class="f-card"><div class="f-emoji">🦤</div><div><div class="f-name">Burung Surga</div><span class="f-status slc">Aman</span><div class="f-fact">Papua memiliki 42 dari 45 spesies di dunia. Bulu jantan berevolusi ekstrem untuk menarik betina yang sangat selektif.</div></div></div>
      <div class="f-card"><div class="f-emoji">🦚</div><div><div class="f-name">Merak Hijau</div><span class="f-status sen">Terancam</span><div class="f-fact">Asli Indonesia, berbeda dari merak India. Jantan dapat membentangkan ekor hingga 2,5 meter saat kawin.</div></div></div>
      <div class="f-card"><div class="f-emoji">🐦</div><div><div class="f-name">Rangkong Badak</div><span class="f-status svu">Rentan</span><div class="f-fact">Simbol Kalimantan. Tanduk kepalanya (casque) terbuat dari keratin. Berperan vital menyebarkan biji pohon besar.</div></div></div>
      <div class="f-card"><div class="f-emoji">🦆</div><div><div class="f-name">Toucan Raksasa</div><span class="f-status slc">Aman</span><div class="f-fact">Paruh besar justru ringan dan berfungsi mengatur suhu tubuh. Predator oportunistik yang juga makan buah-buahan.</div></div></div>
    </div>
    <div class="f-panel" id="fp-reptil">
      <div class="f-card"><div class="f-emoji">🐍</div><div><div class="f-name">Anaconda Hijau</div><span class="f-status slc">Aman</span><div class="f-fact">Ular terberat di dunia (hingga 250 kg). Mengintai di sungai Amazon, berburu kapibara dan caiman muda.</div></div></div>
      <div class="f-card"><div class="f-emoji">🦎</div><div><div class="f-name">Komodo</div><span class="f-status sen">Terancam</span><div class="f-fact">Kadal terbesar di dunia, reptil warisan zaman purba. Racun dalam air liur mencegah pembekuan darah mangsa.</div></div></div>
      <div class="f-card"><div class="f-emoji">🐊</div><div><div class="f-name">Buaya Muara</div><span class="f-status svu">Rentan</span><div class="f-fact">Reptil terbesar di dunia, penjaga muara sungai hutan tropis. Rahang dengan gigitan terkuat di dunia hewan.</div></div></div>
      <div class="f-card"><div class="f-emoji">🐸</div><div><div class="f-name">Katak Pohon Kaca</div><span class="f-status slc">Aman</span><div class="f-fact">Kulit transparan memperlihatkan organ dalam. Hidup di dedaunan di tepi aliran sungai hutan tropis Amerika.</div></div></div>
      <div class="f-card"><div class="f-emoji">🐢</div><div><div class="f-name">Kura-kura Hutan</div><span class="f-status sen">Terancam</span><div class="f-fact">Penyebar benih penting di lantai hutan. Biji keras yang tidak bisa dimakan hewan lain dicerna oleh kura-kura.</div></div></div>
      <div class="f-card"><div class="f-emoji">🦎</div><div><div class="f-name">Tokek Raksasa</div><span class="f-status slc">Aman</span><div class="f-fact">Kadal nokturnal dengan bantalan jari yang dapat menempel di permukaan halus. Berperan penting mengontrol populasi serangga.</div></div></div>
    </div>
    <div class="f-panel" id="fp-serangga">
      <div class="f-card"><div class="f-emoji">🦋</div><div><div class="f-name">Kupu Morpho Biru</div><span class="f-status slc">Aman</span><div class="f-fact">Sayap biru metalik bukan dari pigmen tapi dari struktur nano yang membiaskan cahaya. Rentang sayap 20 cm.</div></div></div>
      <div class="f-card"><div class="f-emoji">🐛</div><div><div class="f-name">Kumbang Hercules</div><span class="f-status slc">Aman</span><div class="f-fact">Serangga terberat di dunia (85g). Jantan memiliki tanduk panjang untuk berduel memperebutkan betina di Amazon.</div></div></div>
      <div class="f-card"><div class="f-emoji">🐜</div><div><div class="f-name">Semut Pemotong Daun</div><span class="f-status slc">Aman</span><div class="f-fact">Membangun koloni hingga 8 juta pekerja. Membudidayakan jamur sebagai makanan — "pertanian" tertua di bumi.</div></div></div>
      <div class="f-card"><div class="f-emoji">🪲</div><div><div class="f-name">Kumbang Goliath</div><span class="f-status slc">Aman</span><div class="f-fact">Serangga terbesar berdasarkan massa. Larva seberat 100g. Dewasa hanya makan getah pohon dan buah-buahan matang.</div></div></div>
      <div class="f-card"><div class="f-emoji">🕷️</div><div><div class="f-name">Tarantula Goliath</div><span class="f-status slc">Aman</span><div class="f-fact">Laba-laba terbesar di dunia (rentang kaki 30cm). Hidup di liang lantai hutan Amazon, berburu katak kecil dan tikus.</div></div></div>
      <div class="f-card"><div class="f-emoji">✨</div><div><div class="f-name">Kunang-kunang Tropis</div><span class="f-status slc">Aman</span><div class="f-fact">Cahaya bioluminesen mereka berfungsi sinyal kawin. Ribuan kunang-kunang berkedip sinkron di pohon bakau.</div></div></div>
    </div>
  </div>
</section>

<!-- DATA -->
<section class="data-section">
  <div style="max-width:1100px;margin:0 auto;">
    <p class="section-tag">Parameter Ekosistem</p>
    <h2 class="section-heading">Data <em style="color:var(--mid);">Iklim & Kondisi</em></h2>
    <div class="green-rule"></div>
    <div class="biome-compare" id="compareSection">
      <div class="compare-card" style="border-top:3px solid var(--leaf);">
        <div class="cc-title">Kondisi Atmosfer</div>
        <div class="metric-row"><div class="metric-label">Curah Hujan</div><div class="metric-track"><div class="metric-fill" data-w="92%" style="background:var(--river);"></div></div><div class="metric-val">2500 mm</div></div>
        <div class="metric-row"><div class="metric-label">Kelembapan</div><div class="metric-track"><div class="metric-fill" data-w="85%" style="background:var(--sky);"></div></div><div class="metric-val">77–88%</div></div>
        <div class="metric-row"><div class="metric-label">Suhu Rata-rata</div><div class="metric-track"><div class="metric-fill" data-w="62%" style="background:var(--amber);"></div></div><div class="metric-val">27°C</div></div>
        <div class="metric-row"><div class="metric-label">Variasi Suhu</div><div class="metric-track"><div class="metric-fill" data-w="15%" style="background:var(--rust);"></div></div><div class="metric-val">±3°C</div></div>
      </div>
      <div class="compare-card" style="border-top:3px solid var(--mid);">
        <div class="cc-title">Tutupan Vegetasi</div>
        <div class="metric-row"><div class="metric-label">Kanopi Tertutup</div><div class="metric-track"><div class="metric-fill" data-w="95%" style="background:var(--leaf);"></div></div><div class="metric-val">~95%</div></div>
        <div class="metric-row"><div class="metric-label">Kepadatan Pohon</div><div class="metric-track"><div class="metric-fill" data-w="88%" style="background:var(--mid);"></div></div><div class="metric-val">Sangat Tinggi</div></div>
        <div class="metric-row"><div class="metric-label">Epifit</div><div class="metric-track"><div class="metric-fill" data-w="75%" style="background:var(--lime);"></div></div><div class="metric-val">Melimpah</div></div>
        <div class="metric-row"><div class="metric-label">Liana & Panjat</div><div class="metric-track"><div class="metric-fill" data-w="70%" style="background:var(--bright);"></div></div><div class="metric-val">Tinggi</div></div>
      </div>
      <div class="compare-card" style="border-top:3px solid var(--amber);">
        <div class="cc-title">Keanekaragaman Hayati</div>
        <div class="metric-row"><div class="metric-label">Spesies Pohon</div><div class="metric-track"><div class="metric-fill" data-w="97%" style="background:var(--mid);"></div></div><div class="metric-val">400+/ha</div></div>
        <div class="metric-row"><div class="metric-label">Spesies Serangga</div><div class="metric-track"><div class="metric-fill" data-w="99%" style="background:var(--lime);"></div></div><div class="metric-val">Jutaan</div></div>
        <div class="metric-row"><div class="metric-label">Spesies Burung</div><div class="metric-track"><div class="metric-fill" data-w="80%" style="background:var(--sky);"></div></div><div class="metric-val">1300+</div></div>
        <div class="metric-row"><div class="metric-label">Endemisitas</div><div class="metric-track"><div class="metric-fill" data-w="90%" style="background:var(--gold);"></div></div><div class="metric-val">Sangat Tinggi</div></div>
      </div>
    </div>
  </div>
</section>

<!-- THREATS -->
<section class="threats-section">
  <div style="max-width:1100px;margin:0 auto;">
    <p class="section-tag" style="color:var(--rust);">Ancaman & Konservasi</p>
    <h2 class="section-heading">Bahaya yang <em style="color:var(--rust);">Mengancam</em></h2>
    <div class="green-rule" style="background:var(--rust);"></div>
    <div class="threat-grid">
      <div class="t-card"><span class="t-icon">🪚</span><div class="t-title">Deforestasi & Pembalakan</div><div class="t-text">Setiap menit, luas hutan setara 40 lapangan bola hilang. Pembalakan legal maupun ilegal mengancam integritas ekosistem hutan tropis yang telah terbentuk jutaan tahun.</div></div>
      <div class="t-card"><span class="t-icon">🌋</span><div class="t-title">Kebakaran Hutan</div><div class="t-text">Hutan hujan tropis yang seharusnya terlalu lembap untuk terbakar kini rentan akibat kekeringan panjang El Niño. Kebakaran gambut melepaskan karbon tersimpan ribuan tahun ke atmosfer.</div></div>
      <div class="t-card"><span class="t-icon">🌡️</span><div class="t-title">Perubahan Iklim</div><div class="t-text">Peningkatan suhu menggeser zona iklim, mengubah pola hujan, dan mengancam spesies yang beradaptasi dalam rentang toleransi sempit. Amazon berpotensi mencapai titik kritis dalam 15–20 tahun.</div></div>
      <div class="t-card"><span class="t-icon">🌾</span><div class="t-title">Konversi Perkebunan</div><div class="t-text">Ekspansi kelapa sawit, kedelai, dan ternak sapi menjadi penyebab utama deforestasi di Asia Tenggara dan Amerika Selatan. Monokultur menggantikan ekosistem paling beragam di Bumi.</div></div>
      <div class="t-card"><span class="t-icon">🔫</span><div class="t-title">Perburuan & Perdagangan Liar</div><div class="t-text">Perdagangan ilegal satwa liar senilai $23 miliar per tahun. Primata, reptil, dan burung eksotis diperdagangkan secara global, mengancam populasi spesies yang sudah terancam punah.</div></div>
      <div class="t-card"><span class="t-icon">⛏️</span><div class="t-title">Pertambangan</div><div class="t-text">Tambang emas, nikel, dan mineral langka membuka tutupan hutan, mencemari sungai dengan merkuri, dan menghancurkan habitat endemik yang tidak ditemukan di tempat lain di Bumi.</div></div>
    </div>
  </div>
</section>

<!-- HOTSPOTS -->
<section class="hotspot-section">
  <div style="max-width:1100px;margin:0 auto;">
    <p class="section-tag">Persebaran Global</p>
    <h2 class="section-heading">Hotspot <em style="color:var(--bright);">Hutan Tropis</em></h2>
    <div class="green-rule"></div>
    <div class="hotspot-grid">
      <div class="hotspot-card"><div class="hotspot-num">01</div><div class="hotspot-flag">🇧🇷</div><div class="hotspot-name">Amazon</div><div class="hotspot-region">Amerika Selatan</div><div class="hotspot-desc">Hutan hujan tropis terbesar di Bumi. 5,5 juta km², rumah bagi 10% spesies di planet ini. Sungai Amazon mengalirkan 20% air tawar dunia ke laut.</div></div>
      <div class="hotspot-card"><div class="hotspot-num">02</div><div class="hotspot-flag">🇮🇩</div><div class="hotspot-name">Kalimantan</div><div class="hotspot-region">Asia Tenggara</div><div class="hotspot-desc">Pulau ketiga terbesar di dunia dengan hutan hujan tropis tertua (140 juta tahun). Pusat keanekaragaman hayati Asia, habitat orangutan, proboscis, dan bekantan.</div></div>
      <div class="hotspot-card"><div class="hotspot-num">03</div><div class="hotspot-flag">🇨🇩</div><div class="hotspot-name">Kongo</div><div class="hotspot-region">Afrika Tengah</div><div class="hotspot-desc">Hutan hujan terbesar kedua di dunia. Rumah gorila, bonobo, dan okapi. Lembah Kongo menjadi "paru-paru hijau" benua Afrika.</div></div>
      <div class="hotspot-card"><div class="hotspot-num">04</div><div class="hotspot-flag">🇵🇬</div><div class="hotspot-name">Papua</div><div class="hotspot-region">Oceania</div><div class="hotspot-desc">Salah satu kawasan paling tidak terjamah di dunia. Ribuan spesies belum teridentifikasi ilmu pengetahuan. Hutan pegunungan dengan fauna endemik luar biasa.</div></div>
      <div class="hotspot-card"><div class="hotspot-num">05</div><div class="hotspot-flag">🇲🇾</div><div class="hotspot-name">Sundaland</div><div class="hotspot-region">Asia Tenggara</div><div class="hotspot-desc">Semenanjung Malaya dan Sumatra sebagai hotspot biodiversitas kritis. Harimau Sumatera, badak Sumatera, dan gajah Kalimantan hidup di sini.</div></div>
      <div class="hotspot-card"><div class="hotspot-num">06</div><div class="hotspot-flag">🇲🇬</div><div class="hotspot-name">Madagaskar</div><div class="hotspot-region">Afrika</div><div class="hotspot-desc">90% spesies tumbuhan dan hewannya endemik, tidak ditemukan di mana pun di Bumi. Evolusi terisolasi selama 88 juta tahun menciptakan kehidupan yang benar-benar unik.</div></div>
    </div>
  </div>
</section>


<!-- INDONESIA LOCATIONS -->
<section class="indonesia-section">
  <div style="max-width:1100px;margin:0 auto;">
    <p class="section-tag">Ekosistem Nusantara</p>
    <h2 class="section-heading">Hutan Hujan Tropis <em style="color:var(--bright);">Indonesia</em></h2>
    <div class="green-rule"></div>
    <div class="indonesia-grid">
      <div class="indonesia-card">
        <div class="indo-header">🇮🇩 Kalimantan</div>
        <div class="indo-content">
          <div class="indo-detail"><strong>Luas:</strong> ~73 juta hektar</div>
          <div class="indo-detail"><strong>Umur Hutan:</strong> 140 juta tahun (tertua di Asia Tenggara)</div>
          <div class="indo-detail"><strong>Lokasi:</strong> Pulau Kalimantan (Kaltim, Kalbar, Kalteng, Kalisel)</div>
          <div class="indo-detail"><strong>Fauna Khasusus:</strong> Orangutan Borneo, Bekantan, Proboscis, Gajah Borneo, Badak Sumatera</div>
          <div class="indo-detail"><strong>Karakter:</strong> Hutan dataran rendah dengan pohon meranti, kapur, dan rimba primer yang sangat lebat</div>
        </div>
      </div>
      <div class="indonesia-card">
        <div class="indo-header">🇮🇩 Sumatera</div>
        <div class="indo-content">
          <div class="indo-detail"><strong>Luas:</strong> ~50 juta hektar</div>
          <div class="indo-detail"><strong>Lokasi:</strong> Pulau Sumatera (Aceh, Riau, Jambi, Bengkulu, Sumsel, Lampung)</div>
          <div class="indo-detail"><strong>Fauna Khasusus:</strong> Harimau Sumatera, Badak Sumatera, Gajah Sumatera, Orangutan Sumatera</div>
          <div class="indo-detail"><strong>Habitat Penting:</strong> Taman Nasional Tanjung Puting, Bukit Barisan Selatan, Kerinci Seblat</div>
          <div class="indo-detail"><strong>Karakter:</strong> Hutan pegunungan dan dataran rendah dengan ekosistem lembap, rawa gambut, dan hutan sekunder yang dinamis</div>
        </div>
      </div>
      <div class="indonesia-card">
        <div class="indo-header">🇮🇩 Papua & Maluku</div>
        <div class="indo-content">
          <div class="indo-detail"><strong>Luas:</strong> ~40 juta hektar</div>
          <div class="indo-detail"><strong>Lokasi:</strong> Papua, Papua Barat, Maluku, Maluku Utara</div>
          <div class="indo-detail"><strong>Fauna Khasusus:</strong> Burung Cendrawasih, Kasuari, Lumba-lumba Irawaddy, Trenggiling</div>
          <div class="indo-detail"><strong>Endemisitas:</strong> Salah satu kawasan paling endemik di dunia, ribuan spesies belum teridentifikasi</div>
          <div class="indo-detail"><strong>Karakter:</strong> Hutan pegunungan dengan keragaman flora-fauna paling tinggi, ekosistem karang-mangrove di pesisir</div>
        </div>
      </div>
      <div class="indonesia-card">
        <div class="indo-header">🇮🇩 Hutan Hujan Jawa</div>
        <div class="indo-content">
          <div class="indo-detail"><strong>Luas:</strong> ~3-4 juta hektar (tersisa)</div>
          <div class="indo-detail"><strong>Lokasi:</strong> Jawa Barat, Jawa Tengah, Jawa Timur (pegunungan)</div>
          <div class="indo-detail"><strong>Fauna Khasusus:</strong> Badak Jawa (kritis), Harimau Jawa (punah), Tarsius, Elang Jawa</div>
          <div class="indo-detail"><strong>Taman Penting:</strong> Ujung Kulon, Gunung Halimun, Gede-Pangrango, Bromo-Semeru</div>
          <div class="indo-detail"><strong>Karakter:</strong> Hutan pegunungan tropis dengan vegetasi heterogen, banyak endemit lokal, status sangat kritis</div>
        </div>
      </div>
      <div class="indonesia-card">
        <div class="indo-header">🇮🇩 Hutan Hujan Sulawesi</div>
        <div class="indo-content">
          <div class="indo-detail"><strong>Luas:</strong> ~20 juta hektar</div>
          <div class="indo-detail"><strong>Lokasi:</strong> Sulawesi (Utara, Tengah, Selatan, Tenggara)</div>
          <div class="indo-detail"><strong>Fauna Khasusus:</strong> Babi Rusa, Anoa, Tangkasi, Maleo, Luwak Sulawesi</div>
          <div class="indo-detail"><strong>Tingkat Endemisitas:</strong> 89% mamalia endemik, 72% burung endemik</div>
          <div class="indo-detail"><strong>Karakter:</strong> Pulau vulkanik dengan hutan pegunungan unik, ekosistem laut-darat yang terintegrasi baik</div>
        </div>
      </div>
      <div class="indonesia-card">
        <div class="indo-header">🇮🇩 Nusa Tenggara & Timor</div>
        <div class="indo-content">
          <div class="indo-detail"><strong>Luas:</strong> ~8 juta hektar (hutan, savana, dan padang rumput)</div>
          <div class="indo-detail"><strong>Lokasi:</strong> Nusa Tenggara (Flores, Sumba, Sumbawa, Timor Barat)</div>
          <div class="indo-detail"><strong>Fauna Khasusus:</strong> Komodo, Rusa Timor, Burung Endemik, Pesut Mahakam</div>
          <div class="indo-detail"><strong>Habitat Transisi:</strong> Percampuran hutan hujan tropis, hutan musiman, dan savana</div>
          <div class="indo-detail"><strong>Karakter:</strong> Ekosistem unik dengan flora-fauna campuran Asia dan Australia (Wallace Line)</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- NATURAL RESOURCES -->
<section class="resources-section">
  <div style="max-width:1100px;margin:0 auto;">
    <p class="section-tag" style="color:var(--river);">Nilai Ekosistem</p>
    <h2 class="section-heading">Sumber Daya Alam <em style="color:var(--river);">Hutan Tropis</em></h2>
    <div class="green-rule" style="background:var(--river);"></div>
    <div class="resources-grid">
      <div class="resource-card">
        <div class="resource-icon">🫁</div>
        <div class="resource-title">Penyerap Karbon Global</div>
        <div class="resource-text">Hutan tropis menyerap 2,4 miliar ton karbon setiap tahun. Pohon-pohon raksasa dengan umur ribuan tahun menyimpan karbon dalam kayu dan tanah. Kehilangan hutan berarti pelepasan karbon tersimpan jutaan tahun ke atmosfer.</div>
      </div>
      <div class="resource-card">
        <div class="resource-icon">💧</div>
        <div class="resource-title">Pengatur Siklus Air</div>
        <div class="resource-text">Transpirasi pohon hutan tropis mengembalikan 20 triliun ton air ke atmosfer per tahun. Mempengaruhi pola hujan regional dan global. Amazon saja menghasilkan setengah dari curah hujannya sendiri melalui siklus evapotranspirasi.</div>
      </div>
      <div class="resource-card">
        <div class="resource-icon">🌿</div>
        <div class="resource-title">Sumber Obat & Bahan Kimia</div>
        <div class="resource-text">25% obat modern berasal dari tumbuhan hutan tropis. Quinine dari kuinina untuk malaria, morphine dari poppy, aspirin dari willow. Ilmuwan memperkirakan masih ada 137.900 spesies tanaman obat yang belum diteliti di hutan tropis.</div>
      </div>
      <div class="resource-card">
        <div class="resource-icon">🏭</div>
        <div class="resource-title">Bahan Baku Industri</div>
        <div class="resource-text">Kayu keras untuk furnitur, veneer, dan konstruksi. Karet alami dari pohon Hevea brasiliensis. Cokelat, kopi, dan rempah-rempah (pala, cengkih) berasal dari hutan tropis. Minyak esensial untuk parfum dan kosmetik dari tanaman aromatik hutan.</div>
      </div>
      <div class="resource-card">
        <div class="resource-icon">🍯</div>
        <div class="resource-title">Pangan & Nutrisi Tradisional</div>
        <div class="resource-text">Ribuan spesies buah hutan tropis yang kaya nutrisi: acai, cacao, durian, rambutan, mangga, bakau. Madu hutan dari lebah lokal. Tanaman pangan tradisional seperti cassava, yam, dan sagu menjadi sumber kalori utama masyarakat lokal.</div>
      </div>
      <div class="resource-card">
        <div class="resource-icon">🧬</div>
        <div class="resource-title">Reservoir Genetik Biodiversitas</div>
        <div class="resource-text">Hutan tropis menyimpan gen-gen unik hasil evolusi jutaan tahun. Gen tahan penyakit, adaptasi lingkungan ekstrem, kemampuan metabolisme unik yang bisa dimanfaatkan untuk pemuliaan tanaman dan rekayasa genetik masa depan.</div>
      </div>
      <div class="resource-card">
        <div class="resource-icon">🌍</div>
        <div class="resource-title">Regulasi Iklim Planet</div>
        <div class="resource-text">Hutan tropis mempengaruhi pola monsun, sistem arus lautan, dan jet streams global. Deforestasi luas bisa memicu "tipping point" perubahan iklim yang tidak reversibel. Menjaga hutan tropis adalah investasi untuk stabilitas iklim global.</div>
      </div>
      <div class="resource-card">
        <div class="resource-icon">🏞️</div>
        <div class="resource-title">Nilai Ekowisata & Rekreasi</div>
        <div class="resource-text">Ekowisata hutan tropis menghasilkan miliaran dollar per tahun. Wisata petualangan, penelitian, fotografi alam, dan spiritual retreat. Menciptakan lapangan kerja berkelanjutan tanpa merusak hutan, memberikan insentif ekonomi untuk konservasi.</div>
      </div>
      <div class="resource-card">
        <div class="resource-icon">📚</div>
        <div class="resource-title">Warisan Budaya & Pengetahuan</div>
        <div class="resource-text">Ribuan komunitas indigenous menghuni hutan tropis dengan pengetahuan etnobotani mendalam. Sistem medis tradisional, praktik pertanian berkelanjutan, dan spiritual wisdom yang terakumulasi ribuan tahun. Pengetahuan ini bernilai intelektual dan praktis yang tak ternilai.</div>
      </div>
    </div>
  </div>
</section>

<footer>
  <strong>Hutan Hujan Tropis</strong> — Menutupi hanya 6% permukaan bumi, namun menjadi tempat tinggal lebih dari 50% spesies yang diketahui.<br>
  Setiap tahun, hutan tropis menyerap 2,4 miliar ton karbon — senjata terpenting dalam melawan krisis iklim.
</footer>

<script>
(function(){
  var c=document.getElementById('rain');
  for(var i=0;i<120;i++){
    var d=document.createElement('div');
    d.className='raindrop';
    var left=Math.random()*110-5;
    var h=15+Math.random()*35;
    var dur=0.6+Math.random()*0.8;
    var delay=-Math.random()*3;
    d.style.cssText='left:'+left+'%;height:'+h+'px;animation-duration:'+dur+'s;animation-delay:'+delay+'s;opacity:'+(0.3+Math.random()*0.5);
    c.appendChild(d);
  }
})();
(function(){
  var c=document.getElementById('fireflies');
  c.style.cssText='position:absolute;inset:0;z-index:3;pointer-events:none;';
  var colors=['#CCFF88','#AAFFCC','#FFFF88','#88FFCC'];
  for(var i=0;i<30;i++){
    var f=document.createElement('div');
    f.className='firefly';
    f.style.cssText='left:'+(5+Math.random()*90)+'%;top:'+(20+Math.random()*70)+'%;animation-duration:'+(4+Math.random()*6)+'s,'+(1.5+Math.random()*2)+'s;animation-delay:'+(-Math.random()*8)+'s,'+(-Math.random()*3)+'s;background:'+colors[Math.floor(Math.random()*colors.length)]+';box-shadow:0 0 '+(6+Math.random()*8)+'px '+(3+Math.random()*5)+'px rgba(180,255,100,0.6);';
    c.appendChild(f);
  }
})();
function switchTab(id,el){
  document.querySelectorAll('.f-tab').forEach(function(t){t.classList.remove('active')});
  document.querySelectorAll('.f-panel').forEach(function(p){p.classList.remove('active')});
  el.classList.add('active');
  document.getElementById('fp-'+id).classList.add('active');
}
var fills=document.querySelectorAll('.metric-fill');
var obs=new IntersectionObserver(function(entries){entries.forEach(function(e){if(e.isIntersecting){fills.forEach(function(f){f.style.width=f.dataset.w});obs.disconnect()}})},{threshold:0.3});
var cs=document.getElementById('compareSection');
if(cs)obs.observe(cs);
</script>
</body>
</html>

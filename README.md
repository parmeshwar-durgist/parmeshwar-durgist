<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Parmeshwar Durgist · 3D Profile</title>
  <style>
    /* ================= RESET ================= */
    *, *::before, *::after {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    html, body {
      width: 100%;
      height: 100%;
      overflow: hidden;
      font-family: 'Inter', 'Segoe UI', system-ui, -apple-system, sans-serif;
      background: #03040c;
    }

    /* ================= STARFIELD ================= */
    .stars {
      position: fixed;
      inset: 0;
      background-image:
        radial-gradient(2px 2px at 20px 30px, rgba(255,255,255,0.35), transparent),
        radial-gradient(2px 2px at 40px 70px, rgba(0,194,255,0.45), transparent),
        radial-gradient(1px 1px at 90px 40px, rgba(255,255,255,0.25), transparent),
        radial-gradient(2px 2px at 160px 120px, rgba(123,104,238,0.35), transparent),
        radial-gradient(1px 1px at 300px 250px, rgba(255,255,255,0.4), transparent),
        radial-gradient(2px 2px at 420px 80px, rgba(0,194,255,0.3), transparent),
        radial-gradient(1px 1px at 550px 320px, rgba(255,255,255,0.25), transparent),
        radial-gradient(2px 2px at 680px 190px, rgba(123,104,238,0.35), transparent);
      background-size: 800px 400px;
      background-repeat: repeat;
      animation: twinkle 8s ease-in-out infinite alternate;
      pointer-events: none;
      z-index: 0;
    }

    @keyframes twinkle {
      0%   { opacity: 0.45; }
      100% { opacity: 1; }
    }

    /* ================= SCENE ================= */
    .scene {
      position: relative;
      width: 100vw;
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      perspective: 1400px;
      perspective-origin: 50% 45%;
      z-index: 2;
    }

    /* ================= GLOW ORB BEHIND ================= */
    .glow-orb {
      position: absolute;
      width: 520px;
      height: 520px;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(0,194,255,0.18) 0%, rgba(123,104,238,0.08) 40%, transparent 70%);
      filter: blur(40px);
      animation: orbPulse 6s ease-in-out infinite;
      pointer-events: none;
      z-index: 0;
    }

    @keyframes orbPulse {
      0%, 100% { transform: scale(1); opacity: 0.7; }
      50%      { transform: scale(1.18); opacity: 1; }
    }

    /* ================= 3D CARD GROUP ================= */
    .card-group {
      position: relative;
      transform-style: preserve-3d;
      animation: cardFloat 7s ease-in-out infinite, cardRotate 16s ease-in-out infinite alternate;
    }

    @keyframes cardFloat {
      0%, 100% { transform: translateY(0) rotateX(0deg) rotateY(0deg); }
      50%      { transform: translateY(-16px) rotateX(4deg) rotateY(-4deg); }
    }

    @keyframes cardRotate {
      0%   { transform: rotateY(-14deg) rotateX(8deg); }
      50%  { transform: rotateY(14deg) rotateX(6deg); }
      100% { transform: rotateY(-14deg) rotateX(8deg); }
    }

    /* combine float + rotate via nested element */
    .card-group .float-wrap {
      transform-style: preserve-3d;
      animation: floatY 5s ease-in-out infinite;
    }

    @keyframes floatY {
      0%, 100% { transform: translateY(0); }
      50%      { transform: translateY(-14px); }
    }

    /* ================= MAIN 3D PLATE ================= */
    .plate {
      position: relative;
      width: 620px;
      height: 280px;
      border-radius: 32px;
      background:
        linear-gradient(145deg, #0d1226 0%, #060918 100%);
      border: 1px solid rgba(0,194,255,0.28);
      box-shadow:
        0 0 0 1px rgba(0,194,255,0.08) inset,
        0 40px 80px -30px rgba(0,0,0,0.95),
        0 0 60px rgba(0,194,255,0.15),
        0 0 120px rgba(123,104,238,0.1),
        0 60px 100px -40px rgba(0,194,255,0.15);
      transform-style: preserve-3d;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 30px;
      overflow: hidden;
      transition: box-shadow 0.4s ease;
    }

    .plate:hover {
      box-shadow:
        0 0 0 1px rgba(0,194,255,0.14) inset,
        0 50px 100px -30px rgba(0,0,0,0.95),
        0 0 80px rgba(0,194,255,0.3),
        0 0 160px rgba(123,104,238,0.18);
    }

    /* Inner gradient glow */
    .plate::before {
      content: '';
      position: absolute;
      inset: 0;
      border-radius: 32px;
      background: linear-gradient(
        135deg,
        rgba(0,194,255,0.14) 0%,
        transparent 35%,
        transparent 65%,
        rgba(123,104,238,0.14) 100%
      );
      pointer-events: none;
      z-index: 0;
    }

    /* Shine sweep */
    .plate::after {
      content: '';
      position: absolute;
      top: -80%;
      left: -80%;
      width: 260%;
      height: 260%;
      background: linear-gradient(
        115deg,
        transparent 32%,
        rgba(255,255,255,0.04) 46%,
        rgba(0,194,255,0.1) 50%,
        rgba(255,255,255,0.04) 54%,
        transparent 68%
      );
      transform: rotate(25deg);
      animation: shine 8s linear infinite;
      pointer-events: none;
      z-index: 1;
    }

    @keyframes shine {
      0%   { transform: rotate(25deg) translateX(-35%); }
      100% { transform: rotate(25deg) translateX(35%); }
    }

    /* ================= TEXT CONTENT ================= */
    .name {
      position: relative;
      z-index: 3;
      font-size: 3.4rem;
      font-weight: 800;
      letter-spacing: 0.06em;
      text-transform: uppercase;
      background: linear-gradient(135deg, #ffffff 15%, #b0e0ff 55%, #00c2ff 100%);
      -webkit-background-clip: text;
      background-clip: text;
      -webkit-text-fill-color: transparent;
      text-shadow:
        0 0 30px rgba(0,194,255,0.45),
        0 0 80px rgba(0,194,255,0.15);
      transform: translateZ(50px);
      animation: nameGlow 3s ease-in-out infinite alternate;
      line-height: 1.05;
      text-align: center;
      white-space: nowrap;
    }

    @keyframes nameGlow {
      0%   { filter: drop-shadow(0 0 14px rgba(0,194,255,0.3)); }
      100% { filter: drop-shadow(0 0 36px rgba(0,194,255,0.75)); }
    }

    .subtitle {
      position: relative;
      z-index: 3;
      margin-top: 14px;
      font-size: 0.95rem;
      font-weight: 400;
      letter-spacing: 0.4em;
      text-transform: uppercase;
      color: #8ab8e0;
      text-shadow: 0 0 22px rgba(0,194,255,0.35);
      transform: translateZ(30px);
    }

    .divider {
      position: relative;
      z-index: 3;
      width: 72%;
      height: 1px;
      margin: 24px 0 20px;
      background: linear-gradient(90deg, transparent, rgba(0,194,255,0.5), rgba(123,104,238,0.5), transparent);
      transform: translateZ(25px);
    }

    /* ================= BADGES ================= */
    .badges {
      position: relative;
      z-index: 3;
      display: flex;
      gap: 14px;
      flex-wrap: wrap;
      justify-content: center;
      transform: translateZ(40px);
    }

    .badge {
      padding: 8px 22px;
      border-radius: 40px;
      font-size: 0.72rem;
      font-weight: 500;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      color: #d0eaff;
      background: rgba(0,194,255,0.08);
      border: 1px solid rgba(0,194,255,0.35);
      box-shadow:
        0 0 22px rgba(0,194,255,0.12),
        0 0 0 1px rgba(0,194,255,0.05) inset;
      backdrop-filter: blur(6px);
      transition: all 0.3s ease;
      animation: badgeFloat 4s ease-in-out infinite;
      cursor: default;
    }

    .badge:nth-child(2) { animation-delay: 0.6s; }
    .badge:nth-child(3) { animation-delay: 1.2s; }

    @keyframes badgeFloat {
      0%, 100% { transform: translateY(0); }
      50%      { transform: translateY(-4px); }
    }

    .badge:hover {
      background: rgba(0,194,255,0.2);
      border-color: rgba(0,194,255,0.75);
      box-shadow: 0 0 32px rgba(0,194,255,0.35);
      transform: translateY(-3px) scale(1.03);
    }

    /* ================= FLOATING 3D ICONS ================= */
    .icon {
      position: absolute;
      border-radius: 30% 70% 70% 30% / 30% 30% 70% 70%;
      animation: iconFloat 6s ease-in-out infinite;
      transform-style: preserve-3d;
      z-index: 2;
      pointer-events: none;
    }

    .icon::after {
      content: '';
      position: absolute;
      inset: 20%;
      border-radius: 50%;
      background: radial-gradient(circle at 40% 40%, rgba(255,255,255,0.4), transparent 70%);
    }

    .icon1 {
      width: 40px; height: 40px;
      top: 8%; left: 4%;
      background: radial-gradient(circle at 30% 30%, #00c2ff, #003355);
      box-shadow: 0 0 30px rgba(0,194,255,0.55), 0 0 70px rgba(0,194,255,0.2);
      animation-delay: 0s;
    }

    .icon2 {
      width: 28px; height: 28px;
      top: 70%; left: 2%;
      background: radial-gradient(circle at 30% 30%, #7b68ee, #2a1a5e);
      box-shadow: 0 0 30px rgba(123,104,238,0.55), 0 0 70px rgba(123,104,238,0.2);
      animation-delay: 1.2s;
    }

    .icon3 {
      width: 34px; height: 34px;
      top: 12%; right: 3%;
      background: radial-gradient(circle at 30% 30%, #ffaa00, #664400);
      box-shadow: 0 0 30px rgba(255,170,0,0.55), 0 0 70px rgba(255,170,0,0.2);
      animation-delay: 0.8s;
    }

    .icon4 {
      width: 24px; height: 24px;
      top: 74%; right: 2%;
      background: radial-gradient(circle at 30% 30%, #00ffaa, #005544);
      box-shadow: 0 0 30px rgba(0,255,170,0.55), 0 0 70px rgba(0,255,170,0.2);
      animation-delay: 1.8s;
    }

    .icon5 {
      width: 20px; height: 20px;
      top: 44%; left: 0.5%;
      background: radial-gradient(circle at 30% 30%, #ff66aa, #661133);
      box-shadow: 0 0 30px rgba(255,102,170,0.55), 0 0 70px rgba(255,102,170,0.2);
      animation-delay: 2.4s;
    }

    .icon6 {
      width: 22px; height: 22px;
      top: 48%; right: 0.5%;
      background: radial-gradient(circle at 30% 30%, #00c2ff, #003355);
      box-shadow: 0 0 30px rgba(0,194,255,0.55), 0 0 70px rgba(0,194,255,0.2);
      animation-delay: 3s;
    }

    @keyframes iconFloat {
      0%, 100% { transform: translateY(0) rotate(0deg) scale(1); }
      50%      { transform: translateY(-20px) rotate(14deg) scale(1.1); }
    }

    /* ================= CSS PARTICLES ================= */
    .particle {
      position: absolute;
      border-radius: 50%;
      background: #ffffff;
      opacity: 0;
      animation: particleRise linear infinite;
      pointer-events: none;
      z-index: 1;
    }

    @keyframes particleRise {
      0%   { transform: translateY(0) translateX(0); opacity: 0; }
      10%  { opacity: 0.85; }
      90%  { opacity: 0.85; }
      100% { transform: translateY(-160px) translateX(50px); opacity: 0; }
    }

    /* ================= FOOTER CREDIT ================= */
    .footer-credit {
      position: fixed;
      bottom: 18px;
      left: 0;
      width: 100%;
      text-align: center;
      font-size: 0.68rem;
      letter-spacing: 0.3em;
      color: rgba(255,255,255,0.25);
      text-transform: uppercase;
      pointer-events: none;
      z-index: 10;
    }

    /* ================= RESPONSIVE ================= */
    @media (max-width: 720px) {
      .plate { width: 90vw; height: 240px; padding: 20px; border-radius: 24px; }
      .name { font-size: 2.1rem; }
      .subtitle { font-size: 0.65rem; letter-spacing: 0.22em; }
      .badge { font-size: 0.55rem; padding: 5px 12px; }
      .icon { display: none; }
      .glow-orb { width: 320px; height: 320px; }
    }

    @media (max-width: 420px) {
      .plate { height: 210px; }
      .name { font-size: 1.55rem; }
      .subtitle { font-size: 0.55rem; }
      .badges { gap: 8px; }
      .badge { font-size: 0.5rem; padding: 4px 10px; }
    }
  </style>
</head>
<body>

  <!-- ===== STARFIELD ===== -->
  <div class="stars"></div>

  <!-- ===== SCENE ===== -->
  <div class="scene">

    <!-- Glow orb -->
    <div class="glow-orb"></div>

    <!-- 3D card group -->
    <div class="card-group">
      <div class="float-wrap">

        <!-- Floating tech icons -->
        <div class="icon icon1"></div>
        <div class="icon icon2"></div>
        <div class="icon icon3"></div>
        <div class="icon icon4"></div>
        <div class="icon icon5"></div>
        <div class="icon icon6"></div>

        <!-- Main plate -->
        <div class="plate">
          <div class="name">Parmeshwar Durgist</div>
          <div class="subtitle">Full Stack Developer</div>
          <div class="divider"></div>
          <div class="badges">
            <span class="badge">⚡ Full Stack</span>
            <span class="badge">🐍 Python / JS</span>
            <span class="badge">☁️ Docker / Cloud</span>
          </div>
        </div>

      </div>
    </div>

  </div>

  <!-- ===== FOOTER ===== -->
  <div class="footer-credit">3D Profile · Parmeshwar Durgist</div>

  <!-- ===== CSS PARTICLES ===== -->
  <div style="position:fixed; inset:0; pointer-events:none; z-index:1; overflow:hidden;">
    <div class="particle" style="width:3px; height:3px; top:22%; left:14%; animation-duration:8s;  animation-delay:0s;"></div>
    <div class="particle" style="width:2px; height:2px; top:36%; left:82%; animation-duration:10s; animation-delay:1s;"></div>
    <div class="particle" style="width:4px; height:4px; top:62%; left:9%;  animation-duration:12s; animation-delay:2s;"></div>
    <div class="particle" style="width:2px; height:2px; top:76%; left:87%; animation-duration:9s;  animation-delay:0.5s;"></div>
    <div class="particle" style="width:3px; height:3px; top:46%; left:46%; animation-duration:11s; animation-delay:3s;"></div>
    <div class="particle" style="width:2px; height:2px; top:15%; left:72%; animation-duration:7s;  animation-delay:1.5s;"></div>
    <div class="particle" style="width:3px; height:3px; top:82%; left:30%; animation-duration:13s; animation-delay:2.5s;"></div>
    <div class="particle" style="width:2px; height:2px; top:52%; left:62%; animation-duration:8s;  animation-delay:0.8s;"></div>
    <div class="particle" style="width:4px; height:4px; top:26%; left:24%; animation-duration:14s; animation-delay:4s;"></div>
    <div class="particle" style="width:2px; height:2px; top:70%; left:56%; animation-duration:10s; animation-delay:3.5s;"></div>
  </div>

</body>
</html>

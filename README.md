<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Parmeshwar Durgist · 3D Profile</title>
  <style>
    /* ---------- RESET & BASE ---------- */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      min-height: 100vh;
      background: radial-gradient(circle at 30% 20%, #0b1026, #03040c 80%);
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: 'Inter', 'Segoe UI', system-ui, -apple-system, sans-serif;
      overflow: hidden;
      perspective: 1200px;
    }

    /* ---------- STARFIELD / BACKGROUND DOTS ---------- */
    .stars {
      position: fixed;
      inset: 0;
      background-image:
        radial-gradient(2px 2px at 20px 30px, #ffffff33, transparent),
        radial-gradient(2px 2px at 40px 70px, #00c2ff44, transparent),
        radial-gradient(1px 1px at 90px 40px, #ffffff22, transparent),
        radial-gradient(2px 2px at 160px 120px, #7b68ee33, transparent),
        radial-gradient(1px 1px at 300px 250px, #ffffff44, transparent),
        radial-gradient(2px 2px at 420px 80px, #00c2ff33, transparent),
        radial-gradient(1px 1px at 550px 320px, #ffffff22, transparent),
        radial-gradient(2px 2px at 680px 190px, #7b68ee33, transparent);
      background-size: 800px 400px;
      background-repeat: repeat;
      animation: twinkle 8s ease-in-out infinite alternate;
      pointer-events: none;
    }

    @keyframes twinkle {
      0% { opacity: 0.5; }
      100% { opacity: 1; }
    }

    /* ---------- SCENE WRAPPER ---------- */
    .scene {
      position: relative;
      width: 100%;
      max-width: 1000px;
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      transform-style: preserve-3d;
    }

    /* ---------- 3D CARD GROUP ---------- */
    .card-group {
      position: relative;
      transform-style: preserve-3d;
      animation: floatGroup 6s ease-in-out infinite;
      transform: rotateX(8deg) rotateY(-6deg);
    }

    @keyframes floatGroup {
      0%, 100% { transform: rotateX(8deg) rotateY(-6deg) translateY(0px); }
      50% { transform: rotateX(6deg) rotateY(-2deg) translateY(-12px); }
    }

    /* ---------- MAIN GLASS PLATE ---------- */
    .plate {
      position: relative;
      width: 600px;
      height: 260px;
      background: linear-gradient(145deg, #0e142a, #070a18);
      border-radius: 28px;
      border: 1px solid rgba(0, 194, 255, 0.25);
      box-shadow:
        0 0 0 1px rgba(0, 194, 255, 0.08) inset,
        0 30px 60px -20px rgba(0, 0, 0, 0.9),
        0 0 50px rgba(0, 194, 255, 0.12),
        0 0 100px rgba(123, 104, 238, 0.08);
      transform-style: preserve-3d;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 30px;
      overflow: hidden;
    }

    /* inner glow line */
    .plate::before {
      content: '';
      position: absolute;
      inset: 0;
      border-radius: 28px;
      background: linear-gradient(
        135deg,
        rgba(0, 194, 255, 0.15) 0%,
        transparent 30%,
        transparent 70%,
        rgba(123, 104, 238, 0.15) 100%
      );
      pointer-events: none;
      z-index: 0;
    }

    /* shine sweep */
    .plate::after {
      content: '';
      position: absolute;
      top: -60%;
      left: -60%;
      width: 220%;
      height: 220%;
      background: linear-gradient(
        115deg,
        transparent 30%,
        rgba(255, 255, 255, 0.03) 45%,
        rgba(0, 194, 255, 0.08) 50%,
        rgba(255, 255, 255, 0.03) 55%,
        transparent 70%
      );
      transform: rotate(25deg);
      animation: shine 7s linear infinite;
      pointer-events: none;
      z-index: 1;
    }

    @keyframes shine {
      0% { transform: rotate(25deg) translateX(-30%); }
      100% { transform: rotate(25deg) translateX(30%); }
    }

    /* ---------- NAME ---------- */
    .name {
      position: relative;
      z-index: 3;
      font-size: 3.4rem;
      font-weight: 700;
      letter-spacing: 0.06em;
      text-transform: uppercase;
      background: linear-gradient(135deg, #ffffff 20%, #b0e0ff 60%, #00c2ff 100%);
      -webkit-background-clip: text;
      background-clip: text;
      -webkit-text-fill-color: transparent;
      text-shadow:
        0 0 30px rgba(0, 194, 255, 0.4),
        0 0 80px rgba(0, 194, 255, 0.15);
      transform: translateZ(40px);
      animation: nameGlow 3s ease-in-out infinite alternate;
      line-height: 1.1;
      text-align: center;
    }

    @keyframes nameGlow {
      0% { filter: drop-shadow(0 0 15px rgba(0, 194, 255, 0.3)); }
      100% { filter: drop-shadow(0 0 35px rgba(0, 194, 255, 0.7)); }
    }

    /* ---------- SUBTITLE ---------- */
    .subtitle {
      position: relative;
      z-index: 3;
      margin-top: 12px;
      font-size: 0.95rem;
      font-weight: 400;
      letter-spacing: 0.35em;
      text-transform: uppercase;
      color: #8ab8e0;
      text-shadow: 0 0 20px rgba(0, 194, 255, 0.3);
      transform: translateZ(25px);
    }

    /* ---------- DIVIDER ---------- */
    .divider {
      position: relative;
      z-index: 3;
      width: 70%;
      height: 1px;
      margin: 22px 0 18px;
      background: linear-gradient(90deg, transparent, #00c2ff66, #7b68ee66, transparent);
      transform: translateZ(20px);
    }

    /* ---------- BADGES ---------- */
    .badges {
      position: relative;
      z-index: 3;
      display: flex;
      gap: 14px;
      flex-wrap: wrap;
      justify-content: center;
      transform: translateZ(30px);
    }

    .badge {
      padding: 7px 20px;
      border-radius: 40px;
      font-size: 0.7rem;
      font-weight: 500;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: #d0eaff;
      background: rgba(0, 194, 255, 0.08);
      border: 1px solid rgba(0, 194, 255, 0.35);
      box-shadow:
        0 0 20px rgba(0, 194, 255, 0.12),
        0 0 0 1px rgba(0, 194, 255, 0.05) inset;
      backdrop-filter: blur(6px);
      transition: all 0.3s ease;
      animation: badgeFloat 4s ease-in-out infinite;
    }

    .badge:nth-child(2) { animation-delay: 0.6s; }
    .badge:nth-child(3) { animation-delay: 1.2s; }

    @keyframes badgeFloat {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-4px); }
    }

    .badge:hover {
      background: rgba(0, 194, 255, 0.18);
      border-color: rgba(0, 194, 255, 0.7);
      box-shadow: 0 0 30px rgba(0, 194, 255, 0.3);
      transform: translateY(-3px) scale(1.02);
    }

    /* ---------- FLOATING TECH ICONS (CSS-only) ---------- */
    .icon {
      position: absolute;
      border-radius: 30% 70% 70% 30% / 30% 30% 70% 70%;
      background: radial-gradient(circle at 30% 30%, #00c2ff, #004466);
      box-shadow: 0 0 25px #00c2ff88, 0 0 60px #00c2ff33;
      animation: iconFloat 5s ease-in-out infinite;
      transform-style: preserve-3d;
      z-index: 2;
      opacity: 0.85;
    }

    .icon::after {
      content: '';
      position: absolute;
      inset: 20%;
      border-radius: 50%;
      background: radial-gradient(circle at 40% 40%, #ffffff66, transparent 70%);
    }

    .icon1 {
      width: 38px;
      height: 38px;
      top: 12%;
      left: 6%;
      background: radial-gradient(circle at 30% 30%, #00c2ff, #003355);
      animation-delay: 0s;
    }

    .icon2 {
      width: 26px;
      height: 26px;
      top: 68%;
      left: 3%;
      background: radial-gradient(circle at 30% 30%, #7b68ee, #2a1a5e);
      box-shadow: 0 0 25px #7b68ee88, 0 0 60px #7b68ee33;
      animation-delay: 1.2s;
    }

    .icon3 {
      width: 32px;
      height: 32px;
      top: 18%;
      right: 5%;
      background: radial-gradient(circle at 30% 30%, #ffaa00, #664400);
      box-shadow: 0 0 25px #ffaa0088, 0 0 60px #ffaa0033;
      animation-delay: 0.8s;
    }

    .icon4 {
      width: 22px;
      height: 22px;
      top: 72%;
      right: 4%;
      background: radial-gradient(circle at 30% 30%, #00ffaa, #005544);
      box-shadow: 0 0 25px #00ffaa88, 0 0 60px #00ffaa33;
      animation-delay: 1.8s;
    }

    .icon5 {
      width: 18px;
      height: 18px;
      top: 44%;
      left: 1%;
      background: radial-gradient(circle at 30% 30%, #ff66aa, #661133);
      box-shadow: 0 0 25px #ff66aa88, 0 0 60px #ff66aa33;
      animation-delay: 2.4s;
    }

    .icon6 {
      width: 20px;
      height: 20px;
      top: 48%;
      right: 1%;
      background: radial-gradient(circle at 30% 30%, #00c2ff, #003355);
      animation-delay: 3s;
    }

    @keyframes iconFloat {
      0%, 100% { transform: translateY(0) rotate(0deg) scale(1); }
      50% { transform: translateY(-18px) rotate(12deg) scale(1.08); }
    }

    /* ---------- GLOWING ORB BEHIND CARD ---------- */
    .glow-orb {
      position: absolute;
      width: 450px;
      height: 450px;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(0, 194, 255, 0.12) 0%, transparent 65%);
      filter: blur(30px);
      animation: orbPulse 6s ease-in-out infinite;
      pointer-events: none;
      z-index: 0;
    }

    @keyframes orbPulse {
      0%, 100% { transform: scale(1); opacity: 0.6; }
      50% { transform: scale(1.15); opacity: 1; }
    }

    /* ---------- FLOATING PARTICLES (CSS dots) ---------- */
    .particle {
      position: absolute;
      border-radius: 50%;
      background: white;
      opacity: 0.6;
      animation: particleFloat linear infinite;
      pointer-events: none;
      z-index: 1;
    }

    @keyframes particleFloat {
      0% { transform: translateY(0) translateX(0); opacity: 0; }
      10% { opacity: 0.8; }
      90% { opacity: 0.8; }
      100% { transform: translateY(-120px) translateX(40px); opacity: 0; }
    }

    /* ---------- FOOTER CREDIT (subtle) ---------- */
    .footer-credit {
      position: fixed;
      bottom: 18px;
      left: 0;
      width: 100%;
      text-align: center;
      font-size: 0.7rem;
      letter-spacing: 0.2em;
      color: #ffffff33;
      text-transform: uppercase;
      pointer-events: none;
      z-index: 10;
    }

    /* ---------- RESPONSIVE ---------- */
    @media (max-width: 700px) {
      .plate {
        width: 90vw;
        height: 220px;
        padding: 20px;
        border-radius: 22px;
      }
      .name { font-size: 2rem; }
      .subtitle { font-size: 0.65rem; letter-spacing: 0.2em; }
      .badge { font-size: 0.55rem; padding: 5px 12px; }
      .icon { display: none; }
      .glow-orb { width: 300px; height: 300px; }
    }

    @media (max-width: 420px) {
      .plate { height: 200px; }
      .name { font-size: 1.5rem; }
      .subtitle { font-size: 0.55rem; }
      .badges { gap: 8px; }
      .badge { font-size: 0.5rem; padding: 4px 10px; }
    }
  </style>
</head>
<body>
  <!-- twinkling star field -->
  <div class="stars"></div>

  <!-- main 3D scene -->
  <div class="scene">
    <!-- glow orb behind -->
    <div class="glow-orb"></div>

    <!-- 3D card group -->
    <div class="card-group">

      <!-- floating tech icons (CSS 3D) -->
      <div class="icon icon1"></div>
      <div class="icon icon2"></div>
      <div class="icon icon3"></div>
      <div class="icon icon4"></div>
      <div class="icon icon5"></div>
      <div class="icon icon6"></div>

      <!-- main glass plate -->
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

  <!-- tiny footer -->
  <div class="footer-credit">3D Profile · Parmeshwar Durgist</div>

  <!-- floating particles generated with CSS (inline for no JS) -->
  <div style="position: fixed; inset: 0; pointer-events: none; z-index: 1;">
    <div class="particle" style="width:3px;height:3px;top:20%;left:15%;animation-duration:8s;animation-delay:0s;"></div>
    <div class="particle" style="width:2px;height:2px;top:35%;left:80%;animation-duration:10s;animation-delay:1s;"></div>
    <div class="particle" style="width:4px;height:4px;top:60%;left:10%;animation-duration:12s;animation-delay:2s;"></div>
    <div class="particle" style="width:2px;height:2px;top:75%;left:85%;animation-duration:9s;animation-delay:0.5s;"></div>
    <div class="particle" style="width:3px;height:3px;top:45%;left:45%;animation-duration:11s;animation-delay:3s;"></div>
    <div class="particle" style="width:2px;height:2px;top:15%;left:70%;animation-duration:7s;animation-delay:1.5s;"></div>
    <div class="particle" style="width:3px;height:3px;top:80%;left:30%;animation-duration:13s;animation-delay:2.5s;"></div>
    <div class="particle" style="width:2px;height:2px;top:50%;left:60%;animation-duration:8s;animation-delay:0.8s;"></div>
    <div class="particle" style="width:4px;height:4px;top:25%;left:25%;animation-duration:14s;animation-delay:4s;"></div>
    <div class="particle" style="width:2px;height:2px;top:70%;left:55%;animation-duration:10s;animation-delay:3.5s;"></div>
  </div>
</body>
</html>

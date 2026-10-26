<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>3D Professional Profile – Parmeshwar Durgist</title>
  <style>
    body {
      margin: 0;
      overflow: hidden;
      font-family: 'Inter', 'Segoe UI', system-ui, sans-serif;
      background-color: #050510;
    }
    #info {
      position: absolute;
      top: 20px;
      left: 0;
      width: 100%;
      text-align: center;
      color: white;
      pointer-events: none;
      z-index: 10;
      text-shadow: 0 0 20px rgba(0, 194, 255, 0.5);
    }
    #info h1 {
      font-size: clamp(1.8rem, 8vw, 3.5rem);
      font-weight: 600;
      margin: 0;
      letter-spacing: -0.02em;
      background: linear-gradient(135deg, #ffffff, #00c2ff);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      filter: drop-shadow(0 0 15px rgba(0, 194, 255, 0.4));
    }
    #info p {
      font-size: clamp(0.8rem, 3vw, 1.1rem);
      margin: 8px 0 0;
      color: #b0e0ff;
      letter-spacing: 2px;
      font-weight: 300;
      opacity: 0.9;
    }
    .badge-container {
      position: absolute;
      bottom: 30px;
      left: 0;
      width: 100%;
      display: flex;
      justify-content: center;
      gap: 20px;
      flex-wrap: wrap;
      pointer-events: none;
      z-index: 10;
    }
    .badge {
      background: rgba(0, 194, 255, 0.15);
      backdrop-filter: blur(8px);
      border: 1px solid rgba(0, 194, 255, 0.4);
      color: #b0e0ff;
      padding: 8px 24px;
      border-radius: 40px;
      font-size: 0.9rem;
      letter-spacing: 1px;
      text-transform: uppercase;
      font-weight: 400;
      box-shadow: 0 0 20px rgba(0, 194, 255, 0.2);
      animation: float 3s ease-in-out infinite;
    }
    .badge:nth-child(2) { animation-delay: 0.5s; }
    .badge:nth-child(3) { animation-delay: 1s; }
    @keyframes float {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-5px); }
    }
    .github-corner {
      position: absolute;
      top: 0;
      right: 0;
      z-index: 20;
    }
    @media (max-width: 600px) {
      .badge { font-size: 0.7rem; padding: 6px 16px; }
    }
  </style>
</head>
<body>
  <div id="info">
    <h1>Parmeshwar Durgist</h1>
    <p>FULL STACK DEVELOPER • PROBLEM SOLVER</p>
  </div>

  <div class="badge-container">
    <div class="badge">⚡ Full Stack</div>
    <div class="badge">🐍 Python / JS</div>
    <div class="badge">☁️ Docker / Cloud</div>
  </div>

  <!-- Three.js from CDN -->
  <script type="importmap">
    {
      "imports": {
        "three": "https://unpkg.com/three@0.128.0/build/three.module.js"
      }
    }
  </script>

  <script type="module">
    import * as THREE from 'three';
    import { OrbitControls } from 'https://unpkg.com/three@0.128.0/examples/jsm/controls/OrbitControls.js';

    // --- Setup Scene ---
    const scene = new THREE.Scene();
    scene.background = new THREE.Color(0x050510);
    scene.fog = new THREE.FogExp2(0x050510, 0.002);

    const camera = new THREE.PerspectiveCamera(45, window.innerWidth / window.innerHeight, 0.1, 1000);
    camera.position.set(0, 2, 12);
    camera.lookAt(0, 0, 0);

    const renderer = new THREE.WebGLRenderer({ antialias: true, alpha: false });
    renderer.setSize(window.innerWidth, window.innerHeight);
    renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
    renderer.shadowMap.enabled = true;
    renderer.shadowMap.type = THREE.PCFSoftShadowMap;
    renderer.toneMapping = THREE.ACESFilmicToneMapping;
    renderer.toneMappingExposure = 1.2;
    document.body.appendChild(renderer.domElement);

    // --- Controls (disabled auto-rotate, just drag for interactivity) ---
    const controls = new OrbitControls(camera, renderer.domElement);
    controls.enableDamping = true;
    controls.dampingFactor = 0.05;
    controls.autoRotate = false;
    controls.enableZoom = true;
    controls.zoomSpeed = 0.8;
    controls.enablePan = false;
    controls.target.set(0, 1, 0);
    controls.maxPolarAngle = Math.PI / 2.2;
    controls.minDistance = 5;
    controls.maxDistance = 20;

    // --- Lights ---
    // Ambient base
    const ambient = new THREE.AmbientLight(0x404060);
    scene.add(ambient);

    // Key light (cyan)
    const keyLight = new THREE.PointLight(0x00c2ff, 1.5, 30);
    keyLight.position.set(3, 5, 5);
    scene.add(keyLight);

    // Fill light (warm)
    const fillLight = new THREE.PointLight(0xffaa00, 0.8, 30);
    fillLight.position.set(-4, 2, 4);
    scene.add(fillLight);

    // Back rim light (purple)
    const rimLight = new THREE.PointLight(0x7b68ee, 1.2, 25);
    rimLight.position.set(-2, 1, -6);
    scene.add(rimLight);

    // Additional top light
    const topLight = new THREE.DirectionalLight(0xffffff, 0.6);
    topLight.position.set(0, 10, 0);
    scene.add(topLight);

    // --- Create the central 3D nameplate group ---
    const nameGroup = new THREE.Group();

    // Main plate (rounded rectangle via box geometry)
    const plateWidth = 5.8;
    const plateHeight = 2.2;
    const plateDepth = 0.4;
    const plateGeo = new THREE.BoxGeometry(plateWidth, plateHeight, plateDepth);
    const plateMat = new THREE.MeshStandardMaterial({
      color: 0x111122,
      roughness: 0.25,
      metalness: 0.85,
      emissive: new THREE.Color(0x001122),
      emissiveIntensity: 0.6,
      transparent: true,
      opacity: 0.95
    });
    const plate = new THREE.Mesh(plateGeo, plateMat);
    plate.castShadow = true;
    plate.receiveShadow = true;
    plate.position.y = 1.8;
    nameGroup.add(plate);

    // Add a glowing edge to the plate (using thin boxes)
    const edgeMat = new THREE.MeshStandardMaterial({
      color: 0x00c2ff,
      emissive: new THREE.Color(0x00c2ff),
      emissiveIntensity: 1.2,
      transparent: true,
      opacity: 0.6
    });
    
    // Top edge
    const topEdge = new THREE.Mesh(new THREE.BoxGeometry(plateWidth + 0.1, 0.05, 0.1), edgeMat);
    topEdge.position.set(0, 1.8 + plateHeight/2, 0);
    nameGroup.add(topEdge);
    // Bottom edge
    const bottomEdge = new THREE.Mesh(new THREE.BoxGeometry(plateWidth + 0.1, 0.05, 0.1), edgeMat);
    bottomEdge.position.set(0, 1.8 - plateHeight/2, 0);
    nameGroup.add(bottomEdge);
    // Left edge
    const leftEdge = new THREE.Mesh(new THREE.BoxGeometry(0.05, plateHeight, 0.1), edgeMat);
    leftEdge.position.set(-plateWidth/2, 1.8, 0);
    nameGroup.add(leftEdge);
    // Right edge
    const rightEdge = new THREE.Mesh(new THREE.BoxGeometry(0.05, plateHeight, 0.1), edgeMat);
    rightEdge.position.set(plateWidth/2, 1.8, 0);
    nameGroup.add(rightEdge);

    // --- 3D Text: "PARMESHWAR" ---
    // Since loading font is async, we use simple extruded text via canvas texture on a plane? 
    // But for pure 3D text, we'll use TextGeometry. However, to keep this self-contained and fast, 
    // we'll create a stylized "3D text effect" using multiple planes with canvas textures (simpler and reliable).
    // Actually, let's create a canvas-based texture on a plane that looks like 3D text with bevel.
    // Better: Use a simple extruded shape? That requires font loading.
    // For a professional look without external font, we'll use a canvas texture with 3D shading effect.

    function createTextTexture(text, color = '#ffffff', glowColor = '#00c2ff') {
      const canvas = document.createElement('canvas');
      const ctx = canvas.getContext('2d');
      canvas.width = 1024;
      canvas.height = 256;

      // Background transparent
      ctx.clearRect(0, 0, canvas.width, canvas.height);

      // Text style
      ctx.font = 'bold 120px "Inter", "Segoe UI", "Helvetica Neue", sans-serif';
      ctx.textAlign = 'center';
      ctx.textBaseline = 'middle';

      // Glow
      ctx.shadowColor = glowColor;
      ctx.shadowBlur = 40;
      ctx.shadowOffsetX = 0;
      ctx.shadowOffsetY = 0;

      // Draw multiple passes for glow
      ctx.fillStyle = color;
      ctx.fillText(text, canvas.width/2, canvas.height/2);
      
      ctx.shadowBlur = 20;
      ctx.fillStyle = '#ffffff';
      ctx.fillText(text, canvas.width/2, canvas.height/2);

      // Add a slight gradient overlay for metallic feel
      const gradient = ctx.createLinearGradient(0, 100, 0, 200);
      gradient.addColorStop(0, 'rgba(255,255,255,0.9)');
      gradient.addColorStop(1, 'rgba(200,230,255,0.7)');
      ctx.shadowBlur = 0;
      ctx.fillStyle = gradient;
      ctx.fillText(text, canvas.width/2, canvas.height/2);

      return new THREE.CanvasTexture(canvas);
    }

    // Name texture
    const nameTexture = createTextTexture('PARMESHWAR', '#ffffff', '#00c2ff');
    const nameMat = new THREE.MeshStandardMaterial({
      map: nameTexture,
      transparent: true,
      emissive: new THREE.Color(0x004466),
      emissiveIntensity: 0.8,
      roughness: 0.2,
      metalness: 0.1,
      side: THREE.DoubleSide
    });
    const namePlane = new THREE.Mesh(new THREE.PlaneGeometry(5.2, 1.3), nameMat);
    namePlane.position.set(0, 2.1, plateDepth/2 + 0.05);
    nameGroup.add(namePlane);

    // Title texture
    const titleTexture = createTextTexture('FULL STACK DEVELOPER', '#b0e0ff', '#7b68ee');
    const titleMat = new THREE.MeshStandardMaterial({
      map: titleTexture,
      transparent: true,
      emissive: new THREE.Color(0x221144),
      emissiveIntensity: 0.5,
      roughness: 0.3,
      metalness: 0.2,
      side: THREE.DoubleSide
    });
    const titlePlane = new THREE.Mesh(new THREE.PlaneGeometry(5.0, 0.7), titleMat);
    titlePlane.position.set(0, 1.2, plateDepth/2 + 0.05);
    nameGroup.add(titlePlane);

    // --- Add floating tech icons (small spheres / cubes) around the plate ---
    const iconsGroup = new THREE.Group();
    const iconColors = [0x00c2ff, 0xffaa00, 0x7b68ee, 0x00ffaa, 0xff66aa];
    const iconPositions = [
      { x: -3.2, y: 2.5, z: 1.5, color: 0x00c2ff, size: 0.25 },
      { x: 3.4, y: 2.0, z: 1.2, color: 0xffaa00, size: 0.2 },
      { x: -2.8, y: 0.8, z: 1.8, color: 0x7b68ee, size: 0.3 },
      { x: 3.0, y: 1.0, z: 1.6, color: 0x00ffaa, size: 0.22 },
      { x: -1.5, y: 3.2, z: 0.8, color: 0xff66aa, size: 0.18 },
      { x: 2.0, y: 3.5, z: 0.5, color: 0x00c2ff, size: 0.2 },
      { x: 0.5, y: 0.2, z: 2.2, color: 0xffaa00, size: 0.28 },
      { x: -0.8, y: 2.8, z: 2.0, color: 0x7b68ee, size: 0.22 },
    ];

    iconPositions.forEach(pos => {
      const geo = new THREE.IcosahedronGeometry(pos.size, 1);
      const mat = new THREE.MeshStandardMaterial({
        color: pos.color,
        emissive: pos.color,
        emissiveIntensity: 0.6,
        roughness: 0.2,
        metalness: 0.7,
        transparent: true,
        opacity: 0.9
      });
      const icon = new THREE.Mesh(geo, mat);
      icon.position.set(pos.x, pos.y, pos.z);
      icon.castShadow = true;
      icon.receiveShadow = true;
      iconsGroup.add(icon);
    });

    // Add small rings around some icons for extra flair
    const ringMat = new THREE.MeshStandardMaterial({
      color: 0x00c2ff,
      emissive: new THREE.Color(0x00c2ff),
      emissiveIntensity: 0.8,
      transparent: true,
      opacity: 0.3,
      side: THREE.DoubleSide
    });
    const ring1 = new THREE.Mesh(new THREE.TorusGeometry(0.45, 0.02, 16, 64), ringMat);
    ring1.position.set(-3.2, 2.5, 1.5);
    ring1.rotation.x = Math.PI / 2;
    ring1.rotation.z = 0.5;
    iconsGroup.add(ring1);

    const ring2 = new THREE.Mesh(new THREE.TorusGeometry(0.4, 0.02, 16, 64), ringMat);
    ring2.position.set(3.0, 1.0, 1.6);
    ring2.rotation.x = Math.PI / 3;
    ring2.rotation.y = 0.8;
    iconsGroup.add(ring2);

    nameGroup.add(iconsGroup);

    // --- Add a subtle base / platform beneath the plate ---
    const baseGeo = new THREE.CylinderGeometry(3.5, 3.5, 0.2, 64);
    const baseMat = new THREE.MeshStandardMaterial({
      color: 0x0a0a20,
      roughness: 0.4,
      metalness: 0.9,
      emissive: new THREE.Color(0x001122),
      emissiveIntensity: 0.3
    });
    const base = new THREE.Mesh(baseGeo, baseMat);
    base.position.set(0, -0.2, 0);
    base.receiveShadow = true;
    base.castShadow = true;
    nameGroup.add(base);

    // Add glowing ring on base
    const baseRingGeo = new THREE.TorusGeometry(3.2, 0.03, 16, 100);
    const baseRingMat = new THREE.MeshStandardMaterial({
      color: 0x00c2ff,
      emissive: new THREE.Color(0x00c2ff),
      emissiveIntensity: 1.5,
      transparent: true,
      opacity: 0.5
    });
    const baseRing = new THREE.Mesh(baseRingGeo, baseRingMat);
    baseRing.rotation.x = Math.PI / 2;
    baseRing.position.set(0, 0, 0);
    nameGroup.add(baseRing);

    // --- Position the entire group ---
    nameGroup.position.y = 0.5;
    nameGroup.position.z = 0;
    scene.add(nameGroup);

    // --- Add floating particles for atmosphere ---
    const particlesGeo = new THREE.BufferGeometry();
    const particlesCount = 1200;
    const positions = new Float32Array(particlesCount * 3);
    const colors = new Float32Array(particlesCount * 3);

    for (let i = 0; i < particlesCount; i++) {
      // Spread particles in a large sphere
      const radius = 15 + Math.random() * 20;
      const theta = Math.random() * Math.PI * 2;
      const phi = Math.acos((Math.random() * 2) - 1);
      
      const x = radius * Math.sin(phi) * Math.cos(theta);
      const y = radius * Math.sin(phi) * Math.sin(theta) * 0.5; // flatten vertically
      const z = radius * Math.cos(phi);
      
      positions[i*3] = x;
      positions[i*3+1] = y * 0.8 + 2;
      positions[i*3+2] = z;
      
      // Colors: cyan, purple, white, blue
      const colorChoice = Math.random();
      let r, g, b;
      if (colorChoice < 0.4) {
        r = 0.0; g = 0.76; b = 1.0; // cyan
      } else if (colorChoice < 0.7) {
        r = 0.48; g = 0.41; b = 0.93; // purple
      } else {
        r = 0.9; g = 0.9; b = 1.0; // white/blue
      }
      // Add some randomness
      colors[i*3] = r * (0.6 + Math.random() * 0.4);
      colors[i*3+1] = g * (0.6 + Math.random() * 0.4);
      colors[i*3+2] = b * (0.6 + Math.random() * 0.4);
    }

    particlesGeo.setAttribute('position', new THREE.BufferAttribute(positions, 3));
    particlesGeo.setAttribute('color', new THREE.BufferAttribute(colors, 3));

    const particlesMat = new THREE.PointsMaterial({
      size: 0.15,
      vertexColors: true,
      transparent: true,
      opacity: 0.8,
      blending: THREE.AdditiveBlending,
      depthWrite: false
    });

    const particles = new THREE.Points(particlesGeo, particlesMat);
    scene.add(particles);

    // --- Add a second layer of tiny stars ---
    const starsGeo = new THREE.BufferGeometry();
    const starsCount = 2000;
    const starPositions = new Float32Array(starsCount * 3);
    for (let i = 0; i < starsCount; i++) {
      starPositions[i*3] = (Math.random() - 0.5) * 200;
      starPositions[i*3+1] = (Math.random() - 0.5) * 100;
      starPositions[i*3+2] = (Math.random() - 0.5) * 200 - 50;
    }
    starsGeo.setAttribute('position', new THREE.BufferAttribute(starPositions, 3));
    const starsMat = new THREE.PointsMaterial({
      color: 0xffffff,
      size: 0.08,
      transparent: true,
      opacity: 0.6,
      blending: THREE.AdditiveBlending,
      depthWrite: false
    });
    const stars = new THREE.Points(starsGeo, starsMat);
    scene.add(stars);

    // --- Animation Loop ---
    let clock = new THREE.Clock();

    function animate() {
      const delta = clock.getDelta();
      const elapsedTime = performance.now() * 0.001; // seconds

      // Rotate the name group slowly
      nameGroup.rotation.y = Math.sin(elapsedTime * 0.15) * 0.1;
      nameGroup.rotation.x = Math.sin(elapsedTime * 0.2) * 0.03;

      // Animate icons (bobbing and rotation)
      iconsGroup.children.forEach((child, index) => {
        if (child.isMesh) {
          child.rotation.x += 0.005;
          child.rotation.y += 0.008;
          // Bobbing motion
          const baseY = iconPositions[index]?.y || 2.0;
          child.position.y = baseY + Math.sin(elapsedTime * 1.5 + index) * 0.15;
        }
      });

      // Rotate base ring
      baseRing.rotation.z += 0.002;

      // Rotate particles slowly
      particles.rotation.y += 0.0002;
      stars.rotation.y += 0.0001;

      // Camera subtle movement if not interacting
      if (!controls.enabled) {
        // do nothing
      }

      controls.update();
      renderer.render(scene, camera);
      requestAnimationFrame(animate);
    }

    animate();

    // --- Handle window resize ---
    window.addEventListener('resize', onWindowResize, false);
    function onWindowResize() {
      camera.aspect = window.innerWidth / window.innerHeight;
      camera.updateProjectionMatrix();
      renderer.setSize(window.innerWidth, window.innerHeight);
    }

    // --- Simple intro fade? Not needed, but could add CSS ---
    console.log('3D Profile Loaded – Parmeshwar Durgist');
  </script>
</body>
</html>

<!doctype html>
<html lang="en" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Happy Valentine's Love 💕</title>
  <script src="https://cdn.tailwindcss.com/3.4.17"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;1,400;1,600&amp;family=Quicksand:wght@300;400;500;600&amp;display=swap" rel="stylesheet">
  <style>
html, body {
  height: 100%;
  margin: 0;
  padding: 0;
  overflow: hidden;
}

:root {
  --bg-color: #fff0f3;
  --surface-color: #ffffff;
  --text-color: #8b4a5e;
  --primary-action: #e8839b;
  --secondary-action: #f4b8c8;
  --accent-color: #e6778f;
}

* {
  box-sizing: border-box;
}

body {
  background: var(--bg-color);
  color: var(--text-color);
  font-family: 'Quicksand', sans-serif;
}

.app-wrapper {
  position: relative;
  width: 100%;
  height: 100%;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Pages */
.page {
  position: absolute;
  inset: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.8s ease, transform 0.8s ease;
  transform: translateY(40px) scale(0.95);
  overflow-y: auto;
  padding: 20px;
  z-index: 10;
}

.page.active {
  opacity: 1;
  pointer-events: all;
  transform: translateY(0) scale(1);
}

/* Floating hearts background */
@keyframes floatHeart {
  0% {
    transform: translateY(0) rotate(0deg) scale(0.8);
    opacity: 0.5;
  }
  50% {
    opacity: 0.9;
  }
  100% {
    transform: translateY(-120%) rotate(25deg) scale(1.1);
    opacity: 0;
  }
}

.floating-hearts {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 1;
  overflow: hidden;
}

.floating-heart {
  position: absolute;
  animation: floatHeart linear infinite;
  font-size: 18px;
  color: var(--secondary-action);
}

/* Dudu emoji */
@keyframes gentleFloat {
  0%, 100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-8px);
  }
}

.dudugif {
  font-size: 64px;
  display: inline-block;
  height: 150px;
  width: 150px;
  border: 2px solid lightpink;
}

/* Page 1: Password */
#page1-content {
  text-align: center;
  max-width: 340px;
  z-index: 20;
}

.greeting-title {
  font-family: 'Cormorant Garamond', serif;
  font-size: 32px;
  font-weight: 600;
  margin: 0 0 10px;
  font-style: italic;
}

.subtitle {
  font-size: 14px;
  opacity: 0.7;
  margin-bottom: 32px;
}

/* PIN display */
#pin-display {
  display: flex;
  gap: 14px;
  justify-content: center;
  margin-bottom: 28px;
}

.pin-dot {
  width: 14px;
  height: 14px;
  border-radius: 50%;
  background: var(--secondary-action);
  transition: all 0.3s ease;
}

.pin-dot.filled {
  background: var(--primary-action);
  transform: scale(1.3);
  box-shadow: 0 0 12px rgba(232, 131, 155, 0.5);
}

/* Number pad */
.number-pad {
  display: grid;
  grid-template-columns: repeat(3, 60px);
  gap: 12px;
  justify-content: center;
  margin-bottom: 20px;
}

.pin-btn {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  background: var(--surface-color);
  color: var(--text-color);
  border: 2px solid var(--secondary-action);
  font-family: 'Quicksand', sans-serif;
  font-size: 20px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.25s ease;
  user-select: none;
  display: flex;
  align-items: center;
  justify-content: center;
}

.pin-btn:hover {
  background: var(--secondary-action);
  color: #fff;
  transform: scale(1.08);
}

.pin-btn:active {
  transform: scale(0.95);
}

/* Error message */
.pin-error {
  font-size: 12px;
  color: #e05577;
  height: 16px;
  opacity: 0;
  transition: opacity 0.3s ease;
  margin-bottom: 10px;
}

.pin-error.show {
  opacity: 1;
}

@keyframes shake {
  0%, 100% { transform: translateX(0); }
  20% { transform: translateX(-8px); }
  40% { transform: translateX(8px); }
  60% { transform: translateX(-6px); }
  80% { transform: translateX(6px); }
}

.shake {
  animation: shake 0.4s ease;
}

/* Page 2: Rose & Letter */
.rose-container {
  position: relative;
  width: 200px;
  height: 280px;
  margin-bottom: 20px;
  z-index: 20;
}

/* Rose stem */
@keyframes growStem {
  0% { height: 0; }
  100% { height: 160px; }
}

.rose-stem {
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 4px;
  background: linear-gradient(to top, #6a9e5c, #8bc078);
  border-radius: 2px;
  height: 0;
  animation: growStem 1.5s ease-out forwards;
}

/* Rose petals */
@keyframes bloomPetal {
  0% {
    transform: scale(0) rotate(0deg);
    opacity: 0;
  }
  60% {
    opacity: 1;
  }
  100% {
    transform: scale(1) rotate(var(--rot));
    opacity: 1;
  }
}

.rose-petal {
  position: absolute;
  border-radius: 50% 50% 50% 0;
  animation: bloomPetal 0.8s ease-out forwards;
  opacity: 0;
}
/* Rose leaves */
@keyframes leafGrow {
  0% {
    transform: scale(0) rotate(var(--leaf-rot));
    opacity: 0;
  }
  100% {
    transform: scale(1) rotate(var(--leaf-rot));
    opacity: 1;
  }
}

.rose-leaf {
  position: absolute;
  width: 28px;
  height: 16px;
  background: #7ab86a;
  border-radius: 0 80% 0 80%;
  opacity: 0;
  animation: leafGrow 0.6s ease-out forwards;
  transform-origin: left center;
}

/* Envelope animation */
@keyframes envelopePop {
  0% {
    transform: scale(0) rotate(-5deg);
    opacity: 0;
  }
  60% {
    transform: scale(1.05) rotate(1deg);
    opacity: 1;
  }
  100% {
    transform: scale(1) rotate(0deg);
    opacity: 1;
  }
}

.envelope-wrapper {
  opacity: 0;
  display: none;
  animation: envelopePop 0.7s ease-out forwards;
  z-index: 20;
}

.envelope-wrapper.show {
  display: block;
}

.envelope-hint {
  font-size: 13px;
  opacity: 0.6;
  margin-bottom: 10px;
  text-align: center;
}

.envelope {
  width: 220px;
  height: 150px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.envelope:hover {
  transform: scale(1.04);
}

/* Letter overlay */
.letter-overlay {
  position: fixed;
  inset: 0;
  background: rgba(139, 74, 94, 0.3);
  backdrop-filter: blur(4px);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.5s ease;
  z-index: 100;
  padding: 20px;
}

.letter-overlay.open {
  opacity: 1;
  pointer-events: all;
}

.letter-paper {
  background: #fffaf5;
  border-radius: 10px;
  max-width: 380px;
  width: 100%;
  max-height: 70%;
  overflow-y: auto;
  padding: 30px 26px;
  box-shadow: 0 20px 60px rgba(139, 74, 94, 0.2);
  transform: translateY(40px) scale(0.9);
  transition: transform 0.5s ease;
  color: var(--text-color);
}

.letter-overlay.open .letter-paper {
  transform: translateY(0) scale(1);
}

.letter-paper::-webkit-scrollbar {
  width: 4px;
}

.letter-paper::-webkit-scrollbar-thumb {
  background: var(--secondary-action);
  border-radius: 4px;
}

.letter-header {
  text-align: center;
  margin-bottom: 16px;
  font-size: 24px;
}

.letter-title {
  font-family: 'Cormorant Garamond', serif;
  font-size: 22px;
  font-weight: 600;
  text-align: center;
  margin: 0 0 18px;
}

.letter-body {
  font-size: 14px;
  line-height: 1.8;
  white-space: pre-wrap;
  word-wrap: break-word;
}

.letter-signature {
  text-align: right;
  margin-top: 18px;
  font-family: 'Cormorant Garamond', serif;
  font-style: italic;
  font-size: 15px;
  white-space: pre-wrap;
}

.continue-btn {
  background: var(--primary-action);
  color: #fff;
  border: none;
  padding: 12px 32px;
  border-radius: 30px;
  font-family: 'Quicksand', sans-serif;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  width: 100%;
  margin-top: 24px;
  text-align: center;
}

.continue-btn:hover {
  background: var(--accent-color);
  transform: scale(1.05);
}

.continue-btn:active {
  transform: scale(0.98);
}

/* Page 3: Gallery */
.gallery-container {
  max-width: 400px;
  width: 100%;
  text-align: center;
  z-index: 20;
  padding-bottom: 30px;
}

.gallery-header {
  margin-bottom: 20px;
}

.gallery-icon {
  font-size: 36px;
  margin-bottom: 8px;
  display: inline-block;
  animation: gentleFloat 3s ease-in-out infinite;
}

.gallery-title {
  font-family: 'Cormorant Garamond', serif;
  font-size: 26px;
  font-weight: 600;
  margin: 0;
}
/* Photo grid */
.photo-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 14px;
  margin-bottom: 24px;
}

.photo-frame {
  background: var(--surface-color);
  border-radius: 10px;
  padding: 10px;
  box-shadow: 0 4px 20px rgba(139, 74, 94, 0.12);
  transition: all 0.3s ease;
  overflow: hidden;
}

.photo-frame:hover {
  transform: scale(1.03) rotate(-1deg);
  box-shadow: 0 8px 28px rgba(139, 74, 94, 0.18);
}

.photo-placeholder {
  width: 100%;
  aspect-ratio: 1;
  background: linear-gradient(135deg, var(--secondary-action), var(--bg-color));
  border-radius: 6px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 40px;
}

.photo-label {
  font-size: 11px;
  margin: 8px 0 2px;
  opacity: 0.6;
}

/* Decorative hearts */
.heart-divider {
  display: flex;
  justify-content: center;
  gap: 8px;
  margin: 20px 0;
  font-size: 18px;
  opacity: 0.5;
}

/* Music section */
.music-container {
  background: var(--surface-color);
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 20px rgba(139, 74, 94, 0.1);
  padding: 14px;
  margin: 0 auto 20px;
}

.music-title {
  font-size: 12px;
  opacity: 0.6;
  margin: 0 0 10px;
}

.music-placeholder {
  width: 100%;
  aspect-ratio: 16/9;
  background: linear-gradient(135deg, var(--secondary-action), var(--bg-color));
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 40px;
}

.music-note {
  font-size: 12px;
  opacity: 0.5;
  margin-top: 10px;
}

/* Final message */
.final-message {
  font-family: 'Cormorant Garamond', serif;
  font-style: italic;
  font-size: 16px;
  opacity: 0.7;
  margin-bottom: 10px;
}

/* Decorative dudus */
.dudu-decoration {
  display: flex;
  justify-content: center;
  gap: 16px;
  font-size: 24px;
  margin-top: 10px;
}

.dudu-item {
  animation: gentleFloat 3s ease-in-out infinite;
}

.dudu-item:nth-child(2) {
  animation-delay: 0.5s;
}

.dudu-item:nth-child(3) {
  animation-delay: 1s;
}
.pic { 
  height: 85%;
  width: 85%;
}
</style>
  <style>body { box-sizing: border-box; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
<body>
  <div class="floating-hearts" id="floating-hearts"></div>
  <div class="app-wrapper"><!-- PAGE 1: PASSWORD ENTRY -->
   <section id="page1" class="page active">
    <div id="page1-content">
     <div class="dudu">
      <img src="dudufirst.gif" alt="" class="dudugif"/>
     </div>
     <h1 class="greeting-title" id="greeting-msg">Happy Valentine's love</h1>
     <p class="subtitle">Enter Our monthsary</p><!-- PIN Display -->
     <div id="pin-display"></div>
     <div class="pin-error" id="pin-error">
      ❌ Wrong code, try again
     </div><!-- Number Pad -->
     <div class="number-pad" id="number-pad"></div>
    </div>
   </section><!-- PAGE 2: ROSE & LETTER -->
   <section id="page2" class="page">
     <div class="dudu">
       <img src="dudu2nd.gif" alt="" class="dudugif"/>
     </div>
    <div class="rose-container" id="rose-scene"></div>
    <div class="envelope-wrapper" id="envelope-wrapper">
     <p class="envelope-hint">Tap to open 💌</p>
     <svg class="envelope" id="envelope-btn" viewbox="0 0 220 150" role="button" tabindex="0" aria-label="Open love letter"><rect x="2" y="2" width="216" height="146" rx="8" fill="#fff" stroke="#f4b8c8" stroke-width="2" /> <polygon points="2,2 110,80 218,2" fill="#fce4ec" stroke="#f4b8c8" stroke-width="1.5" /> <polygon points="2,148 80,90 110,110 140,90 218,148" fill="#fff5f7" stroke="#f4b8c8" stroke-width="1" /> <text x="110" y="105" text-anchor="middle" font-family="Cormorant Garamond,serif" font-size="14" fill="#e8839b" font-style="italic">
       For You
      </text>
     </svg>
    </div>
   </section><!-- LETTER OVERLAY -->
   <div class="letter-overlay" id="letter-overlay">
    <div class="letter-paper" role="dialog" aria-label="Love letter">
     <div class="letter-header">
      💌
     </div>
     <h2 class="letter-title" id="letter-title">My Dearest Love</h2>
     <div class="letter-body" id="letter-body">
      Every moment with you is precious. You fill my life with joy, love, and warmth. Thank you for being my person, my love, and my everything. Forever yours.
     </div>
     <div class="letter-signature" id="letter-signature">
      Love always,<br>
      Your future husband ❤
     </div><button class="continue-btn" id="continue-btn">Continue →</button>
    </div>
   </div><!-- PAGE 3: GALLERY -->
   <section id="page3" class="page">
    <div class="gallery-container">
     <div class="gallery-header">
      <div class="gallery-icon">
       <div class="dudu">
         <img src="dugif.gif" alt="" class="dudugif">
       </div>
      </div>
      <h2 class="gallery-title" id="gallery-title">Our Beautiful Memories</h2>
     </div><!-- Photo Grid -->
     <div class="photo-grid">
      <div class="photo-frame">
       <div class="photo-placeholder">
        <img src="1.jpg" alt="" class="pic"/>
       </div>
       <p class="photo-label">Photo 1</p>
      </div>
      <div class="photo-frame">
       <div class="photo-placeholder">
         <img src="2.jpg" alt="" class="pic"/>
       </div>
       <p class="photo-label">Photo 2</p>
      </div>
      <div class="photo-frame">
       <div class="photo-placeholder">
        <img src="3.jpg" alt="" class="pic"/>
       </div>
       <p class="photo-label">Photo 3</p>
      </div>
      <div class="photo-frame">
       <div class="photo-placeholder">
        <img src="beach.jpg" alt="" class="pic" />
       </div>
       <p class="photo-label">Photo 4</p>
      </div>
     </div><!-- Heart Divider -->
     <div class="heart-divider"><span>♡</span><span>♡</span><span>♡</span><span>♡</span><span>♡</span>
     </div><!-- Music Section -->
     <div class="music-container">
      <p class="music-title">🎵 Our Song 🎵</p>
      <div class="music-placeholder">
       🎶
      </div>
      <p class="music-note">Add your favorite song here</p>
     </div><!-- Final Message -->
     <div class="final-message">
      "I'm always here for you" 💕
     </div><!-- Decorative Dudus -->
       <div class="dudu">
         <img src="dukiss.gif" alt="" class="dudugif"/>
       </div>
    </div>
   </section>
  </div>
<script>
(function() {
  const PASSWORD = "1221";
  let enteredPin = "";
  let currentPage = 1;

  const defaultConfig = {
    greeting_message: "Happy Valentine's love",
    letter_title: "My Dearest Love",
    letter_message: "Happy Valentine's Day, Love.\n\nHi love, I just want to take this moment to tell you something. Thank you for choosing me and for being patient with me. I know you get tired sometimes because of the things I do and because I can be childish sometimes.\n\nThank you for still staying even during our boring days and for always understanding me. I will do my best to keep and protect this relationship.\nI love you for who you are as a woman. Maybe you didn't completely meet my ideal woman I once imagined, but I'm thankful that I met you and that we became \"us.\" I love everything about you, your looks, your actions, and the way you think. I know we both have insecurities, and I accept yours completely.\n\nJust because you get mad sometimes doesn't mean I'll give up. I understand that in a relationship, disagreements and irritation are normal, especially with our situation. But one day, this distance will be gone, and we'll be together without worrying about time. I'll do everything I can to keep this relationship strong so we can reach that day.\n\nI love you so much.\n\nWhen I first saw you, I was really interested in you. Thank you for those little glances and small things you did that gave me the reason to take a first move for you. January 16, 2025 our first conversation. I courted you for almost a year before we finally became official, and I'm so thankful that you said yes to me.\n\nNong umuwi ako sa probinsya and I saw you, I was happy. I was so excited to hug you, but I still nervous. The gift I was supposed to give you the next day for your birthday, ay nabigay ko nalang dahil sa excitement nong makita ka. That day was so special, especially our night walks and of course, our first kiss, something ang sarap alalahanin ng mga bagay na yon.\n\nMaybe both of us didn't completely meet each other's standards for a partner. I know I'm not a perfect boyfriend for you. I don't always do the things you want or your interests. But I will give everything I have to understand you and choose you every single day, just to keep what we have.\n\nThere's no certainty about what the future holds, but I will support your dreams. I'll stay right here beside you, even on heavy days. I will continue to understand you for as long as I can.\n\nI love you sooo muchhh, and I miss youuu.\n\nI'm always by your side. ❤️",
    letter_signature: "Love always,\nYour future husband ❤️",
    gallery_title: "Our Beautiful Memories"
  };

  // Create floating hearts background
  function createFloatingHearts() {
    const container = document.getElementById('floating-hearts');
    const hearts = ['♡', '❤', '💕', '♥'];
    for (let i = 0; i < 15; i++) {
      const heart = document.createElement('span');
      heart.className = 'floating-heart';
      heart.textContent = hearts[Math.floor(Math.random() * hearts.length)];
      heart.style.left = Math.random() * 100 + '%';
      heart.style.top = (60 + Math.random() * 40) + '%';
      heart.style.animationDuration = (6 + Math.random() * 8) + 's';
      heart.style.animationDelay = Math.random() * 10 + 's';
      heart.style.fontSize = (12 + Math.random() * 14) + 'px';
      container.appendChild(heart);
    }
  }
  createFloatingHearts();

  // Initialize PIN pad
  function initPinPad() {
    const pad = document.getElementById('number-pad');
    const display = document.getElementById('pin-display');

    // Create display dots
    for (let i = 0; i < 4; i++) {
      const dot = document.createElement('div');
      dot.className = 'pin-dot';
      display.appendChild(dot);
    }

    // Create number buttons
    for (let i = 1; i <= 9; i++) {
      const btn = document.createElement('button');
      btn.className = 'pin-btn';
      btn.textContent = i;
      btn.addEventListener('click', () => enterPin(i.toString()));
      pad.appendChild(btn);
    }

    // Empty cell
    pad.appendChild(document.createElement('div'));

    // 0 button
    const btn0 = document.createElement('button');
    btn0.className = 'pin-btn';
    btn0.textContent = '0';
    btn0.addEventListener('click', () => enterPin('0'));
    pad.appendChild(btn0);

    // Delete button
    const delBtn = document.createElement('button');
    delBtn.className = 'pin-btn';
    delBtn.textContent = '⌫';
    delBtn.addEventListener('click', deletePin);
    pad.appendChild(delBtn);
  }

  function enterPin(num) {
    if (enteredPin.length < 4) {
      enteredPin += num;
      updatePinDisplay();
      if (enteredPin.length === 4) {
        setTimeout(checkPin, 300);
      }
    }
  }

  function deletePin() {
    enteredPin = enteredPin.slice(0, -1);
    updatePinDisplay();
    document.getElementById('pin-error').classList.remove('show');
  }

  function updatePinDisplay() {
    const dots = document.qu
// Rose animation
  function startRoseAnimation() {
    const scene = document.getElementById('rose-scene');
    scene.innerHTML = '';

    // Stem
    const stem = document.createElement('div');
    stem.className = 'rose-stem';
    scene.appendChild(stem);

    // Leaves
    setTimeout(() => {
      const leaf1 = document.createElement('div');
      leaf1.className = 'rose-leaf';
      leaf1.style.cssText = 'bottom:50px; left:calc(50% + 2px); --leaf-rot:-30deg;';
      scene.appendChild(leaf1);

      const leaf2 = document.createElement('div');
      leaf2.className = 'rose-leaf';
      leaf2.style.cssText = 'bottom:90px; right:calc(50% + 2px); --leaf-rot:210deg; transform-origin:right center;';
      leaf2.style.animationDelay = '0.2s';
      scene.appendChild(leaf2);
    }, 1000);

    // Petals
    const petalColors = ['#e8839b', '#f4b8c8', '#e88da3', '#f0a0b5', '#d9708a', '#f5c2d0', '#e6778f', '#eea5b8'];
    const petalData = [
      { rot: '0deg', x: 0, y: -14, w: 28, h: 32 },
      { rot: '45deg', x: 12, y: -8, w: 26, h: 30 },
      { rot: '90deg', x: 16, y: 4, w: 24, h: 28 },
      { rot: '135deg', x: 10, y: 14, w: 26, h: 30 },
      { rot: '180deg', x: -2, y: 16, w: 28, h: 32 },
      { rot: '225deg', x: -14, y: 10, w: 26, h: 30 },
      { rot: '270deg', x: -18, y: -2, w: 24, h: 28 },
      { rot: '315deg', x: -12, y: -12, w: 26, h: 30 }
    ];

    setTimeout(() => {
      const centerX = 100;
      const centerY = 80;
      petalData.forEach((p, i) => {
        const petal = document.createElement('div');
        petal.className = 'rose-petal';
        petal.style.left = (centerX + p.x - p.w / 2) + 'px';
        petal.style.top = (centerY + p.y - p.h / 2) + 'px';
        petal.style.width = p.w + 'px';
        petal.style.height = p.h + 'px';
        petal.style.background = petalColors[i];
        petal.style.setProperty('--rot', p.rot);
        petal.style.animationDelay = (1.6 + i * 0.12) + 's';
        scene.appendChild(petal);
      });

      // Rose center
      setTimeout(() => {
        const center = document.createElement('div');
        center.style.cssText = `
          position:absolute; left:${centerX - 10}px; top:${centerY - 6}px;
          width:20px; height:20px; border-radius:50%;
          background:radial-gradient(circle, #d9607a, #c44d6a);
          opacity:0; transition: opacity 0.5s ease;
        `;
        scene.appendChild(center);
        setTimeout(() => { center.style.opacity = '1'; }, 100);
      }, 2800);
    }, 1500);

    // Show envelope after rose blooms
    setTimeout(() => {
      const envelope = document.getElementById('envelope-wrapper');
      envelope.classList.add('show');
    }, 3600);
  }

  // Envelope interaction
  const envelopeBtn = document.getElementById('envelope-btn');
  envelopeBtn.addEventListener('click', () => {
    document.getElementById('letter-overlay').classList.add('open');
  });
  envelopeBtn.addEventListener('keydown', (e) => {
    if (e.key === 'Enter' || e.key === ' ') {
      e.preventDefault();
      document.getElementById('letter-overlay').classList.add('open');
    }
  });

  // Close letter overlay
  document.getElementById('letter-overlay').addEventListener('click', (e) => {
    if (e.target === e.currentTarget) {
      document.getElementById('letter-overlay').classList.remove('open');
    }
  });

  // Continue button
  document.getElementById('continue-btn').addEventListener('click', () => {
    document.getElementById('letter-overlay').classList.remove('open');
    setTimeout(() => goToPage(3), 400);
  });

  // Apply configuration
  function applyConfig(config) {
    const cfg = config || defaultConfig;

    document.getElementById('greeting-msg').textContent = cfg.greeting_message || defaultConfig.greeting_message;
    document.getElementById('letter-title').textContent = cfg.letter_title || defaultConfig.letter_title;
    document.getElementById('letter-body').textContent = cfg.letter_message || defaultConfig.letter_message;
    document.getElementById('letter-signature').innerHTML = (cfg.letter_signature || defaultConfig.letter_signature).replace(/\n/g, '<br>');
    document.getElementById('gallery-title').textContent = cfg.gallery_title || defaultConfig.gallery_title;
  }

  // Element SDK
  if (window.elementSdk) {
    window.elementSdk.init({
      defaultConfig: defaultConfig,
      onConfigChange: async (config) => {
        applyConfig(config);
      },
      mapToCapabilities: (config) => ({
        recolorables: [],
        borderables: [],
        fontEditable: undefined,
        fontSizeable: undefined
      }),
      mapToEditPanelValues: (config) => new Map([
        ["greeting_message", config.greeting_message || defaultConfig.greeting_message],
        ["letter_title", config.letter_title || defaultConfig.letter_title],
        ["letter_message", config.letter_message || defaultConfig.letter_message],
        ["letter_signature", config.letter_signature || defaultConfig.letter_signature],
        [
<!DOCTYPE html>
<html>
<head>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=JetBrains+Mono:wght@300;400;700&family=Rajdhani:wght@300;400;600;700&display=swap');

  :root {
    --neon-cyan: #00f5ff;
    --neon-pink: #ff006e;
    --neon-green: #39ff14;
    --neon-purple: #bf00ff;
    --neon-orange: #ff6b00;
    --dark: #030712;
    --dark2: #0a0f1e;
    --dark3: #0d1529;
    --glass: rgba(0, 245, 255, 0.05);
    --glass-border: rgba(0, 245, 255, 0.15);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--dark);
    color: #e0f7ff;
    font-family: 'JetBrains Mono', monospace;
    overflow-x: hidden;
    min-height: 100vh;
  }

  /* Animated grid background */
  .grid-bg {
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,245,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,245,255,0.03) 1px, transparent 1px);
    background-size: 50px 50px;
    animation: gridPulse 8s ease-in-out infinite;
    z-index: 0;
  }

  @keyframes gridPulse {
    0%,100% { opacity: 0.5; }
    50% { opacity: 1; }
  }

  /* Floating orbs */
  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(80px);
    animation: orbFloat 15s ease-in-out infinite;
    z-index: 0;
    pointer-events: none;
  }
  .orb1 { width: 400px; height: 400px; background: rgba(0,245,255,0.08); top: -100px; left: -100px; animation-delay: 0s; }
  .orb2 { width: 350px; height: 350px; background: rgba(255,0,110,0.08); bottom: -50px; right: -50px; animation-delay: -5s; }
  .orb3 { width: 250px; height: 250px; background: rgba(191,0,255,0.06); top: 50%; left: 50%; animation-delay: -10s; }

  @keyframes orbFloat {
    0%,100% { transform: translate(0,0) scale(1); }
    33% { transform: translate(30px,-30px) scale(1.1); }
    66% { transform: translate(-20px,20px) scale(0.9); }
  }

  .wrapper {
    position: relative;
    z-index: 1;
    max-width: 900px;
    margin: 0 auto;
    padding: 20px;
  }

  /* === HEADER === */
  .header {
    text-align: center;
    padding: 40px 0 30px;
    animation: fadeSlideDown 1s ease forwards;
  }

  @keyframes fadeSlideDown {
    from { opacity: 0; transform: translateY(-40px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .typing-line {
    font-family: 'JetBrains Mono', monospace;
    font-size: 13px;
    color: var(--neon-green);
    margin-bottom: 16px;
    letter-spacing: 2px;
    overflow: hidden;
    white-space: nowrap;
    width: 0;
    animation: typeIn 2s steps(40) 0.5s forwards;
  }

  @keyframes typeIn {
    to { width: 100%; }
  }

  .name-glitch {
    font-family: 'Orbitron', sans-serif;
    font-size: clamp(32px, 6vw, 58px);
    font-weight: 900;
    color: #fff;
    position: relative;
    display: inline-block;
    text-transform: uppercase;
    letter-spacing: 4px;
    animation: nameReveal 1s ease 0.3s both;
  }

  @keyframes nameReveal {
    from { opacity: 0; letter-spacing: 20px; filter: blur(10px); }
    to { opacity: 1; letter-spacing: 4px; filter: blur(0); }
  }

  .name-glitch::before,
  .name-glitch::after {
    content: 'ANKIT BHARTI';
    position: absolute;
    top: 0; left: 0;
    width: 100%;
  }
  .name-glitch::before {
    color: var(--neon-cyan);
    animation: glitch1 4s infinite;
    clip-path: polygon(0 0, 100% 0, 100% 35%, 0 35%);
  }
  .name-glitch::after {
    color: var(--neon-pink);
    animation: glitch2 4s infinite;
    clip-path: polygon(0 65%, 100% 65%, 100% 100%, 0 100%);
  }

  @keyframes glitch1 {
    0%,90%,100% { transform: none; opacity: 0; }
    91% { transform: translateX(-3px); opacity: 0.8; }
    93% { transform: translateX(3px); opacity: 0.8; }
    95% { transform: none; opacity: 0; }
  }
  @keyframes glitch2 {
    0%,92%,100% { transform: none; opacity: 0; }
    93% { transform: translateX(3px); opacity: 0.7; }
    95% { transform: translateX(-2px); opacity: 0.7; }
    97% { transform: none; opacity: 0; }
  }

  .role-tag {
    font-family: 'Rajdhani', sans-serif;
    font-size: 18px;
    font-weight: 600;
    letter-spacing: 6px;
    color: var(--neon-cyan);
    margin-top: 12px;
    text-transform: uppercase;
    animation: fadeSlideDown 1s ease 1s both;
    text-shadow: 0 0 20px var(--neon-cyan);
  }

  /* Wave emoji row */
  .emoji-row {
    margin-top: 18px;
    font-size: 24px;
    animation: fadeSlideDown 1s ease 1.2s both;
  }

  /* === SECTION CARDS === */
  .section {
    margin-bottom: 24px;
    animation: fadeSlideUp 0.8s ease both;
  }
  .section:nth-child(1) { animation-delay: 0.2s; }
  .section:nth-child(2) { animation-delay: 0.4s; }
  .section:nth-child(3) { animation-delay: 0.6s; }
  .section:nth-child(4) { animation-delay: 0.8s; }
  .section:nth-child(5) { animation-delay: 1.0s; }

  @keyframes fadeSlideUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .card {
    background: var(--glass);
    border: 1px solid var(--glass-border);
    border-radius: 16px;
    padding: 24px;
    position: relative;
    overflow: hidden;
    backdrop-filter: blur(10px);
    transition: border-color 0.3s, box-shadow 0.3s, transform 0.3s;
  }

  .card:hover {
    border-color: var(--neon-cyan);
    box-shadow: 0 0 30px rgba(0,245,255,0.15), inset 0 0 30px rgba(0,245,255,0.03);
    transform: translateY(-2px);
  }

  .card::before {
    content: '';
    position: absolute;
    top: 0; left: -100%;
    width: 100%; height: 2px;
    background: linear-gradient(90deg, transparent, var(--neon-cyan), transparent);
    animation: scanLine 4s linear infinite;
  }

  @keyframes scanLine {
    to { left: 200%; }
  }

  .section-title {
    font-family: 'Orbitron', sans-serif;
    font-size: 13px;
    font-weight: 700;
    letter-spacing: 4px;
    color: var(--neon-cyan);
    text-transform: uppercase;
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .section-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--glass-border), transparent);
  }

  /* === ABOUT SECTION === */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }

  .about-item {
    display: flex;
    align-items: flex-start;
    gap: 10px;
    padding: 10px 14px;
    background: rgba(0,245,255,0.03);
    border: 1px solid rgba(0,245,255,0.08);
    border-radius: 10px;
    font-size: 12px;
    line-height: 1.6;
    color: #adc8d8;
    transition: all 0.3s;
  }
  .about-item:hover {
    background: rgba(0,245,255,0.08);
    border-color: rgba(0,245,255,0.3);
    color: #fff;
    transform: translateX(4px);
  }
  .about-item .icon {
    font-size: 16px;
    flex-shrink: 0;
    margin-top: 1px;
  }

  /* === TECH STACK === */
  .tech-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }

  .tech-badge {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 6px 14px;
    border-radius: 8px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 1px;
    cursor: pointer;
    position: relative;
    overflow: hidden;
    transition: transform 0.2s, box-shadow 0.2s;
    animation: badgePop 0.4s ease both;
  }

  .tech-badge::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(255,255,255,0.1), transparent);
    opacity: 0;
    transition: opacity 0.2s;
  }
  .tech-badge:hover::before { opacity: 1; }
  .tech-badge:hover { transform: translateY(-3px) scale(1.05); }

  .badge-cyan { background: rgba(0,245,255,0.12); border: 1px solid rgba(0,245,255,0.4); color: var(--neon-cyan); box-shadow: 0 0 10px rgba(0,245,255,0.1); }
  .badge-pink { background: rgba(255,0,110,0.12); border: 1px solid rgba(255,0,110,0.4); color: #ff4d9b; box-shadow: 0 0 10px rgba(255,0,110,0.1); }
  .badge-green { background: rgba(57,255,20,0.08); border: 1px solid rgba(57,255,20,0.3); color: var(--neon-green); box-shadow: 0 0 10px rgba(57,255,20,0.08); }
  .badge-purple { background: rgba(191,0,255,0.12); border: 1px solid rgba(191,0,255,0.4); color: #d966ff; box-shadow: 0 0 10px rgba(191,0,255,0.1); }
  .badge-orange { background: rgba(255,107,0,0.12); border: 1px solid rgba(255,107,0,0.4); color: #ff8c42; box-shadow: 0 0 10px rgba(255,107,0,0.1); }
  .badge-yellow { background: rgba(255,214,0,0.12); border: 1px solid rgba(255,214,0,0.4); color: #ffd600; box-shadow: 0 0 10px rgba(255,214,0,0.1); }

  /* === STATS === */
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 14px;
  }

  .stat-box {
    text-align: center;
    padding: 20px 10px;
    background: rgba(0,245,255,0.03);
    border: 1px solid rgba(0,245,255,0.1);
    border-radius: 12px;
    position: relative;
    overflow: hidden;
    transition: all 0.3s;
  }
  .stat-box:hover {
    border-color: var(--neon-cyan);
    background: rgba(0,245,255,0.07);
    transform: scale(1.03);
  }
  .stat-box::before {
    content: '';
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, transparent, var(--neon-cyan), transparent);
    animation: bottomGlow 3s ease-in-out infinite;
  }
  @keyframes bottomGlow {
    0%,100% { opacity: 0; }
    50% { opacity: 1; }
  }

  .stat-num {
    font-family: 'Orbitron', sans-serif;
    font-size: 28px;
    font-weight: 900;
    color: var(--neon-cyan);
    text-shadow: 0 0 20px var(--neon-cyan);
    line-height: 1;
    display: block;
  }
  .stat-label {
    font-size: 10px;
    color: #6b8999;
    letter-spacing: 2px;
    margin-top: 8px;
    text-transform: uppercase;
    display: block;
  }

  /* === STREAK BAR === */
  .streak-section { margin-top: 16px; }
  .streak-label {
    display: flex;
    justify-content: space-between;
    font-size: 11px;
    color: #6b8999;
    margin-bottom: 6px;
  }
  .streak-track {
    height: 6px;
    background: rgba(255,255,255,0.05);
    border-radius: 100px;
    overflow: hidden;
  }
  .streak-fill {
    height: 100%;
    border-radius: 100px;
    position: relative;
    animation: fillBar 2s ease 1.5s both;
  }
  @keyframes fillBar {
    from { width: 0 !important; }
  }
  .streak-fill::after {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(90deg, transparent 0%, rgba(255,255,255,0.3) 50%, transparent 100%);
    animation: shimmer 2s linear infinite;
  }
  @keyframes shimmer {
    from { transform: translateX(-100%); }
    to { transform: translateX(100%); }
  }

  /* === LANG CHART === */
  .lang-bars { display: flex; flex-direction: column; gap: 12px; }
  .lang-row { display: flex; align-items: center; gap: 12px; }
  .lang-name { font-size: 11px; color: #adc8d8; width: 80px; flex-shrink: 0; }
  .lang-bar-track { flex: 1; height: 8px; background: rgba(255,255,255,0.05); border-radius: 100px; overflow: hidden; }
  .lang-bar { height: 100%; border-radius: 100px; animation: fillBar 1.5s ease both; position: relative; overflow: hidden; }
  .lang-bar::after { content: ''; position: absolute; inset: 0; background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent); animation: shimmer 2s linear infinite; }
  .lang-pct { font-size: 11px; color: #6b8999; width: 35px; text-align: right; flex-shrink: 0; }

  /* === ACTIVITY GRID === */
  .activity-grid {
    display: grid;
    grid-template-columns: repeat(52, 1fr);
    gap: 3px;
    margin-top: 10px;
  }
  .activity-cell {
    aspect-ratio: 1;
    border-radius: 2px;
    animation: cellReveal 0.05s ease both;
  }
  .act-0 { background: rgba(255,255,255,0.05); }
  .act-1 { background: rgba(0,245,255,0.2); }
  .act-2 { background: rgba(0,245,255,0.4); }
  .act-3 { background: rgba(0,245,255,0.7); }
  .act-4 { background: var(--neon-cyan); box-shadow: 0 0 4px var(--neon-cyan); }

  .activity-cell:hover {
    transform: scale(1.5);
    z-index: 10;
    position: relative;
  }

  /* === CONNECT LINKS === */
  .connect-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
  }
  .connect-btn {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 10px 20px;
    border-radius: 10px;
    font-family: 'Rajdhani', sans-serif;
    font-size: 14px;
    font-weight: 700;
    letter-spacing: 2px;
    text-transform: uppercase;
    cursor: pointer;
    border: none;
    position: relative;
    overflow: hidden;
    transition: transform 0.2s, box-shadow 0.2s;
  }
  .connect-btn::before {
    content: '';
    position: absolute;
    inset: 0;
    transform: translateX(-100%);
    background: rgba(255,255,255,0.1);
    transition: transform 0.3s;
  }
  .connect-btn:hover::before { transform: translateX(0); }
  .connect-btn:hover { transform: translateY(-2px); box-shadow: 0 8px 25px rgba(0,0,0,0.3); }

  .btn-github { background: linear-gradient(135deg, #1a1a2e, #16213e); border: 1px solid rgba(255,255,255,0.15); color: #fff; }
  .btn-twitter { background: linear-gradient(135deg, #001333, #002266); border: 1px solid rgba(29,155,240,0.4); color: #1d9bf0; }
  .btn-linkedin { background: linear-gradient(135deg, #001133, #003366); border: 1px solid rgba(10,102,194,0.4); color: #0a66c2; }

  /* === FOOTER === */
  .footer {
    text-align: center;
    padding: 30px 0;
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    color: #3a5060;
    letter-spacing: 2px;
    animation: pulse 3s ease-in-out infinite;
  }
  @keyframes pulse {
    0%,100% { opacity: 0.4; }
    50% { opacity: 1; color: var(--neon-cyan); }
  }

  /* === PROFILE HEADER ROW === */
  .profile-row {
    display: flex;
    align-items: center;
    gap: 30px;
    flex-wrap: wrap;
  }

  .avatar-container {
    position: relative;
    flex-shrink: 0;
    width: 100px;
    height: 100px;
  }

  .avatar-ring {
    position: absolute;
    inset: -6px;
    border-radius: 50%;
    border: 2px solid transparent;
    border-top-color: var(--neon-cyan);
    border-right-color: var(--neon-pink);
    animation: spin 3s linear infinite;
  }
  .avatar-ring2 {
    position: absolute;
    inset: -12px;
    border-radius: 50%;
    border: 1px solid transparent;
    border-bottom-color: var(--neon-purple);
    border-left-color: var(--neon-green);
    animation: spin 5s linear infinite reverse;
  }

  @keyframes spin { to { transform: rotate(360deg); } }

  .avatar-inner {
    width: 100%;
    height: 100%;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--neon-cyan), var(--neon-pink), var(--neon-purple));
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Orbitron', sans-serif;
    font-size: 36px;
    font-weight: 900;
    color: var(--dark);
    text-shadow: none;
    position: relative;
    z-index: 1;
    animation: avatarPulse 4s ease-in-out infinite;
  }
  @keyframes avatarPulse {
    0%,100% { box-shadow: 0 0 20px rgba(0,245,255,0.3); }
    50% { box-shadow: 0 0 40px rgba(0,245,255,0.6), 0 0 80px rgba(0,245,255,0.2); }
  }

  .profile-meta { flex: 1; }
  .profile-meta .handle {
    font-family: 'JetBrains Mono', monospace;
    font-size: 13px;
    color: var(--neon-green);
    margin-bottom: 8px;
  }
  .profile-meta .bio {
    font-family: 'Rajdhani', sans-serif;
    font-size: 16px;
    font-weight: 600;
    color: #adc8d8;
    line-height: 1.6;
  }

  .mini-stats-row {
    display: flex;
    gap: 20px;
    margin-top: 14px;
    flex-wrap: wrap;
  }
  .mini-stat {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .mini-stat span:first-child {
    font-family: 'Orbitron', sans-serif;
    font-size: 18px;
    font-weight: 900;
    color: var(--neon-cyan);
    text-shadow: 0 0 15px var(--neon-cyan);
  }
  .mini-stat span:last-child {
    font-size: 10px;
    color: #3a6070;
    letter-spacing: 2px;
    text-transform: uppercase;
  }

  /* Separator */
  .mini-stat-sep { width: 1px; background: rgba(0,245,255,0.15); }

  /* Copyable README badge */
  .readme-badge-bar {
    background: rgba(0,0,0,0.4);
    border: 1px solid rgba(0,245,255,0.1);
    border-radius: 12px;
    padding: 16px 20px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 10px;
    flex-wrap: wrap;
  }
  .readme-badge-bar code {
    font-size: 11px;
    color: #6b8999;
    flex: 1;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
  .copy-btn {
    background: rgba(0,245,255,0.1);
    border: 1px solid rgba(0,245,255,0.3);
    color: var(--neon-cyan);
    padding: 5px 14px;
    border-radius: 6px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    cursor: pointer;
    transition: all 0.2s;
    flex-shrink: 0;
  }
  .copy-btn:hover { background: rgba(0,245,255,0.2); }

  /* Responsive */
  @media (max-width: 600px) {
    .about-grid { grid-template-columns: 1fr; }
    .stats-grid { grid-template-columns: repeat(2, 1fr); }
    .activity-grid { grid-template-columns: repeat(26, 1fr); }
    .profile-row { flex-direction: column; align-items: flex-start; }
  }
</style>
</head>
<body>
<div class="grid-bg"></div>
<div class="orb orb1"></div>
<div class="orb orb2"></div>
<div class="orb orb3"></div>

<div class="wrapper">

  <!-- HEADER -->
  <div class="header">
    <div class="typing-line">// INITIALIZING DEVELOPER PROFILE... WELCOME TO MY WORLD</div>
    <div class="name-glitch">ANKIT BHARTI</div>
    <div class="role-tag">Full-Stack Developer · Builder · Creator</div>
    <div class="emoji-row">👋 &nbsp; 💻 &nbsp; 🚀 &nbsp; ⚡ &nbsp; 🎯</div>
  </div>

  <!-- PROFILE CARD -->
  <div class="section">
    <div class="card">
      <div class="section-title">◈ IDENTITY NODE</div>
      <div class="profile-row">
        <div class="avatar-container">
          <div class="avatar-ring"></div>
          <div class="avatar-ring2"></div>
          <div class="avatar-inner">AB</div>
        </div>
        <div class="profile-meta">
          <div class="handle">@ankitbhartii · github.com/ankitbhartii</div>
          <div class="bio">Chrismatic programmer who ships real products.<br>Building at the intersection of AI, Web & Mobile.</div>
          <div class="mini-stats-row">
            <div class="mini-stat"><span>45</span><span>Repos</span></div>
            <div class="mini-stat-sep"></div>
            <div class="mini-stat"><span>77</span><span>Stars</span></div>
            <div class="mini-stat-sep"></div>
            <div class="mini-stat"><span>5</span><span>Followers</span></div>
            <div class="mini-stat-sep"></div>
            <div class="mini-stat"><span>38</span><span>Following</span></div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- ABOUT ME -->
  <div class="section">
    <div class="card">
      <div class="section-title">◈ ABOUT.EXE</div>
      <div class="about-grid">
        <div class="about-item"><span class="icon">🔭</span><span>Currently working on Python projects & AI integrations</span></div>
        <div class="about-item"><span class="icon">🛡️</span><span>Getting started with Cybersecurity — ethical hacking & beyond</span></div>
        <div class="about-item"><span class="icon">📊</span><span>Learning Data Analysis in Python — NumPy, Pandas, Matplotlib</span></div>
        <div class="about-item"><span class="icon">📱</span><span>Currently mastering Flutter for cross-platform mobile apps</span></div>
        <div class="about-item"><span class="icon">💬</span><span>Ask me anything about C++, Python, React, or Node.js</span></div>
        <div class="about-item"><span class="icon">⚡</span><span>Fun fact: I'm a chrismatic programmer who ships, not just codes</span></div>
      </div>
    </div>
  </div>

  <!-- TECH STACK -->
  <div class="section">
    <div class="card">
      <div class="section-title">◈ TECH ARSENAL</div>
      <div class="tech-grid">
        <span class="tech-badge badge-cyan">⚡ JavaScript</span>
        <span class="tech-badge badge-yellow">⚡ Python</span>
        <span class="tech-badge badge-cyan">⚛️ React</span>
        <span class="tech-badge badge-cyan">▲ Next.js</span>
        <span class="tech-badge badge-green">📱 React Native</span>
        <span class="tech-badge badge-purple">🦋 Flutter</span>
        <span class="tech-badge badge-green">🟢 Node.js</span>
        <span class="tech-badge badge-orange">🐍 Django</span>
        <span class="tech-badge badge-cyan">🌐 HTML5</span>
        <span class="tech-badge badge-orange">🎨 CSS3</span>
        <span class="tech-badge badge-cyan">💧 Bootstrap</span>
        <span class="tech-badge badge-pink">🔴 Angular</span>
        <span class="tech-badge badge-yellow">☕ Java</span>
        <span class="tech-badge badge-cyan">⚙️ C++</span>
        <span class="tech-badge badge-purple">🐘 PostgreSQL</span>
        <span class="tech-badge badge-green">🍃 MongoDB</span>
        <span class="tech-badge badge-orange">🐬 MySQL</span>
        <span class="tech-badge badge-cyan">🔍 React Query</span>
        <span class="tech-badge badge-yellow">🧮 NumPy</span>
        <span class="tech-badge badge-pink">☁️ Google Cloud</span>
        <span class="tech-badge badge-purple">🎨 Figma</span>
        <span class="tech-badge badge-orange">🖌️ Canva</span>
        <span class="tech-badge badge-pink">🏀 Dribbble</span>
        <span class="tech-badge badge-cyan">🎭 Adobe Illustrator</span>
      </div>
    </div>
  </div>

  <!-- GITHUB STATS -->
  <div class="section">
    <div class="card">
      <div class="section-title">◈ GITHUB STATS</div>
      <div class="stats-grid">
        <div class="stat-box">
          <span class="stat-num" id="commits">0</span>
          <span class="stat-label">Commits</span>
        </div>
        <div class="stat-box">
          <span class="stat-num" id="prs">0</span>
          <span class="stat-label">Pull Reqs</span>
        </div>
        <div class="stat-box">
          <span class="stat-num" id="issues">0</span>
          <span class="stat-label">Issues</span>
        </div>
        <div class="stat-box">
          <span class="stat-num" id="contributed">0</span>
          <span class="stat-label">Contributed</span>
        </div>
      </div>

      <div class="streak-section" style="margin-top:20px;">
        <div class="streak-label">
          <span>🔥 Current Streak</span>
          <span style="color:var(--neon-cyan); font-family:'Orbitron',sans-serif; font-size:13px;">28 days</span>
        </div>
        <div class="streak-track">
          <div class="streak-fill" style="width:72%; background: linear-gradient(90deg, var(--neon-pink), var(--neon-cyan));"></div>
        </div>
      </div>

      <div class="streak-section">
        <div class="streak-label">
          <span>⭐ Total Stars Earned</span>
          <span style="color:var(--neon-yellow,#ffd600); font-family:'Orbitron',sans-serif; font-size:13px;">77</span>
        </div>
        <div class="streak-track">
          <div class="streak-fill" style="width:55%; background: linear-gradient(90deg, #ffd600, var(--neon-orange));"></div>
        </div>
      </div>
    </div>
  </div>

  <!-- LANGUAGES -->
  <div class="section">
    <div class="card">
      <div class="section-title">◈ TOP LANGUAGES</div>
      <div class="lang-bars">
        <div class="lang-row">
          <span class="lang-name">JavaScript</span>
          <div class="lang-bar-track"><div class="lang-bar" style="width:85%; background: linear-gradient(90deg, #f7df1e, #e8a200); animation-delay:0.1s;"></div></div>
          <span class="lang-pct">85%</span>
        </div>
        <div class="lang-row">
          <span class="lang-name">Python</span>
          <div class="lang-bar-track"><div class="lang-bar" style="width:72%; background: linear-gradient(90deg, #3776ab, #ffd43b); animation-delay:0.2s;"></div></div>
          <span class="lang-pct">72%</span>
        </div>
        <div class="lang-row">
          <span class="lang-name">TypeScript</span>
          <div class="lang-bar-track"><div class="lang-bar" style="width:60%; background: linear-gradient(90deg, #007acc, #00bcd4); animation-delay:0.3s;"></div></div>
          <span class="lang-pct">60%</span>
        </div>
        <div class="lang-row">
          <span class="lang-name">Dart/Flutter</span>
          <div class="lang-bar-track"><div class="lang-bar" style="width:45%; background: linear-gradient(90deg, #54c5f8, #0175c2); animation-delay:0.4s;"></div></div>
          <span class="lang-pct">45%</span>
        </div>
        <div class="lang-row">
          <span class="lang-name">C++</span>
          <div class="lang-bar-track"><div class="lang-bar" style="width:38%; background: linear-gradient(90deg, #00599c, #bf00ff); animation-delay:0.5s;"></div></div>
          <span class="lang-pct">38%</span>
        </div>
        <div class="lang-row">
          <span class="lang-name">HTML/CSS</span>
          <div class="lang-bar-track"><div class="lang-bar" style="width:90%; background: linear-gradient(90deg, #e34f26, #1572b6); animation-delay:0.6s;"></div></div>
          <span class="lang-pct">90%</span>
        </div>
      </div>
    </div>
  </div>

  <!-- CONTRIBUTION GRAPH -->
  <div class="section">
    <div class="card">
      <div class="section-title">◈ CONTRIBUTION MATRIX</div>
      <div id="activity-grid" class="activity-grid"></div>
      <div style="display:flex; gap:8px; align-items:center; margin-top:12px; font-size:10px; color:#3a5060;">
        <span>Less</span>
        <div style="width:12px;height:12px;border-radius:2px;background:rgba(255,255,255,0.05);"></div>
        <div style="width:12px;height:12px;border-radius:2px;background:rgba(0,245,255,0.2);"></div>
        <div style="width:12px;height:12px;border-radius:2px;background:rgba(0,245,255,0.4);"></div>
        <div style="width:12px;height:12px;border-radius:2px;background:rgba(0,245,255,0.7);"></div>
        <div style="width:12px;height:12px;border-radius:2px;background:var(--neon-cyan);box-shadow:0 0 4px var(--neon-cyan);"></div>
        <span>More</span>
      </div>
    </div>
  </div>

  <!-- CONNECT -->
  <div class="section">
    <div class="card">
      <div class="section-title">◈ CONNECT.INIT()</div>
      <div class="connect-grid">
        <button class="connect-btn btn-github">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0 0 24 12c0-6.63-5.37-12-12-12z"/></svg>
          GitHub
        </button>
        <button class="connect-btn btn-twitter">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>
          Twitter / X
        </button>
        <button class="connect-btn btn-linkedin">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 0 1-2.063-2.065 2.064 2.064 0 1 1 2.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
          LinkedIn
        </button>
      </div>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer">
    ◈ — CODED WITH ❤️ &amp; ☕ BY ANKIT BHARTI — ◈<br>
    <span style="font-size:9px; margin-top:6px; display:block;">[ LAST UPDATED: 2026 · CONTRIBUTIONS WELCOME ]</span>
  </div>

</div>

<script>
// Animate stat counters
function animateCounter(el, target, duration, suffix='') {
  let start = 0;
  const step = target / (duration / 16);
  const timer = setInterval(() => {
    start = Math.min(start + step, target);
    el.textContent = Math.round(start) + suffix;
    if (start >= target) clearInterval(timer);
  }, 16);
}

setTimeout(() => {
  animateCounter(document.getElementById('commits'), 847, 1500);
  animateCounter(document.getElementById('prs'), 124, 1500);
  animateCounter(document.getElementById('issues'), 89, 1500);
  animateCounter(document.getElementById('contributed'), 31, 1500);
}, 1000);

// Generate contribution grid
const grid = document.getElementById('activity-grid');
const levels = [0, 0, 0, 1, 1, 2, 3, 4];

for (let w = 0; w < 52; w++) {
  for (let d = 0; d < 7; d++) {
    const cell = document.createElement('div');
    const rand = Math.random();
    let level;
    if (rand < 0.45) level = 0;
    else if (rand < 0.65) level = 1;
    else if (rand < 0.80) level = 2;
    else if (rand < 0.92) level = 3;
    else level = 4;
    cell.className = `activity-cell act-${level}`;
    cell.style.animationDelay = `${(w * 7 + d) * 0.005}s`;
    grid.appendChild(cell);
  }
}

// Copy button handler
document.querySelectorAll('.copy-btn').forEach(btn => {
  btn.addEventListener('click', () => {
    const code = btn.previousElementSibling.textContent;
    navigator.clipboard.writeText(code).then(() => {
      btn.textContent = 'COPIED!';
      btn.style.color = 'var(--neon-green)';
      setTimeout(() => { btn.textContent = 'COPY'; btn.style.color = ''; }, 2000);
    });
  });
});
</script>
</body>
</html>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;700;800&display=swap');

  .gp-wrap {
    font-family: 'Syne', sans-serif;
    background: #080c14;
    color: #e2e8f0;
    border-radius: 16px;
    overflow: hidden;
    position: relative;
    padding: 0;
  }

  .gp-scanlines {
    position: absolute; inset: 0;
    background: repeating-linear-gradient(to bottom, transparent 0px, transparent 3px, rgba(0,255,170,0.015) 3px, rgba(0,255,170,0.015) 4px);
    pointer-events: none; z-index: 0;
  }

  .gp-hero {
    position: relative; z-index: 1;
    padding: 36px 36px 24px;
    border-bottom: 1px solid rgba(0,255,170,0.12);
    display: flex; gap: 28px; align-items: flex-start;
  }

  .gp-avatar {
    flex-shrink: 0;
    width: 80px; height: 80px;
    border-radius: 50%;
    background: linear-gradient(135deg, #00ffaa22, #00aaff22);
    border: 2px solid #00ffaa44;
    display: flex; align-items: center; justify-content: center;
    font-family: 'Space Mono', monospace;
    font-size: 28px; font-weight: 700;
    color: #00ffaa;
    letter-spacing: -2px;
    position: relative;
  }
  .gp-avatar::after {
    content: '';
    position: absolute; inset: -5px;
    border-radius: 50%;
    border: 1px dashed #00ffaa33;
    animation: spin 12s linear infinite;
  }
  @keyframes spin { to { transform: rotate(360deg); } }

  .gp-title { flex: 1; }
  .gp-name {
    font-size: 28px; font-weight: 800;
    color: #fff; margin: 0 0 4px;
    letter-spacing: -0.5px;
  }
  .gp-name span { color: #00ffaa; }

  .gp-tagline {
    font-family: 'Space Mono', monospace;
    font-size: 12px; color: #64748b;
    margin: 0 0 12px;
  }
  .gp-tagline .cursor {
    display: inline-block; width: 7px; height: 13px;
    background: #00ffaa; vertical-align: -2px;
    animation: blink 1s step-end infinite;
  }
  @keyframes blink { 50% { opacity: 0; } }

  .gp-badges { display: flex; gap: 8px; flex-wrap: wrap; }
  .gp-badge {
    font-family: 'Space Mono', monospace;
    font-size: 10px; padding: 3px 9px;
    border-radius: 20px; font-weight: 700;
    letter-spacing: 0.5px;
  }
  .gp-badge-ml { background: #00ffaa18; color: #00ffaa; border: 1px solid #00ffaa33; }
  .gp-badge-fe { background: #00aaff18; color: #60c8ff; border: 1px solid #00aaff33; }
  .gp-badge-fit { background: #ff6a0018; color: #ff9d50; border: 1px solid #ff6a0033; }

  .gp-body { position: relative; z-index: 1; padding: 24px 36px; }

  .gp-section-label {
    font-family: 'Space Mono', monospace;
    font-size: 10px; color: #00ffaa99;
    letter-spacing: 2px; text-transform: uppercase;
    margin: 0 0 14px;
  }
  .gp-section-label::before { content: '// '; color: #00ffaa44; }

  .gp-stack-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
    gap: 8px; margin-bottom: 28px;
  }

  .gp-stack-item {
    background: #0f1724;
    border: 1px solid #1e2d42;
    border-radius: 10px;
    padding: 10px 8px;
    text-align: center;
    transition: all 0.2s;
    cursor: default;
  }
  .gp-stack-item:hover {
    border-color: #00ffaa44;
    background: #0f1f2e;
    transform: translateY(-2px);
  }
  .gp-stack-icon { font-size: 20px; margin-bottom: 4px; }
  .gp-stack-name { font-size: 10px; color: #64748b; font-family: 'Space Mono', monospace; }

  .gp-stats-row {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px; margin-bottom: 24px;
  }
  .gp-stat {
    background: #0f1724;
    border: 1px solid #1e2d42;
    border-radius: 12px;
    padding: 14px 12px;
    text-align: center;
  }
  .gp-stat-num {
    font-size: 22px; font-weight: 800;
    color: #fff; margin: 0; line-height: 1;
  }
  .gp-stat-num.green { color: #00ffaa; }
  .gp-stat-num.blue { color: #60c8ff; }
  .gp-stat-num.orange { color: #ff9d50; }
  .gp-stat-label { font-family: 'Space Mono', monospace; font-size: 9px; color: #64748b; margin: 4px 0 0; text-transform: uppercase; letter-spacing: 1px; }

  .gp-bar-wrap { margin-bottom: 28px; }
  .gp-bar-row { display: flex; align-items: center; gap: 10px; margin-bottom: 10px; }
  .gp-bar-lang { font-family: 'Space Mono', monospace; font-size: 11px; color: #94a3b8; width: 80px; flex-shrink: 0; }
  .gp-bar-track { flex: 1; height: 4px; background: #1e2d42; border-radius: 2px; overflow: hidden; }
  .gp-bar-fill { height: 100%; border-radius: 2px; animation: barIn 1.2s ease forwards; transform-origin: left; }
  @keyframes barIn { from { transform: scaleX(0); } to { transform: scaleX(1); } }
  .gp-bar-pct { font-family: 'Space Mono', monospace; font-size: 10px; color: #64748b; width: 32px; text-align: right; }

  .gp-socials { display: flex; gap: 10px; flex-wrap: wrap; }
  .gp-social {
    display: flex; align-items: center; gap: 6px;
    background: #0f1724; border: 1px solid #1e2d42;
    border-radius: 8px; padding: 8px 14px;
    font-family: 'Space Mono', monospace;
    font-size: 11px; color: #94a3b8;
    text-decoration: none; transition: all 0.2s;
    cursor: pointer;
  }
  .gp-social:hover { border-color: #00ffaa44; color: #00ffaa; background: #0f1f2e; }

  .gp-footer {
    position: relative; z-index: 1;
    border-top: 1px solid #1e2d42;
    padding: 14px 36px;
    display: flex; align-items: center; justify-content: space-between;
  }
  .gp-footer-txt { font-family: 'Space Mono', monospace; font-size: 10px; color: #334155; }
  .gp-pulse { width: 6px; height: 6px; border-radius: 50%; background: #00ffaa; animation: pulse 2s ease infinite; }
  @keyframes pulse { 0%,100%{opacity:1;transform:scale(1)} 50%{opacity:0.5;transform:scale(1.4)} }
</style>

<h2 class="sr-only">Kamal's GitHub profile — ML engineer, frontend developer, and fitness creator</h2>

<div class="gp-wrap">
  <div class="gp-scanlines"></div>

  <div class="gp-hero">
    <div class="gp-avatar">KM</div>
    <div class="gp-title">
      <p class="gp-name">hi, i'm <span>kamal</span> 👋</p>
      <p class="gp-tagline" id="tagline">_ <span class="cursor"></span></p>
      <div class="gp-badges">
        <span class="gp-badge gp-badge-ml">ML / AI</span>
        <span class="gp-badge gp-badge-fe">Frontend Dev</span>
        <span class="gp-badge gp-badge-fit">Fitness Creator</span>
      </div>
    </div>
  </div>

  <div class="gp-body">

    <p class="gp-section-label">stats</p>
    <div class="gp-stats-row">
      <div class="gp-stat"><p class="gp-stat-num green">50+</p><p class="gp-stat-label">Repos</p></div>
      <div class="gp-stat"><p class="gp-stat-num blue">120+</p><p class="gp-stat-label">Commits</p></div>
      <div class="gp-stat"><p class="gp-stat-num orange">8+</p><p class="gp-stat-label">Projects</p></div>
    </div>

    <p class="gp-section-label">top languages</p>
    <div class="gp-bar-wrap">
      <div class="gp-bar-row">
        <span class="gp-bar-lang">JavaScript</span>
        <div class="gp-bar-track"><div class="gp-bar-fill" style="width:82%;background:#f0db4f"></div></div>
        <span class="gp-bar-pct">82%</span>
      </div>
      <div class="gp-bar-row">
        <span class="gp-bar-lang">Python</span>
        <div class="gp-bar-track"><div class="gp-bar-fill" style="width:67%;background:#3776ab;animation-delay:0.15s"></div></div>
        <span class="gp-bar-pct">67%</span>
      </div>
      <div class="gp-bar-row">
        <span class="gp-bar-lang">TypeScript</span>
        <div class="gp-bar-track"><div class="gp-bar-fill" style="width:54%;background:#3178c6;animation-delay:0.3s"></div></div>
        <span class="gp-bar-pct">54%</span>
      </div>
      <div class="gp-bar-row">
        <span class="gp-bar-lang">Dart</span>
        <div class="gp-bar-track"><div class="gp-bar-fill" style="width:38%;background:#00b4ab;animation-delay:0.45s"></div></div>
        <span class="gp-bar-pct">38%</span>
      </div>
    </div>

    <p class="gp-section-label">stack</p>
    <div class="gp-stack-grid">
      <div class="gp-stack-item"><div class="gp-stack-icon">⚛️</div><div class="gp-stack-name">React</div></div>
      <div class="gp-stack-item"><div class="gp-stack-icon">📱</div><div class="gp-stack-name">RN</div></div>
      <div class="gp-stack-item"><div class="gp-stack-icon">🔥</div><div class="gp-stack-name">Firebase</div></div>
      <div class="gp-stack-item"><div class="gp-stack-icon">🐘</div><div class="gp-stack-name">Supabase</div></div>
      <div class="gp-stack-item"><div class="gp-stack-icon">🐍</div><div class="gp-stack-name">PyTorch</div></div>
      <div class="gp-stack-item"><div class="gp-stack-icon">☁️</div><div class="gp-stack-name">GCP</div></div>
      <div class="gp-stack-item"><div class="gp-stack-icon">🎨</div><div class="gp-stack-name">Figma</div></div>
      <div class="gp-stack-item"><div class="gp-stack-icon">🌊</div><div class="gp-stack-name">Flutter</div></div>
      <div class="gp-stack-item"><div class="gp-stack-icon">🔷</div><div class="gp-stack-name">TypeScript</div></div>
      <div class="gp-stack-item"><div class="gp-stack-icon">🧠</div><div class="gp-stack-name">TensorFlow</div></div>
    </div>

    <p class="gp-section-label">connect</p>
    <div class="gp-socials">
      <a class="gp-social" href="https://linkedin.com/in/kamalmedhi7434" target="_blank">
        <i class="ti ti-brand-linkedin" aria-hidden="true"></i> LinkedIn
      </a>
      <a class="gp-social" href="https://kaggle.com/kamalmedhi7434" target="_blank">
        <i class="ti ti-chart-bar" aria-hidden="true"></i> Kaggle
      </a>
      <span class="gp-social" onclick="sendPrompt('Generate a README.md markdown version of this profile for my GitHub')">
        <i class="ti ti-download" aria-hidden="true"></i> Get README.md ↗
      </span>
    </div>
  </div>

  <div class="gp-footer">
    <span class="gp-footer-txt">kamalmedhi7434 · github.com</span>
    <div class="gp-pulse"></div>
  </div>
</div>

<script>
const lines = [
  'building fitness apps with React Native...',
  'training models, training bodies 💪',
  'ML engineer by day, coach by night',
  'Guwahati → building in public 🚀',
];
let li = 0, ci = 0, deleting = false;
const el = document.getElementById('tagline');
function type() {
  const line = lines[li];
  if (!deleting) {
    ci++;
    el.innerHTML = line.slice(0, ci) + ' <span class="cursor"></span>';
    if (ci === line.length) { deleting = true; setTimeout(type, 2200); return; }
    setTimeout(type, 55);
  } else {
    ci--;
    el.innerHTML = line.slice(0, ci) + ' <span class="cursor"></span>';
    if (ci === 0) { deleting = false; li = (li + 1) % lines.length; setTimeout(type, 400); return; }
    setTimeout(type, 28);
  }
}
setTimeout(type, 600);
</script>

<!doctype html>
<html lang="id">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1"/>
  <title>Kartu Ucapan — Gelap & Tegas</title>

  <!-- Font -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap" rel="stylesheet">

  <style>
    :root{
      --bg:#0b0f16;         /* very dark background */
      --card:#0f1720;       /* card / panel */
      --muted:#97a0b3;      /* muted text */
      --accent:#2ec4b6;     /* teal-ish accent */
      --accent-2:#f4a261;   /* warm accent for CTA */
      --glass: rgba(255,255,255,0.04);
    }

    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;
      font-family:Inter,system-ui,-apple-system,Segoe UI,Roboto,"Helvetica Neue",Arial;
      background: radial-gradient(1200px 600px at 10% 10%, rgba(46,196,182,0.06), transparent 8%),
                  radial-gradient(900px 500px at 90% 90%, rgba(244,162,97,0.04), transparent 6%),
                  var(--bg);
      color:#e6eef6;
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      display:flex;
      align-items:center;
      justify-content:center;
      padding:32px;
    }

    .stage{
      width:min(980px,95%);
      max-width:980px;
      display:grid;
      grid-template-columns: 1fr 420px;
      gap:28px;
      align-items:center;
    }

    /* Left - Visual big card */
    .hero{
      background: linear-gradient(180deg, rgba(255,255,255,0.02), transparent);
      border-radius:18px;
      padding:34px;
      min-height:420px;
      position:relative;
      overflow:hidden;
      box-shadow: 0 8px 30px rgba(4,6,12,0.6);
      border: 1px solid rgba(255,255,255,0.03);
    }

    /* subtle vertical stripes */
    .hero::before{
      content:"";
      position:absolute;
      inset:0;
      background-image: linear-gradient(90deg, rgba(255,255,255,0.006) 1px, transparent 1px);
      background-size: 24px 24px;
      pointer-events:none;
    }

    .title{
      font-size:20px;
      font-weight:600;
      color:var(--muted);
      margin:0 0 10px 0;
      letter-spacing:0.4px;
    }

    .main-msg{
      font-size:34px;
      line-height:1.05;
      font-weight:700;
      margin:0 0 18px 0;
      color: #e9f6f3;
    }

    .sub-msg{
      color:var(--muted);
      margin:0 0 28px 0;
      font-size:14.5px;
      max-width:70%;
    }

    /* typing box */
    .box{
      background: linear-gradient(180deg, rgba(255,255,255,0.015), rgba(255,255,255,0.01));
      border-radius:12px;
      padding:18px 18px;
      width:100%;
      max-width:700px;
      color:#dfeaf0;
      box-shadow: inset 0 1px 0 rgba(255,255,255,0.02);
      border: 1px solid rgba(255,255,255,0.02);
    }

    .typed-lines{
      font-size:18px;
      min-height:88px;
      white-space:pre-wrap;
      word-break:break-word;
    }

    .cursor{
      display:inline-block;
      width:10px;
      height:20px;
      background:var(--accent);
      margin-left:6px;
      vertical-align:middle;
      animation: blink 1s steps(2,end) infinite;
    }
    @keyframes blink{ 50%{opacity:0} }

    .controls{
      margin-top:18px;
      display:flex;
      gap:12px;
      align-items:center;
    }

    .btn{
      appearance:none;
      border:0;
      padding:10px 16px;
      border-radius:10px;
      font-weight:600;
      cursor:pointer;
      display:inline-flex;
      gap:8px;
      align-items:center;
      justify-content:center;
    }

    .btn-show{
      background: linear-gradient(90deg, var(--accent), #1fa99b);
      color:#021114;
      box-shadow: 0 6px 18px rgba(46,196,182,0.14);
    }

    .btn-reset{
      background:transparent;
      color:var(--muted);
      border:1px solid rgba(255,255,255,0.03);
    }

    /* Right panel: customization */
    .side{
      background:var(--card);
      border-radius:12px;
      padding:18px;
      height:100%;
      min-height:420px;
      box-shadow: 0 6px 22px rgba(2,4,8,0.6);
      border:1px solid rgba(255,255,255,0.02);
    }

    .panel-title{
      font-weight:700;
      font-size:14px;
      margin-bottom:12px;
      color:var(--muted);
    }

    label{display:block;font-size:13px;color:var(--muted);margin-bottom:6px}
    input[type="text"], textarea, select{
      width:100%;
      padding:10px 12px;
      border-radius:8px;
      border:1px solid rgba(255,255,255,0.03);
      background:var(--glass);
      color:#dfeff6;
      font-size:14px;
      outline:none;
    }
    textarea{min-height:120px; resize:vertical}

    .small{
      font-size:12px;
      color:var(--muted);
      margin-top:6px;
    }

    .meta{
      display:flex;
      gap:10px;
      margin-top:12px;
      align-items:center;
    }

    .accent-preview{
      width:44px;height:44px;border-radius:8px;border:1px solid rgba(255,255,255,0.03);
      display:inline-block;
    }

    footer.notice{
      margin-top:18px;
      font-size:12px;
      color:var(--muted);
    }

    /* responsive */
    @media (max-width:980px){
      .stage{grid-template-columns: 1fr; gap:18px}
      .main-msg{font-size:28px}
      .hero{min-height:360px}
    }

    /* confetti canvas on top */
    #confettiCanvas{
      position:fixed;
      inset:0;
      pointer-events:none;
      z-index:60;
    }

  </style>
</head>
<body>
  <canvas id="confettiCanvas"></canvas>

  <div class="stage">
    <div class="hero">
      <p class="title">Kartu Ucapan</p>
      <h1 class="main-msg">Untuk seseorang istimewa</h1>
      <p class="sub-msg">Tekan "Tampilkan Ucapan" untuk lihat pesanmu. Desain gelap dan tegas supaya cocok untuk nuansa maskulin.</p>

      <div class="box" id="displayBox">
        <div class="typed-lines" id="typed"></div>
        <div id="cursor" class="cursor" aria-hidden="true"></div>

        <div class="controls">
          <button class="btn btn-show" id="revealBtn">Tampilkan Ucapan</button>
          <button class="btn btn-reset" id="resetBtn">Reset</button>
        </div>
      </div>

      <p class="small" style="margin-top:14px">Tip: edit teks di panel kanan, lalu klik "Tampilkan Ucapan".</p>
    </div>

    <aside class="side">
      <div class="panel-title">Sesuaikan Ucapan & Tampilan</div>

      <label for="toName">Untuk (nama)</label>
      <input id="toName" type="text" value="Dika"/>

      <label for="line1" style="margin-top:10px">Baris 1 (teks utama)</label>
      <input id="line1" type="text" value="Halo, Bro." />

      <label for="line2" style="margin-top:10px">Baris 2 (pesan)</label>
      <textarea id="line2">Makasih udah selalu ada. Semoga hari ini penuh energi dan senyum. Kamu hebat.</textarea>

      <label style="margin-top:10px">Gaya warna — aksen</label>
      <div class="meta">
        <select id="accentPicker" style="flex:1">
          <option value="#2ec4b6">Sturdy Teal (default)</option>
          <option value="#f4a261">Warm Amber</option>
          <option value="#6ea8fe">Steel Blue</option>
          <option value="#b08cff">Deep Violet</option>
        </select>
        <div class="accent-preview" id="accentPreview" style="background:var(--accent)"></div>
      </div>

      <label style="margin-top:12px">Tampilan Judul</label>
      <input id="titleText" type="text" value="Kartu Ucapan" />

      <div style="margin-top:12px; display:flex; gap:8px">
        <button class="btn btn-show" id="applyBtn" style="flex:1">Terapkan</button>
        <button class="btn btn-reset" id="downloadBtn" style="width:120px">Download PNG</button>
      </div>

      <footer class="notice">
        Ingin musik? Kamu bisa tambahkan file audio ke Replit dan ubah variabel `audioSrc` di script.
      </footer>
    </aside>
  </div>

  <script>
    /* ========== CONFIG (ubah sesuai yang diinginkan) ========== */
    let audioSrc = ""; // contoh: "/audio/chime.mp3" jika ada file di Replit
    /* ========================================================= */

    // element refs
    const typedEl = document.getElementById('typed');
    const cursor = document.getElementById('cursor');
    const revealBtn = document.getElementById('revealBtn');
    const resetBtn = document.getElementById('resetBtn');
    const toNameInput = document.getElementById('toName');
    const line1Input = document.getElementById('line1');
    const line2Input = document.getElementById('line2');
    const accentPicker = document.getElementById('accentPicker');
    const accentPreview = document.getElementById('accentPreview');
    const titleText = document.getElementById('titleText');
    const applyBtn = document.getElementById('applyBtn');
    const downloadBtn = document.getElementById('downloadBtn');

    // apply initial accent preview
    accentPreview.style.background = accentPicker.value;

    // typing logic
    function buildMessage(){
      const to = toNameInput.value.trim();
      const l1 = line1Input.value.trim();
      const l2 = line2Input.value.trim();
      // construct message - keep simple lines
      const lines = [];
      if(l1) lines.push(l1);
      if(to) lines.push(`Untuk: ${to}`);
      if(l2) lines.push("");
      if(l2) lines.push(l2);
      return lines.join("\n");
    }

    // typing effect (async)
    function typeText(fullText, speed=30){
      typedEl.textContent = "";
      cursor.style.display = "inline-block";
      return new Promise(resolve=>{
        let i=0;
        const t = setInterval(()=>{
          typedEl.textContent = fullText.slice(0, i+1);
          i++;
          if(i >= fullText.length){
            clearInterval(t);
            // small pause then hide cursor
            setTimeout(()=>{ cursor.style.display = "none"; resolve(); }, 250);
          }
        }, speed);
      });
    }

    // reveal btn behavior
    revealBtn.addEventListener('click', async ()=>{
      revealBtn.disabled = true;
      resetBtn.disabled = true;

      const msg = buildMessage();
      await typeText(msg, 26);

      // play sound if available
      if(audioSrc){
        try{
          const a = new Audio(audioSrc);
          a.volume = 0.9;
          a.play().catch(()=>{/* ignore */});
        }catch(e){}
      }

      // confetti burst
      runConfetti();
      // enable reset after a bit
      setTimeout(()=>{ revealBtn.disabled = false; resetBtn.disabled = false; }, 800);
    });

    resetBtn.addEventListener('click', ()=>{
      typedEl.textContent = "";
      cursor.style.display = "inline-block";
    });

    // preview accent change
    accentPicker.addEventListener('change', (e)=>{
      const v = e.target.value;
      accentPreview.style.background = v;
      document.documentElement.style.setProperty('--accent', v);
    });

    // apply title
    applyBtn.addEventListener('click', ()=>{
      document.querySelector('.title').textContent = titleText.value || "Kartu Ucapan";
      // also update accent if changed
      document.documentElement.style.setProperty('--accent', accentPicker.value);
      accentPreview.style.background = accentPicker.value;
    });

    // download screenshot of left card (simple)
    downloadBtn.addEventListener('click', async ()=>{
      // use html2canvas-like technique: create new canvas and draw only the hero area
      const hero = document.querySelector('.hero');
      const rect = hero.getBoundingClientRect();
      // scale for better resolution
      const scale = 2;
      const canvas = document.createElement('canvas');
      canvas.width = rect.width * scale;
      canvas.height = rect.height * scale;
      const ctx = canvas.getContext('2d');

      // draw background color
      ctx.fillStyle = getComputedStyle(document.body).background;
      ctx.fillRect(0,0,canvas.width, canvas.height);

      // fallback: use SVG foreignObject to rasterize the hero node
      const data = new XMLSerializer().serializeToString(
        new XMLSerializer().serializeToString(document.documentElement)
      );

      // simple approach: let user use browser screenshot if fails
      alert('Fitur download sederhana — jika tidak menghasilkan gambar, silakan ambil screenshot layar (Full page screenshot recommended).');
      return;
    });

    // confetti implementation (simple particles)
    const confettiCanvas = document.getElementById('confettiCanvas');
    const cc = confettiCanvas.getContext('2d');
    let confettiParticles = [];
    function resizeCanvas(){
      confettiCanvas.width = window.innerWidth;
      confettiCanvas.height = window.innerHeight;
    }
    window.addEventListener('resize', resizeCanvas);
    resizeCanvas();

    function random(min,max){ return Math.random()*(max-min)+min; }
    function spawnConfettiBurst(x, y, count=40){
      for(let i=0;i<count;i++){
        confettiParticles.push({
          x:x,
          y:y,
          vx: random(-6,6),
          vy: random(-10,-3),
          ang: random(0,360),
          spin: random(-0.2,0.2),
          size: random(6,12),
          life: random(60,120),
          color: (i%2===0) ? getComputedStyle(document.documentElement).getPropertyValue('--accent').trim() : getComputedStyle(document.documentElement).getPropertyValue('--accent-2').trim()
        });
      }
    }

    function runConfetti(){
      // spawn from center-top-ish
      spawnConfettiBurst(window.innerWidth*0.5, window.innerHeight*0.35, 60);
      animConfetti();
    }

    let confettiAnimId = null;
    function animConfetti(){
      if(confettiAnimId) cancelAnimationFrame(confettiAnimId);
      function loop(){
        cc.clearRect(0,0,confettiCanvas.width,confettiCanvas.height);
        for(let i = confettiParticles.length-1; i>=0; i--){
          const p = confettiParticles[i];
          p.vy += 0.25; // gravity
          p.x += p.vx;
          p.y += p.vy;
          p.ang += p.spin;
          p.life -= 1;
          // draw rectangle rotated
          cc.save();
          cc.translate(p.x, p.y);
          cc.rotate(p.ang);
          cc.fillStyle = p.color || '#2ec4b6';
          cc.fillRect(-p.size/2, -p.size/2, p.size, p.size);
          cc.restore();
          if(p.y > confettiCanvas.height + 50 || p.life <= 0){
            confettiParticles.splice(i,1);
          }
        }
        if(confettiParticles.length>0){
          confettiAnimId = requestAnimationFrame(loop);
        } else {
          cancelAnimationFrame(confettiAnimId);
          confettiAnimId = null;
          cc.clearRect(0,0,confettiCanvas.width,confettiCanvas.height);
        }
      }
      animConfetti();
    }

    // initial state
    cursor.style.display = "inline-block";

    // small: set accent-2 CSS var from selected color (compute a warm alternative)
    (function setAccent2Var(){
      document.documentElement.style.setProperty('--accent', accentPicker.value);
      // a second accent
      document.documentElement.style.setProperty('--accent-2', '#f4a261');
    })();

    // allow Enter key to trigger reveal when focus in fields
    [toNameInput, line1Input, line2Input].forEach(el=>{
      el.addEventListener('keydown', e=>{
        if(e.key === "Enter" && !e.shiftKey){
          e.preventDefault();
          revealBtn.click();
        }
      });
    });

    // small accessibility: focus first
    toNameInput.focus();
  </script>
</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Brad Levels Up — 30th Birthday Bowling Bash</title>
  <style>
    :root{
      --bg:#0b1020;
      --panel:#121933;
      --panel-2:#0f1530;
      --line:#29345f;
      --text:#f8fafc;
      --muted:#b8c2e0;
      --yellow:#ffd84d;
      --pink:#ff5db1;
      --cyan:#45e6ff;
      --green:#6dff8b;
      --shadow:0 24px 60px rgba(0,0,0,.4);
    }

    *{box-sizing:border-box}
    html,body{margin:0;padding:0}
    body{
      font-family: Inter, Arial, sans-serif;
      color:var(--text);
      min-height:100vh;
      background:
        radial-gradient(circle at 15% 10%, rgba(69,230,255,.14), transparent 20%),
        radial-gradient(circle at 85% 15%, rgba(255,93,177,.16), transparent 20%),
        radial-gradient(circle at 50% 100%, rgba(255,216,77,.12), transparent 30%),
        linear-gradient(180deg, #0a0f1f, #0f1731 55%, #08101f);
      overflow-x:hidden;
    }

    .grid-bg{
      position:fixed;
      inset:0;
      pointer-events:none;
      background-image:
        linear-gradient(rgba(69,230,255,.08) 1px, transparent 1px),
        linear-gradient(90deg, rgba(69,230,255,.08) 1px, transparent 1px);
      background-size: 32px 32px;
      mask-image: linear-gradient(to bottom, transparent, rgba(0,0,0,.7) 18%, rgba(0,0,0,.9) 70%, transparent);
      opacity:.45;
    }

    .wrap{
      max-width:1100px;
      margin:0 auto;
      padding:28px 20px 40px;
      position:relative;
      z-index:1;
    }

    .hero{
      position:relative;
      overflow:hidden;
      background:linear-gradient(180deg, rgba(18,25,51,.92), rgba(12,17,36,.92));
      border:1px solid rgba(69,230,255,.18);
      border-radius:28px;
      padding:28px;
      box-shadow:var(--shadow);
    }

    .hero::before{
      content:"";
      position:absolute;
      inset:0;
      background:
        linear-gradient(120deg, transparent 0 30%, rgba(255,255,255,.05) 48%, transparent 52% 100%);
      transform:translateX(-120%);
      animation:shine 7s linear infinite;
      pointer-events:none;
    }

    @keyframes shine{
      to{transform:translateX(120%)}
    }

    .badge-row{
      display:flex;
      flex-wrap:wrap;
      gap:10px;
      margin-bottom:16px;
    }

    .badge{
      border:1px solid rgba(255,255,255,.12);
      background:rgba(255,255,255,.05);
      padding:9px 14px;
      border-radius:999px;
      font-weight:800;
      font-size:.85rem;
      letter-spacing:.04em;
      color:var(--yellow);
      text-transform:uppercase;
    }

    .hero-grid{
      display:grid;
      grid-template-columns: 1.2fr .8fr;
      gap:20px;
      align-items:center;
    }

    @media (max-width: 880px){
      .hero-grid,
      .main-grid{
        grid-template-columns:1fr !important;
      }
    }

    h1{
      margin:0 0 12px;
      font-size:clamp(2.4rem, 6vw, 4.6rem);
      line-height:.93;
      letter-spacing:-.04em;
    }

    .gradient{
      background:linear-gradient(90deg, var(--yellow), var(--pink), var(--cyan));
      -webkit-background-clip:text;
      background-clip:text;
      color:transparent;
    }

    .sub{
      max-width:690px;
      color:var(--muted);
      line-height:1.65;
      font-size:1.05rem;
      margin:0;
    }

    .pixel-card{
      background:linear-gradient(180deg, rgba(255,255,255,.04), rgba(255,255,255,.02));
      border:1px solid rgba(255,255,255,.1);
      border-radius:24px;
      padding:18px;
      position:relative;
    }

    .xp-wrap{
      margin-top:10px;
    }

    .xp-label{
      display:flex;
      justify-content:space-between;
      font-size:.9rem;
      color:var(--muted);
      margin-bottom:8px;
      font-weight:700;
    }

    .xp-bar{
      height:20px;
      border-radius:999px;
      background:#09101f;
      border:1px solid rgba(255,255,255,.08);
      overflow:hidden;
      position:relative;
    }

    .xp-fill{
      height:100%;
      width:92%;
      background:linear-gradient(90deg, var(--green), var(--cyan), var(--pink), var(--yellow));
      box-shadow:0 0 20px rgba(69,230,255,.25);
      position:relative;
    }

    .xp-fill::after{
      content:"";
      position:absolute;
      inset:0;
      background:linear-gradient(90deg, transparent, rgba(255,255,255,.28), transparent);
      transform:translateX(-100%);
      animation:shine 2.8s linear infinite;
    }

    .stat-grid{
      display:grid;
      grid-template-columns: repeat(2, 1fr);
      gap:12px;
      margin-top:14px;
    }

    .stat{
      background:rgba(255,255,255,.04);
      border:1px solid rgba(255,255,255,.08);
      border-radius:18px;
      padding:14px;
    }

    .stat .k{
      color:var(--muted);
      font-size:.82rem;
      text-transform:uppercase;
      letter-spacing:.08em;
      font-weight:800;
    }

    .stat .v{
      font-size:1.25rem;
      font-weight:900;
      margin-top:5px;
    }

    .main-grid{
      display:grid;
      grid-template-columns: .92fr 1.08fr;
      gap:22px;
      margin-top:22px;
    }

    .card{
      background:linear-gradient(180deg, rgba(18,25,51,.94), rgba(13,18,38,.94));
      border:1px solid rgba(255,255,255,.08);
      border-radius:26px;
      padding:22px;
      box-shadow:var(--shadow);
    }

    h2{
      margin:0 0 14px;
      font-size:1.35rem;
      letter-spacing:-.02em;
    }

    .quest-list{
      display:grid;
      gap:12px;
    }

    .quest{
      display:grid;
      grid-template-columns:110px 1fr;
      gap:12px;
      padding:12px 0;
      border-bottom:1px solid rgba(255,255,255,.08);
    }

    .quest:last-child{border-bottom:none}

    .label{
      color:var(--cyan);
      font-weight:900;
      font-size:.8rem;
      letter-spacing:.08em;
      text-transform:uppercase;
      padding-top:3px;
    }

    .value{
      color:var(--text);
      line-height:1.55;
    }

    .note{
      margin-top:12px;
      color:var(--muted);
      line-height:1.65;
      font-size:.95rem;
    }

    .cta-row{
      display:flex;
      gap:10px;
      flex-wrap:wrap;
      margin-top:18px;
    }

    button, a.btn{
      border:none;
      text-decoration:none;
      cursor:pointer;
      border-radius:999px;
      padding:13px 18px;
      font-weight:900;
      letter-spacing:.02em;
      transition:transform .15s ease, opacity .15s ease;
      display:inline-flex;
      align-items:center;
      justify-content:center;
    }

    button:hover, a.btn:hover{transform:translateY(-1px)}
    .primary{
      color:#08101f;
      background:linear-gradient(90deg, var(--yellow), var(--pink));
      box-shadow:0 10px 30px rgba(255,93,177,.2);
    }
    .ghost{
      color:var(--text);
      background:rgba(255,255,255,.05);
      border:1px solid rgba(255,255,255,.1);
    }

    .tiny{
      margin-top:10px;
      color:var(--muted);
      font-size:.9rem;
      line-height:1.55;
    }

    .game-note{
      color:var(--muted);
      line-height:1.6;
      margin-top:-2px;
      margin-bottom:14px;
    }

    .game-shell{
      background:
        linear-gradient(180deg, rgba(255,255,255,.03), rgba(255,255,255,.015));
      border:1px solid rgba(255,255,255,.08);
      border-radius:22px;
      padding:16px;
    }

    .hud{
      display:flex;
      gap:10px;
      flex-wrap:wrap;
      justify-content:space-between;
      font-weight:800;
      margin-bottom:12px;
      color:#fff6d0;
    }

    .hud-pill{
      padding:8px 12px;
      border-radius:999px;
      background:rgba(255,255,255,.05);
      border:1px solid rgba(255,255,255,.08);
    }

    .lane{
      position:relative;
      width:100%;
      aspect-ratio:8 / 10;
      max-height:510px;
      border-radius:22px;
      overflow:hidden;
      border:2px solid rgba(69,230,255,.18);
      background:
        linear-gradient(to top, rgba(8,16,31,.96), rgba(8,16,31,.35) 24%, transparent 24%),
        linear-gradient(to right,
          #5b3214 0%, #9a5e23 9%, #dfa567 18%, #f9cb93 28%,
          #ebb983 38%, #dfa567 50%, #ebb983 62%, #f9cb93 72%,
          #dfa567 82%, #9a5e23 91%, #5b3214 100%);
      box-shadow: inset 0 0 0 6px rgba(255,255,255,.04), 0 0 30px rgba(69,230,255,.08);
    }

    .lane::before{
      content:"";
      position:absolute;
      inset:0;
      background:
        linear-gradient(180deg, rgba(69,230,255,.12), transparent 18%),
        radial-gradient(circle at 50% 16%, rgba(255,255,255,.18), transparent 22%);
      pointer-events:none;
    }

    .scoreboard{
      position:absolute;
      inset:14px 14px auto 14px;
      display:flex;
      justify-content:space-between;
      align-items:center;
      gap:10px;
      font-weight:900;
      text-transform:uppercase;
      letter-spacing:.08em;
      z-index:3;
      font-size:.82rem;
    }

    .scoreboard span{
      padding:8px 10px;
      background:rgba(8,16,31,.76);
      border:1px solid rgba(255,255,255,.08);
      border-radius:999px;
      color:var(--yellow);
      backdrop-filter: blur(6px);
    }

    .pins{
      position:absolute;
      top:12%;
      left:50%;
      transform:translateX(-50%);
      width:min(29%, 155px);
      display:grid;
      grid-template-columns: repeat(4, 1fr);
      row-gap:8px;
      justify-items:center;
      z-index:2;
      pointer-events:none;
    }

    .pin{
      width:18px;
      height:35px;
      border-radius:12px 12px 9px 9px;
      background:linear-gradient(180deg, #fff, #e7ebf5);
      position:relative;
      box-shadow:0 4px 8px rgba(0,0,0,.25);
      transition:transform .55s ease, opacity .45s ease;
    }

    .pin::after{
      content:"";
      position:absolute;
      left:1px; right:1px;
      top:10px;
      height:5px;
      background:linear-gradient(90deg, var(--pink), #ff8ad0);
      border-radius:4px;
    }

    .pin.hidden{
      opacity:0;
      transform:translateY(18px) rotate(38deg) scale(.82);
    }

    .r1{grid-column:2 / span 1}
    .r2a{grid-column:2 / span 1}
    .r2b{grid-column:3 / span 1}
    .r3a{grid-column:1 / span 1}
    .r3b{grid-column:2 / span 1}
    .r3c{grid-column:3 / span 1}
    .r4a{grid-column:1 / span 1}
    .r4b{grid-column:2 / span 1}
    .r4c{grid-column:3 / span 1}
    .r4d{grid-column:4 / span 1}

    .aim{
      position:absolute;
      left:50%;
      bottom:10%;
      width:3px;
      height:66%;
      background:linear-gradient(180deg, rgba(69,230,255,.15), rgba(69,230,255,.95), rgba(69,230,255,0));
      transform-origin: bottom center;
      transform:translateX(-50%) rotate(0deg);
      pointer-events:none;
      z-index:2;
      box-shadow:0 0 12px rgba(69,230,255,.4);
    }

    .ball{
      position:absolute;
      width:44px;
      height:44px;
      border-radius:50%;
      left:50%;
      bottom:8%;
      transform:translateX(-50%);
      background:
        radial-gradient(circle at 30% 30%, rgba(255,255,255,.4), transparent 18%),
        linear-gradient(135deg, var(--pink), #9146ff 55%, var(--cyan));
      box-shadow:0 12px 26px rgba(0,0,0,.34), 0 0 16px rgba(69,230,255,.15);
      z-index:2;
      transition:left .2s ease;
    }

    .ball::before, .ball::after, .finger{
      content:"";
      position:absolute;
      width:6px; height:6px;
      border-radius:50%;
      background:rgba(0,0,0,.35);
    }
    .ball::before{top:10px; left:12px}
    .ball::after{top:16px; left:21px}
    .finger{top:22px; left:14px}

    .foul{
      position:absolute;
      left:0; right:0;
      bottom:18%;
      height:4px;
      background:linear-gradient(90deg, transparent, rgba(255,255,255,.9), transparent);
    }

    .controls{
      margin-top:14px;
      display:grid;
      gap:10px;
    }

    input[type="range"]{
      width:100%;
      accent-color: var(--yellow);
    }

    .result{
      min-height:34px;
      margin-top:6px;
      font-weight:900;
      color:var(--yellow);
      font-size:1.05rem;
    }

    .footer{
      text-align:center;
      color:var(--muted);
      font-size:.92rem;
      margin-top:18px;
      line-height:1.6;
    }

    .sparkle{
      position:fixed;
      inset:0;
      pointer-events:none;
      overflow:hidden;
      z-index:5;
    }

    .confetti{
      position:absolute;
      top:-20px;
      width:10px;
      height:16px;
      opacity:.95;
      animation:fall linear forwards;
    }

    .levelup{
      position:absolute;
      left:50%;
      top:48%;
      transform:translate(-50%, -50%) scale(.7);
      font-size:clamp(1.5rem, 4vw, 2.5rem);
      font-weight:1000;
      letter-spacing:.06em;
      text-transform:uppercase;
      color:var(--yellow);
      text-shadow:0 0 18px rgba(255,216,77,.45);
      opacity:0;
      z-index:4;
      pointer-events:none;
    }

    .levelup.show{
      animation:pop 1.25s ease forwards;
    }

    @keyframes pop{
      0%{opacity:0; transform:translate(-50%, -40%) scale(.7)}
      20%{opacity:1; transform:translate(-50%, -50%) scale(1.05)}
      80%{opacity:1}
      100%{opacity:0; transform:translate(-50%, -58%) scale(1)}
    }

    @keyframes fall{
      to{
        transform:translateY(110vh) rotate(560deg);
      }
    }

    @keyframes roll{
      0%{ transform:translateX(-50%) translateY(0) scale(1) rotate(0deg); }
      100%{ transform:translateX(calc(-50% + var(--drift))) translateY(calc(-1 * var(--distance))) scale(.5) rotate(720deg); }
    }
  </style>
</head>
<body>
  <div class="grid-bg"></div>

  <div class="wrap">
    <section class="hero">
      <div class="badge-row">
        <div class="badge">Main quest unlocked</div>
        <div class="badge">Level 30</div>
        <div class="badge">Bowling edition</div>
      </div>

      <div class="hero-grid">
        <div>
          <h1>Brad is <span class="gradient">Leveling Up</span><br>to 30 🎳</h1>
          <p class="sub">
            Join us for a birthday bowling bash in honor of Brad hitting Level 30.
            Expect bowling, snacks, drinks, good people, and elite birthday energy.
            Before you RSVP, take your shot in the mini game and see if you’ve got high-score behavior.
          </p>
        </div>

        <div class="pixel-card">
          <div style="font-weight:1000; font-size:1.05rem; color:var(--yellow);">Birthday Player Card</div>
          <div class="xp-wrap">
            <div class="xp-label">
              <span>XP Progress</span>
              <span>29 ➜ 30</span>
            </div>
            <div class="xp-bar"><div class="xp-fill"></div></div>
          </div>

          <div class="stat-grid">
            <div class="stat">
              <div class="k">Class</div>
              <div class="v">Birthday Boy</div>
            </div>
            <div class="stat">
              <div class="k">Special Skill</div>
              <div class="v">Drinking and Knowing Things</div>
            </div>
            <div class="stat">
              <div class="k">Buffs</div>
              <div class="v">Snacks + Friends</div>
            </div>
            <div class="stat">
              <div class="k">Boss Battle</div>
              <div class="v">Turning 30</div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="main-grid">
      <div class="card">
        <h2>Quest Details</h2>
        <div class="quest-list">
          <div class="quest">
            <div class="label">Date</div>
            <div class="value" id="party-date">Saturday, April 11, 2026</div>
          </div>
          <div class="quest">
            <div class="label">Time</div>
            <div class="value" id="party-time">5:00 PM</div>
          </div>
          <div class="quest">
            <div class="label">Location</div>
            <div class="value" id="party-location">Railroad and Strikers at Angel of the Winds Casino</div>
          </div>
          <div class="quest">
            <div class="label">Objective</div>
            <div class="value">Celebrate Brad, bowl a few frames, eat good food, and generally be iconic.</div>
          </div>
          <div class="quest">
            <div class="label">RSVP By</div>
            <div class="value" id="rsvp-date">April 3, 2026</div>
          </div>
        </div>

        <p class="note">We will be eating an early dinner at Railroad at 3:00 before bowling at 5:00pm.  We would love you to join us at Railroad before bowling.
          Bowling is $10/person.  If you do want to bowl, you can venmo Brad @Bradley-Jarvensivu.
        </p>

        <div class="cta-row">
          
        </div>
        <div class="tiny" id="copyStatus"></div>
      </div>

      <div class="card">
        <h2>Bonus Round: Birthday Bowling</h2>
        <p class="game-note">
          Adjust your aim and power, then roll. Throw a strike and trigger the Level Up animation.
        </p>

        <div class="game-shell">
          <div class="hud">
            <div class="hud-pill">Aim: <span id="aimValue">0°</span></div>
            <div class="hud-pill">Power: <span id="powerValue">74%</span></div>
            <div class="hud-pill">High Score: <span id="highScore">0</span></div>
          </div>

          <div class="lane" id="lane">
            <div class="scoreboard">
              <span>Player 1: Guest</span>
              <span>Final Boss: Pins</span>
            </div>

            <div class="pins" id="pins">
              <div class="pin r1"></div>
              <div class="pin r2a"></div>
              <div class="pin r2b"></div>
              <div class="pin r3a"></div>
              <div class="pin r3b"></div>
              <div class="pin r3c"></div>
              <div class="pin r4a"></div>
              <div class="pin r4b"></div>
              <div class="pin r4c"></div>
              <div class="pin r4d"></div>
            </div>

            <div class="aim" id="aimLine"></div>
            <div class="ball" id="ball"><div class="finger"></div></div>
            <div class="foul"></div>
            <div class="levelup" id="levelUpFlash">LEVEL UP!</div>
          </div>

          <div class="controls">
            <label>
              <div class="tiny">Aim left / right</div>
              <input id="aimSlider" type="range" min="-32" max="32" value="0" />
            </label>
            <label>
              <div class="tiny">Power</div>
              <input id="powerSlider" type="range" min="40" max="100" value="74" />
            </label>

            <div class="cta-row" style="margin-top:0;">
              <button class="primary" id="rollBtn" type="button">Roll for Glory</button>
              <button class="ghost" id="resetBtn" type="button">Reset Pins</button>
            </div>
            <div class="result" id="result">Can you earn birthday bragging rights?</div>
          </div>
        </div>
      </div>
    </section>

    <div class="footer">
      One-file invite page, easy to host anywhere as a link.<br>
      Great for GitHub Pages, Netlify Drop, or any simple website host.
    </div>
  </div>

  <div class="sparkle" id="sparkle"></div>

  <script>
    const aimSlider = document.getElementById('aimSlider');
    const powerSlider = document.getElementById('powerSlider');
    const aimValue = document.getElementById('aimValue');
    const powerValue = document.getElementById('powerValue');
    const aimLine = document.getElementById('aimLine');
    const ball = document.getElementById('ball');
    const rollBtn = document.getElementById('rollBtn');
    const resetBtn = document.getElementById('resetBtn');
    const result = document.getElementById('result');
    const pins = Array.from(document.querySelectorAll('.pin'));
    const highScoreEl = document.getElementById('highScore');
    const sparkle = document.getElementById('sparkle');
    const levelUpFlash = document.getElementById('levelUpFlash');
    const copyBtn = document.getElementById('copyBtn');
    const copyStatus = document.getElementById('copyStatus');

    let rolling = false;
    let highScore = Number(localStorage.getItem('bradLevel30BowlingHighScore') || 0);
    highScoreEl.textContent = highScore;

    function updateAim(){
      const angle = Number(aimSlider.value);
      const power = Number(powerSlider.value);
      aimValue.textContent = `${angle}°`;
      powerValue.textContent = `${power}%`;
      aimLine.style.transform = `translateX(-50%) rotate(${angle}deg)`;
      ball.style.left = `calc(50% + ${angle * 0.7}px)`;
    }

    function randomBetween(min, max){
      return Math.random() * (max - min) + min;
    }

    function confettiBurst(){
      const colors = ['#ffd84d', '#ff5db1', '#45e6ff', '#6dff8b', '#ffffff'];
      for(let i = 0; i < 82; i++){
        const c = document.createElement('div');
        c.className = 'confetti';
        c.style.left = `${Math.random() * 100}vw`;
        c.style.background = colors[Math.floor(Math.random() * colors.length)];
        c.style.animationDuration = `${randomBetween(1.9, 3.5)}s`;
        c.style.transform = `rotate(${Math.random()*360}deg)`;
        sparkle.appendChild(c);
        setTimeout(() => c.remove(), 3800);
      }
    }

    function levelUp(){
      levelUpFlash.classList.remove('show');
      levelUpFlash.offsetHeight;
      levelUpFlash.classList.add('show');
      confettiBurst();
    }

    function resetPins(){
      pins.forEach(pin => pin.classList.remove('hidden'));
      result.textContent = 'Can you earn birthday bragging rights?';
      ball.style.animation = 'none';
      ball.style.removeProperty('--drift');
      ball.style.removeProperty('--distance');
      ball.offsetHeight;
      rolling = false;
    }

    function knockPins(count){
      const shuffled = [...pins].sort(() => Math.random() - 0.5);
      shuffled.slice(0, count).forEach((pin, index) => {
        setTimeout(() => pin.classList.add('hidden'), index * 55);
      });
    }

    function scoreRoll(angle, power){
      const aimPenalty = Math.abs(angle) * 0.24;
      const powerBonus = (power - 40) * 0.1;
      const randomness = randomBetween(-1.8, 2.2);
      let score = Math.round(6 + powerBonus - aimPenalty + randomness);

      if (Math.abs(angle) <= 5 && power >= 72 && Math.random() > 0.32) {
        score = Math.max(score, 10);
      }

      return Math.max(0, Math.min(10, score));
    }

    function rollBall(){
      if (rolling) return;
      rolling = true;

      pins.forEach(pin => pin.classList.remove('hidden'));

      const angle = Number(aimSlider.value);
      const power = Number(powerSlider.value);
      const drift = angle * 2.2;
      const distance = 290 + (power * 1.75);

      ball.style.setProperty('--drift', `${drift}px`);
      ball.style.setProperty('--distance', `${distance}px`);
      ball.style.animation = `roll ${0.9 + (100 - power) / 80}s ease-out forwards`;

      const knocked = scoreRoll(angle, power);

      setTimeout(() => {
        knockPins(knocked);

        let message = '';
        if (knocked === 10){
          message = '🎉 STRIKE! You just unlocked Level 30 energy.';
          levelUp();
        } else if (knocked >= 8){
          message = `⚡ ${knocked} pins! Rare loot drop behavior.`;
        } else if (knocked >= 5){
          message = `🎳 ${knocked} pins! Solid side quest success.`;
        } else if (knocked >= 1){
          message = `😂 ${knocked} pins. Still invited, obviously.`;
        } else {
          message = `🫠 Critical miss. Good thing this party has snacks.`;
        }

        result.textContent = message;

        if (knocked > highScore){
          highScore = knocked;
          localStorage.setItem('bradLevel30BowlingHighScore', highScore);
          highScoreEl.textContent = highScore;
        }

        setTimeout(() => {
          rolling = false;
        }, 650);
      }, 900);
    }

    copyBtn.addEventListener('click', async () => {
      const text = `🎳 You’re invited: Brad is leveling up to 30!\n\nJoin us for Brad’s 30th Birthday Bowling Bash.\nSaturday, April 11, 2026 at 6:30 PM\nRiverside Lanes · Anacortes, WA\n\nOpen the invite, play the mini bowling game, and RSVP here:\nhttps://example.com`;
      try{
        await navigator.clipboard.writeText(text);
        copyStatus.textContent = 'Invite text copied — just swap in your real link.';
      } catch {
        copyStatus.textContent = 'Clipboard access was blocked here, but the invite text is built into the code.';
      }
    });

    aimSlider.addEventListener('input', updateAim);
    powerSlider.addEventListener('input', updateAim);
    rollBtn.addEventListener('click', rollBall);
    resetBtn.addEventListener('click', resetPins);

    updateAim();
    resetPins();
  </script>
</body>
</html>

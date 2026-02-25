<!DOCTYPE html>
<html lang="ro">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Windsor Castle Fire 1992</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700;900&family=Inter:wght@300;400;600;700&display=swap');
  
  * { margin: 0; padding: 0; box-sizing: border-box; }
  
  body {
    font-family: 'Inter', sans-serif;
    background: #0a0a0a;
    color: #fff;
    overflow: hidden;
    height: 100vh;
    width: 100vw;
  }

  .presentation {
    width: 100%;
    height: 100vh;
    position: relative;
  }

  .slide {
    position: absolute;
    width: 100%;
    height: 100%;
    display: none;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 40px;
    opacity: 0;
    transition: opacity 0.6s ease;
  }

  .slide.active {
    display: flex;
    opacity: 1;
  }

  /* SLIDE 1 - COVER */
  .slide-1 {
    background: #0a0a0a;
    position: relative;
    overflow: hidden;
  }

  .fire-bg {
    position: absolute;
    inset: 0;
    background: radial-gradient(ellipse at 50% 80%, #ff4400 0%, #ff2200 20%, #8b0000 50%, #0a0a0a 80%);
    opacity: 0.6;
  }

  .fire-particles {
    position: absolute;
    inset: 0;
    overflow: hidden;
  }

  .particle {
    position: absolute;
    bottom: 0;
    border-radius: 50% 50% 20% 20%;
    animation: rise linear infinite;
    opacity: 0;
  }

  @keyframes rise {
    0% { transform: translateY(0) scale(1) rotate(0deg); opacity: 0.8; }
    100% { transform: translateY(-100vh) scale(0.2) rotate(20deg); opacity: 0; }
  }

  .slide-1 .content {
    position: relative;
    z-index: 2;
    text-align: center;
  }

  .crown {
    font-size: 60px;
    margin-bottom: 10px;
    filter: drop-shadow(0 0 20px #ffaa00);
    animation: pulse 2s ease-in-out infinite;
  }

  @keyframes pulse { 0%,100%{transform:scale(1);} 50%{transform:scale(1.1);} }

  .slide-1 h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(32px, 5vw, 64px);
    font-weight: 900;
    line-height: 1.1;
    background: linear-gradient(135deg, #ffcc00, #ff6600, #ff2200);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    text-shadow: none;
    margin-bottom: 8px;
    letter-spacing: -1px;
  }

  .slide-1 .year {
    font-size: clamp(60px, 10vw, 120px);
    font-family: 'Playfair Display', serif;
    font-weight: 900;
    color: rgba(255,255,255,0.05);
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    white-space: nowrap;
    z-index: 1;
  }

  .slide-1 .subtitle {
    font-size: clamp(14px, 2vw, 20px);
    color: #ffcc88;
    letter-spacing: 4px;
    text-transform: uppercase;
    margin-bottom: 30px;
  }

  .authors-box {
    display: inline-flex;
    gap: 20px;
    background: rgba(255,255,255,0.08);
    border: 1px solid rgba(255,150,0,0.4);
    padding: 14px 28px;
    border-radius: 4px;
    backdrop-filter: blur(10px);
  }

  .authors-box .author {
    font-size: 13px;
    color: #ffddaa;
    text-transform: uppercase;
    letter-spacing: 2px;
  }

  /* SLIDE 2 */
  .slide-2 { background: linear-gradient(135deg, #0d0d0d 0%, #1a0800 100%); }

  .two-col {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 30px;
    width: 100%;
    max-width: 1100px;
  }

  .info-card {
    background: rgba(255,255,255,0.04);
    border: 1px solid rgba(255,100,0,0.3);
    border-radius: 8px;
    padding: 28px;
    position: relative;
    overflow: hidden;
  }

  .info-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 4px; height: 100%;
    background: linear-gradient(to bottom, #ff6600, #ff2200);
  }

  .card-icon { font-size: 32px; margin-bottom: 12px; }
  .card-title {
    font-size: 11px;
    text-transform: uppercase;
    letter-spacing: 3px;
    color: #ff6600;
    margin-bottom: 14px;
  }

  .card-content p {
    font-size: 14px;
    color: #ccc;
    line-height: 1.7;
    margin-bottom: 8px;
  }

  .highlight { color: #ffcc00; font-weight: 700; }

  .timeline-item {
    display: flex;
    gap: 12px;
    margin-bottom: 12px;
    align-items: flex-start;
  }

  .tl-dot {
    width: 10px; height: 10px;
    background: #ff4400;
    border-radius: 50%;
    margin-top: 5px;
    flex-shrink: 0;
    box-shadow: 0 0 8px #ff4400;
  }

  .tl-text { font-size: 13px; color: #ccc; line-height: 1.5; }
  .tl-year { color: #ffcc00; font-weight: 700; display: block; }

  /* SLIDE 3 */
  .slide-3 { background: linear-gradient(135deg, #0d0d0d 0%, #1a0000 100%); }

  .damage-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
    max-width: 1000px;
    width: 100%;
    margin-top: 20px;
  }

  .damage-card {
    background: rgba(255,0,0,0.06);
    border: 1px solid rgba(255,50,0,0.25);
    border-radius: 8px;
    padding: 22px;
    text-align: center;
    transition: transform 0.3s;
  }

  .damage-card:hover { transform: translateY(-4px); }
  .damage-icon { font-size: 36px; margin-bottom: 10px; }
  .damage-title { font-size: 13px; color: #ff6600; text-transform: uppercase; letter-spacing: 2px; margin-bottom: 8px; }
  .damage-text { font-size: 13px; color: #aaa; line-height: 1.6; }

  .stat-row {
    display: flex;
    gap: 20px;
    margin-bottom: 24px;
    max-width: 1000px;
    width: 100%;
  }

  .stat-box {
    flex: 1;
    background: rgba(255,100,0,0.1);
    border: 1px solid #ff4400;
    border-radius: 6px;
    padding: 16px;
    text-align: center;
  }

  .stat-num {
    font-family: 'Playfair Display', serif;
    font-size: 36px;
    color: #ff4400;
    font-weight: 900;
    display: block;
  }

  .stat-label { font-size: 11px; color: #999; text-transform: uppercase; letter-spacing: 2px; }

  /* SLIDE 4 */
  .slide-4 { background: linear-gradient(135deg, #0d0d0d 0%, #0d0800 100%); }

  .causes-list {
    max-width: 900px;
    width: 100%;
  }

  .cause-item {
    display: flex;
    gap: 20px;
    margin-bottom: 18px;
    background: rgba(255,255,255,0.03);
    border-radius: 8px;
    padding: 18px 22px;
    border-left: 3px solid #ff4400;
    align-items: center;
  }

  .cause-num {
    font-family: 'Playfair Display', serif;
    font-size: 28px;
    color: #ff4400;
    opacity: 0.5;
    font-weight: 900;
    flex-shrink: 0;
    width: 36px;
  }

  .cause-info h4 { font-size: 14px; color: #ffcc00; margin-bottom: 4px; text-transform: uppercase; letter-spacing: 1px; }
  .cause-info p { font-size: 13px; color: #aaa; line-height: 1.6; }

  /* SLIDE 5 */
  .slide-5 { background: linear-gradient(135deg, #0d0d0d, #00080d 100%); }

  .subjects-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 18px;
    max-width: 1000px;
    width: 100%;
    margin-top: 20px;
  }

  .subject-card {
    background: rgba(255,255,255,0.04);
    border: 1px solid rgba(100,150,255,0.2);
    border-radius: 8px;
    padding: 22px;
    display: flex;
    gap: 16px;
    align-items: flex-start;
  }

  .subject-icon { font-size: 28px; flex-shrink: 0; }
  .subject-name { font-size: 14px; color: #88aaff; text-transform: uppercase; letter-spacing: 1px; margin-bottom: 6px; font-weight: 700; }
  .subject-desc { font-size: 13px; color: #999; line-height: 1.6; }

  /* SLIDE 6 */
  .slide-6 { background: linear-gradient(135deg, #0d0d0d, #000d08); }

  .solutions-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 24px;
    max-width: 1050px;
    width: 100%;
    margin-top: 16px;
  }

  .sol-card {
    background: rgba(0,200,100,0.05);
    border: 1px solid rgba(0,200,100,0.2);
    border-radius: 8px;
    padding: 22px;
  }

  .sol-card.law {
    background: rgba(100,100,255,0.05);
    border-color: rgba(100,100,255,0.25);
  }

  .sol-title { font-size: 11px; text-transform: uppercase; letter-spacing: 3px; color: #00cc66; margin-bottom: 14px; }
  .sol-card.law .sol-title { color: #8888ff; }

  .sol-item { display: flex; gap: 10px; margin-bottom: 10px; align-items: flex-start; }
  .sol-dot { width: 6px; height: 6px; background: #00cc66; border-radius: 50%; margin-top: 6px; flex-shrink: 0; }
  .sol-card.law .sol-dot { background: #8888ff; }
  .sol-text { font-size: 13px; color: #aaa; line-height: 1.6; }

  /* SLIDE 7 */
  .slide-7 { background: linear-gradient(135deg, #0d0d0d, #0d0d00); }

  .legal-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 24px;
    max-width: 1050px;
    width: 100%;
    margin-top: 16px;
  }

  .legal-card {
    background: rgba(255,200,0,0.05);
    border: 1px solid rgba(255,200,0,0.2);
    border-radius: 8px;
    padding: 22px;
  }

  .legal-title { font-size: 11px; text-transform: uppercase; letter-spacing: 3px; color: #ffcc00; margin-bottom: 14px; }
  .article-box {
    background: rgba(255,200,0,0.08);
    border-radius: 6px;
    padding: 12px 16px;
    margin-bottom: 10px;
  }
  .article-num { font-size: 12px; color: #ffcc00; font-weight: 700; margin-bottom: 4px; }
  .article-text { font-size: 12px; color: #aaa; line-height: 1.5; }

  .example-card {
    background: rgba(255,150,0,0.06);
    border: 1px solid rgba(255,150,0,0.2);
    border-radius: 8px;
    padding: 18px;
    margin-bottom: 12px;
  }

  .ex-title { font-size: 13px; color: #ffaa00; font-weight: 700; margin-bottom: 6px; }
  .ex-text { font-size: 12px; color: #999; line-height: 1.6; }

  /* SLIDE 8 */
  .slide-8 { background: linear-gradient(135deg, #0d0d0d, #0a0a0a); }

  .sources-container {
    max-width: 850px;
    width: 100%;
    margin-top: 20px;
  }

  .source-item {
    display: flex;
    gap: 16px;
    padding: 14px 0;
    border-bottom: 1px solid rgba(255,255,255,0.06);
    align-items: flex-start;
  }

  .src-num {
    font-family: 'Playfair Display', serif;
    font-size: 20px;
    color: #ff4400;
    font-weight: 900;
    flex-shrink: 0;
    width: 28px;
  }

  .src-text { font-size: 13px; color: #999; line-height: 1.7; }
  .src-text a { color: #ff8844; text-decoration: none; }

  .final-tag {
    margin-top: 30px;
    text-align: center;
    font-size: 12px;
    color: #555;
    text-transform: uppercase;
    letter-spacing: 3px;
  }

  /* SHARED */
  .slide-header {
    text-align: center;
    margin-bottom: 30px;
  }

  .slide-num {
    font-size: 11px;
    color: #ff4400;
    text-transform: uppercase;
    letter-spacing: 4px;
    margin-bottom: 8px;
  }

  .slide-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(22px, 3.5vw, 40px);
    font-weight: 900;
    color: #fff;
  }

  .slide-title span { color: #ff4400; }

  /* NAV */
  .nav {
    position: fixed;
    bottom: 28px;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    align-items: center;
    gap: 16px;
    z-index: 100;
    background: rgba(0,0,0,0.6);
    backdrop-filter: blur(12px);
    border: 1px solid rgba(255,255,255,0.1);
    border-radius: 50px;
    padding: 10px 20px;
  }

  .nav-btn {
    background: none;
    border: 1px solid rgba(255,100,0,0.4);
    color: #ff6600;
    padding: 8px 18px;
    border-radius: 30px;
    cursor: pointer;
    font-size: 13px;
    font-family: 'Inter', sans-serif;
    transition: all 0.2s;
  }

  .nav-btn:hover { background: #ff4400; color: #fff; border-color: #ff4400; }
  .nav-btn:disabled { opacity: 0.3; cursor: default; }

  .nav-dots { display: flex; gap: 8px; }

  .dot {
    width: 8px; height: 8px;
    border-radius: 50%;
    background: rgba(255,255,255,0.2);
    cursor: pointer;
    transition: all 0.3s;
  }

  .dot.active { background: #ff4400; transform: scale(1.4); }

  .slide-counter { font-size: 12px; color: #666; min-width: 40px; text-align: center; }

  /* LOGO watermark */
  .watermark {
    position: fixed;
    top: 20px;
    right: 24px;
    font-size: 11px;
    color: rgba(255,100,0,0.35);
    text-transform: uppercase;
    letter-spacing: 3px;
    z-index: 100;
  }
</style>
</head>
<body>

<div class="watermark">Windsor · 1992</div>

<div class="presentation">

  <!-- SLIDE 1: COVER -->
  <div class="slide slide-1 active">
    <div class="fire-bg"></div>
    <div class="fire-particles" id="particles"></div>
    <div class="year">1992</div>
    <div class="content">
      <div class="crown">👑🔥</div>
      <div class="subtitle">Studiu de caz · Construcție avariată</div>
      <h1>Windsor Castle<br>Fire</h1>
      <p style="font-size:13px;color:#ff8844;letter-spacing:2px;text-transform:uppercase;margin:10px 0 24px;">20 noiembrie 1992 · Anglia, Marea Britanie</p>
      <div class="authors-box">
        <span class="author">⚑ Zastavnetchi Lucas</span>
        <span style="color:rgba(255,255,255,0.2)">|</span>
        <span class="author">⚑ Varvaruc Adrian</span>
      </div>
    </div>
  </div>

  <!-- SLIDE 2: DENUMIRE + DATE CRONOLOGICE -->
  <div class="slide slide-2">
    <div class="slide-header">
      <div class="slide-num">01 — 02</div>
      <div class="slide-title">Construcția avariată & <span>Cronologie</span></div>
    </div>
    <div class="two-col">
      <div class="info-card">
        <div class="card-icon">🏰</div>
        <div class="card-title">Denumirea Construcției</div>
        <div class="card-content">
          <p><span class="highlight">Windsor Castle</span> — una dintre cele mai vechi și mai mari castele locuite din lume.</p>
          <p>Construit în <span class="highlight">sec. XI</span>, de regele <span class="highlight">William Cuceritorul</span>.</p>
          <p>Reședința oficială a familiei regale britanice. Suprafață totală: <span class="highlight">~45.000 m²</span>.</p>
          <p>Clasificat ca <span class="highlight">Monument de Patrimoniu Mondial UNESCO</span>.</p>
        </div>
      </div>
      <div class="info-card">
        <div class="card-icon">📅</div>
        <div class="card-title">Date Cronologice</div>
        <div class="card-content">
          <div class="timeline-item"><div class="tl-dot"></div><div class="tl-text"><span class="tl-year">1070</span>Prima construcție — turn de lemn de William I</div></div>
          <div class="timeline-item"><div class="tl-dot"></div><div class="tl-text"><span class="tl-year">1165–1170</span>Reconstrucție în piatră (Henric II)</div></div>
          <div class="timeline-item"><div class="tl-dot"></div><div class="tl-text"><span class="tl-year">1820–1830</span>Extindere majoră — Arhitect Jeffry Wyatville</div></div>
          <div class="timeline-item"><div class="tl-dot"></div><div class="tl-text"><span class="tl-year">20 Nov 1992</span>🔥 Incendiu devastator — ora 11:33</div></div>
          <div class="timeline-item"><div class="tl-dot"></div><div class="tl-text"><span class="tl-year">1992–1997</span>Restaurare completă — £37 milioane</div></div>
        </div>
      </div>
    </div>
  </div>

  <!-- SLIDE 3: STAREA FIZICĂ -->
  <div class="slide slide-3">
    <div class="slide-header">
      <div class="slide-num">03</div>
      <div class="slide-title">Starea Fizică a <span>Construcției Avariate</span></div>
    </div>
    <div class="stat-row">
      <div class="stat-box"><span class="stat-num">9</span><span class="stat-label">Camere de stat distruse</span></div>
      <div class="stat-box"><span class="stat-num">100+</span><span class="stat-label">Camere avariate</span></div>
      <div class="stat-box"><span class="stat-num">~20%</span><span class="stat-label">Din castel afectat</span></div>
      <div class="stat-box"><span class="stat-num">15h</span><span class="stat-label">Durata incendiului</span></div>
    </div>
    <div class="damage-grid">
      <div class="damage-card">
        <div class="damage-icon">🏛️</div>
        <div class="damage-title">Capelă Regală</div>
        <div class="damage-text">St. George's Hall și Private Chapel — complet distruse. Structura acoperișului prăbușită.</div>
      </div>
      <div class="damage-card">
        <div class="damage-icon">🪟</div>
        <div class="damage-title">Ferestre & Vitralii</div>
        <div class="damage-text">Sute de ferestre istorice, inclusiv vitralii din sec. XIX — sparte sau topite de căldură.</div>
      </div>
      <div class="damage-card">
        <div class="damage-icon">🖼️</div>
        <div class="damage-title">Opere de Artă</div>
        <div class="damage-text">Tablouri, mobilier regal și artefacte istorice — deteriorate sau distruse definitiv.</div>
      </div>
      <div class="damage-card">
        <div class="damage-icon">🔥</div>
        <div class="damage-title">Structura de Lemn</div>
        <div class="damage-text">Grinde și planșee de lemn vechi de secole — carbonizate sau prăbușite complet.</div>
      </div>
      <div class="damage-card">
        <div class="damage-icon">💧</div>
        <div class="damage-title">Deteriorare prin Apă</div>
        <div class="damage-text">Apa folosită în stingere a provocat daune suplimentare în zone neafectate de flăcări.</div>
      </div>
      <div class="damage-card">
        <div class="damage-icon">🧱</div>
        <div class="damage-title">Zidărie Istorică</div>
        <div class="damage-text">Pereți din piatră medievală — crăpați și slăbiți structural din cauza șocului termic.</div>
      </div>
    </div>
  </div>

  <!-- SLIDE 4: CAUZE -->
  <div class="slide slide-4">
    <div class="slide-header">
      <div class="slide-num">04</div>
      <div class="slide-title">Cauzele Stării <span>Avariate</span></div>
    </div>
    <div class="causes-list">
      <div class="cause-item">
        <div class="cause-num">01</div>
        <div class="cause-info">
          <h4>🔌 Cauza directă — Scânteie electrică</h4>
          <p>Un reflector portabil plasat prea aproape de o perdea în <strong>Private Chapel</strong> a generat o scânteie care a aprins materialele textile. Incendiul s-a extins rapid la structura de lemn a acoperișului.</p>
        </div>
      </div>
      <div class="cause-item">
        <div class="cause-num">02</div>
        <div class="cause-info">
          <h4>🚫 Absența sistemelor moderne de protecție</h4>
          <p>Castelul nu dispunea de <strong>sprinklere automate</strong> sau sisteme moderne de detecție și suprimare a incendiilor în zonele afectate — o lacună critică pentru o clădire istorică de această anvergură.</p>
        </div>
      </div>
      <div class="cause-item">
        <div class="cause-num">03</div>
        <div class="cause-info">
          <h4>🏗️ Lucrări de renovare în desfășurare</h4>
          <p>Activitățile de restaurare în curs au implicat deplasarea sistemelor de detecție și a barierelor antiincendiu, reducând capacitatea de izolare a unui eventual focar de foc.</p>
        </div>
      </div>
      <div class="cause-item">
        <div class="cause-num">04</div>
        <div class="cause-info">
          <h4>🌬️ Propagare rapidă prin acoperiș</h4>
          <p>Structura de lemn veche, uscată, a acoperișului a acționat ca un <strong>conductor ideal</strong> pentru flăcări. Spațiile libere din podul clădirii au favorizat tirajul și extinderea pe orizontală a incendiului.</p>
        </div>
      </div>
    </div>
  </div>

  <!-- SLIDE 5: SUBIECȚI -->
  <div class="slide slide-5">
    <div class="slide-header">
      <div class="slide-num">05</div>
      <div class="slide-title">Subiecții & Structurile <span>Implicate</span></div>
    </div>
    <div class="subjects-grid">
      <div class="subject-card">
        <div class="subject-icon">👑</div>
        <div>
          <div class="subject-name">Casa Regală Britanică</div>
          <div class="subject-desc">Proprietarul castelului. Regina Elisabeta a II-a a urmărit personal operațiunile de stingere. Familia regală a suportat o parte din costurile de restaurare.</div>
        </div>
      </div>
      <div class="subject-card">
        <div class="subject-icon">🚒</div>
        <div>
          <div class="subject-name">Brigada de Pompieri Royal Berkshire</div>
          <div class="subject-desc">225 de pompieri mobilizați. Peste 39 de autospeciale implicate. Au luptat 15 ore pentru controlul incendiului folosind apă din râul Tamisa.</div>
        </div>
      </div>
      <div class="subject-card">
        <div class="subject-icon">🏛️</div>
        <div>
          <div class="subject-name">Guvernul Britanic / Ministerul Culturii</div>
          <div class="subject-desc">A finanțat restaurarea prin fonduri publice (dezbatere politică majoră). A supervizat procesul de reabilitare și conformarea cu standardele de patrimoniu.</div>
        </div>
      </div>
      <div class="subject-card">
        <div class="subject-icon">🏗️</div>
        <div>
          <div class="subject-name">Echipa de Restaurare & Arhitecți</div>
          <div class="subject-desc">Condusă de arhitectul <strong>Donald Insall Associates</strong>. Peste 1.500 de meșteșugari, conservatori și specialiști implicați în restaurarea de 5 ani.</div>
        </div>
      </div>
      <div class="subject-card">
        <div class="subject-icon">🎨</div>
        <div>
          <div class="subject-name">English Heritage & Conservatori</div>
          <div class="subject-desc">Responsabili de salvarea, catalogarea și restaurarea operelor de artă, mobilierului regal și obiectelor de patrimoniu afectate de foc și apă.</div>
        </div>
      </div>
      <div class="subject-card">
        <div class="subject-icon">📰</div>
        <div>
          <div class="subject-name">Opinia Publică & Presa</div>
          <div class="subject-desc">Dezbateri naționale privind cine ar trebui să plătească restaurarea. A dus la decizia Reginei de a deschide Palatul Buckingham publicului pentru a genera fonduri.</div>
        </div>
      </div>
    </div>
  </div>

  <!-- SLIDE 6: SOLUȚII + CERINȚE -->
  <div class="slide slide-6">
    <div class="slide-header">
      <div class="slide-num">06</div>
      <div class="slide-title">Soluții de Reabilitare & <span>Cerințe Încălcate</span></div>
    </div>
    <div class="solutions-grid">
      <div class="sol-card">
        <div class="sol-title">✅ Soluții de Reabilitare</div>
        <div class="sol-item"><div class="sol-dot"></div><div class="sol-text">Instalarea sistemelor de sprinklere automate în întregul castel (£37M investiți)</div></div>
        <div class="sol-item"><div class="sol-dot"></div><div class="sol-text">Refacerea acoperișului St. George's Hall cu lemn de stejar — tehnici tradiționale combinate cu materiale moderne ignifuge</div></div>
        <div class="sol-item"><div class="sol-dot"></div><div class="sol-text">Restaurarea capelei private în stil neo-gotic (arhitect Giles Downes) — proiect inovator apreciat internațional</div></div>
        <div class="sol-item"><div class="sol-dot"></div><div class="sol-text">Implementarea unui plan de urgență și protecție contra incendiilor actualizat, obligatoriu pentru toate clădirile de patrimoniu din UK</div></div>
        <div class="sol-item"><div class="sol-dot"></div><div class="sol-text">Compartimentare antiincendiu modernă integrată discret în structura istorică</div></div>
      </div>
      <div class="sol-card law">
        <div class="sol-title">⚖️ Cerințe Fundamentale Încălcate</div>
        <div class="sol-item"><div class="sol-dot"></div><div class="sol-text"><strong style="color:#aaf">Cerința A — Rezistență și Stabilitate:</strong> Structura din lemn a acoperișului nu oferea rezistență la foc adecvată</div></div>
        <div class="sol-item"><div class="sol-dot"></div><div class="sol-text"><strong style="color:#aaf">Cerința B — Securitate la Incendiu:</strong> Lipsa sprinklerelor, a compartimentării și a detecției automate — violarea directă a normelor de siguranță</div></div>
        <div class="sol-item"><div class="sol-dot"></div><div class="sol-text"><strong style="color:#aaf">Cerința C — Igienă și Mediu:</strong> Fumul toxic și cenușa au afectat mediul înconjurător și sănătatea populației din zonă</div></div>
        <div class="sol-item"><div class="sol-dot"></div><div class="sol-text"><strong style="color:#aaf">Cerința F — Economie de Energie:</strong> Instalațiile electrice improvizate pentru lucrările de renovare nu respectau normele tehnice</div></div>
      </div>
    </div>
  </div>

  <!-- SLIDE 7: LEGISLATIV + EXEMPLE -->
  <div class="slide slide-7">
    <div class="slide-header">
      <div class="slide-num">07</div>
      <div class="slide-title">Cadru Legislativ & <span>Cazuri Similare</span></div>
    </div>
    <div class="legal-grid">
      <div class="legal-card">
        <div class="legal-title">📜 Codul Penal al RM — Articole Aplicabile</div>
        <div class="article-box">
          <div class="article-num">Art. 197 CP RM — Distrugerea sau deteriorarea intenționată a bunurilor</div>
          <div class="article-text">Distrugerea sau deteriorarea bunurilor în proporții mari — pedepsită cu amendă sau închisoare până la 5 ani. Aplicabil în cazul neglijenței grave.</div>
        </div>
        <div class="article-box">
          <div class="article-num">Art. 298 CP RM — Încălcarea regulilor de securitate la incendii</div>
          <div class="article-text">Nerespectarea normelor de protecție contra incendiilor cu consecințe grave — pedepsită cu privare de libertate până la 3 ani.</div>
        </div>
        <div class="article-box">
          <div class="article-num">Art. 328 CP RM — Neglijența în serviciu</div>
          <div class="article-text">Neîndeplinirea atribuțiilor de serviciu, cu cauzarea de daune patrimoniale esențiale — pedepsită cu amendă sau muncă neremunerată.</div>
        </div>
      </div>
      <div class="legal-card" style="background:rgba(255,150,0,0.05);border-color:rgba(255,150,0,0.2);">
        <div class="legal-title" style="color:#ffaa00;">🔥 Cazuri Similare în Lume</div>
        <div class="example-card">
          <div class="ex-title">🇫🇷 Notre-Dame de Paris — 15 Aprilie 2019</div>
          <div class="ex-text">Incendiu provocat de scurtcircuit în timpul lucrărilor de renovare. Acoperișul și fleșa (spira) s-au prăbușit. Cauze similare: lucrări de construcție + echipamente electrice defecte + structură veche din lemn. Restaurare estimată: €700 milioane.</div>
        </div>
        <div class="example-card">
          <div class="ex-title">🇷🇺 Palatul de Iarnă (Hermitage) — Incendiu 1837</div>
          <div class="ex-text">Incendiu de 3 zile care a distrus apartamentele imperiale. Cauze: instalații de ventilație defectuoase + materiale inflamabile. Restaurat de Țarul Nicolae I în mai puțin de 2 ani — exemplu de restaurare rapidă a patrimoniului.</div>
        </div>
      </div>
    </div>
  </div>

  <!-- SLIDE 8: SURSE -->
  <div class="slide slide-8">
    <div class="slide-header">
      <div class="slide-num">08</div>
      <div class="slide-title">Surse <span>Bibliografice</span></div>
    </div>
    <div class="sources-container">
      <div class="source-item">
        <div class="src-num">1</div>
        <div class="src-text">Historic Royal Palaces. <em>Windsor Castle: The Official Illustrated History.</em> Royal Collection Trust, 2002.</div>
      </div>
      <div class="source-item">
        <div class="src-num">2</div>
        <div class="src-text">BBC News Archive. <em>"Windsor Castle fire: 20 years on."</em> BBC, November 2012. <a>bbc.co.uk/news</a></div>
      </div>
      <div class="source-item">
        <div class="src-num">3</div>
        <div class="src-text">Donald Insall Associates. <em>Windsor Castle: Restoration after the 1992 Fire.</em> English Heritage Technical Report, 1997.</div>
      </div>
      <div class="source-item">
        <div class="src-num">4</div>
        <div class="src-text">Codul Urbanismului și Construcțiilor al Republicii Moldova, adoptat prin Legea nr. 401 din 2022.</div>
      </div>
      <div class="source-item">
        <div class="src-num">5</div>
        <div class="src-text">Codul Penal al Republicii Moldova, nr. 985 din 18.04.2002. Art. 197, 298, 328.</div>
      </div>
      <div class="source-item">
        <div class="src-num">6</div>
        <div class="src-text">The Guardian. <em>"Notre-Dame fire: what we know about what happened."</em> April 2019. <a>theguardian.com</a></div>
      </div>
      <div class="source-item">
        <div class="src-num">7</div>
        <div class="src-text">Royal Collection Trust. <em>The Restoration of Windsor Castle.</em> London: Royal Collection Enterprises, 1997.</div>
      </div>
    </div>
    <div class="final-tag">Elaborat de: Zastavnetchi Lucas · Varvaruc Adrian</div>
  </div>

</div>

<!-- NAVIGATION -->
<div class="nav">
  <button class="nav-btn" id="prev" onclick="changeSlide(-1)" disabled>← Înapoi</button>
  <div class="nav-dots" id="dots"></div>
  <span class="slide-counter" id="counter">1 / 8</span>
  <button class="nav-btn" id="next" onclick="changeSlide(1)">Înainte →</button>
</div>

<script>
  let current = 0;
  const slides = document.querySelectorAll('.slide');
  const total = slides.length;
  const dotsEl = document.getElementById('dots');
  const counter = document.getElementById('counter');

  // Create dots
  for (let i = 0; i < total; i++) {
    const d = document.createElement('div');
    d.className = 'dot' + (i === 0 ? ' active' : '');
    d.onclick = () => goTo(i);
    dotsEl.appendChild(d);
  }

  function goTo(n) {
    slides[current].style.opacity = '0';
    setTimeout(() => { slides[current].style.display = 'none'; }, 300);
    current = n;
    slides[current].style.display = 'flex';
    setTimeout(() => { slides[current].style.opacity = '1'; }, 10);
    document.querySelectorAll('.dot').forEach((d,i) => d.classList.toggle('active', i === current));
    counter.textContent = (current + 1) + ' / ' + total;
    document.getElementById('prev').disabled = current === 0;
    document.getElementById('next').disabled = current === total - 1;
  }

  function changeSlide(dir) { goTo(current + dir); }

  document.addEventListener('keydown', e => {
    if (e.key === 'ArrowRight' && current < total - 1) changeSlide(1);
    if (e.key === 'ArrowLeft' && current > 0) changeSlide(-1);
  });

  // Fire particles
  function createParticle() {
    const p = document.createElement('div');
    p.className = 'particle';
    const size = Math.random() * 20 + 10;
    const colors = ['#ff4400','#ff6600','#ff2200','#ffaa00','#ff8800'];
    p.style.cssText = `
      width:${size}px;height:${size*1.5}px;
      left:${Math.random()*100}%;
      background:${colors[Math.floor(Math.random()*colors.length)]};
      animation-duration:${Math.random()*3+2}s;
      animation-delay:${Math.random()*2}s;
      opacity:0;
    `;
    document.getElementById('particles').appendChild(p);
    setTimeout(() => p.remove(), 5000);
  }

  setInterval(createParticle, 200);
</script>
</body>
</html>

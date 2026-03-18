<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Manjunath R. — DevOps Engineer</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;500;700&family=Syne:wght@400;600;800&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #080c10;
    --bg2: #0d1117;
    --bg3: #161b22;
    --card: #0d1117;
    --border: #21262d;
    --green: #00ff88;
    --cyan: #00e5ff;
    --blue: #388bfd;
    --muted: #8b949e;
    --text: #e6edf3;
    --text2: #c9d1d9;
    --red: #ff4466;
    --yellow: #ffa600;
    --radius: 8px;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'JetBrains Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ── GRID NOISE BACKGROUND ── */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,255,136,.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,255,136,.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  /* ── GLOW ORBS ── */
  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(120px);
    opacity: .18;
    pointer-events: none;
    z-index: 0;
  }
  .orb1 { width: 500px; height: 500px; background: var(--green); top: -100px; left: -150px; animation: drift 12s ease-in-out infinite alternate; }
  .orb2 { width: 400px; height: 400px; background: var(--cyan);  bottom: -80px; right: -100px; animation: drift 15s ease-in-out infinite alternate-reverse; }

  @keyframes drift { from { transform: translate(0,0); } to { transform: translate(40px, 30px); } }

  /* ── LAYOUT ── */
  .container { max-width: 900px; margin: 0 auto; padding: 0 24px; position: relative; z-index: 1; }

  /* ── HEADER ── */
  header {
    padding: 80px 0 60px;
    text-align: center;
    animation: fadeUp .8s ease both;
  }

  .badge {
    display: inline-block;
    border: 1px solid var(--green);
    color: var(--green);
    font-size: 11px;
    letter-spacing: .14em;
    padding: 4px 14px;
    border-radius: 20px;
    margin-bottom: 24px;
    animation: pulse-border 3s ease-in-out infinite;
  }

  @keyframes pulse-border {
    0%,100% { box-shadow: 0 0 0 0 rgba(0,255,136,.4); }
    50%      { box-shadow: 0 0 0 8px rgba(0,255,136,0); }
  }

  h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(2.4rem, 6vw, 4rem);
    font-weight: 800;
    line-height: 1.05;
    letter-spacing: -.02em;
    background: linear-gradient(135deg, #fff 30%, var(--green));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 12px;
  }

  .subtitle {
    font-size: 13px;
    color: var(--muted);
    letter-spacing: .08em;
    margin-bottom: 32px;
  }

  .subtitle span { color: var(--cyan); }

  /* terminal prompt decoration */
  .prompt {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    font-size: 12px;
    color: var(--muted);
    border: 1px solid var(--border);
    background: var(--bg3);
    padding: 6px 16px;
    border-radius: 6px;
  }
  .prompt .dot { width: 8px; height: 8px; border-radius: 50%; background: var(--green); animation: blink 1.2s step-end infinite; }
  @keyframes blink { 50% { opacity: 0; } }

  /* ── SECTION ── */
  section { padding: 48px 0; animation: fadeUp .8s ease both; }

  .section-label {
    font-size: 10px;
    letter-spacing: .2em;
    color: var(--green);
    text-transform: uppercase;
    margin-bottom: 8px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .section-label::after { content: ''; flex: 1; height: 1px; background: var(--border); }

  h2 {
    font-family: 'Syne', sans-serif;
    font-size: 1.5rem;
    font-weight: 700;
    color: var(--text);
    margin-bottom: 28px;
  }

  /* ── ABOUT CARD ── */
  .about-card {
    background: var(--bg3);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 28px 32px;
    position: relative;
    overflow: hidden;
  }
  .about-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 3px; height: 100%;
    background: linear-gradient(180deg, var(--green), var(--cyan));
  }
  .about-card p {
    font-size: 13.5px;
    line-height: 1.85;
    color: var(--text2);
  }
  .about-card p strong { color: var(--green); font-weight: 500; }

  /* ── SKILLS GRID ── */
  .skills-section { display: grid; gap: 20px; }

  .skill-group {
    background: var(--bg3);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 20px 24px;
    transition: border-color .25s, transform .25s;
  }
  .skill-group:hover { border-color: var(--green); transform: translateY(-2px); }

  .skill-group-title {
    font-size: 10px;
    color: var(--cyan);
    letter-spacing: .15em;
    text-transform: uppercase;
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .skill-group-title .ico { font-size: 14px; }

  .tags { display: flex; flex-wrap: wrap; gap: 8px; }

  .tag {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    font-size: 11.5px;
    padding: 5px 12px;
    border-radius: 4px;
    border: 1px solid var(--border);
    background: var(--bg2);
    color: var(--text2);
    transition: all .2s;
    cursor: default;
  }
  .tag:hover { border-color: var(--green); color: var(--green); background: rgba(0,255,136,.06); }
  .tag .dot { width: 5px; height: 5px; border-radius: 50%; }
  .tag .dot.g  { background: var(--green); }
  .tag .dot.c  { background: var(--cyan); }
  .tag .dot.b  { background: var(--blue); }
  .tag .dot.y  { background: var(--yellow); }

  /* ── STATS GRID ── */
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 16px;
    margin-bottom: 28px;
  }

  .stat-card {
    background: var(--bg3);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 20px 20px;
    text-align: center;
    transition: border-color .25s;
    overflow: hidden;
  }
  .stat-card:hover { border-color: var(--cyan); }
  .stat-card img { width: 100%; border-radius: 4px; filter: brightness(.92); }
  .stat-card p { font-size: 11px; color: var(--muted); margin-top: 10px; letter-spacing: .08em; }

  /* ── CONTACT ── */
  .contact-row {
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
  }

  .contact-link {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    font-size: 12px;
    padding: 10px 20px;
    border-radius: 6px;
    border: 1px solid var(--border);
    background: var(--bg3);
    color: var(--text2);
    text-decoration: none;
    transition: all .2s;
  }
  .contact-link:hover { border-color: var(--green); color: var(--green); transform: translateY(-2px); }
  .contact-link svg { width: 16px; height: 16px; }

  /* ── FOOTER ── */
  footer {
    text-align: center;
    padding: 40px 0 60px;
    font-size: 11px;
    color: var(--muted);
    letter-spacing: .06em;
    border-top: 1px solid var(--border);
  }
  footer span { color: var(--green); }

  /* ── PROFILE VIEWS BADGE ── */
  .profile-views {
    display: flex;
    justify-content: center;
    margin-bottom: 20px;
  }

  /* ── ANIMATION ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  section:nth-child(2) { animation-delay: .1s; }
  section:nth-child(3) { animation-delay: .2s; }
  section:nth-child(4) { animation-delay: .3s; }
  section:nth-child(5) { animation-delay: .4s; }

  /* ── DIVIDER ── */
  .divider { height: 1px; background: var(--border); margin: 0; }

  /* ── 3D CONTRIB ── */
  .contrib-wrap {
    background: var(--bg3);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 20px;
    text-align: center;
  }
  .contrib-wrap img { width: 100%; border-radius: 4px; }

  /* scrollbar */
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--border); border-radius: 3px; }
  ::-webkit-scrollbar-thumb:hover { background: var(--green); }
</style>
</head>
<body>

<div class="orb orb1"></div>
<div class="orb orb2"></div>

<div class="container">

  <!-- ── HEADER ── -->
  <header>
    <div class="badge">OPEN TO OPPORTUNITIES</div>
    <h1>Manjunath R.</h1>
    <p class="subtitle">DevOps Engineer &nbsp;·&nbsp; <span>Cloud Infrastructure</span> &nbsp;·&nbsp; Automation</p>
    <div class="prompt">
      <span class="dot"></span>
      <span>manjuappu1375@ubuntu:~$ <em style="color:var(--green)">kubectl get pods --all-namespaces</em></span>
    </div>
  </header>

  <div class="divider"></div>

  <!-- ── ABOUT ── -->
  <section>
    <div class="section-label">01 &nbsp; About</div>
    <h2>Who I Am</h2>
    <div class="about-card">
      <p>
        Hello! I'm <strong>Manjunath R.</strong>, a passionate <strong>DevOps Engineer</strong> with a strong
        interest in automation, cloud computing, and infrastructure management. I thrive on solving complex
        problems and continuously expanding my technical skill set. I enjoy working with various technologies
        to optimize workflows and enhance system reliability.
      </p>
    </div>
  </section>

  <!-- ── SKILLS ── -->
  <section>
    <div class="section-label">02 &nbsp; Skills &amp; Tools</div>
    <h2>Tech Stack</h2>
    <div class="skills-section">

      <div class="skill-group">
        <div class="skill-group-title"><span class="ico">🖥️</span> Programming Languages</div>
        <div class="tags">
          <span class="tag"><span class="dot g"></span>Shell Scripting</span>
          <span class="tag"><span class="dot b"></span>SQL</span>
          <span class="tag"><span class="dot y"></span>YAML</span>
        </div>
      </div>

      <div class="skill-group">
        <div class="skill-group-title"><span class="ico">☁️</span> AWS Services</div>
        <div class="tags">
          <span class="tag"><span class="dot y"></span>EC2</span>
          <span class="tag"><span class="dot y"></span>S3</span>
          <span class="tag"><span class="dot y"></span>VPC</span>
          <span class="tag"><span class="dot y"></span>IAM</span>
          <span class="tag"><span class="dot y"></span>Lambda</span>
          <span class="tag"><span class="dot y"></span>SNS</span>
          <span class="tag"><span class="dot y"></span>CloudWatch</span>
          <span class="tag"><span class="dot y"></span>Route 53</span>
          <span class="tag"><span class="dot y"></span>AWS CLI</span>
        </div>
      </div>

      <div class="skill-group">
        <div class="skill-group-title"><span class="ico">⚙️</span> DevOps Toolchain</div>
        <div class="tags">
          <span class="tag"><span class="dot g"></span>Docker</span>
          <span class="tag"><span class="dot g"></span>Kubernetes</span>
          <span class="tag"><span class="dot g"></span>Jenkins</span>
          <span class="tag"><span class="dot g"></span>Ansible</span>
          <span class="tag"><span class="dot g"></span>Terraform</span>
          <span class="tag"><span class="dot c"></span>Git / GitHub</span>
        </div>
      </div>

      <div class="skill-group">
        <div class="skill-group-title"><span class="ico">🖥️</span> Operating Systems</div>
        <div class="tags">
          <span class="tag"><span class="dot g"></span>Linux — Ubuntu</span>
          <span class="tag"><span class="dot g"></span>Linux — CentOS</span>
          <span class="tag"><span class="dot b"></span>Windows</span>
        </div>
      </div>

    </div>
  </section>

  <!-- ── GITHUB STATS ── -->
  <section>
    <div class="section-label">03 &nbsp; GitHub</div>
    <h2>Stats &amp; Activity</h2>

    <div class="profile-views">
      <img src="https://komarev.com/ghpvc/?username=manjuappu1375&label=Profile%20Views&color=00ff88&style=flat-square" alt="Profile Views"/>
    </div>

    <div class="stats-grid">
      <div class="stat-card">
        <img src="https://github-readme-stats.vercel.app/api?username=manjuappu1375&show_icons=true&count_private=true&hide_title=true&theme=dark&bg_color=0d1117&border_color=21262d&icon_color=00ff88&text_color=e6edf3" alt="GitHub Stats"/>
        <p>GitHub Stats</p>
      </div>
      <div class="stat-card">
        <img src="https://github-readme-streak-stats.herokuapp.com/?user=manjuappu1375&theme=dark&background=0d1117&border=21262d&ring=00ff88&fire=00e5ff&currStreakLabel=00ff88" alt="GitHub Streaks"/>
        <p>Contribution Streak</p>
      </div>
    </div>

    <div class="stats-grid" style="grid-template-columns: repeat(auto-fit, minmax(240px,1fr))">
      <div class="stat-card">
        <img src="https://github-readme-stats.vercel.app/api/top-langs?username=manjuappu1375&show_icons=true&layout=compact&theme=dark&bg_color=0d1117&border_color=21262d&text_color=e6edf3" alt="Top Languages"/>
        <p>Most Used Languages</p>
      </div>
      <div class="stat-card">
        <img src="https://github-profile-trophy.vercel.app/?username=manjuappu1375&theme=darkhub&margin-w=8&no-bg=true&no-frame=true&column=3&rank=SECRET,SSS,SS,S,AAA,AA,A" alt="Trophies"/>
        <p>GitHub Trophies</p>
      </div>
    </div>

    <div class="contrib-wrap">
      <img src="https://github.com/manjuappu1375/manjuappu1375/blob/main/profile-3d-contrib/profile-night-green.svg" alt="3D Contribution Graph"/>
      <p style="font-size:11px;color:var(--muted);margin-top:10px;letter-spacing:.06em;">3D Contribution Graph</p>
    </div>
  </section>

  <!-- ── CONTACT ── -->
  <section>
    <div class="section-label">04 &nbsp; Contact</div>
    <h2>Get In Touch</h2>
    <div class="contact-row">

      <a href="mailto:manjuappu1375@gmail.com" class="contact-link">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m2 7 10 7 10-7"/></svg>
        manjuappu1375@gmail.com
      </a>

      <a href="https://linkedin.com/in/yourprofile" class="contact-link" target="_blank">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2"/></svg>
        LinkedIn
      </a>

      <a href="https://twitter.com/YourHandle" class="contact-link" target="_blank">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>
        Twitter / X
      </a>

      <a href="https://github.com/manjuappu1375" class="contact-link" target="_blank">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0 1 12 6.844a9.59 9.59 0 0 1 2.504.337c1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.02 10.02 0 0 0 22 12.017C22 6.484 17.522 2 12 2z"/></svg>
        GitHub
      </a>

    </div>
  </section>

</div>

<footer>
  <p>crafted with <span>❤</span> by Manjunath R. &nbsp;·&nbsp; DevOps Engineer &nbsp;·&nbsp; Bengaluru, India</p>
</footer>

</body>
</html>

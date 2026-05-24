<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>unichat-devops-lab — Documentación</title>
  <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;600;700&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet" />
  <style>
    :root {
      --bg:        #0d0f14;
      --bg2:       #13161e;
      --bg3:       #1a1e2a;
      --border:    #252b3b;
      --green:     #3ddc84;
      --green-dim: #1e6644;
      --cyan:      #5dd8f8;
      --amber:     #f5a623;
      --red:       #f25d6b;
      --purple:    #a78bfa;
      --text:      #c8d3e8;
      --text-dim:  #5a6382;
      --text-head: #e8eef8;
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'JetBrains Mono', monospace;
      font-size: 14px;
      line-height: 1.75;
      min-height: 100vh;
    }

    /* ── GRID NOISE BACKGROUND ── */
    body::before {
      content: '';
      position: fixed; inset: 0;
      background-image:
        linear-gradient(rgba(61,220,132,.03) 1px, transparent 1px),
        linear-gradient(90deg, rgba(61,220,132,.03) 1px, transparent 1px);
      background-size: 40px 40px;
      pointer-events: none;
      z-index: 0;
    }

    /* ── SIDEBAR NAV ── */
    .sidebar {
      position: fixed;
      top: 0; left: 0;
      width: 240px;
      height: 100vh;
      background: var(--bg2);
      border-right: 1px solid var(--border);
      padding: 28px 0;
      overflow-y: auto;
      z-index: 100;
    }

    .sidebar-logo {
      padding: 0 20px 24px;
      border-bottom: 1px solid var(--border);
    }

    .sidebar-logo .repo-tag {
      font-family: 'Syne', sans-serif;
      font-size: 10px;
      font-weight: 700;
      letter-spacing: .12em;
      text-transform: uppercase;
      color: var(--green);
      margin-bottom: 4px;
    }

    .sidebar-logo .repo-name {
      font-family: 'Syne', sans-serif;
      font-size: 16px;
      font-weight: 800;
      color: var(--text-head);
      line-height: 1.2;
    }

    .nav-section {
      padding: 18px 0 4px;
    }

    .nav-label {
      font-size: 9px;
      font-weight: 700;
      letter-spacing: .15em;
      text-transform: uppercase;
      color: var(--text-dim);
      padding: 0 20px;
      margin-bottom: 6px;
    }

    .nav-link {
      display: block;
      padding: 6px 20px;
      color: var(--text-dim);
      text-decoration: none;
      font-size: 12px;
      border-left: 2px solid transparent;
      transition: color .2s, border-color .2s, background .2s;
    }

    .nav-link:hover,
    .nav-link.active {
      color: var(--green);
      border-left-color: var(--green);
      background: rgba(61,220,132,.05);
    }

    /* ── MAIN ── */
    .main {
      margin-left: 240px;
      position: relative;
      z-index: 1;
    }

    /* ── HERO ── */
    .hero {
      padding: 72px 64px 56px;
      border-bottom: 1px solid var(--border);
      background: linear-gradient(135deg, var(--bg2) 0%, var(--bg) 60%);
      position: relative;
      overflow: hidden;
    }

    .hero::after {
      content: '';
      position: absolute;
      top: -80px; right: -80px;
      width: 400px; height: 400px;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(61,220,132,.08) 0%, transparent 70%);
      pointer-events: none;
    }

    .hero-badge {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      background: rgba(61,220,132,.1);
      border: 1px solid var(--green-dim);
      border-radius: 4px;
      padding: 4px 10px;
      font-size: 11px;
      color: var(--green);
      margin-bottom: 20px;
      letter-spacing: .06em;
    }

    .hero-badge .dot {
      width: 6px; height: 6px;
      border-radius: 50%;
      background: var(--green);
      animation: pulse 2s ease-in-out infinite;
    }

    @keyframes pulse {
      0%, 100% { opacity: 1; }
      50%       { opacity: .3; }
    }

    .hero h1 {
      font-family: 'Syne', sans-serif;
      font-size: clamp(28px, 4vw, 48px);
      font-weight: 800;
      color: var(--text-head);
      letter-spacing: -.02em;
      line-height: 1.1;
      margin-bottom: 16px;
    }

    .hero h1 span { color: var(--green); }

    .hero-desc {
      max-width: 620px;
      color: var(--text-dim);
      font-size: 13px;
      line-height: 1.8;
      margin-bottom: 32px;
    }

    .badge-row {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
    }

    .badge {
      display: inline-flex;
      align-items: center;
      gap: 5px;
      background: var(--bg3);
      border: 1px solid var(--border);
      border-radius: 4px;
      padding: 4px 10px;
      font-size: 11px;
      color: var(--text-dim);
    }

    .badge.green { color: var(--green); border-color: var(--green-dim); }
    .badge.cyan  { color: var(--cyan);  border-color: #1a4f60; }
    .badge.amber { color: var(--amber); border-color: #5a3e10; }

    /* ── CONTENT ── */
    .content {
      max-width: 900px;
      padding: 56px 64px;
    }

    /* SECTION */
    section { margin-bottom: 64px; }

    .section-label {
      font-size: 9px;
      font-weight: 700;
      letter-spacing: .2em;
      text-transform: uppercase;
      color: var(--green);
      margin-bottom: 8px;
    }

    h2 {
      font-family: 'Syne', sans-serif;
      font-size: 22px;
      font-weight: 800;
      color: var(--text-head);
      margin-bottom: 20px;
      padding-bottom: 12px;
      border-bottom: 1px solid var(--border);
      display: flex;
      align-items: center;
      gap: 10px;
    }

    h2 .h2-icon { font-size: 18px; }

    h3 {
      font-family: 'Syne', sans-serif;
      font-size: 14px;
      font-weight: 700;
      color: var(--cyan);
      margin: 28px 0 12px;
      letter-spacing: .04em;
    }

    p { color: var(--text); margin-bottom: 14px; line-height: 1.8; }

    /* ── CODE BLOCKS ── */
    .code-block {
      background: var(--bg2);
      border: 1px solid var(--border);
      border-radius: 8px;
      overflow: hidden;
      margin: 16px 0;
    }

    .code-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 8px 14px;
      background: var(--bg3);
      border-bottom: 1px solid var(--border);
    }

    .code-header .dots {
      display: flex;
      gap: 6px;
    }

    .code-header .dots span {
      width: 10px; height: 10px;
      border-radius: 50%;
    }

    .dot-red    { background: #f25d6b; }
    .dot-amber  { background: #f5a623; }
    .dot-green  { background: #3ddc84; }

    .code-lang {
      font-size: 10px;
      letter-spacing: .1em;
      color: var(--text-dim);
      text-transform: uppercase;
    }

    .code-block pre {
      padding: 18px 20px;
      overflow-x: auto;
      font-size: 12.5px;
      line-height: 1.7;
      color: var(--text);
    }

    .code-block pre .c  { color: var(--text-dim); }  /* comment */
    .code-block pre .k  { color: var(--cyan); }       /* keyword */
    .code-block pre .s  { color: var(--amber); }      /* string */
    .code-block pre .p  { color: var(--green); }      /* prompt/command */

    /* ── INLINE CODE ── */
    code {
      background: var(--bg3);
      border: 1px solid var(--border);
      border-radius: 3px;
      padding: 1px 6px;
      font-size: 12px;
      color: var(--cyan);
      font-family: 'JetBrains Mono', monospace;
    }

    /* ── TABLES ── */
    .table-wrap {
      overflow-x: auto;
      margin: 16px 0;
      border-radius: 8px;
      border: 1px solid var(--border);
    }

    table {
      width: 100%;
      border-collapse: collapse;
    }

    thead tr {
      background: var(--bg3);
      border-bottom: 1px solid var(--border);
    }

    thead th {
      padding: 10px 16px;
      text-align: left;
      font-size: 10px;
      letter-spacing: .12em;
      text-transform: uppercase;
      color: var(--text-dim);
      font-weight: 700;
    }

    tbody tr {
      border-bottom: 1px solid var(--border);
      transition: background .15s;
    }

    tbody tr:last-child { border-bottom: none; }
    tbody tr:hover      { background: rgba(255,255,255,.02); }

    tbody td {
      padding: 10px 16px;
      font-size: 12.5px;
      color: var(--text);
      vertical-align: middle;
    }

    tbody td:first-child { color: var(--green); }

    /* ── CALLOUT ── */
    .callout {
      display: flex;
      gap: 12px;
      background: rgba(245,166,35,.05);
      border: 1px solid rgba(245,166,35,.25);
      border-radius: 8px;
      padding: 14px 16px;
      margin: 16px 0;
    }

    .callout .icon { font-size: 16px; flex-shrink: 0; margin-top: 1px; }

    .callout-body { font-size: 12.5px; color: var(--text-dim); line-height: 1.7; }

    .callout-body strong { color: var(--amber); }

    .callout.green-callout {
      background: rgba(61,220,132,.05);
      border-color: rgba(61,220,132,.2);
    }

    .callout.green-callout .callout-body strong { color: var(--green); }

    /* ── SERVICES GRID ── */
    .services-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
      gap: 14px;
      margin-top: 16px;
    }

    .service-card {
      background: var(--bg2);
      border: 1px solid var(--border);
      border-radius: 10px;
      padding: 16px 18px;
      transition: border-color .2s, transform .2s;
      position: relative;
      overflow: hidden;
    }

    .service-card:hover {
      border-color: var(--green-dim);
      transform: translateY(-2px);
    }

    .service-card::before {
      content: '';
      position: absolute;
      top: 0; left: 0; right: 0;
      height: 2px;
      background: linear-gradient(90deg, var(--green), transparent);
      opacity: 0;
      transition: opacity .2s;
    }

    .service-card:hover::before { opacity: 1; }

    .service-emoji { font-size: 22px; margin-bottom: 10px; display: block; }

    .service-name {
      font-family: 'Syne', sans-serif;
      font-weight: 700;
      font-size: 13px;
      color: var(--text-head);
      margin-bottom: 4px;
    }

    .service-url {
      font-size: 11px;
      color: var(--cyan);
      margin-bottom: 8px;
    }

    .service-desc {
      font-size: 11px;
      color: var(--text-dim);
      line-height: 1.6;
    }

    /* ── STEP LIST ── */
    .step-list {
      list-style: none;
      counter-reset: steps;
      display: flex;
      flex-direction: column;
      gap: 10px;
      margin: 16px 0;
    }

    .step-list li {
      counter-increment: steps;
      display: flex;
      gap: 14px;
      align-items: flex-start;
    }

    .step-list li::before {
      content: counter(steps);
      flex-shrink: 0;
      width: 24px; height: 24px;
      border-radius: 50%;
      background: rgba(61,220,132,.12);
      border: 1px solid var(--green-dim);
      color: var(--green);
      font-size: 11px;
      font-weight: 700;
      display: flex;
      align-items: center;
      justify-content: center;
      margin-top: 2px;
    }

    .step-list li .step-body { flex: 1; }

    .step-list li .step-title {
      font-size: 13px;
      font-weight: 600;
      color: var(--text-head);
      margin-bottom: 6px;
    }

    /* ── TROUBLE TABLE ── */
    tbody td.problem  { color: var(--red); }
    tbody td.solution { color: var(--text); }

    /* ── SCROLLBAR ── */
    ::-webkit-scrollbar { width: 6px; height: 6px; }
    ::-webkit-scrollbar-track { background: var(--bg); }
    ::-webkit-scrollbar-thumb { background: var(--border); border-radius: 3px; }
    ::-webkit-scrollbar-thumb:hover { background: var(--text-dim); }

    /* ── RESPONSIVE ── */
    @media (max-width: 768px) {
      .sidebar { display: none; }
      .main    { margin-left: 0; }
      .hero, .content { padding: 32px 24px; }
    }
  </style>
</head>
<body>

  <!-- ══ SIDEBAR ══ -->
  <nav class="sidebar">
    <div class="sidebar-logo">
      <div class="repo-tag">DevOps Lab</div>
      <div class="repo-name">unichat-<br>devops-lab</div>
    </div>

    <div class="nav-section">
      <div class="nav-label">Inicio</div>
      <a href="#quickstart" class="nav-link">⚡ Inicio rápido</a>
      <a href="#requisitos" class="nav-link">📋 Requisitos</a>
    </div>

    <div class="nav-section">
      <div class="nav-label">Instalación</div>
      <a href="#make"  class="nav-link">🔧 Instalar Make</a>
      <a href="#clone" class="nav-link">📦 Clonar repo</a>
      <a href="#env"   class="nav-link">⚙️ Configurar .env</a>
    </div>

    <div class="nav-section">
      <div class="nav-label">Uso</div>
      <a href="#makefile"  class="nav-link">🛠 Makefile</a>
      <a href="#servicios" class="nav-link">🌐 Servicios</a>
    </div>

    <div class="nav-section">
      <div class="nav-label">Ayuda</div>
      <a href="#problemas" class="nav-link">🚨 Solución de problemas</a>
    </div>
  </nav>

  <!-- ══ MAIN ══ -->
  <div class="main">

    <!-- HERO -->
    <div class="hero">
      <div class="hero-badge">
        <span class="dot"></span>
        Stack activo
      </div>
      <h1>unichat-<span>devops-lab</span></h1>
      <p class="hero-desc">
        Laboratorio DevOps para desplegar el stack completo de <strong style="color:var(--text-head)">UNI-CHAT</strong> con Docker Compose —
        API, MongoDB, Redis, RabbitMQ, Nginx, Portainer, Seq, Dozzle y más,
        todo controlado desde un <code>Makefile</code>.
      </p>
      <div class="badge-row">
        <span class="badge green">🐳 Docker Compose</span>
        <span class="badge cyan">🔧 GNU Make</span>
        <span class="badge amber">🍃 MongoDB</span>
        <span class="badge">⚡ Redis</span>
        <span class="badge">🐇 RabbitMQ</span>
        <span class="badge">📜 Seq · Dozzle</span>
      </div>
    </div>

    <!-- CONTENT -->
    <div class="content">

      <!-- ── INICIO RÁPIDO ── -->
      <section id="quickstart">
        <div class="section-label">// 00 — overview</div>
        <h2><span class="h2-icon">⚡</span> Inicio rápido</h2>
        <p>Cuatro pasos para tener el stack completo corriendo desde cero:</p>

        <div class="code-block">
          <div class="code-header">
            <div class="dots">
              <span class="dot-red"></span>
              <span class="dot-amber"></span>
              <span class="dot-green"></span>
            </div>
            <span class="code-lang">bash</span>
          </div>
          <pre><span class="c"># 1. Instalar Make</span>
<span class="p">$</span> sudo apt update && sudo apt upgrade -y
<span class="p">$</span> sudo apt install make -y

<span class="c"># 2. Clonar el repositorio</span>
<span class="p">$</span> git clone https://github.com/DaR3kDev/unichat-devops-lab.git
<span class="p">$</span> cd unichat-devops-lab

<span class="c"># 3. Crear el archivo .env (ver sección de configuración)</span>
<span class="p">$</span> nano .env

<span class="c"># 4. Levantar todo el stack</span>
<span class="p">$</span> make up</pre>
        </div>

        <div class="callout green-callout">
          <span class="icon">✅</span>
          <div class="callout-body">
            Una vez corriendo, ejecuta <strong>make help</strong> para ver el panel de control con todas las URLs y comandos disponibles.
          </div>
        </div>
      </section>

      <!-- ── REQUISITOS ── -->
      <section id="requisitos">
        <div class="section-label">// 01 — prerequisites</div>
        <h2><span class="h2-icon">📋</span> Requisitos previos</h2>

        <div class="table-wrap">
          <table>
            <thead>
              <tr>
                <th>Herramienta</th>
                <th>Linux / WSL</th>
                <th>Notas</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>Docker + Compose v2</td>
                <td>Docker Engine</td>
                <td>Obligatorio</td>
              </tr>
              <tr>
                <td>GNU Make</td>
                <td><code>apt install make</code></td>
                <td>Ver sección de instalación</td>
              </tr>
              <tr>
                <td>Git</td>
                <td><code>apt install git</code></td>
                <td>Para clonar el repo</td>
              </tr>
              <tr>
                <td>Bash</td>
                <td>Incluido en Linux / WSL2</td>
                <td>Requerido por el Makefile</td>
              </tr>
            </tbody>
          </table>
        </div>

        <div class="callout">
          <span class="icon">⚠️</span>
          <div class="callout-body">
            En <strong>Windows</strong> se recomienda usar <strong>WSL2</strong> para ejecutar todos los comandos sin inconvenientes.
          </div>
        </div>
      </section>

      <!-- ── INSTALAR MAKE ── -->
      <section id="make">
        <div class="section-label">// 02 — installation</div>
        <h2><span class="h2-icon">🔧</span> Instalación de Make</h2>
        <p>Antes de usar el <code>Makefile</code>, asegúrate de tener <code>make</code> instalado en tu sistema.</p>

        <ol class="step-list">
          <li>
            <div class="step-body">
              <div class="step-title">Actualizar paquetes del sistema</div>
              <div class="code-block">
                <div class="code-header">
                  <div class="dots"><span class="dot-red"></span><span class="dot-amber"></span><span class="dot-green"></span></div>
                  <span class="code-lang">bash</span>
                </div>
                <pre><span class="p">$</span> sudo apt update && sudo apt upgrade -y</pre>
              </div>
            </div>
          </li>
          <li>
            <div class="step-body">
              <div class="step-title">Instalar Make</div>
              <div class="code-block">
                <div class="code-header">
                  <div class="dots"><span class="dot-red"></span><span class="dot-amber"></span><span class="dot-green"></span></div>
                  <span class="code-lang">bash</span>
                </div>
                <pre><span class="p">$</span> sudo apt install make -y</pre>
              </div>
            </div>
          </li>
          <li>
            <div class="step-body">
              <div class="step-title">Verificar instalación</div>
              <div class="code-block">
                <div class="code-header">
                  <div class="dots"><span class="dot-red"></span><span class="dot-amber"></span><span class="dot-green"></span></div>
                  <span class="code-lang">bash</span>
                </div>
                <pre><span class="p">$</span> make --version

<span class="c">GNU Make 4.3
Built for x86_64-pc-linux-gnu</span></pre>
              </div>
            </div>
          </li>
        </ol>
      </section>

      <!-- ── CLONAR ── -->
      <section id="clone">
        <div class="section-label">// 03 — setup</div>
        <h2><span class="h2-icon">📦</span> Clonar el repositorio</h2>

        <div class="code-block">
          <div class="code-header">
            <div class="dots"><span class="dot-red"></span><span class="dot-amber"></span><span class="dot-green"></span></div>
            <span class="code-lang">bash</span>
          </div>
          <pre><span class="c"># Clonar desde GitHub</span>
<span class="p">$</span> git clone https://github.com/DaR3kDev/unichat-devops-lab.git

<span class="c"># Ingresar a la carpeta del proyecto</span>
<span class="p">$</span> cd unichat-devops-lab</pre>
        </div>
      </section>

      <!-- ── ENV ── -->
      <section id="env">
        <div class="section-label">// 04 — configuration</div>
        <h2><span class="h2-icon">⚙️</span> Configuración del .env</h2>
        <p>Crea un archivo <code>.env</code> en la raíz del proyecto con el siguiente contenido:</p>

        <div class="code-block">
          <div class="code-header">
            <div class="dots"><span class="dot-red"></span><span class="dot-amber"></span><span class="dot-green"></span></div>
            <span class="code-lang">.env</span>
          </div>
          <pre><span class="c"># =========================
# CONFIG
# =========================</span>
<span class="k">PROD_FILE</span>=<span class="s">docker-compose.prod.yml</span>
<span class="k">TOOLS_FILE</span>=<span class="s">docker-compose.tools.yml</span></pre>
        </div>

        <div class="callout">
          <span class="icon">⚠️</span>
          <div class="callout-body">
            <strong>No subas este archivo a Git.</strong> Verifica que <code>.env</code> esté en tu <code>.gitignore</code>.
          </div>
        </div>

        <h3>¿Cómo detecta la IP el Makefile?</h3>
        <p>El <code>Makefile</code> detecta automáticamente tu IP local real según el sistema operativo:</p>

        <div class="table-wrap">
          <table>
            <thead>
              <tr><th>Sistema</th><th>Método de detección</th></tr>
            </thead>
            <tbody>
              <tr>
                <td>Linux / WSL2</td>
                <td><code>hostname -I</code> → primer resultado</td>
              </tr>
              <tr>
                <td>Windows (PowerShell)</td>
                <td>Interfaz Wi-Fi activa sin IP <code>169.x.x.x</code></td>
              </tr>
              <tr>
                <td>Sin detección</td>
                <td>Fallback a <code>127.0.0.1</code></td>
              </tr>
            </tbody>
          </table>
        </div>
      </section>

      <!-- ── MAKEFILE ── -->
      <section id="makefile">
        <div class="section-label">// 05 — usage</div>
        <h2><span class="h2-icon">🛠</span> Makefile — Comandos disponibles</h2>
        <p>Ejecuta <code>make help</code> desde la raíz para ver el panel de control completo:</p>

        <div class="code-block">
          <div class="code-header">
            <div class="dots"><span class="dot-red"></span><span class="dot-amber"></span><span class="dot-green"></span></div>
            <span class="code-lang">output</span>
          </div>
          <pre><span class="c">======================================
 🚀 UNI-CHAT SERVER CONTROL PANEL
======================================</span>

 🌐 IP LOCAL (RED REAL): http://&lt;TU_IP&gt;

 📡 SERVICIOS DISPONIBLES:
 🔥 API:
   SCALAR API    -&gt; http://&lt;TU_IP&gt;/scalar
 🐇 RABBITMQ:
   RABBIT UI     -&gt; http://&lt;TU_IP&gt;:15672
 🍃 MONGODB:
   MONGO EXPRESS -&gt; http://&lt;TU_IP&gt;:8081
 ⚡ REDIS:
   REDIS UI      -&gt; http://&lt;TU_IP&gt;:5540
 📜 LOGS:
   SEQ LOGS      -&gt; http://&lt;TU_IP&gt;:8083
   DOZZLE        -&gt; http://&lt;TU_IP&gt;:8082
 🐳 DOCKER:
   PORTAINER     -&gt; http://&lt;TU_IP&gt;:9000</pre>
        </div>

        <h3>Comandos principales</h3>
        <div class="table-wrap">
          <table>
            <thead>
              <tr><th>Comando</th><th>Descripción</th></tr>
            </thead>
            <tbody>
              <tr><td>make up</td><td>Levanta todo el stack (prod + tools)</td></tr>
              <tr><td>make prod</td><td>Solo levanta los servicios de backend</td></tr>
              <tr><td>make tools</td><td>Solo levanta las herramientas (Portainer, Seq, etc.)</td></tr>
              <tr><td>make down</td><td>Apaga todos los contenedores</td></tr>
              <tr><td>make restart</td><td>Reinicia todos los contenedores</td></tr>
              <tr><td>make rebuild</td><td>Reconstruye y vuelve a levantar todas las imágenes</td></tr>
              <tr><td>make clean</td><td>Apaga todo y elimina volúmenes e imágenes</td></tr>
            </tbody>
          </table>
        </div>

        <h3>Logs</h3>
        <div class="table-wrap">
          <table>
            <thead>
              <tr><th>Comando</th><th>Descripción</th></tr>
            </thead>
            <tbody>
              <tr><td>make logs</td><td>Logs en vivo de todos los servicios</td></tr>
              <tr><td>make logs-api</td><td>Logs del contenedor <code>uni-chat-api</code></td></tr>
              <tr><td>make logs-nginx</td><td>Logs del contenedor <code>uni-chat-nginx</code></td></tr>
              <tr><td>make logs-mongo</td><td>Logs del contenedor <code>mongodb</code></td></tr>
              <tr><td>make logs-redis</td><td>Logs del contenedor <code>redis</code></td></tr>
              <tr><td>make logs-rabbit</td><td>Logs del contenedor <code>rabbitmq</code></td></tr>
            </tbody>
          </table>
        </div>

        <h3>Estado e información</h3>
        <div class="table-wrap">
          <table>
            <thead>
              <tr><th>Comando</th><th>Descripción</th></tr>
            </thead>
            <tbody>
              <tr><td>make ps</td><td>Lista los contenedores activos</td></tr>
              <tr><td>make info</td><td>Muestra IP, usuario, fecha, estado Docker, disco y RAM</td></tr>
            </tbody>
          </table>
        </div>
      </section>

      <!-- ── SERVICIOS ── -->
      <section id="servicios">
        <div class="section-label">// 06 — services</div>
        <h2><span class="h2-icon">🌐</span> Servicios disponibles</h2>
        <p>Una vez que el stack esté corriendo con <code>make up</code>, accede a cada servicio desde tu red local:</p>

        <div class="services-grid">
          <div class="service-card">
            <span class="service-emoji">🔥</span>
            <div class="service-name">API — Scalar</div>
            <div class="service-url">http://&lt;TU_IP&gt;/scalar</div>
            <div class="service-desc">Documentación interactiva de la API (OpenAPI / Scalar UI)</div>
          </div>
          <div class="service-card">
            <span class="service-emoji">🐇</span>
            <div class="service-name">RabbitMQ UI</div>
            <div class="service-url">http://&lt;TU_IP&gt;:15672</div>
            <div class="service-desc">Panel de administración de colas y exchanges de RabbitMQ</div>
          </div>
          <div class="service-card">
            <span class="service-emoji">🍃</span>
            <div class="service-name">Mongo Express</div>
            <div class="service-url">http://&lt;TU_IP&gt;:8081</div>
            <div class="service-desc">Interfaz web para explorar y administrar MongoDB</div>
          </div>
          <div class="service-card">
            <span class="service-emoji">⚡</span>
            <div class="service-name">Redis UI</div>
            <div class="service-url">http://&lt;TU_IP&gt;:5540</div>
            <div class="service-desc">Interfaz web para inspeccionar claves y datos en Redis</div>
          </div>
          <div class="service-card">
            <span class="service-emoji">📜</span>
            <div class="service-name">Seq Logs</div>
            <div class="service-url">http://&lt;TU_IP&gt;:8083</div>
            <div class="service-desc">Visor de logs estructurados con filtros y búsqueda</div>
          </div>
          <div class="service-card">
            <span class="service-emoji">📜</span>
            <div class="service-name">Dozzle</div>
            <div class="service-url">http://&lt;TU_IP&gt;:8082</div>
            <div class="service-desc">Logs en tiempo real de todos los contenedores Docker</div>
          </div>
          <div class="service-card">
            <span class="service-emoji">🐳</span>
            <div class="service-name">Portainer</div>
            <div class="service-url">http://&lt;TU_IP&gt;:9000</div>
            <div class="service-desc">Panel visual para administrar contenedores, imágenes y redes Docker</div>
          </div>
        </div>

        <div class="callout green-callout" style="margin-top:20px">
          <span class="icon">💡</span>
          <div class="callout-body">
            Reemplaza <strong>&lt;TU_IP&gt;</strong> con tu IP real en la red local.
            Usa <strong>make help</strong> o <strong>make info</strong> para verla automáticamente en tu terminal.
          </div>
        </div>
      </section>

      <!-- ── PROBLEMAS ── -->
      <section id="problemas">
        <div class="section-label">// 07 — troubleshooting</div>
        <h2><span class="h2-icon">🚨</span> Solución de problemas</h2>

        <div class="table-wrap">
          <table>
            <thead>
              <tr><th>Problema</th><th>Solución</th></tr>
            </thead>
            <tbody>
              <tr>
                <td class="problem">make: command not found</td>
                <td class="solution">Ejecuta <code>sudo apt install make -y</code></td>
              </tr>
              <tr>
                <td class="problem">docker: command not found</td>
                <td class="solution">Instala Docker Engine desde <code>docs.docker.com/engine/install</code></td>
              </tr>
              <tr>
                <td class="problem">Puerto ya en uso</td>
                <td class="solution">Ejecuta <code>make down</code> y luego <code>make up</code> de nuevo</td>
              </tr>
              <tr>
                <td class="problem">IP muestra 127.0.0.1</td>
                <td class="solution">Verifica tu conexión de red; en WSL2 asegúrate de estar en la red correcta</td>
              </tr>
              <tr>
                <td class="problem">Contenedor no inicia</td>
                <td class="solution">Revisa los logs con <code>make logs</code> o <code>make logs-&lt;servicio&gt;</code></td>
              </tr>
              <tr>
                <td class="problem">Cambios en compose no aplicados</td>
                <td class="solution">Usa <code>make rebuild</code> para forzar reconstrucción de imágenes</td>
              </tr>
              <tr>
                <td class="problem">Quiero limpiar todo desde cero</td>
                <td class="solution"><code>make clean</code> elimina contenedores, volúmenes e imágenes</td>
              </tr>
            </tbody>
          </table>
        </div>
      </section>

    </div><!-- /content -->
  </div><!-- /main -->

  <script>
    // Highlight active nav link on scroll
    const sections = document.querySelectorAll('section[id]');
    const links    = document.querySelectorAll('.nav-link');

    const observer = new IntersectionObserver(entries => {
      entries.forEach(e => {
        if (e.isIntersecting) {
          links.forEach(l => l.classList.remove('active'));
          const active = document.querySelector(`.nav-link[href="#${e.target.id}"]`);
          if (active) active.classList.add('active');
        }
      });
    }, { threshold: 0.4 });

    sections.forEach(s => observer.observe(s));
  </script>
</body>
</html>

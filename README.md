<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Daniel Dippel — Asesor de Propiedades</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,500;1,400;1,500&family=Lora:ital,wght@0,400;0,500;1,400&family=Nunito:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --tierra: #7C5C3E;
    --tierra-light: #A0795A;
    --tierra-pale: #C4A882;
    --verde: #4A6741;
    --verde-light: #6B8F62;
    --verde-pale: #C8D9C4;
    --crema: #F7F1E8;
    --crema-2: #EEE4D2;
    --crema-3: #E3D5BF;
    --cafe: #3B2A1A;
    --cafe-2: #5C3D22;
    --text: #3B2A1A;
    --text-mid: #6B5240;
    --text-soft: #9A8070;
    --white: #FDFAF5;
    --serif: 'Playfair Display', Georgia, serif;
    --body: 'Lora', Georgia, serif;
    --sans: 'Nunito', sans-serif;
  }

  html { scroll-behavior: smooth; }

  body {
    font-family: var(--body);
    background: var(--crema);
    color: var(--text);
    line-height: 1.7;
    overflow-x: hidden;
  }

  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%23000000' fill-opacity='0.015'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 0;
  }

  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1.2rem 5%;
    background: rgba(247,241,232,0.96);
    border-bottom: 1.5px solid var(--crema-3);
    backdrop-filter: blur(8px);
    transition: box-shadow 0.3s;
  }
  nav.scrolled { box-shadow: 0 2px 20px rgba(60,40,20,0.08); }

  .nav-logo { display: flex; flex-direction: column; text-decoration: none; }
  .nav-logo-name {
    font-family: var(--serif);
    font-size: 1.15rem;
    font-weight: 500;
    color: var(--cafe);
    line-height: 1.1;
  }
  .nav-logo-sub {
    font-family: var(--sans);
    font-size: 0.65rem;
    font-weight: 400;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--tierra-light);
  }

  .nav-cta {
    font-family: var(--sans);
    font-size: 0.8rem;
    font-weight: 500;
    color: var(--white);
    background: var(--verde);
    text-decoration: none;
    padding: 0.6rem 1.4rem;
    border-radius: 30px;
    transition: background 0.2s;
  }
  .nav-cta:hover { background: var(--verde-light); }

  /* HERO */
  .hero {
    min-height: 100vh;
    display: grid;
    grid-template-columns: 1fr 1fr;
    align-items: center;
    padding: 6rem 5% 4rem;
    gap: 4rem;
    position: relative;
    z-index: 1;
  }

  .hero-left { animation: fadeUp 0.9s ease both; }

  .hero-badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: var(--verde-pale);
    color: var(--verde);
    font-family: var(--sans);
    font-size: 0.72rem;
    font-weight: 500;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    padding: 0.4rem 1rem;
    border-radius: 30px;
    margin-bottom: 1.5rem;
  }

  .hero h1 {
    font-family: var(--serif);
    font-size: clamp(2.4rem, 4.5vw, 3.8rem);
    font-weight: 400;
    line-height: 1.15;
    color: var(--cafe);
    margin-bottom: 1.2rem;
  }
  .hero h1 em { font-style: italic; color: var(--tierra); }

  .hero-sub {
    font-size: 1rem;
    color: var(--text-mid);
    line-height: 1.8;
    margin-bottom: 2rem;
    max-width: 440px;
  }

  .hero-firma {
    display: flex;
    align-items: center;
    gap: 14px;
    margin-bottom: 2rem;
    padding: 1rem 1.2rem;
    background: var(--white);
    border: 1.5px solid var(--crema-3);
    border-radius: 12px;
    max-width: 360px;
  }
  .firma-avatar {
    width: 52px; height: 52px;
    border-radius: 50%;
    background: var(--crema-3);
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: var(--serif);
    font-size: 1.2rem;
    color: var(--tierra);
    flex-shrink: 0;
    border: 2px solid var(--tierra-pale);
  }
  .firma-info strong {
    display: block;
    font-family: var(--serif);
    font-size: 0.95rem;
    font-weight: 500;
    color: var(--cafe);
  }
  .firma-info span {
    font-family: var(--sans);
    font-size: 0.75rem;
    color: var(--text-soft);
  }

  .hero-actions { display: flex; gap: 12px; flex-wrap: wrap; }

  .btn-primary {
    display: inline-block;
    background: var(--tierra);
    color: var(--white);
    font-family: var(--sans);
    font-size: 0.85rem;
    font-weight: 500;
    padding: 0.85rem 1.8rem;
    border-radius: 8px;
    text-decoration: none;
    transition: background 0.2s;
  }
  .btn-primary:hover { background: var(--tierra-light); }

  .btn-ghost {
    display: inline-block;
    color: var(--verde);
    font-family: var(--sans);
    font-size: 0.85rem;
    font-weight: 500;
    padding: 0.85rem 1.8rem;
    border-radius: 8px;
    border: 1.5px solid var(--verde-pale);
    text-decoration: none;
    transition: all 0.2s;
    background: transparent;
  }
  .btn-ghost:hover { background: var(--verde-pale); }

  .hero-right { position: relative; animation: fadeUp 0.9s 0.2s ease both; }

  .hero-img-wrap {
    position: relative;
    border-radius: 16px;
    overflow: hidden;
    aspect-ratio: 4/5;
    max-height: 560px;
  }
  .hero-img-wrap img { width: 100%; height: 100%; object-fit: cover; display: block; }

  .hero-img-card {
    position: absolute;
    bottom: 1.5rem; left: 1.5rem; right: 1.5rem;
    background: rgba(247,241,232,0.95);
    backdrop-filter: blur(8px);
    border-radius: 10px;
    padding: 1rem 1.2rem;
    border: 1px solid rgba(255,255,255,0.6);
  }
  .hero-img-card p {
    font-family: var(--serif);
    font-size: 0.95rem;
    font-style: italic;
    color: var(--cafe);
    line-height: 1.5;
  }
  .hero-img-card span {
    font-family: var(--sans);
    font-size: 0.72rem;
    color: var(--text-soft);
    display: block;
    margin-top: 0.4rem;
  }

  /* SOBRE MÍ */
  .sobre-mi {
    padding: 5rem 5%;
    background: var(--white);
    position: relative;
    z-index: 1;
    border-top: 1.5px solid var(--crema-3);
    border-bottom: 1.5px solid var(--crema-3);
  }
  .sobre-inner {
    max-width: 860px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: auto 1fr;
    gap: 3.5rem;
    align-items: center;
  }
  .sobre-deco { text-align: center; }
  .sobre-icon { font-size: 3.5rem; display: block; margin-bottom: 0.5rem; }
  .sobre-linea { width: 1.5px; height: 80px; background: var(--crema-3); margin: 0 auto; }
  .sobre-texto blockquote {
    font-family: var(--serif);
    font-size: clamp(1.15rem, 2.5vw, 1.5rem);
    font-style: italic;
    color: var(--cafe);
    line-height: 1.5;
    margin-bottom: 1rem;
    border-left: 3px solid var(--tierra-pale);
    padding-left: 1.5rem;
  }
  .sobre-texto p { font-size: 0.95rem; color: var(--text-mid); line-height: 1.8; }

  /* SERVICIOS */
  .servicios {
    padding: 6rem 5%;
    background: var(--crema);
    position: relative;
    z-index: 1;
  }
  .section-header { text-align: center; margin-bottom: 3.5rem; }
  .section-tag {
    display: inline-block;
    font-family: var(--sans);
    font-size: 0.65rem;
    font-weight: 500;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--verde);
    background: var(--verde-pale);
    padding: 0.3rem 0.9rem;
    border-radius: 20px;
    margin-bottom: 1rem;
  }
  .section-title {
    font-family: var(--serif);
    font-size: clamp(1.8rem, 3.5vw, 2.8rem);
    font-weight: 400;
    color: var(--cafe);
    line-height: 1.2;
  }
  .section-title em { font-style: italic; color: var(--tierra); }

  .servicios-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 1.5rem;
    max-width: 1000px;
    margin: 0 auto;
  }
  .servicio-card {
    background: var(--white);
    border: 1.5px solid var(--crema-3);
    border-radius: 16px;
    padding: 2.2rem 1.8rem;
    transition: transform 0.2s, box-shadow 0.2s;
  }
  .servicio-card:hover { transform: translateY(-4px); box-shadow: 0 8px 32px rgba(60,40,20,0.08); }
  .servicio-emoji { font-size: 2.2rem; display: block; margin-bottom: 1rem; }
  .servicio-card h3 {
    font-family: var(--serif);
    font-size: 1.4rem;
    font-weight: 500;
    color: var(--cafe);
    margin-bottom: 0.6rem;
  }
  .servicio-card p { font-size: 0.875rem; color: var(--text-mid); line-height: 1.75; margin-bottom: 1.2rem; }
  .servicio-link {
    font-family: var(--sans);
    font-size: 0.78rem;
    font-weight: 500;
    color: var(--tierra);
    text-decoration: none;
    display: inline-flex;
    align-items: center;
    gap: 6px;
  }
  .servicio-link:hover { color: var(--tierra-light); }
  .servicio-link::after { content: '→'; }

  /* CONFIANZA */
  .confianza {
    padding: 4rem 5%;
    background: var(--cafe);
    position: relative;
    z-index: 1;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
  }
  .confianza-item {
    padding: 2rem 1.5rem;
    text-align: center;
    border-right: 1px solid rgba(255,255,255,0.08);
  }
  .confianza-item:last-child { border-right: none; }
  .confianza-num {
    font-family: var(--serif);
    font-size: 2.8rem;
    font-weight: 400;
    color: var(--tierra-pale);
    line-height: 1;
    margin-bottom: 0.4rem;
  }
  .confianza-label {
    font-family: var(--sans);
    font-size: 0.75rem;
    color: rgba(255,255,255,0.5);
  }

  /* FORMULARIO */
  .formulario {
    padding: 6rem 5%;
    background: var(--crema-2);
    position: relative;
    z-index: 1;
  }
  .form-layout {
    display: grid;
    grid-template-columns: 1fr 1.1fr;
    gap: 4rem;
    align-items: start;
    max-width: 980px;
    margin: 0 auto;
  }
  .form-intro .section-title { text-align: left; margin-bottom: 1rem; }
  .form-intro > p { font-size: 0.95rem; color: var(--text-mid); line-height: 1.8; margin-bottom: 1.5rem; }

  .beneficios { list-style: none; }
  .beneficios li {
    font-family: var(--sans);
    font-size: 0.875rem;
    color: var(--text-mid);
    padding: 0.55rem 0;
    border-bottom: 1px dashed var(--crema-3);
    display: flex;
    align-items: flex-start;
    gap: 10px;
  }
  .beneficios li::before { content: '✓'; color: var(--verde); font-weight: 500; flex-shrink: 0; margin-top: 1px; }

  .contacto-directo {
    margin-top: 1.8rem;
    padding: 1rem 1.2rem;
    background: var(--white);
    border-radius: 10px;
    border: 1.5px solid var(--crema-3);
    font-family: var(--sans);
    font-size: 0.82rem;
    color: var(--text-mid);
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .contacto-directo strong { color: var(--cafe); }

  .lead-form {
    background: var(--white);
    border-radius: 16px;
    border: 1.5px solid var(--crema-3);
    padding: 2.2rem;
    position: relative;
    overflow: hidden;
  }
  .lead-form::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 4px;
    background: linear-gradient(90deg, var(--tierra), var(--tierra-pale), var(--verde));
  }
  .form-title {
    font-family: var(--serif);
    font-size: 1.3rem;
    font-weight: 500;
    color: var(--cafe);
    margin-bottom: 1.5rem;
  }

  .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
  .form-group { margin-bottom: 0.9rem; }
  .form-group.full { grid-column: 1 / -1; }
  .form-group label {
    display: block;
    font-family: var(--sans);
    font-size: 0.72rem;
    font-weight: 500;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    color: var(--text-soft);
    margin-bottom: 5px;
  }
  .form-group input,
  .form-group select,
  .form-group textarea {
    width: 100%;
    padding: 0.7rem 0.9rem;
    border: 1.5px solid var(--crema-3);
    border-radius: 8px;
    background: var(--crema);
    font-family: var(--sans);
    font-size: 0.875rem;
    color: var(--text);
    outline: none;
    transition: border-color 0.2s, background 0.2s;
    appearance: none;
    -webkit-appearance: none;
  }
  .form-group input:focus,
  .form-group select:focus,
  .form-group textarea:focus { border-color: var(--tierra-light); background: var(--white); }
  .form-group textarea { resize: vertical; min-height: 80px; }

  .select-wrap { position: relative; }
  .select-wrap::after {
    content: '▾';
    position: absolute;
    right: 12px; top: 50%;
    transform: translateY(-50%);
    color: var(--tierra);
    pointer-events: none;
    font-size: 0.8rem;
  }

  .form-submit {
    width: 100%;
    padding: 0.95rem;
    background: var(--tierra);
    color: var(--white);
    border: none;
    border-radius: 8px;
    font-family: var(--sans);
    font-size: 0.875rem;
    font-weight: 500;
    cursor: pointer;
    transition: background 0.2s;
    margin-top: 0.4rem;
  }
  .form-submit:hover { background: var(--tierra-light); }

  .form-success { display: none; text-align: center; padding: 2.5rem 1.5rem; }
  .form-success .check { font-size: 2.5rem; margin-bottom: 1rem; display: block; }
  .form-success h4 {
    font-family: var(--serif);
    font-size: 1.5rem;
    font-weight: 400;
    color: var(--cafe);
    margin-bottom: 0.5rem;
  }
  .form-success p { font-size: 0.875rem; color: var(--text-mid); line-height: 1.7; }

  .privacy-note {
    font-family: var(--sans);
    font-size: 0.68rem;
    color: var(--text-soft);
    text-align: center;
    margin-top: 0.75rem;
  }

  footer {
    padding: 2.5rem 5%;
    background: var(--cafe-2);
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 1rem;
    position: relative;
    z-index: 1;
  }
  .footer-logo {
    font-family: var(--serif);
    font-size: 1.1rem;
    font-weight: 400;
    color: var(--crema);
  }
  .footer-copy { font-family: var(--sans); font-size: 0.72rem; color: rgba(255,255,255,0.4); }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(28px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  .reveal {
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible { opacity: 1; transform: none; }

  @media (max-width: 820px) {
    .hero { grid-template-columns: 1fr; padding-top: 7rem; }
    .hero-right { display: none; }
    .sobre-inner { grid-template-columns: 1fr; gap: 1.5rem; }
    .sobre-deco { display: none; }
    .form-layout { grid-template-columns: 1fr; gap: 2rem; }
    .form-row { grid-template-columns: 1fr; }
    .confianza-item { border-right: none; border-bottom: 1px solid rgba(255,255,255,0.08); }
  }
  @media (max-width: 480px) {
    .hero-actions { flex-direction: column; }
    .confianza { grid-template-columns: repeat(2, 1fr); }
  }
</style>
</head>
<body>

<nav id="navbar">
  <a href="#" class="nav-logo">
    <span class="nav-logo-name">Daniel Dippel</span>
    <span class="nav-logo-sub">Gestión Agencia Inmobiliaria</span>
  </a>
  <a href="#contacto" class="nav-cta">Escríbeme</a>
</nav>

<section class="hero">
  <div class="hero-left">
    <div class="hero-badge">🌿 Gestión Agencia Inmobiliaria</div>
    <h1>Te ayudo a encontrar<br>la propiedad <em>que buscas</em>,<br>sin vueltas</h1>
    <p class="hero-sub">Más de 10 años acompañando familias y personas en la compra, venta y tasación de propiedades. Trato directo, honesto y sin letra chica.</p>

    <div class="hero-firma">
      <div class="firma-avatar">DD</div>
      <div class="firma-info">
        <strong>Daniel Dippel</strong>
        <span>Gestión Agencia Inmobiliaria</span>
      </div>
    </div>

    <div class="hero-actions">
      <a href="#contacto" class="btn-primary">Solicitar asesoría gratis</a>
      <a href="#servicios" class="btn-ghost">Ver servicios</a>
    </div>
  </div>

  <div class="hero-right">
    <div class="hero-img-wrap">
      <img src="https://images.unsplash.com/photo-1570129477492-45c003edd2be?w=800&q=80" alt="Casa campo chilena">
      <div class="hero-img-card">
        <p>"Cada propiedad tiene su historia, y yo te ayudo a escribir la tuya."</p>
        <span>— Daniel Dippel</span>
      </div>
    </div>
  </div>
</section>

<section class="sobre-mi">
  <div class="sobre-inner reveal">
    <div class="sobre-deco">
      <span class="sobre-icon">🌾</span>
      <div class="sobre-linea"></div>
    </div>
    <div class="sobre-texto">
      <blockquote>Soy una persona independiente, no una empresa. Cuando me contratas, hablas directamente conmigo.</blockquote>
      <p>Trabajo en la Región de Los Lagos y Los Ríos desde hace más de una década. Conozco el mercado local como la palma de mi mano. Mi objetivo es simple: que tomes la mejor decisión con información clara y sin presiones.</p>
    </div>
  </div>
</section>

<section class="servicios" id="servicios">
  <div class="section-header reveal">
    <span class="section-tag">¿En qué te puedo ayudar?</span>
    <h2 class="section-title">Servicios <em>personalizados</em></h2>
  </div>

  <div class="servicios-grid">
    <div class="servicio-card reveal">
      <span class="servicio-emoji">🏡</span>
      <h3>Compra</h3>
      <p>Te acompaño desde la búsqueda hasta la firma. Analizo opciones, negocio por ti y te digo la verdad aunque no sea lo que querías escuchar.</p>
      <a href="#contacto" class="servicio-link">Quiero comprar</a>
    </div>
    <div class="servicio-card reveal" style="transition-delay:0.1s">
      <span class="servicio-emoji">🔑</span>
      <h3>Venta</h3>
      <p>Pongo tu propiedad en el valor que le corresponde, con difusión real y compradores serios. Sin comisiones exageradas.</p>
      <a href="#contacto" class="servicio-link">Quiero vender</a>
    </div>
    <div class="servicio-card reveal" style="transition-delay:0.2s">
      <span class="servicio-emoji">📋</span>
      <h3>Tasación</h3>
      <p>Informe de tasación con respaldo técnico, útil para bancos, herencias, divisiones y decisiones de inversión.</p>
      <a href="#contacto" class="servicio-link">Necesito una tasación</a>
    </div>
  </div>
</section>

<div class="confianza">
  <div class="confianza-item reveal">
    <div class="confianza-num">+10</div>
    <div class="confianza-label">Años de experiencia</div>
  </div>
  <div class="confianza-item reveal" style="transition-delay:0.1s">
    <div class="confianza-num">+300</div>
    <div class="confianza-label">Familias asesoradas</div>
  </div>
  <div class="confianza-item reveal" style="transition-delay:0.2s">
    <div class="confianza-num">+150</div>
    <div class="confianza-label">Tasaciones realizadas</div>
  </div>
  <div class="confianza-item reveal" style="transition-delay:0.3s">
    <div class="confianza-num">100%</div>
    <div class="confianza-label">Trato directo y personal</div>
  </div>
</div>

<section class="formulario" id="contacto">
  <div class="form-layout">
    <div class="form-intro reveal">
      <span class="section-tag">Conversemos</span>
      <h2 class="section-title">Cuéntame<br><em>qué necesitas</em></h2>
      <p>Llena el formulario y te respondo yo mismo por WhatsApp, generalmente el mismo día. Sin secretarias ni call centers.</p>

      <ul class="beneficios">
        <li>Primera consulta completamente gratuita</li>
        <li>Hablas conmigo directamente, siempre</li>
        <li>Conozco la Región de Los Lagos y Los Ríos en detalle</li>
        <li>Tasaciones con validez para bancos e instituciones</li>
        <li>Sin letras chicas ni compromisos</li>
      </ul>

      <div class="contacto-directo">
        💬 <span>También puedes escribirme directo: <strong>+56 9 7834 4513</strong></span>
      </div>
    </div>

    <div class="reveal" style="transition-delay:0.15s">
      <form class="lead-form" id="leadForm" onsubmit="submitForm(event)">
        <h3 class="form-title">Enviarme un mensaje</h3>

        <div class="form-row">
          <div class="form-group">
            <label>Nombre</label>
            <input type="text" name="nombre" placeholder="Tu nombre" required>
          </div>
          <div class="form-group">
            <label>Apellido</label>
            <input type="text" name="apellido" placeholder="Tu apellido">
          </div>
        </div>

        <div class="form-row">
          <div class="form-group">
            <label>Teléfono</label>
            <input type="tel" name="tel" placeholder="+56 9 XXXX XXXX" required>
          </div>
          <div class="form-group">
            <label>Email (opcional)</label>
            <input type="email" name="email" placeholder="tu@correo.com">
          </div>
        </div>

        <div class="form-row">
          <div class="form-group">
            <label>¿Qué necesitas?</label>
            <div class="select-wrap">
              <select name="servicio" required>
                <option value="">Seleccionar...</option>
                <option>Compra</option>
                <option>Venta</option>
                <option>Tasación</option>
              </select>
            </div>
          </div>
          <div class="form-group">
            <label>Tipo de propiedad</label>
            <div class="select-wrap">
              <select name="tipo">
                <option value="">Seleccionar...</option>
                <option>Casa</option>
                <option>Departamento</option>
                <option>Terreno</option>
                <option>Parcela / Campo</option>
                <option>Local comercial</option>
                <option>Otro</option>
              </select>
            </div>
          </div>
        </div>

        <div class="form-group full">
          <label>Sector o comuna</label>
          <input type="text" name="comuna" placeholder="Ej: Puerto Montt, Osorno, Valdivia...">
        </div>

        <div class="form-group full">
          <label>Presupuesto o valor estimado</label>
          <input type="text" name="presupuesto" placeholder="Ej: UF 2.000 — UF 4.000">
        </div>

        <div class="form-group full">
          <label>Cuéntame más (opcional)</label>
          <textarea name="mensaje" placeholder="¿Qué buscas? ¿Hay algo específico que necesites saber?"></textarea>
        </div>

        <button type="submit" class="form-submit">💬 Enviar por WhatsApp</button>
        <p class="privacy-note">Tu información es solo para que yo pueda contactarte. Nada más.</p>
      </form>

      <div class="form-success" id="formSuccess">
        <span class="check">🌿</span>
        <h4>¡Mensaje listo!</h4>
        <p>Se abrió WhatsApp con tu consulta ya escrita. Envíala y te respondo personalmente a la brevedad.</p>
      </div>
    </div>
  </div>
</section>

<footer>
  <div class="footer-logo">Daniel Dippel · Asesor de Propiedades</div>
  <div class="footer-copy">© 2026 · Región de Los Lagos & Los Ríos</div>
</footer>

<script>
  const navbar = document.getElementById('navbar');
  window.addEventListener('scroll', () => {
    navbar.classList.toggle('scrolled', window.scrollY > 50);
  });

  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
  }, { threshold: 0.1 });
  reveals.forEach(el => observer.observe(el));

  const WA_NUMBER = '56978344513';

  function submitForm(e) {
    e.preventDefault();
    const form = document.getElementById('leadForm');
    const success = document.getElementById('formSuccess');
    const data = new FormData(form);
    const lead = Object.fromEntries(data.entries());

    const mensaje =
      `🌿 *Nueva consulta de propiedad*\n` +
      `────────────────────\n` +
      `👤 *Nombre:* ${lead.nombre} ${lead.apellido || ''}\n` +
      `📞 *Teléfono:* ${lead.tel}\n` +
      `📧 *Email:* ${lead.email || '—'}\n` +
      `🔑 *Servicio:* ${lead.servicio}\n` +
      `🏡 *Propiedad:* ${lead.tipo || '—'}\n` +
      `📍 *Sector:* ${lead.comuna || '—'}\n` +
      `💰 *Presupuesto:* ${lead.presupuesto || '—'}\n` +
      `💬 *Mensaje:* ${lead.mensaje || '—'}\n` +
      `────────────────────\n` +
      `🕐 ${new Date().toLocaleString('es-CL')}`;

    const waUrl = `https://wa.me/${WA_NUMBER}?text=${encodeURIComponent(mensaje)}`;
    window.open(waUrl, '_blank');
    form.style.display = 'none';
    success.style.display = 'block';
  }
</script>
</body>
</html>

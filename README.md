<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>El Camino de las Ánimas - Manuscrito</title>
  
  <!-- Tipografías: Cinzel (Títulos), Share Tech Mono (Cuerpo retro), VT323 (Pixel UI) -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@700;900&family=Share+Tech+Mono&family=VT323&display=swap" rel="stylesheet">
  
  <style>
    :root {
      --bg-dark: #040205;
      --card-bg: rgba(13, 5, 16, 0.9);
      --border-crimson: #5c1430;
      --glow-crimson: #e6005c;
      --glow-amber: #ff8800;
      --text-main: #d8c8d0;
      --text-muted: #997e8b;
      --radius: 6px;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      background-color: var(--bg-dark);
      background-image: 
        radial-gradient(circle at 50% 10%, #290619 0%, transparent 50%),
        radial-gradient(circle at 50% 90%, #150311 0%, transparent 70%);
      color: var(--text-main);
      font-family: 'Share Tech Mono', monospace;
      line-height: 1.8;
      padding: 30px 15px;
      display: flex;
      justify-content: center;
      position: relative;
    }

    /* Efecto Scanlines CRT */
    body::before {
      content: " ";
      display: block;
      position: fixed;
      top: 0; left: 0; bottom: 0; right: 0;
      background: linear-gradient(rgba(18, 16, 16, 0) 50%, rgba(0, 0, 0, 0.4) 50%);
      background-size: 100% 4px;
      z-index: 20;
      pointer-events: none;
      opacity: 0.75;
    }

    .container {
      max-width: 860px;
      width: 100%;
      display: flex;
      flex-direction: column;
      gap: 3.5rem;
      z-index: 1;
    }

    /* Header y Título Principal */
    .hero-header {
      text-align: center;
      padding: 2rem 1rem;
      border-bottom: 2px solid var(--border-crimson);
      position: relative;
    }

    .hero-title {
      font-family: 'Cinzel', serif;
      font-size: 2.4rem;
      font-weight: 900;
      color: #ffb3ce;
      text-shadow: 0 0 15px rgba(230, 0, 92, 0.7), 2px 2px 4px #000;
      letter-spacing: 3px;
      margin-bottom: 0.5rem;
    }

    .hero-subtitle {
      font-family: 'VT323', monospace;
      font-size: 1.5rem;
      color: var(--glow-amber);
      letter-spacing: 2px;
    }

    /* Botón de Demo Jugable Principal */
    .demo-banner {
      background: radial-gradient(circle, rgba(230, 0, 92, 0.25) 0%, rgba(20, 5, 15, 0.95) 100%);
      border: 2px solid var(--glow-crimson);
      border-radius: var(--radius);
      padding: 1.5rem;
      text-align: center;
      box-shadow: 0 0 25px rgba(230, 0, 92, 0.3);
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 1rem;
    }

    .btn-play {
      display: inline-block;
      background: var(--glow-crimson);
      color: #ffffff;
      font-family: 'VT323', monospace;
      font-size: 1.8rem;
      text-decoration: none;
      padding: 0.8rem 2.5rem;
      border-radius: 4px;
      letter-spacing: 2px;
      box-shadow: 0 0 15px rgba(230, 0, 92, 0.8);
      transition: all 0.3s ease;
      text-transform: uppercase;
      border: none;
    }

    .btn-play:hover {
      background: #ff1a75;
      box-shadow: 0 0 25px rgba(255, 26, 117, 1);
      transform: scale(1.03);
    }

    /* Estructura de Capítulos / Tarjetas */
    .chapter-card {
      background: var(--card-bg);
      backdrop-filter: blur(10px);
      -webkit-backdrop-filter: blur(10px);
      border: 1px solid var(--border-crimson);
      border-radius: var(--radius);
      padding: 2.5rem;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.8), inset 0 0 20px rgba(0, 0, 0, 0.9);
      position: relative;
    }

    /* Indicador Numérico de Capítulo */
    .chapter-tag {
      font-family: 'VT323', monospace;
      font-size: 1.2rem;
      color: var(--glow-amber);
      letter-spacing: 2px;
      text-transform: uppercase;
      display: block;
      margin-bottom: 0.3rem;
    }

    h2 {
      font-family: 'Cinzel', serif;
      font-size: 1.6rem;
      color: #ffccd9;
      text-shadow: 0 0 8px rgba(230, 0, 92, 0.5);
      margin-bottom: 1.5rem;
      border-bottom: 1px solid rgba(92, 20, 48, 0.6);
      padding-bottom: 8px;
    }

    p {
      margin-bottom: 1.2rem;
      font-size: 1.05rem;
    }

    /* Tension Phrases (Frases cortas estilizadas) */
    .tension-phrase {
      font-family: 'Cinzel', serif;
      color: #ffffff;
      font-size: 1.15rem;
      margin: 0.5rem 0;
      letter-spacing: 1px;
    }

    .quote-box {
      border-left: 3px solid var(--glow-crimson);
      background: rgba(230, 0, 92, 0.05);
      padding: 1rem 1.2rem;
      margin: 1.5rem 0;
      font-style: italic;
      color: #f0d5e0;
    }

    /* Slot de Imagen de Ancho Completo con CRT Mirroring */
    .image-slot {
      width: 100%;
      min-height: 250px;
      background: #0d040a;
      border: 2px dashed var(--border-crimson);
      border-radius: 8px;
      margin: 2rem 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      position: relative;
      overflow: hidden;
      box-shadow: 0 0 15px rgba(0, 0, 0, 0.9);
    }

    .image-slot img {
      width: 100%;
      height: auto;
      display: block;
      image-rendering: pixelated;
    }

    .image-placeholder-text {
      font-family: 'VT323', monospace;
      color: var(--text-muted);
      font-size: 1.2rem;
      text-align: center;
      padding: 20px;
      letter-spacing: 1px;
    }

    /* Grilla de Bestiario / Leyendas */
    .bestiary-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 15px;
      margin: 1.5rem 0;
    }

    .bestiary-item {
      background: rgba(30, 8, 20, 0.7);
      border: 1px solid var(--border-crimson);
      padding: 12px 15px;
      border-radius: 4px;
      font-family: 'VT323', monospace;
      font-size: 1.3rem;
      color: #ffb8d1;
      display: flex;
      align-items: center;
      gap: 10px;
    }

    /* Lista de Checkmarks */
    .checklist {
      list-style: none;
      margin: 1.5rem 0;
    }

    .checklist li {
      padding: 8px 0;
      border-bottom: 1px dashed rgba(92, 20, 48, 0.4);
      display: flex;
      align-items: center;
      gap: 10px;
      color: #e6d5dc;
    }

    .checklist li::before {
      content: '✔';
      color: var(--glow-amber);
      font-weight: bold;
    }

    /* Footer de Llamada a la Acción (Vaki) */
    .vaki-cta {
      text-align: center;
      background: radial-gradient(circle, rgba(50, 8, 30, 0.95) 0%, rgba(10, 2, 8, 1) 100%);
      border: 2px solid var(--glow-crimson);
    }

    @media (max-width: 600px) {
      .hero-title { font-size: 1.8rem; }
      .chapter-card { padding: 1.5rem; }
      body { padding: 15px 10px; }
      .bestiary-grid { grid-template-columns: 1fr; }
    }
  </style>
</head>
<body>

  <main class="container">

    <!-- Header Principal -->
    <header class="hero-header">
      <h1 class="hero-title">El Camino de las Ánimas</h1>
      <p class="hero-subtitle">🕯️ UN GRIMORIO INTERACTIVO DEL FOLCLOR COLOMBIANO</p>
    </header>

    <!-- Banner Demo Jugable -->
    <section class="demo-banner">
      <p class="tension-phrase">¿TE ATREVES A DAR EL PRIMER PASO EN LA PENUMBRA?</p>
      <a href="https://lole07.github.io/Animas/" target="_blank" rel="noopener" class="btn-play">
        ▶ PROBAR DEMO JUGABLE AHORA
      </a>
      <p style="font-size: 0.9rem; color: var(--text-muted); margin: 0;">Prototipo funcional jugable directamente desde tu navegador.</p>
    </section>

    <!-- CAPÍTULO I -->
    <article class="chapter-card">
      <span class="chapter-tag">Capítulo I</span>
      <h2>Antes de que existieran los videojuegos... existían las historias</h2>
      
      <!-- Slot de Imagen 1 -->
      <div class="image-slot">
        <!-- Reemplaza esta etiqueta <img> cuando tengas la imagen lista -->
        <div class="image-placeholder-text">🖼️ [IMAGEN PANORÁMICA DEL CAMINO Y EL FAROL]</div>
      </div>

      <p class="tension-phrase">¿Recuerdas la primera vez que alguien te habló de La Llorona?</p>
      <p class="tension-phrase">¿De La Patasola?</p>
      <p class="tension-phrase">¿Del Silbón?</p>

      <p>Tal vez fue tu abuela. Tal vez un vecino. Tal vez una historia que escuchaste cuando eras niño para que no salieras de casa al caer la noche.</p>
      
      <div class="quote-box">
        "Durante siglos... las leyendas colombianas viajaron de generación en generación. No estaban escritas en libros. Vivían en las voces de quienes las contaban."
      </div>

      <p>Pero el tiempo cambia todo. Hoy miles de niños conocen a Kratos, a Medusa, a Loki o a los Yokai. Pero muy pocos han tenido la oportunidad de descubrir la riqueza de las leyendas de Colombia.</p>
      <p class="lead-text" style="color: var(--glow-crimson);">Y cada historia que deja de contarse... es una parte de nuestra memoria que desaparece.</p>
    </article>

    <!-- CAPÍTULO II -->
    <article class="chapter-card">
      <span class="chapter-tag">Capítulo II</span>
      <h2>Por eso nació El Camino de las Ánimas</h2>

      <!-- Slot de Imagen 2 -->
      <div class="image-slot">
        <div class="image-placeholder-text">🖼️ [IMAGEN CINEMATOGRÁFICA DEL PROTAGONISTA CON EL FAROL]</div>
      </div>

      <p>No queremos hacer únicamente un videojuego. Queremos construir un universo inspirado en las historias que crecieron junto a nosotros.</p>
      <p>Un mundo donde el terror no nace de monstruos inventados; nace de los relatos que durante generaciones recorrieron nuestros pueblos.</p>

      <div class="quote-box">
        Cada escenario. Cada sonido. Cada criatura. Cada personaje.<br>
        Ha sido diseñado para rendir homenaje al folclor colombiano.
      </div>

      <p>Nuestro objetivo no es solo entretener. Queremos emocionar, despertar curiosidad y lograr que alguien termine esta aventura con el deseo de conocer la historia real detrás de cada leyenda.</p>
    </article>

    <!-- CAPÍTULO III -->
    <article class="chapter-card">
      <span class="chapter-tag">Capítulo III</span>
      <h2>Todo comienza con una cinta roja</h2>

      <!-- Slot de Imagen 3 -->
      <div class="image-slot">
        <div class="image-placeholder-text">🖼️ [IMAGEN DE LA CINTA ROJA SOBRE EL BARRO]</div>
      </div>

      <p class="tension-phrase">Una noche... todo cambia.</p>
      <p>Un padre despierta. El silencio invade la casa. Su hija, <strong style="color: var(--glow-amber);">Luz</strong>, ha desaparecido.</p>
      <p>No hay gritos. No hay respuestas. Solo una pequeña cinta roja abandonada sobre el barro.</p>

      <p class="tension-phrase">Nadie quiere seguir esas huellas.</p>
      <p>Porque todos conocen las historias. Todos saben qué ocurre cuando alguien se adentra en el Camino de las Ánimas.</p>
      
      <p>Pero un padre... no puede quedarse esperando. Con un viejo machete en una mano y el farol heredado de su padre en la otra, comienza un viaje que lo enfrentará a las leyendas más oscuras del folclor colombiano.</p>
    </article>

    <!-- CAPÍTULO IV -->
    <article class="chapter-card">
      <span class="chapter-tag">Capítulo IV</span>
      <h2>Cada paso te acerca a una leyenda</h2>

      <!-- Slot de Imagen 4 -->
      <div class="image-slot">
        <div class="image-placeholder-text">🖼️ [IMAGEN HORIZONTAL DE TODOS LOS ENEMIGOS Y CRIATURAS]</div>
      </div>

      <p>No recorrerás un simple mapa. Recorrerás nuestra memoria. Cada región representa una historia, cada enemigo representa una leyenda y cada victoria revela un nuevo fragmento del misterio.</p>

      <div class="bestiary-grid">
        <div class="bestiary-item">🌾 El Silbón</div>
        <div class="bestiary-item">🌧️ La Llorona</div>
        <div class="bestiary-item">🌳 La Madremonte</div>
        <div class="bestiary-item">🪦 La Patasola</div>
        <div class="bestiary-item">👁️ El Ángel de Mil Ojos</div>
        <div class="bestiary-item">⛪ El Cura sin Cabeza</div>
      </div>

      <p style="color: var(--glow-amber); font-weight: bold; margin-top: 1rem;">
        🌑 Y una presencia ancestral que observa desde la montaña...
      </p>
    </article>

    <!-- CAPÍTULO V -->
    <article class="chapter-card">
      <span class="chapter-tag">Capítulo V</span>
      <h2>¿Por qué Colombia necesita este videojuego?</h2>

      <p>Durante años hemos explorado mundos inspirados en la mitología griega, nórdica, japonesa o egipcia, demostrando que las leyendas pueden convertirse en experiencias inolvidables.</p>
      <p class="tension-phrase">Entonces nos hicimos una pregunta: ¿Y las nuestras?</p>
      <p>Colombia posee uno de los folclores más ricos de Latinoamérica. Sin embargo, muy pocas veces ha sido llevado al mundo de los videojuegos con una narrativa propia.</p>
      <p>No queremos copiar otros universos. Queremos demostrar que nuestras historias también pueden emocionar al mundo.</p>
    </article>

    <!-- CAPÍTULO VI -->
    <article class="chapter-card">
      <span class="chapter-tag">Capítulo VI</span>
      <h2>Este proyecto ya está caminando</h2>

      <!-- Slot de Imagen 5 -->
      <div class="image-slot">
        <div class="image-placeholder-text">🖼️ [IMAGEN O GIF DEL GAMEPLAY ACTUAL]</div>
      </div>

      <p>Este sueño ya dejó de ser una idea. Hoy existe una base sólida sobre la que seguimos construyendo:</p>

      <ul class="checklist">
        <li>Demo jugable completamente funcional</li>
        <li>Historia y guion estructurados</li>
        <li>Prototipo mecánico y ambiental</li>
        <li>Diseño de criaturas originales</li>
        <li>Escenarios inspirados en paisajes colombianos</li>
        <li>Arte conceptual y modelado 2D/3D</li>
        <li>Cinemáticas en desarrollo</li>
      </ul>
    </article>

    <!-- CAPÍTULO VII (CTA VAKI) -->
    <article class="chapter-card vaki-cta">
      <span class="chapter-tag">Capítulo VII</span>
      <h2 style="border: none; color: #ffffff;">¿Por qué necesitamos tu ayuda?</h2>

      <p>Los grandes videojuegos no nacen únicamente del presupuesto. Nacen de personas que creen en una visión.</p>
      <p>Esta Vaki no es solo una campaña para recaudar fondos: es una invitación a construir juntos un proyecto que represente la creatividad, el talento y las historias de nuestra tierra.</p>

      <!-- Slot de Imagen 6 (Opcional para recompensas/comunidad) -->
      <div class="image-slot" style="min-height: 180px;">
        <div class="image-placeholder-text">🖼️ [IMAGEN DE RECOMPENSAS / ARTE DE LA COMUNIDAD]</div>
      </div>

      <div class="quote-box" style="border-left-color: var(--glow-amber);">
        "Dentro de algunos años... alguien podría descubrir por primera vez quién fue La Madremonte, El Silbón o La Patasola gracias a que tú decidiste creer cuando este proyecto apenas comenzaba."
      </div>

      <p class="tension-phrase" style="color: var(--glow-amber); margin: 1.5rem 0;">
        NO ESTARÁS HACIENDO UNA DONACIÓN. ESTARÁS DEJANDO UNA HUELLA.
      </p>

      <a href="https://lole07.github.io/Animas/" target="_blank" rel="noopener" class="btn-play" style="margin-top: 1rem;">
        🩸 APOYAR EL PROYECTO & PROBAR DEMO
      </a>
    </article>

  </main>

</body>
</html>

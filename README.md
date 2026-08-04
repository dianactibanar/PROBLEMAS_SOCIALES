<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="description" content="Infografía interactiva sobre hitos históricos y académicos de los problemas sociales contemporáneos.">
<title>Problemas sociales contemporáneos — Línea del tiempo interactiva</title>
<style>
:root {
  --azul:#003057;
  --azul-2:#006A8E;
  --celeste:#00A9E0;
  --amarillo:#F2A900;
  --naranja:#F39200;
  --gris-900:#17212b;
  --gris-700:#44515e;
  --gris-500:#73808d;
  --gris-200:#dfe6eb;
  --gris-100:#f4f7f9;
  --blanco:#ffffff;
  --sombra:0 16px 46px rgba(0,48,87,.12);
}
*{box-sizing:border-box}
html{scroll-behavior:smooth}
body{
  margin:0;
  font-family:"Helvetica Neue",Arial,sans-serif;
  color:var(--gris-900);
  background:linear-gradient(180deg,#f7fafc 0,#fff 36%,#f4f7f9 100%);
  line-height:1.55;
}
a{color:inherit}
button,input{font:inherit}
button{cursor:pointer}
.topbar{
  position:sticky; top:0; z-index:50;
  background:rgba(255,255,255,.94);
  backdrop-filter:blur(12px);
  border-bottom:1px solid rgba(0,48,87,.12);
}
.topbar-inner{
  max-width:1280px; margin:auto; padding:10px 24px;
  display:flex; align-items:center; justify-content:space-between; gap:18px;
}
.brand-mini{display:flex;align-items:center;gap:10px;color:var(--azul);font-weight:800;letter-spacing:.02em}
.brand-star{
  width:30px;height:30px;background:var(--amarillo);
  clip-path:polygon(50% 0,61% 35%,98% 35%,68% 57%,79% 94%,50% 72%,21% 94%,32% 57%,2% 35%,39% 35%);
}
.top-actions{display:flex;gap:8px;flex-wrap:wrap}
.top-actions button,.top-actions a{
  border:1px solid var(--gris-200);background:#fff;color:var(--azul);
  border-radius:999px;padding:8px 13px;text-decoration:none;font-weight:700;font-size:.86rem;
}
.hero{
  background:
    radial-gradient(circle at 85% 20%,rgba(242,169,0,.28),transparent 23%),
    radial-gradient(circle at 75% 75%,rgba(0,169,224,.20),transparent 28%),
    linear-gradient(130deg,var(--azul) 0%,#004a73 58%,#006a8e 100%);
  color:white; overflow:hidden; position:relative;
}
.hero:after{
  content:"";position:absolute;right:-90px;bottom:-170px;width:420px;height:420px;
  border:44px solid rgba(255,255,255,.07);border-radius:50%;
}
.hero-inner{max-width:1280px;margin:auto;padding:72px 24px 64px;display:grid;grid-template-columns:1.3fr .7fr;gap:40px;align-items:end;position:relative;z-index:1}
.eyebrow{display:inline-flex;align-items:center;gap:8px;text-transform:uppercase;letter-spacing:.13em;font-size:.78rem;font-weight:800;color:#dceef8}
.eyebrow:before{content:"";width:34px;height:4px;background:var(--amarillo)}
h1{font-size:clamp(2.5rem,6vw,5.4rem);line-height:.98;margin:18px 0 20px;max-width:900px;letter-spacing:-.045em}
.hero p{font-size:1.12rem;max-width:780px;color:#e7f2f7;margin:0}
.hero-note{border-left:5px solid var(--amarillo);padding:18px 20px;background:rgba(255,255,255,.09);border-radius:0 14px 14px 0}
.hero-note strong{display:block;font-size:1.05rem;margin-bottom:6px}
.hero-note span{color:#e7f2f7;font-size:.92rem}
.hero-stats{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin-top:28px;max-width:700px}
.stat{background:rgba(255,255,255,.1);border:1px solid rgba(255,255,255,.16);padding:15px;border-radius:14px}
.stat b{font-size:1.45rem;display:block;color:var(--amarillo)}
.stat span{font-size:.8rem;color:#e7f2f7}
main{max-width:1280px;margin:auto;padding:36px 24px 80px}
.intro-grid{display:grid;grid-template-columns:1fr 1fr;gap:20px;margin-bottom:30px}
.intro-card{background:#fff;border:1px solid var(--gris-200);border-radius:18px;padding:24px;box-shadow:0 8px 25px rgba(0,48,87,.05)}
.intro-card h2{color:var(--azul);margin:0 0 10px;font-size:1.3rem}
.intro-card p{margin:0;color:var(--gris-700)}
.controls{background:#fff;border:1px solid var(--gris-200);border-radius:20px;padding:18px;box-shadow:var(--sombra);margin:26px 0;position:sticky;top:61px;z-index:35}
.controls-top{display:flex;gap:12px;align-items:center;justify-content:space-between;flex-wrap:wrap}
.search-wrap{flex:1;min-width:240px;position:relative}
.search-wrap input{width:100%;padding:12px 15px 12px 42px;border:1px solid var(--gris-200);border-radius:12px;background:var(--gris-100);outline:none}
.search-wrap:before{content:"⌕";position:absolute;left:15px;top:7px;font-size:1.35rem;color:var(--azul-2)}
.filters{display:flex;gap:7px;flex-wrap:wrap;margin-top:12px}
.filter{border:1px solid var(--gris-200);background:#fff;border-radius:999px;padding:8px 12px;font-size:.82rem;font-weight:700;color:var(--gris-700)}
.filter:hover,.filter.active{background:var(--azul);border-color:var(--azul);color:white}
.result-count{font-size:.86rem;color:var(--gris-500);font-weight:700}
.stage-nav{display:grid;grid-template-columns:repeat(6,1fr);gap:8px;margin:24px 0 34px}
.stage-link{text-align:left;border:0;background:#fff;border-top:5px solid var(--amarillo);padding:14px 12px;border-radius:5px 5px 14px 14px;box-shadow:0 8px 22px rgba(0,48,87,.08);color:var(--azul);font-weight:800;font-size:.8rem;min-height:90px}
.stage-link span{display:block;color:var(--naranja);font-size:.72rem;margin-bottom:5px}
.stage-link:hover{transform:translateY(-2px)}
.timeline{position:relative;max-width:1040px;margin:0 auto}
.timeline:before{content:"";position:absolute;left:74px;top:0;bottom:0;width:4px;background:linear-gradient(var(--amarillo),var(--azul-2),var(--celeste));border-radius:99px}
.event-card{display:grid;grid-template-columns:150px 1fr;gap:22px;position:relative;margin:0 0 24px}
.timeline-marker{position:relative;display:flex;justify-content:center;padding-top:24px}
.timeline-marker:after{content:"";position:absolute;right:64px;top:38px;width:20px;height:20px;background:var(--amarillo);border:5px solid white;border-radius:50%;box-shadow:0 0 0 2px var(--azul)}
.timeline-marker span{font-size:1.55rem;font-weight:900;color:var(--azul);position:absolute;left:0;top:23px}
.event-shell{background:white;border:1px solid var(--gris-200);border-radius:20px;overflow:hidden;box-shadow:0 12px 36px rgba(0,48,87,.08);transition:.25s}
.event-shell:hover{transform:translateY(-2px);box-shadow:var(--sombra)}
.event-head{width:100%;border:0;background:white;text-align:left;padding:24px 26px;color:inherit}
.event-meta{display:flex;justify-content:space-between;gap:10px;align-items:center}
.event-year{font-weight:900;color:var(--naranja);font-size:.9rem}
.event-type{font-size:.72rem;letter-spacing:.05em;text-transform:uppercase;color:var(--gris-500);font-weight:800}
.event-head h3{font-size:1.48rem;line-height:1.2;color:var(--azul);margin:8px 0 5px}
.author{font-weight:700;color:var(--azul-2);margin:0 0 12px;font-size:.92rem}
.summary{margin:0;color:var(--gris-700)}
.tags{display:flex;gap:6px;flex-wrap:wrap;margin-top:16px}
.tag{font-size:.72rem;font-weight:700;background:#eef6fa;color:var(--azul-2);border-radius:999px;padding:5px 8px}
.expand-label{display:inline-flex;align-items:center;gap:8px;margin-top:18px;color:var(--azul);font-weight:800;font-size:.84rem}
.plus{width:23px;height:23px;border-radius:50%;display:grid;place-items:center;background:var(--amarillo);color:var(--azul);font-size:1.15rem;transition:.2s}
.event-head[aria-expanded="true"] .plus{transform:rotate(45deg)}
.event-detail{border-top:1px solid var(--gris-200);padding:24px 26px;background:linear-gradient(180deg,#fbfdfe,#f4f7f9)}
.detail-grid{display:grid;grid-template-columns:1fr 1fr;gap:24px}
.detail-grid h4{color:var(--azul);margin:0 0 8px}
.detail-grid p,.detail-grid ul{color:var(--gris-700);margin-top:0}
.detail-grid ul{padding-left:20px}
.source-box{display:flex;align-items:center;justify-content:space-between;gap:16px;background:white;border-left:5px solid var(--amarillo);padding:16px;border-radius:0 12px 12px 0;margin-top:12px}
.source-kicker{display:block;font-size:.68rem;text-transform:uppercase;letter-spacing:.1em;color:var(--gris-500);font-weight:800}
.source-box strong{color:var(--azul);font-size:.9rem}
.source-actions{display:flex;gap:8px;flex-wrap:wrap;justify-content:flex-end}
.source-actions a,.source-actions button{border:0;border-radius:9px;padding:9px 11px;text-decoration:none;font-weight:800;font-size:.78rem}
.source-actions a{background:var(--azul);color:#fff}
.source-actions button{background:#eaf2f6;color:var(--azul)}
.hidden-card{display:none}
.no-results{display:none;text-align:center;padding:50px 20px;color:var(--gris-500)}
.section-title{margin:74px 0 22px;display:flex;align-items:end;justify-content:space-between;gap:20px}
.section-title h2{font-size:2rem;color:var(--azul);margin:0}
.section-title p{max-width:620px;color:var(--gris-700);margin:0}
.reading-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:16px}
.reading-card{background:#fff;padding:22px;border-radius:16px;border:1px solid var(--gris-200);border-bottom:5px solid var(--amarillo)}
.reading-card span{color:var(--naranja);font-weight:900;font-size:.8rem}
.reading-card h3{color:var(--azul);margin:7px 0}
.reading-card p{color:var(--gris-700);margin:0;font-size:.9rem}
.key-shifts{display:grid;grid-template-columns:repeat(5,1fr);gap:10px}
.shift{background:var(--azul);color:white;border-radius:15px;padding:18px;min-height:145px;position:relative;overflow:hidden}
.shift b{display:block;color:var(--amarillo);font-size:1.65rem;margin-bottom:8px}
.shift span{font-weight:800}
.shift small{display:block;color:#dceef8;margin-top:8px}
.sources{background:white;border-radius:20px;border:1px solid var(--gris-200);padding:20px 24px}
.sources ol{padding:0;margin:0;list-style:none}
.sources li{display:grid;grid-template-columns:55px 1fr 150px;gap:12px;padding:12px 0;border-bottom:1px solid var(--gris-200);align-items:start}
.sources li:last-child{border-bottom:0}
.sources li span{font-weight:900;color:var(--naranja)}
.sources li a{color:var(--azul);font-weight:700;text-decoration-thickness:1px;text-underline-offset:3px}
.sources li em{font-style:normal;color:var(--gris-500);font-size:.8rem;text-align:right}
.method-note{margin-top:18px;background:#fff8e5;border:1px solid #f6d987;border-radius:14px;padding:16px;color:#63501a}
.footer{background:var(--azul);color:white;padding:30px 24px}
.footer-inner{max-width:1280px;margin:auto;display:flex;justify-content:space-between;gap:20px;align-items:center}
.footer p{margin:0;color:#dceef8;font-size:.88rem}
.toast{position:fixed;right:22px;bottom:22px;background:var(--gris-900);color:white;padding:12px 16px;border-radius:10px;box-shadow:var(--sombra);opacity:0;transform:translateY(10px);pointer-events:none;transition:.25s;z-index:100}
.toast.show{opacity:1;transform:translateY(0)}
.progress-line{position:fixed;top:0;left:0;height:4px;background:var(--amarillo);width:0;z-index:100}
@media(max-width:1000px){
  .hero-inner{grid-template-columns:1fr}
  .stage-nav{grid-template-columns:repeat(3,1fr)}
  .reading-grid{grid-template-columns:repeat(2,1fr)}
  .key-shifts{grid-template-columns:repeat(2,1fr)}
}
@media(max-width:720px){
  .topbar-inner{padding:8px 14px} .brand-mini span{display:none}
  .hero-inner{padding:48px 18px} .hero-stats{grid-template-columns:1fr}
  main{padding:24px 14px 60px}
  .intro-grid,.detail-grid{grid-template-columns:1fr}
  .controls{top:50px}
  .stage-nav{grid-template-columns:1fr 1fr}
  .event-card{grid-template-columns:58px 1fr;gap:9px}
  .timeline:before{left:27px}
  .timeline-marker span{display:none}
  .timeline-marker:after{right:19px}
  .event-head,.event-detail{padding:19px}
  .event-head h3{font-size:1.23rem}
  .source-box{align-items:flex-start;flex-direction:column}
  .source-actions{justify-content:flex-start}
  .reading-grid,.key-shifts{grid-template-columns:1fr}
  .sources li{grid-template-columns:45px 1fr}
  .sources li em{grid-column:2;text-align:left}
  .section-title{align-items:flex-start;flex-direction:column}
  .footer-inner{flex-direction:column;align-items:flex-start}
}
@media print{
  .topbar,.controls,.top-actions,.stage-nav,.expand-label,.source-actions,.toast,.progress-line{display:none!important}
  .hero{background:white!important;color:var(--azul)!important;border-bottom:4px solid var(--amarillo)}
  .hero p,.hero-note span{color:var(--gris-700)!important}
  .hero-note{background:#f4f7f9}
  .event-detail{display:block!important}
  .event-card{break-inside:avoid}
  .event-shell{box-shadow:none}
  body{background:white}
}
</style>
</head>
<body>
<div class="progress-line" id="progressLine"></div>
<header class="topbar">
  <div class="topbar-inner">
    <div class="brand-mini"><div class="brand-star" aria-hidden="true"></div><span>Problemas Sociales Contemporáneos</span></div>
    <div class="top-actions">
      <button id="expandAll">Expandir todo</button>
      <button onclick="window.print()">Imprimir / PDF</button>
      <a href="#fuentes">Fuentes</a>
    </div>
  </div>
</header>

<section class="hero">
  <div class="hero-inner">
    <div>
      <span class="eyebrow">Línea del tiempo interactiva</span>
      <h1>Problemas sociales contemporáneos</h1>
      <p>Hitos históricos, académicos y normativos para comprender cómo las sociedades han definido, investigado y enfrentado la desigualdad, la exclusión, los riesgos y las crisis colectivas.</p>
      <div class="hero-stats">
        <div class="stat"><b>24</b><span>hitos documentados</span></div>
        <div class="stat"><b>180 años</b><span>de transformaciones</span></div>
        <div class="stat"><b>6</b><span>etapas analíticas</span></div>
      </div>
    </div>
    <aside class="hero-note">
      <strong>Clave para leer la infografía</strong>
      <span>Un problema social no es únicamente una condición dañina. También supone procesos de interpretación, visibilización, disputa, acción colectiva, respuesta institucional y distribución desigual de consecuencias.</span>
    </aside>
  </div>
</section>

<main>
  <section class="intro-grid">
    <article class="intro-card">
      <h2>¿Qué presenta esta línea del tiempo?</h2>
      <p>Una selección analítica —no exhaustiva— de documentos que modificaron la manera de entender los problemas sociales: desde la cuestión obrera y la pobreza urbana hasta la interseccionalidad, el cambio climático, el trabajo en plataformas y la crisis de confianza.</p>
    </article>
    <article class="intro-card">
      <h2>¿Cómo utilizarla?</h2>
      <p>Filtra por tema, busca un concepto y abre cada hito para consultar sus rasgos, su aporte conceptual y la fuente original. Los enlaces se abren en una pestaña nueva.</p>
    </article>
  </section>

  <section class="controls" aria-label="Controles de la línea del tiempo">
    <div class="controls-top">
      <div class="search-wrap"><input id="searchInput" type="search" placeholder="Buscar: pobreza, género, riesgo, Colombia, trabajo…" aria-label="Buscar en la línea del tiempo"></div>
      <span class="result-count" id="resultCount">24 hitos visibles</span>
    </div>
    <div class="filters"><button class="filter active" data-filter="Todos">Todos</button>
<button class="filter" data-filter="Desigualdad y trabajo">Desigualdad y trabajo</button>
<button class="filter" data-filter="Derechos y política">Derechos y política</button>
<button class="filter" data-filter="Teoría y método">Teoría y método</button>
<button class="filter" data-filter="Ambiente y salud">Ambiente y salud</button>
<button class="filter" data-filter="Género, raza e intersecciones">Género, raza e intersecciones</button>
<button class="filter" data-filter="Colombia">Colombia</button>
<button class="filter" data-filter="Digital y global">Digital y global</button></div>
  </section>

  <nav class="stage-nav" aria-label="Navegación por etapas">
    <button class="stage-link" data-stage="Cuestión social e industrialización"><span>1845–1903</span>Cuestión social e industrialización</button>
<button class="stage-link" data-stage="Institucionalización y derechos"><span>1919–1949</span>Institucionalización y derechos</button>
<button class="stage-link" data-stage="Ambiente, construcción social y riesgos"><span>1962–1986</span>Ambiente, construcción social y riesgos</button>
<button class="stage-link" data-stage="Interseccionalidad y desarrollo humano"><span>1989–1991</span>Interseccionalidad y desarrollo humano</button>
<button class="stage-link" data-stage="Problemas integrados y metas globales"><span>2000–2015</span>Problemas integrados y metas globales</button>
<button class="stage-link" data-stage="Crisis sistémicas y nuevas desigualdades"><span>2020–2025</span>Crisis sistémicas y nuevas desigualdades</button>
  </nav>

  <section class="timeline" id="timeline">
    
    <article class="event-card" id="evento-1" data-year="1845" data-stage="Cuestión social e industrialización" data-cats="Desigualdad y trabajo|Teoría y método" data-search="la cuestión social industrial entra en escena friedrich engels — la situación de la clase obrera en inglaterra la pobreza urbana, la enfermedad, la vivienda insalubre y la explotación laboral dejan de verse como infortunios aislados y se interpretan como efectos del capitalismo industrial. centralidad de la clase social y de las condiciones materiales de existencia. relación entre organización del trabajo, urbanización, salud y mortalidad. lectura estructural y conflictiva: los problemas se producen socialmente.">
      <div class="timeline-marker" aria-hidden="true"><span>1845</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-1">
          <div class="event-meta">
            <span class="event-year">1845</span>
            <span class="event-type">Documento histórico</span>
          </div>
          <h3>La cuestión social industrial entra en escena</h3>
          <p class="author">Friedrich Engels — La situación de la clase obrera en Inglaterra</p>
          <p class="summary">La pobreza urbana, la enfermedad, la vivienda insalubre y la explotación laboral dejan de verse como infortunios aislados y se interpretan como efectos del capitalismo industrial.</p>
          <div class="tags"><span class="tag">Desigualdad y trabajo</span><span class="tag">Teoría y método</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-1" hidden>
          <div class="detail-grid">
            <section>
              <h4>Rasgos principales</h4>
              <ul><li>Centralidad de la clase social y de las condiciones materiales de existencia.</li><li>Relación entre organización del trabajo, urbanización, salud y mortalidad.</li><li>Lectura estructural y conflictiva: los problemas se producen socialmente.</li></ul>
            </section>
            <section>
              <h4>¿Qué cambia en la comprensión?</h4>
              <p>Consolida una de las primeras grandes interpretaciones estructurales de la «cuestión social». Aunque es una obra polémica y situada, se convierte en un documento histórico clave para estudiar la industrialización y sus costos humanos.</p>
            </section>
          </div>
          <div class="source-box">
            <div>
              <span class="source-kicker">Documento o fuente clave</span>
              <strong>Engels, F. (1845). The Condition of the Working Class in England.</strong>
            </div>
            <div class="source-actions">
              <a href="https://www.marxists.org/archive/marx/works/1845/condition-working-class/index.htm" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a>
              <button class="copy-citation" data-citation="Engels, F. (1845). The Condition of the Working Class in England. https://www.marxists.org/archive/marx/works/1845/condition-working-class/index.htm">Copiar referencia</button>
            </div>
          </div>
        </div>
      </div>
    </article>
    
    <article class="event-card" id="evento-2" data-year="1889" data-stage="Cuestión social e industrialización" data-cats="Desigualdad y trabajo|Teoría y método" data-search="la pobreza se mide y se cartografía charles booth — maps descriptive of london poverty la investigación social empírica vincula territorio, ingresos, ocupación y condiciones de vida, haciendo visible la distribución espacial de la pobreza. uso combinado de observación, entrevistas, registros y mapas. clasificación territorial de niveles de pobreza y posición social. base temprana para diagnósticos sociales y políticas urbanas.">
      <div class="timeline-marker" aria-hidden="true"><span>1889</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-2">
          <div class="event-meta">
            <span class="event-year">1889</span>
            <span class="event-type">Archivo histórico</span>
          </div>
          <h3>La pobreza se mide y se cartografía</h3>
          <p class="author">Charles Booth — Maps Descriptive of London Poverty</p>
          <p class="summary">La investigación social empírica vincula territorio, ingresos, ocupación y condiciones de vida, haciendo visible la distribución espacial de la pobreza.</p>
          <div class="tags"><span class="tag">Desigualdad y trabajo</span><span class="tag">Teoría y método</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-2" hidden>
          <div class="detail-grid">
            <section>
              <h4>Rasgos principales</h4>
              <ul><li>Uso combinado de observación, entrevistas, registros y mapas.</li><li>Clasificación territorial de niveles de pobreza y posición social.</li><li>Base temprana para diagnósticos sociales y políticas urbanas.</li></ul>
            </section>
            <section>
              <h4>¿Qué cambia en la comprensión?</h4>
              <p>Marca el paso de la denuncia moral a la producción sistemática de evidencia social. También muestra que toda medición incorpora categorías y decisiones interpretativas.</p>
            </section>
          </div>
          <div class="source-box">
            <div>
              <span class="source-kicker">Documento o fuente clave</span>
              <strong>London School of Economics. What were the poverty maps?</strong>
            </div>
            <div class="source-actions">
              <a href="https://booth.lse.ac.uk/learn-more/what-were-the-poverty-maps" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a>
              <button class="copy-citation" data-citation="London School of Economics. What were the poverty maps? https://booth.lse.ac.uk/learn-more/what-were-the-poverty-maps">Copiar referencia</button>
            </div>
          </div>
        </div>
      </div>
    </article>
    
    <article class="event-card" id="evento-3" data-year="1897" data-stage="Cuestión social e industrialización" data-cats="Teoría y método|Ambiente y salud" data-search="incluso los actos individuales tienen causas sociales émile durkheim — el suicidio el suicidio se estudia mediante regularidades colectivas asociadas con la integración y la regulación social, no solo como decisión psicológica individual. distinción entre explicación individual y explicación sociológica. uso comparado de tasas y patrones sociales. importancia de los vínculos, normas e instituciones.">
      <div class="timeline-marker" aria-hidden="true"><span>1897</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-3">
          <div class="event-meta">
            <span class="event-year">1897</span>
            <span class="event-type">Obra académica</span>
          </div>
          <h3>Incluso los actos individuales tienen causas sociales</h3>
          <p class="author">Émile Durkheim — El suicidio</p>
          <p class="summary">El suicidio se estudia mediante regularidades colectivas asociadas con la integración y la regulación social, no solo como decisión psicológica individual.</p>
          <div class="tags"><span class="tag">Teoría y método</span><span class="tag">Ambiente y salud</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-3" hidden>
          <div class="detail-grid">
            <section>
              <h4>Rasgos principales</h4>
              <ul><li>Distinción entre explicación individual y explicación sociológica.</li><li>Uso comparado de tasas y patrones sociales.</li><li>Importancia de los vínculos, normas e instituciones.</li></ul>
            </section>
            <section>
              <h4>¿Qué cambia en la comprensión?</h4>
              <p>Fortalece la idea de «hecho social»: una situación puede manifestarse en individuos y, al mismo tiempo, depender de estructuras y relaciones colectivas.</p>
            </section>
          </div>
          <div class="source-box">
            <div>
              <span class="source-kicker">Documento o fuente clave</span>
              <strong>Durkheim, É. (1897). Le suicide. Étude de sociologie.</strong>
            </div>
            <div class="source-actions">
              <a href="https://classiques.uqam.ca/classiques/Durkheim_emile/suicide/suicide.html" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a>
              <button class="copy-citation" data-citation="Durkheim, É. (1897). Le suicide. Étude de sociologie. https://classiques.uqam.ca/classiques/Durkheim_emile/suicide/suicide.html">Copiar referencia</button>
            </div>
          </div>
        </div>
      </div>
    </article>
    
    <article class="event-card" id="evento-4" data-year="1903" data-stage="Cuestión social e industrialización" data-cats="Género, raza e intersecciones|Teoría y método" data-search="la “línea de color” como problema estructural w. e. b. du bois — the souls of black folk du bois sitúa el racismo, la segregación y la ciudadanía desigual en el centro de la modernidad, vinculando experiencia subjetiva e instituciones. racialización de oportunidades, derechos y reconocimiento. concepto de doble conciencia y experiencia de subordinación. crítica a explicaciones que responsabilizan a la población discriminada.">
      <div class="timeline-marker" aria-hidden="true"><span>1903</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-4">
          <div class="event-meta">
            <span class="event-year">1903</span>
            <span class="event-type">Obra académica</span>
          </div>
          <h3>La “línea de color” como problema estructural</h3>
          <p class="author">W. E. B. Du Bois — The Souls of Black Folk</p>
          <p class="summary">Du Bois sitúa el racismo, la segregación y la ciudadanía desigual en el centro de la modernidad, vinculando experiencia subjetiva e instituciones.</p>
          <div class="tags"><span class="tag">Género, raza e intersecciones</span><span class="tag">Teoría y método</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-4" hidden>
          <div class="detail-grid">
            <section>
              <h4>Rasgos principales</h4>
              <ul><li>Racialización de oportunidades, derechos y reconocimiento.</li><li>Concepto de doble conciencia y experiencia de subordinación.</li><li>Crítica a explicaciones que responsabilizan a la población discriminada.</li></ul>
            </section>
            <section>
              <h4>¿Qué cambia en la comprensión?</h4>
              <p>Amplía el análisis de los problemas sociales más allá de la clase e introduce una sociología histórica de la raza, el poder y la ciudadanía.</p>
            </section>
          </div>
          <div class="source-box">
            <div>
              <span class="source-kicker">Documento o fuente clave</span>
              <strong>Du Bois, W. E. B. (1903). The Souls of Black Folk.</strong>
            </div>
            <div class="source-actions">
              <a href="https://www.gutenberg.org/ebooks/408" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a>
              <button class="copy-citation" data-citation="Du Bois, W. E. B. (1903). The Souls of Black Folk. https://www.gutenberg.org/ebooks/408">Copiar referencia</button>
            </div>
          </div>
        </div>
      </div>
    </article>
    
    <article class="event-card" id="evento-5" data-year="1919" data-stage="Institucionalización y derechos" data-cats="Desigualdad y trabajo|Derechos y política" data-search="el trabajo digno se convierte en asunto internacional constitución de la organización internacional del trabajo tras la primera guerra mundial, la justicia social y las condiciones laborales se consideran requisitos de una paz duradera. normas internacionales sobre jornada, salario, seguridad y asociación. reconocimiento del conflicto laboral como cuestión pública. gobernanza tripartita: estados, empleadores y trabajadores.">
      <div class="timeline-marker" aria-hidden="true"><span>1919</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-5">
          <div class="event-meta">
            <span class="event-year">1919</span>
            <span class="event-type">Documento normativo</span>
          </div>
          <h3>El trabajo digno se convierte en asunto internacional</h3>
          <p class="author">Constitución de la Organización Internacional del Trabajo</p>
          <p class="summary">Tras la Primera Guerra Mundial, la justicia social y las condiciones laborales se consideran requisitos de una paz duradera.</p>
          <div class="tags"><span class="tag">Desigualdad y trabajo</span><span class="tag">Derechos y política</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-5" hidden>
          <div class="detail-grid">
            <section>
              <h4>Rasgos principales</h4>
              <ul><li>Normas internacionales sobre jornada, salario, seguridad y asociación.</li><li>Reconocimiento del conflicto laboral como cuestión pública.</li><li>Gobernanza tripartita: Estados, empleadores y trabajadores.</li></ul>
            </section>
            <section>
              <h4>¿Qué cambia en la comprensión?</h4>
              <p>Los problemas laborales dejan de depender exclusivamente de la caridad o de cada Estado y entran en un sistema internacional de estándares sociales.</p>
            </section>
          </div>
          <div class="source-box">
            <div>
              <span class="source-kicker">Documento o fuente clave</span>
              <strong>International Labour Organization. ILO Constitution (1919).</strong>
            </div>
            <div class="source-actions">
              <a href="https://normlex.ilo.org/dyn/nrmlx_en/f?p=1000:62:0::NO:62:P62_LIST_ENTRIE_ID:2453907:NO" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a>
              <button class="copy-citation" data-citation="International Labour Organization. ILO Constitution (1919). https://normlex.ilo.org/dyn/nrmlx_en/f?p=1000:62:0::NO:62:P62_LIST_ENTRIE_ID:2453907:NO">Copiar referencia</button>
            </div>
          </div>
        </div>
      </div>
    </article>
    
    <article class="event-card" id="evento-6" data-year="1942" data-stage="Institucionalización y derechos" data-cats="Desigualdad y trabajo|Derechos y política" data-search="el estado de bienestar responde a los “cinco gigantes” william beveridge — social insurance and allied services la pobreza, la enfermedad, la ignorancia, la insalubridad y el desempleo se organizan como riesgos sociales que requieren protección pública coherente. seguridad social y cobertura frente a riesgos del ciclo vital. responsabilidad estatal más allá de la filantropía. articulación entre empleo, salud, educación, vivienda e ingresos.">
      <div class="timeline-marker" aria-hidden="true"><span>1942</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-6">
          <div class="event-meta">
            <span class="event-year">1942</span>
            <span class="event-type">Informe gubernamental</span>
          </div>
          <h3>El Estado de bienestar responde a los “cinco gigantes”</h3>
          <p class="author">William Beveridge — Social Insurance and Allied Services</p>
          <p class="summary">La pobreza, la enfermedad, la ignorancia, la insalubridad y el desempleo se organizan como riesgos sociales que requieren protección pública coherente.</p>
          <div class="tags"><span class="tag">Desigualdad y trabajo</span><span class="tag">Derechos y política</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-6" hidden>
          <div class="detail-grid">
            <section>
              <h4>Rasgos principales</h4>
              <ul><li>Seguridad social y cobertura frente a riesgos del ciclo vital.</li><li>Responsabilidad estatal más allá de la filantropía.</li><li>Articulación entre empleo, salud, educación, vivienda e ingresos.</li></ul>
            </section>
            <section>
              <h4>¿Qué cambia en la comprensión?</h4>
              <p>Ofrece un modelo influyente de política social universal y consolida la idea de que los problemas sociales exigen sistemas, no intervenciones aisladas.</p>
            </section>
          </div>
          <div class="source-box">
            <div>
              <span class="source-kicker">Documento o fuente clave</span>
              <strong>UK Parliament. The 1942 Beveridge Report.</strong>
            </div>
            <div class="source-actions">
              <a href="https://www.parliament.uk/about/living-heritage/transformingsociety/livinglearning/coll-9-health1/coll-9-health/" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a>
              <button class="copy-citation" data-citation="UK Parliament. The 1942 Beveridge Report. https://www.parliament.uk/about/living-heritage/transformingsociety/livinglearning/coll-9-health1/coll-9-health/">Copiar referencia</button>
            </div>
          </div>
        </div>
      </div>
    </article>
    
    <article class="event-card" id="evento-7" data-year="1948" data-stage="Institucionalización y derechos" data-cats="Derechos y política|Género, raza e intersecciones" data-search="los problemas sociales se reformulan como vulneraciones de derechos declaración universal de los derechos humanos la dignidad, la igualdad y los derechos civiles, políticos, económicos, sociales y culturales se convierten en un referente universal. universalidad e indivisibilidad de los derechos. prohibición de discriminación y reconocimiento de derechos sociales. obligación de transformar instituciones que producen exclusión.">
      <div class="timeline-marker" aria-hidden="true"><span>1948</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-7">
          <div class="event-meta">
            <span class="event-year">1948</span>
            <span class="event-type">Documento internacional</span>
          </div>
          <h3>Los problemas sociales se reformulan como vulneraciones de derechos</h3>
          <p class="author">Declaración Universal de los Derechos Humanos</p>
          <p class="summary">La dignidad, la igualdad y los derechos civiles, políticos, económicos, sociales y culturales se convierten en un referente universal.</p>
          <div class="tags"><span class="tag">Derechos y política</span><span class="tag">Género, raza e intersecciones</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-7" hidden>
          <div class="detail-grid">
            <section>
              <h4>Rasgos principales</h4>
              <ul><li>Universalidad e indivisibilidad de los derechos.</li><li>Prohibición de discriminación y reconocimiento de derechos sociales.</li><li>Obligación de transformar instituciones que producen exclusión.</li></ul>
            </section>
            <section>
              <h4>¿Qué cambia en la comprensión?</h4>
              <p>Introduce un lenguaje normativo para evaluar condiciones sociales: no solo hay necesidades o carencias, también hay titulares de derechos y responsables de garantía.</p>
            </section>
          </div>
          <div class="source-box">
            <div>
              <span class="source-kicker">Documento o fuente clave</span>
              <strong>Naciones Unidas. Declaración Universal de los Derechos Humanos (1948).</strong>
            </div>
            <div class="source-actions">
              <a href="https://www.un.org/es/about-us/universal-declaration-of-human-rights" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a>
              <button class="copy-citation" data-citation="Naciones Unidas. Declaración Universal de los Derechos Humanos (1948). https://www.un.org/es/about-us/universal-declaration-of-human-rights">Copiar referencia</button>
            </div>
          </div>
        </div>
      </div>
    </article>
    

    <article class="event-card" id="evento-23" data-year="1949" data-stage="Institucionalización y derechos" data-cats="Desigualdad y trabajo|Teoría y método|Digital y global" data-search="américa latina interpreta el subdesarrollo como relación estructural raúl prebisch cepal centro periferia la desigualdad internacional no se explica como simple atraso interno sino por una inserción asimétrica en la economía mundial. estructura centro periferia. deterioro de los términos de intercambio. necesidad de transformación productiva y políticas de desarrollo propias.">
      <div class="timeline-marker" aria-hidden="true"><span>1949</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-23">
          <div class="event-meta"><span class="event-year">1949</span><span class="event-type">Pensamiento latinoamericano</span></div>
          <h3>América Latina interpreta el subdesarrollo como relación estructural</h3>
          <p class="author">Raúl Prebisch — CEPAL</p>
          <p class="summary">La desigualdad internacional deja de explicarse como simple atraso interno y se vincula con una inserción asimétrica entre centros industriales y periferias exportadoras.</p>
          <div class="tags"><span class="tag">Desigualdad y trabajo</span><span class="tag">Teoría y método</span><span class="tag">Digital y global</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-23" hidden>
          <div class="detail-grid">
            <section><h4>Rasgos principales</h4><ul><li>Estructura centro–periferia.</li><li>Deterioro de los términos de intercambio.</li><li>Heterogeneidad productiva y dependencia externa.</li></ul></section>
            <section><h4>¿Qué cambia en la comprensión?</h4><p>Introduce una lectura latinoamericana de los problemas del desarrollo: pobreza, empleo y desigualdad se relacionan con la estructura productiva y con la posición de la región en la economía mundial.</p></section>
          </div>
          <div class="source-box"><div><span class="source-kicker">Documento o fuente clave</span><strong>Prebisch, R. (1949). El desarrollo económico de la América Latina y algunos de sus principales problemas.</strong></div><div class="source-actions"><a href="https://www.cepal.org/es/publicaciones/40010-desarrollo-economico-la-america-latina-algunos-sus-principales-problemas" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a><button class="copy-citation" data-citation="Prebisch, R. (1949). El desarrollo económico de la América Latina y algunos de sus principales problemas. CEPAL. https://www.cepal.org/es/publicaciones/40010-desarrollo-economico-la-america-latina-algunos-sus-principales-problemas">Copiar referencia</button></div></div>
        </div>
      </div>
    </article>

    <article class="event-card" id="evento-8" data-year="1962" data-stage="Ambiente, construcción social y riesgos" data-cats="Ambiente y salud|Derechos y política" data-search="el ambiente se reconoce como problema social y sanitario rachel carson — silent spring la contaminación química revela que el progreso tecnológico puede generar daños difusos, acumulativos y difíciles de revertir. interdependencia entre ecosistemas, salud humana y producción. conflictos entre evidencia científica, industria y regulación. daños transgeneracionales y distribución desigual de la exposición.">
      <div class="timeline-marker" aria-hidden="true"><span>1962</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-8">
          <div class="event-meta">
            <span class="event-year">1962</span>
            <span class="event-type">Historia institucional</span>
          </div>
          <h3>El ambiente se reconoce como problema social y sanitario</h3>
          <p class="author">Rachel Carson — Silent Spring</p>
          <p class="summary">La contaminación química revela que el progreso tecnológico puede generar daños difusos, acumulativos y difíciles de revertir.</p>
          <div class="tags"><span class="tag">Ambiente y salud</span><span class="tag">Derechos y política</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-8" hidden>
          <div class="detail-grid">
            <section>
              <h4>Rasgos principales</h4>
              <ul><li>Interdependencia entre ecosistemas, salud humana y producción.</li><li>Conflictos entre evidencia científica, industria y regulación.</li><li>Daños transgeneracionales y distribución desigual de la exposición.</li></ul>
            </section>
            <section>
              <h4>¿Qué cambia en la comprensión?</h4>
              <p>Contribuye al ambientalismo contemporáneo y cuestiona la idea de que todo avance técnico equivale automáticamente a bienestar social.</p>
            </section>
          </div>
          <div class="source-box">
            <div>
              <span class="source-kicker">Documento o fuente clave</span>
              <strong>U.S. Environmental Protection Agency. The Origins of EPA.</strong>
            </div>
            <div class="source-actions">
              <a href="https://www.epa.gov/history/origins-epa" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a>
              <button class="copy-citation" data-citation="U.S. Environmental Protection Agency. The Origins of EPA. https://www.epa.gov/history/origins-epa">Copiar referencia</button>
            </div>
          </div>
        </div>
      </div>
    </article>
    
    <article class="event-card" id="evento-9" data-year="1971" data-stage="Ambiente, construcción social y riesgos" data-cats="Teoría y método" data-search="un problema social también debe ser reconocido colectivamente herbert blumer — social problems as collective behavior las condiciones objetivas no se convierten automáticamente en problemas públicos: deben ser nombradas, legitimadas, movilizadas y disputadas. procesos de definición colectiva y competencia por atención pública. papel de movimientos sociales, medios, expertos e instituciones. diferencia entre daño existente y reconocimiento político del daño.">
      <div class="timeline-marker" aria-hidden="true"><span>1971</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-9">
          <div class="event-meta">
            <span class="event-year">1971</span>
            <span class="event-type">Artículo académico</span>
          </div>
          <h3>Un problema social también debe ser reconocido colectivamente</h3>
          <p class="author">Herbert Blumer — Social Problems as Collective Behavior</p>
          <p class="summary">Las condiciones objetivas no se convierten automáticamente en problemas públicos: deben ser nombradas, legitimadas, movilizadas y disputadas.</p>
          <div class="tags"><span class="tag">Teoría y método</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-9" hidden>
          <div class="detail-grid">
            <section>
              <h4>Rasgos principales</h4>
              <ul><li>Procesos de definición colectiva y competencia por atención pública.</li><li>Papel de movimientos sociales, medios, expertos e instituciones.</li><li>Diferencia entre daño existente y reconocimiento político del daño.</li></ul>
            </section>
            <section>
              <h4>¿Qué cambia en la comprensión?</h4>
              <p>Inaugura un giro construccionista: estudiar un problema implica analizar quién lo define, con qué lenguaje, frente a qué oposiciones y con qué efectos.</p>
            </section>
          </div>
          <div class="source-box">
            <div>
              <span class="source-kicker">Documento o fuente clave</span>
              <strong>Blumer, H. (1971). Social Problems as Collective Behavior. Social Problems, 18(3), 298–306.</strong>
            </div>
            <div class="source-actions">
              <a href="https://www.jstor.org/stable/799797" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a>
              <button class="copy-citation" data-citation="Blumer, H. (1971). Social Problems as Collective Behavior. Social Problems, 18(3), 298–306. https://www.jstor.org/stable/799797">Copiar referencia</button>
            </div>
          </div>
        </div>
      </div>
    </article>
    
    <article class="event-card" id="evento-10" data-year="1972" data-stage="Ambiente, construcción social y riesgos" data-cats="Ambiente y salud|Teoría y método" data-search="los límites planetarios entran al debate social club de roma — the limits to growth los modelos de dinámica de sistemas muestran que población, producción, recursos y contaminación están interconectados en un planeta finito. pensamiento sistémico y retroalimentaciones. crítica al crecimiento ilimitado. escenarios de largo plazo y prevención.">
      <div class="timeline-marker" aria-hidden="true"><span>1972</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-10">
          <div class="event-meta">
            <span class="event-year">1972</span>
            <span class="event-type">Informe científico</span>
          </div>
          <h3>Los límites planetarios entran al debate social</h3>
          <p class="author">Club de Roma — The Limits to Growth</p>
          <p class="summary">Los modelos de dinámica de sistemas muestran que población, producción, recursos y contaminación están interconectados en un planeta finito.</p>
          <div class="tags"><span class="tag">Ambiente y salud</span><span class="tag">Teoría y método</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-10" hidden>
          <div class="detail-grid">
            <section>
              <h4>Rasgos principales</h4>
              <ul><li>Pensamiento sistémico y retroalimentaciones.</li><li>Crítica al crecimiento ilimitado.</li><li>Escenarios de largo plazo y prevención.</li></ul>
            </section>
            <section>
              <h4>¿Qué cambia en la comprensión?</h4>
              <p>Traslada el análisis desde problemas sectoriales hacia sistemas socioecológicos globales, aunque sus supuestos y escenarios han sido ampliamente debatidos.</p>
            </section>
          </div>
          <div class="source-box">
            <div>
              <span class="source-kicker">Documento o fuente clave</span>
              <strong>Club of Rome. The Limits to Growth (1972).</strong>
            </div>
            <div class="source-actions">
              <a href="https://www.clubofrome.org/publication/the-limits-to-growth/" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a>
              <button class="copy-citation" data-citation="Club of Rome. The Limits to Growth (1972). https://www.clubofrome.org/publication/the-limits-to-growth/">Copiar referencia</button>
            </div>
          </div>
        </div>
      </div>
    </article>
    
    <article class="event-card" id="evento-11" data-year="1979" data-stage="Ambiente, construcción social y riesgos" data-cats="Género, raza e intersecciones|Derechos y política" data-search="la desigualdad de género se reconoce como discriminación sistémica convención cedaw la discriminación contra las mujeres se aborda en la política, el trabajo, la educación, la salud, la familia y la cultura. conexión entre esfera pública y relaciones privadas. medidas legales e institucionales para la igualdad sustantiva. reconocimiento de estereotipos y tradiciones como mecanismos de desigualdad.">
      <div class="timeline-marker" aria-hidden="true"><span>1979</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-11">
          <div class="event-meta">
            <span class="event-year">1979</span>
            <span class="event-type">Tratado internacional</span>
          </div>
          <h3>La desigualdad de género se reconoce como discriminación sistémica</h3>
          <p class="author">Convención CEDAW</p>
          <p class="summary">La discriminación contra las mujeres se aborda en la política, el trabajo, la educación, la salud, la familia y la cultura.</p>
          <div class="tags"><span class="tag">Género, raza e intersecciones</span><span class="tag">Derechos y política</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-11" hidden>
          <div class="detail-grid">
            <section>
              <h4>Rasgos principales</h4>
              <ul><li>Conexión entre esfera pública y relaciones privadas.</li><li>Medidas legales e institucionales para la igualdad sustantiva.</li><li>Reconocimiento de estereotipos y tradiciones como mecanismos de desigualdad.</li></ul>
            </section>
            <section>
              <h4>¿Qué cambia en la comprensión?</h4>
              <p>Amplía el campo de los derechos humanos y muestra que la reproducción de los problemas sociales ocurre también en la vida cotidiana y familiar.</p>
            </section>
          </div>
          <div class="source-box">
            <div>
              <span class="source-kicker">Documento o fuente clave</span>
              <strong>Naciones Unidas. Convención sobre la Eliminación de Todas las Formas de Discriminación contra la Mujer (1979).</strong>
            </div>
            <div class="source-actions">
              <a href="https://www.un.org/womenwatch/daw/cedaw/cedaw.htm" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a>
              <button class="copy-citation" data-citation="Naciones Unidas. Convención sobre la Eliminación de Todas las Formas de Discriminación contra la Mujer (1979). https://www.un.org/womenwatch/daw/cedaw/cedaw.htm">Copiar referencia</button>
            </div>
          </div>
        </div>
      </div>
    </article>
    
    <article class="event-card" id="evento-12" data-year="1986" data-stage="Ambiente, construcción social y riesgos" data-cats="Ambiente y salud|Teoría y método|Digital y global" data-search="la modernidad produce sus propios riesgos ulrich beck — la sociedad del riesgo los riesgos tecnológicos, nucleares, ambientales y económicos son fabricados por sistemas modernos y atraviesan fronteras. riesgos invisibles o mediados por conocimiento experto. incertidumbre, controversia científica y dificultad de atribuir responsabilidades. distribución desigual del daño y capacidad desigual de protección.">
      <div class="timeline-marker" aria-hidden="true"><span>1986</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-12">
          <div class="event-meta">
            <span class="event-year">1986</span>
            <span class="event-type">Obra académica</span>
          </div>
          <h3>La modernidad produce sus propios riesgos</h3>
          <p class="author">Ulrich Beck — La sociedad del riesgo</p>
          <p class="summary">Los riesgos tecnológicos, nucleares, ambientales y económicos son fabricados por sistemas modernos y atraviesan fronteras.</p>
          <div class="tags"><span class="tag">Ambiente y salud</span><span class="tag">Teoría y método</span><span class="tag">Digital y global</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-12" hidden>
          <div class="detail-grid">
            <section>
              <h4>Rasgos principales</h4>
              <ul><li>Riesgos invisibles o mediados por conocimiento experto.</li><li>Incertidumbre, controversia científica y dificultad de atribuir responsabilidades.</li><li>Distribución desigual del daño y capacidad desigual de protección.</li></ul>
            </section>
            <section>
              <h4>¿Qué cambia en la comprensión?</h4>
              <p>Propone que el conflicto social ya no gira solo alrededor de la distribución de riqueza, sino también de la distribución de riesgos producidos.</p>
            </section>
          </div>
          <div class="source-box">
            <div>
              <span class="source-kicker">Documento o fuente clave</span>
              <strong>Beck, U. (1986). Risikogesellschaft: Auf dem Weg in eine andere Moderne.</strong>
            </div>
            <div class="source-actions">
              <a href="https://www.suhrkamp.de/rights/book/ulrich-beck-risk-society-fr-9783518113653" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a>
              <button class="copy-citation" data-citation="Beck, U. (1986). Risikogesellschaft: Auf dem Weg in eine andere Moderne. https://www.suhrkamp.de/rights/book/ulrich-beck-risk-society-fr-9783518113653">Copiar referencia</button>
            </div>
          </div>
        </div>
      </div>
    </article>
    
    <article class="event-card" id="evento-13" data-year="1989" data-stage="Interseccionalidad y desarrollo humano" data-cats="Género, raza e intersecciones|Teoría y método" data-search="la interseccionalidad cuestiona los análisis de un solo eje kimberlé crenshaw — demarginalizing the intersection of race and sex las desigualdades de género, raza y clase no operan de forma separada; su intersección produce experiencias y barreras específicas. crítica a categorías universales que invisibilizan diferencias internas. análisis simultáneo de sistemas de poder. consecuencias para el derecho, las políticas y la investigación.">
      <div class="timeline-marker" aria-hidden="true"><span>1989</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-13">
          <div class="event-meta">
            <span class="event-year">1989</span>
            <span class="event-type">Artículo académico</span>
          </div>
          <h3>La interseccionalidad cuestiona los análisis de un solo eje</h3>
          <p class="author">Kimberlé Crenshaw — Demarginalizing the Intersection of Race and Sex</p>
          <p class="summary">Las desigualdades de género, raza y clase no operan de forma separada; su intersección produce experiencias y barreras específicas.</p>
          <div class="tags"><span class="tag">Género, raza e intersecciones</span><span class="tag">Teoría y método</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-13" hidden>
          <div class="detail-grid">
            <section>
              <h4>Rasgos principales</h4>
              <ul><li>Crítica a categorías universales que invisibilizan diferencias internas.</li><li>Análisis simultáneo de sistemas de poder.</li><li>Consecuencias para el derecho, las políticas y la investigación.</li></ul>
            </section>
            <section>
              <h4>¿Qué cambia en la comprensión?</h4>
              <p>Transforma el estudio contemporáneo de los problemas sociales al exigir enfoques situados, relacionales y atentos a múltiples posiciones sociales.</p>
            </section>
          </div>
          <div class="source-box">
            <div>
              <span class="source-kicker">Documento o fuente clave</span>
              <strong>Crenshaw, K. (1989). Demarginalizing the Intersection of Race and Sex.</strong>
            </div>
            <div class="source-actions">
              <a href="https://chicagounbound.uchicago.edu/uclf/vol1989/iss1/8/" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a>
              <button class="copy-citation" data-citation="Crenshaw, K. (1989). Demarginalizing the Intersection of Race and Sex. https://chicagounbound.uchicago.edu/uclf/vol1989/iss1/8/">Copiar referencia</button>
            </div>
          </div>
        </div>
      </div>
    </article>
    
    <article class="event-card" id="evento-14" data-year="1990" data-stage="Interseccionalidad y desarrollo humano" data-cats="Desigualdad y trabajo|Derechos y política|Teoría y método" data-search="el desarrollo se mide por las capacidades de las personas pnud — primer informe sobre desarrollo humano el bienestar deja de reducirse al crecimiento económico y se examina mediante salud, educación, ingreso y ampliación de opciones humanas. personas como fin del desarrollo, no solo como recurso productivo. indicadores multidimensionales y comparación internacional. énfasis en oportunidades, capacidades y calidad de vida.">
      <div class="timeline-marker" aria-hidden="true"><span>1990</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-14">
          <div class="event-meta">
            <span class="event-year">1990</span>
            <span class="event-type">Informe internacional</span>
          </div>
          <h3>El desarrollo se mide por las capacidades de las personas</h3>
          <p class="author">PNUD — Primer Informe sobre Desarrollo Humano</p>
          <p class="summary">El bienestar deja de reducirse al crecimiento económico y se examina mediante salud, educación, ingreso y ampliación de opciones humanas.</p>
          <div class="tags"><span class="tag">Desigualdad y trabajo</span><span class="tag">Derechos y política</span><span class="tag">Teoría y método</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-14" hidden>
          <div class="detail-grid">
            <section>
              <h4>Rasgos principales</h4>
              <ul><li>Personas como fin del desarrollo, no solo como recurso productivo.</li><li>Indicadores multidimensionales y comparación internacional.</li><li>Énfasis en oportunidades, capacidades y calidad de vida.</li></ul>
            </section>
            <section>
              <h4>¿Qué cambia en la comprensión?</h4>
              <p>Reorienta el diagnóstico de pobreza y desarrollo hacia dimensiones humanas y abre el camino a mediciones multidimensionales.</p>
            </section>
          </div>
          <div class="source-box">
            <div>
              <span class="source-kicker">Documento o fuente clave</span>
              <strong>UNDP. Human Development Report 1990.</strong>
            </div>
            <div class="source-actions">
              <a href="https://hdr.undp.org/system/files/documents/hdr1990encompletenostats.pdf" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a>
              <button class="copy-citation" data-citation="UNDP. Human Development Report 1990. https://hdr.undp.org/system/files/documents/hdr1990encompletenostats.pdf">Copiar referencia</button>
            </div>
          </div>
        </div>
      </div>
    </article>
    
    <article class="event-card" id="evento-15" data-year="1991" data-stage="Interseccionalidad y desarrollo humano" data-cats="Colombia|Derechos y política|Género, raza e intersecciones" data-search="colombia adopta el estado social de derecho constitución política de colombia la dignidad, la participación, el pluralismo, la igualdad real y efectiva, los derechos sociales y la diversidad étnica y cultural se convierten en principios constitucionales. estado social de derecho y prevalencia del interés general. protección especial a grupos discriminados o marginados. reconocimiento de diversidad, participación y mecanismos de exigibilidad.">
      <div class="timeline-marker" aria-hidden="true"><span>1991</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-15">
          <div class="event-meta">
            <span class="event-year">1991</span>
            <span class="event-type">Documento constitucional</span>
          </div>
          <h3>Colombia adopta el Estado social de derecho</h3>
          <p class="author">Constitución Política de Colombia</p>
          <p class="summary">La dignidad, la participación, el pluralismo, la igualdad real y efectiva, los derechos sociales y la diversidad étnica y cultural se convierten en principios constitucionales.</p>
          <div class="tags"><span class="tag">Colombia</span><span class="tag">Derechos y política</span><span class="tag">Género, raza e intersecciones</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-15" hidden>
          <div class="detail-grid">
            <section>
              <h4>Rasgos principales</h4>
              <ul><li>Estado social de derecho y prevalencia del interés general.</li><li>Protección especial a grupos discriminados o marginados.</li><li>Reconocimiento de diversidad, participación y mecanismos de exigibilidad.</li></ul>
            </section>
            <section>
              <h4>¿Qué cambia en la comprensión?</h4>
              <p>Ofrece el marco jurídico central para interpretar los problemas sociales colombianos como asuntos de derechos, desigualdad territorial, exclusión y deberes estatales.</p>
            </section>
          </div>
          <div class="source-box">
            <div>
              <span class="source-kicker">Documento o fuente clave</span>
              <strong>Colombia. Constitución Política de 1991.</strong>
            </div>
            <div class="source-actions">
              <a href="https://www.secretariasenado.gov.co/senado/basedoc/constitucion_politica_1991.html" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a>
              <button class="copy-citation" data-citation="Colombia. Constitución Política de 1991. https://www.secretariasenado.gov.co/senado/basedoc/constitucion_politica_1991.html">Copiar referencia</button>
            </div>
          </div>
        </div>
      </div>
    </article>
    
    <article class="event-card" id="evento-16" data-year="2000" data-stage="Problemas integrados y metas globales" data-cats="Derechos y política|Desigualdad y trabajo|Digital y global" data-search="la pobreza global se traduce en metas verificables declaración del milenio de las naciones unidas los estados acuerdan objetivos cuantificables sobre pobreza, educación, salud, género y cooperación internacional. metas, indicadores y plazos comunes. coordinación de cooperación y financiamiento. mayor rendición de cuentas, con riesgo de simplificar realidades complejas.">
      <div class="timeline-marker" aria-hidden="true"><span>2000</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-16">
          <div class="event-meta">
            <span class="event-year">2000</span>
            <span class="event-type">Documento internacional</span>
          </div>
          <h3>La pobreza global se traduce en metas verificables</h3>
          <p class="author">Declaración del Milenio de las Naciones Unidas</p>
          <p class="summary">Los Estados acuerdan objetivos cuantificables sobre pobreza, educación, salud, género y cooperación internacional.</p>
          <div class="tags"><span class="tag">Derechos y política</span><span class="tag">Desigualdad y trabajo</span><span class="tag">Digital y global</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-16" hidden>
          <div class="detail-grid">
            <section>
              <h4>Rasgos principales</h4>
              <ul><li>Metas, indicadores y plazos comunes.</li><li>Coordinación de cooperación y financiamiento.</li><li>Mayor rendición de cuentas, con riesgo de simplificar realidades complejas.</li></ul>
            </section>
            <section>
              <h4>¿Qué cambia en la comprensión?</h4>
              <p>Consolida una gobernanza global basada en resultados y prepara el tránsito hacia una agenda más integral de desarrollo sostenible.</p>
            </section>
          </div>
          <div class="source-box">
            <div>
              <span class="source-kicker">Documento o fuente clave</span>
              <strong>Naciones Unidas. Declaración del Milenio (2000).</strong>
            </div>
            <div class="source-actions">
              <a href="https://www.un.org/esa/devagenda/millennium.html" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a>
              <button class="copy-citation" data-citation="Naciones Unidas. Declaración del Milenio (2000). https://www.un.org/esa/devagenda/millennium.html">Copiar referencia</button>
            </div>
          </div>
        </div>
      </div>
    </article>
    

    <article class="event-card" id="evento-24" data-year="2000" data-stage="Problemas integrados y metas globales" data-cats="Género, raza e intersecciones|Teoría y método|Digital y global" data-search="la colonialidad explica la persistencia histórica de jerarquías aníbal quijano colonialidad del poder eurocentrismo américa latina raza trabajo conocimiento autoridad modernidad colonialidad. persistencia de clasificaciones raciales. articulación entre capitalismo colonialismo y eurocentrismo. crítica a categorías universales desconectadas de la historia latinoamericana.">
      <div class="timeline-marker" aria-hidden="true"><span>2000</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-24">
          <div class="event-meta"><span class="event-year">2000</span><span class="event-type">Pensamiento latinoamericano</span></div>
          <h3>La colonialidad explica la persistencia histórica de jerarquías</h3>
          <p class="author">Aníbal Quijano — colonialidad del poder</p>
          <p class="summary">Las desigualdades contemporáneas se vinculan con clasificaciones raciales, formas de trabajo, autoridad y producción de conocimiento originadas en la experiencia colonial.</p>
          <div class="tags"><span class="tag">Género, raza e intersecciones</span><span class="tag">Teoría y método</span><span class="tag">Digital y global</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-24" hidden>
          <div class="detail-grid">
            <section><h4>Rasgos principales</h4><ul><li>Persistencia de clasificaciones raciales del poder.</li><li>Articulación entre capitalismo, colonialismo y eurocentrismo.</li><li>Crítica a categorías universales desconectadas de la historia latinoamericana.</li></ul></section>
            <section><h4>¿Qué cambia en la comprensión?</h4><p>Permite analizar racismo, desigualdad, exclusión epistémica y subordinación territorial como continuidades históricas, no únicamente como fallas recientes de integración.</p></section>
          </div>
          <div class="source-box"><div><span class="source-kicker">Documento o fuente clave</span><strong>Quijano, A. (2000). Colonialidad del poder, eurocentrismo y América Latina.</strong></div><div class="source-actions"><a href="https://biblioteca.clacso.edu.ar/clacso/se/20140507042402/eje3-8.pdf" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a><button class="copy-citation" data-citation="Quijano, A. (2000). Colonialidad del poder, eurocentrismo y América Latina. En E. Lander (comp.), La colonialidad del saber. CLACSO. https://biblioteca.clacso.edu.ar/clacso/se/20140507042402/eje3-8.pdf">Copiar referencia</button></div></div>
        </div>
      </div>
    </article>

    <article class="event-card" id="evento-17" data-year="2008" data-stage="Problemas integrados y metas globales" data-cats="Ambiente y salud|Desigualdad y trabajo|Derechos y política" data-search="la salud depende de las “causas de las causas” oms — comisión sobre determinantes sociales de la salud las inequidades en salud se explican por las condiciones en que las personas nacen, crecen, viven, trabajan y envejecen, y por la distribución del poder y los recursos. gradiente social de la salud. articulación entre territorio, empleo, género, educación, vivienda y protección social. equidad en salud como cuestión de justicia social.">
      <div class="timeline-marker" aria-hidden="true"><span>2008</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-17">
          <div class="event-meta">
            <span class="event-year">2008</span>
            <span class="event-type">Informe científico</span>
          </div>
          <h3>La salud depende de las “causas de las causas”</h3>
          <p class="author">OMS — Comisión sobre Determinantes Sociales de la Salud</p>
          <p class="summary">Las inequidades en salud se explican por las condiciones en que las personas nacen, crecen, viven, trabajan y envejecen, y por la distribución del poder y los recursos.</p>
          <div class="tags"><span class="tag">Ambiente y salud</span><span class="tag">Desigualdad y trabajo</span><span class="tag">Derechos y política</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-17" hidden>
          <div class="detail-grid">
            <section>
              <h4>Rasgos principales</h4>
              <ul><li>Gradiente social de la salud.</li><li>Articulación entre territorio, empleo, género, educación, vivienda y protección social.</li><li>Equidad en salud como cuestión de justicia social.</li></ul>
            </section>
            <section>
              <h4>¿Qué cambia en la comprensión?</h4>
              <p>Desplaza la intervención desde conductas individuales hacia estructuras sociales, políticas públicas e inequidades evitables.</p>
            </section>
          </div>
          <div class="source-box">
            <div>
              <span class="source-kicker">Documento o fuente clave</span>
              <strong>WHO. Closing the gap in a generation (2008).</strong>
            </div>
            <div class="source-actions">
              <a href="https://www.who.int/publications/i/item/9789241563703" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a>
              <button class="copy-citation" data-citation="WHO. Closing the gap in a generation (2008). https://www.who.int/publications/i/item/9789241563703">Copiar referencia</button>
            </div>
          </div>
        </div>
      </div>
    </article>
    
    <article class="event-card" id="evento-18" data-year="2015" data-stage="Problemas integrados y metas globales" data-cats="Derechos y política|Ambiente y salud|Desigualdad y trabajo|Digital y global" data-search="los problemas se integran en una agenda universal agenda 2030 y objetivos de desarrollo sostenible diecisiete objetivos conectan pobreza, desigualdad, género, salud, educación, trabajo, paz, instituciones y ambiente bajo el principio de no dejar a nadie atrás. universalidad: compromete a países de todos los niveles de ingreso. interdependencia de dimensiones sociales, económicas y ambientales. indicadores globales con necesidad de adaptación territorial.">
      <div class="timeline-marker" aria-hidden="true"><span>2015</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-18">
          <div class="event-meta">
            <span class="event-year">2015</span>
            <span class="event-type">Agenda internacional</span>
          </div>
          <h3>Los problemas se integran en una agenda universal</h3>
          <p class="author">Agenda 2030 y Objetivos de Desarrollo Sostenible</p>
          <p class="summary">Diecisiete objetivos conectan pobreza, desigualdad, género, salud, educación, trabajo, paz, instituciones y ambiente bajo el principio de no dejar a nadie atrás.</p>
          <div class="tags"><span class="tag">Derechos y política</span><span class="tag">Ambiente y salud</span><span class="tag">Desigualdad y trabajo</span><span class="tag">Digital y global</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-18" hidden>
          <div class="detail-grid">
            <section>
              <h4>Rasgos principales</h4>
              <ul><li>Universalidad: compromete a países de todos los niveles de ingreso.</li><li>Interdependencia de dimensiones sociales, económicas y ambientales.</li><li>Indicadores globales con necesidad de adaptación territorial.</li></ul>
            </section>
            <section>
              <h4>¿Qué cambia en la comprensión?</h4>
              <p>Refuerza una lectura integral de los problemas contemporáneos, aunque enfrenta tensiones entre metas, capacidades estatales y modelos económicos.</p>
            </section>
          </div>
          <div class="source-box">
            <div>
              <span class="source-kicker">Documento o fuente clave</span>
              <strong>Naciones Unidas. Transformar nuestro mundo: Agenda 2030 (2015).</strong>
            </div>
            <div class="source-actions">
              <a href="https://sdgs.un.org/es/2030agenda" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a>
              <button class="copy-citation" data-citation="Naciones Unidas. Transformar nuestro mundo: Agenda 2030 (2015). https://sdgs.un.org/es/2030agenda">Copiar referencia</button>
            </div>
          </div>
        </div>
      </div>
    </article>
    
    <article class="event-card" id="evento-19" data-year="2020" data-stage="Crisis sistémicas y nuevas desigualdades" data-cats="Ambiente y salud|Desigualdad y trabajo|Género, raza e intersecciones|Digital y global" data-search="la pandemia revela desigualdades sistémicas covid-19 y crisis social global la emergencia sanitaria amplifica pobreza, informalidad, brechas educativas y digitales, violencias de género y sobrecarga de cuidados. crisis simultánea de salud, empleo, educación, cuidados y protección social. impactos desiguales según clase, género, edad, territorio, raza y ocupación. dependencia de infraestructura digital y trabajo esencial.">
      <div class="timeline-marker" aria-hidden="true"><span>2020</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-19">
          <div class="event-meta">
            <span class="event-year">2020</span>
            <span class="event-type">Informe internacional</span>
          </div>
          <h3>La pandemia revela desigualdades sistémicas</h3>
          <p class="author">COVID-19 y crisis social global</p>
          <p class="summary">La emergencia sanitaria amplifica pobreza, informalidad, brechas educativas y digitales, violencias de género y sobrecarga de cuidados.</p>
          <div class="tags"><span class="tag">Ambiente y salud</span><span class="tag">Desigualdad y trabajo</span><span class="tag">Género, raza e intersecciones</span><span class="tag">Digital y global</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-19" hidden>
          <div class="detail-grid">
            <section>
              <h4>Rasgos principales</h4>
              <ul><li>Crisis simultánea de salud, empleo, educación, cuidados y protección social.</li><li>Impactos desiguales según clase, género, edad, territorio, raza y ocupación.</li><li>Dependencia de infraestructura digital y trabajo esencial.</li></ul>
            </section>
            <section>
              <h4>¿Qué cambia en la comprensión?</h4>
              <p>Muestra que los problemas sociales forman sistemas interdependientes y que las crisis no afectan por igual: se apoyan en vulnerabilidades preexistentes.</p>
            </section>
          </div>
          <div class="source-box">
            <div>
              <span class="source-kicker">Documento o fuente clave</span>
              <strong>UN DESA. The Sustainable Development Goals Report 2020.</strong>
            </div>
            <div class="source-actions">
              <a href="https://www.un.org/development/desa/en/news/sustainable/sustainable-development-goals-report-2020.html" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a>
              <button class="copy-citation" data-citation="UN DESA. The Sustainable Development Goals Report 2020. https://www.un.org/development/desa/en/news/sustainable/sustainable-development-goals-report-2020.html">Copiar referencia</button>
            </div>
          </div>
        </div>
      </div>
    </article>
    
    <article class="event-card" id="evento-20" data-year="2021" data-stage="Crisis sistémicas y nuevas desigualdades" data-cats="Digital y global|Desigualdad y trabajo|Derechos y política" data-search="el trabajo se organiza mediante plataformas y algoritmos oit — world employment and social outlook 2021 las plataformas digitales transforman la contratación, la supervisión, la remuneración y la protección de trabajadores en mercados transnacionales. gestión algorítmica, reputaciones y asimetría de datos. debate sobre subordinación, autonomía y clasificación laboral. flexibilidad combinada con ingresos inciertos y protección desigual.">
      <div class="timeline-marker" aria-hidden="true"><span>2021</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-20">
          <div class="event-meta">
            <span class="event-year">2021</span>
            <span class="event-type">Informe internacional</span>
          </div>
          <h3>El trabajo se organiza mediante plataformas y algoritmos</h3>
          <p class="author">OIT — World Employment and Social Outlook 2021</p>
          <p class="summary">Las plataformas digitales transforman la contratación, la supervisión, la remuneración y la protección de trabajadores en mercados transnacionales.</p>
          <div class="tags"><span class="tag">Digital y global</span><span class="tag">Desigualdad y trabajo</span><span class="tag">Derechos y política</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-20" hidden>
          <div class="detail-grid">
            <section>
              <h4>Rasgos principales</h4>
              <ul><li>Gestión algorítmica, reputaciones y asimetría de datos.</li><li>Debate sobre subordinación, autonomía y clasificación laboral.</li><li>Flexibilidad combinada con ingresos inciertos y protección desigual.</li></ul>
            </section>
            <section>
              <h4>¿Qué cambia en la comprensión?</h4>
              <p>Actualiza la cuestión laboral para una economía de datos y evidencia que la innovación tecnológica puede reproducir formas tradicionales de precariedad.</p>
            </section>
          </div>
          <div class="source-box">
            <div>
              <span class="source-kicker">Documento o fuente clave</span>
              <strong>ILO. World Employment and Social Outlook 2021: Digital labour platforms.</strong>
            </div>
            <div class="source-actions">
              <a href="https://www.ilo.org/publications/flagship-reports/role-digital-labour-platforms-transforming-world-work" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a>
              <button class="copy-citation" data-citation="ILO. World Employment and Social Outlook 2021: Digital labour platforms. https://www.ilo.org/publications/flagship-reports/role-digital-labour-platforms-transforming-world-work">Copiar referencia</button>
            </div>
          </div>
        </div>
      </div>
    </article>
    
    <article class="event-card" id="evento-21" data-year="2023" data-stage="Crisis sistémicas y nuevas desigualdades" data-cats="Ambiente y salud|Género, raza e intersecciones|Digital y global" data-search="la crisis climática se entiende como crisis de justicia ipcc — sexto informe de evaluación, síntesis el cambio climático produce riesgos compuestos para salud, alimentación, agua, vivienda, migración y medios de vida, con impactos desproporcionados sobre poblaciones vulnerables. vulnerabilidad diferencial y responsabilidades históricas desiguales. riesgos en cascada y límites de adaptación. necesidad de transiciones justas, mitigación y reparación de pérdidas.">
      <div class="timeline-marker" aria-hidden="true"><span>2023</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-21">
          <div class="event-meta">
            <span class="event-year">2023</span>
            <span class="event-type">Informe científico</span>
          </div>
          <h3>La crisis climática se entiende como crisis de justicia</h3>
          <p class="author">IPCC — Sexto Informe de Evaluación, síntesis</p>
          <p class="summary">El cambio climático produce riesgos compuestos para salud, alimentación, agua, vivienda, migración y medios de vida, con impactos desproporcionados sobre poblaciones vulnerables.</p>
          <div class="tags"><span class="tag">Ambiente y salud</span><span class="tag">Género, raza e intersecciones</span><span class="tag">Digital y global</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-21" hidden>
          <div class="detail-grid">
            <section>
              <h4>Rasgos principales</h4>
              <ul><li>Vulnerabilidad diferencial y responsabilidades históricas desiguales.</li><li>Riesgos en cascada y límites de adaptación.</li><li>Necesidad de transiciones justas, mitigación y reparación de pérdidas.</li></ul>
            </section>
            <section>
              <h4>¿Qué cambia en la comprensión?</h4>
              <p>Fusiona ciencia climática y análisis social: la exposición física no basta para explicar el daño sin considerar desigualdad, gobernanza y capacidades de adaptación.</p>
            </section>
          </div>
          <div class="source-box">
            <div>
              <span class="source-kicker">Documento o fuente clave</span>
              <strong>IPCC. Climate Change 2023: AR6 Synthesis Report.</strong>
            </div>
            <div class="source-actions">
              <a href="https://www.ipcc.ch/report/ar6/syr/" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a>
              <button class="copy-citation" data-citation="IPCC. Climate Change 2023: AR6 Synthesis Report. https://www.ipcc.ch/report/ar6/syr/">Copiar referencia</button>
            </div>
          </div>
        </div>
      </div>
    </article>
    
    <article class="event-card" id="evento-22" data-year="2025" data-stage="Crisis sistémicas y nuevas desigualdades" data-cats="Desigualdad y trabajo|Derechos y política|Digital y global" data-search="inseguridad, desigualdad y desconfianza erosionan la cohesión social naciones unidas — world social report 2025 la inseguridad económica, la desigualdad persistente, la desconfianza institucional y la fragmentación social aparecen como amenazas conectadas. debilitamiento de vínculos, expectativas y confianza pública. polarización y sensación de pérdida de control. propuesta de consenso basado en equidad, seguridad económica y solidaridad.">
      <div class="timeline-marker" aria-hidden="true"><span>2025</span></div>
      <div class="event-shell">
        <button class="event-head" aria-expanded="false" aria-controls="detalle-22">
          <div class="event-meta">
            <span class="event-year">2025</span>
            <span class="event-type">Informe internacional</span>
          </div>
          <h3>Inseguridad, desigualdad y desconfianza erosionan la cohesión social</h3>
          <p class="author">Naciones Unidas — World Social Report 2025</p>
          <p class="summary">La inseguridad económica, la desigualdad persistente, la desconfianza institucional y la fragmentación social aparecen como amenazas conectadas.</p>
          <div class="tags"><span class="tag">Desigualdad y trabajo</span><span class="tag">Derechos y política</span><span class="tag">Digital y global</span></div>
          <span class="expand-label"><span class="plus">+</span> Explorar hito</span>
        </button>
        <div class="event-detail" id="detalle-22" hidden>
          <div class="detail-grid">
            <section>
              <h4>Rasgos principales</h4>
              <ul><li>Debilitamiento de vínculos, expectativas y confianza pública.</li><li>Polarización y sensación de pérdida de control.</li><li>Propuesta de consenso basado en equidad, seguridad económica y solidaridad.</li></ul>
            </section>
            <section>
              <h4>¿Qué cambia en la comprensión?</h4>
              <p>El foco contemporáneo no se limita a ingresos: incluye cohesión, confianza, pertenencia y capacidad colectiva para sostener acuerdos democráticos.</p>
            </section>
          </div>
          <div class="source-box">
            <div>
              <span class="source-kicker">Documento o fuente clave</span>
              <strong>UN DESA. World Social Report 2025: A New Policy Consensus to Accelerate Social Progress.</strong>
            </div>
            <div class="source-actions">
              <a href="https://desapublications.un.org/publications/world-social-report-2025-new-policy-consensus-accelerate-social-progress" target="_blank" rel="noopener noreferrer">Abrir fuente ↗</a>
              <button class="copy-citation" data-citation="UN DESA. World Social Report 2025: A New Policy Consensus to Accelerate Social Progress. https://desapublications.un.org/publications/world-social-report-2025-new-policy-consensus-accelerate-social-progress">Copiar referencia</button>
            </div>
          </div>
        </div>
      </div>
    </article>
    
    <div class="no-results" id="noResults">
      <h3>No se encontraron hitos</h3>
      <p>Prueba con otra palabra o selecciona “Todos”.</p>
    </div>
  </section>

  <section>
    <div class="section-title">
      <h2>Seis etapas para interpretar el cambio</h2>
      <p>La historia no es lineal: los enfoques se superponen, compiten y reaparecen. Estas etapas sirven como organizadores pedagógicos.</p>
    </div>
    <div class="reading-grid"><article class="reading-card"><span>1845–1903</span><h3>Cuestión social e industrialización</h3><p>De la caridad y la moralización a explicaciones estructurales, empíricas y sociológicas.</p></article>
<article class="reading-card"><span>1919–1948</span><h3>Institucionalización y derechos</h3><p>El trabajo, la protección social y la dignidad se convierten en responsabilidades públicas e internacionales.</p></article>
<article class="reading-card"><span>1962–1986</span><h3>Ambiente, construcción social y riesgos</h3><p>Surgen los daños socioambientales, la definición colectiva de los problemas y los riesgos fabricados por la modernidad.</p></article>
<article class="reading-card"><span>1989–1991</span><h3>Interseccionalidad y desarrollo humano</h3><p>Se cuestionan las categorías únicas y se amplía el bienestar hacia capacidades, diversidad e igualdad sustantiva.</p></article>
<article class="reading-card"><span>2000–2015</span><h3>Problemas integrados y metas globales</h3><p>Los diagnósticos se vuelven multidimensionales y se articulan con indicadores, metas y gobernanza global.</p></article>
<article class="reading-card"><span>2020–2025</span><h3>Crisis sistémicas y nuevas desigualdades</h3><p>Pandemia, plataformas, clima y desconfianza muestran problemas conectados, transnacionales y distribuidos de forma desigual.</p></article></div>
  </section>

  <section>
    <div class="section-title">
      <h2>Cinco desplazamientos centrales</h2>
      <p>Estos movimientos resumen la transformación del campo de los problemas sociales contemporáneos.</p>
    </div>
    <div class="key-shifts">
      <article class="shift"><b>01</b><span>Del defecto individual a la estructura social</span><small>Trabajo, clase, territorio, instituciones y relaciones de poder.</small></article>
      <article class="shift"><b>02</b><span>De la carencia a los derechos</span><small>Titulares de derechos, obligaciones estatales y exigibilidad.</small></article>
      <article class="shift"><b>03</b><span>De una causa única a la intersección</span><small>Clase, género, raza, edad, territorio, discapacidad y otras posiciones.</small></article>
      <article class="shift"><b>04</b><span>De lo nacional a lo transnacional</span><small>Migraciones, cadenas globales, pandemias, plataformas y clima.</small></article>
      <article class="shift"><b>05</b><span>Del daño visible al riesgo sistémico</span><small>Incertidumbre, efectos acumulativos, algoritmos y crisis en cascada.</small></article>
    </div>
  </section>

  <section id="fuentes">
    <div class="section-title">
      <h2>Fuentes históricas y académicas</h2>
      <p>Se priorizaron documentos originales, archivos universitarios, organismos multilaterales y editoriales académicas.</p>
    </div>
    <div class="sources"><ol><li><span>1845</span><a href="https://www.marxists.org/archive/marx/works/1845/condition-working-class/index.htm" target="_blank" rel="noopener noreferrer">Engels, F. (1845). The Condition of the Working Class in England.</a><em>Documento histórico</em></li>
<li><span>1889</span><a href="https://booth.lse.ac.uk/learn-more/what-were-the-poverty-maps" target="_blank" rel="noopener noreferrer">London School of Economics. What were the poverty maps?</a><em>Archivo histórico</em></li>
<li><span>1897</span><a href="https://classiques.uqam.ca/classiques/Durkheim_emile/suicide/suicide.html" target="_blank" rel="noopener noreferrer">Durkheim, É. (1897). Le suicide. Étude de sociologie.</a><em>Obra académica</em></li>
<li><span>1903</span><a href="https://www.gutenberg.org/ebooks/408" target="_blank" rel="noopener noreferrer">Du Bois, W. E. B. (1903). The Souls of Black Folk.</a><em>Obra académica</em></li>
<li><span>1919</span><a href="https://normlex.ilo.org/dyn/nrmlx_en/f?p=1000:62:0::NO:62:P62_LIST_ENTRIE_ID:2453907:NO" target="_blank" rel="noopener noreferrer">International Labour Organization. ILO Constitution (1919).</a><em>Documento normativo</em></li>
<li><span>1942</span><a href="https://www.parliament.uk/about/living-heritage/transformingsociety/livinglearning/coll-9-health1/coll-9-health/" target="_blank" rel="noopener noreferrer">UK Parliament. The 1942 Beveridge Report.</a><em>Informe gubernamental</em></li>
<li><span>1948</span><a href="https://www.un.org/es/about-us/universal-declaration-of-human-rights" target="_blank" rel="noopener noreferrer">Naciones Unidas. Declaración Universal de los Derechos Humanos (1948).</a><em>Documento internacional</em></li>
<li><span>1949</span><a href="https://www.cepal.org/es/publicaciones/40010-desarrollo-economico-la-america-latina-algunos-sus-principales-problemas" target="_blank" rel="noopener noreferrer">Prebisch, R. (1949). El desarrollo económico de la América Latina y algunos de sus principales problemas.</a><em>Pensamiento latinoamericano</em></li>
<li><span>1962</span><a href="https://www.epa.gov/history/origins-epa" target="_blank" rel="noopener noreferrer">U.S. Environmental Protection Agency. The Origins of EPA.</a><em>Historia institucional</em></li>
<li><span>1971</span><a href="https://www.jstor.org/stable/799797" target="_blank" rel="noopener noreferrer">Blumer, H. (1971). Social Problems as Collective Behavior. Social Problems, 18(3), 298–306.</a><em>Artículo académico</em></li>
<li><span>1972</span><a href="https://www.clubofrome.org/publication/the-limits-to-growth/" target="_blank" rel="noopener noreferrer">Club of Rome. The Limits to Growth (1972).</a><em>Informe científico</em></li>
<li><span>1979</span><a href="https://www.un.org/womenwatch/daw/cedaw/cedaw.htm" target="_blank" rel="noopener noreferrer">Naciones Unidas. Convención sobre la Eliminación de Todas las Formas de Discriminación contra la Mujer (1979).</a><em>Tratado internacional</em></li>
<li><span>1986</span><a href="https://www.suhrkamp.de/rights/book/ulrich-beck-risk-society-fr-9783518113653" target="_blank" rel="noopener noreferrer">Beck, U. (1986). Risikogesellschaft: Auf dem Weg in eine andere Moderne.</a><em>Obra académica</em></li>
<li><span>1989</span><a href="https://chicagounbound.uchicago.edu/uclf/vol1989/iss1/8/" target="_blank" rel="noopener noreferrer">Crenshaw, K. (1989). Demarginalizing the Intersection of Race and Sex.</a><em>Artículo académico</em></li>
<li><span>1990</span><a href="https://hdr.undp.org/system/files/documents/hdr1990encompletenostats.pdf" target="_blank" rel="noopener noreferrer">UNDP. Human Development Report 1990.</a><em>Informe internacional</em></li>
<li><span>1991</span><a href="https://www.secretariasenado.gov.co/senado/basedoc/constitucion_politica_1991.html" target="_blank" rel="noopener noreferrer">Colombia. Constitución Política de 1991.</a><em>Documento constitucional</em></li>
<li><span>2000</span><a href="https://www.un.org/esa/devagenda/millennium.html" target="_blank" rel="noopener noreferrer">Naciones Unidas. Declaración del Milenio (2000).</a><em>Documento internacional</em></li>
<li><span>2000</span><a href="https://biblioteca.clacso.edu.ar/clacso/se/20140507042402/eje3-8.pdf" target="_blank" rel="noopener noreferrer">Quijano, A. (2000). Colonialidad del poder, eurocentrismo y América Latina.</a><em>Pensamiento latinoamericano</em></li>
<li><span>2008</span><a href="https://www.who.int/publications/i/item/9789241563703" target="_blank" rel="noopener noreferrer">WHO. Closing the gap in a generation (2008).</a><em>Informe científico</em></li>
<li><span>2015</span><a href="https://sdgs.un.org/es/2030agenda" target="_blank" rel="noopener noreferrer">Naciones Unidas. Transformar nuestro mundo: Agenda 2030 (2015).</a><em>Agenda internacional</em></li>
<li><span>2020</span><a href="https://www.un.org/development/desa/en/news/sustainable/sustainable-development-goals-report-2020.html" target="_blank" rel="noopener noreferrer">UN DESA. The Sustainable Development Goals Report 2020.</a><em>Informe internacional</em></li>
<li><span>2021</span><a href="https://www.ilo.org/publications/flagship-reports/role-digital-labour-platforms-transforming-world-work" target="_blank" rel="noopener noreferrer">ILO. World Employment and Social Outlook 2021: Digital labour platforms.</a><em>Informe internacional</em></li>
<li><span>2023</span><a href="https://www.ipcc.ch/report/ar6/syr/" target="_blank" rel="noopener noreferrer">IPCC. Climate Change 2023: AR6 Synthesis Report.</a><em>Informe científico</em></li>
<li><span>2025</span><a href="https://desapublications.un.org/publications/world-social-report-2025-new-policy-consensus-accelerate-social-progress" target="_blank" rel="noopener noreferrer">UN DESA. World Social Report 2025: A New Policy Consensus to Accelerate Social Progress.</a><em>Informe internacional</em></li></ol></div>
    <div class="method-note"><strong>Nota metodológica.</strong> La selección privilegia hitos que cambiaron marcos de interpretación, métodos de investigación o respuestas públicas. No pretende afirmar que un solo documento “creó” cada enfoque ni reemplazar historias regionales, indígenas, afrodescendientes, feministas o latinoamericanas más amplias.</div>
  </section>
</main>

<footer class="footer">
  <div class="footer-inner">
    <p>Diseño académico inspirado en la paleta institucional de la Universidad de La Salle: azul #003057 y amarillo #F2A900.</p>
    <p>Elaborado para uso educativo · Actualizado a 2026</p>
  </div>
</footer>
<div class="toast" id="toast">Referencia copiada</div>

<script>
const cards = [...document.querySelectorAll('.event-card')];
const filters = [...document.querySelectorAll('.filter')];
const searchInput = document.getElementById('searchInput');
const count = document.getElementById('resultCount');
const noResults = document.getElementById('noResults');
let activeFilter = 'Todos';

function updateCards() {
  const q = searchInput.value.trim().toLowerCase();
  let visible = 0;
  cards.forEach(card => {
    const cats = card.dataset.cats.split('|');
    const filterOk = activeFilter === 'Todos' || cats.includes(activeFilter);
    const searchOk = !q || card.dataset.search.includes(q) || card.dataset.year.includes(q);
    const show = filterOk && searchOk;
    card.classList.toggle('hidden-card', !show);
    if (show) visible++;
  });
  count.textContent = `${visible} ${visible === 1 ? 'hito visible' : 'hitos visibles'}`;
  noResults.style.display = visible ? 'none' : 'block';
}

filters.forEach(btn => btn.addEventListener('click', () => {
  filters.forEach(b => b.classList.remove('active'));
  btn.classList.add('active');
  activeFilter = btn.dataset.filter;
  updateCards();
}));
searchInput.addEventListener('input', updateCards);

document.querySelectorAll('.event-head').forEach(btn => {
  btn.addEventListener('click', () => {
    const open = btn.getAttribute('aria-expanded') === 'true';
    btn.setAttribute('aria-expanded', String(!open));
    const detail = document.getElementById(btn.getAttribute('aria-controls'));
    detail.hidden = open;
  });
});

let expanded = false;
document.getElementById('expandAll').addEventListener('click', e => {
  expanded = !expanded;
  document.querySelectorAll('.event-head').forEach(btn => {
    btn.setAttribute('aria-expanded', String(expanded));
    document.getElementById(btn.getAttribute('aria-controls')).hidden = !expanded;
  });
  e.currentTarget.textContent = expanded ? 'Contraer todo' : 'Expandir todo';
});

document.querySelectorAll('.stage-link').forEach(btn => btn.addEventListener('click', () => {
  const target = cards.find(c => c.dataset.stage === btn.dataset.stage && !c.classList.contains('hidden-card'));
  if (target) target.scrollIntoView({behavior:'smooth', block:'center'});
}));

const toast = document.getElementById('toast');
document.querySelectorAll('.copy-citation').forEach(btn => btn.addEventListener('click', async () => {
  try {
    await navigator.clipboard.writeText(btn.dataset.citation);
    toast.textContent = 'Referencia copiada';
  } catch (e) {
    toast.textContent = 'No fue posible copiar automáticamente';
  }
  toast.classList.add('show');
  setTimeout(() => toast.classList.remove('show'), 1800);
}));

const progress = document.getElementById('progressLine');
window.addEventListener('scroll', () => {
  const max = document.documentElement.scrollHeight - window.innerHeight;
  progress.style.width = (max > 0 ? (window.scrollY / max) * 100 : 0) + '%';
});
</script>
</body>
</html>

<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>DGIUG Bank — Ihr Geld ist unser Geld</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,600;0,700;0,900;1,600&family=Inter:wght@400;500;600;700&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root{
    --navy:#0B1F3A;
    --navy-2:#142A4D;
    --gold:#C6A15B;
    --cream:#F3EEE2;
    --red:#7A1F2B;
    --green:#1F5C4A;
    --line: rgba(243,238,226,0.15);
  }
  *{margin:0;padding:0;box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--cream);
    color:var(--navy);
    font-family:'Inter',sans-serif;
    line-height:1.5;
    overflow-x:hidden;
  }
  h1,h2,h3,.serif{font-family:'Playfair Display',serif;}
  .mono{font-family:'IBM Plex Mono',monospace;}
  a{color:inherit;text-decoration:none;}
  .wrap{max-width:1100px;margin:0 auto;padding:0 28px;}

  /* NAV */
  header{
    position:sticky;top:0;z-index:50;
    background:var(--navy);
    color:var(--cream);
    border-bottom:3px solid var(--gold);
  }
  nav{
    display:flex;align-items:center;justify-content:space-between;
    padding:16px 28px;max-width:1100px;margin:0 auto;
  }
  .logo{display:flex;align-items:center;gap:10px;font-family:'Playfair Display',serif;font-weight:900;font-size:1.3rem;letter-spacing:0.5px;}
  .logo .seal{
    width:34px;height:34px;border-radius:50%;
    background:var(--gold);color:var(--navy);
    display:flex;align-items:center;justify-content:center;
    font-size:0.75rem;font-weight:900;font-family:'IBM Plex Mono',monospace;
    border:2px solid var(--cream);
  }
  .navlinks{display:flex;gap:28px;font-size:0.92rem;font-weight:500;}
  .navlinks a{opacity:0.85;transition:opacity .2s;border-bottom:1px solid transparent;padding-bottom:2px;}
  .navlinks a:hover{opacity:1;border-color:var(--gold);}
  @media (max-width:720px){.navlinks{display:none;}}

  /* TICKER BAR */
  .tickerbar{
    background:var(--red);color:var(--cream);
    font-family:'IBM Plex Mono',monospace;font-size:0.78rem;
    padding:6px 0;overflow:hidden;white-space:nowrap;
    border-bottom:1px solid rgba(0,0,0,0.15);
  }
  .tickertrack{display:inline-block;padding-left:100%;animation:scroll 22s linear infinite;}
  @keyframes scroll{from{transform:translateX(0);}to{transform:translateX(-100%);}}

  /* HERO */
  .hero{
    background:radial-gradient(circle at 20% -10%, var(--navy-2), var(--navy) 60%);
    color:var(--cream);
    padding:96px 0 80px;
    position:relative;
  }
  .hero-grid{display:grid;grid-template-columns:1.2fr 1fr;gap:48px;align-items:center;}
  @media (max-width:860px){.hero-grid{grid-template-columns:1fr;}}
  .eyebrow{
    display:inline-block;font-family:'IBM Plex Mono',monospace;font-size:0.75rem;
    letter-spacing:1.5px;text-transform:uppercase;color:var(--gold);
    border:1px solid var(--gold);padding:5px 12px;border-radius:999px;margin-bottom:22px;
  }
  .hero h1{
    font-size:clamp(2.4rem,5.5vw,4.2rem);font-weight:900;line-height:1.05;letter-spacing:-1px;
  }
  .hero h1 em{font-style:italic;color:var(--gold);}
  .hero p.lead{margin-top:22px;font-size:1.15rem;max-width:480px;color:rgba(243,238,226,0.85);}
  .cta-row{margin-top:34px;display:flex;gap:16px;flex-wrap:wrap;}
  .btn{
    padding:14px 26px;border-radius:4px;font-weight:600;font-size:0.95rem;
    display:inline-flex;align-items:center;gap:8px;cursor:pointer;border:none;
    transition:transform .15s ease, box-shadow .15s ease;
  }
  .btn-gold{background:var(--gold);color:var(--navy);}
  .btn-gold:hover{transform:translateY(-2px);box-shadow:0 10px 24px rgba(198,161,91,0.35);}
  .btn-ghost{background:transparent;border:1px solid rgba(243,238,226,0.4);color:var(--cream);}
  .btn-ghost:hover{border-color:var(--cream);}
  .fineprint{margin-top:10px;font-size:0.72rem;color:rgba(243,238,226,0.5);max-width:420px;}

  /* KONTOSTAND DISPLAY */
  .display-card{
    background:#08172C;
    border:1px solid rgba(198,161,91,0.4);
    border-radius:10px;padding:28px;
    box-shadow:0 30px 60px rgba(0,0,0,0.4);
  }
  .display-label{font-family:'IBM Plex Mono',monospace;font-size:0.72rem;letter-spacing:1px;color:var(--gold);text-transform:uppercase;margin-bottom:12px;}
  .display-amount{
    font-family:'IBM Plex Mono',monospace;font-size:clamp(1.8rem,4vw,2.6rem);
    font-weight:600;color:#ff6b6b;letter-spacing:1px;
    text-shadow:0 0 18px rgba(255,107,107,0.35);
  }
  .display-sub{margin-top:10px;font-size:0.78rem;color:rgba(243,238,226,0.55);font-family:'IBM Plex Mono',monospace;}
  .display-bar{margin-top:18px;height:6px;background:rgba(255,255,255,0.08);border-radius:99px;overflow:hidden;}
  .display-bar-fill{height:100%;width:100%;background:linear-gradient(90deg,var(--gold),#ff6b6b);animation:shrink 8s linear infinite;}
  @keyframes shrink{0%{width:100%;}100%{width:4%;}}

  /* SECTIONS */
  section{padding:80px 0;}
  .section-head{max-width:640px;margin-bottom:48px;}
  .section-head .eyebrow{color:var(--red);border-color:var(--red);}
  .section-head h2{font-size:clamp(1.8rem,3.4vw,2.6rem);font-weight:700;margin-top:14px;}
  .section-head p{margin-top:12px;color:rgba(11,31,58,0.65);font-size:1.02rem;}

  /* LEISTUNGEN GRID */
  .cards{display:grid;grid-template-columns:repeat(3,1fr);gap:24px;}
  @media (max-width:860px){.cards{grid-template-columns:1fr;}}
  .card{
    background:#fff;border:1px solid rgba(11,31,58,0.1);border-radius:10px;padding:28px;
    position:relative;overflow:hidden;
  }
  .card::before{content:"";position:absolute;top:0;left:0;width:4px;height:100%;background:var(--gold);}
  .card h3{font-size:1.15rem;margin-bottom:10px;font-weight:700;}
  .card .promise{color:var(--green);font-weight:600;font-size:0.9rem;margin-bottom:8px;}
  .card .truth{color:var(--red);font-size:0.88rem;font-family:'IBM Plex Mono',monospace;}
  .card .truth::before{content:"* eigentlich: ";opacity:0.7;}

  /* GEBÜHRENTABELLE */
  .fees{background:var(--navy);color:var(--cream);}
  .fees .section-head p{color:rgba(243,238,226,0.65);}
  .fees .eyebrow{color:var(--gold);border-color:var(--gold);}
  table{width:100%;border-collapse:collapse;font-size:0.95rem;}
  thead th{
    text-align:left;padding:14px 16px;font-family:'IBM Plex Mono',monospace;
    font-size:0.75rem;text-transform:uppercase;letter-spacing:0.8px;color:var(--gold);
    border-bottom:1px solid var(--line);
  }
  tbody td{padding:16px;border-bottom:1px solid var(--line);}
  tbody tr:hover{background:rgba(198,161,91,0.06);}
  td.price{font-family:'IBM Plex Mono',monospace;text-align:right;color:#ff9b7a;font-weight:600;}
  .fees-note{margin-top:18px;font-size:0.78rem;color:rgba(243,238,226,0.45);}

  /* SIEGEL / TRUST BADGES */
  .badges{display:flex;flex-wrap:wrap;gap:18px;}
  .badge{
    flex:1 1 200px;background:#fff;border:1px dashed rgba(11,31,58,0.25);border-radius:10px;
    padding:22px;text-align:center;
  }
  .badge .stamp{
    width:56px;height:56px;border-radius:50%;border:2px solid var(--red);color:var(--red);
    display:flex;align-items:center;justify-content:center;margin:0 auto 12px;
    font-family:'IBM Plex Mono',monospace;font-weight:700;font-size:0.95rem;
    transform:rotate(-8deg);
  }
  .badge h4{font-size:0.98rem;margin-bottom:6px;}
  .badge p{font-size:0.82rem;color:rgba(11,31,58,0.6);}

  /* TESTIMONIALS */
  .testis{display:grid;grid-template-columns:repeat(3,1fr);gap:22px;}
  @media (max-width:860px){.testis{grid-template-columns:1fr;}}
  .testi{background:#fff;border-radius:10px;padding:26px;border:1px solid rgba(11,31,58,0.1);}
  .testi p.quote{font-family:'Playfair Display',serif;font-style:italic;font-size:1.05rem;color:var(--navy);}
  .testi .who{margin-top:16px;display:flex;align-items:center;gap:10px;}
  .avatar{width:38px;height:38px;border-radius:50%;background:var(--navy);color:var(--gold);display:flex;align-items:center;justify-content:center;font-weight:700;font-family:'IBM Plex Mono',monospace;font-size:0.85rem;}
  .who .name{font-weight:600;font-size:0.9rem;}
  .who .role{font-size:0.78rem;color:rgba(11,31,58,0.55);}

  /* FOOTER */
  footer{background:#08172C;color:rgba(243,238,226,0.55);padding:56px 0 30px;font-size:0.82rem;}
  .footer-grid{display:grid;grid-template-columns:2fr 1fr 1fr;gap:32px;margin-bottom:36px;}
  @media (max-width:720px){.footer-grid{grid-template-columns:1fr;}}
  footer h5{color:var(--cream);font-size:0.85rem;margin-bottom:14px;font-family:'IBM Plex Mono',monospace;letter-spacing:0.5px;}
  footer ul{list-style:none;}
  footer li{margin-bottom:8px;}
  footer a:hover{color:var(--gold);}
  .footer-bottom{border-top:1px solid var(--line);padding-top:20px;font-size:0.72rem;color:rgba(243,238,226,0.35);}

  /* COOKIE BANNER */
  .cookie{
    position:fixed;bottom:18px;left:18px;right:18px;max-width:520px;margin:0 auto;
    background:var(--navy);color:var(--cream);border:1px solid var(--gold);border-radius:10px;
    padding:20px 22px;box-shadow:0 20px 50px rgba(0,0,0,0.35);z-index:100;
    transform:translateY(140%);transition:transform .5s ease;
  }
  .cookie.show{transform:translateY(0);}
  .cookie h4{font-size:0.95rem;margin-bottom:8px;}
  .cookie p{font-size:0.82rem;color:rgba(243,238,226,0.7);margin-bottom:14px;}
  .cookie .row{display:flex;gap:10px;flex-wrap:wrap;}
  .cookie button{
    padding:9px 16px;border-radius:5px;border:none;font-size:0.82rem;font-weight:600;cursor:pointer;
  }
  .cookie .accept-all{background:var(--gold);color:var(--navy);}
  .cookie .accept-soul{background:var(--red);color:var(--cream);}
  .cookie .reject{background:transparent;color:rgba(243,238,226,0.6);border:1px solid rgba(243,238,226,0.3);}

  /* PAGE HERO (Unterseiten) */
  .page-hero{
    background:radial-gradient(circle at 80% -20%, var(--navy-2), var(--navy) 65%);
    color:var(--cream);padding:64px 0 56px;
  }
  .page-hero h1{font-size:clamp(2rem,4.4vw,3rem);font-weight:800;letter-spacing:-0.5px;}
  .page-hero p{margin-top:14px;max-width:560px;color:rgba(243,238,226,0.8);font-size:1.05rem;}
  .breadcrumb{font-family:'IBM Plex Mono',monospace;font-size:0.75rem;color:var(--gold);margin-bottom:16px;opacity:0.8;}
  .back-link{display:inline-flex;align-items:center;gap:6px;font-family:'IBM Plex Mono',monospace;font-size:0.82rem;color:var(--gold);margin-top:28px;}
  .back-link:hover{text-decoration:underline;}

  /* LEGAL TEXT */
  .legal{background:#fff;border:1px solid rgba(11,31,58,0.1);border-radius:10px;padding:40px;font-size:0.95rem;color:rgba(11,31,58,0.75);}
  .legal h3{font-family:'IBM Plex Mono',monospace;font-size:0.92rem;color:var(--navy);margin:26px 0 10px;text-transform:uppercase;letter-spacing:0.5px;}
  .legal h3:first-child{margin-top:0;}
  .legal p{margin-bottom:12px;line-height:1.65;}
  .legal ol,.legal ul{margin:0 0 12px 22px;}
  .legal li{margin-bottom:6px;}

  /* KEVIN CHAT WIDGET */
  .kevin-bubble{
    position:fixed;bottom:24px;right:24px;z-index:200;
    width:60px;height:60px;border-radius:50%;
    background:var(--gold);color:var(--navy);border:none;cursor:pointer;
    font-size:1.5rem;box-shadow:0 12px 30px rgba(0,0,0,0.3);
    display:flex;align-items:center;justify-content:center;
    transition:transform .2s ease;
  }
  .kevin-bubble:hover{transform:scale(1.08);}
  .kevin-panel{
    position:fixed;bottom:98px;right:24px;z-index:200;
    width:340px;max-width:calc(100vw - 40px);
    background:#08172C;border:1px solid rgba(198,161,91,0.4);border-radius:12px;
    box-shadow:0 30px 60px rgba(0,0,0,0.45);
    display:flex;flex-direction:column;overflow:hidden;
    opacity:0;pointer-events:none;transform:translateY(16px);
    transition:opacity .2s ease, transform .2s ease;
  }
  .kevin-panel.open{opacity:1;pointer-events:auto;transform:translateY(0);}
  .kevin-head{
    background:var(--navy-2);padding:14px 16px;display:flex;align-items:center;gap:10px;
    border-bottom:1px solid rgba(198,161,91,0.2);
  }
  .kevin-head .kdot{width:9px;height:9px;border-radius:50%;background:#4ade80;box-shadow:0 0 8px #4ade80;}
  .kevin-head span{color:var(--cream);font-size:0.85rem;font-weight:600;flex:1;}
  .kevin-close{background:transparent;border:none;color:rgba(243,238,226,0.6);cursor:pointer;font-size:1rem;}
  .kevin-body{padding:16px;display:flex;flex-direction:column;gap:10px;min-height:180px;max-height:320px;overflow-y:auto;}
  .kmsg{max-width:82%;padding:9px 12px;border-radius:10px;font-size:0.85rem;line-height:1.4;}
  .kmsg.bot{background:rgba(198,161,91,0.15);color:var(--cream);align-self:flex-start;border-bottom-left-radius:2px;}
  .kmsg.user{background:var(--gold);color:var(--navy);align-self:flex-end;border-bottom-right-radius:2px;}
  .kevin-input-row{display:flex;gap:8px;padding:12px 14px;border-top:1px solid rgba(198,161,91,0.2);}
  .kevin-input-row input{
    flex:1;padding:9px 12px;border-radius:6px;border:1px solid rgba(198,161,91,0.3);
    background:#0B1F3A;color:var(--cream);font-size:0.84rem;font-family:'Inter',sans-serif;
  }
  .kevin-input-row input::placeholder{color:rgba(243,238,226,0.4);}
  .kevin-input-row button{
    padding:9px 14px;border-radius:6px;border:none;background:var(--gold);color:var(--navy);
    font-weight:700;cursor:pointer;font-size:0.9rem;
  }
  @media (max-width:480px){
    .kevin-panel{right:12px;left:12px;width:auto;bottom:90px;}
    .kevin-bubble{right:16px;bottom:16px;}
  }


  /* LEGAL MODAL */
  .legal-overlay{
    position:fixed;inset:0;z-index:300;
    background:rgba(8,23,44,0.72);
    display:none;align-items:center;justify-content:center;
    padding:24px;
  }
  .legal-overlay.open{display:flex;}
  .legal-modal{
    background:#fff;border-radius:12px;max-width:720px;width:100%;
    max-height:80vh;display:flex;flex-direction:column;
    box-shadow:0 40px 80px rgba(0,0,0,0.5);
    animation:legalIn .2s ease;
  }
  @keyframes legalIn{from{opacity:0;transform:translateY(12px);}to{opacity:1;transform:translateY(0);}}
  .legal-modal-head{
    display:flex;align-items:center;justify-content:space-between;
    padding:20px 26px;border-bottom:1px solid rgba(11,31,58,0.1);
    background:var(--navy);color:var(--cream);border-radius:12px 12px 0 0;
  }
  .legal-modal-head h3{font-family:'Playfair Display',serif;font-size:1.3rem;font-weight:700;}
  .legal-modal-close{
    background:transparent;border:1px solid rgba(243,238,226,0.35);color:var(--cream);
    width:32px;height:32px;border-radius:50%;cursor:pointer;font-size:1rem;
    display:flex;align-items:center;justify-content:center;flex-shrink:0;
  }
  .legal-modal-close:hover{border-color:var(--gold);color:var(--gold);}
  .legal-modal-body{padding:26px;overflow-y:auto;font-size:0.95rem;color:rgba(11,31,58,0.78);}
  .legal-modal-body h4{font-family:'IBM Plex Mono',monospace;font-size:0.85rem;color:var(--navy);margin:22px 0 8px;text-transform:uppercase;letter-spacing:0.5px;}
  .legal-modal-body h4:first-child{margin-top:0;}
  .legal-modal-body p{margin-bottom:10px;line-height:1.65;}
  .legal-modal-body ol,.legal-modal-body ul{margin:0 0 10px 22px;}
  .legal-modal-body li{margin-bottom:5px;}

</style>
</head>
<body>

<header>
  <nav>
    <div class="logo"><span class="seal">DGIUG</span> DGIUG Bank</div>
    <div class="navlinks">
      <a href="#leistungen">Leistungen</a>
      <a href="#gebuehren">Gebühren</a>
      <a href="#vertrauen">Vertrauen</a>
      <a href="#stimmen">Kundenstimmen</a>
    </div>
    <a href="#kontakt" class="btn btn-gold" style="padding:9px 18px;font-size:0.85rem;">Konto eröffnen</a>
  </nav>
</header>

<div class="tickerbar">
  <div class="tickertrack mono" id="tickertext">
    ⚠ AKTUELLER LEITZINS: „hoch genug, um es zu spüren" &nbsp;•&nbsp; NEU: Gebühr fürs Gebührenschauen &nbsp;•&nbsp; Ihr Berater Kevin hat heute frei &nbsp;•&nbsp; 99,2 % aller Beschwerden landen im Papierkorb, nicht bei uns &nbsp;•&nbsp; Warteschleife jetzt in 4K &nbsp;•&nbsp; AKTUELLER LEITZINS: „hoch genug, um es zu spüren" &nbsp;•&nbsp; NEU: Gebühr fürs Gebührenschauen &nbsp;•&nbsp; Ihr Berater Kevin hat heute frei &nbsp;•&nbsp;
  </div>
</div>

<section class="hero">
  <div class="wrap hero-grid">
    <div>
      <span class="eyebrow">Seit 2024 Ihr Vertrauen missbrauchend</span>
      <h1>Ihr Geld ist <em>unser</em> Geld.</h1>
      <p class="lead">Wir bei DGIUG Bank glauben an Transparenz. Deshalb sagen wir Ihnen ganz offen: was auf Ihrem Konto landet, betrachten wir ab sofort als gemeinsames Projekt.</p>
      <div class="cta-row">
        <button class="btn btn-gold" onclick="oeffnen()">Jetzt Konto eröffnen</button>
        <a href="#kontakt" class="btn btn-ghost">Konto schließen (viel Glück)</a>
      </div>
      <p class="fineprint" id="disclaimer">*Kontoeröffnung dauert 3 Minuten. Kontoschließung dauert bis zum Ende des Universums.</p>
    </div>
    <div class="display-card">
      <div class="display-label">Ihr Kontostand · live</div>
      <div class="display-amount mono" id="kontostand">3.482,17 €</div>
      <div class="display-bar"><div class="display-bar-fill"></div></div>
      <div class="display-sub" id="statusline">wird aktualisiert … zu unseren Gunsten</div>
    </div>
  </div>
</section>

<section id="leistungen">
  <div class="wrap">
    <div class="section-head">
      <span class="eyebrow">Leistungen</span>
      <h2>Alles, was Sie brauchen. Und mehr, was wir wollen.</h2>
      <p>Unser Portfolio wurde von echten Menschen entworfen, die echtes Geld haben wollen. Ihres.</p>
    </div>
    <div class="cards">
      <div class="card">
        <h3>Kostenlose Kontoführung</h3>
        <div class="promise">✓ Für immer gebührenfrei</div>
        <div class="truth">14,99 €/Monat „Servicepauschale"</div>
      </div>
      <div class="card">
        <h3>24/7 Erreichbarkeit</h3>
        <div class="promise">✓ Wir sind immer für Sie da</div>
        <div class="truth">Warteschleifenmusik in Endlosschleife, Track 1 von 1</div>
      </div>
      <div class="card">
        <h3>Sichere Geldanlage</h3>
        <div class="promise">✓ Ihr Kapital ist geschützt</div>
        <div class="truth">Ihr Kapital ist irgendwo. Wir melden uns.</div>
      </div>
      <div class="card">
        <h3>Persönliche Beratung</h3>
        <div class="promise">✓ Ihr fester Ansprechpartner</div>
        <div class="truth">Ein Chatbot namens „Kevin", trainiert auf Ausreden</div>
      </div>
      <div class="card">
        <h3>Blitzschnelle Überweisungen</h3>
        <div class="promise">✓ In Sekunden beim Empfänger</div>
        <div class="truth">3–5 Werktage, außer an Werktagen</div>
      </div>
      <div class="card">
        <h3>Nachhaltiges Banking</h3>
        <div class="promise">✓ Klimaneutral seit 2024</div>
        <div class="truth">Wir drucken einfach keine Kontoauszüge mehr</div>
      </div>
    </div>
  </div>
</section>

<section class="fees" id="gebuehren">
  <div class="wrap">
    <div class="section-head">
      <span class="eyebrow">Gebührentabelle</span>
      <h2>Fair. Nachvollziehbar. Erfunden.</h2>
      <p>Alle Preise verstehen sich zzgl. Fassungslosigkeit.</p>
    </div>
    <table>
      <thead>
        <tr><th>Leistung</th><th style="text-align:right;">Preis</th></tr>
      </thead>
      <tbody>
        <tr><td>Kontoauszug ansehen</td><td class="price">2,00 €</td></tr>
        <tr><td>Kontoauszug NICHT ansehen</td><td class="price">2,00 €</td></tr>
        <tr><td>Lächeln des Bankberaters</td><td class="price">5,00 €</td></tr>
        <tr><td>Schweigen des Bankberaters</td><td class="price">5,00 €</td></tr>
        <tr><td>PIN vergessen (unser Fehler, Ihr Problem)</td><td class="price">9,90 €</td></tr>
        <tr><td>Anruf in der Warteschleife, pro Minute Beethoven</td><td class="price">1,20 €</td></tr>
        <tr><td>Existenz Ihres Kontos</td><td class="price">0,01 €/Sekunde</td></tr>
        <tr><td>Luft einatmen in der Filiale</td><td class="price">0,50 €</td></tr>
      </tbody>
    </table>
    <p class="fees-note">Alle Gebühren können sich jederzeit ändern — meistens nach oben, aus Prinzip.</p>
  </div>
</section>

<section id="vertrauen">
  <div class="wrap">
    <div class="section-head">
      <span class="eyebrow">Vertrauen &amp; Sicherheit</span>
      <h2>Ausgezeichnet mit Siegeln, die wir selbst gemalt haben.</h2>
    </div>
    <div class="badges">
      <div class="badge"><div class="stamp">TÜV</div><h4>TÜV-geprüft</h4><p>Nein.</p></div>
      <div class="badge"><div class="stamp">6,0</div><h4>Stiftung Warentest</h4><p>Note: „Mangelhaft", aber mit Herz.</p></div>
      <div class="badge"><div class="stamp">★</div><h4>Kundenbewertung</h4><p>1,2 von 5 Sternen. Der 1 Stern ist echt.</p></div>
      <div class="badge"><div class="stamp">§</div><h4>Kleingedrucktes</h4><p>127 Seiten. Niemand hat sie gelesen. Auch wir nicht.</p></div>
    </div>
  </div>
</section>

<section id="stimmen" style="background:#EFE9DA;">
  <div class="wrap">
    <div class="section-head">
      <span class="eyebrow">Kundenstimmen</span>
      <h2>Das sagen echte Menschen. Wahrscheinlich.</h2>
    </div>
    <div class="testis">
      <div class="testi">
        <p class="quote">„Ich wollte nur mein Geld abheben. Jetzt schulde ich der Bank einen Kaffee."</p>
        <div class="who"><div class="avatar">MK</div><div><div class="name">Martina K.</div><div class="role">Kundin seit 3 Wochen, gefühlt 3 Jahren</div></div></div>
      </div>
      <div class="testi">
        <p class="quote">„Kevin hat mir sehr geholfen. Kevin ist kein Mensch. Kevin ist trotzdem netter als meine alte Bank."</p>
        <div class="who"><div class="avatar">TS</div><div><div class="name">Tobias S.</div><div class="role">Freund von Kevin</div></div></div>
      </div>
      <div class="testi">
        <p class="quote">„Ich habe die AGB gelesen. Ich rate dringend davon ab."</p>
        <div class="who"><div class="avatar">JR</div><div><div class="name">Jana R.</div><div class="role">Fachanwältin, jetzt in Therapie</div></div></div>
      </div>
    </div>
  </div>
</section>

<footer id="kontakt">
  <div class="wrap">
    <div class="footer-grid">
      <div>
        <h5>DGIUG BANK AG</h5>
        <p style="max-width:340px;">Irgendwo im Nirgendwo 1, 00000 Nirgendwostadt. Erreichbar nur per Brieftaube, die wir zusätzlich berechnen.</p>
      </div>
      <div>
        <h5>Navigation</h5>
        <ul>
          <li><a href="#leistungen">Leistungen</a></li>
          <li><a href="#gebuehren">Gebühren</a></li>
          <li><a href="#vertrauen">Vertrauen</a></li>
        </ul>
      </div>
      <div>
        <h5>Rechtliches</h5>
        <ul>
          <li><a href="#" onclick="openLegal('impressum');return false;">Impressum (folgt seit 2024)</a></li>
          <li><a href="#" onclick="openLegal('datenschutz');return false;">Datenschutz (theoretisch)</a></li>
          <li><a href="#" onclick="openLegal('agb');return false;">AGB (127 Seiten, viel Spaß)</a></li>
        </ul>
      </div>
    </div>
    <div class="footer-bottom">
      © 2026 DGIUG Bank AG — Diese Seite ist ein Scherz und keine echte Bank. Falls doch: bitte nicht Ihr echtes Geld überweisen.
    </div>
  </div>
</footer>

<div class="cookie" id="cookieBanner">
  <h4>🍪 Cookies, Kekse &amp; mehr</h4>
  <p>Wir akzeptieren nicht nur Cookies, sondern auch Ihre Krümel, Ihr Kleingeld und optional Ihre Seele. Bitte wählen Sie aus.</p>
  <div class="row">
    <button class="accept-all" onclick="closeCookie()">Alle akzeptieren</button>
    <button class="accept-soul" onclick="soulTaken()">Alles + Seele akzeptieren</button>
    <button class="reject" onclick="closeCookie()">Ablehnen (wirkungslos)</button>
  </div>
</div>

<div class="legal-overlay" id="legalOverlay" onclick="if(event.target===this) closeLegal();">
  <div class="legal-modal">
    <div class="legal-modal-head">
      <h3 id="legalTitle">Rechtliches</h3>
      <button class="legal-modal-close" onclick="closeLegal()" aria-label="Schließen">✕</button>
    </div>
    <div class="legal-modal-body" id="legalBody"></div>
  </div>
</div>

<!-- Inhalte fuer die Modals: bleiben unsichtbar, werden per JS in legalBody geladen -->
<template id="legal-agb">
  <h4>§1 Geltungsbereich</h4>
  <p>Diese Allgemeinen Geschäftsbedingungen gelten für alle Verträge zwischen Ihnen und der DGIUG Bank AG — unabhängig davon, ob Sie sie gelesen, verstanden oder überhaupt bemerkt haben, dass es sie gibt.</p>

  <h4>§2 Kontoführung</h4>
  <p>Die Kontoführung ist kostenlos im Sinne von „es kostet etwas, aber wir nennen es anders". Details entnehmen Sie bitte unserer Gebührentabelle, die wir absichtlich in einer anderen Schriftgröße gedruckt haben.</p>

  <h4>§3 Gebührenänderungen</h4>
  <ol>
    <li>Gebühren können sich jederzeit ändern.</li>
    <li>Sie werden darüber informiert — in Absatz 14, Unterabsatz c, auf Seite 96.</li>
    <li>Widerspruch ist möglich, aber wirkungslos.</li>
  </ol>

  <h4>§4 Kevin, unser digitaler Berater</h4>
  <p>Kevin ist kein Mensch, kein Rechtsanwalt und keine verbindliche Auskunftsstelle. Alles, was Kevin sagt, ist unverbindlich, auch wenn er sehr überzeugend klingt. Besonders dann.</p>

  <h4>§5 Kontoschließung</h4>
  <p>Ein Konto kann jederzeit geschlossen werden, sofern der entsprechende Antrag in dreifacher Ausfertigung, unterschrieben, notariell beglaubigt und per Brieftaube eingereicht wird. Bearbeitungszeit: unbestimmt.</p>

  <h4>§6 Haftung</h4>
  <p>Die DGIUG Bank AG haftet für nichts, was entgegen Erwarten schiefgeht, alles was erwartungsgemäß schiefgeht, sowie für Dinge, die noch gar nicht schiefgegangen sind, es aber könnten.</p>

  <h4>§7 Salvatorische Klausel</h4>
  <p>Sollte eine Bestimmung dieser AGB unwirksam sein, bleibt der Rest trotzdem gültig — und wir erfinden bei Gelegenheit eine neue Bestimmung als Ersatz.</p>

  <h4>§8 Schlussbestimmung</h4>
  <p>Mit der Nutzung dieser Webseite erklären Sie sich damit einverstanden, dass Sie diese AGB nicht gelesen haben. Das ist in Ordnung. Wir auch nicht.</p>
</template>

<template id="legal-impressum">
  <h4>Angaben gemäß § 5 TMG (fiktiv)</h4>
  <p>DGIUG Bank AG<br>
  Irgendwo im Nirgendwo 1<br>
  00000 Nirgendwostadt<br>
  Deutschland (wahrscheinlich)</p>

  <h4>Vertreten durch</h4>
  <p>Ralf M., Vorstandsvorsitzender — erreichbar nur, wenn er gerade nicht joggt.</p>

  <h4>Kontakt</h4>
  <p>Telefon: bitte nicht anrufen<br>
  E-Mail: geht-nicht-durch@deingeldistunsergeld.de<br>
  Brieftaube: bevorzugt, aber kostenpflichtig</p>

  <h4>Registereintrag</h4>
  <p>Eintragung im Handelsregister: „folgt seit 2024"<br>
  Registergericht: existiert noch nicht<br>
  Registernummer: 000-NICHT-ECHT</p>

  <h4>Umsatzsteuer-ID</h4>
  <p>Gemäß § 27a Umsatzsteuergesetz: DE-KEVIN-WEISS-ES-NICHT</p>

  <h4>Verantwortlich für den Inhalt</h4>
  <p>Kevin. Immer Kevin.</p>

  <h4>Haftungshinweis</h4>
  <p>Diese Webseite ist ein Scherzprojekt und stellt keine echte Bank dar. Falls Sie versehentlich echtes Geld überwiesen haben: das tut uns leid, und gleichzeitig auch nicht, weil es diese Bank ja gar nicht gibt.</p>
</template>

<template id="legal-datenschutz">
  <h4>1. Welche Daten wir erheben</h4>
  <p>Alles, was Sie uns geben. Und ein bisschen mehr, das wir uns dazudenken. Name, Kontostand, Seufzer beim Lesen der Gebührentabelle — wir erfassen es mit Sorgfalt.</p>

  <h4>2. Warum wir das tun</h4>
  <ul>
    <li>Um Ihnen ein „personalisiertes" Erlebnis zu bieten</li>
    <li>Um herauszufinden, wie viel Gebühr Sie theoretisch noch verkraften</li>
    <li>Aus Prinzip</li>
  </ul>

  <h4>3. Kevin und Ihre Nachrichten</h4>
  <p>Wenn Sie mit Kevin chatten, wird Ihre Nachricht an einen echten Menschen weitergeleitet, der sie liest, bevor Kevin „antwortet". Das ist keine künstliche Intelligenz — das ist künstliche Verzögerung.</p>

  <h4>4. Speicherdauer</h4>
  <p>Ihre Daten werden gespeichert, solange es uns nützt. Das ist absichtlich vage formuliert.</p>

  <h4>5. Weitergabe an Dritte</h4>
  <p>Wir geben Ihre Daten nicht an Dritte weiter. Wir behalten sie lieber selbst.</p>

  <h4>6. Ihre Rechte</h4>
  <p>Sie haben das Recht auf Auskunft, Berichtigung und Löschung. Ausübbar durch einen formlosen Antrag, den wir dann formvoll ablehnen.</p>

  <h4>7. Cookies</h4>
  <p>Wir verwenden Cookies. Und Kekse. Und, wenn Sie beim Banner nicht aufpassen, offenbar auch Ihre Seele. Siehe Cookie-Hinweis.</p>

  <h4>8. Kontakt Datenschutz</h4>
  <p>Bei Fragen zum Datenschutz wenden Sie sich an Kevin. Kevin wird ausweichen, aber freundlich.</p>
</template>

<button class="kevin-bubble" onclick="toggleKevin()" aria-label="Chat mit Kevin öffnen">💬</button>
<div class="kevin-panel" id="kevinPanel">
  <div class="kevin-head">
    <div class="kdot"></div>
    <span>Kevin · Ihr digitaler Berater</span>
    <button class="kevin-close" onclick="toggleKevin()" aria-label="Chat schließen">✕</button>
  </div>
  <div class="kevin-body" id="kevinBody">
    <div class="kmsg bot">Hallo! Ich bin Kevin. Wie kann ich Ihnen heute nicht wirklich helfen?</div>
  </div>
  <div class="kevin-input-row">
    <input type="text" id="kevinInput" placeholder="Nachricht an Kevin …" onkeydown="kevinKeyPress(event)">
    <button onclick="sendKevinMessage()">➤</button>
  </div>
</div>


<script>
  // Live "Kontostand" das langsam sinkt
  let balance = 3482.17;
  const el = document.getElementById('kontostand');
  const status = document.getElementById('statusline');
  const messages = [
    "wird aktualisiert … zu unseren Gunsten",
    "Gebühr wurde soeben erfunden",
    "Kevin hat wieder zugeschlagen",
    "Ihre Zustimmung war nicht erforderlich",
    "Danke für Ihr Vertrauen. Ernsthaft, danke."
  ];
  setInterval(() => {
    balance = Math.max(0, balance - (Math.random()*3.2));
    el.textContent = balance.toLocaleString('de-DE', {minimumFractionDigits:2, maximumFractionDigits:2}) + " €";
    status.textContent = messages[Math.floor(Math.random()*messages.length)];
  }, 1800);

  function oeffnen(){
    alert("Konto wird eröffnet … und schon läuft die Gebührenuhr. Willkommen bei DGIUG Bank!");
  }

  // Cookie-Banner nach kurzer Verzögerung einblenden
  const banner = document.getElementById('cookieBanner');
  setTimeout(() => banner.classList.add('show'), 1600);
  function closeCookie(){ banner.classList.remove('show'); }
  function soulTaken(){
    alert("Vielen Dank. Ihre Seele wurde Ihrem Konto als Sicherheit hinzugefügt.");
    closeCookie();
  }

  const legalTitles = { agb: 'Allgemeine Geschäftsbedingungen', impressum: 'Impressum', datenschutz: 'Datenschutzerklärung' };
  function openLegal(type){
    const tpl = document.getElementById('legal-' + type);
    if(!tpl) return;
    document.getElementById('legalTitle').textContent = legalTitles[type] || 'Rechtliches';
    document.getElementById('legalBody').innerHTML = tpl.innerHTML;
    document.getElementById('legalOverlay').classList.add('open');
  }
  function closeLegal(){
    document.getElementById('legalOverlay').classList.remove('open');
  }
  document.addEventListener('keydown', (e) => { if(e.key === 'Escape') closeLegal(); });
</script>

<script src="https://cdn.socket.io/4.7.5/socket.io.min.js"></script>
<script>
  // ==== KEVIN <-> DISCORD ANBINDUNG ====
  // Hier die URL deines gehosteten Discord-Relay-Bots eintragen (siehe discord-bot/README.md)
  const KEVIN_BACKEND_URL = "https://DEIN-BACKEND-URL.example.com";

  let kevinConversationId = sessionStorage.getItem('kevin_cid');
  if(!kevinConversationId){
    kevinConversationId = (window.crypto && crypto.randomUUID) ? crypto.randomUUID() : ('cid-' + Math.random().toString(36).slice(2) + Date.now());
    sessionStorage.setItem('kevin_cid', kevinConversationId);
  }

  let kevinSocket = null;

  function initKevinSocket(){
    if(kevinSocket || !window.io) return;
    kevinSocket = io(KEVIN_BACKEND_URL, { transports: ['websocket','polling'] });
    kevinSocket.on('connect', () => {
      kevinSocket.emit('join', kevinConversationId);
    });
    kevinSocket.on('kevin:reply', (data) => {
      appendKevinMessage(data.text, 'bot');
    });
  }

  function toggleKevin(){
    const panel = document.getElementById('kevinPanel');
    panel.classList.toggle('open');
    if(panel.classList.contains('open')) initKevinSocket();
  }

  function appendKevinMessage(text, who){
    const body = document.getElementById('kevinBody');
    const div = document.createElement('div');
    div.className = 'kmsg ' + who;
    div.textContent = text;
    body.appendChild(div);
    body.scrollTop = body.scrollHeight;
  }

  function sendKevinMessage(){
    const input = document.getElementById('kevinInput');
    const text = input.value.trim();
    if(!text) return;
    appendKevinMessage(text, 'user');
    input.value = '';
    if(kevinSocket && kevinSocket.connected){
      kevinSocket.emit('web:message', { conversationId: kevinConversationId, text });
    } else {
      appendKevinMessage('Kevin ist gerade offline. Versuch es gleich nochmal.', 'bot');
    }
  }

  function kevinKeyPress(e){
    if(e.key === 'Enter') sendKevinMessage();
  }
</script>

</body>
</html>

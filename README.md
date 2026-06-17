<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Before the Door Closes — With Love</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400;1,700&family=Cormorant+Garamond:ital,wght@0,300;0,400;1,300;1,400&family=Dancing+Script:wght@500;700&display=swap" rel="stylesheet">
<style>
:root{
  --ink:   #08060E;
  --rose:  #8B1A4E;
  --moon:  #DDD0FF;
  --ivory: #F5EDE3;
  --gold:  #C9A86C;
  --gd:    rgba(201,168,108,.18);
  --md:    rgba(221,208,255,.1);
}

*,*::before,*::after{margin:0;padding:0;box-sizing:border-box;}
html{scroll-behavior:smooth;}

body{
  background:var(--ink);
  color:var(--ivory);
  font-family:'Cormorant Garamond',Georgia,serif;
  font-weight:300;
  line-height:1.85;
  overflow-x:hidden;
}

/* ── FIXED BACKGROUND LAYERS ───────────────────────────── */

#cosmos{position:fixed;inset:0;z-index:0;pointer-events:none;}

#cursor-glow{
  position:fixed;width:380px;height:380px;border-radius:50%;
  pointer-events:none;z-index:3;
  background:radial-gradient(circle,rgba(139,26,78,.09) 0%,transparent 65%);
  transform:translate(-50%,-50%);
  opacity:0;transition:opacity .4s ease;
}

#petals{position:fixed;inset:0;z-index:1;pointer-events:none;overflow:hidden;}

.petal{position:absolute;top:-95px;animation:petalDrift linear infinite;}

@keyframes petalDrift{
  0%  {transform:translateY(0) rotate(0deg) translateX(0);opacity:0;}
  6%  {opacity:.65;}
  94% {opacity:.3;}
  100%{transform:translateY(108vh) rotate(var(--rot)) translateX(var(--sway));opacity:0;}
}

/* ── SHARED ─────────────────────────────────────────────── */
section{position:relative;z-index:2;}

@keyframes riseIn{
  from{opacity:0;transform:translateY(30px);}
  to  {opacity:1;transform:translateY(0);}
}
@keyframes fadeIn{from{opacity:0;}to{opacity:1;}}
@keyframes floatGently{
  0%,100%{transform:translateY(0) scale(1);}
  50%    {transform:translateY(-10px) scale(1.04);}
}

/* ── HERO ───────────────────────────────────────────────── */
.hero{
  min-height:100vh;
  display:flex;flex-direction:column;
  align-items:center;justify-content:center;
  text-align:center;padding:4rem 2rem;
}

.hero-eyebrow{
  font-family:'Dancing Script',cursive;
  font-size:1.35rem;color:var(--gold);letter-spacing:.18em;
  opacity:0;animation:riseIn 1.4s ease .3s forwards;
}

.hero-title{
  margin-top:1.4rem;
  font-family:'Playfair Display',serif;font-weight:400;
  font-size:clamp(3rem,9vw,6.5rem);line-height:1.1;
  color:var(--ivory);
  opacity:0;animation:riseIn 1.7s cubic-bezier(.25,.46,.45,.94) .85s forwards;
}
.hero-title em{display:block;font-style:italic;color:var(--moon);}

.hero-sub{
  margin-top:1.8rem;font-size:1.15rem;font-style:italic;
  color:rgba(245,237,227,.5);letter-spacing:.07em;
  opacity:0;animation:riseIn 1.4s ease 1.7s forwards;
}

.hero-scroll{
  margin-top:5rem;
  display:flex;flex-direction:column;align-items:center;gap:.6rem;
  opacity:0;animation:fadeIn 1s ease 3s forwards;
}
.hero-scroll span{
  font-family:'Dancing Script',cursive;
  font-size:.8rem;letter-spacing:.22em;color:rgba(201,168,108,.4);
}
.stem{
  width:1px;height:60px;
  background:linear-gradient(to bottom,var(--gold),transparent);
  animation:stemPulse 2.6s ease-in-out infinite;
}
@keyframes stemPulse{
  0%,100%{opacity:.3;transform:scaleY(.85);}
  50%    {opacity:.9;transform:scaleY(1);}
}

/* ── EPIGRAPH ───────────────────────────────────────────── */
.epigraph-section{
  padding:2rem 2rem 0;
  display:flex;justify-content:center;
}
.epigraph{
  max-width:520px;text-align:center;
  opacity:0;transform:translateY(20px);
  transition:all 1.1s ease;
}
.epigraph.in{opacity:1;transform:translateY(0);}
.epigraph p{
  font-style:italic;font-size:1.12rem;
  line-height:2.1;color:rgba(245,237,227,.48);
}
.epigraph cite{
  display:block;margin-top:1.1rem;
  font-family:'Dancing Script',cursive;
  font-size:.95rem;color:rgba(201,168,108,.55);
}

/* ── LETTER ─────────────────────────────────────────────── */
.letter-section{
  min-height:100vh;
  display:flex;align-items:center;justify-content:center;
  padding:7rem 2rem;
}
.letter-card{
  max-width:590px;width:100%;
  background:linear-gradient(150deg,rgba(139,26,78,.07),rgba(201,168,108,.04));
  border:1px solid var(--gd);
  padding:4.5rem 3.8rem;position:relative;
  opacity:0;transform:translateY(40px);
  transition:opacity 1.2s ease,transform 1.2s ease;
}
.letter-card::before{
  content:'';position:absolute;inset:14px;
  border:1px solid rgba(201,168,108,.07);pointer-events:none;
}
.letter-card.in{opacity:1;transform:translateY(0);}

.letter-open{
  font-family:'Dancing Script',cursive;
  font-size:2.1rem;color:var(--gold);margin-bottom:1.8rem;
}
.letter-text{
  font-size:1.08rem;font-style:italic;
  line-height:2.15;color:rgba(245,237,227,.84);
}
.letter-text em{color:var(--moon);font-style:normal;}
.letter-close{
  font-family:'Dancing Script',cursive;
  font-size:1.55rem;color:var(--moon);
  margin-top:2.2rem;text-align:right;opacity:.9;
}

/* ── HEARTBEAT ──────────────────────────────────────────── */
.heart-section{
  min-height:80vh;
  display:flex;flex-direction:column;
  align-items:center;justify-content:center;
  text-align:center;padding:4rem 2rem;gap:3rem;
}
.heart-wrap{position:relative;width:210px;height:210px;}
.heart-glow{
  position:absolute;inset:-52px;border-radius:50%;
  background:radial-gradient(circle,rgba(139,26,78,.32) 0%,transparent 70%);
  animation:glowPulse 1.2s ease-in-out infinite;
}
@keyframes glowPulse{
  0%,100%{transform:scale(1);   opacity:.55;}
  14%    {transform:scale(1.14);opacity:1;}
  28%    {transform:scale(1);   opacity:.55;}
  42%    {transform:scale(1.09);opacity:.9;}
}
.heart-svg{
  width:100%;height:100%;position:relative;z-index:1;
  fill:var(--rose);
  filter:drop-shadow(0 0 22px rgba(139,26,78,.8))
         drop-shadow(0 0 55px rgba(139,26,78,.38));
  animation:heartBeat 1.2s ease-in-out infinite;
}
@keyframes heartBeat{
  0%  {transform:scale(1);}
  14% {transform:scale(1.13);}
  28% {transform:scale(1);}
  42% {transform:scale(1.08);}
  70% {transform:scale(1);}
  100%{transform:scale(1);}
}
.heart-label{
  font-style:italic;font-size:1.25rem;
  color:rgba(221,208,255,.62);letter-spacing:.15em;
}

/* ── MOMENTS ────────────────────────────────────────────── */
.moments-section{padding:7rem 2rem;max-width:1100px;margin:0 auto;}
.moments-intro{text-align:center;margin-bottom:4.5rem;}
.moments-intro h2{
  font-family:'Playfair Display',serif;
  font-weight:400;font-style:italic;
  font-size:clamp(1.8rem,4vw,3rem);color:var(--ivory);
}
.moments-grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(180px,1fr));
  gap:1.4rem;
}
.moment{
  border:1px solid var(--md);padding:2.8rem 1.7rem;text-align:center;
  opacity:0;transform:translateY(26px);
  transition:opacity .85s ease,transform .85s ease,
             border-color .4s ease,background .4s ease;
}
.moment.in{opacity:1;transform:translateY(0);}
.moment:hover{
  border-color:var(--gd);background:rgba(139,26,78,.09);
  transform:translateY(-7px)!important;
  box-shadow:0 0 36px rgba(139,26,78,.1);
}
.roman{
  display:block;font-family:'Playfair Display',serif;
  font-style:italic;font-size:1.45rem;
  color:var(--gold);opacity:.7;margin-bottom:1rem;
}
.moment p{
  font-style:italic;font-size:.97rem;
  line-height:2;color:rgba(245,237,227,.74);
}

/* ── BRIDGE ─────────────────────────────────────────────── */
.bridge-section{
  min-height:80vh;
  display:flex;flex-direction:column;
  align-items:center;justify-content:center;
  text-align:center;padding:6rem 2rem;
}
.bridge-vein{
  width:1px;height:90px;
  background:linear-gradient(to bottom,transparent,rgba(139,26,78,.8),transparent);
  margin-bottom:3.5rem;
}
.bridge-eye{
  font-family:'Dancing Script',cursive;
  font-size:1.25rem;color:rgba(139,26,78,.95);
  letter-spacing:.14em;margin-bottom:1.5rem;
  opacity:0;transform:translateY(22px);
  transition:opacity 1s ease,transform 1s ease;
}
.bridge-title{
  font-family:'Playfair Display',serif;font-weight:400;
  font-size:clamp(2.2rem,5.5vw,4.2rem);
  line-height:1.2;color:var(--ivory);margin-bottom:2.5rem;
  opacity:0;transform:translateY(22px);
  transition:opacity 1s ease .2s,transform 1s ease .2s;
}
.bridge-title em{color:var(--moon);font-style:italic;}
.bridge-body{
  max-width:540px;font-size:1.12rem;line-height:2.2;
  color:rgba(245,237,227,.6);
  opacity:0;transform:translateY(22px);
  transition:opacity 1s ease .4s,transform 1s ease .4s;
}
.bridge-body strong{
  font-weight:400;font-style:italic;
  color:rgba(245,237,227,.88);
}
.bridge-section.in .bridge-eye,
.bridge-section.in .bridge-title,
.bridge-section.in .bridge-body{opacity:1;transform:translateY(0);}

/* ── Q&A SECTION ────────────────────────────────────────── */
.qa-section{padding:2rem 2rem 8rem;}
.qa-container{max-width:700px;margin:0 auto;}

/* Name field */
.qa-name-wrap{
  margin-bottom:4rem;text-align:center;
  opacity:0;transform:translateY(20px);
  transition:all .8s ease;
}
.qa-name-wrap.in{opacity:1;transform:translateY(0);}
.qa-name-label{
  display:block;font-family:'Dancing Script',cursive;
  font-size:1.35rem;color:var(--gold);margin-bottom:1rem;
}
.qa-name-input{
  width:100%;max-width:360px;
  background:transparent;border:none;
  border-bottom:1px solid rgba(201,168,108,.28);
  color:var(--ivory);
  font-family:'Cormorant Garamond',serif;
  font-weight:300;font-size:1.1rem;
  text-align:center;padding:.65rem 1rem;
  outline:none;transition:border-color .3s ease;
}
.qa-name-input:focus{border-color:var(--gold);}
.qa-name-input::placeholder{color:rgba(245,237,227,.22);font-style:italic;}

/* Optional email */
.qa-email-wrap{
  margin-bottom:4rem;text-align:center;
  opacity:0;transform:translateY(20px);
  transition:all .8s ease .1s;
}
.qa-email-wrap.in{opacity:1;transform:translateY(0);}
.qa-email-label{
  display:block;font-style:italic;font-size:.95rem;
  color:rgba(245,237,227,.38);margin-bottom:.75rem;letter-spacing:.04em;
}

/* Part headers */
.qa-part{
  margin:5rem 0 2.2rem;text-align:center;
  opacity:0;transform:translateY(16px);
  transition:all .8s ease;
}
.qa-part.in{opacity:1;transform:translateY(0);}
.part-label{
  display:block;font-family:'Dancing Script',cursive;
  font-size:.9rem;color:rgba(201,168,108,.5);
  letter-spacing:.25em;margin-bottom:.4rem;
}
.part-title{
  font-family:'Playfair Display',serif;
  font-weight:400;font-style:italic;
  font-size:1.7rem;color:var(--moon);
}

/* Q items */
.qa-item{
  margin-bottom:2rem;padding:2.2rem 2.4rem;
  border:1px solid rgba(201,168,108,.1);
  background:rgba(8,6,14,.5);
  backdrop-filter:blur(10px);
  opacity:0;transform:translateY(16px);
  transition:opacity .8s ease,transform .8s ease,border-color .3s ease;
}
.qa-item.in{opacity:1;transform:translateY(0);}
.qa-item:hover{border-color:rgba(201,168,108,.2);}
.qa-item.qa-final{
  border-color:rgba(201,168,108,.25);
  background:rgba(139,26,78,.08);
}

.q-num{
  display:block;font-family:'Playfair Display',serif;
  font-style:italic;font-size:.8rem;
  color:rgba(201,168,108,.48);letter-spacing:.14em;
  margin-bottom:.7rem;
}
.q-text{
  font-family:'Playfair Display',serif;
  font-weight:400;font-style:italic;
  font-size:1.1rem;color:rgba(245,237,227,.9);
  line-height:1.65;margin-bottom:1.2rem;
}
.qa-textarea{
  width:100%;background:transparent;
  border:none;border-bottom:1px solid rgba(201,168,108,.14);
  color:var(--ivory);
  font-family:'Cormorant Garamond',serif;
  font-weight:300;font-size:1rem;font-style:italic;
  line-height:1.9;padding:.8rem .2rem;
  min-height:92px;resize:vertical;
  outline:none;transition:border-color .3s ease;
}
.qa-textarea:focus{border-bottom-color:rgba(201,168,108,.48);}
.qa-textarea::placeholder{color:rgba(245,237,227,.16);font-style:italic;}
.qa-textarea::-webkit-scrollbar{width:3px;}
.qa-textarea::-webkit-scrollbar-thumb{background:rgba(201,168,108,.22);}

/* Submit */
.submit-wrap{
  margin-top:5rem;text-align:center;
  opacity:0;transform:translateY(20px);
  transition:all .8s ease;
}
.submit-wrap.in{opacity:1;transform:translateY(0);}
.submit-note{
  font-style:italic;font-size:1rem;
  color:rgba(245,237,227,.42);margin-bottom:2.2rem;
}
.submit-btn{
  background:transparent;
  border:1px solid rgba(201,168,108,.35);
  color:var(--gold);
  font-family:'Dancing Script',cursive;
  font-size:1.9rem;padding:1.25rem 4.5rem;
  cursor:pointer;letter-spacing:.04em;
  position:relative;overflow:hidden;
  transition:all .5s ease;
}
.submit-btn::before{
  content:'';position:absolute;inset:0;
  background:linear-gradient(135deg,rgba(139,26,78,0),rgba(139,26,78,.35));
  opacity:0;transition:opacity .5s ease;
}
.submit-btn:hover::before{opacity:1;}
.submit-btn:hover{
  border-color:rgba(201,168,108,.7);
  box-shadow:0 0 50px rgba(139,26,78,.22);
  transform:translateY(-3px);
}
.submit-btn:disabled{opacity:.45;cursor:not-allowed;transform:none;}
.submit-btn:disabled::before{opacity:0;}
#btn-text{position:relative;z-index:1;}

#error-msg{
  margin-top:1.5rem;display:none;
  font-style:italic;font-size:.95rem;
  color:rgba(255,140,140,.7);
}

/* Success state */
#success-state{transition:opacity 1s ease;}
.success-card{text-align:center;padding:7rem 2rem;}
.success-fleur{
  display:block;font-size:3.2rem;color:var(--gold);
  margin-bottom:2.2rem;
  animation:floatGently 4s ease-in-out infinite;
}
.success-title{
  font-family:'Playfair Display',serif;
  font-weight:400;font-style:italic;
  font-size:clamp(2rem,5vw,3.2rem);
  color:var(--ivory);margin-bottom:1.5rem;
}
.success-body{
  font-style:italic;font-size:1.12rem;
  line-height:2.4;color:rgba(245,237,227,.72);
}

/* ── CLOSE ──────────────────────────────────────────────── */
.close-section{
  min-height:80vh;
  display:flex;align-items:center;justify-content:center;
  padding:6rem 2rem;
}
.close-inner{text-align:center;max-width:460px;}
.fleur{
  display:block;font-size:3rem;color:var(--rose);
  margin-bottom:2.2rem;
  filter:drop-shadow(0 0 16px rgba(139,26,78,.65));
  animation:floatGently 4s ease-in-out infinite;
}
.close-title{
  font-family:'Playfair Display',serif;
  font-weight:400;font-style:italic;
  font-size:clamp(2rem,4.5vw,3.2rem);
  color:var(--ivory);margin-bottom:1.6rem;
}
.close-body{
  font-style:italic;font-size:1.12rem;
  line-height:2.35;color:rgba(245,237,227,.72);
  margin-bottom:2.8rem;
}
.close-sig{
  font-family:'Dancing Script',cursive;
  font-size:2rem;color:var(--gold);
}

/* ── RESPONSIVE ─────────────────────────────────────────── */
@media(max-width:640px){
  .letter-card{padding:2.8rem 1.8rem;}
  .qa-item{padding:1.8rem 1.5rem;}
  .submit-btn{padding:1.1rem 2.8rem;font-size:1.6rem;}
  .moments-grid{grid-template-columns:1fr 1fr;}
}
@media(max-width:440px){
  .moments-grid{grid-template-columns:1fr;}
}
@media(prefers-reduced-motion:reduce){
  .petal,.heart-svg,.heart-glow,.stem,.fleur{animation:none!important;}
}
</style>
</head>
<body>

<!-- ── FIXED LAYERS ── -->
<canvas id="cosmos"></canvas>
<div id="cursor-glow"></div>
<div id="petals"></div>

<!-- ══════════════════════════════════════
     HERO
══════════════════════════════════════ -->
<section class="hero">
  <p class="hero-eyebrow">what we were</p>
  <h1 class="hero-title">
    I loved you<br>
    <em>in every way I knew how</em>
  </h1>
  <p class="hero-sub">and I am still here — still listening</p>
  <div class="hero-scroll">
    <span>begin</span>
    <div class="stem"></div>
  </div>
</section>

<!-- ══════════════════════════════════════
     EPIGRAPH
══════════════════════════════════════ -->
<section class="epigraph-section">
  <blockquote class="epigraph" data-watch>
    <p>"Tonight I can write the saddest lines.<br>
       I loved her, and sometimes she loved me too."</p>
    <cite>— Pablo Neruda</cite>
  </blockquote>
</section>

<!-- ══════════════════════════════════════
     LETTER
══════════════════════════════════════ -->
<section class="letter-section">
  <div class="letter-card" data-watch>
    <p class="letter-open">My love,</p>
    <p class="letter-text">
      There are words I have searched the length of every language to find,<br>
      and none of them have ever been enough.<br><br>
      So here, instead, is the truth in its most unadorned form —<br>
      You were the pause before the music began.<br>
      The warmth that filled every room you entered.<br>
      The quiet I had been looking for without knowing its name.<br><br>
      I loved you in the small hours and in the ordinary rush,<br>
      in the in-between spaces where love quietly took root —<br>
      and I let it. Without question. Without condition.<br><br>
      I still don't fully understand where that love went.<br>
      <em>That is why I need you to tell me.</em>
    </p>
    <p class="letter-close">— yours, still</p>
  </div>
</section>

<!-- ══════════════════════════════════════
     HEARTBEAT
══════════════════════════════════════ -->
<section class="heart-section">
  <div class="heart-wrap">
    <div class="heart-glow"></div>
    <svg class="heart-svg" viewBox="0 0 100 90" xmlns="http://www.w3.org/2000/svg">
      <path d="M50 86C50 86 4 52 4 26C4 10 17 2 34 8C41 11 46 17 50 24C54 17 59 11 66 8C83 2 96 10 96 26C96 52 50 86 50 86Z"/>
    </svg>
  </div>
  <p class="heart-label">still beating — still yours</p>
</section>

<!-- ══════════════════════════════════════
     MOMENTS
══════════════════════════════════════ -->
<section class="moments-section">
  <div class="moments-intro"><h2>The things I will always carry</h2></div>
  <div class="moments-grid">
    <div class="moment" data-watch data-delay="0">
      <span class="roman">I</span>
      <p>the way you laughed<br>at your own stories<br>before you finished them</p>
    </div>
    <div class="moment" data-watch data-delay="140">
      <span class="roman">II</span>
      <p>how the world became<br>smaller and safer<br>when you were near</p>
    </div>
    <div class="moment" data-watch data-delay="280">
      <span class="roman">III</span>
      <p>the quiet that lived<br>between us<br>that asked for nothing</p>
    </div>
    <div class="moment" data-watch data-delay="420">
      <span class="roman">IV</span>
      <p>every ordinary moment<br>you made feel like<br>the only one that mattered</p>
    </div>
    <div class="moment" data-watch data-delay="560">
      <span class="roman">V</span>
      <p>the way even your absence<br>still feels like you —<br>something I keep reaching for</p>
    </div>
  </div>
</section>

<!-- ══════════════════════════════════════
     BRIDGE
══════════════════════════════════════ -->
<section class="bridge-section" data-watch>
  <div class="bridge-vein"></div>
  <p class="bridge-eye">and yet</p>
  <h2 class="bridge-title">There are things<br><em>I need to understand.</em></h2>
  <p class="bridge-body">
    These are the questions I have been carrying in silence —<br>
    ones I was too afraid to ask out loud.<br><br>
    But the not-knowing has its own kind of weight.<br><br>
    <strong>If you can find the words — I am ready to receive them.<br>
    Without anger. Without blame.<br>
    Only with the quiet hope of understanding.</strong>
  </p>
</section>

<!-- ══════════════════════════════════════
     Q & A SECTION
══════════════════════════════════════ -->
<section class="qa-section">
  <div class="qa-container">

    <!-- FORM WRAPPER -->
    <div id="qa-form-wrap">
      <form id="qa-form">
        <!-- FormSubmit config -->
        <input type="hidden" name="_subject"  value="Your Truth — Questions Answered With Love">
        <input type="hidden" name="_captcha"  value="false">
        <input type="hidden" name="_template" value="table">
        <input type="text"   name="_honey"    style="display:none" tabindex="-1" aria-hidden="true">

        <!-- NAME -->
        <div class="qa-name-wrap" data-watch>
          <label class="qa-name-label">Yo

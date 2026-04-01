<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AndMetaX — Doginal Dog #4238</title>
<link href="https://fonts.googleapis.com/css2?family=Bangers&family=Black+Ops+One&family=Rajdhani:wght@600;700&display=swap" rel="stylesheet">
<style>
:root{
  --ng:#00ff88;--nc:#00ffff;--np:#ff00ff;--ny:#ffff00;--no:#ff6600;--nr:#ff2244;
  --void:#000008;
  --gg:0 0 8px #00ff88,0 0 24px #00ff88;
  --gc:0 0 8px #00ffff,0 0 24px #00ffff;
  --gp:0 0 8px #ff00ff,0 0 24px #ff00ff;
  --gy:0 0 8px #ffff00,0 0 24px #ffff00;
}
*{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent}
body{background:var(--void);font-family:'Rajdhani',sans-serif;min-height:100vh;overflow-x:hidden;cursor:crosshair}

/* ── BG CANVAS ── */
#bgCanvas{position:fixed;inset:0;z-index:0;width:100%;height:100%}

/* ── FLOATING COMIC BG LAYER ── */
.bgl{position:fixed;inset:0;z-index:1;overflow:hidden;pointer-events:none}
.fw{position:absolute;font-family:'Bangers',cursive;color:transparent;letter-spacing:4px;pointer-events:none;animation:floatUp linear infinite;white-space:nowrap}
@keyframes floatUp{0%{transform:translateY(110vh) rotate(var(--r0));opacity:0}5%{opacity:1}95%{opacity:1}100%{transform:translateY(-15vh) rotate(var(--r1));opacity:0}}
.fp{position:absolute;border:2px solid;animation:panelDrift linear infinite}
@keyframes panelDrift{0%{transform:translateY(110vh) rotate(var(--r0));opacity:0}8%{opacity:1}92%{opacity:1}100%{transform:translateY(-15vh) rotate(var(--r1));opacity:0}}

/* ── HALFTONE + SCANLINES ── */
.halftone{position:fixed;inset:0;z-index:1;background-image:radial-gradient(circle,rgba(255,229,0,.06) 1px,transparent 1px);background-size:12px 12px;pointer-events:none;animation:haloShift 8s linear infinite}
@keyframes haloShift{0%{background-position:0 0}100%{background-position:48px 48px}}
.scanlines{position:fixed;inset:0;z-index:2;background:repeating-linear-gradient(0deg,transparent,transparent 2px,rgba(0,255,136,.012) 2px,rgba(0,255,136,.012) 4px);pointer-events:none}
.vig{position:fixed;inset:0;z-index:2;background:radial-gradient(ellipse at center,transparent 35%,rgba(0,0,5,.88) 100%);pointer-events:none}

/* ── MUSIC BTN ── */
#musicBtn{position:fixed;top:14px;left:14px;z-index:1000;width:40px;height:40px;border-radius:50%;background:rgba(0,0,8,.92);border:2px solid var(--ng);color:var(--ng);font-size:17px;display:flex;align-items:center;justify-content:center;cursor:pointer;box-shadow:var(--gg);transition:.2s}
#musicBtn:hover{background:rgba(0,255,136,.18);transform:scale(1.1)}
#musicBtn.off{border-color:rgba(0,255,136,.3);color:rgba(0,255,136,.3);box-shadow:none}

/* ── ZAP POPUP ── */
.zap{position:fixed;font-family:'Bangers',cursive;font-size:38px;pointer-events:none;z-index:9000;letter-spacing:2px;animation:zapPop .75s ease-out forwards}
@keyframes zapPop{0%{transform:translate(-50%,-50%) scale(.3) rotate(-15deg);opacity:1}40%{transform:translate(-50%,-80%) scale(1.6) rotate(5deg);opacity:1}100%{transform:translate(-50%,-140%) scale(1) rotate(0deg);opacity:0}}

/* ── PAGE ── */
.page{position:relative;z-index:10;min-height:100vh;display:flex;flex-direction:column;align-items:center;justify-content:center;padding:50px 20px 70px}

/* ── TITLE BANNER ── */
.tban{text-align:center;margin-bottom:22px}
.tban .ser{font-family:'Black Ops One',cursive;font-size:10px;letter-spacing:6px;color:var(--nc);text-shadow:var(--gc);display:block;margin-bottom:4px;animation:flk 5s infinite}
@keyframes flk{0%,18%,20%,22%,24%,54%,56%,100%{opacity:1}19%,23%,55%{opacity:.3}}
.tban .logo{font-family:'Bangers',cursive;font-size:clamp(54px,15vw,92px);letter-spacing:8px;line-height:.9;color:var(--ng);text-shadow:var(--gg),5px 5px 0 #003320,10px 10px 0 rgba(0,255,136,.15);display:block;animation:logoPulse 2.5s ease-in-out infinite}
@keyframes logoPulse{0%,100%{text-shadow:var(--gg),5px 5px 0 #003320}50%{text-shadow:0 0 20px #00ff88,0 0 70px #00ff88,0 0 130px #00ff88,5px 5px 0 #003320}}
.tban .sub{font-family:'Black Ops One',cursive;font-size:9px;letter-spacing:4px;color:var(--np);text-shadow:var(--gp);display:block;margin-top:7px;animation:flk 7s infinite 2s}

/* ── CARD ── */
.card{max-width:430px;width:100%;position:relative;background:rgba(0,0,10,.94);border:3px solid var(--ng);animation:cardGlow 4s ease-in-out infinite}
@keyframes cardGlow{0%,100%{box-shadow:0 0 0 1px rgba(0,255,136,.15),0 0 30px rgba(0,255,136,.25),0 0 80px rgba(0,255,136,.08),8px 8px 0 rgba(255,34,68,.3);border-color:var(--ng)}33%{box-shadow:0 0 0 1px rgba(0,255,255,.15),0 0 30px rgba(0,255,255,.25),0 0 80px rgba(0,255,255,.08),8px 8px 0 rgba(0,255,255,.2);border-color:var(--nc)}66%{box-shadow:0 0 0 1px rgba(255,0,255,.15),0 0 30px rgba(255,0,255,.25),0 0 80px rgba(255,0,255,.08),8px 8px 0 rgba(255,0,255,.2);border-color:var(--np)}}
/* corner brackets */
.card::before{content:'';position:absolute;top:-5px;left:-5px;width:28px;height:28px;border-top:3px solid var(--nc);border-left:3px solid var(--nc);box-shadow:-2px -2px 8px var(--nc);z-index:20}
.card::after{content:'';position:absolute;bottom:-5px;right:-5px;width:28px;height:28px;border-bottom:3px solid var(--np);border-right:3px solid var(--np);box-shadow:2px 2px 8px var(--np);z-index:20}
.ctr{position:absolute;top:-5px;right:-5px;width:28px;height:28px;border-top:3px solid var(--ny);border-right:3px solid var(--ny);box-shadow:2px -2px 8px var(--ny);z-index:20}
.cbl{position:absolute;bottom:-5px;left:-5px;width:28px;height:28px;border-bottom:3px solid var(--no);border-left:3px solid var(--no);box-shadow:-2px 2px 8px var(--no);z-index:20}

/* ── BONE — above pfp, clickable ── */
.bone-wrap{display:flex;justify-content:center;align-items:center;padding:10px 0 0;background:linear-gradient(180deg,#001018,#000d1a)}
.bone-link{text-decoration:none;display:inline-flex;align-items:center;justify-content:center;width:48px;height:48px;position:relative;cursor:pointer}
.bone-emoji{font-size:30px;display:block;animation:boneGlow 2s ease-in-out infinite;filter:drop-shadow(0 0 6px var(--ng)) drop-shadow(0 0 14px var(--ng))}
@keyframes boneGlow{0%,100%{transform:translateY(0px) rotate(-10deg);filter:drop-shadow(0 0 6px var(--ng)) drop-shadow(0 0 14px var(--ng))}50%{transform:translateY(-6px) rotate(10deg);filter:drop-shadow(0 0 12px var(--ng)) drop-shadow(0 0 30px var(--ng)) drop-shadow(0 0 50px rgba(0,255,136,.4))}}
.bone-label{position:absolute;bottom:-18px;left:50%;transform:translateX(-50%);font-family:'Black Ops One',cursive;font-size:7px;letter-spacing:2px;color:var(--ng);white-space:nowrap;opacity:0;transition:.25s;text-shadow:var(--gg)}
.bone-link:hover .bone-label{opacity:1}

/* ── HEADER ── */
.ch{background:linear-gradient(90deg,#001a08,#000d20,#1a0020);border-top:1px solid rgba(0,255,136,.15);border-bottom:1px solid rgba(0,255,136,.2);padding:8px 16px;display:flex;justify-content:space-between;align-items:center;position:relative;overflow:hidden}
.ch::after{content:'';position:absolute;bottom:0;left:0;right:0;height:1px;background:linear-gradient(90deg,var(--ng),var(--nc),var(--np));animation:scanBar 3s linear infinite}
@keyframes scanBar{0%{transform:translateX(-100%)}100%{transform:translateX(100%)}}
.it{font-family:'Black Ops One',cursive;font-size:9px;letter-spacing:2px;color:var(--ng);text-shadow:var(--gg)}
/* FREE MINT — clickable, easter egg 1 */
.free-mint-btn{font-family:'Bangers',cursive;font-size:14px;letter-spacing:2px;color:var(--ny);text-shadow:var(--gy);border:2px solid var(--ny);padding:2px 10px;box-shadow:0 0 10px rgba(255,255,0,.4),inset 0 0 8px rgba(255,255,0,.05);animation:mintBlink 3.5s infinite;cursor:pointer;text-decoration:none;display:inline-block;transition:.15s;background:rgba(255,255,0,.05)}
.free-mint-btn:hover{background:rgba(255,255,0,.18);box-shadow:0 0 24px rgba(255,255,0,.7);transform:scale(1.06)}
@keyframes mintBlink{0%,88%,100%{opacity:1}90%,96%{opacity:.35}}

/* ── AVATAR SECTION ── */
.aw{background:linear-gradient(180deg,#000d1a 0%,#000508 100%);display:flex;justify-content:center;padding:22px 20px 20px;position:relative;overflow:hidden}
.aw::after{content:'';position:absolute;bottom:0;left:0;right:0;height:34px;background:linear-gradient(90deg,rgba(0,255,136,.07) 1px,transparent 1px),linear-gradient(0deg,rgba(0,255,136,.07) 1px,transparent 1px);background-size:20px 20px;transform:perspective(80px) rotateX(45deg);transform-origin:bottom;opacity:.5}
/* spinning rings container */
.av-wrap{position:relative;width:154px;height:154px}
.ring{position:absolute;border-radius:0;border-style:solid;top:50%;left:50%;animation:spinRing linear infinite;pointer-events:none}
.r1{width:178px;height:178px;border-width:2px;border-color:var(--ng) transparent var(--ng) transparent;box-shadow:0 0 10px var(--ng);animation-duration:3s;border-radius:0}
.r2{width:198px;height:198px;border-width:1px;border-color:transparent var(--nc) transparent var(--nc);box-shadow:0 0 8px var(--nc);animation-duration:5s;animation-direction:reverse}
.r3{width:218px;height:218px;border-width:1px;border-color:var(--np) transparent transparent transparent;box-shadow:0 0 6px var(--np);animation-duration:7s}
@keyframes spinRing{from{transform:translate(-50%,-50%) rotate(0deg)}to{transform:translate(-50%,-50%) rotate(360deg)}}
/* SQUARE AVATAR FRAME */
.av-link{display:block;position:relative;z-index:5;width:154px;height:154px;text-decoration:none}
.av-frame{width:154px;height:154px;border:3px solid var(--ng);overflow:hidden;background:#7dffb3;position:relative;animation:avPulse 2.5s ease-in-out infinite;image-rendering:pixelated}
.av-frame::before{content:'';position:absolute;top:0;left:0;width:14px;height:14px;border-top:3px solid var(--nc);border-left:3px solid var(--nc);z-index:10;pointer-events:none}
.av-frame::after{content:'';position:absolute;bottom:0;right:0;width:14px;height:14px;border-bottom:3px solid var(--np);border-right:3px solid var(--np);z-index:10;pointer-events:none}
@keyframes avPulse{0%,100%{border-color:var(--ng);box-shadow:0 0 0 2px rgba(0,255,136,.2),0 0 24px var(--ng),0 0 60px rgba(0,255,136,.3)}33%{border-color:var(--nc);box-shadow:0 0 0 2px rgba(0,255,255,.2),0 0 24px var(--nc),0 0 60px rgba(0,255,255,.3)}66%{border-color:var(--np);box-shadow:0 0 0 2px rgba(255,0,255,.2),0 0 24px var(--np),0 0 60px rgba(255,0,255,.3)}}
.av-frame img{width:154px;height:154px;display:block;image-rendering:pixelated;image-rendering:crisp-edges}
/* scan sweep */
.av-scan{position:absolute;inset:0;background:linear-gradient(180deg,transparent 0%,rgba(0,255,136,.07) 50%,transparent 100%);animation:avScan 3s ease-in-out infinite;pointer-events:none;z-index:8}
@keyframes avScan{0%{transform:translateY(-154px)}100%{transform:translateY(154px)}}
.av-glow{position:absolute;inset:0;background:radial-gradient(circle,rgba(0,255,136,.13),transparent 70%);opacity:0;transition:.3s;z-index:6;pointer-events:none}
.av-link:hover .av-glow{opacity:1}
.x-badge{position:absolute;bottom:-16px;left:50%;transform:translateX(-50%) scale(.85);background:var(--void);border:2px solid var(--ny);color:var(--ny);font-family:'Black Ops One',cursive;font-size:8px;letter-spacing:3px;padding:3px 12px;white-space:nowrap;text-shadow:var(--gy);box-shadow:0 0 12px rgba(255,255,0,.4);z-index:10;opacity:0;transition:.25s}
.av-link:hover .x-badge{opacity:1;transform:translateX(-50%) scale(1)}
.ptag{position:absolute;bottom:8px;left:50%;transform:translateX(-50%);background:var(--void);border:1px solid var(--nc);color:var(--nc);font-family:'Black Ops One',cursive;font-size:8px;letter-spacing:3px;padding:3px 12px;white-space:nowrap;text-shadow:var(--gc);box-shadow:0 0 10px rgba(0,255,255,.35);z-index:10}

/* ── CARD BODY ── */
.cb{padding:20px 20px 16px;background:rgba(0,0,10,.96)}
/* name */
.nd{text-align:center;margin-bottom:14px;position:relative}
.nd::before,.nd::after{content:'◈';font-size:13px;color:var(--np);text-shadow:var(--gp);position:absolute;top:50%;transform:translateY(-50%)}
.nd::before{left:0}.nd::after{right:0}
.nd h1{font-family:'Bangers',cursive;font-size:clamp(36px,10vw,52px);letter-spacing:6px;color:var(--ng);text-shadow:0 0 10px var(--ng),0 0 30px var(--ng),3px 3px 0 rgba(0,80,40,.8);line-height:1;animation:nameGlitch 9s infinite}
@keyframes nameGlitch{0%,88%,100%{text-shadow:0 0 10px var(--ng),0 0 30px var(--ng),3px 3px 0 rgba(0,80,40,.8);transform:none}89%{transform:translateX(-3px);text-shadow:3px 0 var(--nc),-3px 0 var(--np)}90%{transform:translateX(3px);text-shadow:-3px 0 var(--nc),3px 0 var(--np)}91%,99%{transform:none;text-shadow:0 0 10px var(--ng),0 0 30px var(--ng),3px 3px 0 rgba(0,80,40,.8)}}
/* stats */
.stats{display:grid;grid-template-columns:1fr 1fr;gap:5px;margin-bottom:14px}
.sb{background:rgba(0,255,136,.04);border:1px solid rgba(0,255,136,.1);padding:5px 8px}
.slb{font-size:7px;letter-spacing:2px;color:rgba(0,255,136,.45);display:block;margin-bottom:3px}
.sf{height:4px;animation:statFill 2.2s ease-out forwards;transform-origin:left}
@keyframes statFill{from{transform:scaleX(0)}to{transform:scaleX(1)}}
/* bio */
.bp{border:1px solid rgba(0,255,255,.18);border-left:3px solid var(--nc);background:rgba(0,255,255,.025);padding:12px 14px;margin-bottom:16px;position:relative}
.bp::before{content:'// BIO.txt';position:absolute;top:-9px;left:10px;background:var(--void);color:var(--nc);font-size:7px;letter-spacing:2px;padding:0 6px;text-shadow:var(--gc)}
.bp p{color:rgba(200,255,230,.85);font-size:11.5px;line-height:1.75;letter-spacing:.2px}
.bp strong{color:var(--ny);text-shadow:0 0 8px rgba(255,255,0,.5);font-weight:700}
.bp em{color:var(--ng);font-style:normal}
.bp .secret{color:rgba(0,255,136,.38);font-size:9px;margin-top:9px;display:block;border-top:1px solid rgba(0,255,136,.1);padding-top:7px;letter-spacing:.5px}
/* section label */
.sl2{font-family:'Black Ops One',cursive;font-size:9px;letter-spacing:5px;color:var(--np);text-shadow:var(--gp);text-align:center;margin-bottom:12px;position:relative}
.sl2::before,.sl2::after{content:'';position:absolute;top:50%;width:20%;height:1px}
.sl2::before{left:0;background:linear-gradient(90deg,transparent,var(--np))}
.sl2::after{right:0;background:linear-gradient(270deg,transparent,var(--np))}
/* links */
.lks{display:flex;flex-direction:column;gap:10px}
.lk{display:flex;align-items:center;text-decoration:none;border:2px solid rgba(0,255,136,.22);background:rgba(0,255,136,.03);overflow:hidden;position:relative;transition:all .2s;box-shadow:3px 3px 0 rgba(0,255,136,.15)}
.lk::before{content:'';position:absolute;inset:0;background:linear-gradient(90deg,transparent,rgba(0,255,136,.06),transparent);transform:translateX(-100%);transition:.5s}
.lk:hover{border-color:var(--ng);box-shadow:0 0 20px rgba(0,255,136,.3),4px 4px 0 rgba(0,255,136,.3);transform:translate(-2px,-2px)}
.lk:hover::before{transform:translateX(100%)}
.lk.pink{border-color:rgba(255,0,255,.22);background:rgba(255,0,255,.03);box-shadow:3px 3px 0 rgba(255,0,255,.15)}
.lk.pink:hover{border-color:var(--np);box-shadow:0 0 20px rgba(255,0,255,.3),4px 4px 0 rgba(255,0,255,.3)}
.lk.cyan{border-color:rgba(0,255,255,.22);background:rgba(0,255,255,.03);box-shadow:3px 3px 0 rgba(0,255,255,.15)}
.lk.cyan:hover{border-color:var(--nc);box-shadow:0 0 20px rgba(0,255,255,.3),4px 4px 0 rgba(0,255,255,.3)}
.lk.yellow{border-color:rgba(255,255,0,.22);background:rgba(255,255,0,.03);box-shadow:3px 3px 0 rgba(255,255,0,.15)}
.lk.yellow:hover{border-color:var(--ny);box-shadow:0 0 20px rgba(255,255,0,.3),4px 4px 0 rgba(255,255,0,.3)}
.lth{width:68px;height:68px;object-fit:cover;flex-shrink:0;border-right:2px solid rgba(0,255,136,.15)}
.lk.pink .lth,.lk.pink canvas{border-right-color:rgba(255,0,255,.15)}
.lk.cyan .lth,.lk.cyan canvas{border-right-color:rgba(0,255,255,.15)}
.lk.yellow .lth,.lk.yellow canvas{border-right-color:rgba(255,255,0,.15)}
.lth-c{width:68px;height:68px;flex-shrink:0;border-right:2px solid rgba(0,255,255,.15);display:block;image-rendering:pixelated}
.li{flex:1;padding:10px 12px}
.ln{font-family:'Black Ops One',cursive;font-size:12px;letter-spacing:1px;color:var(--ng);text-shadow:0 0 8px rgba(0,255,136,.4);display:block;line-height:1.3}
.lk.pink .ln{color:var(--np);text-shadow:0 0 8px rgba(255,0,255,.4)}
.lk.cyan .ln{color:var(--nc);text-shadow:0 0 8px rgba(0,255,255,.4)}
.lk.yellow .ln{color:var(--ny);text-shadow:0 0 8px rgba(255,255,0,.4)}
.lm{font-size:8px;letter-spacing:2px;color:rgba(0,255,255,.45);display:block;margin-top:3px}
.la{width:38px;height:68px;display:flex;align-items:center;justify-content:center;font-size:18px;color:var(--ng);text-shadow:var(--gg);border-left:1px solid rgba(0,255,136,.12);flex-shrink:0;font-family:'Bangers',cursive;transition:.2s}
.lk:hover .la{transform:translateX(3px)}
.lk.pink .la{color:var(--np);text-shadow:var(--gp)}
.lk.cyan .la{color:var(--nc);text-shadow:var(--gc)}
.lk.yellow .la{color:var(--ny);text-shadow:var(--gy)}

/* ── FOOTER ── */
.cf{background:linear-gradient(90deg,#001a08,#000d20,#1a0020);border-top:2px solid rgba(0,255,136,.12);padding:10px 16px;display:flex;justify-content:space-between;align-items:center;position:relative;overflow:hidden}
.cf::before{content:'';position:absolute;top:0;left:0;right:0;height:1px;background:linear-gradient(90deg,var(--np),var(--nc),var(--ng));animation:scanBar 4s linear infinite reverse}
.ft{font-family:'Black Ops One',cursive;font-size:7px;letter-spacing:3px;color:rgba(0,255,136,.35)}
/* CONTINUED — easter egg 3, plays portal animation then opens link */
.cont-btn{font-family:'Bangers',cursive;font-size:15px;letter-spacing:3px;color:var(--nc);text-shadow:var(--gc);cursor:pointer;background:rgba(0,255,255,.06);border:2px solid rgba(0,255,255,.4);padding:5px 14px;transition:.2s;outline:none}
.cont-btn:hover{border-color:var(--nc);box-shadow:0 0 16px rgba(0,255,255,.5),inset 0 0 12px rgba(0,255,255,.08);color:#fff;text-shadow:0 0 20px #00ffff}

/* ── PORTAL OVERLAY ── */
#portalOverlay{position:fixed;inset:0;z-index:8000;display:none;align-items:center;justify-content:center;pointer-events:none}
#portalOverlay.active{display:flex;pointer-events:all}
#portalCanvas{position:absolute;inset:0;width:100%;height:100%}
.portal-msg{position:relative;z-index:2;text-align:center;opacity:0;transition:.5s}
.portal-msg h2{font-family:'Bangers',cursive;font-size:40px;letter-spacing:8px;color:var(--nc);text-shadow:var(--gc),0 0 80px #00ffff}
.portal-msg p{font-family:'Black Ops One',cursive;font-size:10px;letter-spacing:4px;color:rgba(0,255,255,.65);margin-top:8px}

@media(max-width:460px){.lth,.lth-c{width:56px;height:56px}.la{width:32px;height:56px}.stats{grid-template-columns:1fr}}
</style>
</head>
<body>

<!-- MUSIC BTN -->
<button id="musicBtn" class="off" onclick="toggleMusic()" title="Toggle music">▶</button>

<!-- BG LAYERS -->
<canvas id="bgCanvas"></canvas>
<div class="bgl" id="bgl"></div>
<div class="halftone"></div>
<div class="scanlines"></div>
<div class="vig"></div>

<!-- PORTAL -->
<div id="portalOverlay">
  <canvas id="portalCanvas"></canvas>
  <div class="portal-msg" id="portalMsg">
    <h2>🌌 ENTERING THE UNIVERSE 🌌</h2>
    <p>◈ DOGINAL DOGS WORLD AWAITS ◈</p>
  </div>
</div>

<main class="page">

  <!-- TITLE -->
  <div class="tban">
    <span class="ser">◈ ANDMETAX UNIVERSE · ISSUE #001 ◈</span>
    <span class="logo">AndMetaX</span>
    <span class="sub">⚡ DIGITAL AND'S UNIVERSE COLLECTION ⚡</span>
  </div>

  <div class="card">
    <div class="ctr"></div><div class="cbl"></div>

    <!-- BONE — easter egg 2, above pfp, clickable -->
    <div class="bone-wrap">
      <a class="bone-link" href="https://x.com/DDSalesBot" target="_blank" rel="noopener">
        <span class="bone-emoji">🦴</span>
        <span class="bone-label">DD SALES BOT</span>
      </a>
    </div>

    <!-- HEADER -->
    <div class="ch">
      <span class="it">★ DOGINAL WAR ARC · VOL.1</span>
      <a class="free-mint-btn" href="https://market.doginaldogs.com/" target="_blank" rel="noopener">FREE MINT</a>
    </div>

    <!-- AVATAR -->
    <div class="aw">
      <div class="av-wrap">
        <div class="ring r1"></div>
        <div class="ring r2"></div>
        <div class="ring r3"></div>
        <a class="av-link" href="https://x.com/Andmetax" target="_blank" rel="noopener" title="@Andmetax on X">
          <div class="av-frame">
            <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAA+gAAAPoCAYAAABNo9TkAAAaj0lEQVR4nO3ZMW5cexmH4QyamgYpdQrfAqXMAmixi4gF+DapwJSTHqXPoUJJKhfcWUBkJDsswrejcgoKKko2MGzgchA21veO8zwr+Mk6+o9ffZvlsD88AwAAAEb9bHoAAAAAINABAAAgQaADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAA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" alt="AndMetaX Doginal Dog #4238" width="154" height="154"/>
            <div class="av-scan"></div>
          </div>
          <div class="av-glow"></div>
          <div class="x-badge">✦ @ANDMETAX ON X ✦</div>
        </a>
      </div>
      <div class="ptag">⚡ DOGINAL DOG #4238 ⚡</div>
    </div>

    <!-- BODY -->
    <div class="cb">
      <div class="nd"><h1>AndMetaX</h1></div>

      <div class="stats">
        <div class="sb"><span class="slb">ART POWER</span><div class="sf" style="width:92%;background:linear-gradient(90deg,var(--ng),var(--nc));box-shadow:0 0 6px var(--ng)"></div></div>
        <div class="sb"><span class="slb">NFT LEVEL</span><div class="sf" style="width:87%;background:linear-gradient(90deg,var(--np),var(--nc));box-shadow:0 0 6px var(--np)"></div></div>
        <div class="sb"><span class="slb">DOGINAL RANK</span><div class="sf" style="width:99%;background:linear-gradient(90deg,var(--ny),var(--no));box-shadow:0 0 6px var(--ny)"></div></div>
        <div class="sb"><span class="slb">XRP POWER</span><div class="sf" style="width:78%;background:linear-gradient(90deg,var(--nc),var(--np));box-shadow:0 0 6px var(--nc)"></div></div>
      </div>

      <div class="bp">
        <p>Welcome to <strong>And's Universe</strong> — a creative corner built by a proud member of the <em>Doginal Dogs community</em>, one of the most vibrant NFT communities on the Dogecoin blockchain. 🐾<br><br>
        I create <strong>custom digital art</strong> — reach me on X to commission something uniquely yours. My personal NFT collections, including <strong>'The Spark of Doginal War'</strong> and <strong>'Doginal Dog Pops'</strong> on XRP Cafe, exist entirely to <em>support the Doginal Dogs community</em> — funding new ideas, powering giveaways, and helping more people discover and own Doginal Dog NFTs.<br><br>
        Every piece, every drop, every game is a love letter back to the community that sparked all of this. 🦴</p>
        <span class="secret">🔍 secret.log: 3 hidden portals exist on this page...can you find them all?</span>
      </div>

      <div class="sl2">MISSION SELECT</div>
      <div class="lks">

        <a class="lk" href="https://xrp.cafe/collection/thesparkofdoginalwar" target="_blank" rel="noopener">
          <img class="lth" src="https://media.bio.site/sites/0221a58b-2d03-426a-80d6-ad3f952991af/oJ5oDAYNLmDh8HpCzrozUn.jpg" alt="The Spark Of Doginal War"/>
          <div class="li"><span class="ln">The Spark Of Doginal War</span><span class="lm">NFT COLLECTION · XRP CAFE</span></div>
          <div class="la">→</div>
        </a>

        <a class="lk pink" href="https://xrp.cafe/collection/doginaldogpops" target="_blank" rel="noopener">
          <img class="lth" src="https://media.bio.site/sites/0221a58b-2d03-426a-80d6-ad3f952991af/KmdGboADojimzc7nC4r4Z8.jpg" alt="Doginal Dog Pops"/>
          <div class="li"><span class="ln">Doginal Dog Pops</span><span class="lm">NFT COLLECTION · XRP CAFE</span></div>
          <div class="la">→</div>
        </a>

        <a class="lk cyan" href="https://cryptospaces.net/" target="_blank" rel="noopener">
          <canvas class="lth-c" id="csThumb" width="68" height="68"></canvas>
          <div class="li"><span class="ln">24/7 Crypto Spaces</span><span class="lm">LIVE CRYPTO COMMUNITY</span></div>
          <div class="la">→</div>
        </a>

        <a class="lk yellow" id="doggerBtn" href="dogger.html" target="_blank" rel="noopener">
          <canvas class="lth-c" id="dgThumb" width="68" height="68"></canvas>
          <div class="li"><span class="ln">DOGGER GAME 🐾</span><span class="lm">PLAY FREE · EARN YOUR RANK</span></div>
          <div class="la">→</div>
        </a>

      </div>
    </div>

    <!-- FOOTER — continued = easter egg 3 -->
    <div class="cf">
      <span class="ft">© ANDMETAX STUDIOS</span>
      <button class="cont-btn" id="contBtn">CONTINUED →</button>
    </div>

  </div>
</main>

<script>
// ── CURSOR ZAP (comic style) ──
const ZAPWORDS=['POW!','ZAP!','BOOM!','BAM!','WHAM!','KAPOW!','BLAM!','KO!!','NICE!','🐾'];
const ZAPCOLS=['#00ff88','#00ffff','#ff00ff','#ffff00','#ff6600','#ff2244'];
document.addEventListener('click',e=>{
  if(e.target.closest('a')||e.target.closest('button')) return;
  const z=document.createElement('div');
  z.className='zap';
  z.textContent=ZAPWORDS[Math.floor(Math.random()*ZAPWORDS.length)];
  z.style.cssText=`left:${e.clientX}px;top:${e.clientY}px;color:${ZAPCOLS[Math.floor(Math.random()*ZAPCOLS.length)]};text-shadow:0 0 20px currentColor`;
  document.body.appendChild(z);
  setTimeout(()=>z.remove(),800);
});

// ── BG CANVAS — comic speed lines + halftone particles ──
const bgC=document.getElementById('bgCanvas');
const bgX=bgC.getContext('2d');
function resizeBg(){bgC.width=innerWidth;bgC.height=innerHeight}
resizeBg();window.addEventListener('resize',resizeBg);
let bgT=0;
const NCOLS=['#00ff88','#00ffff','#ff00ff','#ffff00','#ff6600'];

// Comic panels BG
const bgl=document.getElementById('bgl');
const WORDS=['POW!','ZAP!','BOOM!','BAM!','WHAM!','KAPOW!','BLAM!','CRACK!','KO!!','SMASH!','ZZZAP!'];
function spawnBg(){
  const isWord=Math.random()>.45;
  const el=document.createElement('div');
  const c=NCOLS[Math.floor(Math.random()*NCOLS.length)];
  const dur=13+Math.random()*17,delay=Math.random()*3;
  if(isWord){
    el.className='fw';
    el.textContent=WORDS[Math.floor(Math.random()*WORDS.length)];
    el.style.cssText=`left:${Math.random()*92}vw;font-size:${26+Math.random()*72}px;-webkit-text-stroke:2px ${c}22;text-shadow:0 0 12px ${c}15;--r0:${Math.random()*30-15}deg;--r1:${Math.random()*30-15}deg;animation-duration:${dur}s;animation-delay:${delay}s`;
  } else {
    el.className='fp';
    el.style.cssText=`left:${Math.random()*90}vw;width:${55+Math.random()*155}px;height:${45+Math.random()*135}px;border-color:${c}1e;background:radial-gradient(circle at 30% 30%,${c}09,transparent);box-shadow:0 0 10px ${c}11;--r0:${Math.random()*18-9}deg;--r1:${Math.random()*18-9}deg;animation-duration:${dur}s;animation-delay:${delay}s`;
  }
  bgl.appendChild(el);
  setTimeout(()=>el.remove(),(dur+delay+2)*1000);
}
setInterval(spawnBg,650);
for(let i=0;i<18;i++) setTimeout(spawnBg,i*120);

// Canvas: speed line bursts + energy particles
function drawBgCanvas(){
  bgX.clearRect(0,0,bgC.width,bgC.height);
  // Speed line bursts from corners
  const bursts=[
    {x:bgC.width*.12,y:bgC.height*.18,a:.06},
    {x:bgC.width*.88,y:bgC.height*.72,a:.05},
    {x:bgC.width*.5,y:bgC.height*.92,a:.04}
  ];
  bursts.forEach(({x,y,a})=>{
    for(let i=0;i<28;i++){
      const ang=(i/28)*Math.PI*2+bgT*.18;
      const r1=55+Math.sin(bgT*2+i)*10;
      const r2=220+Math.sin(bgT+i*.5)*35;
      bgX.beginPath();bgX.moveTo(x+Math.cos(ang)*r1,y+Math.sin(ang)*r1);bgX.lineTo(x+Math.cos(ang)*r2,y+Math.sin(ang)*r2);
      bgX.strokeStyle=`hsla(${(i/28)*60+40},100%,60%,${a})`;bgX.lineWidth=1.5;bgX.stroke();
    }
  });
  // Perspective grid floor
  const vx=bgC.width/2,vy=bgC.height*.58;
  for(let i=0;i<=12;i++){
    const x=(i/12)*bgC.width;
    bgX.beginPath();bgX.moveTo(x,bgC.height);bgX.lineTo(vx,vy);
    bgX.strokeStyle=`rgba(0,255,136,${.04+Math.sin(bgT+i*.5)*.015})`;bgX.lineWidth=1;bgX.stroke();
  }
  for(let j=1;j<=8;j++){
    const f=j/8,y=vy+(bgC.height-vy)*f,xl=vx-vx*f,xr=vx+(bgC.width-vx)*f;
    bgX.beginPath();bgX.moveTo(xl,y);bgX.lineTo(xr,y);
    bgX.strokeStyle=`rgba(0,255,136,${.025+f*.05+Math.sin(bgT*2+j)*.012})`;bgX.lineWidth=1;bgX.stroke();
  }
  // Expanding rings from top center
  for(let r=0;r<4;r++){
    const rad=((bgT*70+r*110)%500);
    const a=Math.max(0,.15-rad/500*.15);
    bgX.beginPath();bgX.arc(bgC.width/2,0,rad,0,Math.PI*2);
    bgX.strokeStyle=`rgba(0,255,136,${a})`;bgX.lineWidth=1.5;bgX.stroke();
  }
  // Floating energy particles
  for(let i=0;i<30;i++){
    const px=(Math.sin(bgT*.2+i*2.3)*.5+.5)*bgC.width;
    const py=(Math.cos(bgT*.15+i*1.7)*.5+.5)*bgC.height;
    const c=NCOLS[i%NCOLS.length];
    bgX.beginPath();bgX.arc(px,py,.7+Math.sin(bgT+i)*.5,0,Math.PI*2);
    bgX.shadowBlur=8;bgX.shadowColor=c;bgX.fillStyle=c;bgX.fill();bgX.shadowBlur=0;
  }
  bgT+=.011;
  requestAnimationFrame(drawBgCanvas);
}
drawBgCanvas();

// ── LINK THUMBNAILS ──

// ══ CRYPTO SPACES — glowing satellite dish + live signal rings ══
(function(){
  const c=document.getElementById('csThumb'),x=c.getContext('2d');
  // deep space bg with star field
  const bg=x.createRadialGradient(34,34,2,34,34,48);
  bg.addColorStop(0,'#001830');bg.addColorStop(1,'#000510');
  x.fillStyle=bg;x.fillRect(0,0,68,68);
  // stars
  const stars=[[8,6],[15,18],[4,30],[60,8],[55,20],[62,35],[10,55],[58,58],[30,5],[45,60],[20,45],[50,40]];
  stars.forEach(([sx,sy])=>{
    x.beginPath();x.arc(sx,sy,Math.random()<0.5?0.8:1.2,0,Math.PI*2);
    x.fillStyle=`rgba(255,255,255,${0.4+Math.random()*0.5})`;x.fill();
  });
  // LIVE badge top-left
  x.fillStyle='#ff2244';x.fillRect(3,3,22,9);
  x.fillStyle='#fff';x.font='bold 5.5px Arial';x.textAlign='left';x.fillText('● LIVE',5,10);
  // satellite dish base
  x.strokeStyle='#00ffff';x.lineWidth=1.5;x.shadowBlur=0;
  x.fillStyle='rgba(0,255,255,.08)';
  // dish bowl — arc
  x.beginPath();x.arc(34,46,16,Math.PI*1.1,Math.PI*2,false);x.closePath();
  x.fill();
  x.strokeStyle='#00ffff';x.shadowBlur=8;x.shadowColor='#00ffff';x.stroke();
  // dish arm / pole
  x.beginPath();x.moveTo(34,46);x.lineTo(34,58);x.lineWidth=2;x.stroke();
  x.beginPath();x.moveTo(26,58);x.lineTo(42,58);x.stroke();
  // dish receiver dot at focus
  x.beginPath();x.arc(34,36,3,0,Math.PI*2);
  x.fillStyle='#00ffff';x.shadowBlur=12;x.shadowColor='#00ffff';x.fill();
  // feed arm
  x.beginPath();x.moveTo(34,36);x.lineTo(26,44);x.lineWidth=1.5;x.stroke();
  x.shadowBlur=0;
  // signal rings emanating from receiver
  const ringColors=['#00ffff','#00ffff','rgba(0,255,255,.5)','rgba(0,255,255,.25)'];
  [6,12,18,24].forEach((r,i)=>{
    x.beginPath();x.arc(34,36,r,Math.PI*1.25,Math.PI*1.75,false);
    x.strokeStyle=ringColors[i];x.lineWidth=1.2;
    x.shadowBlur=i<2?8:4;x.shadowColor='#00ffff';x.stroke();
  });
  x.shadowBlur=0;
  // "24/7" label
  x.textAlign='center';
  x.font='bold 9px Orbitron,monospace';x.fillStyle='#00ffff';
  x.shadowBlur=6;x.shadowColor='#00ffff';
  x.fillText('24/7',34,28);x.shadowBlur=0;
})();

// ══ DOGGER GAME — pixel art scene: dog crossing neon road ══
(function(){
  const c=document.getElementById('dgThumb'),x=c.getContext('2d');
  // dark asphalt bg
  x.fillStyle='#060608';x.fillRect(0,0,68,68);

  // === ROAD LANES (3 lanes) ===
  const laneH=11;
  const lanes=[{y:6,col:'#0a0a12'},{y:28,col:'#0c0a08'},{y:50,col:'#0a0a12'}];
  lanes.forEach(l=>{x.fillStyle=l.col;x.fillRect(0,l.y,68,laneH);});

  // lane dividers — neon dashes
  [[17,'#ffff00'],[39,'#ff6600']].forEach(([dy,dc])=>{
    x.setLineDash([5,4]);x.strokeStyle=dc+'66';x.lineWidth=1;
    x.beginPath();x.moveTo(0,dy);x.lineTo(68,dy);x.stroke();
  });
  x.setLineDash([]);

  // safe zones — green glow strips
  x.fillStyle='rgba(0,255,136,.06)';x.fillRect(0,0,68,6);
  x.fillStyle='rgba(0,255,136,.06)';x.fillRect(0,39,68,11);
  x.fillStyle='rgba(0,255,136,.1)';x.fillRect(0,61,68,7);

  // === CAR 1 — cyan sports car lane 1 ===
  const car1x=6;
  x.fillStyle='#001a2a';x.fillRect(car1x,8,20,7);
  // body gradient
  const cg1=x.createLinearGradient(car1x,8,car1x,15);
  cg1.addColorStop(0,'rgba(0,255,255,.3)');cg1.addColorStop(1,'rgba(0,255,255,.08)');
  x.fillStyle=cg1;x.fillRect(car1x,8,20,7);
  x.strokeStyle='#00ffff';x.lineWidth=1;x.shadowBlur=6;x.shadowColor='#00ffff';
  x.strokeRect(car1x,8,20,7);
  // headlights
  x.fillStyle='#ffffaa';x.shadowColor='#ffff88';x.shadowBlur=5;
  x.fillRect(car1x+17,9,2,2);x.fillRect(car1x+17,12,2,2);
  x.shadowBlur=0;

  // === CAR 2 — pink enemy car lane 2, going other way ===
  const car2x=42;
  x.fillStyle='#1a0008';x.fillRect(car2x,30,20,7);
  const cg2=x.createLinearGradient(car2x,30,car2x,37);
  cg2.addColorStop(0,'rgba(255,0,255,.3)');cg2.addColorStop(1,'rgba(255,0,255,.08)');
  x.fillStyle=cg2;x.fillRect(car2x,30,20,7);
  x.strokeStyle='#ff00ff';x.lineWidth=1;x.shadowBlur=6;x.shadowColor='#ff00ff';
  x.strokeRect(car2x,30,20,7);
  // tail lights going left
  x.fillStyle='#ff2244';x.shadowColor='#ff2244';x.shadowBlur=5;
  x.fillRect(car2x+1,31,2,2);x.fillRect(car2x+1,34,2,2);
  x.shadowBlur=0;

  // === GOLD COIN — lane 3 ===
  x.beginPath();x.arc(50,55,5,0,Math.PI*2);
  x.fillStyle='#ffd700';x.shadowBlur=10;x.shadowColor='#ffdd00';x.fill();
  x.strokeStyle='#fff8a0';x.lineWidth=1;x.stroke();
  x.fillStyle='#8a5800';x.font='bold 5px Arial';x.textAlign='center';x.shadowBlur=0;
  x.fillText('₿',50,57);

  // === PIXEL DOG — center of road, mid-cross ===
  // body (brown squares — pixel art style)
  const dog=[
    [28,40,'#5c3317'],[32,40,'#5c3317'],[36,40,'#5c3317'],
    [26,44,'#000'],[28,44,'#5c3317'],[32,44,'#5c3317'],[36,44,'#5c3317'],[38,44,'#000'],
    [28,48,'#5c3317'],[32,48,'#5c3317'],[36,48,'#5c3317'],
    // ears
    [26,38,'#3d2010'],[38,38,'#3d2010'],
    // eyes
    [30,42,'#00ff44'],[34,42,'#00ff44'],
    // chain
    [28,50,'#ccc'],[32,50,'#aaa'],[36,50,'#ccc'],
  ];
  dog.forEach(([dx,dy,dc])=>{
    x.fillStyle=dc;x.fillRect(dx,dy,4,4);
  });
  // dog glow
  x.shadowBlur=8;x.shadowColor='#00ff88';
  x.strokeStyle='rgba(0,255,136,.3)';x.lineWidth=1;
  x.strokeRect(25,37,18,18);x.shadowBlur=0;

  // === TITLE ===
  x.textAlign='center';
  x.font='bold 7.5px Orbitron,monospace';
  x.fillStyle='#00ff88';x.shadowBlur=7;x.shadowColor='#00ff88';
  x.fillText('DOGGER',34,68);x.shadowBlur=0;
})();

// ── PORTAL ANIMATION ──
const portalOverlay=document.getElementById('portalOverlay');
const portalCanvas=document.getElementById('portalCanvas');
const pCtx=portalCanvas.getContext('2d');
let portalActive=false,portalRaf=null;

document.getElementById('contBtn').addEventListener('click',function(){
  if(portalActive) return;
  portalActive=true;
  portalCanvas.width=innerWidth;portalCanvas.height=innerHeight;
  portalOverlay.classList.add('active');
  const msg=document.getElementById('portalMsg');
  msg.style.opacity='0';
  let start=null;

  function animatePortal(ts){
    if(!start) start=ts;
    const el=(ts-start)/1000;
    const cw=portalCanvas.width,ch=portalCanvas.height;
    const cx=cw/2,cy=ch/2;

    // Black bg
    pCtx.fillStyle=`rgba(0,0,8,${Math.min(el/.35,.97)})`;
    pCtx.fillRect(0,0,cw,ch);

    // 18 pulsing portal rings
    for(let r=0;r<18;r++){
      const phase=(el*2.8+r/18)*Math.PI*2;
      const radius=15+r*28+Math.sin(phase)*14;
      const hue=(r/18)*360+el*90;
      const alpha=Math.min(el/.25,1)*(0.25+0.38*Math.sin(phase));
      pCtx.beginPath();pCtx.arc(cx,cy,radius,0,Math.PI*2);
      pCtx.strokeStyle=`hsla(${hue},100%,65%,${alpha})`;
      pCtx.lineWidth=1.8+Math.sin(phase)*1.5;
      pCtx.shadowBlur=20;pCtx.shadowColor=`hsla(${hue},100%,65%,.9)`;
      pCtx.stroke();pCtx.shadowBlur=0;
    }

    // 140-star tunnel
    for(let s=0;s<140;s++){
      const angle=(s/140)*Math.PI*2+(el*.25);
      const depth=(s*6+el*280)%750;
      const persp=280/(depth+1);
      const sx=cx+Math.cos(angle)*depth*persp*.013;
      const sy=cy+Math.sin(angle)*depth*persp*.013;
      const sz=Math.max(0,1-depth/750)*2.8;
      const alpha=Math.max(0,1-depth/750)*Math.min(el/.4,1);
      pCtx.beginPath();pCtx.arc(sx,sy,sz,0,Math.PI*2);
      pCtx.fillStyle=`hsla(${(s*2.5+el*100)%360},100%,80%,${alpha})`;pCtx.fill();
    }

    // 10 swirling color streams
    const streamColors=['#00ff88','#00ffff','#ff00ff','#ffff00','#ff6600','#ff2244','#8800ff','#00aaff','#ffaa00','#00ff44'];
    for(let i=0;i<10;i++){
      const a=el*4.5+i*(Math.PI/5);
      const r1=40+el*110,r2=r1+90+Math.sin(el*3+i)*35;
      pCtx.beginPath();
      pCtx.moveTo(cx+Math.cos(a)*r1,cy+Math.sin(a)*r1);
      pCtx.quadraticCurveTo(cx+Math.cos(a+.45)*(r1+r2)/2,cy+Math.sin(a+.45)*(r1+r2)/2,cx+Math.cos(a+.35)*r2,cy+Math.sin(a+.35)*r2);
      pCtx.strokeStyle=streamColors[i]+'aa';pCtx.lineWidth=2.5+Math.sin(el*2+i);
      pCtx.shadowBlur=12;pCtx.shadowColor=streamColors[i];pCtx.stroke();pCtx.shadowBlur=0;
    }

    // Screen shake at 2.4s
    if(el>2.4){
      const shk=Math.min((el-2.4)*14,12);
      portalCanvas.style.transform=`translate(${(Math.random()-.5)*shk}px,${(Math.random()-.5)*shk}px)`;
    }

    // Show text at 0.7s
    if(el>0.7) msg.style.opacity=Math.min((el-.7)/.4,1).toString();

    // Cyan flash at 3s
    if(el>3.0){
      const fa=Math.min((el-3.0)/.45,1);
      pCtx.fillStyle=`rgba(0,255,255,${fa})`;
      pCtx.fillRect(0,0,cw,ch);
    }

    // Open tab + reset at 3.6s
    if(el>3.6){
      cancelAnimationFrame(portalRaf);
      window.open('https://doginaldogs.com/','_blank');
      setTimeout(()=>{
        portalCanvas.style.transform='';
        portalOverlay.classList.remove('active');
        msg.style.opacity='0';
        pCtx.clearRect(0,0,portalCanvas.width,portalCanvas.height);
        portalActive=false;
      },300);
      return;
    }
    portalRaf=requestAnimationFrame(animatePortal);
  }
  portalRaf=requestAnimationFrame(animatePortal);
});

// ── MUSIC ENGINE ──
let audioCtx=null,musicOn=false,musicNodes=[];
function initAudio(){if(!audioCtx) audioCtx=new(window.AudioContext||window.webkitAudioContext)()}
function toggleMusic(){
  initAudio();
  if(musicOn) stopMusic(); else startMusic();
}
function stopMusic(){
  musicNodes.forEach(n=>{try{n.stop()}catch(e){}});
  musicNodes=[];musicOn=false;
  const btn=document.getElementById('musicBtn');
  btn.textContent='▶';btn.classList.add('off');
}
function startMusic(){
  if(!audioCtx) return;
  musicOn=true;
  const btn=document.getElementById('musicBtn');
  btn.textContent='⏸';btn.classList.remove('off');

  const master=audioCtx.createGain();master.gain.value=.17;master.connect(audioCtx.destination);
  // Reverb
  const rev=audioCtx.createConvolver();
  const rb=audioCtx.createBuffer(2,audioCtx.sampleRate*2,audioCtx.sampleRate);
  for(let ch=0;ch<2;ch++){const d=rb.getChannelData(ch);for(let i=0;i<d.length;i++)d[i]=(Math.random()*2-1)*Math.pow(1-i/d.length,2.2)}
  rev.buffer=rb;const rg=audioCtx.createGain();rg.gain.value=.22;rev.connect(rg);rg.connect(master);

  const BPM=126,beat=60/BPM;
  const now=audioCtx.currentTime+.1;

  // Melody (sawtooth)
  const mel=[[261.63,0],[329.63,beat],[392,beat*2],[523.25,beat*3],[440,beat*4],[392,beat*5],[329.63,beat*6],[261.63,beat*7],[293.66,beat*8],[349.23,beat*9],[440,beat*10],[587.33,beat*11],[523.25,beat*12],[440,beat*13],[392,beat*14],[349.23,beat*15]];
  // Bass
  const bass=[[65.41,0],[65.41,beat*2],[87.31,beat*4],[87.31,beat*6],[73.42,beat*8],[73.42,beat*10],[97.99,beat*12],[97.99,beat*14]];
  // Arp
  const arp=[523.25,659.25,783.99,1046.5,783.99,659.25];

  for(let loop=0;loop<8;loop++){
    const ls=now+loop*beat*16;
    // Melody
    mel.forEach(([freq,off])=>{
      const o=audioCtx.createOscillator(),g=audioCtx.createGain(),f=audioCtx.createBiquadFilter();
      f.type='lowpass';f.frequency.value=2100;o.type='sawtooth';o.frequency.value=freq;
      const ts=ls+off;g.gain.setValueAtTime(0,ts);g.gain.linearRampToValueAtTime(.3,ts+.02);g.gain.exponentialRampToValueAtTime(.01,ts+beat*.85);
      o.connect(f);f.connect(g);g.connect(master);g.connect(rev);o.start(ts);o.stop(ts+beat);musicNodes.push(o);
    });
    // Bass
    bass.forEach(([freq,off])=>{
      const o=audioCtx.createOscillator(),g=audioCtx.createGain();
      o.type='square';o.frequency.value=freq;const ts=ls+off;
      g.gain.setValueAtTime(0,ts);g.gain.linearRampToValueAtTime(.26,ts+.01);g.gain.exponentialRampToValueAtTime(.01,ts+beat*1.8);
      o.connect(g);g.connect(master);o.start(ts);o.stop(ts+beat*2);musicNodes.push(o);
    });
    // Drums
    for(let b=0;b<16;b++){
      const bt=ls+b*beat;
      // Kick
      if(b%4===0){const o=audioCtx.createOscillator(),g=audioCtx.createGain();o.frequency.setValueAtTime(150,bt);o.frequency.exponentialRampToValueAtTime(.001,bt+.25);g.gain.setValueAtTime(.85,bt);g.gain.exponentialRampToValueAtTime(.001,bt+.25);o.connect(g);g.connect(master);o.start(bt);o.stop(bt+.25);musicNodes.push(o);}
      // Snare
      if(b%4===2){const buf=audioCtx.createBuffer(1,audioCtx.sampleRate*.1,audioCtx.sampleRate);const d=buf.getChannelData(0);for(let i=0;i<d.length;i++)d[i]=Math.random()*2-1;const src=audioCtx.createBufferSource(),g=audioCtx.createGain(),f=audioCtx.createBiquadFilter();f.type='bandpass';f.frequency.value=1200;g.gain.setValueAtTime(.42,bt);g.gain.exponentialRampToValueAtTime(.001,bt+.12);src.buffer=buf;src.connect(f);f.connect(g);g.connect(master);src.start(bt);musicNodes.push(src);}
      // Hihat
      const hbt=b%2===1?bt+beat*.5:bt;const hbuf=audioCtx.createBuffer(1,audioCtx.sampleRate*.04,audioCtx.sampleRate);const hd=hbuf.getChannelData(0);for(let i=0;i<hd.length;i++)hd[i]=Math.random()*2-1;const hs=audioCtx.createBufferSource(),hg=audioCtx.createGain(),hf=audioCtx.createBiquadFilter();hf.type='highpass';hf.frequency.value=8000;hg.gain.setValueAtTime(.11,hbt);hg.gain.exponentialRampToValueAtTime(.001,hbt+.04);hs.buffer=hbuf;hs.connect(hf);hf.connect(hg);hg.connect(master);hs.start(hbt);musicNodes.push(hs);
    }
    // Arp (every other loop)
    if(loop%2===0){
      for(let rep=0;rep<8;rep++){
        arp.forEach((freq,i)=>{
          const o=audioCtx.createOscillator(),g=audioCtx.createGain();
          o.type='triangle';o.frequency.value=freq;
          const ts=ls+rep*(beat*2)+i*(beat/3);
          g.gain.setValueAtTime(0,ts);g.gain.linearRampToValueAtTime(.09,ts+.01);g.gain.exponentialRampToValueAtTime(.001,ts+beat/3*.9);
          o.connect(g);g.connect(master);g.connect(rev);o.start(ts);o.stop(ts+beat/3);musicNodes.push(o);
        });
      }
    }
  }
  // Loop
  setTimeout(()=>{if(musicOn){stopMusic();startMusic();}},beat*16*8*1000+250);
}
// Auto-start on first interaction
document.addEventListener('click',()=>{if(!musicOn&&!audioCtx){initAudio();startMusic();}},{once:true});
</script>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
<title>DOGGER — AndMetaX</title>
<link href="https://fonts.googleapis.com/css2?family=Bangers&family=Orbitron:wght@700;900&family=Black+Ops+One&display=swap" rel="stylesheet">
<style>
:root{
  --ng:#00ff88;--nc:#00ffff;--np:#ff00ff;--ny:#ffff00;--no:#ff6600;--nr:#ff2244;
  --void:#000008;
  --gg:0 0 8px #00ff88,0 0 20px #00ff88;
  --gc:0 0 8px #00ffff,0 0 20px #00ffff;
  --gp:0 0 8px #ff00ff,0 0 20px #ff00ff;
  --gy:0 0 8px #ffff00,0 0 20px #ffff00;
}
*{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent;user-select:none}
body{background:var(--void);font-family:'Orbitron',monospace;color:#fff;height:100vh;width:100vw;overflow:hidden;display:flex;flex-direction:column;align-items:center;justify-content:center}

/* SCREENS */
.screen{position:fixed;inset:0;display:flex;flex-direction:column;align-items:center;justify-content:center;padding:16px;z-index:10;background:var(--void);overflow-y:auto}
.screen.hidden{display:none!important}

/* BG CANVAS */
#bgCanvas{position:fixed;inset:0;z-index:0;width:100%;height:100%;pointer-events:none}
.scl{position:fixed;inset:0;z-index:1;background:repeating-linear-gradient(0deg,transparent,transparent 3px,rgba(0,255,136,.012) 3px,rgba(0,255,136,.012) 4px);pointer-events:none}

/* TITLE SCREEN */
.game-logo{font-family:'Bangers',cursive;font-size:clamp(60px,18vw,110px);letter-spacing:10px;color:var(--ng);text-shadow:var(--gg),0 0 60px #00ff88,6px 6px 0 #003320;line-height:1;animation:logoPulse 2s ease-in-out infinite;text-align:center}
@keyframes logoPulse{0%,100%{text-shadow:var(--gg),0 0 60px #00ff88,6px 6px 0 #003320}50%{text-shadow:0 0 20px #00ff88,0 0 80px #00ff88,0 0 140px #00ff88,6px 6px 0 #003320}}
.game-sub{font-family:'Black Ops One',cursive;font-size:10px;letter-spacing:5px;color:var(--nc);text-shadow:var(--gc);margin-bottom:4px;animation:flk 4s infinite}
@keyframes flk{0%,18%,20%,100%{opacity:1}19%{opacity:.3}}
.doginal-tag{font-family:'Black Ops One',cursive;font-size:10px;letter-spacing:3px;color:var(--np);text-shadow:var(--gp);margin-bottom:20px}

/* PREVIEW AVATAR */
#previewWrap{position:relative;width:100px;height:100px;margin:0 auto 18px;cursor:pointer}
#previewCanvas{display:block;width:100px;height:100px;border:2px solid var(--ng);box-shadow:0 0 20px var(--ng),0 0 60px rgba(0,255,136,.3);image-rendering:pixelated}
.preview-overlay{position:absolute;inset:0;background:rgba(0,255,136,.0);display:flex;align-items:center;justify-content:center;transition:.2s;font-family:'Black Ops One',cursive;font-size:8px;letter-spacing:1px;color:rgba(0,255,136,.0);text-align:center;border:2px solid transparent}
#previewWrap:hover .preview-overlay{background:rgba(0,0,8,.7);color:var(--ng);border-color:var(--ng)}

/* SETUP PANEL */
.setup-panel{background:rgba(0,255,136,.04);border:1px solid rgba(0,255,136,.25);padding:14px 18px;width:100%;max-width:340px;margin-bottom:14px;position:relative}
.setup-panel::before{content:'// PLAYER SETUP';position:absolute;top:-9px;left:10px;background:var(--void);color:var(--nc);font-size:8px;letter-spacing:2px;padding:0 6px;text-shadow:var(--gc)}
.s-row{display:flex;gap:8px;margin-bottom:9px;align-items:center}
.s-row:last-child{margin-bottom:0}
.s-lbl{font-size:8px;letter-spacing:2px;color:rgba(0,255,136,.55);white-space:nowrap;flex-shrink:0;min-width:44px}
.s-inp{background:rgba(0,0,0,.6);border:1px solid rgba(0,255,136,.35);color:var(--ng);font-family:'Orbitron',monospace;font-size:12px;padding:6px 9px;flex:1;min-width:0;outline:none}
.s-inp:focus{border-color:var(--ng);box-shadow:0 0 8px rgba(0,255,136,.3)}
.upload-btn{background:rgba(0,255,136,.08);border:1px solid var(--ng);color:var(--ng);font-family:'Black Ops One',cursive;font-size:8px;letter-spacing:1px;padding:7px 12px;cursor:pointer;transition:.2s;white-space:nowrap}
.upload-btn:hover{background:rgba(0,255,136,.22);box-shadow:var(--gg)}
#pfpInput{display:none}

/* VISION CHECK */
#visionStatus{font-family:'Black Ops One',cursive;font-size:9px;letter-spacing:2px;padding:6px 12px;margin-top:6px;text-align:center;border:1px solid;display:none;width:100%;max-width:340px}
#visionStatus.checking{color:var(--ny);border-color:var(--ny);display:block;animation:flk .8s infinite}
#visionStatus.ok{color:var(--ng);border-color:var(--ng);display:block}
#visionStatus.bad{color:var(--nr);border-color:var(--nr);display:block}

/* BUTTONS */
.btn{font-family:'Bangers',cursive;font-size:22px;letter-spacing:4px;padding:11px 30px;border:2px solid;cursor:pointer;transition:all .15s;display:block;width:100%;max-width:300px;text-align:center;text-decoration:none;margin:5px auto}
.btn-green{color:var(--ng);border-color:var(--ng);background:rgba(0,255,136,.07);box-shadow:0 0 12px rgba(0,255,136,.18)}
.btn-green:hover,.btn-green:active{background:rgba(0,255,136,.2);box-shadow:0 0 28px rgba(0,255,136,.4);transform:translateY(-2px)}
.btn-green:disabled{opacity:.35;cursor:not-allowed;transform:none}
.btn-cyan{color:var(--nc);border-color:var(--nc);background:rgba(0,255,255,.07)}
.btn-cyan:hover,.btn-cyan:active{background:rgba(0,255,255,.2);box-shadow:0 0 28px rgba(0,255,255,.4)}
.btn-pink{color:var(--np);border-color:var(--np);background:rgba(255,0,255,.07)}
.btn-pink:hover,.btn-pink:active{background:rgba(255,0,255,.2);box-shadow:0 0 28px rgba(255,0,255,.4)}
.btn-yellow{color:var(--ny);border-color:var(--ny);background:rgba(255,255,0,.07)}
.btn-yellow:hover,.btn-yellow:active{background:rgba(255,255,0,.2);box-shadow:0 0 28px rgba(255,255,0,.4)}
.btn-sm{font-size:14px;padding:8px 18px;letter-spacing:2px}

/* GAME SCREEN */
#gameScreen{padding:0;background:var(--void);justify-content:flex-start}
#hud{width:100%;max-width:420px;display:flex;justify-content:space-between;align-items:center;padding:5px 10px;background:rgba(0,0,0,.85);border-bottom:1px solid rgba(0,255,136,.18);flex-shrink:0;z-index:20}
.hud-item{text-align:center}
.hud-lbl{font-size:6px;letter-spacing:2px;color:rgba(0,255,136,.45);display:block}
.hud-val{font-family:'Bangers',cursive;font-size:19px;letter-spacing:2px;color:var(--ng);text-shadow:var(--gg)}
.hud-val.yel{color:var(--ny);text-shadow:var(--gy)}
.hud-val.red{color:var(--nr);text-shadow:0 0 8px var(--nr)}
#gameCanvas{display:block;max-width:420px;width:100%;flex:1;image-rendering:pixelated;z-index:10}

/* DPAD */
#dpad{width:100%;max-width:420px;background:rgba(0,0,0,.92);border-top:1px solid rgba(0,255,136,.12);padding:8px 0 6px;flex-shrink:0;z-index:20}
.dpad-inner{display:grid;grid-template-columns:repeat(3,54px);grid-template-rows:repeat(3,46px);gap:3px;margin:0 auto;width:fit-content}
.dp{background:rgba(0,255,136,.07);border:2px solid rgba(0,255,136,.25);color:var(--ng);font-size:22px;display:flex;align-items:center;justify-content:center;cursor:pointer;border-radius:7px}
.dp:active,.dp.on{background:rgba(0,255,136,.3);border-color:var(--ng);box-shadow:var(--gg);transform:scale(.93)}
.dp-blank{background:transparent;border:none;pointer-events:none}

/* LEVEL BANNER */
#lvlBanner{position:fixed;top:50%;left:50%;transform:translate(-50%,-50%) scale(0);z-index:200;font-family:'Bangers',cursive;font-size:52px;letter-spacing:6px;color:var(--ny);text-shadow:var(--gy),0 0 60px #ffff00;text-align:center;pointer-events:none;transition:transform .2s}
#lvlBanner.show{transform:translate(-50%,-50%) scale(1)}

/* GAME OVER */
#goScreen .go-title{font-family:'Bangers',cursive;font-size:58px;letter-spacing:6px;color:var(--nr);text-shadow:0 0 20px var(--nr),0 0 60px var(--nr);animation:goPulse 1s ease-in-out infinite}
@keyframes goPulse{0%,100%{transform:scale(1)}50%{transform:scale(1.05)}}
.go-stats{background:rgba(0,255,136,.04);border:1px solid rgba(0,255,136,.18);padding:14px 22px;margin:12px 0;width:100%;max-width:320px}
.go-row{display:flex;justify-content:space-between;align-items:center;margin-bottom:7px}
.go-row:last-child{margin-bottom:0}
.go-lbl{font-size:8px;letter-spacing:3px;color:rgba(0,255,136,.55)}
.go-val{font-family:'Bangers',cursive;font-size:22px;color:var(--ny);text-shadow:var(--gy)}
.share-box{background:#000;border:2px solid var(--ny);padding:12px 14px;margin:8px 0;width:100%;max-width:320px;text-align:center}
.share-txt{font-family:'Black Ops One',cursive;font-size:10px;color:#fff;line-height:1.7;letter-spacing:.5px}
.sh-nc{color:var(--nc)}.sh-ng{color:var(--ng)}.sh-np{color:var(--np)}.sh-ny{color:var(--ny)}

/* LEADERBOARD */
#lbScreen .lb-title{font-family:'Bangers',cursive;font-size:44px;letter-spacing:6px;color:var(--ny);text-shadow:var(--gy);margin-bottom:4px}
.lb-list{width:100%;max-width:380px;margin:10px 0}
.lb-row{display:flex;align-items:center;gap:9px;padding:7px 11px;margin-bottom:5px;border:1px solid rgba(0,255,136,.14);background:rgba(0,255,136,.03)}
.lb-row.me{border-color:var(--ny);background:rgba(255,255,0,.05)}
.lb-rank{font-family:'Bangers',cursive;font-size:22px;width:30px;text-align:center;flex-shrink:0}
.lb-rank.g{color:#ffd700;text-shadow:0 0 10px #ffd700}
.lb-rank.s{color:#c0c0c0;text-shadow:0 0 10px #c0c0c0}
.lb-rank.b{color:#cd7f32;text-shadow:0 0 10px #cd7f32}
.lb-dog{width:32px;height:32px;border:2px solid var(--ng);flex-shrink:0;object-fit:contain;image-rendering:pixelated;background:#7dffb3}
.lb-info{flex:1;min-width:0}
.lb-name{font-family:'Black Ops One',cursive;font-size:11px;color:var(--ng);overflow:hidden;text-overflow:ellipsis;white-space:nowrap}
.lb-sub{font-size:8px;color:var(--nc);letter-spacing:1px}
.lb-pts{font-family:'Bangers',cursive;font-size:20px;color:var(--ny);text-shadow:var(--gy);flex-shrink:0}
</style>
</head>
<body>
<canvas id="bgCanvas"></canvas>
<div class="scl"></div>
<div id="lvlBanner">LEVEL UP!<br><span id="lvlNum" style="font-size:30px;color:var(--nc)"></span></div>

<!-- ══ TITLE ══ -->
<div class="screen" id="titleScreen">
  <div class="game-sub">◈ ANDMETAX PRESENTS ◈</div>
  <div class="game-logo">DOGGER</div>
  <div class="doginal-tag">⚡ DOGINAL DOG FROGGER ⚡</div>

  <div id="previewWrap" onclick="document.getElementById('pfpInput').click()">
    <canvas id="previewCanvas" width="100" height="100"></canvas>
    <div class="preview-overlay">📷 TAP TO<br>UPLOAD DOG</div>
  </div>
  <input type="file" id="pfpInput" accept="image/*"/>

  <div id="visionStatus"></div>

  <div class="setup-panel">
    <div class="s-row">
      <span class="s-lbl">DOG #</span>
      <input class="s-inp" id="nftNum" type="number" placeholder="e.g. 4238" min="1" max="9999"/>
    </div>
    <div class="s-row">
      <span class="s-lbl">NAME</span>
      <input class="s-inp" id="playerName" type="text" placeholder="Your handle" maxlength="16"/>
    </div>
    <div class="s-row">
      <span class="s-lbl">PFP</span>
      <button class="upload-btn" onclick="document.getElementById('pfpInput').click()">📷 UPLOAD YOUR DOGINAL DOG</button>
    </div>
  </div>

  <button class="btn btn-green" id="playBtn" onclick="startGame()">▶ PLAY NOW</button>
  <button class="btn btn-cyan btn-sm" onclick="showLB()">🏆 LEADERBOARD</button>
  <a class="btn btn-pink btn-sm" href="andmetax.html">🏠 BACK TO SITE</a>
</div>

<!-- ══ GAME ══ -->
<div class="screen hidden" id="gameScreen">
  <div id="hud">
    <div class="hud-item"><span class="hud-lbl">SCORE</span><span class="hud-val" id="hudScore">0</span></div>
    <div class="hud-item"><span class="hud-lbl">LEVEL</span><span class="hud-val yel" id="hudLevel">1</span></div>
    <div class="hud-item"><span class="hud-lbl">COINS</span><span class="hud-val yel" id="hudCoins">0</span></div>
    <div class="hud-item"><span class="hud-lbl">LIVES</span><span class="hud-val red" id="hudLives">🐾🐾🐾</span></div>
    <div class="hud-item"><span class="hud-lbl">BEST</span><span class="hud-val" id="hudBest">0</span></div>
  </div>
  <canvas id="gameCanvas"></canvas>
  <div id="dpad">
    <div class="dpad-inner">
      <div class="dp-blank"></div>
      <div class="dp" id="bU" ontouchstart="dpadOn('U',event)" ontouchend="dpadOff('U')">▲</div>
      <div class="dp-blank"></div>
      <div class="dp" id="bL" ontouchstart="dpadOn('L',event)" ontouchend="dpadOff('L')">◀</div>
      <div class="dp-blank"></div>
      <div class="dp" id="bR" ontouchstart="dpadOn('R',event)" ontouchend="dpadOff('R')">▶</div>
      <div class="dp-blank"></div>
      <div class="dp" id="bD" ontouchstart="dpadOn('D',event)" ontouchend="dpadOff('D')">▼</div>
      <div class="dp-blank"></div>
    </div>
  </div>
</div>

<!-- ══ GAME OVER ══ -->
<div class="screen hidden" id="goScreen">
  <div class="go-title">WOOF!</div>
  <div style="font-family:'Black Ops One',cursive;font-size:10px;letter-spacing:3px;color:rgba(255,34,68,.8);margin-bottom:6px">GAME OVER</div>
  <canvas id="goPfp" width="70" height="70" style="border:2px solid var(--ny);box-shadow:0 0 20px var(--ny);margin:6px auto;display:block;image-rendering:pixelated;background:#7dffb3;border-radius:4px"></canvas>
  <div class="go-stats">
    <div class="go-row"><span class="go-lbl">SCORE</span><span class="go-val" id="goScore">0</span></div>
    <div class="go-row"><span class="go-lbl">LEVEL</span><span class="go-val" id="goLevel">1</span></div>
    <div class="go-row"><span class="go-lbl">COINS</span><span class="go-val" id="goCoins">0</span></div>
    <div class="go-row"><span class="go-lbl">DOG</span><span class="go-val" id="goDog">#4238</span></div>
    <div class="go-row"><span class="go-lbl">RANK</span><span class="go-val" id="goRank">#1</span></div>
    <div class="go-row"><span class="go-lbl">BEST</span><span class="go-val" id="goBest">0</span></div>
  </div>
  <div class="share-box">
    <div class="share-txt">
      🐾 I scored <span class="sh-ny" id="sh-score">0</span> pts as<br>
      Doginal Dog <span class="sh-ng" id="sh-dog">#4238</span> in DOGGER!<br>
      Level <span class="sh-nc" id="sh-lvl">1</span> · Rank <span class="sh-np" id="sh-rank">#1</span><br>
      <span style="color:var(--nc)">#Dogger #AndMetaX #DoginalDog #XRP</span>
    </div>
  </div>
  <button class="btn btn-yellow" onclick="shareX()">🐦 SHARE ON X</button>
  <button class="btn btn-green" onclick="startGame()">▶ PLAY AGAIN</button>
  <button class="btn btn-cyan btn-sm" onclick="showLB()">🏆 LEADERBOARD</button>
  <button class="btn btn-pink btn-sm" onclick="showScreen('titleScreen')">🏠 MENU</button>
</div>

<!-- ══ LEADERBOARD ══ -->
<div class="screen hidden" id="lbScreen">
  <div class="lb-title">🏆 TOP DOGGERS</div>
  <div style="font-family:'Black Ops One',cursive;font-size:9px;letter-spacing:3px;color:var(--np);margin-bottom:3px">DOGINAL WAR RANKINGS</div>
  <div class="lb-list" id="lbList"></div>
  <button class="btn btn-green btn-sm" onclick="startGame()">▶ PLAY</button>
  <button class="btn btn-pink btn-sm" onclick="showScreen('titleScreen')">🏠 MENU</button>
</div>

<script>
// ══════════════════════════════════════════
//  CONSTANTS & STATE
// ══════════════════════════════════════════
const DEFAULT_DOG = 'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAA+gAAAPoCAYAAABNo9TkAAAaj0lEQVR4nO3ZMW5cexmH4QyamgYpdQrfAqXMAmixi4gF+DapwJSTHqXPoUJJKhfcWUBkJDsswrejcgoKKko2MGzgchA21veO8zwr+Mk6+o9ffZvlsD88AwAAAEb9bHoAAAAAINABAAAgQaADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAA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';

let playerImg = new Image(); playerImg.src = DEFAULT_DOG;
let playerNFT = '4238', playerName = 'DOGGER';
let customPfp = null, visionPassed = false;

let score=0,level=1,lives=3,coins=0,bestScore=0;
let gameRunning=false;
let dog={x:0,y:0,col:0,row:0};
let obstacles=[],coinItems=[],logItems=[];
let rafId=null,lastTime=0;
let invincible=false,invincTimer=0,flashTimer=0;

const COLS_G=9,ROWS_G=13;
let CELL=40,W=360,H=520;

let leaderboard=JSON.parse(localStorage.getItem('dogger_lb')||'[]');
bestScore=parseInt(localStorage.getItem('dogger_best')||'0');

const LANE_TYPES=['safe','river','river','river','safe','road','road','road','road','road','road','road','safe'];

// ══════════════════════════════════════════
//  BG CANVAS
// ══════════════════════════════════════════
const bgc=document.getElementById('bgCanvas'),bx=bgc.getContext('2d');
let bt=0;
function resizeBG(){bgc.width=innerWidth;bgc.height=innerHeight}
resizeBG();window.addEventListener('resize',resizeBG);
const BCOLS=['#00ff88','#00ffff','#ff00ff','#ffff00','#ff6600'];
function drawBG(){
  bx.clearRect(0,0,bgc.width,bgc.height);
  const vx=bgc.width/2,vy=bgc.height*.65;
  for(let i=0;i<=12;i++){const px=(i/12)*bgc.width;bx.beginPath();bx.moveTo(px,bgc.height);bx.lineTo(vx,vy);bx.strokeStyle=`rgba(0,255,136,${.04+Math.sin(bt+i*.5)*.015})`;bx.lineWidth=1;bx.stroke()}
  for(let r=0;r<4;r++){const rad=((bt*70+r*130)%500),a=Math.max(0,.12-rad/500*.12);bx.beginPath();bx.arc(bgc.width/2,0,rad,0,Math.PI*2);bx.strokeStyle=`rgba(0,255,136,${a})`;bx.lineWidth=1.5;bx.stroke()}
  for(let i=0;i<25;i++){const px=(Math.sin(bt*.2+i*2.3)*.5+.5)*bgc.width,py=(Math.cos(bt*.15+i*1.7)*.5+.5)*bgc.height,c=BCOLS[i%BCOLS.length];bx.beginPath();bx.arc(px,py,.6+Math.sin(bt+i)*.4,0,Math.PI*2);bx.shadowBlur=6;bx.shadowColor=c;bx.fillStyle=c;bx.fill();bx.shadowBlur=0}
  bt+=.01;requestAnimationFrame(drawBG);
}
drawBG();

// ══════════════════════════════════════════
//  PREVIEW DOG
// ══════════════════════════════════════════
function drawPreview(){
  const pc=document.getElementById('previewCanvas'),px=pc.getContext('2d');
  px.clearRect(0,0,100,100);
  px.fillStyle='#7dffb3';px.fillRect(0,0,100,100);
  px.imageSmoothingEnabled=false;
  px.drawImage(playerImg,0,0,100,100);
  px.strokeStyle='#00ff88';px.lineWidth=3;px.shadowBlur=14;px.shadowColor='#00ff88';
  px.strokeRect(1,1,98,98);px.shadowBlur=0;
}
playerImg.onload=drawPreview;

// ══════════════════════════════════════════
//  CLAUDE VISION CHECK
// ══════════════════════════════════════════
const vs=document.getElementById('visionStatus');
const playBtn=document.getElementById('playBtn');

async function checkWithVision(b64data){
  vs.className='checking';vs.style.display='block';
  vs.textContent='🔍 SCANNING YOUR DOG... AI VISION CHECKING...';
  playBtn.disabled=true;

  try{
    const res=await fetch('https://api.anthropic.com/v1/messages',{
      method:'POST',
      headers:{'Content-Type':'application/json'},
      body:JSON.stringify({
        model:'claude-sonnet-4-20250514',
        max_tokens:120,
        messages:[{
          role:'user',
          content:[
            {
              type:'image',
              source:{type:'base64',media_type:'image/png',data:b64data.replace(/^data:image\/\w+;base64,/,'')}
            },
            {
              type:'text',
              text:'You are a content moderator for the Doginal Dogs NFT game DOGGER. Look at this image and respond with ONLY a JSON object like {"ok":true,"reason":""} or {"ok":false,"reason":"short reason"}. Approve (ok:true) ONLY if the image shows: a pixel art dog, cartoon dog, NFT dog/animal avatar, or any dog-themed digital art. Reject (ok:false) if it contains: explicit/adult content, real human faces, hate symbols, graphic violence, logos of other companies, or anything clearly not a dog/animal NFT. Be generous with dog-related art styles.'
            }
          ]
        }]
      })
    });
    const data=await res.json();
    const text=data.content?.[0]?.text||'';
    let parsed;
    try{
      const clean=text.replace(/```json|```/g,'').trim();
      parsed=JSON.parse(clean);
    }catch(e){
      // if parse fails, be generous and allow it
      parsed={ok:true,reason:''};
    }
    if(parsed.ok){
      vs.className='ok';
      vs.textContent='✅ DOGINAL DOG VERIFIED — READY TO PLAY!';
      playBtn.disabled=false;
      visionPassed=true;
    } else {
      vs.className='bad';
      vs.textContent=`❌ INVALID IMAGE — ${(parsed.reason||'must be a Doginal Dog NFT').toUpperCase()}`;
      // reset to default dog
      playerImg=new Image();playerImg.src=DEFAULT_DOG;
      customPfp=null;playerImg.onload=drawPreview;
      playBtn.disabled=false;
      visionPassed=false;
    }
  }catch(err){
    // network error — be gracious, let them play
    vs.className='ok';
    vs.textContent='⚠️ VISION CHECK OFFLINE — PROCEEDING...';
    playBtn.disabled=false;
    visionPassed=true;
  }
}

// FILE UPLOAD
document.getElementById('pfpInput').addEventListener('change',e=>{
  const f=e.target.files[0];if(!f)return;
  const r=new FileReader();
  r.onload=ev=>{
    const dataUrl=ev.target.result;
    customPfp=dataUrl;
    playerImg=new Image();
    playerImg.onload=drawPreview;
    playerImg.src=dataUrl;
    // Run vision check
    checkWithVision(dataUrl);
  };
  r.readAsDataURL(f);
});

// ══════════════════════════════════════════
//  GAME RESIZE
// ══════════════════════════════════════════
function resizeGame(){
  const gs=document.getElementById('gameScreen');
  const hudH=document.getElementById('hud').offsetHeight||44;
  const dpadH=document.getElementById('dpad').offsetHeight||118;
  const avail=gs.offsetHeight-hudH-dpadH;
  CELL=Math.floor(Math.min(gs.offsetWidth/COLS_G,avail/ROWS_G));
  CELL=Math.max(26,Math.min(CELL,46));
  W=COLS_G*CELL;H=ROWS_G*CELL;
  const gc=document.getElementById('gameCanvas');
  gc.width=W;gc.height=H;gc.style.width=W+'px';gc.style.height=H+'px';
}

// ══════════════════════════════════════════
//  START GAME
// ══════════════════════════════════════════
function startGame(){
  playerNFT=document.getElementById('nftNum').value||'4238';
  playerName=(document.getElementById('playerName').value||'DOGGER').trim()||'DOGGER';
  score=0;level=1;lives=3;coins=0;
  bestScore=parseInt(localStorage.getItem('dogger_best')||'0');
  showScreen('gameScreen');
  setTimeout(()=>{resizeGame();resetDog();genLanes();gameRunning=true;if(rafId)cancelAnimationFrame(rafId);lastTime=0;rafId=requestAnimationFrame(loop);},60);
}

function resetDog(){
  dog.col=Math.floor(COLS_G/2);dog.row=ROWS_G-1;
  dog.x=dog.col*CELL;dog.y=dog.row*CELL;
  invincible=true;invincTimer=120;flashTimer=0;
}

// ══════════════════════════════════════════
//  GENERATE LANES
// ══════════════════════════════════════════
function genLanes(){
  obstacles=[];coinItems=[];logItems=[];
  const spd=1+(level-1)*.2;
  for(let row=0;row<ROWS_G;row++){
    const lt=LANE_TYPES[row];
    if(lt==='road'){
      const dir=(row%2===0)?1:-1;
      const cnt=2+Math.min(level,4);
      for(let i=0;i<cnt;i++){
        const isEnemy=Math.random()<.22&&level>=2;
        obstacles.push({x:i*(W/cnt)+Math.random()*15,y:row*CELL+4,w:CELL*(isEnemy?1.2:1.3+Math.random()*.7),h:CELL-8,row,speed:dir*(spd+Math.random()*.5),type:isEnemy?'enemy':'car',color:isEnemy?'#ff2244':['#ff6600','#00ffff','#ff00ff','#ffff00'][Math.floor(Math.random()*4)]});
      }
      if(Math.random()<.5)coinItems.push({x:Math.random()*(W-CELL)+CELL/2,y:row*CELL+CELL/2,row,collected:false,bob:Math.random()*Math.PI*2});
    }
    if(lt==='river'){
      const dir=(row%2===0)?1:-1;
      const cnt=2+Math.min(level,3);
      for(let i=0;i<cnt;i++){
        logItems.push({x:i*(W/cnt)+Math.random()*20,y:row*CELL+2,w:CELL*(1.8+Math.random()*.8),h:CELL-4,row,speed:dir*(spd*.65+Math.random()*.3)});
      }
      if(Math.random()<.4)coinItems.push({x:Math.random()*(W-CELL)+CELL/2,y:row*CELL+CELL/2,row,collected:false,bob:Math.random()*Math.PI*2,onRiver:true});
    }
  }
}

// ══════════════════════════════════════════
//  MAIN LOOP
// ══════════════════════════════════════════
function loop(ts){
  if(!gameRunning)return;
  const dt=Math.min((ts-lastTime)/16.67,3);lastTime=ts;
  update(dt);render();
  rafId=requestAnimationFrame(loop);
}

function update(dt){
  if(invincible){invincTimer-=dt;if(invincTimer<=0)invincible=false;}
  if(flashTimer>0)flashTimer-=dt;
  // move obstacles
  obstacles.forEach(o=>{o.x+=o.speed*dt;if(o.x>W+o.w)o.x=-o.w;if(o.x<-o.w)o.x=W+o.w;});
  logItems.forEach(l=>{l.x+=l.speed*dt;if(l.x>W+l.w)l.x=-l.w;if(l.x<-l.w-10)l.x=W+l.w;});
  coinItems.forEach(c=>c.bob+=.08*dt);
  // river check
  const lt=LANE_TYPES[dog.row];
  if(lt==='river'){
    let onLog=false;
    for(const l of logItems){
      if(l.row===dog.row){const dx=dog.x+CELL/2,dy=dog.y+CELL/2;if(dx>l.x&&dx<l.x+l.w&&dy>l.y&&dy<l.y+l.h){onLog=true;dog.x+=l.speed*dt;break;}}
    }
    if(!onLog&&!invincible)die();
  }
  if((dog.x<-CELL||dog.x>W)&&!invincible)die();
  // road collision
  if(lt==='road'&&!invincible){
    const dx=dog.x+CELL*.15,dw=CELL*.7,dy=dog.y+CELL*.1,dh=CELL*.8;
    for(const o of obstacles){if(o.row===dog.row&&dx<o.x+o.w&&dx+dw>o.x&&dy<o.y+o.h&&dy+dh>o.y){die();break;}}
  }
  // coins
  coinItems.forEach(c=>{if(!c.collected&&Math.abs(dog.x+CELL/2-c.x)<CELL*.7&&Math.abs(dog.y+CELL/2-c.y)<CELL*.7){c.collected=true;coins++;score+=50;updateHUD();}});
  // reached top
  if(dog.row===0){score+=200+level*50;level++;updateHUD();showLvlBanner();resetDog();genLanes();}
}

function die(){
  if(invincible)return;
  lives--;updateHUD();
  invincible=true;invincTimer=130;flashTimer=50;
  if(lives<=0){gameRunning=false;setTimeout(gameOver,700);}
  else resetDog();
}

// ══════════════════════════════════════════
//  RENDER
// ══════════════════════════════════════════
function render(){
  const gc=document.getElementById('gameCanvas'),ctx=gc.getContext('2d');
  ctx.clearRect(0,0,W,H);
  for(let row=0;row<ROWS_G;row++){
    const lt=LANE_TYPES[row],y=row*CELL;
    if(lt==='safe'){
      ctx.fillStyle=row===0?'#002200':'#001800';ctx.fillRect(0,y,W,CELL);
      ctx.strokeStyle='rgba(0,255,136,.1)';ctx.lineWidth=1;ctx.beginPath();ctx.moveTo(0,y);ctx.lineTo(W,y);ctx.stroke();
      if(row===0){ctx.fillStyle='rgba(0,255,136,.08)';ctx.fillRect(0,y,W,CELL);ctx.font=`bold ${CELL*.32}px Orbitron`;ctx.fillStyle='rgba(0,255,136,.35)';ctx.textAlign='center';ctx.fillText('⭐ FINISH ⭐',W/2,y+CELL*.65);}
    }else if(lt==='river'){
      ctx.fillStyle='#001428';ctx.fillRect(0,y,W,CELL);
      for(let wx=0;wx<W;wx+=18){ctx.fillStyle=`rgba(0,150,255,${.03+.025*Math.sin(Date.now()/700+wx*.1)})`;ctx.fillRect(wx,y,10,CELL);}
      ctx.strokeStyle='rgba(0,80,200,.25)';ctx.lineWidth=1;ctx.beginPath();ctx.moveTo(0,y);ctx.lineTo(W,y);ctx.stroke();
    }else{
      ctx.fillStyle=row%2===0?'#09090d':'#070708';ctx.fillRect(0,y,W,CELL);
      ctx.strokeStyle='rgba(255,220,0,.12)';ctx.lineWidth=1.5;ctx.setLineDash([CELL*.38,CELL*.28]);
      ctx.beginPath();ctx.moveTo(0,y+CELL/2);ctx.lineTo(W,y+CELL/2);ctx.stroke();ctx.setLineDash([]);
    }
  }
  // logs
  logItems.forEach(l=>{
    ctx.fillStyle='#3d2000';ctx.fillRect(l.x,l.y,l.w,l.h);
    ctx.strokeStyle='#00ff88';ctx.lineWidth=1.5;ctx.shadowBlur=5;ctx.shadowColor='#00ff88';ctx.strokeRect(l.x,l.y,l.w,l.h);ctx.shadowBlur=0;
    ctx.strokeStyle='rgba(80,40,0,.5)';ctx.lineWidth=1;
    for(let gx=l.x+8;gx<l.x+l.w-4;gx+=8){ctx.beginPath();ctx.moveTo(gx,l.y+2);ctx.lineTo(gx,l.y+l.h-2);ctx.stroke();}
  });
  // obstacles
  obstacles.forEach(o=>{
    if(o.type==='enemy'){
      ctx.fillStyle='#100003';ctx.fillRect(o.x,o.y,o.w,o.h);
      ctx.strokeStyle=o.color;ctx.lineWidth=1.5;ctx.shadowBlur=9;ctx.shadowColor=o.color;ctx.strokeRect(o.x,o.y,o.w,o.h);ctx.shadowBlur=0;
      ctx.font=`${CELL*.48}px sans-serif`;ctx.textAlign='center';ctx.fillText('🐕',o.x+o.w/2,o.y+o.h*.72);
    }else{
      ctx.fillStyle='#080808';ctx.fillRect(o.x,o.y,o.w,o.h);
      const gr=ctx.createLinearGradient(o.x,o.y,o.x,o.y+o.h);gr.addColorStop(0,o.color+'55');gr.addColorStop(.5,o.color+'99');gr.addColorStop(1,o.color+'22');
      ctx.fillStyle=gr;ctx.fillRect(o.x,o.y,o.w,o.h);
      ctx.strokeStyle=o.color;ctx.lineWidth=1.2;ctx.shadowBlur=7;ctx.shadowColor=o.color;ctx.strokeRect(o.x,o.y,o.w,o.h);ctx.shadowBlur=0;
      const lc=o.speed>0?'#ffffaa':'#ff3355',rc=o.speed>0?'#ff3355':'#ffffaa';
      ctx.fillStyle=lc;ctx.shadowColor=lc;ctx.shadowBlur=5;ctx.fillRect(o.x+2,o.y+2,4,5);ctx.fillRect(o.x+2,o.y+o.h-7,4,5);
      ctx.fillStyle=rc;ctx.shadowColor=rc;ctx.fillRect(o.x+o.w-6,o.y+2,4,5);ctx.fillRect(o.x+o.w-6,o.y+o.h-7,4,5);
      ctx.shadowBlur=0;
    }
  });
  // coins
  coinItems.forEach(c=>{
    if(c.collected)return;
    const by=Math.sin(c.bob)*3.5;
    ctx.save();ctx.shadowBlur=14;ctx.shadowColor='#ffdd00';
    ctx.fillStyle='#ffd700';ctx.beginPath();ctx.arc(c.x,c.y+by,CELL*.26,0,Math.PI*2);ctx.fill();
    ctx.fillStyle='#fff8a0';ctx.beginPath();ctx.arc(c.x-2,c.y+by-2,CELL*.1,0,Math.PI*2);ctx.fill();
    ctx.fillStyle='#7a4800';ctx.font=`bold ${CELL*.2}px sans-serif`;ctx.textAlign='center';ctx.textBaseline='middle';ctx.fillText('₿',c.x,c.y+by+1);
    ctx.restore();
  });
  // player dog
  const show=!invincible||Math.floor(flashTimer/4)%2===0;
  if(show){
    ctx.save();
    if(invincible&&flashTimer>0)ctx.globalAlpha=.55;
    ctx.shadowBlur=14;ctx.shadowColor='#00ff88';
    // square frame for dog
    ctx.fillStyle='#7dffb3';ctx.fillRect(dog.x+CELL*.05,dog.y+CELL*.05,CELL*.9,CELL*.9);
    ctx.imageSmoothingEnabled=false;
    ctx.drawImage(playerImg,dog.x+CELL*.05,dog.y+CELL*.05,CELL*.9,CELL*.9);
    ctx.strokeStyle='#00ff88';ctx.lineWidth=2;ctx.strokeRect(dog.x+CELL*.05,dog.y+CELL*.05,CELL*.9,CELL*.9);
    ctx.restore();
    ctx.font=`bold ${CELL*.16}px Orbitron`;ctx.fillStyle='#00ff88';ctx.textAlign='center';ctx.shadowBlur=4;ctx.shadowColor='#00ff88';
    ctx.fillText('#'+playerNFT,dog.x+CELL/2,dog.y+CELL+CELL*.18);ctx.shadowBlur=0;
  }
  updateHUD();
}

// ══════════════════════════════════════════
//  HUD
// ══════════════════════════════════════════
function updateHUD(){
  document.getElementById('hudScore').textContent=score;
  document.getElementById('hudLevel').textContent=level;
  document.getElementById('hudCoins').textContent=coins;
  document.getElementById('hudLives').textContent='🐾'.repeat(Math.max(0,lives));
  document.getElementById('hudBest').textContent=Math.max(score,bestScore);
}

// ══════════════════════════════════════════
//  LEVEL BANNER
// ══════════════════════════════════════════
function showLvlBanner(){
  const b=document.getElementById('lvlBanner');
  document.getElementById('lvlNum').textContent='LEVEL '+level;
  b.classList.add('show');setTimeout(()=>b.classList.remove('show'),1900);
}

// ══════════════════════════════════════════
//  DPAD
// ══════════════════════════════════════════
const dState={};
function dpadOn(d,e){e.preventDefault();if(dState[d])return;dState[d]=true;document.getElementById({U:'bU',D:'bD',L:'bL',R:'bR'}[d]).classList.add('on');moveDog(d);}
function dpadOff(d){dState[d]=false;document.getElementById({U:'bU',D:'bD',L:'bL',R:'bR'}[d]).classList.remove('on');}
function moveDog(d){
  if(!gameRunning)return;
  let nr=dog.row,nc=dog.col;
  if(d==='U')nr=Math.max(0,dog.row-1);
  if(d==='D')nr=Math.min(ROWS_G-1,dog.row+1);
  if(d==='L')nc=Math.max(0,dog.col-1);
  if(d==='R')nc=Math.min(COLS_G-1,dog.col+1);
  dog.row=nr;dog.col=nc;dog.x=nc*CELL;dog.y=nr*CELL;
  if(d==='U')score+=10;updateHUD();
}
document.addEventListener('keydown',e=>{
  const m={ArrowUp:'U',ArrowDown:'D',ArrowLeft:'L',ArrowRight:'R',w:'U',s:'D',a:'L',d:'R'};
  if(m[e.key]){e.preventDefault();moveDog(m[e.key]);}
});

// ══════════════════════════════════════════
//  GAME OVER
// ══════════════════════════════════════════
function gameOver(){
  if(score>bestScore){bestScore=score;localStorage.setItem('dogger_best',bestScore);}
  saveToLB();
  const rank=getRank();
  document.getElementById('goScore').textContent=score;
  document.getElementById('goLevel').textContent=level;
  document.getElementById('goCoins').textContent=coins;
  document.getElementById('goDog').textContent='#'+playerNFT;
  document.getElementById('goRank').textContent='#'+rank;
  document.getElementById('goBest').textContent=bestScore;
  document.getElementById('sh-score').textContent=score;
  document.getElementById('sh-dog').textContent='#'+playerNFT;
  document.getElementById('sh-lvl').textContent=level;
  document.getElementById('sh-rank').textContent='#'+rank;
  // copy pfp to game-over canvas
  const gp=document.getElementById('goPfp'),gpx=gp.getContext('2d');
  gpx.fillStyle='#7dffb3';gpx.fillRect(0,0,70,70);
  gpx.imageSmoothingEnabled=false;gpx.drawImage(playerImg,0,0,70,70);
  showScreen('goScreen');
}

// ══════════════════════════════════════════
//  LEADERBOARD
// ══════════════════════════════════════════
function saveToLB(){
  leaderboard=leaderboard.filter(e=>!(e.nft===playerNFT&&e.name===playerName));
  leaderboard.push({name:playerName.substring(0,16),nft:playerNFT,score,level,coins,pfp:customPfp||DEFAULT_DOG,ts:Date.now()});
  leaderboard.sort((a,b)=>b.score-a.score);leaderboard=leaderboard.slice(0,20);
  localStorage.setItem('dogger_lb',JSON.stringify(leaderboard));
}
function getRank(){const i=leaderboard.findIndex(e=>e.nft===playerNFT&&e.score===score);return i===-1?leaderboard.length:i+1;}
function showLB(){renderLB();showScreen('lbScreen');}
function renderLB(){
  const lb=document.getElementById('lbList');
  if(!leaderboard.length){lb.innerHTML='<div style="text-align:center;color:rgba(0,255,136,.4);font-size:11px;letter-spacing:2px;padding:20px">NO SCORES YET — BE FIRST! 🐾</div>';return;}
  const rc=['g','s','b'];
  lb.innerHTML=leaderboard.slice(0,10).map((e,i)=>{
    const isMe=e.nft===playerNFT&&e.name===playerName;
    return `<div class="lb-row${isMe?' me':''}">
      <span class="lb-rank ${rc[i]||''}">${i===0?'🥇':i===1?'🥈':i===2?'🥉':'#'+(i+1)}</span>
      <img class="lb-dog" src="${e.pfp}" alt="dog"/>
      <div class="lb-info"><div class="lb-name">${e.name} <span style="color:var(--nc);font-size:9px">#${e.nft}</span></div><div class="lb-sub">LVL ${e.level} · ${e.coins} COINS</div></div>
      <span class="lb-pts">${e.score}</span>
    </div>`;
  }).join('');
}

// ══════════════════════════════════════════
//  SHARE TO X
// ══════════════════════════════════════════
function shareX(){
  const rank=getRank();
  const txt=`🐾 I scored ${score} pts as Doginal Dog #${playerNFT} in DOGGER!\nLevel ${level} · ${coins} coins · Rank #${rank}\n\nPlay free: https://andmetax.glitch.me\n\n#Dogger #AndMetaX #DoginalDog #XRP`;
  window.open('https://twitter.com/intent/tweet?text='+encodeURIComponent(txt),'_blank');
}

// ══════════════════════════════════════════
//  SCREEN MANAGEMENT
// ══════════════════════════════════════════
function showScreen(id){
  document.querySelectorAll('.screen').forEach(s=>s.classList.add('hidden'));
  document.getElementById(id).classList.remove('hidden');
  if(id==='gameScreen')setTimeout(resizeGame,60);
}
// init
showScreen('titleScreen');
setTimeout(drawPreview,150);
</script>
</body>
</html><!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
<title>DOGGER — AndMetaX</title>
<link href="https://fonts.googleapis.com/css2?family=Bangers&family=Orbitron:wght@700;900&family=Black+Ops+One&display=swap" rel="stylesheet">
<style>
:root{
  --ng:#00ff88;--nc:#00ffff;--np:#ff00ff;--ny:#ffff00;--no:#ff6600;--nr:#ff2244;
  --void:#000008;
  --gg:0 0 8px #00ff88,0 0 20px #00ff88;
  --gc:0 0 8px #00ffff,0 0 20px #00ffff;
  --gp:0 0 8px #ff00ff,0 0 20px #ff00ff;
  --gy:0 0 8px #ffff00,0 0 20px #ffff00;
}
*{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent;user-select:none}
body{background:var(--void);font-family:'Orbitron',monospace;color:#fff;height:100vh;width:100vw;overflow:hidden;display:flex;flex-direction:column;align-items:center;justify-content:center}

/* SCREENS */
.screen{position:fixed;inset:0;display:flex;flex-direction:column;align-items:center;justify-content:center;padding:16px;z-index:10;background:var(--void);overflow-y:auto}
.screen.hidden{display:none!important}

/* BG CANVAS */
#bgCanvas{position:fixed;inset:0;z-index:0;width:100%;height:100%;pointer-events:none}
.scl{position:fixed;inset:0;z-index:1;background:repeating-linear-gradient(0deg,transparent,transparent 3px,rgba(0,255,136,.012) 3px,rgba(0,255,136,.012) 4px);pointer-events:none}

/* TITLE SCREEN */
.game-logo{font-family:'Bangers',cursive;font-size:clamp(60px,18vw,110px);letter-spacing:10px;color:var(--ng);text-shadow:var(--gg),0 0 60px #00ff88,6px 6px 0 #003320;line-height:1;animation:logoPulse 2s ease-in-out infinite;text-align:center}
@keyframes logoPulse{0%,100%{text-shadow:var(--gg),0 0 60px #00ff88,6px 6px 0 #003320}50%{text-shadow:0 0 20px #00ff88,0 0 80px #00ff88,0 0 140px #00ff88,6px 6px 0 #003320}}
.game-sub{font-family:'Black Ops One',cursive;font-size:10px;letter-spacing:5px;color:var(--nc);text-shadow:var(--gc);margin-bottom:4px;animation:flk 4s infinite}
@keyframes flk{0%,18%,20%,100%{opacity:1}19%{opacity:.3}}
.doginal-tag{font-family:'Black Ops One',cursive;font-size:10px;letter-spacing:3px;color:var(--np);text-shadow:var(--gp);margin-bottom:20px}

/* PREVIEW AVATAR */
#previewWrap{position:relative;width:100px;height:100px;margin:0 auto 18px;cursor:pointer}
#previewCanvas{display:block;width:100px;height:100px;border:2px solid var(--ng);box-shadow:0 0 20px var(--ng),0 0 60px rgba(0,255,136,.3);image-rendering:pixelated}
.preview-overlay{position:absolute;inset:0;background:rgba(0,255,136,.0);display:flex;align-items:center;justify-content:center;transition:.2s;font-family:'Black Ops One',cursive;font-size:8px;letter-spacing:1px;color:rgba(0,255,136,.0);text-align:center;border:2px solid transparent}
#previewWrap:hover .preview-overlay{background:rgba(0,0,8,.7);color:var(--ng);border-color:var(--ng)}

/* SETUP PANEL */
.setup-panel{background:rgba(0,255,136,.04);border:1px solid rgba(0,255,136,.25);padding:14px 18px;width:100%;max-width:340px;margin-bottom:14px;position:relative}
.setup-panel::before{content:'// PLAYER SETUP';position:absolute;top:-9px;left:10px;background:var(--void);color:var(--nc);font-size:8px;letter-spacing:2px;padding:0 6px;text-shadow:var(--gc)}
.s-row{display:flex;gap:8px;margin-bottom:9px;align-items:center}
.s-row:last-child{margin-bottom:0}
.s-lbl{font-size:8px;letter-spacing:2px;color:rgba(0,255,136,.55);white-space:nowrap;flex-shrink:0;min-width:44px}
.s-inp{background:rgba(0,0,0,.6);border:1px solid rgba(0,255,136,.35);color:var(--ng);font-family:'Orbitron',monospace;font-size:12px;padding:6px 9px;flex:1;min-width:0;outline:none}
.s-inp:focus{border-color:var(--ng);box-shadow:0 0 8px rgba(0,255,136,.3)}
.upload-btn{background:rgba(0,255,136,.08);border:1px solid var(--ng);color:var(--ng);font-family:'Black Ops One',cursive;font-size:8px;letter-spacing:1px;padding:7px 12px;cursor:pointer;transition:.2s;white-space:nowrap}
.upload-btn:hover{background:rgba(0,255,136,.22);box-shadow:var(--gg)}
#pfpInput{display:none}

/* VISION CHECK */
#visionStatus{font-family:'Black Ops One',cursive;font-size:9px;letter-spacing:2px;padding:6px 12px;margin-top:6px;text-align:center;border:1px solid;display:none;width:100%;max-width:340px}
#visionStatus.checking{color:var(--ny);border-color:var(--ny);display:block;animation:flk .8s infinite}
#visionStatus.ok{color:var(--ng);border-color:var(--ng);display:block}
#visionStatus.bad{color:var(--nr);border-color:var(--nr);display:block}

/* BUTTONS */
.btn{font-family:'Bangers',cursive;font-size:22px;letter-spacing:4px;padding:11px 30px;border:2px solid;cursor:pointer;transition:all .15s;display:block;width:100%;max-width:300px;text-align:center;text-decoration:none;margin:5px auto}
.btn-green{color:var(--ng);border-color:var(--ng);background:rgba(0,255,136,.07);box-shadow:0 0 12px rgba(0,255,136,.18)}
.btn-green:hover,.btn-green:active{background:rgba(0,255,136,.2);box-shadow:0 0 28px rgba(0,255,136,.4);transform:translateY(-2px)}
.btn-green:disabled{opacity:.35;cursor:not-allowed;transform:none}
.btn-cyan{color:var(--nc);border-color:var(--nc);background:rgba(0,255,255,.07)}
.btn-cyan:hover,.btn-cyan:active{background:rgba(0,255,255,.2);box-shadow:0 0 28px rgba(0,255,255,.4)}
.btn-pink{color:var(--np);border-color:var(--np);background:rgba(255,0,255,.07)}
.btn-pink:hover,.btn-pink:active{background:rgba(255,0,255,.2);box-shadow:0 0 28px rgba(255,0,255,.4)}
.btn-yellow{color:var(--ny);border-color:var(--ny);background:rgba(255,255,0,.07)}
.btn-yellow:hover,.btn-yellow:active{background:rgba(255,255,0,.2);box-shadow:0 0 28px rgba(255,255,0,.4)}
.btn-sm{font-size:14px;padding:8px 18px;letter-spacing:2px}

/* GAME SCREEN */
#gameScreen{padding:0;background:var(--void);justify-content:flex-start}
#hud{width:100%;max-width:420px;display:flex;justify-content:space-between;align-items:center;padding:5px 10px;background:rgba(0,0,0,.85);border-bottom:1px solid rgba(0,255,136,.18);flex-shrink:0;z-index:20}
.hud-item{text-align:center}
.hud-lbl{font-size:6px;letter-spacing:2px;color:rgba(0,255,136,.45);display:block}
.hud-val{font-family:'Bangers',cursive;font-size:19px;letter-spacing:2px;color:var(--ng);text-shadow:var(--gg)}
.hud-val.yel{color:var(--ny);text-shadow:var(--gy)}
.hud-val.red{color:var(--nr);text-shadow:0 0 8px var(--nr)}
#gameCanvas{display:block;max-width:420px;width:100%;flex:1;image-rendering:pixelated;z-index:10}

/* DPAD */
#dpad{width:100%;max-width:420px;background:rgba(0,0,0,.92);border-top:1px solid rgba(0,255,136,.12);padding:8px 0 6px;flex-shrink:0;z-index:20}
.dpad-inner{display:grid;grid-template-columns:repeat(3,54px);grid-template-rows:repeat(3,46px);gap:3px;margin:0 auto;width:fit-content}
.dp{background:rgba(0,255,136,.07);border:2px solid rgba(0,255,136,.25);color:var(--ng);font-size:22px;display:flex;align-items:center;justify-content:center;cursor:pointer;border-radius:7px}
.dp:active,.dp.on{background:rgba(0,255,136,.3);border-color:var(--ng);box-shadow:var(--gg);transform:scale(.93)}
.dp-blank{background:transparent;border:none;pointer-events:none}

/* LEVEL BANNER */
#lvlBanner{position:fixed;top:50%;left:50%;transform:translate(-50%,-50%) scale(0);z-index:200;font-family:'Bangers',cursive;font-size:52px;letter-spacing:6px;color:var(--ny);text-shadow:var(--gy),0 0 60px #ffff00;text-align:center;pointer-events:none;transition:transform .2s}
#lvlBanner.show{transform:translate(-50%,-50%) scale(1)}

/* GAME OVER */
#goScreen .go-title{font-family:'Bangers',cursive;font-size:58px;letter-spacing:6px;color:var(--nr);text-shadow:0 0 20px var(--nr),0 0 60px var(--nr);animation:goPulse 1s ease-in-out infinite}
@keyframes goPulse{0%,100%{transform:scale(1)}50%{transform:scale(1.05)}}
.go-stats{background:rgba(0,255,136,.04);border:1px solid rgba(0,255,136,.18);padding:14px 22px;margin:12px 0;width:100%;max-width:320px}
.go-row{display:flex;justify-content:space-between;align-items:center;margin-bottom:7px}
.go-row:last-child{margin-bottom:0}
.go-lbl{font-size:8px;letter-spacing:3px;color:rgba(0,255,136,.55)}
.go-val{font-family:'Bangers',cursive;font-size:22px;color:var(--ny);text-shadow:var(--gy)}
.share-box{background:#000;border:2px solid var(--ny);padding:12px 14px;margin:8px 0;width:100%;max-width:320px;text-align:center}
.share-txt{font-family:'Black Ops One',cursive;font-size:10px;color:#fff;line-height:1.7;letter-spacing:.5px}
.sh-nc{color:var(--nc)}.sh-ng{color:var(--ng)}.sh-np{color:var(--np)}.sh-ny{color:var(--ny)}

/* LEADERBOARD */
#lbScreen .lb-title{font-family:'Bangers',cursive;font-size:44px;letter-spacing:6px;color:var(--ny);text-shadow:var(--gy);margin-bottom:4px}
.lb-list{width:100%;max-width:380px;margin:10px 0}
.lb-row{display:flex;align-items:center;gap:9px;padding:7px 11px;margin-bottom:5px;border:1px solid rgba(0,255,136,.14);background:rgba(0,255,136,.03)}
.lb-row.me{border-color:var(--ny);background:rgba(255,255,0,.05)}
.lb-rank{font-family:'Bangers',cursive;font-size:22px;width:30px;text-align:center;flex-shrink:0}
.lb-rank.g{color:#ffd700;text-shadow:0 0 10px #ffd700}
.lb-rank.s{color:#c0c0c0;text-shadow:0 0 10px #c0c0c0}
.lb-rank.b{color:#cd7f32;text-shadow:0 0 10px #cd7f32}
.lb-dog{width:32px;height:32px;border:2px solid var(--ng);flex-shrink:0;object-fit:contain;image-rendering:pixelated;background:#7dffb3}
.lb-info{flex:1;min-width:0}
.lb-name{font-family:'Black Ops One',cursive;font-size:11px;color:var(--ng);overflow:hidden;text-overflow:ellipsis;white-space:nowrap}
.lb-sub{font-size:8px;color:var(--nc);letter-spacing:1px}
.lb-pts{font-family:'Bangers',cursive;font-size:20px;color:var(--ny);text-shadow:var(--gy);flex-shrink:0}
</style>
</head>
<body>
<canvas id="bgCanvas"></canvas>
<div class="scl"></div>
<div id="lvlBanner">LEVEL UP!<br><span id="lvlNum" style="font-size:30px;color:var(--nc)"></span></div>

<!-- ══ TITLE ══ -->
<div class="screen" id="titleScreen">
  <div class="game-sub">◈ ANDMETAX PRESENTS ◈</div>
  <div class="game-logo">DOGGER</div>
  <div class="doginal-tag">⚡ DOGINAL DOG FROGGER ⚡</div>

  <div id="previewWrap" onclick="document.getElementById('pfpInput').click()">
    <canvas id="previewCanvas" width="100" height="100"></canvas>
    <div class="preview-overlay">📷 TAP TO<br>UPLOAD DOG</div>
  </div>
  <input type="file" id="pfpInput" accept="image/*"/>

  <div id="visionStatus"></div>

  <div class="setup-panel">
    <div class="s-row">
      <span class="s-lbl">DOG #</span>
      <input class="s-inp" id="nftNum" type="number" placeholder="e.g. 4238" min="1" max="9999"/>
    </div>
    <div class="s-row">
      <span class="s-lbl">NAME</span>
      <input class="s-inp" id="playerName" type="text" placeholder="Your handle" maxlength="16"/>
    </div>
    <div class="s-row">
      <span class="s-lbl">PFP</span>
      <button class="upload-btn" onclick="document.getElementById('pfpInput').click()">📷 UPLOAD YOUR DOGINAL DOG</button>
    </div>
  </div>

  <button class="btn btn-green" id="playBtn" onclick="startGame()">▶ PLAY NOW</button>
  <button class="btn btn-cyan btn-sm" onclick="showLB()">🏆 LEADERBOARD</button>
  <a class="btn btn-pink btn-sm" href="andmetax.html">🏠 BACK TO SITE</a>
</div>

<!-- ══ GAME ══ -->
<div class="screen hidden" id="gameScreen">
  <div id="hud">
    <div class="hud-item"><span class="hud-lbl">SCORE</span><span class="hud-val" id="hudScore">0</span></div>
    <div class="hud-item"><span class="hud-lbl">LEVEL</span><span class="hud-val yel" id="hudLevel">1</span></div>
    <div class="hud-item"><span class="hud-lbl">COINS</span><span class="hud-val yel" id="hudCoins">0</span></div>
    <div class="hud-item"><span class="hud-lbl">LIVES</span><span class="hud-val red" id="hudLives">🐾🐾🐾</span></div>
    <div class="hud-item"><span class="hud-lbl">BEST</span><span class="hud-val" id="hudBest">0</span></div>
  </div>
  <canvas id="gameCanvas"></canvas>
  <div id="dpad">
    <div class="dpad-inner">
      <div class="dp-blank"></div>
      <div class="dp" id="bU" ontouchstart="dpadOn('U',event)" ontouchend="dpadOff('U')">▲</div>
      <div class="dp-blank"></div>
      <div class="dp" id="bL" ontouchstart="dpadOn('L',event)" ontouchend="dpadOff('L')">◀</div>
      <div class="dp-blank"></div>
      <div class="dp" id="bR" ontouchstart="dpadOn('R',event)" ontouchend="dpadOff('R')">▶</div>
      <div class="dp-blank"></div>
      <div class="dp" id="bD" ontouchstart="dpadOn('D',event)" ontouchend="dpadOff('D')">▼</div>
      <div class="dp-blank"></div>
    </div>
  </div>
</div>

<!-- ══ GAME OVER ══ -->
<div class="screen hidden" id="goScreen">
  <div class="go-title">WOOF!</div>
  <div style="font-family:'Black Ops One',cursive;font-size:10px;letter-spacing:3px;color:rgba(255,34,68,.8);margin-bottom:6px">GAME OVER</div>
  <canvas id="goPfp" width="70" height="70" style="border:2px solid var(--ny);box-shadow:0 0 20px var(--ny);margin:6px auto;display:block;image-rendering:pixelated;background:#7dffb3;border-radius:4px"></canvas>
  <div class="go-stats">
    <div class="go-row"><span class="go-lbl">SCORE</span><span class="go-val" id="goScore">0</span></div>
    <div class="go-row"><span class="go-lbl">LEVEL</span><span class="go-val" id="goLevel">1</span></div>
    <div class="go-row"><span class="go-lbl">COINS</span><span class="go-val" id="goCoins">0</span></div>
    <div class="go-row"><span class="go-lbl">DOG</span><span class="go-val" id="goDog">#4238</span></div>
    <div class="go-row"><span class="go-lbl">RANK</span><span class="go-val" id="goRank">#1</span></div>
    <div class="go-row"><span class="go-lbl">BEST</span><span class="go-val" id="goBest">0</span></div>
  </div>
  <div class="share-box">
    <div class="share-txt">
      🐾 I scored <span class="sh-ny" id="sh-score">0</span> pts as<br>
      Doginal Dog <span class="sh-ng" id="sh-dog">#4238</span> in DOGGER!<br>
      Level <span class="sh-nc" id="sh-lvl">1</span> · Rank <span class="sh-np" id="sh-rank">#1</span><br>
      <span style="color:var(--nc)">#Dogger #AndMetaX #DoginalDog #XRP</span>
    </div>
  </div>
  <button class="btn btn-yellow" onclick="shareX()">🐦 SHARE ON X</button>
  <button class="btn btn-green" onclick="startGame()">▶ PLAY AGAIN</button>
  <button class="btn btn-cyan btn-sm" onclick="showLB()">🏆 LEADERBOARD</button>
  <button class="btn btn-pink btn-sm" onclick="showScreen('titleScreen')">🏠 MENU</button>
</div>

<!-- ══ LEADERBOARD ══ -->
<div class="screen hidden" id="lbScreen">
  <div class="lb-title">🏆 TOP DOGGERS</div>
  <div style="font-family:'Black Ops One',cursive;font-size:9px;letter-spacing:3px;color:var(--np);margin-bottom:3px">DOGINAL WAR RANKINGS</div>
  <div class="lb-list" id="lbList"></div>
  <button class="btn btn-green btn-sm" onclick="startGame()">▶ PLAY</button>
  <button class="btn btn-pink btn-sm" onclick="showScreen('titleScreen')">🏠 MENU</button>
</div>

<script>
// ══════════════════════════════════════════
//  CONSTANTS & STATE
// ══════════════════════════════════════════
const DEFAULT_DOG = 'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAA+gAAAPoCAYAAABNo9TkAAAaj0lEQVR4nO3ZMW5cexmH4QyamgYpdQrfAqXMAmixi4gF+DapwJSTHqXPoUJJKhfcWUBkJDsswrejcgoKKko2MGzgchA21veO8zwr+Mk6+o9ffZvlsD88AwAAAEb9bHoAAAAAINABAAAgQaADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAAECDQAQAAIECgAwAAQIBABwAAgACBDgAAAAECHQAAAAIEOgAAAAQIdAAAAAgQ6AAAABAg0AEAACBAoAMAAECAQAcAAIAAgQ4AAAABAh0AAAACBDoAAAAECHQAAAAIEOgAAAAQINABAAAgQKADAABAgEAHAACAAIEOAAAAAQIdAAAAAgQ6AAAABAh0AAAACBDoAAAA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';

let playerImg = new Image(); playerImg.src = DEFAULT_DOG;
let playerNFT = '4238', playerName = 'DOGGER';
let customPfp = null, visionPassed = false;

let score=0,level=1,lives=3,coins=0,bestScore=0;
let gameRunning=false;
let dog={x:0,y:0,col:0,row:0};
let obstacles=[],coinItems=[],logItems=[];
let rafId=null,lastTime=0;
let invincible=false,invincTimer=0,flashTimer=0;

const COLS_G=9,ROWS_G=13;
let CELL=40,W=360,H=520;

let leaderboard=JSON.parse(localStorage.getItem('dogger_lb')||'[]');
bestScore=parseInt(localStorage.getItem('dogger_best')||'0');

const LANE_TYPES=['safe','river','river','river','safe','road','road','road','road','road','road','road','safe'];

// ══════════════════════════════════════════
//  BG CANVAS
// ══════════════════════════════════════════
const bgc=document.getElementById('bgCanvas'),bx=bgc.getContext('2d');
let bt=0;
function resizeBG(){bgc.width=innerWidth;bgc.height=innerHeight}
resizeBG();window.addEventListener('resize',resizeBG);
const BCOLS=['#00ff88','#00ffff','#ff00ff','#ffff00','#ff6600'];
function drawBG(){
  bx.clearRect(0,0,bgc.width,bgc.height);
  const vx=bgc.width/2,vy=bgc.height*.65;
  for(let i=0;i<=12;i++){const px=(i/12)*bgc.width;bx.beginPath();bx.moveTo(px,bgc.height);bx.lineTo(vx,vy);bx.strokeStyle=`rgba(0,255,136,${.04+Math.sin(bt+i*.5)*.015})`;bx.lineWidth=1;bx.stroke()}
  for(let r=0;r<4;r++){const rad=((bt*70+r*130)%500),a=Math.max(0,.12-rad/500*.12);bx.beginPath();bx.arc(bgc.width/2,0,rad,0,Math.PI*2);bx.strokeStyle=`rgba(0,255,136,${a})`;bx.lineWidth=1.5;bx.stroke()}
  for(let i=0;i<25;i++){const px=(Math.sin(bt*.2+i*2.3)*.5+.5)*bgc.width,py=(Math.cos(bt*.15+i*1.7)*.5+.5)*bgc.height,c=BCOLS[i%BCOLS.length];bx.beginPath();bx.arc(px,py,.6+Math.sin(bt+i)*.4,0,Math.PI*2);bx.shadowBlur=6;bx.shadowColor=c;bx.fillStyle=c;bx.fill();bx.shadowBlur=0}
  bt+=.01;requestAnimationFrame(drawBG);
}
drawBG();

// ══════════════════════════════════════════
//  PREVIEW DOG
// ══════════════════════════════════════════
function drawPreview(){
  const pc=document.getElementById('previewCanvas'),px=pc.getContext('2d');
  px.clearRect(0,0,100,100);
  px.fillStyle='#7dffb3';px.fillRect(0,0,100,100);
  px.imageSmoothingEnabled=false;
  px.drawImage(playerImg,0,0,100,100);
  px.strokeStyle='#00ff88';px.lineWidth=3;px.shadowBlur=14;px.shadowColor='#00ff88';
  px.strokeRect(1,1,98,98);px.shadowBlur=0;
}
playerImg.onload=drawPreview;

// ══════════════════════════════════════════
//  CLAUDE VISION CHECK
// ══════════════════════════════════════════
const vs=document.getElementById('visionStatus');
const playBtn=document.getElementById('playBtn');

async function checkWithVision(b64data){
  vs.className='checking';vs.style.display='block';
  vs.textContent='🔍 SCANNING YOUR DOG... AI VISION CHECKING...';
  playBtn.disabled=true;

  try{
    const res=await fetch('https://api.anthropic.com/v1/messages',{
      method:'POST',
      headers:{'Content-Type':'application/json'},
      body:JSON.stringify({
        model:'claude-sonnet-4-20250514',
        max_tokens:120,
        messages:[{
          role:'user',
          content:[
            {
              type:'image',
              source:{type:'base64',media_type:'image/png',data:b64data.replace(/^data:image\/\w+;base64,/,'')}
            },
            {
              type:'text',
              text:'You are a content moderator for the Doginal Dogs NFT game DOGGER. Look at this image and respond with ONLY a JSON object like {"ok":true,"reason":""} or {"ok":false,"reason":"short reason"}. Approve (ok:true) ONLY if the image shows: a pixel art dog, cartoon dog, NFT dog/animal avatar, or any dog-themed digital art. Reject (ok:false) if it contains: explicit/adult content, real human faces, hate symbols, graphic violence, logos of other companies, or anything clearly not a dog/animal NFT. Be generous with dog-related art styles.'
            }
          ]
        }]
      })
    });
    const data=await res.json();
    const text=data.content?.[0]?.text||'';
    let parsed;
    try{
      const clean=text.replace(/```json|```/g,'').trim();
      parsed=JSON.parse(clean);
    }catch(e){
      // if parse fails, be generous and allow it
      parsed={ok:true,reason:''};
    }
    if(parsed.ok){
      vs.className='ok';
      vs.textContent='✅ DOGINAL DOG VERIFIED — READY TO PLAY!';
      playBtn.disabled=false;
      visionPassed=true;
    } else {
      vs.className='bad';
      vs.textContent=`❌ INVALID IMAGE — ${(parsed.reason||'must be a Doginal Dog NFT').toUpperCase()}`;
      // reset to default dog
      playerImg=new Image();playerImg.src=DEFAULT_DOG;
      customPfp=null;playerImg.onload=drawPreview;
      playBtn.disabled=false;
      visionPassed=false;
    }
  }catch(err){
    // network error — be gracious, let them play
    vs.className='ok';
    vs.textContent='⚠️ VISION CHECK OFFLINE — PROCEEDING...';
    playBtn.disabled=false;
    visionPassed=true;
  }
}

// FILE UPLOAD
document.getElementById('pfpInput').addEventListener('change',e=>{
  const f=e.target.files[0];if(!f)return;
  const r=new FileReader();
  r.onload=ev=>{
    const dataUrl=ev.target.result;
    customPfp=dataUrl;
    playerImg=new Image();
    playerImg.onload=drawPreview;
    playerImg.src=dataUrl;
    // Run vision check
    checkWithVision(dataUrl);
  };
  r.readAsDataURL(f);
});

// ══════════════════════════════════════════
//  GAME RESIZE
// ══════════════════════════════════════════
function resizeGame(){
  const gs=document.getElementById('gameScreen');
  const hudH=document.getElementById('hud').offsetHeight||44;
  const dpadH=document.getElementById('dpad').offsetHeight||118;
  const avail=gs.offsetHeight-hudH-dpadH;
  CELL=Math.floor(Math.min(gs.offsetWidth/COLS_G,avail/ROWS_G));
  CELL=Math.max(26,Math.min(CELL,46));
  W=COLS_G*CELL;H=ROWS_G*CELL;
  const gc=document.getElementById('gameCanvas');
  gc.width=W;gc.height=H;gc.style.width=W+'px';gc.style.height=H+'px';
}

// ══════════════════════════════════════════
//  START GAME
// ══════════════════════════════════════════
function startGame(){
  playerNFT=document.getElementById('nftNum').value||'4238';
  playerName=(document.getElementById('playerName').value||'DOGGER').trim()||'DOGGER';
  score=0;level=1;lives=3;coins=0;
  bestScore=parseInt(localStorage.getItem('dogger_best')||'0');
  showScreen('gameScreen');
  setTimeout(()=>{resizeGame();resetDog();genLanes();gameRunning=true;if(rafId)cancelAnimationFrame(rafId);lastTime=0;rafId=requestAnimationFrame(loop);},60);
}

function resetDog(){
  dog.col=Math.floor(COLS_G/2);dog.row=ROWS_G-1;
  dog.x=dog.col*CELL;dog.y=dog.row*CELL;
  invincible=true;invincTimer=120;flashTimer=0;
}

// ══════════════════════════════════════════
//  GENERATE LANES
// ══════════════════════════════════════════
function genLanes(){
  obstacles=[];coinItems=[];logItems=[];
  const spd=1+(level-1)*.2;
  for(let row=0;row<ROWS_G;row++){
    const lt=LANE_TYPES[row];
    if(lt==='road'){
      const dir=(row%2===0)?1:-1;
      const cnt=2+Math.min(level,4);
      for(let i=0;i<cnt;i++){
        const isEnemy=Math.random()<.22&&level>=2;
        obstacles.push({x:i*(W/cnt)+Math.random()*15,y:row*CELL+4,w:CELL*(isEnemy?1.2:1.3+Math.random()*.7),h:CELL-8,row,speed:dir*(spd+Math.random()*.5),type:isEnemy?'enemy':'car',color:isEnemy?'#ff2244':['#ff6600','#00ffff','#ff00ff','#ffff00'][Math.floor(Math.random()*4)]});
      }
      if(Math.random()<.5)coinItems.push({x:Math.random()*(W-CELL)+CELL/2,y:row*CELL+CELL/2,row,collected:false,bob:Math.random()*Math.PI*2});
    }
    if(lt==='river'){
      const dir=(row%2===0)?1:-1;
      const cnt=2+Math.min(level,3);
      for(let i=0;i<cnt;i++){
        logItems.push({x:i*(W/cnt)+Math.random()*20,y:row*CELL+2,w:CELL*(1.8+Math.random()*.8),h:CELL-4,row,speed:dir*(spd*.65+Math.random()*.3)});
      }
      if(Math.random()<.4)coinItems.push({x:Math.random()*(W-CELL)+CELL/2,y:row*CELL+CELL/2,row,collected:false,bob:Math.random()*Math.PI*2,onRiver:true});
    }
  }
}

// ══════════════════════════════════════════
//  MAIN LOOP
// ══════════════════════════════════════════
function loop(ts){
  if(!gameRunning)return;
  const dt=Math.min((ts-lastTime)/16.67,3);lastTime=ts;
  update(dt);render();
  rafId=requestAnimationFrame(loop);
}

function update(dt){
  if(invincible){invincTimer-=dt;if(invincTimer<=0)invincible=false;}
  if(flashTimer>0)flashTimer-=dt;
  // move obstacles
  obstacles.forEach(o=>{o.x+=o.speed*dt;if(o.x>W+o.w)o.x=-o.w;if(o.x<-o.w)o.x=W+o.w;});
  logItems.forEach(l=>{l.x+=l.speed*dt;if(l.x>W+l.w)l.x=-l.w;if(l.x<-l.w-10)l.x=W+l.w;});
  coinItems.forEach(c=>c.bob+=.08*dt);
  // river check
  const lt=LANE_TYPES[dog.row];
  if(lt==='river'){
    let onLog=false;
    for(const l of logItems){
      if(l.row===dog.row){const dx=dog.x+CELL/2,dy=dog.y+CELL/2;if(dx>l.x&&dx<l.x+l.w&&dy>l.y&&dy<l.y+l.h){onLog=true;dog.x+=l.speed*dt;break;}}
    }
    if(!onLog&&!invincible)die();
  }
  if((dog.x<-CELL||dog.x>W)&&!invincible)die();
  // road collision
  if(lt==='road'&&!invincible){
    const dx=dog.x+CELL*.15,dw=CELL*.7,dy=dog.y+CELL*.1,dh=CELL*.8;
    for(const o of obstacles){if(o.row===dog.row&&dx<o.x+o.w&&dx+dw>o.x&&dy<o.y+o.h&&dy+dh>o.y){die();break;}}
  }
  // coins
  coinItems.forEach(c=>{if(!c.collected&&Math.abs(dog.x+CELL/2-c.x)<CELL*.7&&Math.abs(dog.y+CELL/2-c.y)<CELL*.7){c.collected=true;coins++;score+=50;updateHUD();}});
  // reached top
  if(dog.row===0){score+=200+level*50;level++;updateHUD();showLvlBanner();resetDog();genLanes();}
}

function die(){
  if(invincible)return;
  lives--;updateHUD();
  invincible=true;invincTimer=130;flashTimer=50;
  if(lives<=0){gameRunning=false;setTimeout(gameOver,700);}
  else resetDog();
}

// ══════════════════════════════════════════
//  RENDER
// ══════════════════════════════════════════
function render(){
  const gc=document.getElementById('gameCanvas'),ctx=gc.getContext('2d');
  ctx.clearRect(0,0,W,H);
  for(let row=0;row<ROWS_G;row++){
    const lt=LANE_TYPES[row],y=row*CELL;
    if(lt==='safe'){
      ctx.fillStyle=row===0?'#002200':'#001800';ctx.fillRect(0,y,W,CELL);
      ctx.strokeStyle='rgba(0,255,136,.1)';ctx.lineWidth=1;ctx.beginPath();ctx.moveTo(0,y);ctx.lineTo(W,y);ctx.stroke();
      if(row===0){ctx.fillStyle='rgba(0,255,136,.08)';ctx.fillRect(0,y,W,CELL);ctx.font=`bold ${CELL*.32}px Orbitron`;ctx.fillStyle='rgba(0,255,136,.35)';ctx.textAlign='center';ctx.fillText('⭐ FINISH ⭐',W/2,y+CELL*.65);}
    }else if(lt==='river'){
      ctx.fillStyle='#001428';ctx.fillRect(0,y,W,CELL);
      for(let wx=0;wx<W;wx+=18){ctx.fillStyle=`rgba(0,150,255,${.03+.025*Math.sin(Date.now()/700+wx*.1)})`;ctx.fillRect(wx,y,10,CELL);}
      ctx.strokeStyle='rgba(0,80,200,.25)';ctx.lineWidth=1;ctx.beginPath();ctx.moveTo(0,y);ctx.lineTo(W,y);ctx.stroke();
    }else{
      ctx.fillStyle=row%2===0?'#09090d':'#070708';ctx.fillRect(0,y,W,CELL);
      ctx.strokeStyle='rgba(255,220,0,.12)';ctx.lineWidth=1.5;ctx.setLineDash([CELL*.38,CELL*.28]);
      ctx.beginPath();ctx.moveTo(0,y+CELL/2);ctx.lineTo(W,y+CELL/2);ctx.stroke();ctx.setLineDash([]);
    }
  }
  // logs
  logItems.forEach(l=>{
    ctx.fillStyle='#3d2000';ctx.fillRect(l.x,l.y,l.w,l.h);
    ctx.strokeStyle='#00ff88';ctx.lineWidth=1.5;ctx.shadowBlur=5;ctx.shadowColor='#00ff88';ctx.strokeRect(l.x,l.y,l.w,l.h);ctx.shadowBlur=0;
    ctx.strokeStyle='rgba(80,40,0,.5)';ctx.lineWidth=1;
    for(let gx=l.x+8;gx<l.x+l.w-4;gx+=8){ctx.beginPath();ctx.moveTo(gx,l.y+2);ctx.lineTo(gx,l.y+l.h-2);ctx.stroke();}
  });
  // obstacles
  obstacles.forEach(o=>{
    if(o.type==='enemy'){
      ctx.fillStyle='#100003';ctx.fillRect(o.x,o.y,o.w,o.h);
      ctx.strokeStyle=o.color;ctx.lineWidth=1.5;ctx.shadowBlur=9;ctx.shadowColor=o.color;ctx.strokeRect(o.x,o.y,o.w,o.h);ctx.shadowBlur=0;
      ctx.font=`${CELL*.48}px sans-serif`;ctx.textAlign='center';ctx.fillText('🐕',o.x+o.w/2,o.y+o.h*.72);
    }else{
      ctx.fillStyle='#080808';ctx.fillRect(o.x,o.y,o.w,o.h);
      const gr=ctx.createLinearGradient(o.x,o.y,o.x,o.y+o.h);gr.addColorStop(0,o.color+'55');gr.addColorStop(.5,o.color+'99');gr.addColorStop(1,o.color+'22');
      ctx.fillStyle=gr;ctx.fillRect(o.x,o.y,o.w,o.h);
      ctx.strokeStyle=o.color;ctx.lineWidth=1.2;ctx.shadowBlur=7;ctx.shadowColor=o.color;ctx.strokeRect(o.x,o.y,o.w,o.h);ctx.shadowBlur=0;
      const lc=o.speed>0?'#ffffaa':'#ff3355',rc=o.speed>0?'#ff3355':'#ffffaa';
      ctx.fillStyle=lc;ctx.shadowColor=lc;ctx.shadowBlur=5;ctx.fillRect(o.x+2,o.y+2,4,5);ctx.fillRect(o.x+2,o.y+o.h-7,4,5);
      ctx.fillStyle=rc;ctx.shadowColor=rc;ctx.fillRect(o.x+o.w-6,o.y+2,4,5);ctx.fillRect(o.x+o.w-6,o.y+o.h-7,4,5);
      ctx.shadowBlur=0;
    }
  });
  // coins
  coinItems.forEach(c=>{
    if(c.collected)return;
    const by=Math.sin(c.bob)*3.5;
    ctx.save();ctx.shadowBlur=14;ctx.shadowColor='#ffdd00';
    ctx.fillStyle='#ffd700';ctx.beginPath();ctx.arc(c.x,c.y+by,CELL*.26,0,Math.PI*2);ctx.fill();
    ctx.fillStyle='#fff8a0';ctx.beginPath();ctx.arc(c.x-2,c.y+by-2,CELL*.1,0,Math.PI*2);ctx.fill();
    ctx.fillStyle='#7a4800';ctx.font=`bold ${CELL*.2}px sans-serif`;ctx.textAlign='center';ctx.textBaseline='middle';ctx.fillText('₿',c.x,c.y+by+1);
    ctx.restore();
  });
  // player dog
  const show=!invincible||Math.floor(flashTimer/4)%2===0;
  if(show){
    ctx.save();
    if(invincible&&flashTimer>0)ctx.globalAlpha=.55;
    ctx.shadowBlur=14;ctx.shadowColor='#00ff88';
    // square frame for dog
    ctx.fillStyle='#7dffb3';ctx.fillRect(dog.x+CELL*.05,dog.y+CELL*.05,CELL*.9,CELL*.9);
    ctx.imageSmoothingEnabled=false;
    ctx.drawImage(playerImg,dog.x+CELL*.05,dog.y+CELL*.05,CELL*.9,CELL*.9);
    ctx.strokeStyle='#00ff88';ctx.lineWidth=2;ctx.strokeRect(dog.x+CELL*.05,dog.y+CELL*.05,CELL*.9,CELL*.9);
    ctx.restore();
    ctx.font=`bold ${CELL*.16}px Orbitron`;ctx.fillStyle='#00ff88';ctx.textAlign='center';ctx.shadowBlur=4;ctx.shadowColor='#00ff88';
    ctx.fillText('#'+playerNFT,dog.x+CELL/2,dog.y+CELL+CELL*.18);ctx.shadowBlur=0;
  }
  updateHUD();
}

// ══════════════════════════════════════════
//  HUD
// ══════════════════════════════════════════
function updateHUD(){
  document.getElementById('hudScore').textContent=score;
  document.getElementById('hudLevel').textContent=level;
  document.getElementById('hudCoins').textContent=coins;
  document.getElementById('hudLives').textContent='🐾'.repeat(Math.max(0,lives));
  document.getElementById('hudBest').textContent=Math.max(score,bestScore);
}

// ══════════════════════════════════════════
//  LEVEL BANNER
// ══════════════════════════════════════════
function showLvlBanner(){
  const b=document.getElementById('lvlBanner');
  document.getElementById('lvlNum').textContent='LEVEL '+level;
  b.classList.add('show');setTimeout(()=>b.classList.remove('show'),1900);
}

// ══════════════════════════════════════════
//  DPAD
// ══════════════════════════════════════════
const dState={};
function dpadOn(d,e){e.preventDefault();if(dState[d])return;dState[d]=true;document.getElementById({U:'bU',D:'bD',L:'bL',R:'bR'}[d]).classList.add('on');moveDog(d);}
function dpadOff(d){dState[d]=false;document.getElementById({U:'bU',D:'bD',L:'bL',R:'bR'}[d]).classList.remove('on');}
function moveDog(d){
  if(!gameRunning)return;
  let nr=dog.row,nc=dog.col;
  if(d==='U')nr=Math.max(0,dog.row-1);
  if(d==='D')nr=Math.min(ROWS_G-1,dog.row+1);
  if(d==='L')nc=Math.max(0,dog.col-1);
  if(d==='R')nc=Math.min(COLS_G-1,dog.col+1);
  dog.row=nr;dog.col=nc;dog.x=nc*CELL;dog.y=nr*CELL;
  if(d==='U')score+=10;updateHUD();
}
document.addEventListener('keydown',e=>{
  const m={ArrowUp:'U',ArrowDown:'D',ArrowLeft:'L',ArrowRight:'R',w:'U',s:'D',a:'L',d:'R'};
  if(m[e.key]){e.preventDefault();moveDog(m[e.key]);}
});

// ══════════════════════════════════════════
//  GAME OVER
// ══════════════════════════════════════════
function gameOver(){
  if(score>bestScore){bestScore=score;localStorage.setItem('dogger_best',bestScore);}
  saveToLB();
  const rank=getRank();
  document.getElementById('goScore').textContent=score;
  document.getElementById('goLevel').textContent=level;
  document.getElementById('goCoins').textContent=coins;
  document.getElementById('goDog').textContent='#'+playerNFT;
  document.getElementById('goRank').textContent='#'+rank;
  document.getElementById('goBest').textContent=bestScore;
  document.getElementById('sh-score').textContent=score;
  document.getElementById('sh-dog').textContent='#'+playerNFT;
  document.getElementById('sh-lvl').textContent=level;
  document.getElementById('sh-rank').textContent='#'+rank;
  // copy pfp to game-over canvas
  const gp=document.getElementById('goPfp'),gpx=gp.getContext('2d');
  gpx.fillStyle='#7dffb3';gpx.fillRect(0,0,70,70);
  gpx.imageSmoothingEnabled=false;gpx.drawImage(playerImg,0,0,70,70);
  showScreen('goScreen');
}

// ══════════════════════════════════════════
//  LEADERBOARD
// ══════════════════════════════════════════
function saveToLB(){
  leaderboard=leaderboard.filter(e=>!(e.nft===playerNFT&&e.name===playerName));
  leaderboard.push({name:playerName.substring(0,16),nft:playerNFT,score,level,coins,pfp:customPfp||DEFAULT_DOG,ts:Date.now()});
  leaderboard.sort((a,b)=>b.score-a.score);leaderboard=leaderboard.slice(0,20);
  localStorage.setItem('dogger_lb',JSON.stringify(leaderboard));
}
function getRank(){const i=leaderboard.findIndex(e=>e.nft===playerNFT&&e.score===score);return i===-1?leaderboard.length:i+1;}
function showLB(){renderLB();showScreen('lbScreen');}
function renderLB(){
  const lb=document.getElementById('lbList');
  if(!leaderboard.length){lb.innerHTML='<div style="text-align:center;color:rgba(0,255,136,.4);font-size:11px;letter-spacing:2px;padding:20px">NO SCORES YET — BE FIRST! 🐾</div>';return;}
  const rc=['g','s','b'];
  lb.innerHTML=leaderboard.slice(0,10).map((e,i)=>{
    const isMe=e.nft===playerNFT&&e.name===playerName;
    return `<div class="lb-row${isMe?' me':''}">
      <span class="lb-rank ${rc[i]||''}">${i===0?'🥇':i===1?'🥈':i===2?'🥉':'#'+(i+1)}</span>
      <img class="lb-dog" src="${e.pfp}" alt="dog"/>
      <div class="lb-info"><div class="lb-name">${e.name} <span style="color:var(--nc);font-size:9px">#${e.nft}</span></div><div class="lb-sub">LVL ${e.level} · ${e.coins} COINS</div></div>
      <span class="lb-pts">${e.score}</span>
    </div>`;
  }).join('');
}

// ══════════════════════════════════════════
//  SHARE TO X
// ══════════════════════════════════════════
function shareX(){
  const rank=getRank();
  const txt=`🐾 I scored ${score} pts as Doginal Dog #${playerNFT} in DOGGER!\nLevel ${level} · ${coins} coins · Rank #${rank}\n\nPlay free: https://andmetax.glitch.me\n\n#Dogger #AndMetaX #DoginalDog #XRP`;
  window.open('https://twitter.com/intent/tweet?text='+encodeURIComponent(txt),'_blank');
}

// ══════════════════════════════════════════
//  SCREEN MANAGEMENT
// ══════════════════════════════════════════
function showScreen(id){
  document.querySelectorAll('.screen').forEach(s=>s.classList.add('hidden'));
  document.getElementById(id).classList.remove('hidden');
  if(id==='gameScreen')setTimeout(resizeGame,60);
}
// init
showScreen('titleScreen');
setTimeout(drawPreview,150);
</script>
</body>
</html>

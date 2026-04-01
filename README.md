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

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SA Kicker — South Africa's #1 Football News</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=Barlow+Condensed:wght@600;700&family=Barlow:wght@300;400;500;600&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
<style>
:root{
  --ink:#0A0A0F;
  --surface:#13131C;
  --card:#1A1A27;
  --border:#2A2A3D;
  --lime:#C8F135;
  --cyan:#00E5C8;
  --orange:#FF5E1F;
  --text:#F2F0F8;
  --muted:#7C7A94;
  --red:#FF3B3B;
  --blue:#3B7EFF;
  --gold:#E8C84B;
}
*{margin:0;padding:0;box-sizing:border-box;}
body{background:var(--ink);color:var(--text);font-family:'Barlow',sans-serif;overflow-x:hidden;}

/* ── ANIMATED BACKGROUND ── */
.bg-canvas{position:fixed;top:0;left:0;width:100%;height:100%;z-index:0;pointer-events:none;overflow:hidden;}
.bg-canvas::before{
  content:'';position:absolute;inset:0;
  background:
    radial-gradient(ellipse 80% 60% at 15% 20%, rgba(0,229,200,.07) 0%, transparent 60%),
    radial-gradient(ellipse 60% 50% at 85% 75%, rgba(200,241,53,.06) 0%, transparent 55%),
    radial-gradient(ellipse 50% 40% at 50% 50%, rgba(255,94,31,.04) 0%, transparent 60%);
  animation:bgShift 18s ease-in-out infinite alternate;
}
.bg-canvas::after{
  content:'';position:absolute;inset:0;
  background-image:repeating-linear-gradient(0deg,transparent,transparent 59px,rgba(255,255,255,.018) 60px),
                   repeating-linear-gradient(90deg,transparent,transparent 59px,rgba(255,255,255,.018) 60px);
  background-size:60px 60px;
}
@keyframes bgShift{
  0%{background:radial-gradient(ellipse 80% 60% at 15% 20%,rgba(0,229,200,.07) 0%,transparent 60%),radial-gradient(ellipse 60% 50% at 85% 75%,rgba(200,241,53,.06) 0%,transparent 55%),radial-gradient(ellipse 50% 40% at 50% 50%,rgba(255,94,31,.04) 0%,transparent 60%);}
  33%{background:radial-gradient(ellipse 70% 55% at 70% 15%,rgba(200,241,53,.08) 0%,transparent 60%),radial-gradient(ellipse 65% 45% at 20% 80%,rgba(0,229,200,.06) 0%,transparent 55%),radial-gradient(ellipse 45% 50% at 50% 50%,rgba(59,126,255,.04) 0%,transparent 60%);}
  66%{background:radial-gradient(ellipse 75% 50% at 85% 40%,rgba(255,94,31,.06) 0%,transparent 60%),radial-gradient(ellipse 55% 60% at 25% 30%,rgba(59,126,255,.07) 0%,transparent 55%),radial-gradient(ellipse 50% 40% at 60% 70%,rgba(200,241,53,.04) 0%,transparent 60%);}
  100%{background:radial-gradient(ellipse 80% 60% at 50% 85%,rgba(0,229,200,.07) 0%,transparent 60%),radial-gradient(ellipse 60% 50% at 80% 20%,rgba(255,94,31,.06) 0%,transparent 55%),radial-gradient(ellipse 50% 40% at 20% 50%,rgba(200,241,53,.05) 0%,transparent 60%);}
}
.orb{position:absolute;border-radius:50%;filter:blur(80px);opacity:.5;animation:orbFloat linear infinite;}
.orb1{width:400px;height:400px;background:radial-gradient(circle,rgba(0,229,200,.18),transparent);top:-100px;left:-100px;animation-duration:25s;}
.orb2{width:500px;height:500px;background:radial-gradient(circle,rgba(200,241,53,.12),transparent);bottom:-150px;right:-100px;animation-duration:32s;animation-delay:-10s;}
.orb3{width:350px;height:350px;background:radial-gradient(circle,rgba(255,94,31,.1),transparent);top:40%;left:60%;animation-duration:20s;animation-delay:-5s;}
@keyframes orbFloat{0%{transform:translate(0,0) scale(1);}25%{transform:translate(40px,-60px) scale(1.08);}50%{transform:translate(-30px,40px) scale(.95);}75%{transform:translate(60px,20px) scale(1.05);}100%{transform:translate(0,0) scale(1);}}

/* ── CONTENT LAYER ── */
.layer{position:relative;z-index:1;}

/* ── TICKER ── */
.ticker-wrap{background:var(--lime);overflow:hidden;height:36px;display:flex;align-items:center;position:relative;z-index:100;}
.ticker-label{background:var(--ink);color:var(--lime);font-family:'Space Mono',monospace;font-size:10px;letter-spacing:2px;padding:0 16px;height:100%;display:flex;align-items:center;flex-shrink:0;gap:6px;z-index:2;}
.ticker-label .dot{width:7px;height:7px;background:var(--red);border-radius:50%;animation:blink 1s infinite;}
@keyframes blink{0%,100%{opacity:1;}50%{opacity:0;}}
.ticker-track{display:flex;animation:ticker 55s linear infinite;white-space:nowrap;}
.ticker-track span{font-size:12px;padding:0 36px;color:var(--ink);font-weight:600;font-family:'Barlow Condensed',sans-serif;letter-spacing:.5px;}
.ticker-track span::before{content:"▶";margin-right:10px;font-size:9px;}
@keyframes ticker{0%{transform:translateX(0);}100%{transform:translateX(-50%);}}

/* ── HEADER ── */
header{background:rgba(10,10,15,.85);backdrop-filter:blur(20px);border-bottom:1px solid var(--border);padding:0 40px;position:sticky;top:0;z-index:100;display:flex;align-items:center;justify-content:space-between;height:62px;}
.logo{font-family:'Syne',sans-serif;font-size:32px;font-weight:800;letter-spacing:-1px;color:var(--text);cursor:pointer;}
.logo span{color:var(--lime);}
nav{display:flex;gap:4px;align-items:center;}
nav a{font-size:11px;letter-spacing:1.5px;text-transform:uppercase;color:var(--muted);text-decoration:none;font-weight:600;font-family:'Barlow Condensed',sans-serif;padding:6px 12px;border-radius:4px;transition:all .2s;cursor:pointer;}
nav a:hover,nav a.active{color:var(--lime);background:rgba(200,241,53,.08);}
.nav-cta{background:var(--lime);color:var(--ink)!important;font-weight:700!important;border-radius:4px;padding:7px 16px!important;}
.nav-cta:hover{background:#d8ff4a;transform:translateY(-1px);}

/* PAGES */
.page{display:none;}.page.active{display:block;}

/* ── HERO ── */
.hero{display:grid;grid-template-columns:1fr 380px;max-width:1300px;margin:40px auto;padding:0 40px;gap:0;}
.hero-main{position:relative;overflow:hidden;cursor:pointer;}
.hero-img-placeholder{width:100%;height:520px;background:linear-gradient(135deg,#07191A 0%,#0B1F1A 40%,#0D1020 100%);position:relative;display:flex;align-items:flex-end;overflow:hidden;}
.hero-pitch{position:absolute;bottom:0;left:0;right:0;height:220px;background:repeating-linear-gradient(90deg,rgba(0,229,200,.06) 0px,rgba(0,229,200,.06) 40px,rgba(0,180,160,.06) 40px,rgba(0,180,160,.06) 80px);opacity:.7;}
.hero-grid-bg{position:absolute;inset:0;background-image:repeating-linear-gradient(0deg,transparent,transparent 39px,rgba(0,229,200,.04) 40px),repeating-linear-gradient(90deg,transparent,transparent 39px,rgba(0,229,200,.04) 40px);}
.ball-icon{position:absolute;top:50%;left:50%;transform:translate(-50%,-60%);font-size:120px;opacity:.08;animation:float 5s ease-in-out infinite;}
@keyframes float{0%,100%{transform:translate(-50%,-60%) translateY(0);}50%{transform:translate(-50%,-60%) translateY(-20px);}}
.hero-badge{position:absolute;top:20px;left:20px;background:var(--red);color:#fff;font-family:'Space Mono',monospace;font-size:10px;letter-spacing:1.5px;padding:5px 12px;z-index:3;display:flex;align-items:center;gap:6px;}
.hero-badge .dot{width:6px;height:6px;background:#fff;border-radius:50%;animation:blink 1s infinite;}
.hero-overlay{position:absolute;bottom:0;left:0;right:0;background:linear-gradient(to top,rgba(10,10,15,.97) 0%,rgba(10,10,15,.5) 55%,transparent 100%);padding:32px 28px;z-index:2;}
.hero-cat{font-family:'Space Mono',monospace;font-size:10px;letter-spacing:2px;color:var(--cyan);margin-bottom:12px;text-transform:uppercase;}
.hero-title{font-family:'Syne',sans-serif;font-size:36px;font-weight:800;line-height:1.05;margin-bottom:14px;letter-spacing:-0.5px;}
.hero-excerpt{font-size:14px;color:rgba(242,240,248,.7);line-height:1.65;margin-bottom:18px;}
.hero-meta{display:flex;align-items:center;gap:16px;font-size:12px;color:var(--muted);}
.hero-meta .author{color:var(--lime);font-weight:600;}
.hero-sidebar{border-left:1px solid var(--border);padding-left:24px;display:flex;flex-direction:column;}
.side-article{padding:20px 0;border-bottom:1px solid var(--border);cursor:pointer;transition:all .2s;}
.side-article:hover{transform:translateX(4px);}
.side-article:last-child{border-bottom:none;}
.side-num{font-family:'Syne',sans-serif;font-size:44px;font-weight:800;color:rgba(200,241,53,.1);line-height:1;margin-bottom:6px;}
.side-cat{font-size:10px;letter-spacing:2px;text-transform:uppercase;color:var(--cyan);font-family:'Space Mono',monospace;margin-bottom:6px;}
.side-title{font-family:'Barlow Condensed',sans-serif;font-size:17px;font-weight:700;line-height:1.3;margin-bottom:8px;letter-spacing:.2px;}
.side-meta{font-size:11px;color:var(--muted);}

/* ── STATS BANNER ── */
.stats-banner{background:linear-gradient(135deg,rgba(0,229,200,.12),rgba(200,241,53,.08));border-top:1px solid rgba(0,229,200,.2);border-bottom:1px solid rgba(200,241,53,.15);padding:0 40px;max-width:1300px;margin:0 auto 40px;}
.stats-inner{display:grid;grid-template-columns:repeat(4,1fr);}
.stat-item{padding:18px 24px;border-right:1px solid rgba(255,255,255,.07);transition:background .2s;}
.stat-item:last-child{border-right:none;}
.stat-item:hover{background:rgba(255,255,255,.03);}
.stat-num{font-family:'Syne',sans-serif;font-size:34px;font-weight:800;color:var(--lime);line-height:1;margin-bottom:4px;}
.stat-label{font-size:11px;letter-spacing:.5px;opacity:.75;}
.stat-source{font-size:10px;opacity:.4;margin-top:3px;}

/* ── SECTION ── */
.section{max-width:1300px;margin:0 auto 50px;padding:0 40px;}
.section-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:24px;padding-bottom:14px;border-bottom:1px solid var(--border);}
.section-title{font-family:'Barlow Condensed',sans-serif;font-size:22px;font-weight:700;letter-spacing:2px;text-transform:uppercase;position:relative;padding-left:16px;}
.section-title::before{content:'';position:absolute;left:0;top:50%;transform:translateY(-50%);width:4px;height:100%;background:var(--lime);}
.see-all{font-size:11px;letter-spacing:1.5px;text-transform:uppercase;color:var(--cyan);text-decoration:none;border-bottom:1px solid rgba(0,229,200,.3);padding-bottom:2px;font-family:'Space Mono',monospace;}
.articles-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:24px;}
.card{background:var(--card);border:1px solid var(--border);cursor:pointer;transition:transform .25s,border-color .25s,box-shadow .25s;overflow:hidden;}
.card:hover{transform:translateY(-4px);border-color:rgba(0,229,200,.3);box-shadow:0 8px 32px rgba(0,229,200,.07);}
.card-img{height:190px;position:relative;overflow:hidden;}
.bg-chiefs{background:linear-gradient(135deg,#1a0e00 0%,#3d2200 100%);}
.bg-pirates{background:linear-gradient(135deg,#000 0%,#0a0d1a 60%,#0d0010 100%);}
.bg-sundowns{background:linear-gradient(135deg,#001a0d 0%,#003d1a 60%,#0d1a00 100%);}
.bg-bafana{background:linear-gradient(135deg,#000d1a 0%,#001a3d 60%,#003d2e 100%);}
.bg-psl{background:linear-gradient(135deg,#1a0000 0%,#2d0010 60%,#1a0020 100%);}
.bg-transfer{background:linear-gradient(135deg,#0a0d1a 0%,#001d2d 100%);}
.card-team-icon{position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);font-size:64px;opacity:.12;}
.card-badge{position:absolute;bottom:10px;left:10px;background:var(--lime);color:var(--ink);font-family:'Space Mono',monospace;font-size:9px;letter-spacing:1.5px;padding:3px 8px;text-transform:uppercase;font-weight:700;}
.card-badge.green{background:var(--cyan);color:var(--ink);}
.card-badge.red{background:var(--red);color:#fff;}
.card-body{padding:18px;}
.card-cat{font-size:10px;letter-spacing:2px;text-transform:uppercase;color:var(--cyan);font-family:'Space Mono',monospace;margin-bottom:8px;}
.card-title{font-family:'Barlow Condensed',sans-serif;font-size:20px;font-weight:700;line-height:1.25;margin-bottom:10px;letter-spacing:.2px;}
.card-excerpt{font-size:13px;color:var(--muted);line-height:1.6;margin-bottom:14px;}
.card-meta{display:flex;justify-content:space-between;font-size:11px;color:#555;padding-top:12px;border-top:1px solid var(--border);}

/* ── LIVE NEWS PANEL ── */
.live-news-panel{max-width:1300px;margin:0 auto 50px;padding:0 40px;}
.lnp-inner{background:var(--card);border:1px solid var(--border);border-left:4px solid var(--lime);overflow:hidden;}
.lnp-header{background:rgba(200,241,53,.07);padding:16px 24px;display:flex;align-items:center;justify-content:space-between;border-bottom:1px solid var(--border);}
.lnp-title{font-family:'Syne',sans-serif;font-size:16px;font-weight:800;display:flex;align-items:center;gap:10px;}
.lnp-title .pulse{width:8px;height:8px;background:var(--lime);border-radius:50%;animation:blink 1.2s infinite;}
.lnp-subtitle{font-size:12px;color:var(--muted);font-family:'Space Mono',monospace;}
.lnp-refresh{background:rgba(200,241,53,.1);border:1px solid rgba(200,241,53,.25);color:var(--lime);font-family:'Space Mono',monospace;font-size:10px;letter-spacing:1px;padding:6px 14px;cursor:pointer;transition:all .2s;text-transform:uppercase;}
.lnp-refresh:hover{background:rgba(200,241,53,.2);}
.lnp-refresh:disabled{opacity:.5;cursor:not-allowed;}
.lnp-body{padding:24px;min-height:120px;}
.lnp-loading{display:flex;align-items:center;gap:12px;color:var(--muted);font-size:13px;}
.spinner{width:18px;height:18px;border:2px solid var(--border);border-top-color:var(--lime);border-radius:50%;animation:spin .8s linear infinite;}
@keyframes spin{to{transform:rotate(360deg);}}
.lnp-items{display:flex;flex-direction:column;gap:16px;}
.lnp-item{display:grid;grid-template-columns:auto 1fr;gap:16px;padding-bottom:16px;border-bottom:1px solid var(--border);}
.lnp-item:last-child{border-bottom:none;padding-bottom:0;}
.lnp-badge-wrap{display:flex;flex-direction:column;align-items:center;gap:4px;padding-top:3px;}
.lnp-icon{width:32px;height:32px;background:rgba(200,241,53,.1);border-radius:6px;display:flex;align-items:center;justify-content:center;font-size:16px;flex-shrink:0;}
.lnp-tag{font-family:'Space Mono',monospace;font-size:8px;letter-spacing:1px;color:var(--cyan);text-transform:uppercase;}
.lnp-headline{font-family:'Barlow Condensed',sans-serif;font-size:18px;font-weight:700;line-height:1.2;margin-bottom:5px;letter-spacing:.2px;}
.lnp-summary{font-size:13px;color:var(--muted);line-height:1.55;}
.lnp-timestamp{font-size:11px;color:var(--muted);font-family:'Space Mono',monospace;margin-top:6px;}
.lnp-error{color:var(--red);font-size:13px;display:flex;align-items:center;gap:8px;}

/* ── RESEARCH BOX ── */
.research-box{background:linear-gradient(135deg,rgba(0,229,200,.06) 0%,rgba(200,241,53,.04) 100%);border:1px solid rgba(0,229,200,.2);border-left:4px solid var(--cyan);padding:28px 40px;margin:0 auto 50px;max-width:1300px;position:relative;overflow:hidden;}
.research-label{font-family:'Space Mono',monospace;font-size:10px;letter-spacing:2.5px;color:var(--cyan);margin-bottom:12px;display:flex;align-items:center;gap:10px;text-transform:uppercase;}
.research-label::after{content:'';flex:1;height:1px;background:rgba(0,229,200,.2);}
.research-text{font-family:'Barlow',sans-serif;font-size:18px;line-height:1.65;color:rgba(242,240,248,.85);max-width:1000px;font-weight:300;}
.research-text strong{color:var(--lime);font-weight:600;}
.research-source{margin-top:14px;font-size:12px;color:var(--muted);}

/* ── TWO-COL ── */
.two-col{display:grid;grid-template-columns:1fr 360px;gap:32px;max-width:1300px;margin:0 auto 50px;padding:0 40px;}
.opinion-card{background:linear-gradient(135deg,rgba(0,229,200,.1),rgba(200,241,53,.06));border:1px solid rgba(0,229,200,.2);padding:28px;position:relative;overflow:hidden;cursor:pointer;}
.opinion-label{font-family:'Space Mono',monospace;font-size:10px;letter-spacing:2px;color:var(--cyan);margin-bottom:14px;text-transform:uppercase;}
.opinion-title{font-family:'Syne',sans-serif;font-size:22px;font-weight:800;line-height:1.15;margin-bottom:14px;letter-spacing:-.3px;}
.opinion-body{font-size:14px;line-height:1.7;opacity:.8;margin-bottom:20px;}
.opinion-author{display:flex;align-items:center;gap:12px;}
.author-avatar{width:42px;height:42px;border-radius:8px;background:var(--lime);display:flex;align-items:center;justify-content:center;font-family:'Syne',sans-serif;font-size:16px;font-weight:800;color:var(--ink);flex-shrink:0;}
.author-name{font-weight:600;font-size:14px;}.author-role{font-size:11px;opacity:.55;}
.top-stories{display:flex;flex-direction:column;}
.top-story{display:flex;gap:14px;padding:14px 0;border-bottom:1px solid var(--border);cursor:pointer;transition:transform .2s;}
.top-story:hover{transform:translateX(4px);}
.top-story:last-child{border-bottom:none;}
.story-num{font-family:'Syne',sans-serif;font-size:28px;font-weight:800;color:rgba(200,241,53,.18);flex-shrink:0;width:32px;line-height:1;padding-top:2px;}
.story-cat{font-size:9px;letter-spacing:2px;text-transform:uppercase;color:var(--cyan);font-family:'Space Mono',monospace;margin-bottom:4px;}
.story-title{font-family:'Barlow Condensed',sans-serif;font-size:16px;font-weight:700;line-height:1.3;margin-bottom:4px;}
.story-meta{font-size:11px;color:var(--muted);}

/* ── SHARED FEATURE STYLES ── */
.feature-page{max-width:1300px;margin:0 auto;padding:40px;}
.page-heading{font-family:'Syne',sans-serif;font-size:52px;font-weight:800;letter-spacing:-2px;color:var(--text);margin-bottom:8px;}
.page-heading span{color:var(--lime);}
.page-sub{font-size:14px;color:var(--muted);margin-bottom:32px;}
.ftabs{display:flex;gap:0;border-bottom:2px solid var(--border);margin-bottom:28px;}
.ftab{padding:10px 22px;font-family:'Barlow Condensed',sans-serif;font-size:13px;font-weight:700;letter-spacing:1.5px;text-transform:uppercase;color:var(--muted);cursor:pointer;border-bottom:2px solid transparent;margin-bottom:-2px;transition:all .2s;}
.ftab.active,.ftab:hover{color:var(--lime);border-bottom-color:var(--lime);}

/* ── SCORES ── */
.scores-list{display:flex;flex-direction:column;gap:3px;}
.match-row{background:var(--card);border:1px solid var(--border);padding:16px 22px;display:grid;grid-template-columns:150px 1fr 100px 1fr 140px;align-items:center;gap:12px;transition:border-color .2s;cursor:pointer;}
.match-row:hover{border-color:rgba(200,241,53,.2);}
.match-time{font-family:'Space Mono',monospace;font-size:11px;color:var(--muted);}
.live-row{display:flex;align-items:center;gap:5px;color:var(--red);}
.live-dot{width:7px;height:7px;background:var(--red);border-radius:50%;animation:blink 1s infinite;display:inline-block;}
.team-name{font-size:14px;font-weight:600;font-family:'Barlow Condensed',sans-serif;letter-spacing:.5px;}
.team-home{text-align:right;}.team-away{text-align:left;}
.score-display{text-align:center;font-family:'Syne',sans-serif;font-size:28px;font-weight:800;color:var(--lime);background:rgba(200,241,53,.06);padding:4px 12px;}
.score-display.live{color:var(--red);background:rgba(255,59,59,.08);}
.match-comp{font-size:11px;color:var(--muted);text-align:right;font-family:'Space Mono',monospace;}
.live-badge{display:inline-block;background:var(--red);color:#fff;font-size:9px;font-family:'Space Mono',monospace;letter-spacing:1.5px;padding:2px 6px;margin-left:5px;}
.date-div{padding:12px 0 6px;font-family:'Space Mono',monospace;font-size:11px;letter-spacing:2px;color:var(--muted);text-transform:uppercase;border-bottom:1px solid var(--border);margin-bottom:8px;}

/* ── STANDINGS ── */
.s-table{width:100%;border-collapse:collapse;background:var(--card);border:1px solid var(--border);}
.s-table th{background:var(--surface);font-family:'Space Mono',monospace;font-size:10px;letter-spacing:2px;text-transform:uppercase;color:var(--muted);padding:14px 14px;text-align:center;border-bottom:2px solid var(--border);}
.s-table th:nth-child(1),.s-table th:nth-child(2){text-align:left;}
.s-table td{padding:13px 14px;text-align:center;border-bottom:1px solid rgba(42,42,61,.6);font-size:14px;font-family:'Barlow',sans-serif;}
.s-table td:nth-child(1){font-family:'Space Mono',monospace;color:var(--muted);font-size:13px;}
.s-table td:nth-child(2){text-align:left;font-weight:600;}
.s-table tr:hover td{background:rgba(200,241,53,.025);}
.s-table tr.champ td{border-left:3px solid var(--lime);}
.s-table tr.conf td{border-left:3px solid var(--cyan);}
.s-table tr.rel td{border-left:3px solid var(--red);}
.pts{font-family:'Syne',sans-serif;font-size:20px;font-weight:800;color:var(--lime);}
.form-row{display:flex;gap:3px;justify-content:center;}
.fw{width:18px;height:18px;border-radius:3px;background:rgba(0,229,200,.4);color:#fff;font-size:9px;font-weight:700;display:flex;align-items:center;justify-content:center;font-family:'Space Mono',monospace;}
.fd{background:#444;}.fl{background:rgba(255,59,59,.5);}
.crest{display:inline-flex;align-items:center;gap:10px;}
.cdot{width:10px;height:10px;border-radius:50%;flex-shrink:0;}
.s-legend{display:flex;gap:24px;margin-top:14px;font-size:12px;color:var(--muted);}
.sl-item{display:flex;align-items:center;gap:8px;}
.sl-bar{width:12px;height:12px;}

/* ── FIXTURES ── */
.fix-filter{display:flex;gap:10px;margin-bottom:28px;flex-wrap:wrap;}
.fbtn{padding:8px 18px;border:1px solid var(--border);background:transparent;color:var(--muted);font-family:'Barlow Condensed',sans-serif;font-size:11px;font-weight:700;letter-spacing:1.5px;text-transform:uppercase;cursor:pointer;transition:all .2s;}
.fbtn.active,.fbtn:hover{border-color:var(--lime);color:var(--lime);background:rgba(200,241,53,.05);}
.fix-week{margin-bottom:32px;}
.week-hdr{font-family:'Space Mono',monospace;font-size:11px;letter-spacing:2px;text-transform:uppercase;color:var(--lime);padding:10px 0;border-bottom:1px solid var(--border);margin-bottom:12px;}
.fix-card{background:var(--card);border:1px solid var(--border);padding:18px 22px;display:grid;grid-template-columns:80px 1fr auto 1fr 180px;align-items:center;gap:14px;margin-bottom:4px;transition:border-color .2s;cursor:pointer;}
.fix-card:hover{border-color:rgba(200,241,53,.2);}
.fix-time{font-family:'Space Mono',monospace;font-size:13px;color:var(--lime);}
.fix-team{font-size:15px;font-weight:700;font-family:'Barlow Condensed',sans-serif;}
.fix-home{text-align:right;}
.fix-vs{font-family:'Syne',sans-serif;font-size:20px;font-weight:800;color:var(--border);text-align:center;}
.fix-info{text-align:right;font-size:11px;color:var(--muted);line-height:1.8;}
.remind-btn{display:inline-flex;align-items:center;gap:5px;font-size:10px;letter-spacing:1px;color:var(--lime);cursor:pointer;border:1px solid rgba(200,241,53,.2);padding:3px 8px;transition:all .2s;font-family:'Space Mono',monospace;}
.remind-btn:hover{background:rgba(200,241,53,.08);}

/* ── PLAYER STATS ── */
.top-stat-cards{display:grid;grid-template-columns:repeat(4,1fr);gap:16px;margin-bottom:32px;}
.tsc{background:var(--card);border:1px solid var(--border);padding:20px;text-align:center;position:relative;overflow:hidden;}
.tsc::before{content:'';position:absolute;top:0;left:0;right:0;height:3px;background:var(--lime);}
.tsc-label{font-family:'Space Mono',monospace;font-size:9px;letter-spacing:2px;color:var(--muted);margin-bottom:10px;text-transform:uppercase;}
.tsc-player{font-family:'Barlow Condensed',sans-serif;font-weight:700;font-size:17px;margin-bottom:4px;}
.tsc-club{font-size:11px;color:var(--muted);margin-bottom:8px;}
.tsc-val{font-family:'Syne',sans-serif;font-size:44px;font-weight:800;color:var(--lime);line-height:1;}
.tsc-unit{font-size:12px;color:var(--muted);}
.p-table{width:100%;border-collapse:collapse;}
.p-table th{background:rgba(0,229,200,.06);font-family:'Space Mono',monospace;font-size:10px;letter-spacing:2px;text-transform:uppercase;color:var(--lime);padding:12px 14px;text-align:center;border-bottom:1px solid var(--border);cursor:pointer;transition:background .2s;}
.p-table th:hover{background:rgba(0,229,200,.12);}
.p-table th:nth-child(1),.p-table th:nth-child(2),.p-table th:nth-child(3){text-align:left;}
.p-table td{padding:13px 14px;border-bottom:1px solid rgba(42,42,61,.5);font-size:14px;text-align:center;}
.p-table td:nth-child(1){font-family:'Space Mono',monospace;color:var(--muted);font-size:15px;font-weight:700;}
.p-table td:nth-child(2){text-align:left;font-weight:600;font-family:'Barlow Condensed',sans-serif;}
.p-table td:nth-child(3){text-align:left;font-size:12px;color:var(--muted);}
.p-table tr:hover td{background:rgba(200,241,53,.025);}
.stat-hl{font-family:'Syne',sans-serif;font-size:22px;font-weight:800;color:var(--lime);}
.bar-wrap{display:flex;align-items:center;gap:8px;}
.bar-bg{height:6px;background:rgba(200,241,53,.1);border-radius:3px;flex:1;overflow:hidden;}
.bar-fill{height:100%;background:var(--lime);border-radius:3px;}
.p-av{width:32px;height:32px;border-radius:6px;display:inline-flex;align-items:center;justify-content:center;font-family:'Syne',sans-serif;font-size:12px;font-weight:800;color:var(--ink);margin-right:8px;flex-shrink:0;}
.p-name-cell{display:flex;align-items:center;}

/* ── TIMELINE ── */
.match-sel{display:grid;grid-template-columns:repeat(3,1fr);gap:14px;margin-bottom:36px;}
.msc{background:var(--card);border:2px solid var(--border);padding:16px 18px;cursor:pointer;transition:all .2s;}
.msc:hover,.msc.active{border-color:var(--lime);background:rgba(200,241,53,.04);}
.msc-comp{font-size:10px;letter-spacing:1.5px;text-transform:uppercase;color:var(--muted);margin-bottom:8px;font-family:'Space Mono',monospace;}
.msc-row{display:flex;justify-content:space-between;align-items:center;margin-bottom:4px;}
.msc-team{font-weight:700;font-size:14px;font-family:'Barlow Condensed',sans-serif;}
.msc-score{font-family:'Syne',sans-serif;font-size:28px;font-weight:800;color:var(--lime);}
.msc-date{font-size:11px;color:var(--muted);font-family:'Space Mono',monospace;}
.tw{background:var(--card);border:1px solid var(--border);}
.tw-hdr{background:var(--surface);padding:20px 28px;border-bottom:1px solid var(--border);display:flex;justify-content:space-between;align-items:center;}
.tw-sb{text-align:center;}
.tw-teams{display:flex;align-items:center;gap:24px;justify-content:center;margin-bottom:6px;}
.tw-tn{font-weight:700;font-size:17px;min-width:150px;font-family:'Barlow Condensed',sans-serif;}
.tw-home{text-align:right;}.tw-away{text-align:left;}
.tw-score{font-family:'Syne',sans-serif;font-size:52px;font-weight:800;color:var(--lime);line-height:1;padding:0 20px;}
.tw-info{font-size:12px;color:var(--muted);text-align:center;font-family:'Space Mono',monospace;}
.tw-status{font-family:'Space Mono',monospace;font-size:10px;letter-spacing:2px;}
.tw-status.live{color:var(--red);}
.match-stats-section{padding:20px 28px;border-bottom:1px solid var(--border);}
.mss-title{font-family:'Space Mono',monospace;font-size:10px;letter-spacing:2px;text-transform:uppercase;color:var(--muted);margin-bottom:16px;}
.mstat{display:grid;grid-template-columns:70px 1fr 70px;align-items:center;gap:8px;margin-bottom:10px;}
.msv{font-size:14px;font-weight:700;}
.msv.h{text-align:right;}.msv.a{text-align:left;}
.msn{font-size:11px;color:var(--muted);text-align:center;font-family:'Space Mono',monospace;letter-spacing:1px;text-transform:uppercase;}
.ms-bars{display:flex;height:5px;border-radius:3px;overflow:hidden;margin-bottom:10px;}
.ms-bh{background:var(--lime);height:100%;}
.ms-ba{background:#333;height:100%;}
.tl-section{padding:24px 28px;}
.tl-title{font-family:'Space Mono',monospace;font-size:11px;letter-spacing:2px;text-transform:uppercase;color:var(--muted);margin-bottom:18px;}
.tl-line{position:relative;}
.tl-line::before{content:'';position:absolute;left:50%;top:0;bottom:0;width:1px;background:var(--border);transform:translateX(-50%);}
.tl-event{display:grid;grid-template-columns:1fr 60px 1fr;align-items:center;gap:8px;margin-bottom:16px;}
.tl-h{text-align:right;padding-right:12px;}
.tl-a{padding-left:12px;}
.tl-min{font-family:'Syne',sans-serif;font-size:15px;font-weight:800;color:var(--lime);text-align:center;background:var(--card);border:1px solid var(--border);width:44px;height:28px;display:flex;align-items:center;justify-content:center;margin:0 auto;position:relative;z-index:2;}
.tl-player{font-size:14px;font-weight:700;font-family:'Barlow Condensed',sans-serif;}
.tl-type{font-size:11px;color:var(--muted);margin-top:2px;}
.ht-bar{background:rgba(200,241,53,.06);border:1px solid rgba(200,241,53,.1);text-align:center;font-family:'Space Mono',monospace;font-size:10px;letter-spacing:2px;color:var(--lime);padding:8px;margin:8px 0 20px;}

/* ── FOOTER ── */
footer{background:var(--surface);border-top:1px solid var(--border);padding:48px 40px 24px;margin-top:60px;}
.footer-inner{max-width:1220px;margin:0 auto;display:grid;grid-template-columns:1.5fr 1fr 1fr 1fr;gap:40px;margin-bottom:40px;}
.footer-logo{font-family:'Syne',sans-serif;font-size:42px;font-weight:800;letter-spacing:-2px;margin-bottom:12px;}
.footer-logo span{color:var(--lime);}
.footer-tagline{font-size:13px;color:var(--muted);line-height:1.6;margin-bottom:20px;}
.footer-social{display:flex;gap:10px;}
.soc-btn{width:34px;height:34px;border:1px solid var(--border);display:flex;align-items:center;justify-content:center;font-size:14px;color:var(--muted);cursor:pointer;transition:all .2s;text-decoration:none;border-radius:6px;}
.soc-btn:hover{border-color:var(--lime);color:var(--lime);}
.footer-col h4{font-family:'Space Mono',monospace;font-size:10px;letter-spacing:2px;text-transform:uppercase;color:var(--lime);margin-bottom:16px;}
.footer-col a{display:block;font-size:13px;color:var(--muted);text-decoration:none;margin-bottom:8px;transition:color .2s;}
.footer-col a:hover{color:var(--text);}
.footer-bottom{max-width:1220px;margin:0 auto;padding-top:20px;border-top:1px solid var(--border);display:flex;justify-content:space-between;font-size:11px;color:#444;font-family:'Space Mono',monospace;}
.fade-in{opacity:0;transform:translateY(20px);animation:fiu .6s forwards;}
@keyframes fiu{to{opacity:1;transform:translateY(0);}}
.fade-in:nth-child(1){animation-delay:.1s;}
.fade-in:nth-child(2){animation-delay:.2s;}
.fade-in:nth-child(3){animation-delay:.3s;}
</style>
</head>
<body>

<!-- ANIMATED BACKGROUND -->
<div class="bg-canvas">
  <div class="orb orb1"></div>
  <div class="orb orb2"></div>
  <div class="orb orb3"></div>
</div>

<div class="layer">

<div class="ticker-wrap">
  <div class="ticker-label"><span class="dot"></span>LIVE</div>
  <div class="ticker-track">
    <span>Mamelodi Sundowns extend lead at top of Betway Premiership</span>
    <span>Kaizer Chiefs announce new head coach talks</span>
    <span>Bafana Bafana AFCON qualifier squad named — 23 players called up</span>
    <span>Orlando Pirates secure continental semifinal berth</span>
    <span>PSL Viewership: 19 million unique viewers in 2024/25 season</span>
    <span>Transfer Window: Stellenbosch FC signs Ghanaian winger</span>
    <span>Pirates vs Espérance ST — CAF CL Semi-Final LIVE 67'</span>
    <span>Mamelodi Sundowns extend lead at top of Betway Premiership</span>
    <span>Kaizer Chiefs announce new head coach talks</span>
    <span>Bafana Bafana AFCON qualifier squad named — 23 players called up</span>
    <span>Orlando Pirates secure continental semifinal berth</span>
    <span>PSL Viewership: 19 million unique viewers in 2024/25 season</span>
    <span>Transfer Window: Stellenbosch FC signs Ghanaian winger</span>
    <span>Pirates vs Espérance ST — CAF CL Semi-Final LIVE 67'</span>
  </div>
</div>

<header>
  <div class="logo" onclick="showPage('home')">SA <span>Kicker</span></div>
  <nav>
    <a onclick="showPage('home')" id="nav-home" class="active">Home</a>
    <a onclick="showPage('scores')" id="nav-scores">Scores</a>
    <a onclick="showPage('standings')" id="nav-standings">Standings</a>
    <a onclick="showPage('fixtures')" id="nav-fixtures">Fixtures</a>
    <a onclick="showPage('playerstats')" id="nav-playerstats">Player Stats</a>
    <a onclick="showPage('timeline')" id="nav-timeline">Timeline</a>
    <a href="#" class="nav-cta">Newsletter</a>
  </nav>
</header>

<!-- ═══ HOME ═══ -->
<div id="page-home" class="page active">
  <div class="hero">
    <div class="hero-main fade-in">
      <div class="hero-img-placeholder">
        <div class="hero-grid-bg"></div>
        <div class="hero-pitch"></div>
        <div class="ball-icon">⚽</div>
      </div>
      <div class="hero-badge"><span class="dot"></span>Breaking</div>
      <div class="hero-overlay">
        <div class="hero-cat">Betway Premiership</div>
        <div class="hero-title">Sundowns Reign Supreme: Pitso's Successors Built a Dynasty No One Can Touch</div>
        <div class="hero-excerpt">With 12 points clear at the summit, Mamelodi Sundowns are rewriting the record books. A deep dive into the tactics, squad depth, and philosophy that has made them the continent's most consistent side.</div>
        <div class="hero-meta"><span class="author">Thabo Nkosi</span><span>May 9, 2026</span><span>14 min read</span></div>
      </div>
    </div>
    <div class="hero-sidebar">
      <div class="side-article fade-in"><div class="side-num">01</div><div class="side-cat">Bafana Bafana</div><div class="side-title">Hugo Broos Drops Surprise Selections Ahead of AFCON Qualifier vs Ethiopia</div><div class="side-meta">May 8, 2026 · 6 min</div></div>
      <div class="side-article fade-in"><div class="side-num">02</div><div class="side-cat">Kaizer Chiefs</div><div class="side-title">Chiefs Board in Emergency Meeting — Top European Coach Being Considered</div><div class="side-meta">May 8, 2026 · 8 min</div></div>
      <div class="side-article fade-in"><div class="side-num">03</div><div class="side-cat">CAF Champions League</div><div class="side-title">Pirates' Road to the Final: How They Silenced Cairo's Al-Ahly</div><div class="side-meta">May 7, 2026 · 10 min</div></div>
      <div class="side-article fade-in"><div class="side-num">04</div><div class="side-cat">Transfers</div><div class="side-title">R8m Offer Rejected: Stellenbosch Hold Firm on Striker Mokwena</div><div class="side-meta">May 7, 2026 · 4 min</div></div>
    </div>
  </div>

  <div class="stats-banner">
    <div class="stats-inner">
      <div class="stat-item"><div class="stat-num">19M+</div><div class="stat-label">Unique PSL Viewers (2024/25)</div><div class="stat-source">Source: Nielsen Sports SA / PSL.co.za</div></div>
      <div class="stat-item"><div class="stat-num">27%</div><div class="stat-label">Rise in Live Viewership YoY</div><div class="stat-source">Source: Nielsen Sports SA, 2024</div></div>
      <div class="stat-item"><div class="stat-num">86%</div><div class="stat-label">of South Africans Watch Football</div><div class="stat-source">Source: DCMN Survey</div></div>
      <div class="stat-item"><div class="stat-num">#1</div><div class="stat-label">Football — Highest Viewership on SuperSport</div><div class="stat-source">Source: SuperSport / PSL, 2024</div></div>
    </div>
  </div>

  <!-- ✨ LIVE AI NEWS PANEL -->
  <div class="live-news-panel">
    <div class="lnp-inner">
      <div class="lnp-header">
        <div class="lnp-title"><span class="pulse"></span>AI Match Digest — Live Updates</div>
        <div class="lnp-subtitle" id="lnp-timestamp">Fetching latest stories…</div>
        <button class="lnp-refresh" id="lnp-btn" onclick="fetchLiveNews()">⟳ Refresh</button>
      </div>
      <div class="lnp-body" id="lnp-body">
        <div class="lnp-loading"><div class="spinner"></div>Generating live match digest…</div>
      </div>
    </div>
  </div>

  <div class="section">
    <div class="section-header"><div class="section-title">Latest News</div><a href="#" class="see-all">See All →</a></div>
    <div class="articles-grid">
      <div class="card fade-in"><div class="card-img bg-chiefs"><div class="card-team-icon">⚽</div><div class="card-badge">Transfer</div></div><div class="card-body"><div class="card-cat">Kaizer Chiefs</div><div class="card-title">Inside Naturena: Three Profiles on Chiefs' Coaching Shortlist</div><div class="card-excerpt">SA Kicker can reveal the board has narrowed its coaching search to three candidates — including one former PSL winner.</div><div class="card-meta"><span>Lungelo Dube</span><span>May 9 · 9 min</span></div></div></div>
      <div class="card fade-in"><div class="card-img bg-bafana"><div class="card-team-icon">🇿🇦</div><div class="card-badge green">Bafana</div></div><div class="card-body"><div class="card-cat">National Team</div><div class="card-title">Broos' Bold Gamble: Why a 19-Year-Old Goalkeeper Starts Against Ethiopia</div><div class="card-excerpt">Hugo Broos has raised eyebrows with his goalkeeping selection. We break down the tactical reasoning.</div><div class="card-meta"><span>Sipho Mthembu</span><span>May 8 · 7 min</span></div></div></div>
      <div class="card fade-in"><div class="card-img bg-pirates"><div class="card-team-icon">☠️</div><div class="card-badge red">CAF Live</div></div><div class="card-body"><div class="card-cat">CAF Champions League</div><div class="card-title">Bucs on the Brink of History: Pirates' CAF Journey in Numbers</div><div class="card-excerpt">From the group stages to the semifinal, Orlando Pirates have become the story of this year's Champions League.</div><div class="card-meta"><span>Andile Khumalo</span><span>May 8 · 11 min</span></div></div></div>
    </div>
  </div>

  <div class="research-box">
    <div class="research-label">Why SA Kicker Exists — The Research</div>
    <div class="research-text">Football is <strong>South Africa's most-watched sport</strong>, with the Betway Premiership capturing <strong>over 19 million unique viewers</strong> in 2024/25 and live viewership growing <strong>27% year-on-year</strong>. Studies across 806 PSL fans confirmed that <strong>fan engagement directly predicts match attendance and merchandise spend</strong>. South Africans don't just watch — they are <strong>deeply, passionately retained</strong>.</div>
    <div class="research-source">Sources: Nielsen Sports SA (2024) · PSL.co.za · DCMN South Africa Survey · Stander &amp; De Beer (2016), <em>SA Journal for Research in Sport</em> · SuperSport Viewership Report 2024</div>
  </div>

  <div class="two-col">
    <div>
      <div class="section-header" style="margin-bottom:16px;"><div class="section-title">Editor's Opinion</div></div>
      <div class="opinion-card">
        <div class="opinion-label">Opinion · SA Kicker Editor</div>
        <div class="opinion-title">The PSL Is Africa's Most Underrated League — And the World Is About to Find Out</div>
        <div class="opinion-body">While European media obsesses over AFCON performances, South Africa has quietly built something extraordinary. The Betway Premiership now boasts the fastest-growing viewership on the continent, world-class academy systems at Sundowns, and a generation of players good enough for the top five European leagues.</div>
        <div class="opinion-author"><div class="author-avatar">NK</div><div><div class="author-name">Nkosinathi Khumalo</div><div class="author-role">Editor-in-Chief, SA Kicker</div></div></div>
      </div>
    </div>
    <div>
      <div class="section-header" style="margin-bottom:0;"><div class="section-title">Top Stories</div><a href="#" class="see-all">More →</a></div>
      <div class="top-stories">
        <div class="top-story"><div class="story-num">1</div><div class="story-content"><div class="story-cat">PSL</div><div class="story-title">Sundowns' Transfer Target: Premier League Midfielder Linked with a Bombshell Switch</div><div class="story-meta">May 9, 2026 · 6 min</div></div></div>
        <div class="top-story"><div class="story-num">2</div><div class="story-content"><div class="story-cat">Kaizer Chiefs</div><div class="story-title">Amakhosi's 2026/27 Kit Leaked — Fans React to the New Gold and Black Design</div><div class="story-meta">May 9, 2026 · 3 min</div></div></div>
        <div class="top-story"><div class="story-num">3</div><div class="story-content"><div class="story-cat">Women's Football</div><div class="story-title">Banyana Banyana Eye World Cup Qualification Window: Full Fixture List Released</div><div class="story-meta">May 8, 2026 · 5 min</div></div></div>
        <div class="top-story"><div class="story-num">4</div><div class="story-content"><div class="story-cat">Development</div><div class="story-title">Diski Challenge Final Preview: Five Prospects Who Could Star in the PSL Next Season</div><div class="story-meta">May 7, 2026 · 7 min</div></div></div>
        <div class="top-story"><div class="story-num">5</div><div class="story-content"><div class="story-cat">Grassroots</div><div class="story-title">SAFA's National Schools Programme: 14,000 Kids Enrolled This Year Alone</div><div class="story-meta">May 6, 2026 · 4 min</div></div></div>
      </div>
    </div>
  </div>

  <div class="section">
    <div class="section-header"><div class="section-title">In Depth</div><a href="#" class="see-all">See All →</a></div>
    <div class="articles-grid">
      <div class="card fade-in"><div class="card-img bg-sundowns"><div class="card-team-icon">🌞</div><div class="card-badge">Analysis</div></div><div class="card-body"><div class="card-cat">Tactical Analysis</div><div class="card-title">Sundowns' High Press: Why Opponents Cannot Find a Way Through</div><div class="card-excerpt">Using Opta data, we map exactly how Sundowns' 4-3-3 pressing triggers force 23 turnovers per game.</div><div class="card-meta"><span>Rorisang Mofokeng</span><span>May 7 · 15 min</span></div></div></div>
      <div class="card fade-in"><div class="card-img bg-transfer"><div class="card-team-icon">📋</div><div class="card-badge">Transfers</div></div><div class="card-body"><div class="card-cat">Transfer Window</div><div class="card-title">R200m+ Spent in This PSL Window: The Full Breakdown</div><div class="card-excerpt">Who spent big, who was canny, and which club faces financial fair play questions?</div><div class="card-meta"><span>Jabu Pretorius</span><span>May 6 · 12 min</span></div></div></div>
      <div class="card fade-in"><div class="card-img bg-psl"><div class="card-team-icon">🏆</div><div class="card-badge">Report</div></div><div class="card-body"><div class="card-cat">PSL</div><div class="card-title">The Championship Race: How Each Club Can Still Win the Title</div><div class="card-excerpt">A mathematical look at every scenario for Sundowns, Pirates, and the dark horses.</div><div class="card-meta"><span>Tshepiso Dlamini</span><span>May 5 · 8 min</span></div></div></div>
    </div>
  </div>

  <footer>
    <div class="footer-inner">
      <div><div class="footer-logo">SA <span>Kicker</span></div><div class="footer-tagline">South Africa's home of football journalism. Deep analysis, breaking news, and the stories that matter — from the PSL to the world stage.</div><div class="footer-social"><a class="soc-btn" href="#">𝕏</a><a class="soc-btn" href="#">f</a><a class="soc-btn" href="#">▶</a><a class="soc-btn" href="#">in</a></div></div>
      <div class="footer-col"><h4>Competitions</h4><a href="#">Betway Premiership</a><a href="#">Nedbank Cup</a><a href="#">CAF Champions League</a><a href="#">AFCON</a><a href="#">Diski Challenge</a></div>
      <div class="footer-col"><h4>Clubs</h4><a href="#">Mamelodi Sundowns</a><a href="#">Orlando Pirates</a><a href="#">Kaizer Chiefs</a><a href="#">Stellenbosch FC</a><a href="#">AmaZulu</a></div>
      <div class="footer-col"><h4>SA Kicker</h4><a href="#">About Us</a><a href="#">Newsletter</a><a href="#">Advertise</a><a href="#">Our Journalists</a><a href="#">Contact</a></div>
    </div>
    <div class="footer-bottom"><span>© 2026 SA Kicker. All rights reserved. Based in Johannesburg, South Africa.</span><span>🇿🇦 Built for the game we love</span></div>
  </footer>
</div>

<!-- ═══ SCORES ═══ -->
<div id="page-scores" class="page">
  <div class="feature-page">
    <div class="page-heading">Match <span>Scores</span></div>
    <div class="page-sub">Live results, recent scores and upcoming kick-offs across all competitions.</div>
    <div class="ftabs">
      <div class="ftab active">All Competitions</div>
      <div class="ftab">Betway Premiership</div>
      <div class="ftab">CAF Champions League</div>
      <div class="ftab">Bafana Bafana</div>
      <div class="ftab">Nedbank Cup</div>
    </div>
    <div class="scores-list">
      <div class="date-div">🔴 Live Now</div>
      <div class="match-row">
        <div class="match-time"><div class="live-row"><span class="live-dot"></span>67'</div></div>
        <div class="team-name team-home">Orlando Pirates</div>
        <div class="score-display live">1 – 0</div>
        <div class="team-name team-away">Espérance ST</div>
        <div class="match-comp">CAF CL · Semi-Final<span class="live-badge">LIVE</span></div>
      </div>
      <div class="match-row">
        <div class="match-time"><div class="live-row"><span class="live-dot"></span>45+2'</div></div>
        <div class="team-name team-home">AmaZulu FC</div>
        <div class="score-display live">0 – 0</div>
        <div class="team-name team-away">Cape Town Spurs</div>
        <div class="match-comp">Betway Premiership · GW33<span class="live-badge">LIVE</span></div>
      </div>
      <div class="date-div">Saturday, 9 May 2026 — Full Time</div>
      <div class="match-row">
        <div class="match-time">14:00 SAST · FT</div>
        <div class="team-name team-home">Mamelodi Sundowns</div>
        <div class="score-display">3 – 1</div>
        <div class="team-name team-away">Cape Town City</div>
        <div class="match-comp">Betway Premiership · GW33</div>
      </div>
      <div class="match-row">
        <div class="match-time">16:30 SAST · FT</div>
        <div class="team-name team-home">Orlando Pirates</div>
        <div class="score-display">2 – 0</div>
        <div class="team-name team-away">AmaZulu FC</div>
        <div class="match-comp">Betway Premiership · GW33</div>
      </div>
      <div class="match-row">
        <div class="match-time">15:00 SAST · FT</div>
        <div class="team-name team-home">Stellenbosch FC</div>
        <div class="score-display">1 – 1</div>
        <div class="team-name team-away">Kaizer Chiefs</div>
        <div class="match-comp">Betway Premiership · GW33</div>
      </div>
      <div class="date-div">Friday, 8 May 2026</div>
      <div class="match-row">
        <div class="match-time">20:00 SAST · FT</div>
        <div class="team-name team-home">SuperSport United</div>
        <div class="score-display">0 – 2</div>
        <div class="team-name team-away">Mamelodi Sundowns</div>
        <div class="match-comp">Nedbank Cup · QF</div>
      </div>
      <div class="match-row">
        <div class="match-time">18:00 SAST · FT</div>
        <div class="team-name team-home">Sekhukhune United</div>
        <div class="score-display">1 – 0</div>
        <div class="team-name team-away">TS Galaxy</div>
        <div class="match-comp">Betway Premiership · GW32</div>
      </div>
      <div class="match-row">
        <div class="match-time">19:30 SAST · FT</div>
        <div class="team-name team-home">Golden Arrows</div>
        <div class="score-display">2 – 2</div>
        <div class="team-name team-away">Swallows FC</div>
        <div class="match-comp">Betway Premiership · GW32</div>
      </div>
    </div>
  </div>
</div>

<!-- ═══ STANDINGS ═══ -->
<div id="page-standings" class="page">
  <div class="feature-page">
    <div class="page-heading">League <span>Standings</span></div>
    <div class="page-sub">Betway Premiership 2025/26 — Matchday 33 of 34</div>
    <div class="ftabs" style="margin-bottom:20px;">
      <div class="ftab active">Betway Premiership</div>
      <div class="ftab">Diski Challenge</div>
      <div class="ftab">CAF Group Stages</div>
    </div>
    <table class="s-table">
      <thead><tr><th>#</th><th>Club</th><th>P</th><th>W</th><th>D</th><th>L</th><th>GF</th><th>GA</th><th>GD</th><th>PTS</th><th>Form</th></tr></thead>
      <tbody>
        <tr class="champ"><td>1</td><td><div class="crest"><div class="cdot" style="background:#C8F135;"></div>Mamelodi Sundowns</div></td><td>33</td><td>24</td><td>6</td><td>3</td><td>71</td><td>22</td><td>+49</td><td><span class="pts">78</span></td><td><div class="form-row"><div class="fw">W</div><div class="fw">W</div><div class="fd fw">D</div><div class="fw">W</div><div class="fw">W</div></div></td></tr>
        <tr class="conf"><td>2</td><td><div class="crest"><div class="cdot" style="background:#111;border:1px solid #555;"></div>Orlando Pirates</div></td><td>33</td><td>20</td><td>7</td><td>6</td><td>58</td><td>30</td><td>+28</td><td><span class="pts">67</span></td><td><div class="form-row"><div class="fw">W</div><div class="fd fw">D</div><div class="fw">W</div><div class="fw">W</div><div class="fl fw">L</div></div></td></tr>
        <tr class="conf"><td>3</td><td><div class="crest"><div class="cdot" style="background:#00E5C8;"></div>Stellenbosch FC</div></td><td>33</td><td>17</td><td>9</td><td>7</td><td>48</td><td>33</td><td>+15</td><td><span class="pts">60</span></td><td><div class="form-row"><div class="fd fw">D</div><div class="fw">W</div><div class="fl fw">L</div><div class="fw">W</div><div class="fd fw">D</div></div></td></tr>
        <tr><td>4</td><td><div class="crest"><div class="cdot" style="background:#C8F135;"></div>Kaizer Chiefs</div></td><td>33</td><td>15</td><td>10</td><td>8</td><td>44</td><td>36</td><td>+8</td><td><span class="pts">55</span></td><td><div class="form-row"><div class="fd fw">D</div><div class="fd fw">D</div><div class="fw">W</div><div class="fl fw">L</div><div class="fd fw">D</div></div></td></tr>
        <tr><td>5</td><td><div class="crest"><div class="cdot" style="background:#3B7EFF;"></div>Cape Town City</div></td><td>33</td><td>14</td><td>9</td><td>10</td><td>40</td><td>35</td><td>+5</td><td><span class="pts">51</span></td><td><div class="form-row"><div class="fl fw">L</div><div class="fw">W</div><div class="fw">W</div><div class="fd fw">D</div><div class="fl fw">L</div></div></td></tr>
        <tr><td>6</td><td><div class="crest"><div class="cdot" style="background:#cc0000;"></div>SuperSport United</div></td><td>33</td><td>13</td><td>10</td><td>10</td><td>41</td><td>40</td><td>+1</td><td><span class="pts">49</span></td><td><div class="form-row"><div class="fw">W</div><div class="fl fw">L</div><div class="fd fw">D</div><div class="fl fw">L</div><div class="fw">W</div></div></td></tr>
        <tr><td>7</td><td><div class="crest"><div class="cdot" style="background:#00aaff;"></div>AmaZulu FC</div></td><td>33</td><td>12</td><td>8</td><td>13</td><td>35</td><td>41</td><td>-6</td><td><span class="pts">44</span></td><td><div class="form-row"><div class="fl fw">L</div><div class="fd fw">D</div><div class="fl fw">L</div><div class="fw">W</div><div class="fd fw">D</div></div></td></tr>
        <tr><td>8</td><td><div class="crest"><div class="cdot" style="background:#ff6600;"></div>Sekhukhune United</div></td><td>33</td><td>11</td><td>9</td><td>13</td><td>33</td><td>40</td><td>-7</td><td><span class="pts">42</span></td><td><div class="form-row"><div class="fw">W</div><div class="fd fw">D</div><div class="fw">W</div><div class="fl fw">L</div><div class="fl fw">L</div></div></td></tr>
        <tr><td>9</td><td><div class="crest"><div class="cdot" style="background:#8800aa;"></div>Golden Arrows</div></td><td>33</td><td>10</td><td>8</td><td>15</td><td>30</td><td>43</td><td>-13</td><td><span class="pts">38</span></td><td><div class="form-row"><div class="fl fw">L</div><div class="fl fw">L</div><div class="fd fw">D</div><div class="fw">W</div><div class="fl fw">L</div></div></td></tr>
        <tr><td>10</td><td><div class="crest"><div class="cdot" style="background:#336600;"></div>Swallows FC</div></td><td>33</td><td>9</td><td>7</td><td>17</td><td>29</td><td>50</td><td>-21</td><td><span class="pts">34</span></td><td><div class="form-row"><div class="fd fw">D</div><div class="fl fw">L</div><div class="fl fw">L</div><div class="fl fw">L</div><div class="fw">W</div></div></td></tr>
        <tr class="rel"><td>11</td><td><div class="crest"><div class="cdot" style="background:#ccaa00;"></div>TS Galaxy</div></td><td>33</td><td>7</td><td>8</td><td>18</td><td>24</td><td>52</td><td>-28</td><td><span class="pts">29</span></td><td><div class="form-row"><div class="fl fw">L</div><div class="fl fw">L</div><div class="fd fw">D</div><div class="fl fw">L</div><div class="fl fw">L</div></div></td></tr>
        <tr class="rel"><td>12</td><td><div class="crest"><div class="cdot" style="background:#aa0000;"></div>Cape Town Spurs</div></td><td>33</td><td>5</td><td>8</td><td>20</td><td>22</td><td>58</td><td>-36</td><td><span class="pts">23</span></td><td><div class="form-row"><div class="fl fw">L</div><div class="fd fw">D</div><div class="fl fw">L</div><div class="fl fw">L</div><div class="fl fw">L</div></div></td></tr>
      </tbody>
    </table>
    <div class="s-legend">
      <div class="sl-item"><div class="sl-bar" style="background:var(--lime);"></div>CAF Champions League</div>
      <div class="sl-item"><div class="sl-bar" style="background:var(--cyan);"></div>CAF Confederation Cup</div>
      <div class="sl-item"><div class="sl-bar" style="background:var(--red);"></div>Relegation Zone</div>
    </div>
  </div>
</div>

<!-- ═══ FIXTURES ═══ -->
<div id="page-fixtures" class="page">
  <div class="feature-page">
    <div class="page-heading">Upcoming <span>Fixtures</span></div>
    <div class="page-sub">All scheduled matches across PSL, CAF, and national team competitions.</div>
    <div class="fix-filter">
      <button class="fbtn active" onclick="filterFix(this,'all')">All</button>
      <button class="fbtn" onclick="filterFix(this,'psl')">Betway Premiership</button>
      <button class="fbtn" onclick="filterFix(this,'caf')">CAF</button>
      <button class="fbtn" onclick="filterFix(this,'bafana')">Bafana Bafana</button>
      <button class="fbtn" onclick="filterFix(this,'nedbank')">Nedbank Cup</button>
    </div>
    <div class="fix-week">
      <div class="week-hdr">⚽ Sunday, 10 May 2026</div>
      <div class="fix-card" data-comp="psl"><div class="fix-time">15:00</div><div class="fix-team fix-home">Mamelodi Sundowns</div><div class="fix-vs">VS</div><div class="fix-team">SuperSport United</div><div class="fix-info">FNB Stadium, Soweto<br>Betway Premiership GW34<div class="remind-btn">🔔 Remind Me</div></div></div>
      <div class="fix-card" data-comp="psl"><div class="fix-time">17:30</div><div class="fix-team fix-home">Kaizer Chiefs</div><div class="fix-vs">VS</div><div class="fix-team">Golden Arrows</div><div class="fix-info">FNB Stadium, Soweto<br>Betway Premiership GW34<div class="remind-btn">🔔 Remind Me</div></div></div>
    </div>
    <div class="fix-week">
      <div class="week-hdr">⚽ Monday, 11 May 2026</div>
      <div class="fix-card" data-comp="psl"><div class="fix-time">19:30</div><div class="fix-team fix-home">Cape Town City</div><div class="fix-vs">VS</div><div class="fix-team">Orlando Pirates</div><div class="fix-info">DHL Newlands, Cape Town<br>Betway Premiership GW34<div class="remind-btn">🔔 Remind Me</div></div></div>
    </div>
    <div class="fix-week">
      <div class="week-hdr">🇿🇦 Monday, 12 May 2026</div>
      <div class="fix-card" data-comp="bafana"><div class="fix-time">18:00</div><div class="fix-team fix-home">South Africa</div><div class="fix-vs">VS</div><div class="fix-team">Ethiopia</div><div class="fix-info">Peter Mokaba Stadium, Polokwane<br>AFCON 2027 Qualifier<div class="remind-btn">🔔 Remind Me</div></div></div>
    </div>
    <div class="fix-week">
      <div class="week-hdr">⚽ Wednesday, 14 May 2026</div>
      <div class="fix-card" data-comp="caf"><div class="fix-time">21:00</div><div class="fix-team fix-home">Espérance ST</div><div class="fix-vs">VS</div><div class="fix-team">Orlando Pirates</div><div class="fix-info">Stade Olympique de Radès, Tunisia<br>CAF CL · SF 2nd Leg<div class="remind-btn">🔔 Remind Me</div></div></div>
      <div class="fix-card" data-comp="psl"><div class="fix-time">19:30</div><div class="fix-team fix-home">Stellenbosch FC</div><div class="fix-vs">VS</div><div class="fix-team">AmaZulu FC</div><div class="fix-info">Danie Craven Stadium<br>Betway Premiership GW34<div class="remind-btn">🔔 Remind Me</div></div></div>
    </div>
    <div class="fix-week">
      <div class="week-hdr">🏆 Saturday, 17 May 2026</div>
      <div class="fix-card" data-comp="nedbank"><div class="fix-time">15:00</div><div class="fix-team fix-home">Mamelodi Sundowns</div><div class="fix-vs">VS</div><div class="fix-team">Orlando Pirates</div><div class="fix-info">Moses Mabhida Stadium, Durban<br>Nedbank Cup · Final<div class="remind-btn">🔔 Remind Me</div></div></div>
    </div>
  </div>
</div>

<!-- ═══ PLAYER STATS ═══ -->
<div id="page-playerstats" class="page">
  <div class="feature-page">
    <div class="page-heading">Player <span>Stats</span></div>
    <div class="page-sub">Betway Premiership 2025/26 — Top performers across all categories.</div>
    <div class="top-stat-cards">
      <div class="tsc"><div class="tsc-label">Golden Boot</div><div class="tsc-player">Evidence Makgopa</div><div class="tsc-club">Orlando Pirates</div><div class="tsc-val">22</div><div class="tsc-unit">Goals</div></div>
      <div class="tsc" style="border-top-color:var(--cyan)"><div class="tsc-label">Most Assists</div><div class="tsc-player">Themba Zwane</div><div class="tsc-club">Mamelodi Sundowns</div><div class="tsc-val">15</div><div class="tsc-unit">Assists</div></div>
      <div class="tsc" style="border-top-color:var(--orange)"><div class="tsc-label">Clean Sheets</div><div class="tsc-player">Denis Onyango</div><div class="tsc-club">Mamelodi Sundowns</div><div class="tsc-val">19</div><div class="tsc-unit">Clean Sheets</div></div>
      <div class="tsc" style="border-top-color:var(--red)"><div class="tsc-label">Most Bookings</div><div class="tsc-player">Siyanda Xulu</div><div class="tsc-club">AmaZulu FC</div><div class="tsc-val">11</div><div class="tsc-unit">Yellow Cards</div></div>
    </div>
    <div class="ftabs">
      <div class="ftab active" onclick="switchStat(this,'goals')">⚽ Goals</div>
      <div class="ftab" onclick="switchStat(this,'assists')">🎯 Assists</div>
      <div class="ftab" onclick="switchStat(this,'passing')">📊 Passing</div>
      <div class="ftab" onclick="switchStat(this,'defending')">🛡️ Defending</div>
    </div>
    <div id="stat-table"></div>
  </div>
</div>

<!-- ═══ TIMELINE ═══ -->
<div id="page-timeline" class="page">
  <div class="feature-page">
    <div class="page-heading">Match <span>Timeline</span></div>
    <div class="page-sub">Select a match to view the full event timeline, stats breakdown, and key moments.</div>
    <div class="match-sel">
      <div class="msc active" onclick="pickMatch(this,0)">
        <div class="msc-comp">Betway Premiership · GW33</div>
        <div class="msc-row"><div class="msc-team">Mamelodi Sundowns</div><div class="msc-score">3–1</div><div class="msc-team">Cape Town City</div></div>
        <div class="msc-date">9 May 2026 · FT</div>
      </div>
      <div class="msc" onclick="pickMatch(this,1)">
        <div class="msc-comp">Betway Premiership · GW33</div>
        <div class="msc-row"><div class="msc-team">Orlando Pirates</div><div class="msc-score">2–0</div><div class="msc-team">AmaZulu FC</div></div>
        <div class="msc-date">9 May 2026 · FT</div>
      </div>
      <div class="msc" onclick="pickMatch(this,2)">
        <div class="msc-comp">CAF CL · Semi-Final</div>
        <div class="msc-row"><div class="msc-team">Orlando Pirates</div><div class="msc-score" style="color:var(--red)">1–0</div><div class="msc-team">Espérance ST</div></div>
        <div class="msc-date">9 May 2026 · <span style="color:var(--red)">LIVE 67'</span></div>
      </div>
    </div>
    <div class="tw" id="tw"></div>
  </div>
</div>

</div><!-- end .layer -->

<script>
// ── NAV ──
function showPage(n){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('nav a').forEach(a=>a.classList.remove('active'));
  document.getElementById('page-'+n).classList.add('active');
  const el=document.getElementById('nav-'+n);
  if(el)el.classList.add('active');
  window.scrollTo(0,0);
}

// ── FIXTURE FILTER ──
function filterFix(el,comp){
  document.querySelectorAll('.fbtn').forEach(b=>b.classList.remove('active'));
  el.classList.add('active');
  document.querySelectorAll('.fix-card').forEach(c=>{
    c.style.display=(comp==='all'||c.dataset.comp===comp)?'grid':'none';
  });
}

// ── PLAYER STATS ──
const SD={
  goals:[
    {r:1,n:'Evidence Makgopa',c:'Orlando Pirates',a:31,g:22,s:89,cv:'24.7%',p:100},
    {r:2,n:'Themba Zwane',c:'Mamelodi Sundowns',a:29,g:17,s:64,cv:'26.6%',p:77},
    {r:3,n:'Bradley Grobler',c:'Stellenbosch FC',a:30,g:15,s:71,cv:'21.1%',p:68},
    {r:4,n:'Mduduzi Mdantsane',c:'Cape Town City',a:28,g:12,s:58,cv:'20.7%',p:55},
    {r:5,n:'Bongokuhle Hlongwane',c:'Kaizer Chiefs',a:30,g:11,s:52,cv:'21.2%',p:50},
    {r:6,n:'Lyle Foster',c:'Mamelodi Sundowns',a:27,g:10,s:49,cv:'20.4%',p:45},
    {r:7,n:'Bienvenu Eva Nga',c:'AmaZulu FC',a:29,g:9,s:46,cv:'19.6%',p:41},
    {r:8,n:'Ruzaigh Gamildien',c:'SuperSport United',a:28,g:9,s:44,cv:'20.5%',p:41}
  ],
  assists:[
    {r:1,n:'Themba Zwane',c:'Mamelodi Sundowns',a:29,ast:15,ch:62,p:100},
    {r:2,n:'Gaston Sirino',c:'Mamelodi Sundowns',a:27,ast:13,ch:54,p:87},
    {r:3,n:'Thembinkosi Lorch',c:'Orlando Pirates',a:30,ast:11,ch:47,p:73},
    {r:4,n:'Siphesihle Ndlovu',c:'Mamelodi Sundowns',a:28,ast:10,ch:41,p:67},
    {r:5,n:'Keagan Dolly',c:'Kaizer Chiefs',a:26,ast:9,ch:38,p:60},
    {r:6,n:'Khama Billiat',c:'Kaizer Chiefs',a:24,ast:8,ch:34,p:53}
  ],
  passing:[
    {r:1,n:'Andile Jali',c:'Mamelodi Sundowns',a:28,ps:2841,acc:'89.2%',lb:312,p:100},
    {r:2,n:'Siyabonga Ngezana',c:'Mamelodi Sundowns',a:30,ps:2614,acc:'88.1%',lb:188,p:92},
    {r:3,n:'Thulani Hlatshwayo',c:'Cape Town City',a:29,ps:2401,acc:'85.4%',lb:241,p:85},
    {r:4,n:'Fortune Makaringe',c:'Orlando Pirates',a:31,ps:2310,acc:'83.7%',lb:198,p:81},
    {r:5,n:'Aphiwe Cele',c:'Stellenbosch FC',a:28,ps:2187,acc:'82.9%',lb:176,p:77}
  ],
  defending:[
    {r:1,n:'Mothobi Mvala',c:'Mamelodi Sundowns',a:30,tk:87,int:64,cl:112,p:100},
    {r:2,n:'Nkosinathi Sibisi',c:'Orlando Pirates',a:29,tk:79,int:58,cl:97,p:91},
    {r:3,n:'Siyanda Xulu',c:'AmaZulu FC',a:28,tk:74,int:51,cl:88,p:85},
    {r:4,n:'Ramudzuli Ntshangase',c:'Stellenbosch FC',a:27,tk:68,int:49,cl:81,p:78},
    {r:5,n:'Mosa Lebusa',c:'Kaizer Chiefs',a:28,tk:65,int:44,cl:76,p:75}
  ]
};
const CLR=['#C8F135','#00E5C8','#FF5E1F','#FF3B3B','#9b59b6','#3B7EFF','#1abc9c','#e91e8c'];
function av(n,i){return`<div class="p-av" style="background:${CLR[i]}">${n.split(' ').map(w=>w[0]).slice(0,2).join('')}</div>`;}
function switchStat(el,cat){
  document.querySelectorAll('#page-playerstats .ftab').forEach(t=>t.classList.remove('active'));
  el.classList.add('active');
  renderStat(cat);
}
function renderStat(cat){
  const d=SD[cat];
  let hd='',rows='';
  if(cat==='goals'){
    hd='<th>Rank</th><th>Player</th><th>Club</th><th>Apps</th><th>Goals</th><th>Shots</th><th>Conversion</th><th>Visual</th>';
    rows=d.map((p,i)=>`<tr><td>${p.r}</td><td><div class="p-name-cell">${av(p.n,i)}${p.n}</div></td><td>${p.c}</td><td>${p.a}</td><td><span class="stat-hl">${p.g}</span></td><td>${p.s}</td><td>${p.cv}</td><td><div class="bar-wrap"><div class="bar-bg"><div class="bar-fill" style="width:${p.p}%"></div></div></div></td></tr>`).join('');
  } else if(cat==='assists'){
    hd='<th>Rank</th><th>Player</th><th>Club</th><th>Apps</th><th>Assists</th><th>Chances Created</th><th>Visual</th>';
    rows=d.map((p,i)=>`<tr><td>${p.r}</td><td><div class="p-name-cell">${av(p.n,i)}${p.n}</div></td><td>${p.c}</td><td>${p.a}</td><td><span class="stat-hl">${p.ast}</span></td><td>${p.ch}</td><td><div class="bar-wrap"><div class="bar-bg"><div class="bar-fill" style="width:${p.p}%"></div></div></div></td></tr>`).join('');
  } else if(cat==='passing'){
    hd='<th>Rank</th><th>Player</th><th>Club</th><th>Apps</th><th>Total Passes</th><th>Accuracy</th><th>Long Balls</th><th>Visual</th>';
    rows=d.map((p,i)=>`<tr><td>${p.r}</td><td><div class="p-name-cell">${av(p.n,i)}${p.n}</div></td><td>${p.c}</td><td>${p.a}</td><td><span class="stat-hl">${p.ps.toLocaleString()}</span></td><td>${p.acc}</td><td>${p.lb}</td><td><div class="bar-wrap"><div class="bar-bg"><div class="bar-fill" style="width:${p.p}%"></div></div></div></td></tr>`).join('');
  } else {
    hd='<th>Rank</th><th>Player</th><th>Club</th><th>Apps</th><th>Tackles</th><th>Interceptions</th><th>Clearances</th><th>Visual</th>';
    rows=d.map((p,i)=>`<tr><td>${p.r}</td><td><div class="p-name-cell">${av(p.n,i)}${p.n}</div></td><td>${p.c}</td><td>${p.a}</td><td><span class="stat-hl">${p.tk}</span></td><td>${p.int}</td><td>${p.cl}</td><td><div class="bar-wrap"><div class="bar-bg"><div class="bar-fill" style="width:${p.p}%"></div></div></div></td></tr>`).join('');
  }
  document.getElementById('stat-table').innerHTML=`<table class="p-table"><thead><tr>${hd}</tr></thead><tbody>${rows}</tbody></table>`;
}

// ── TIMELINE ──
const MD=[
  {home:'Mamelodi Sundowns',away:'Cape Town City',score:'3 – 1',comp:'Betway Premiership · GW33',date:'9 May 2026',status:'FT',live:false,
   stats:{pos:[62,38],shots:[18,7],sot:[8,3],cor:[9,4],foul:[10,14],yel:[1,3],off:[2,1]},
   events:[
     {min:'18',side:'h',player:'Evidence Makgopa',type:'⚽ Goal',note:'Header from corner'},
     {min:'34',side:'a',player:'Kermit Erasmus',type:'⚽ Goal',note:'Low drive, 30 yards'},
     {min:'HT',side:'',player:'',type:'',note:''},
     {min:'47',side:'h',player:'Themba Zwane',type:'⚽ Goal',note:'Penalty kick'},
     {min:'61',side:'a',player:'J. Petersen',type:'🟨 Yellow Card',note:'Reckless challenge'},
     {min:'72',side:'h',player:'Lyle Foster',type:'⚽ Goal',note:'Close-range finish'},
     {min:'79',side:'h',player:'S. Modiba',type:'🔄 Sub Off',note:'Zwane on'},
     {min:'85',side:'a',player:'B. Ndah',type:'🟨 Yellow Card',note:'Time-wasting'}
   ]},
  {home:'Orlando Pirates',away:'AmaZulu FC',score:'2 – 0',comp:'Betway Premiership · GW33',date:'9 May 2026',status:'FT',live:false,
   stats:{pos:[55,45],shots:[14,9],sot:[6,2],cor:[7,5],foul:[12,11],yel:[2,2],off:[3,2]},
   events:[
     {min:'29',side:'h',player:'Thembinkosi Lorch',type:'⚽ Goal',note:'Curled effort, top corner'},
     {min:'38',side:'a',player:'S. Xulu',type:'🟨 Yellow Card',note:'Late tackle'},
     {min:'HT',side:'',player:'',type:'',note:''},
     {min:'56',side:'h',player:'H. Makola',type:'🟨 Yellow Card',note:'Dissent'},
     {min:'68',side:'h',player:'M. Ntsiangane',type:'⚽ Goal',note:'Tap-in, loose ball'},
     {min:'75',side:'a',player:'B. Eva Nga',type:'🔄 Sub On',note:'Replaced Mkhize'},
     {min:'88',side:'a',player:'A. Dlamini',type:'🟨 Yellow Card',note:'Foul'}
   ]},
  {home:'Orlando Pirates',away:'Espérance ST',score:'1 – 0',comp:'CAF Champions League · Semi-Final',date:'9 May 2026',status:"LIVE 67'",live:true,
   stats:{pos:[48,52],shots:[9,11],sot:[4,3],cor:[5,6],foul:[8,10],yel:[1,1],off:[1,3]},
   events:[
     {min:'12',side:'a',player:'Y. Msakni',type:'🟨 Yellow Card',note:'Foul on Lorch'},
     {min:'44',side:'h',player:'Evidence Makgopa',type:'⚽ Goal',note:'Powerful header'},
     {min:'HT',side:'',player:'',type:'',note:''},
     {min:'58',side:'h',player:'T. Lorch',type:'🟨 Yellow Card',note:'Tactical foul'}
   ]}
];

function pickMatch(el,i){
  document.querySelectorAll('.msc').forEach(c=>c.classList.remove('active'));
  el.classList.add('active');
  renderTW(i);
}
function renderTW(i){
  const m=MD[i];const s=m.stats;
  const sc=m.live?'color:var(--red)':'color:var(--lime)';
  const statRows=[
    ['Possession',s.pos[0]+'%',s.pos[1]+'%',s.pos[0]],
    ['Shots',s.shots[0],s.shots[1],Math.round(s.shots[0]/(s.shots[0]+s.shots[1])*100)],
    ['Shots on Target',s.sot[0],s.sot[1],Math.round(s.sot[0]/(s.sot[0]+s.sot[1]+.01)*100)],
    ['Corners',s.cor[0],s.cor[1],Math.round(s.cor[0]/(s.cor[0]+s.cor[1])*100)],
    ['Fouls',s.foul[0],s.foul[1],Math.round(s.foul[0]/(s.foul[0]+s.foul[1])*100)],
    ['Yellow Cards',s.yel[0],s.yel[1],Math.round(s.yel[0]/(s.yel[0]+s.yel[1]+.01)*100)],
    ['Offsides',s.off[0],s.off[1],Math.round(s.off[0]/(s.off[0]+s.off[1]+.01)*100)]
  ];
  let statsHTML=statRows.map(r=>`
    <div class="mstat"><div class="msv h">${r[1]}</div><div class="msn">${r[0]}</div><div class="msv a">${r[2]}</div></div>
    <div class="ms-bars"><div class="ms-bh" style="width:${r[3]}%"></div><div class="ms-ba" style="flex:1"></div></div>`).join('');
  let evHTML='';
  m.events.forEach(e=>{
    if(e.min==='HT'){evHTML+=`<div class="ht-bar">— HALF TIME —</div>`;return;}
    const isH=e.side==='h';
    evHTML+=`<div class="tl-event">
      <div class="tl-h">${isH?`<div class="tl-player">${e.player}</div><div class="tl-type">${e.type} · ${e.note}</div>`:''}</div>
      <div class="tl-min">${e.min}'</div>
      <div class="tl-a">${!isH&&e.side?`<div class="tl-player">${e.player}</div><div class="tl-type">${e.type} · ${e.note}</div>`:''}</div>
    </div>`;
  });
  document.getElementById('tw').innerHTML=`
    <div class="tw-hdr">
      <div style="flex:1;font-size:11px;color:var(--muted);font-family:'Space Mono',monospace;letter-spacing:1.5px;">${m.comp}</div>
      <div class="tw-sb">
        <div class="tw-teams">
          <div class="tw-tn tw-home">${m.home}</div>
          <div class="tw-score" style="${sc}">${m.score}</div>
          <div class="tw-tn tw-away">${m.away}</div>
        </div>
        <div class="tw-info"><span class="tw-status ${m.live?'live':''}">${m.status}</span> · ${m.date}</div>
      </div>
      <div style="flex:1;text-align:right;font-size:11px;color:var(--muted);font-family:'Space Mono',monospace;">${m.live?'<span style="color:var(--red)">🔴 Broadcasting Live</span>':'Full Time'}</div>
    </div>
    <div class="match-stats-section">
      <div class="mss-title">Match Statistics</div>
      <div style="display:grid;grid-template-columns:70px 1fr 70px;font-family:'Space Mono',monospace;font-size:9px;letter-spacing:1.5px;text-transform:uppercase;color:var(--muted);margin-bottom:12px;">
        <div style="text-align:right;">${m.home}</div><div style="text-align:center;">STAT</div><div>${m.away}</div>
      </div>
      ${statsHTML}
    </div>
    <div class="tl-section">
      <div class="tl-title">Key Events Timeline</div>
      <div style="display:grid;grid-template-columns:1fr 60px 1fr;font-family:'Space Mono',monospace;font-size:9px;letter-spacing:1.5px;text-transform:uppercase;color:var(--muted);margin-bottom:16px;text-align:center;">
        <div style="text-align:right;padding-right:12px;">${m.home}</div><div>MIN</div><div style="text-align:left;padding-left:12px;">${m.away}</div>
      </div>
      <div class="tl-line">${evHTML}</div>
      ${!m.live?'<div class="ht-bar" style="margin-top:20px;">— FULL TIME —</div>':''}
    </div>`;
}

// ── LIVE AI NEWS ──
async function fetchLiveNews(){
  const btn=document.getElementById('lnp-btn');
  const body=document.getElementById('lnp-body');
  const ts=document.getElementById('lnp-timestamp');
  btn.disabled=true;
  btn.textContent='Loading…';
  body.innerHTML='<div class="lnp-loading"><div class="spinner"></div>Generating live match digest…</div>';
  const matchContext=`Today is 9 May 2026. Here are today's SA football results:
- Mamelodi Sundowns 3–1 Cape Town City (Betway Premiership GW33, FT)
- Orlando Pirates 2–0 AmaZulu FC (Betway Premiership GW33, FT)
- Orlando Pirates 1–0 Espérance ST (CAF Champions League Semi-Final, LIVE 67')
- AmaZulu FC 0–0 Cape Town Spurs (Betway Premiership GW33, LIVE 45+2')
Sundowns are 12 points clear at the top (GW33). Orlando Pirates are in the CAF CL semi-final second leg on 14 May in Tunisia. The Nedbank Cup Final is Sundowns vs Pirates on 17 May.`;
  const prompt=`You are the live news AI for SA Kicker, South Africa's #1 football news site. Based on these real match facts, generate 3 short, punchy news digest items about today's PSL and CAF action. Each item must have: a category tag (e.g. PSL, CAF CL, LIVE), a bold headline (max 12 words), and a 1-sentence summary (max 25 words). Respond ONLY with valid JSON array, no markdown fences. Example format: [{"tag":"PSL","headline":"Sundowns Demolish City in Title Showdown","summary":"Three first-half goals sealed Sundowns' 15th win of the season in a dominant display.","icon":"⚽"},{"tag":"CAF CL","headline":"Pirates Hold the Lead in Tunis","summary":"Makgopa's powerful 44th-minute header gives Bucs the edge with 23 minutes remaining.","icon":"☠️"},{"tag":"LIVE","headline":"AmaZulu Grind Out Stalemate at Half Time","summary":"A tight 0–0 at the break as both sides cancel each other out in Durban.","icon":"🔴"}]. Match facts: ${matchContext}`;
  try {
    const res=await fetch('https://api.anthropic.com/v1/messages',{
      method:'POST',
      headers:{'Content-Type':'application/json'},
      body:JSON.stringify({
        model:'claude-sonnet-4-20250514',
        max_tokens:1000,
        messages:[{role:'user',content:prompt}]
      })
    });
    const data=await res.json();
    const raw=data.content.map(i=>i.text||'').join('');
    const clean=raw.replace(/```json|```/g,'').trim();
    const items=JSON.parse(clean);
    const now=new Date();
    ts.textContent=`Updated ${now.toLocaleTimeString('en-ZA',{hour:'2-digit',minute:'2-digit'})} SAST`;
    body.innerHTML=`<div class="lnp-items">${items.map(it=>`
      <div class="lnp-item">
        <div class="lnp-badge-wrap">
          <div class="lnp-icon">${it.icon}</div>
          <div class="lnp-tag">${it.tag}</div>
        </div>
        <div>
          <div class="lnp-headline">${it.headline}</div>
          <div class="lnp-summary">${it.summary}</div>
          <div class="lnp-timestamp">AI Digest · 9 May 2026</div>
        </div>
      </div>`).join('')}</div>`;
  } catch(err){
    body.innerHTML=`<div class="lnp-error">⚠ Could not load AI digest. <span style="color:var(--muted);font-size:12px;margin-left:8px;">${err.message}</span></div>`;
    ts.textContent='Update failed';
  }
  btn.disabled=false;
  btn.textContent='⟳ Refresh';
}

// ── AUTO-REFRESH LIVE PANEL every 3 minutes ──
fetchLiveNews();
setInterval(fetchLiveNews, 3*60*1000);

// ── INIT ──
renderStat('goals');
renderTW(0);
</script>
</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>IRONFORGE GYM</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Barlow:wght@300;400;500;600;700&family=Barlow+Condensed:wght@600;700&display=swap" rel="stylesheet">
<style>
:root {
  --black:#0a0a0a; --red:#e63022; --red-dark:#b8200f;
  --white:#f5f0eb; --gray:#1a1a1a; --gray-mid:#2e2e2e; --gray-light:#888;
}
*{margin:0;padding:0;box-sizing:border-box;}
html{scroll-behavior:smooth;}
body{background:var(--black);color:var(--white);font-family:'Barlow',sans-serif;overflow-x:hidden;}

/* NAV */
nav{position:fixed;top:0;left:0;right:0;z-index:100;display:flex;align-items:center;justify-content:space-between;padding:0 4rem;height:72px;background:rgba(10,10,10,0.92);backdrop-filter:blur(10px);border-bottom:1px solid rgba(230,48,34,0.2);}
.nav-logo{font-family:'Bebas Neue',sans-serif;font-size:2rem;letter-spacing:0.12em;color:var(--white);text-decoration:none;cursor:pointer;}
.nav-logo span{color:var(--red);}
.nav-links{display:flex;gap:2.5rem;list-style:none;}
.nav-links a{color:var(--gray-light);text-decoration:none;font-size:0.85rem;font-weight:600;letter-spacing:0.12em;text-transform:uppercase;transition:color 0.2s;cursor:pointer;}
.nav-links a:hover,.nav-links a.active{color:var(--red);}
.nav-cta{background:var(--red);color:var(--white);border:none;cursor:pointer;padding:0.6rem 1.4rem;font-family:'Barlow',sans-serif;font-weight:700;font-size:0.8rem;letter-spacing:0.1em;text-transform:uppercase;clip-path:polygon(8px 0%,100% 0%,calc(100% - 8px) 100%,0% 100%);transition:background 0.2s;text-decoration:none;}
.nav-cta:hover{background:var(--red-dark);}

/* PAGES */
.page{display:none;}
.page.active{display:block;}

/* PAGE HERO (about/contact/privacy) */
.page-hero{min-height:42vh;display:flex;align-items:flex-end;padding:4rem;padding-top:72px;position:relative;overflow:hidden;}
.page-hero-bg{position:absolute;inset:0;z-index:0;background:linear-gradient(to right,rgba(10,10,10,0.98) 50%,rgba(10,10,10,0.6)),#1a1a1a;}
.page-hero-stripe{position:absolute;top:0;right:0;width:40%;height:100%;background:repeating-linear-gradient(-45deg,transparent,transparent 20px,rgba(230,48,34,0.04) 20px,rgba(230,48,34,0.04) 40px);}
.page-hero-content{position:relative;z-index:1;}
.breadcrumb{font-size:0.75rem;letter-spacing:0.15em;text-transform:uppercase;color:#555;margin-bottom:1rem;}
.breadcrumb a{color:var(--red);cursor:pointer;text-decoration:none;}
.page-title{font-family:'Bebas Neue',sans-serif;font-size:clamp(4rem,8vw,7rem);letter-spacing:0.04em;line-height:0.9;}
.page-title span{color:var(--red);}
.page-meta{font-size:0.85rem;color:#555;margin-top:1rem;}
.page-meta strong{color:#888;}

/* COMMON SECTION */
section{padding:6rem 4rem;}
.section-tag{font-size:0.7rem;font-weight:700;letter-spacing:0.25em;text-transform:uppercase;color:var(--red);margin-bottom:0.8rem;}
.section-title{font-family:'Bebas Neue',sans-serif;font-size:clamp(2.5rem,5vw,4rem);letter-spacing:0.05em;line-height:1;margin-bottom:1.5rem;}

/* ─── HOME ─── */
.hero{min-height:100vh;display:flex;align-items:center;position:relative;padding:0 4rem;padding-top:72px;overflow:hidden;}
.hero-bg{position:absolute;inset:0;z-index:0;background:linear-gradient(105deg,rgba(10,10,10,0.97) 40%,rgba(10,10,10,0.5) 100%),url('https://images.unsplash.com/photo-1534438327276-14e5300c3a48?w=1600&q=80') center/cover no-repeat;}
.hero-content{position:relative;z-index:1;max-width:700px;}
.hero-tag{display:inline-block;font-size:0.75rem;font-weight:700;letter-spacing:0.2em;text-transform:uppercase;color:var(--red);border:1px solid var(--red);padding:0.3rem 0.9rem;margin-bottom:1.5rem;}
.hero h1{font-family:'Bebas Neue',sans-serif;font-size:clamp(5rem,12vw,10rem);line-height:0.9;letter-spacing:0.03em;}
.hero h1 em{color:var(--red);font-style:normal;display:block;}
.hero-sub{font-size:1.1rem;font-weight:300;color:#aaa;max-width:480px;margin:1.5rem 0 2.5rem;line-height:1.7;}
.hero-btns{display:flex;gap:1rem;flex-wrap:wrap;}
.btn-primary{background:var(--red);color:var(--white);text-decoration:none;padding:1rem 2.2rem;font-weight:700;letter-spacing:0.1em;text-transform:uppercase;font-size:0.9rem;clip-path:polygon(10px 0%,100% 0%,calc(100% - 10px) 100%,0% 100%);transition:background 0.2s;cursor:pointer;border:none;font-family:'Barlow',sans-serif;}
.btn-primary:hover{background:var(--red-dark);}
.btn-secondary{border:1px solid rgba(245,240,235,0.3);color:var(--white);text-decoration:none;padding:1rem 2.2rem;font-weight:600;letter-spacing:0.1em;text-transform:uppercase;font-size:0.9rem;transition:border-color 0.2s;cursor:pointer;background:transparent;font-family:'Barlow',sans-serif;}
.btn-secondary:hover{border-color:var(--red);}
.hero-stats{position:absolute;bottom:3rem;right:4rem;z-index:1;display:flex;gap:3rem;}
.stat{text-align:center;}
.stat-num{font-family:'Bebas Neue',sans-serif;font-size:3rem;color:var(--red);line-height:1;letter-spacing:0.05em;}
.stat-label{font-size:0.7rem;letter-spacing:0.15em;text-transform:uppercase;color:#777;margin-top:0.2rem;}

.features{background:var(--gray);}
.features-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:1px;margin-top:3rem;border:1px solid var(--gray-mid);background:var(--gray-mid);}
.feature-card{background:var(--gray);padding:2.5rem 2rem;position:relative;overflow:hidden;transition:background 0.3s;}
.feature-card:hover{background:var(--gray-mid);}
.feature-num{font-family:'Bebas Neue',sans-serif;font-size:5rem;color:rgba(230,48,34,0.1);line-height:1;position:absolute;top:1rem;right:1.5rem;transition:color 0.3s;}
.feature-card:hover .feature-num{color:rgba(230,48,34,0.2);}
.feature-icon{font-size:1.8rem;margin-bottom:1rem;}
.feature-name{font-family:'Barlow Condensed',sans-serif;font-size:1.3rem;font-weight:700;letter-spacing:0.05em;text-transform:uppercase;margin-bottom:0.6rem;}
.feature-desc{font-size:0.9rem;color:#888;line-height:1.6;}

.classes-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(300px,1fr));gap:1.5rem;margin-top:3rem;}
.class-card{position:relative;height:380px;overflow:hidden;cursor:pointer;}
.class-img{width:100%;height:100%;display:flex;align-items:center;justify-content:center;transition:transform 0.5s;}
.class-card:hover .class-img{transform:scale(1.05);}
.class-overlay{position:absolute;inset:0;background:linear-gradient(to top,rgba(10,10,10,0.95) 40%,transparent);display:flex;flex-direction:column;justify-content:flex-end;padding:2rem;}
.class-tag{font-size:0.65rem;font-weight:700;letter-spacing:0.2em;text-transform:uppercase;color:var(--red);margin-bottom:0.5rem;}
.class-name{font-family:'Bebas Neue',sans-serif;font-size:2rem;letter-spacing:0.05em;margin-bottom:0.5rem;}
.class-meta{font-size:0.8rem;color:#888;}
.bg1{background:#1a1520;}.bg2{background:#15201a;}.bg3{background:#201515;}.bg4{background:#151820;}.bg5{background:#20181a;}.bg6{background:#1a2015;}

.cta-banner{background:var(--red);padding:4rem;display:flex;align-items:center;justify-content:space-between;gap:2rem;flex-wrap:wrap;}
.cta-banner h2{font-family:'Bebas Neue',sans-serif;font-size:3rem;letter-spacing:0.05em;}
.cta-banner p{font-size:1rem;opacity:0.85;margin-top:0.3rem;}
.btn-dark{background:var(--black);color:var(--white);text-decoration:none;padding:1rem 2.2rem;font-weight:700;letter-spacing:0.1em;text-transform:uppercase;font-size:0.9rem;white-space:nowrap;clip-path:polygon(10px 0%,100% 0%,calc(100% - 10px) 100%,0% 100%);transition:opacity 0.2s;cursor:pointer;border:none;font-family:'Barlow',sans-serif;}
.btn-dark:hover{opacity:0.8;}

.pricing{background:var(--black);}
.pricing-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:1.5rem;margin-top:3rem;}
.plan{border:1px solid var(--gray-mid);padding:2.5rem 2rem;position:relative;transition:border-color 0.3s;}
.plan:hover{border-color:rgba(230,48,34,0.4);}
.plan.featured{border-color:var(--red);}
.plan-badge{position:absolute;top:-1px;left:2rem;background:var(--red);padding:0.2rem 0.8rem;font-size:0.65rem;font-weight:700;letter-spacing:0.15em;text-transform:uppercase;}
.plan-name{font-family:'Barlow Condensed',sans-serif;font-size:1.1rem;font-weight:700;letter-spacing:0.1em;text-transform:uppercase;color:#888;margin-bottom:1rem;}
.plan-price{display:flex;align-items:baseline;gap:0.3rem;margin-bottom:0.4rem;}
.plan-price .currency{font-size:1.2rem;font-weight:700;color:var(--red);margin-top:0.5rem;}
.plan-price .amount{font-family:'Bebas Neue',sans-serif;font-size:4rem;letter-spacing:0.03em;}
.plan-price .period{font-size:0.85rem;color:#666;}
.plan-divider{border:none;border-top:1px solid var(--gray-mid);margin:1.5rem 0;}
.plan-features{list-style:none;}
.plan-features li{font-size:0.9rem;color:#aaa;padding:0.4rem 0;display:flex;align-items:center;gap:0.6rem;}
.plan-features li::before{content:'–';color:var(--red);font-weight:700;}
.plan-features li.off{color:#444;}
.plan-features li.off::before{color:#333;}
.plan-btn{display:block;text-align:center;text-decoration:none;margin-top:2rem;padding:0.9rem;font-weight:700;letter-spacing:0.08em;text-transform:uppercase;font-size:0.85rem;transition:all 0.2s;border:1px solid var(--gray-mid);color:var(--white);cursor:pointer;background:transparent;font-family:'Barlow',sans-serif;width:100%;}
.plan-btn:hover,.plan.featured .plan-btn{background:var(--red);border-color:var(--red);}

/* ─── ABOUT ─── */
.story{background:var(--gray);}
.story-layout{display:grid;grid-template-columns:1fr 1fr;gap:6rem;align-items:center;}
.story-text p{font-size:1rem;color:#999;line-height:1.8;margin-bottom:1.2rem;}
.story-text p strong{color:var(--white);font-weight:600;}
.story-visual{position:relative;}
.big-year{font-family:'Bebas Neue',sans-serif;font-size:14rem;color:rgba(230,48,34,0.08);line-height:1;position:absolute;top:-2rem;right:-1rem;z-index:0;pointer-events:none;}
.milestones{position:relative;z-index:1;}
.milestone{display:flex;gap:1.5rem;padding:1.5rem 0;border-bottom:1px solid var(--gray-mid);}
.milestone:last-child{border-bottom:none;}
.milestone-year{font-family:'Bebas Neue',sans-serif;font-size:1.8rem;color:var(--red);letter-spacing:0.05em;min-width:70px;}
.milestone-info h4{font-size:1rem;font-weight:600;margin-bottom:0.3rem;}
.milestone-info p{font-size:0.85rem;color:#666;line-height:1.5;}

.team{background:var(--black);}
.team-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:1.5rem;margin-top:3rem;}
.trainer-card{position:relative;}
.trainer-img{width:100%;aspect-ratio:3/4;display:flex;align-items:center;justify-content:center;font-size:5rem;position:relative;overflow:hidden;}
.trainer-overlay{position:absolute;inset:0;background:linear-gradient(to top,var(--black) 0%,transparent 60%);display:flex;flex-direction:column;justify-content:flex-end;padding:1.5rem;}
.trainer-name{font-family:'Barlow Condensed',sans-serif;font-size:1.4rem;font-weight:700;letter-spacing:0.05em;text-transform:uppercase;}
.trainer-role{font-size:0.75rem;color:var(--red);font-weight:600;letter-spacing:0.1em;text-transform:uppercase;margin-top:0.2rem;}
.trainer-certs{font-size:0.75rem;color:#555;margin-top:0.5rem;}
.t-bg1{background:linear-gradient(135deg,#1a1520,#2a1030);}
.t-bg2{background:linear-gradient(135deg,#0f201a,#1a3020);}
.t-bg3{background:linear-gradient(135deg,#201515,#351520);}
.t-bg4{background:linear-gradient(135deg,#151820,#1a2535);}

.values{background:var(--gray);}
.values-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:2rem;margin-top:3rem;}
.value-item{border-left:3px solid var(--red);padding-left:1.5rem;}
.value-num{font-family:'Bebas Neue',sans-serif;font-size:3rem;color:var(--red);opacity:0.3;line-height:1;}
.value-name{font-family:'Barlow Condensed',sans-serif;font-size:1.2rem;font-weight:700;letter-spacing:0.08em;text-transform:uppercase;margin-bottom:0.5rem;}
.value-desc{font-size:0.9rem;color:#777;line-height:1.6;}

.awards-row{display:flex;gap:0;flex-wrap:wrap;border:1px solid var(--gray-mid);margin-top:3rem;}
.award{flex:1;min-width:200px;padding:2rem 1.5rem;text-align:center;border-right:1px solid var(--gray-mid);}
.award:last-child{border-right:none;}
.award-icon{font-size:2rem;margin-bottom:0.8rem;}
.award-title{font-size:0.95rem;font-weight:600;margin-bottom:0.3rem;}
.award-year{font-size:0.8rem;color:var(--red);font-weight:700;}

/* ─── CONTACT ─── */
.contact-section{padding:6rem 4rem;background:var(--gray);}
.contact-layout{display:grid;grid-template-columns:1fr 1.5fr;gap:6rem;align-items:start;}
.contact-info-item{display:flex;gap:1.2rem;margin-bottom:2rem;}
.info-icon{width:48px;height:48px;min-width:48px;border:1px solid var(--red);display:flex;align-items:center;justify-content:center;font-size:1.2rem;clip-path:polygon(6px 0%,100% 0%,calc(100% - 6px) 100%,0% 100%);}
.info-label{font-size:0.7rem;font-weight:700;letter-spacing:0.15em;text-transform:uppercase;color:var(--red);margin-bottom:0.3rem;}
.info-value{font-size:1rem;font-weight:500;}
.info-sub{font-size:0.85rem;color:#666;margin-top:0.2rem;}
.hours-table{width:100%;border-collapse:collapse;margin-top:1.5rem;}
.hours-table tr{border-bottom:1px solid var(--gray-mid);}
.hours-table td{padding:0.7rem 0;font-size:0.9rem;}
.hours-table td:last-child{text-align:right;color:#aaa;}
.hours-table tr.highlight td{color:var(--red);font-weight:600;}
.form-title{font-family:'Bebas Neue',sans-serif;font-size:2.5rem;letter-spacing:0.05em;margin-bottom:0.5rem;}
.form-subtitle{font-size:0.9rem;color:#666;margin-bottom:2.5rem;}
.form-row{display:grid;grid-template-columns:1fr 1fr;gap:1rem;}
.form-group{margin-bottom:1.2rem;}
.form-group label{display:block;font-size:0.72rem;font-weight:700;letter-spacing:0.12em;text-transform:uppercase;color:#666;margin-bottom:0.5rem;}
.form-group input,.form-group select,.form-group textarea{width:100%;background:var(--black);border:1px solid var(--gray-mid);color:var(--white);padding:0.85rem 1rem;font-family:'Barlow',sans-serif;font-size:0.95rem;transition:border-color 0.2s;resize:vertical;outline:none;}
.form-group input:focus,.form-group select:focus,.form-group textarea:focus{border-color:var(--red);}
.form-group select option{background:#1a1a1a;}
.submit-btn{background:var(--red);color:var(--white);border:none;cursor:pointer;padding:1rem 2.5rem;font-family:'Barlow',sans-serif;font-weight:700;font-size:0.9rem;letter-spacing:0.1em;text-transform:uppercase;clip-path:polygon(10px 0%,100% 0%,calc(100% - 10px) 100%,0% 100%);transition:background 0.2s;width:100%;margin-top:0.5rem;}
.submit-btn:hover{background:var(--red-dark);}
.success-msg{display:none;background:rgba(39,120,60,0.15);border:1px solid rgba(39,120,60,0.4);color:#5de88a;padding:1rem 1.2rem;font-size:0.9rem;margin-top:1rem;}
.map-placeholder{height:280px;background:var(--gray-mid);display:flex;flex-direction:column;align-items:center;justify-content:center;gap:0.8rem;border-top:3px solid var(--red);}
.map-placeholder span{font-size:3rem;}
.map-placeholder p{color:#666;font-size:0.9rem;}
.map-placeholder a{color:var(--red);text-decoration:none;font-weight:600;}
.social-section{padding:4rem;background:var(--gray);display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:2rem;}
.social-text h3{font-family:'Bebas Neue',sans-serif;font-size:2rem;letter-spacing:0.05em;}
.social-text p{color:#666;font-size:0.9rem;margin-top:0.3rem;}
.social-links{display:flex;gap:1rem;}
.social-link{width:48px;height:48px;border:1px solid var(--gray-mid);display:flex;align-items:center;justify-content:center;text-decoration:none;font-size:1.2rem;transition:border-color 0.2s,background 0.2s;clip-path:polygon(6px 0%,100% 0%,calc(100% - 6px) 100%,0% 100%);}
.social-link:hover{border-color:var(--red);background:rgba(230,48,34,0.1);}

/* ─── PRIVACY ─── */
.policy-layout{display:grid;grid-template-columns:260px 1fr;gap:5rem;padding:5rem 4rem;align-items:start;}
.toc{position:sticky;top:100px;}
.toc-title{font-size:0.7rem;font-weight:700;letter-spacing:0.2em;text-transform:uppercase;color:var(--red);margin-bottom:1.2rem;}
.toc ul{list-style:none;}
.toc ul li{border-left:2px solid var(--gray-mid);padding-left:1rem;margin-bottom:0;}
.toc ul li.toc-active{border-left-color:var(--red);}
.toc ul a{display:block;padding:0.5rem 0;color:#555;text-decoration:none;font-size:0.85rem;transition:color 0.2s;cursor:pointer;}
.toc ul a:hover{color:var(--white);}
.toc ul li.toc-active a{color:var(--red);}
.policy-section{margin-bottom:4rem;padding-bottom:4rem;border-bottom:1px solid var(--gray-mid);}
.policy-section:last-child{border-bottom:none;margin-bottom:0;padding-bottom:0;}
.policy-num{font-family:'Bebas Neue',sans-serif;font-size:4rem;color:rgba(230,48,34,0.12);letter-spacing:0.05em;line-height:1;}
.policy-heading{font-family:'Bebas Neue',sans-serif;font-size:2.2rem;letter-spacing:0.05em;margin-bottom:1.5rem;}
.policy-heading span{color:var(--red);}
.policy-content-body p{font-size:0.97rem;color:#999;line-height:1.85;margin-bottom:1.2rem;}
.policy-content-body p strong{color:var(--white);font-weight:600;}
.policy-content-body ul{list-style:none;margin:1rem 0 1.5rem;}
.policy-content-body ul li{font-size:0.95rem;color:#888;padding:0.5rem 0 0.5rem 1.5rem;position:relative;border-bottom:1px solid rgba(46,46,46,0.5);}
.policy-content-body ul li:last-child{border-bottom:none;}
.policy-content-body ul li::before{content:'→';position:absolute;left:0;color:var(--red);font-weight:700;}
.highlight-box{border-left:3px solid var(--red);padding:1.2rem 1.5rem;background:rgba(230,48,34,0.05);margin:1.5rem 0;font-size:0.9rem;color:#aaa;line-height:1.7;}
.highlight-box strong{color:var(--white);}
.contact-box{border:1px solid var(--gray-mid);padding:2rem;margin-top:2rem;}
.contact-box h4{font-family:'Barlow Condensed',sans-serif;font-size:1.1rem;font-weight:700;letter-spacing:0.08em;text-transform:uppercase;margin-bottom:1rem;}
.contact-box p{font-size:0.9rem;color:#888;line-height:1.9;}
.contact-box a{color:var(--red);text-decoration:none;}
.contact-box a:hover{text-decoration:underline;}

/* FOOTER */
footer{background:var(--gray);border-top:1px solid var(--gray-mid);padding:4rem;display:grid;grid-template-columns:2fr 1fr 1fr 1fr;gap:3rem;}
.footer-brand .nav-logo-foot{display:block;margin-bottom:1rem;font-size:2.2rem;font-family:'Bebas Neue',sans-serif;letter-spacing:0.12em;color:var(--white);cursor:pointer;}
.footer-brand .nav-logo-foot span{color:var(--red);}
.footer-brand p{font-size:0.9rem;color:#666;line-height:1.7;max-width:280px;}
.footer-col h4{font-size:0.7rem;font-weight:700;letter-spacing:0.2em;text-transform:uppercase;color:var(--red);margin-bottom:1.2rem;}
.footer-col ul{list-style:none;}
.footer-col ul li{margin-bottom:0.7rem;}
.footer-col ul a{color:#666;text-decoration:none;font-size:0.9rem;transition:color 0.2s;cursor:pointer;}
.footer-col ul a:hover{color:var(--white);}
.footer-bottom{background:var(--black);padding:1.5rem 4rem;display:flex;justify-content:space-between;align-items:center;border-top:1px solid var(--gray-mid);font-size:0.8rem;color:#555;}
.footer-bottom a{color:#555;text-decoration:none;cursor:pointer;}
.footer-bottom a:hover{color:var(--white);}

/* RESPONSIVE */
@media(max-width:900px){
  .policy-layout{grid-template-columns:1fr;gap:0;}
  .toc{position:static;margin-bottom:3rem;}
}
@media(max-width:768px){
  nav{padding:0 1.5rem;} .nav-links{display:none;}
  section{padding:4rem 1.5rem;}
  .hero{padding:0 1.5rem;padding-top:72px;} .hero-stats{display:none;}
  .story-layout{grid-template-columns:1fr;gap:3rem;} .big-year{font-size:7rem;}
  .contact-section{padding:4rem 1.5rem;} .contact-layout{grid-template-columns:1fr;gap:3rem;}
  .form-row{grid-template-columns:1fr;} .social-section{padding:3rem 1.5rem;}
  .page-hero{padding:3rem 1.5rem;padding-top:72px;}
  .policy-layout{padding:3rem 1.5rem;}
  .cta-banner{padding:3rem 1.5rem;}
  footer{grid-template-columns:1fr 1fr;padding:3rem 1.5rem;}
  .footer-bottom{padding:1.5rem;flex-direction:column;gap:0.5rem;text-align:center;}
}
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a class="nav-logo" onclick="showPage('home')">IRON<span>FORGE</span></a>
  <ul class="nav-links">
    <li><a onclick="showPage('home')" id="nav-home" class="active">Home</a></li>
    <li><a onclick="showPage('about')" id="nav-about">About</a></li>
    <li><a onclick="showPage('contact')" id="nav-contact">Contact</a></li>
    <li><a onclick="showPage('privacy')" id="nav-privacy">Privacy</a></li>
  </ul>
  <a class="nav-cta" onclick="showPage('contact')">Join Now</a>
</nav>

<!-- ══════════════════════════════════════════════ HOME ══ -->
<div id="page-home" class="page active">

  <section class="hero" style="padding:0 4rem;padding-top:72px;">
    <div class="hero-bg"></div>
    <div class="hero-content">
      <div class="hero-tag">Est. 2010 · Kathmandu's Premier Gym</div>
      <h1>FORGE<em>YOUR LIMITS</em></h1>
      <p class="hero-sub">Elite training, world-class equipment, and coaches who push you beyond what you thought possible. This is not just a gym. This is your transformation.</p>
      <div class="hero-btns">
        <button class="btn-primary" onclick="showPage('contact')">Start Your Journey</button>
        <button class="btn-secondary" onclick="showPage('about')">Learn More</button>
      </div>
    </div>
    <div class="hero-stats">
      <div class="stat"><div class="stat-num">2K+</div><div class="stat-label">Members</div></div>
      <div class="stat"><div class="stat-num">30+</div><div class="stat-label">Classes</div></div>
      <div class="stat"><div class="stat-num">15+</div><div class="stat-label">Trainers</div></div>
      <div class="stat"><div class="stat-num">12</div><div class="stat-label">Years</div></div>
    </div>
  </section>

  <section class="features">
    <div class="section-tag">Why Ironforge</div>
    <div class="section-title">BUILT FOR ATHLETES,<br>OPEN TO ALL</div>
    <div class="features-grid">
      <div class="feature-card"><div class="feature-num">01</div><div class="feature-icon">🏋️</div><div class="feature-name">Pro Equipment</div><p class="feature-desc">State-of-the-art Rogue, Life Fitness & Hammer Strength gear across 18,000 sq ft of training floor.</p></div>
      <div class="feature-card"><div class="feature-num">02</div><div class="feature-icon">🔥</div><div class="feature-name">Expert Coaching</div><p class="feature-desc">Certified coaches with backgrounds in powerlifting, bodybuilding, CrossFit, and sports conditioning.</p></div>
      <div class="feature-card"><div class="feature-num">03</div><div class="feature-icon">⚡</div><div class="feature-name">24/7 Access</div><p class="feature-desc">Train on your schedule. Smart entry system keeps the iron accessible around the clock, every day.</p></div>
      <div class="feature-card"><div class="feature-num">04</div><div class="feature-icon">🧬</div><div class="feature-name">Nutrition Lab</div><p class="feature-desc">Full nutrition analysis, meal planning services, and an in-house supplement shop to fuel your goals.</p></div>
    </div>
  </section>

  <section style="padding:6rem 4rem;background:var(--black);">
    <div style="display:flex;justify-content:space-between;align-items:flex-end;flex-wrap:wrap;gap:1rem;margin-bottom:3rem;">
      <div><div class="section-tag">What We Offer</div><div class="section-title" style="margin-bottom:0;">OUR CLASSES</div></div>
      <button class="btn-secondary" onclick="showPage('contact')">View Full Schedule</button>
    </div>
    <div class="classes-grid">
      <div class="class-card"><div class="class-img bg1" style="font-size:5rem;">🥊</div><div class="class-overlay"><div class="class-tag">Cardio · Combat</div><div class="class-name">MUAY THAI BOXING</div><div class="class-meta">60 min · All Levels · Mon/Wed/Fri</div></div></div>
      <div class="class-card"><div class="class-img bg2" style="font-size:5rem;">🏋️</div><div class="class-overlay"><div class="class-tag">Strength · Power</div><div class="class-name">POWERLIFTING</div><div class="class-meta">75 min · Intermediate · Tue/Thu/Sat</div></div></div>
      <div class="class-card"><div class="class-img bg3" style="font-size:5rem;">🔄</div><div class="class-overlay"><div class="class-tag">Conditioning</div><div class="class-name">HIIT CIRCUIT</div><div class="class-meta">45 min · All Levels · Daily</div></div></div>
      <div class="class-card"><div class="class-img bg4" style="font-size:5rem;">🧘</div><div class="class-overlay"><div class="class-tag">Recovery · Flex</div><div class="class-name">YOGA & STRETCH</div><div class="class-meta">60 min · All Levels · Sun/Wed</div></div></div>
      <div class="class-card"><div class="class-img bg5" style="font-size:5rem;">🚴</div><div class="class-overlay"><div class="class-tag">Cardio · Endurance</div><div class="class-name">SPIN CYCLING</div><div class="class-meta">45 min · All Levels · Mon-Sat</div></div></div>
      <div class="class-card"><div class="class-img bg6" style="font-size:5rem;">🤸</div><div class="class-overlay"><div class="class-tag">Athletic · Functional</div><div class="class-name">CROSSFIT WOD</div><div class="class-meta">60 min · Advanced · Tue/Thu/Sat</div></div></div>
    </div>
  </section>

  <div class="cta-banner">
    <div><h2>READY TO TRANSFORM?</h2><p>Get your first week free. No commitment. Just results.</p></div>
    <button class="btn-dark" onclick="showPage('contact')">Claim Free Trial</button>
  </div>

  <section class="pricing">
    <div style="text-align:center;margin-bottom:0.5rem;"><div class="section-tag" style="display:inline-block;">Membership Plans</div></div>
    <div class="section-title" style="text-align:center;">CHOOSE YOUR LEVEL</div>
    <div class="pricing-grid" style="max-width:1000px;margin:3rem auto 0;">
      <div class="plan">
        <div class="plan-name">Starter</div>
        <div class="plan-price"><span class="currency">Rs.</span><span class="amount">2500</span><span class="period">/mo</span></div>
        <p style="font-size:0.8rem;color:#555;">Gym floor access only</p>
        <hr class="plan-divider">
        <ul class="plan-features"><li>Gym floor access</li><li>Locker room</li><li>Free weights & machines</li><li class="off">Group classes</li><li class="off">Personal training</li><li class="off">Nutrition consult</li></ul>
        <button class="plan-btn" onclick="showPage('contact')">Get Started</button>
      </div>
      <div class="plan featured">
        <div class="plan-badge">Most Popular</div>
        <div class="plan-name">Pro</div>
        <div class="plan-price"><span class="currency">Rs.</span><span class="amount">4500</span><span class="period">/mo</span></div>
        <p style="font-size:0.8rem;color:#555;">Full access + classes</p>
        <hr class="plan-divider">
        <ul class="plan-features"><li>Everything in Starter</li><li>All group classes</li><li>Sauna & recovery zone</li><li>1 nutrition consult</li><li class="off">Personal training</li><li class="off">Priority booking</li></ul>
        <button class="plan-btn" onclick="showPage('contact')">Get Started</button>
      </div>
      <div class="plan">
        <div class="plan-name">Elite</div>
        <div class="plan-price"><span class="currency">Rs.</span><span class="amount">8000</span><span class="period">/mo</span></div>
        <p style="font-size:0.8rem;color:#555;">The full Ironforge experience</p>
        <hr class="plan-divider">
        <ul class="plan-features"><li>Everything in Pro</li><li>4x personal training</li><li>Monthly body assessment</li><li>Custom meal plan</li><li>Priority class booking</li><li>Guest passes (2/mo)</li></ul>
        <button class="plan-btn" onclick="showPage('contact')">Get Started</button>
      </div>
    </div>
  </section>

  <footer>
    <div class="footer-brand">
      <span class="nav-logo-foot" onclick="showPage('home')">IRON<span>FORGE</span></span>
      <p>Kathmandu's premier training facility since 2010. Every rep, every drop of sweat builds the person you're becoming.</p>
    </div>
    <div class="footer-col"><h4>Navigate</h4><ul><li><a onclick="showPage('home')">Home</a></li><li><a onclick="showPage('about')">About Us</a></li><li><a onclick="showPage('contact')">Contact</a></li><li><a onclick="showPage('privacy')">Privacy Policy</a></li></ul></div>
    <div class="footer-col"><h4>Services</h4><ul><li><a>Personal Training</a></li><li><a>Group Classes</a></li><li><a>Nutrition Plans</a></li><li><a>Body Assessment</a></li></ul></div>
    <div class="footer-col"><h4>Hours</h4><ul><li><a>Mon–Fri: 5am–11pm</a></li><li><a>Saturday: 6am–10pm</a></li><li><a>Sunday: 7am–8pm</a></li><li><a>Members: 24/7 Access</a></li></ul></div>
  </footer>
  <div class="footer-bottom">
    <span>© 2026 Ironforge Gym. All rights reserved.</span>
    <div style="display:flex;gap:1.5rem;"><a onclick="showPage('privacy')">Privacy Policy</a><a>Terms of Service</a></div>
  </div>
</div>

<!-- ══════════════════════════════════════════════ ABOUT ══ -->
<div id="page-about" class="page">

  <div class="page-hero">
    <div class="page-hero-bg"></div><div class="page-hero-stripe"></div>
    <div class="page-hero-content">
      <div class="breadcrumb"><a onclick="showPage('home')">Home</a> / About</div>
      <div class="page-title">ABOUT<br><span>IRONFORGE</span></div>
    </div>
  </div>

  <section class="story">
    <div class="story-layout">
      <div class="story-text">
        <div class="section-tag">Our Story</div>
        <div class="section-title">BUILT FROM<br>SWEAT & IRON</div>
        <p>Ironforge was founded in <strong>2010 by Rajan Shrestha</strong>, a former national powerlifting champion who believed Kathmandu deserved a world-class training facility that didn't compromise on equipment, coaching, or culture.</p>
        <p>What started as a <strong>4,000 sq ft warehouse with second-hand barbells</strong> has grown into Nepal's most respected fitness institution — an 18,000 sq ft facility serving over 2,000 members across every fitness level and discipline.</p>
        <p>We don't believe in trends. We believe in <strong>compound movements, progressive overload, consistent effort</strong>, and a community that holds each other accountable. The iron doesn't lie, and neither do we.</p>
      </div>
      <div class="story-visual">
        <div class="big-year">2010</div>
        <div class="milestones">
          <div class="milestone"><div class="milestone-year">2010</div><div class="milestone-info"><h4>Ironforge Opens</h4><p>First location in Thamel with 4,000 sq ft and 120 founding members.</p></div></div>
          <div class="milestone"><div class="milestone-year">2013</div><div class="milestone-info"><h4>Expansion to New Baneshwor</h4><p>Second facility opened, doubling capacity to 600+ active members.</p></div></div>
          <div class="milestone"><div class="milestone-year">2017</div><div class="milestone-info"><h4>18,000 sq ft Flagship</h4><p>Flagship Lazimpat location launched with full recovery and nutrition services.</p></div></div>
          <div class="milestone"><div class="milestone-year">2022</div><div class="milestone-info"><h4>2,000+ Members Milestone</h4><p>Reached community milestone with 15 certified coaches and 30+ weekly classes.</p></div></div>
        </div>
      </div>
    </div>
  </section>

  <section class="values">
    <div style="text-align:center;margin-bottom:0.5rem;"><div class="section-tag" style="display:inline-block;">What We Stand For</div></div>
    <div class="section-title" style="text-align:center;">OUR CORE VALUES</div>
    <div class="values-grid">
      <div class="value-item"><div class="value-num">01</div><div class="value-name">No Excuses</div><p class="value-desc">Discipline is the bridge between goals and achievement. We build it, rep by rep.</p></div>
      <div class="value-item"><div class="value-num">02</div><div class="value-name">Community First</div><p class="value-desc">You lift heavier with the right people beside you. Our culture is our strength.</p></div>
      <div class="value-item"><div class="value-num">03</div><div class="value-name">Expert Guidance</div><p class="value-desc">Every coach here earns their place. Science-backed methods, not bro-science.</p></div>
      <div class="value-item"><div class="value-num">04</div><div class="value-name">Inclusive Space</div><p class="value-desc">Beginner or elite, this is your house. Ego stays at the door, iron stays inside.</p></div>
      <div class="value-item"><div class="value-num">05</div><div class="value-name">Always Improving</div><p class="value-desc">We reinvest in the facility, our coaches, and our programs every year.</p></div>
    </div>
  </section>

  <section class="team">
    <div class="section-tag">The Coaches</div>
    <div class="section-title">MEET YOUR TEAM</div>
    <div class="team-grid">
      <div class="trainer-card"><div class="trainer-img t-bg1">🏋️<div class="trainer-overlay"><div class="trainer-name">Rajan Shrestha</div><div class="trainer-role">Founder & Head Coach</div><div class="trainer-certs">NSCA-CSCS · Former National Champion</div></div></div></div>
      <div class="trainer-card"><div class="trainer-img t-bg2">🥊<div class="trainer-overlay"><div class="trainer-name">Aisha Tamang</div><div class="trainer-role">Combat & Conditioning</div><div class="trainer-certs">Muay Thai Level 3 · ACE-CPT</div></div></div></div>
      <div class="trainer-card"><div class="trainer-img t-bg3">🔥<div class="trainer-overlay"><div class="trainer-name">Dev Karmacharya</div><div class="trainer-role">Strength & Nutrition</div><div class="trainer-certs">ISSA-Nutritionist · NASM-CPT</div></div></div></div>
      <div class="trainer-card"><div class="trainer-img t-bg4">🧘<div class="trainer-overlay"><div class="trainer-name">Priya Rai</div><div class="trainer-role">Yoga & Recovery</div><div class="trainer-certs">RYT-500 · Mobility Specialist</div></div></div></div>
    </div>
  </section>

  <section style="padding:5rem 4rem;background:var(--gray);">
    <div class="section-tag" style="text-align:center;display:block;">Recognition</div>
    <div class="section-title" style="text-align:center;">AWARDS & PRESS</div>
    <div class="awards-row">
      <div class="award"><div class="award-icon">🏆</div><div class="award-title">Best Gym in Kathmandu</div><div class="award-year">Himalayan Times · 2023</div></div>
      <div class="award"><div class="award-icon">⭐</div><div class="award-title">Top Fitness Facility Nepal</div><div class="award-year">Fit Nepal Awards · 2022</div></div>
      <div class="award"><div class="award-icon">🎖️</div><div class="award-title">Excellence in Coaching</div><div class="award-year">Nepal Sports Council · 2021</div></div>
      <div class="award"><div class="award-icon">📰</div><div class="award-title">Featured: Best Gyms in Asia</div><div class="award-year">Asian Fitness Magazine · 2023</div></div>
    </div>
  </section>

  <footer>
    <div class="footer-brand"><span class="nav-logo-foot" onclick="showPage('home')">IRON<span>FORGE</span></span><p>Kathmandu's premier training facility since 2010. Every rep, every drop of sweat builds the person you're becoming.</p></div>
    <div class="footer-col"><h4>Navigate</h4><ul><li><a onclick="showPage('home')">Home</a></li><li><a onclick="showPage('about')">About Us</a></li><li><a onclick="showPage('contact')">Contact</a></li><li><a onclick="showPage('privacy')">Privacy Policy</a></li></ul></div>
    <div class="footer-col"><h4>Services</h4><ul><li><a>Personal Training</a></li><li><a>Group Classes</a></li><li><a>Nutrition Plans</a></li><li><a>Body Assessment</a></li></ul></div>
    <div class="footer-col"><h4>Hours</h4><ul><li><a>Mon–Fri: 5am–11pm</a></li><li><a>Saturday: 6am–10pm</a></li><li><a>Sunday: 7am–8pm</a></li><li><a>Members: 24/7 Access</a></li></ul></div>
  </footer>
  <div class="footer-bottom"><span>© 2026 Ironforge Gym. All rights reserved.</span><div style="display:flex;gap:1.5rem;"><a onclick="showPage('privacy')">Privacy Policy</a><a>Terms of Service</a></div></div>
</div>

<!-- ══════════════════════════════════════════════ CONTACT ══ -->
<div id="page-contact" class="page">

  <div class="page-hero">
    <div class="page-hero-bg"></div><div class="page-hero-stripe"></div>
    <div class="page-hero-content">
      <div class="breadcrumb"><a onclick="showPage('home')">Home</a> / Contact</div>
      <div class="page-title">GET IN<br><span>TOUCH</span></div>
    </div>
  </div>

  <section class="contact-section">
    <div class="contact-layout">
      <div>
        <div class="section-tag">Find Us</div>
        <div class="section-title" style="font-size:2.5rem;margin-bottom:2.5rem;">VISIT THE FORGE</div>
        <div class="contact-info-item"><div class="info-icon">📍</div><div><div class="info-label">Location</div><div class="info-value">Lazimpat Road, Kathmandu</div><div class="info-sub">Near Lazimpat Chowk, Opposite City Bank</div></div></div>
        <div class="contact-info-item"><div class="info-icon">📞</div><div><div class="info-label">Phone</div><div class="info-value">+977 01-4412345</div><div class="info-sub">+977 98012 34567 (WhatsApp)</div></div></div>
        <div class="contact-info-item"><div class="info-icon">✉️</div><div><div class="info-label">Email</div><div class="info-value">hello@ironforgekathmandu.com</div><div class="info-sub">We reply within 24 hours</div></div></div>
        <div style="border-top:1px solid var(--gray-mid);padding-top:2rem;margin-top:1rem;">
          <div class="section-tag">Hours of Operation</div>
          <table class="hours-table">
            <tr class="highlight"><td>Monday – Friday</td><td>5:00 AM – 11:00 PM</td></tr>
            <tr><td>Saturday</td><td>6:00 AM – 10:00 PM</td></tr>
            <tr><td>Sunday</td><td>7:00 AM – 8:00 PM</td></tr>
            <tr><td>Public Holidays</td><td>8:00 AM – 6:00 PM</td></tr>
            <tr><td>Members (24/7 Access)</td><td>Anytime</td></tr>
          </table>
        </div>
      </div>
      <div>
        <div class="form-title">SEND A MESSAGE</div>
        <p class="form-subtitle">Questions about membership, classes, or personal training? We'd love to hear from you.</p>
        <form onsubmit="handleContactSubmit(event)">
          <div class="form-row">
            <div class="form-group"><label>First Name</label><input type="text" placeholder="Rajan" required></div>
            <div class="form-group"><label>Last Name</label><input type="text" placeholder="Shrestha"></div>
          </div>
          <div class="form-row">
            <div class="form-group"><label>Email Address</label><input type="email" placeholder="you@email.com" required></div>
            <div class="form-group"><label>Phone Number</label><input type="tel" placeholder="+977 98XXXXXXXX"></div>
          </div>
          <div class="form-group"><label>I'm Interested In</label><select><option value="">Select a topic...</option><option>General Membership</option><option>Personal Training</option><option>Group Classes</option><option>Nutrition Consultation</option><option>Corporate Membership</option><option>Free Trial</option><option>Other</option></select></div>
          <div class="form-group"><label>Message</label><textarea rows="5" placeholder="Tell us a bit about your goals or questions..."></textarea></div>
          <button type="submit" class="submit-btn" id="contactBtn">Send Message →</button>
          <div class="success-msg" id="successMsg">✓ Message received! We'll get back to you within 24 hours.</div>
        </form>
      </div>
    </div>
  </section>

  <div class="map-placeholder">
    <span>🗺️</span>
    <p>Lazimpat Road, Kathmandu, Nepal</p>
    <a href="https://maps.google.com" target="_blank">Open in Google Maps →</a>
  </div>

  <div class="social-section">
    <div class="social-text"><h3>FOLLOW THE FORGE</h3><p>Daily motivation, class updates, and member transformations.</p></div>
    <div class="social-links">
      <a class="social-link">📘</a><a class="social-link">📸</a><a class="social-link">🐦</a><a class="social-link">▶️</a><a class="social-link">💬</a>
    </div>
  </div>

  <footer>
    <div class="footer-brand"><span class="nav-logo-foot" onclick="showPage('home')">IRON<span>FORGE</span></span><p>Kathmandu's premier training facility since 2010. Every rep, every drop of sweat builds the person you're becoming.</p></div>
    <div class="footer-col"><h4>Navigate</h4><ul><li><a onclick="showPage('home')">Home</a></li><li><a onclick="showPage('about')">About Us</a></li><li><a onclick="showPage('contact')">Contact</a></li><li><a onclick="showPage('privacy')">Privacy Policy</a></li></ul></div>
    <div class="footer-col"><h4>Services</h4><ul><li><a>Personal Training</a></li><li><a>Group Classes</a></li><li><a>Nutrition Plans</a></li><li><a>Body Assessment</a></li></ul></div>
    <div class="footer-col"><h4>Hours</h4><ul><li><a>Mon–Fri: 5am–11pm</a></li><li><a>Saturday: 6am–10pm</a></li><li><a>Sunday: 7am–8pm</a></li><li><a>Members: 24/7 Access</a></li></ul></div>
  </footer>
  <div class="footer-bottom"><span>© 2026 Ironforge Gym. All rights reserved.</span><div style="display:flex;gap:1.5rem;"><a onclick="showPage('privacy')">Privacy Policy</a><a>Terms of Service</a></div></div>
</div>

<!-- ══════════════════════════════════════════════ PRIVACY ══ -->
<div id="page-privacy" class="page">

  <div class="page-hero">
    <div class="page-hero-bg"></div><div class="page-hero-stripe"></div>
    <div class="page-hero-content">
      <div class="breadcrumb"><a onclick="showPage('home')">Home</a> / Privacy Policy</div>
      <div class="page-title">PRIVACY<br><span>POLICY</span></div>
      <div class="page-meta">Last Updated: <strong>April 20, 2026</strong> · Effective: <strong>April 20, 2026</strong></div>
    </div>
  </div>

  <div class="policy-layout">
    <aside class="toc">
      <div class="toc-title">On This Page</div>
      <ul>
        <li class="toc-active"><a onclick="scrollToPolicy('p-overview')">Overview</a></li>
        <li><a onclick="scrollToPolicy('p-collection')">Information We Collect</a></li>
        <li><a onclick="scrollToPolicy('p-use')">How We Use Your Data</a></li>
        <li><a onclick="scrollToPolicy('p-sharing')">Data Sharing</a></li>
        <li><a onclick="scrollToPolicy('p-security')">Data Security</a></li>
        <li><a onclick="scrollToPolicy('p-retention')">Data Retention</a></li>
        <li><a onclick="scrollToPolicy('p-rights')">Your Rights</a></li>
        <li><a onclick="scrollToPolicy('p-cookies')">Cookies</a></li>
        <li><a onclick="scrollToPolicy('p-minors')">Minors</a></li>
        <li><a onclick="scrollToPolicy('p-changes')">Policy Changes</a></li>
        <li><a onclick="scrollToPolicy('p-contact')">Contact Us</a></li>
      </ul>
    </aside>

    <main class="policy-content-body">

      <div class="policy-section" id="p-overview">
        <div class="policy-num">00</div>
        <h2 class="policy-heading">OVERVIEW & <span>COMMITMENT</span></h2>
        <p>Ironforge Gym ("Ironforge," "we," "our," or "us"), located at Lazimpat Road, Kathmandu, Nepal, is committed to protecting the privacy of our members, visitors, and users of our website and services.</p>
        <p>This Privacy Policy explains how we collect, use, disclose, and safeguard your information when you visit our facility, use our website, or engage with our services. By using our services, you agree to the practices described here.</p>
        <div class="highlight-box"><strong>Plain English Summary:</strong> We collect only what we need to run your membership and improve our services. We do not sell your personal data. You can request deletion of your data at any time.</div>
      </div>

      <div class="policy-section" id="p-collection">
        <div class="policy-num">01</div>
        <h2 class="policy-heading">INFORMATION <span>WE COLLECT</span></h2>
        <p>We collect information you provide directly and information gathered automatically when you use our services.</p>
        <p><strong>Personal Information You Provide:</strong></p>
        <ul>
          <li>Full name, date of birth, gender, and profile photo (for membership registration)</li>
          <li>Contact details: email address, phone number, postal address</li>
          <li>Emergency contact name and phone number</li>
          <li>Health declarations and any pre-existing conditions you disclose for safety purposes</li>
          <li>Payment information (processed securely via third-party providers; we do not store full card numbers)</li>
          <li>Membership preferences, class bookings, and training history</li>
          <li>Communications you send us via email, contact forms, or in person</li>
        </ul>
        <p><strong>Information Collected Automatically:</strong></p>
        <ul>
          <li>Website usage data: IP address, browser type, pages visited, time spent, referral source</li>
          <li>Device information: operating system, device identifiers</li>
          <li>Access log data from our smart entry system (check-in/check-out times)</li>
          <li>CCTV footage captured within the gym premises for security purposes</li>
          <li>Cookies and similar tracking technologies (see Section 8)</li>
        </ul>
      </div>

      <div class="policy-section" id="p-use">
        <div class="policy-num">02</div>
        <h2 class="policy-heading">HOW WE <span>USE YOUR DATA</span></h2>
        <p>We use the information we collect for the following purposes, all necessary to operate our gym and provide the best service:</p>
        <ul>
          <li>Processing and managing your gym membership, including billing and renewals</li>
          <li>Booking and managing class registrations and personal training sessions</li>
          <li>Sending transactional communications (receipts, booking confirmations, schedule changes)</li>
          <li>Sending promotional communications about new classes, offers, and events — only with your consent</li>
          <li>Ensuring the safety and security of our members and staff</li>
          <li>Personalising your experience and recommending relevant training programs</li>
          <li>Conducting internal analytics to improve our services and facilities</li>
          <li>Complying with legal obligations under Nepalese law</li>
          <li>Responding to your inquiries, feedback, or complaints</li>
        </ul>
        <div class="highlight-box"><strong>Marketing communications:</strong> You can opt out of promotional emails at any time by clicking "Unsubscribe" in any email or by contacting us directly. Opting out will not affect transactional communications related to your membership.</div>
      </div>

      <div class="policy-section" id="p-sharing">
        <div class="policy-num">03</div>
        <h2 class="policy-heading">DATA <span>SHARING</span></h2>
        <p>We do not sell, rent, or trade your personal information to third parties for their marketing purposes. We may share your information only in the following limited circumstances:</p>
        <ul>
          <li><strong>Service Providers:</strong> Trusted third-party vendors who assist in operating our business (payment processors, email platforms, booking software, cloud storage). These parties are contractually obligated to protect your data.</li>
          <li><strong>Legal Requirements:</strong> When required by applicable law, court order, or government authority in Nepal, or to protect the rights, property, or safety of Ironforge, our members, or others.</li>
          <li><strong>Business Transfers:</strong> In the event of a merger, acquisition, or sale of assets, your data may be transferred. We will notify you prior to any such transfer.</li>
          <li><strong>With Your Consent:</strong> In any other circumstance, we will seek your explicit consent before sharing your information.</li>
        </ul>
        <p>Our current service providers include: Stripe (payment processing), Mailchimp (email marketing), and Google Analytics (website analytics). Each provider maintains their own privacy policies.</p>
      </div>

      <div class="policy-section" id="p-security">
        <div class="policy-num">04</div>
        <h2 class="policy-heading">DATA <span>SECURITY</span></h2>
        <p>We implement appropriate technical and organisational measures to protect your personal information:</p>
        <ul>
          <li>SSL/TLS encryption for all data transmitted through our website</li>
          <li>Encrypted storage for sensitive member data and payment information</li>
          <li>Restricted access controls — staff access your data only on a need-to-know basis</li>
          <li>Regular security audits and vulnerability assessments</li>
          <li>Staff training on data protection and privacy best practices</li>
          <li>Physical security measures for on-premise systems and paper records</li>
        </ul>
        <div class="highlight-box"><strong>Please note:</strong> No method of transmission over the Internet is 100% secure. While we strive to use commercially acceptable means to protect your information, we cannot guarantee its absolute security.</div>
      </div>

      <div class="policy-section" id="p-retention">
        <div class="policy-num">05</div>
        <h2 class="policy-heading">DATA <span>RETENTION</span></h2>
        <p>We retain your personal information for as long as necessary to fulfil the purposes outlined in this policy, unless a longer retention period is required by law.</p>
        <ul>
          <li><strong>Active membership data:</strong> Retained for the duration of your membership plus 2 years after termination</li>
          <li><strong>Financial and payment records:</strong> Retained for 7 years as required by Nepalese tax and accounting law</li>
          <li><strong>Health declarations:</strong> Retained for 3 years after your last gym visit</li>
          <li><strong>CCTV footage:</strong> Overwritten on a rolling 30-day cycle, unless flagged for incident investigation</li>
          <li><strong>Marketing preferences:</strong> Retained until you withdraw consent or request deletion</li>
          <li><strong>Website analytics data:</strong> Anonymised and retained for up to 26 months</li>
        </ul>
      </div>

      <div class="policy-section" id="p-rights">
        <div class="policy-num">06</div>
        <h2 class="policy-heading">YOUR <span>RIGHTS</span></h2>
        <p>You have the following rights in relation to your personal information:</p>
        <ul>
          <li><strong>Right of Access:</strong> Request a copy of the personal data we hold about you</li>
          <li><strong>Right to Rectification:</strong> Request correction of inaccurate or incomplete data</li>
          <li><strong>Right to Erasure:</strong> Request deletion of your personal data, subject to legal retention obligations</li>
          <li><strong>Right to Restrict Processing:</strong> Request that we limit how we use your data in certain circumstances</li>
          <li><strong>Right to Data Portability:</strong> Receive your data in a structured, machine-readable format</li>
          <li><strong>Right to Object:</strong> Object to processing based on legitimate interests or for direct marketing</li>
          <li><strong>Right to Withdraw Consent:</strong> Withdraw consent at any time where processing is based on consent</li>
        </ul>
        <p>We will respond to all valid requests within <strong>30 days</strong>. We may need to verify your identity before processing your request. There is no charge for exercising your rights.</p>
      </div>

      <div class="policy-section" id="p-cookies">
        <div class="policy-num">07</div>
        <h2 class="policy-heading">COOKIES & <span>TRACKING</span></h2>
        <p>Our website uses cookies and similar tracking technologies to enhance your browsing experience and analyse site usage.</p>
        <ul>
          <li><strong>Essential cookies:</strong> Necessary for the website to function (session management, security). Cannot be disabled.</li>
          <li><strong>Analytics cookies:</strong> Help us understand how visitors use our site (Google Analytics). Can be opted out.</li>
          <li><strong>Marketing cookies:</strong> Used to deliver relevant advertisements. Only placed with your consent.</li>
          <li><strong>Preference cookies:</strong> Remember your settings and preferences for a better experience.</li>
        </ul>
        <p>You can manage cookie preferences through your browser settings at any time. Note that disabling certain cookies may affect website functionality.</p>
      </div>

      <div class="policy-section" id="p-minors">
        <div class="policy-num">08</div>
        <h2 class="policy-heading">MINORS & <span>CHILDREN</span></h2>
        <p>Our gym facilities and services are available to individuals aged 16 and above. For members aged 16–17, parental or guardian consent is required at registration.</p>
        <p>Our website is not directed at children under 16, and we do not knowingly collect personal data from children under 16 without verified parental consent. If you believe we have inadvertently collected such data, please contact us immediately and we will delete it promptly.</p>
      </div>

      <div class="policy-section" id="p-changes">
        <div class="policy-num">09</div>
        <h2 class="policy-heading">POLICY <span>CHANGES</span></h2>
        <p>We may update this Privacy Policy from time to time to reflect changes in our practices, services, or legal requirements. When we make material changes, we will:</p>
        <ul>
          <li>Update the "Last Updated" date at the top of this page</li>
          <li>Notify active members by email at least 14 days before changes take effect</li>
          <li>Display a notice on our website and at the front desk of our facility</li>
        </ul>
        <p>Your continued use of our services after the effective date constitutes your acceptance of the revised policy.</p>
      </div>

      <div class="policy-section" id="p-contact">
        <div class="policy-num">10</div>
        <h2 class="policy-heading">CONTACT <span>US</span></h2>
        <p>If you have any questions, concerns, or requests regarding this Privacy Policy or how we handle your personal data, please reach out to our Privacy Officer:</p>
        <div class="contact-box">
          <h4>Privacy Officer — Ironforge Gym</h4>
          <p>
            <strong style="color:var(--white);">By Email:</strong> <a href="mailto:privacy@ironforgekathmandu.com">privacy@ironforgekathmandu.com</a><br><br>
            <strong style="color:var(--white);">By Post:</strong><br>
            Ironforge Gym — Privacy Officer<br>
            Lazimpat Road, Kathmandu, Bagmati Province, Nepal<br><br>
            <strong style="color:var(--white);">By Phone:</strong> +977 01-4412345<br>
            (Monday–Friday, 9:00 AM – 6:00 PM NPT)<br><br>
            We aim to respond to all privacy-related enquiries within <strong style="color:var(--white);">5 business days</strong>.
          </p>
        </div>
      </div>

    </main>
  </div>

  <footer>
    <div class="footer-brand"><span class="nav-logo-foot" onclick="showPage('home')">IRON<span>FORGE</span></span><p>Kathmandu's premier training facility since 2010. Every rep, every drop of sweat builds the person you're becoming.</p></div>
    <div class="footer-col"><h4>Navigate</h4><ul><li><a onclick="showPage('home')">Home</a></li><li><a onclick="showPage('about')">About Us</a></li><li><a onclick="showPage('contact')">Contact</a></li><li><a onclick="showPage('privacy')">Privacy Policy</a></li></ul></div>
    <div class="footer-col"><h4>Services</h4><ul><li><a>Personal Training</a></li><li><a>Group Classes</a></li><li><a>Nutrition Plans</a></li><li><a>Body Assessment</a></li></ul></div>
    <div class="footer-col"><h4>Hours</h4><ul><li><a>Mon–Fri: 5am–11pm</a></li><li><a>Saturday: 6am–10pm</a></li><li><a>Sunday: 7am–8pm</a></li><li><a>Members: 24/7 Access</a></li></ul></div>
  </footer>
  <div class="footer-bottom"><span>© 2026 Ironforge Gym. All rights reserved.</span><div style="display:flex;gap:1.5rem;"><a onclick="showPage('privacy')">Privacy Policy</a><a>Terms of Service</a></div></div>
</div>

<script>
function showPage(id) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.querySelectorAll('.nav-links a').forEach(a => a.classList.remove('active'));
  document.getElementById('page-' + id).classList.add('active');
  const navLink = document.getElementById('nav-' + id);
  if (navLink) navLink.classList.add('active');
  window.scrollTo({top: 0, behavior: 'smooth'});
  // Reset contact form on nav
  if (id === 'contact') {
    document.getElementById('successMsg').style.display = 'none';
    document.getElementById('contactBtn').textContent = 'Send Message →';
    document.getElementById('contactBtn').disabled = false;
    document.getElementById('contactBtn').style.background = '';
  }
}

function scrollToPolicy(id) {
  document.getElementById(id).scrollIntoView({behavior:'smooth', block:'start'});
}

function handleContactSubmit(e) {
  e.preventDefault();
  const btn = document.getElementById('contactBtn');
  btn.textContent = 'Sending...';
  btn.disabled = true;
  setTimeout(() => {
    document.getElementById('successMsg').style.display = 'block';
    btn.textContent = 'Message Sent ✓';
    btn.style.background = '#27783c';
  }, 1200);
}

// Privacy TOC active state on scroll
const policySections = document.querySelectorAll('.policy-section');
const tocItems = document.querySelectorAll('.toc ul li');
window.addEventListener('scroll', () => {
  let current = '';
  policySections.forEach(s => {
    if (window.scrollY >= s.offsetTop - 200) current = s.id;
  });
  tocItems.forEach(li => {
    li.classList.remove('toc-active');
    const a = li.querySelector('a');
    if (a && a.getAttribute('onclick') && a.getAttribute('onclick').includes(current)) {
      li.classList.add('toc-active');
    }
  });
});
</script>
</body>
</html>

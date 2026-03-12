# digital-mandi1
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Digital Mandi – Direct Farmer to Dealer Marketplace</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet">
<style>
  :root {
    --g50: #f0faf0;
    --g100: #d4f1d4;
    --g200: #a8e6a8;
    --g400: #4caf50;
    --g500: #388e3c;
    --g600: #2e7d32;
    --g700: #1b5e20;
    --g800: #0d3b0d;
    --o400: #ff8c00;
    --o500: #e67e00;
    --o100: #fff3e0;
    --white: #ffffff;
    --bg: #f7faf7;
    --card: #ffffff;
    --text: #1a2e1a;
    --muted: #5a7a5a;
    --border: #c8e6c9;
    --shadow: 0 4px 24px rgba(46,125,50,0.10);
    --shadow-lg: 0 12px 40px rgba(46,125,50,0.15);
    --radius: 16px;
    --radius-sm: 10px;
    --transition: all 0.3s cubic-bezier(0.4,0,0.2,1);
  }
  *{box-sizing:border-box;margin:0;padding:0;}
  html{scroll-behavior:smooth;}
  body{font-family:'DM Sans',sans-serif;background:var(--bg);color:var(--text);overflow-x:hidden;}
  h1,h2,h3,h4{font-family:'Syne',sans-serif;}

  /* ── PAGE SYSTEM ── */
  .page{display:none;min-height:100vh;animation:fadeIn 0.4s ease;}
  .page.active{display:block;}
  @keyframes fadeIn{from{opacity:0;transform:translateY(12px);}to{opacity:1;transform:translateY(0);}}

  /* ── NAVBAR ── */
  nav{position:fixed;top:0;left:0;right:0;z-index:1000;background:rgba(255,255,255,0.95);backdrop-filter:blur(12px);border-bottom:1px solid var(--border);padding:0 5%;height:68px;display:flex;align-items:center;justify-content:space-between;transition:var(--transition);}
  .nav-logo{display:flex;align-items:center;gap:10px;text-decoration:none;}
  .nav-logo-icon{width:40px;height:40px;background:linear-gradient(135deg,var(--g500),var(--g700));border-radius:12px;display:flex;align-items:center;justify-content:center;font-size:20px;}
  .nav-logo span{font-family:'Syne',sans-serif;font-weight:800;font-size:1.3rem;color:var(--g700);}
  .nav-links{display:flex;gap:8px;align-items:center;}
  .nav-links a,.nav-links button{font-family:'DM Sans',sans-serif;font-size:0.9rem;font-weight:500;padding:8px 16px;border-radius:8px;border:none;cursor:pointer;text-decoration:none;color:var(--muted);background:none;transition:var(--transition);}
  .nav-links a:hover,.nav-links button:hover{color:var(--g600);background:var(--g50);}
  .btn-primary{background:var(--g500)!important;color:white!important;border-radius:10px!important;}
  .btn-primary:hover{background:var(--g600)!important;transform:translateY(-1px);}
  .lang-btn{border:1.5px solid var(--g400)!important;color:var(--g600)!important;}
  .hamburger{display:none;flex-direction:column;gap:5px;cursor:pointer;padding:8px;}
  .hamburger span{display:block;width:24px;height:2px;background:var(--g700);border-radius:2px;transition:var(--transition);}
  .mobile-menu{display:none;position:fixed;top:68px;left:0;right:0;background:white;border-bottom:1px solid var(--border);padding:1rem 5%;z-index:999;}
  .mobile-menu.open{display:flex;flex-direction:column;gap:8px;}
  .mobile-menu a,.mobile-menu button{padding:12px 16px;border-radius:10px;text-decoration:none;color:var(--text);font-size:0.95rem;font-weight:500;border:none;background:none;cursor:pointer;text-align:left;display:block;width:100%;}
  .mobile-menu a:hover,.mobile-menu button:hover{background:var(--g50);}

  /* ── HERO ── */
  .hero{padding:120px 5% 80px;min-height:100vh;display:flex;align-items:center;position:relative;overflow:hidden;}
  .hero::before{content:'';position:absolute;top:-100px;right:-150px;width:600px;height:600px;background:radial-gradient(circle,rgba(76,175,80,0.12),transparent 70%);pointer-events:none;}
  .hero::after{content:'';position:absolute;bottom:-80px;left:-100px;width:400px;height:400px;background:radial-gradient(circle,rgba(255,140,0,0.08),transparent 70%);pointer-events:none;}
  .hero-inner{max-width:1100px;margin:0 auto;width:100%;display:grid;grid-template-columns:1fr 1fr;gap:60px;align-items:center;}
  .hero-badge{display:inline-flex;align-items:center;gap:8px;background:var(--g50);border:1px solid var(--g200);border-radius:100px;padding:6px 16px;font-size:0.8rem;font-weight:500;color:var(--g600);margin-bottom:20px;}
  .hero-badge span{width:8px;height:8px;background:var(--g400);border-radius:50%;animation:pulse 2s infinite;}
  @keyframes pulse{0%,100%{transform:scale(1);opacity:1;}50%{transform:scale(1.4);opacity:0.7;}}
  .hero h1{font-size:clamp(2.2rem,5vw,3.5rem);font-weight:800;line-height:1.15;color:var(--g700);margin-bottom:20px;}
  .hero h1 em{font-style:normal;color:var(--o400);}
  .hero p{font-size:1.1rem;color:var(--muted);line-height:1.7;margin-bottom:32px;font-weight:300;}
  .hero-btns{display:flex;gap:16px;flex-wrap:wrap;}
  .btn{padding:14px 28px;border-radius:12px;font-family:'DM Sans',sans-serif;font-weight:500;font-size:0.95rem;cursor:pointer;border:none;text-decoration:none;display:inline-flex;align-items:center;gap:8px;transition:var(--transition);}
  .btn-green{background:var(--g500);color:white;}
  .btn-green:hover{background:var(--g600);transform:translateY(-2px);box-shadow:0 8px 24px rgba(56,142,60,0.35);}
  .btn-outline{background:white;color:var(--g600);border:2px solid var(--g400);}
  .btn-outline:hover{background:var(--g50);transform:translateY(-2px);}
  .btn-orange{background:var(--o400);color:white;}
  .btn-orange:hover{background:var(--o500);transform:translateY(-2px);box-shadow:0 8px 24px rgba(255,140,0,0.3);}
  .hero-visual{position:relative;}
  .hero-card{background:white;border-radius:20px;padding:28px;box-shadow:var(--shadow-lg);border:1px solid var(--border);}
  .hero-stats{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-top:20px;}
  .stat-item{background:var(--g50);border-radius:12px;padding:16px;text-align:center;}
  .stat-num{font-family:'Syne',sans-serif;font-size:1.8rem;font-weight:800;color:var(--g600);}
  .stat-label{font-size:0.8rem;color:var(--muted);margin-top:4px;}
  .crop-preview{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin-bottom:20px;}
  .crop-chip{background:var(--g50);border:1px solid var(--g200);border-radius:10px;padding:10px 8px;text-align:center;font-size:0.75rem;font-weight:500;color:var(--g700);}
  .crop-chip .icon{font-size:1.4rem;display:block;margin-bottom:4px;}

  /* ── SECTIONS ── */
  section{padding:80px 5%;}
  .section-tag{display:inline-block;background:var(--g50);color:var(--g600);border:1px solid var(--g200);border-radius:100px;padding:5px 16px;font-size:0.78rem;font-weight:600;letter-spacing:0.05em;text-transform:uppercase;margin-bottom:16px;}
  .section-title{font-size:clamp(1.8rem,4vw,2.8rem);font-weight:800;color:var(--g700);margin-bottom:16px;line-height:1.2;}
  .section-sub{font-size:1.05rem;color:var(--muted);max-width:560px;line-height:1.7;font-weight:300;}
  .text-center{text-align:center;}
  .text-center .section-sub{margin:0 auto;}
  .max-w{max-width:1100px;margin:0 auto;}

  /* ── HOW IT WORKS ── */
  .steps-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:24px;margin-top:48px;}
  .step-card{background:white;border-radius:var(--radius);padding:32px 24px;border:1px solid var(--border);position:relative;transition:var(--transition);}
  .step-card:hover{transform:translateY(-6px);box-shadow:var(--shadow-lg);}
  .step-num{position:absolute;top:-18px;left:24px;width:36px;height:36px;background:var(--g500);color:white;border-radius:50%;display:flex;align-items:center;justify-content:center;font-family:'Syne',sans-serif;font-weight:800;font-size:0.9rem;box-shadow:0 4px 12px rgba(56,142,60,0.35);}
  .step-icon{font-size:2.4rem;margin-bottom:16px;display:block;}
  .step-card h3{font-size:1.05rem;font-weight:700;margin-bottom:10px;color:var(--g700);}
  .step-card p{font-size:0.88rem;color:var(--muted);line-height:1.65;}

  /* ── BENEFITS ── */
  .benefits-grid{display:grid;grid-template-columns:1fr 1fr;gap:40px;margin-top:48px;align-items:start;}
  .benefit-group{background:white;border-radius:var(--radius);padding:36px;border:1px solid var(--border);}
  .benefit-group h3{font-size:1.3rem;font-weight:800;color:var(--g700);margin-bottom:24px;display:flex;align-items:center;gap:12px;}
  .benefit-item{display:flex;gap:16px;margin-bottom:20px;align-items:flex-start;}
  .benefit-item:last-child{margin-bottom:0;}
  .benefit-icon{width:44px;height:44px;border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:1.2rem;flex-shrink:0;}
  .bi-green{background:var(--g50);}
  .bi-orange{background:var(--o100);}
  .benefit-item h4{font-size:0.95rem;font-weight:600;margin-bottom:4px;color:var(--text);}
  .benefit-item p{font-size:0.85rem;color:var(--muted);line-height:1.6;}

  /* ── CROPS ── */
  .crops-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(140px,1fr));gap:16px;margin-top:48px;}
  .crop-card{background:white;border:1px solid var(--border);border-radius:14px;padding:20px 16px;text-align:center;transition:var(--transition);cursor:pointer;}
  .crop-card:hover{border-color:var(--g400);transform:translateY(-4px);box-shadow:var(--shadow);}
  .crop-card .crop-emoji{font-size:2.5rem;display:block;margin-bottom:10px;}
  .crop-card h4{font-size:0.88rem;font-weight:600;color:var(--g700);}
  .crop-card p{font-size:0.78rem;color:var(--muted);margin-top:4px;}

  /* ── CARDS (listings) ── */
  .cards-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(300px,1fr));gap:24px;margin-top:32px;}
  .listing-card{background:white;border-radius:var(--radius);border:1px solid var(--border);overflow:hidden;transition:var(--transition);}
  .listing-card:hover{transform:translateY(-6px);box-shadow:var(--shadow-lg);}
  .card-img{height:180px;background:linear-gradient(135deg,var(--g100),var(--g200));display:flex;align-items:center;justify-content:center;font-size:4rem;position:relative;}
  .card-badge{position:absolute;top:12px;right:12px;padding:4px 12px;border-radius:100px;font-size:0.75rem;font-weight:600;}
  .badge-available{background:#e8f5e9;color:#2e7d32;}
  .badge-sold{background:#ffebee;color:#c62828;}
  .badge-new{background:var(--o100);color:var(--o500);}
  .card-body{padding:20px;}
  .card-body h3{font-size:1.1rem;font-weight:700;color:var(--g700);margin-bottom:8px;}
  .card-meta{display:flex;flex-wrap:wrap;gap:8px;margin-bottom:16px;}
  .meta-tag{background:var(--g50);color:var(--g600);border-radius:6px;padding:4px 10px;font-size:0.78rem;font-weight:500;display:flex;align-items:center;gap:4px;}
  .card-price{font-family:'Syne',sans-serif;font-size:1.4rem;font-weight:800;color:var(--g600);}
  .card-price span{font-size:0.8rem;font-weight:400;color:var(--muted);}
  .card-actions{display:flex;gap:10px;margin-top:16px;}
  .btn-sm{padding:10px 18px;border-radius:9px;font-size:0.85rem;border:none;cursor:pointer;font-family:'DM Sans',sans-serif;font-weight:500;transition:var(--transition);}
  .btn-sm-green{background:var(--g500);color:white;flex:1;}
  .btn-sm-green:hover{background:var(--g600);}
  .btn-sm-outline{background:white;color:var(--g600);border:1.5px solid var(--g400);flex:1;}
  .btn-sm-outline:hover{background:var(--g50);}

  /* ── DASHBOARD ── */
  .dashboard-layout{max-width:1100px;margin:0 auto;padding:100px 5% 60px;}
  .dashboard-header{display:flex;justify-content:space-between;align-items:center;margin-bottom:32px;flex-wrap:wrap;gap:16px;}
  .dashboard-header h1{font-size:1.8rem;font-weight:800;color:var(--g700);}
  .stats-row{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:16px;margin-bottom:40px;}
  .stat-card{background:white;border:1px solid var(--border);border-radius:14px;padding:20px 24px;}
  .stat-card .num{font-family:'Syne',sans-serif;font-size:2rem;font-weight:800;color:var(--g600);}
  .stat-card .label{font-size:0.85rem;color:var(--muted);margin-top:4px;}
  .stat-card .trend{font-size:0.8rem;color:var(--g500);margin-top:6px;}

  /* ── FILTERS ── */
  .filter-bar{display:flex;gap:12px;flex-wrap:wrap;margin-bottom:28px;align-items:center;}
  .filter-bar input,.filter-bar select{padding:10px 16px;border:1.5px solid var(--border);border-radius:10px;font-family:'DM Sans',sans-serif;font-size:0.9rem;background:white;color:var(--text);outline:none;transition:var(--transition);}
  .filter-bar input:focus,.filter-bar select:focus{border-color:var(--g400);}
  .filter-bar input{flex:1;min-width:200px;}
  .search-wrap{position:relative;flex:1;min-width:200px;}
  .search-wrap input{width:100%;padding-left:44px;}
  .search-icon{position:absolute;left:14px;top:50%;transform:translateY(-50%);color:var(--muted);font-size:1rem;}

  /* ── UPLOAD FORM ── */
  .upload-layout{max-width:700px;margin:0 auto;padding:100px 5% 60px;}
  .form-card{background:white;border-radius:20px;border:1px solid var(--border);padding:40px;box-shadow:var(--shadow);}
  .form-card h2{font-size:1.6rem;font-weight:800;color:var(--g700);margin-bottom:8px;}
  .form-card p{color:var(--muted);font-size:0.92rem;margin-bottom:32px;}
  .form-group{margin-bottom:22px;}
  .form-group label{display:block;font-size:0.88rem;font-weight:500;color:var(--text);margin-bottom:8px;}
  .form-group input,.form-group select,.form-group textarea{width:100%;padding:12px 16px;border:1.5px solid var(--border);border-radius:10px;font-family:'DM Sans',sans-serif;font-size:0.95rem;color:var(--text);background:white;outline:none;transition:var(--transition);}
  .form-group input:focus,.form-group select:focus,.form-group textarea:focus{border-color:var(--g400);box-shadow:0 0 0 4px rgba(76,175,80,0.1);}
  .form-group textarea{resize:vertical;min-height:100px;}
  .form-grid{display:grid;grid-template-columns:1fr 1fr;gap:20px;}
  .upload-area{border:2px dashed var(--g400);border-radius:14px;padding:40px 20px;text-align:center;cursor:pointer;transition:var(--transition);background:var(--g50);}
  .upload-area:hover{border-color:var(--g600);background:var(--g100);}
  .upload-area .upload-icon{font-size:2.5rem;display:block;margin-bottom:12px;}
  .upload-area p{font-size:0.88rem;color:var(--muted);}
  .upload-area strong{color:var(--g600);}
  #preview-imgs{display:flex;flex-wrap:wrap;gap:10px;margin-top:16px;}
  #preview-imgs img{width:80px;height:80px;object-fit:cover;border-radius:10px;border:2px solid var(--border);}

  /* ── AUTH ── */
  .auth-layout{min-height:100vh;display:grid;grid-template-columns:1fr 1fr;overflow:hidden;}
  .auth-left{background:linear-gradient(150deg,var(--g700),var(--g500));display:flex;flex-direction:column;justify-content:center;padding:60px;color:white;}
  .auth-left h2{font-size:2.4rem;font-weight:800;margin-bottom:16px;line-height:1.2;}
  .auth-left p{font-size:1rem;opacity:0.85;line-height:1.7;margin-bottom:40px;font-weight:300;}
  .auth-features{display:flex;flex-direction:column;gap:16px;}
  .auth-feat{display:flex;gap:14px;align-items:flex-start;}
  .auth-feat .af-icon{width:40px;height:40px;background:rgba(255,255,255,0.2);border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:1.2rem;flex-shrink:0;}
  .auth-feat h4{font-size:0.95rem;font-weight:600;margin-bottom:3px;}
  .auth-feat p{font-size:0.82rem;opacity:0.8;}
  .auth-right{display:flex;align-items:center;justify-content:center;padding:60px 40px;background:var(--bg);}
  .auth-box{width:100%;max-width:440px;}
  .auth-box h1{font-size:1.9rem;font-weight:800;color:var(--g700);margin-bottom:8px;}
  .auth-box .sub{color:var(--muted);font-size:0.92rem;margin-bottom:32px;}
  .role-tabs{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:28px;}
  .role-tab{padding:14px;border:2px solid var(--border);border-radius:12px;text-align:center;cursor:pointer;transition:var(--transition);}
  .role-tab.active{border-color:var(--g500);background:var(--g50);}
  .role-tab .rt-icon{font-size:1.6rem;display:block;margin-bottom:6px;}
  .role-tab h4{font-size:0.9rem;font-weight:600;color:var(--g700);}
  .role-tab p{font-size:0.75rem;color:var(--muted);}
  .auth-switch{text-align:center;margin-top:20px;font-size:0.88rem;color:var(--muted);}
  .auth-switch a{color:var(--g600);font-weight:600;cursor:pointer;text-decoration:none;}

  /* ── CHAT ── */
  .chat-layout{max-width:900px;margin:0 auto;padding:100px 5% 40px;}
  .chat-container{background:white;border-radius:20px;border:1px solid var(--border);overflow:hidden;box-shadow:var(--shadow);display:grid;grid-template-columns:260px 1fr;}
  .chat-sidebar{border-right:1px solid var(--border);background:var(--g50);}
  .chat-sidebar-header{padding:20px;border-bottom:1px solid var(--border);}
  .chat-sidebar-header h3{font-size:1rem;font-weight:700;color:var(--g700);}
  .chat-list{overflow-y:auto;max-height:500px;}
  .chat-item{padding:14px 20px;cursor:pointer;transition:var(--transition);border-bottom:1px solid var(--border);}
  .chat-item:hover,.chat-item.active{background:white;}
  .chat-item-top{display:flex;justify-content:space-between;align-items:center;margin-bottom:4px;}
  .chat-item-name{font-size:0.9rem;font-weight:600;color:var(--text);}
  .chat-item-time{font-size:0.72rem;color:var(--muted);}
  .chat-item-msg{font-size:0.8rem;color:var(--muted);white-space:nowrap;overflow:hidden;text-overflow:ellipsis;}
  .chat-item .unread{width:18px;height:18px;background:var(--g500);color:white;border-radius:50%;font-size:0.65rem;display:inline-flex;align-items:center;justify-content:center;font-weight:700;float:right;margin-top:-18px;}
  .chat-main{display:flex;flex-direction:column;}
  .chat-header{padding:16px 24px;border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between;}
  .chat-header-left{display:flex;align-items:center;gap:14px;}
  .chat-avatar{width:42px;height:42px;background:var(--g200);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1.2rem;}
  .chat-user-name{font-size:1rem;font-weight:700;color:var(--text);}
  .chat-user-status{font-size:0.78rem;color:var(--g500);display:flex;align-items:center;gap:4px;}
  .chat-user-status::before{content:'';width:7px;height:7px;background:var(--g500);border-radius:50%;display:inline-block;}
  .chat-messages{flex:1;overflow-y:auto;padding:20px 24px;display:flex;flex-direction:column;gap:12px;max-height:380px;min-height:300px;}
  .msg-bubble{max-width:75%;padding:10px 16px;border-radius:16px;font-size:0.9rem;line-height:1.55;}
  .msg-received{background:var(--g50);color:var(--text);border-bottom-left-radius:4px;align-self:flex-start;}
  .msg-sent{background:var(--g500);color:white;border-bottom-right-radius:4px;align-self:flex-end;}
  .msg-time{font-size:0.7rem;margin-top:4px;opacity:0.65;}
  .msg-wrap{display:flex;flex-direction:column;}
  .msg-wrap.sent{align-items:flex-end;}
  .chat-input-bar{padding:16px 24px;border-top:1px solid var(--border);display:flex;gap:10px;align-items:center;}
  .chat-input-bar input{flex:1;padding:11px 18px;border:1.5px solid var(--border);border-radius:12px;font-family:'DM Sans',sans-serif;font-size:0.9rem;outline:none;transition:var(--transition);}
  .chat-input-bar input:focus{border-color:var(--g400);}
  .chat-send{width:44px;height:44px;background:var(--g500);color:white;border:none;border-radius:12px;cursor:pointer;font-size:1.1rem;transition:var(--transition);display:flex;align-items:center;justify-content:center;}
  .chat-send:hover{background:var(--g600);}

  /* ── NOTIFICATION ── */
  .notif{position:fixed;top:80px;right:20px;background:white;border:1px solid var(--border);border-radius:14px;padding:16px 20px;box-shadow:var(--shadow-lg);z-index:9999;display:none;min-width:280px;animation:slideIn 0.3s ease;}
  .notif.show{display:flex;align-items:center;gap:14px;}
  @keyframes slideIn{from{opacity:0;transform:translateX(20px);}to{opacity:1;transform:translateX(0);}}
  .notif-icon{width:40px;height:40px;background:var(--g50);border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:1.2rem;flex-shrink:0;}
  .notif h4{font-size:0.9rem;font-weight:600;margin-bottom:2px;}
  .notif p{font-size:0.8rem;color:var(--muted);}

  /* ── TABS ── */
  .tabs{display:flex;gap:8px;margin-bottom:32px;border-bottom:2px solid var(--border);padding-bottom:0;}
  .tab-btn{padding:12px 24px;border:none;background:none;cursor:pointer;font-family:'DM Sans',sans-serif;font-size:0.92rem;font-weight:500;color:var(--muted);border-bottom:2px solid transparent;margin-bottom:-2px;transition:var(--transition);}
  .tab-btn.active{color:var(--g600);border-bottom-color:var(--g500);}
  .tab-content{display:none;}
  .tab-content.active{display:block;}

  /* ── FOOTER ── */
  footer{background:var(--g800);color:white;padding:60px 5% 30px;}
  .footer-grid{display:grid;grid-template-columns:2fr 1fr 1fr 1fr;gap:40px;margin-bottom:48px;max-width:1100px;margin-left:auto;margin-right:auto;}
  .footer-brand h3{font-size:1.4rem;font-weight:800;color:white;margin-bottom:12px;}
  .footer-brand p{font-size:0.88rem;color:rgba(255,255,255,0.6);line-height:1.7;}
  .footer-col h4{font-size:0.88rem;font-weight:600;color:rgba(255,255,255,0.5);text-transform:uppercase;letter-spacing:0.08em;margin-bottom:16px;}
  .footer-col a{display:block;font-size:0.88rem;color:rgba(255,255,255,0.75);text-decoration:none;margin-bottom:10px;transition:var(--transition);}
  .footer-col a:hover{color:white;}
  .footer-bottom{border-top:1px solid rgba(255,255,255,0.1);padding-top:24px;display:flex;justify-content:space-between;align-items:center;max-width:1100px;margin:0 auto;flex-wrap:wrap;gap:12px;}
  .footer-bottom p{font-size:0.82rem;color:rgba(255,255,255,0.5);}

  /* ── TOAST ── */
  .toast{position:fixed;bottom:30px;left:50%;transform:translateX(-50%) translateY(100px);background:var(--g700);color:white;padding:14px 28px;border-radius:100px;font-size:0.9rem;font-weight:500;z-index:9999;transition:transform 0.4s cubic-bezier(0.34,1.56,0.64,1);box-shadow:0 8px 32px rgba(0,0,0,0.2);}
  .toast.show{transform:translateX(-50%) translateY(0);}

  /* ── CONFIRM MODAL ── */
  .modal-overlay{position:fixed;inset:0;background:rgba(0,0,0,0.5);z-index:9998;display:none;align-items:center;justify-content:center;backdrop-filter:blur(4px);}
  .modal-overlay.show{display:flex;}
  .modal{background:white;border-radius:20px;padding:40px;max-width:440px;width:90%;text-align:center;}
  .modal .m-icon{font-size:3rem;margin-bottom:16px;display:block;}
  .modal h3{font-size:1.3rem;font-weight:800;color:var(--g700);margin-bottom:10px;}
  .modal p{color:var(--muted);font-size:0.92rem;line-height:1.65;margin-bottom:28px;}
  .modal-actions{display:flex;gap:12px;justify-content:center;}
  .farmer-info{background:var(--g50);border-radius:14px;padding:20px;margin:20px 0;text-align:left;}
  .farmer-info .fi-row{display:flex;gap:10px;margin-bottom:10px;font-size:0.9rem;}
  .farmer-info .fi-row:last-child{margin-bottom:0;}
  .farmer-info .fi-label{color:var(--muted);min-width:90px;}
  .farmer-info .fi-val{font-weight:600;color:var(--text);}

  /* ── BACK BUTTON ── */
  .back-btn{display:inline-flex;align-items:center;gap:8px;background:white;border:1.5px solid var(--border);color:var(--g600);font-family:'DM Sans',sans-serif;font-size:0.88rem;font-weight:500;padding:9px 18px;border-radius:10px;cursor:pointer;transition:var(--transition);margin-bottom:8px;}
  .back-btn:hover{background:var(--g50);border-color:var(--g400);transform:translateX(-3px);}
  .back-btn svg{width:16px;height:16px;stroke:var(--g600);fill:none;stroke-width:2.5;stroke-linecap:round;stroke-linejoin:round;}

  /* ── SCROLL ANIMATION ── */
  .reveal{opacity:0;transform:translateY(30px);transition:opacity 0.6s ease,transform 0.6s ease;}
  .reveal.visible{opacity:1;transform:translateY(0);}

  /* ── RESPONSIVE ── */
  @media(max-width:900px){
    .hero-inner{grid-template-columns:1fr;gap:40px;}
    .hero-visual{display:none;}
    .benefits-grid{grid-template-columns:1fr;}
    .auth-layout{grid-template-columns:1fr;}
    .auth-left{display:none;}
    .chat-container{grid-template-columns:1fr;}
    .chat-sidebar{display:none;}
    .footer-grid{grid-template-columns:1fr 1fr;}
  }
  @media(max-width:600px){
    nav .nav-links{display:none;}
    .hamburger{display:flex;}
    .hero{padding:88px 5% 60px;}
    .form-grid{grid-template-columns:1fr;}
    .footer-grid{grid-template-columns:1fr;}
    .dashboard-header{flex-direction:column;align-items:flex-start;}
    .filter-bar{flex-direction:column;}
    .filter-bar select{width:100%;}
  }
</style>
</head>
<body>

<!-- NOTIFICATION TOAST -->
<div class="toast" id="toast"></div>

<!-- NOTIFICATION POPUP -->
<div class="notif" id="notif">
  <div class="notif-icon">💬</div>
  <div>
    <h4>New Message!</h4>
    <p id="notif-text">Dealer interested in your Wheat</p>
  </div>
</div>

<!-- CONFIRM MODAL -->
<div class="modal-overlay" id="modal">
  <div class="modal">
    <span class="m-icon">🎉</span>
    <h3>Confirm Purchase</h3>
    <p>You are about to confirm this crop purchase. The farmer's details will be shared with you.</p>
    <div class="farmer-info">
      <div class="fi-row"><span class="fi-label">Farmer:</span><span class="fi-val">Ramesh Kumar</span></div>
      <div class="fi-row"><span class="fi-label">Phone:</span><span class="fi-val">+91 9876543210</span></div>
      <div class="fi-row"><span class="fi-label">District:</span><span class="fi-val">Nashik, Maharashtra</span></div>
      <div class="fi-row"><span class="fi-label">Location:</span><span class="fi-val">Village Pimpalgaon</span></div>
    </div>
    <div class="modal-actions">
      <button class="btn btn-outline" onclick="closeModal()">Cancel</button>
      <button class="btn btn-green" onclick="confirmPurchase()">✓ Confirm & Get Contact</button>
    </div>
  </div>
</div>

<!-- ===================== NAVBAR ===================== -->
<nav>
  <a class="nav-logo" href="#" onclick="navigate('home')">
    <div class="nav-logo-icon">🌾</div>
    <span>Digital Mandi</span>
  </a>
  <div class="nav-links" id="nav-links">
    <button onclick="navigate('home')">Home</button>
    <button onclick="navigate('listings')">Browse Crops</button>
    <button onclick="navigate('chat')">💬 Chat</button>
    <button class="lang-btn" onclick="toggleLang()" id="lang-toggle">🌐 हिंदी</button>
    <button class="btn-primary" onclick="navigate('login')">Login / Signup</button>
  </div>
  <div class="hamburger" onclick="toggleMobile()">
    <span></span><span></span><span></span>
  </div>
</nav>
<div class="mobile-menu" id="mobile-menu">
  <button onclick="navigate('home');toggleMobile()">Home</button>
  <button onclick="navigate('listings');toggleMobile()">Browse Crops</button>
  <button onclick="navigate('farmer-dash');toggleMobile()">Farmer Dashboard</button>
  <button onclick="navigate('dealer-dash');toggleMobile()">Dealer Dashboard</button>
  <button onclick="navigate('chat');toggleMobile()">Chat</button>
  <button onclick="toggleLang()">🌐 हिंदी / English</button>
  <button onclick="navigate('login');toggleMobile()" style="background:var(--g500);color:white;border-radius:10px;">Login / Signup</button>
</div>

<!-- ===================== HOME PAGE ===================== -->
<div class="page active" id="page-home">
  <!-- HERO -->
  <section class="hero">
    <div class="hero-inner">
      <div class="hero-content">
        <div class="hero-badge"><span></span><span id="badge-text">Live Marketplace • 500+ Farmers</span></div>
        <h1 id="hero-title">Digital Mandi –<br><em>Direct Farmer</em> to<br>Dealer Marketplace</h1>
        <p id="hero-sub">Sell crops directly without middlemen. Connect farmers and dealers across districts for fair, transparent bulk crop trading.</p>
        <div class="hero-btns">
          <button class="btn btn-green" onclick="navigate('login')">🌾 <span id="btn-farmer">Farmer Login</span></button>
          <button class="btn btn-orange" onclick="navigate('login')">🏪 <span id="btn-dealer">Dealer Login</span></button>
          <button class="btn btn-outline" onclick="navigate('listings')">Browse Crops →</button>
        </div>
      </div>
      <div class="hero-visual">
        <div class="hero-card">
          <div class="crop-preview">
            <div class="crop-chip"><span class="icon">🌾</span>Wheat</div>
            <div class="crop-chip"><span class="icon">🍚</span>Rice</div>
            <div class="crop-chip"><span class="icon">🌽</span>Corn</div>
            <div class="crop-chip"><span class="icon">🧅</span>Onion</div>
            <div class="crop-chip"><span class="icon">🥔</span>Potato</div>
            <div class="crop-chip"><span class="icon">🍅</span>Tomato</div>
          </div>
          <div class="hero-stats">
            <div class="stat-item"><div class="stat-num">2.4K+</div><div class="stat-label">Active Farmers</div></div>
            <div class="stat-item"><div class="stat-num">850+</div><div class="stat-label">Dealers</div></div>
            <div class="stat-item"><div class="stat-num">18</div><div class="stat-label">Districts</div></div>
            <div class="stat-item"><div class="stat-num">₹0</div><div class="stat-label">Commission</div></div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- HOW IT WORKS -->
  <section style="background:white;">
    <div class="max-w">
      <div class="text-center reveal">
        <div class="section-tag">How It Works</div>
        <h2 class="section-title" id="how-title">Simple. Direct. Fair.</h2>
        <p class="section-sub" id="how-sub">Four easy steps to connect farmers directly with buyers — no middlemen, no hidden fees.</p>
      </div>
      <div class="steps-grid">
        <div class="step-card reveal"><div class="step-num">1</div><span class="step-icon">📸</span><h3>Upload Your Crop</h3><p>Farmers upload crop details, photos, quantity, price and district information.</p></div>
        <div class="step-card reveal"><div class="step-num">2</div><span class="step-icon">🔍</span><h3>Dealers Browse</h3><p>Dealers search and filter crops by district, type, price and quantity.</p></div>
        <div class="step-card reveal"><div class="step-num">3</div><span class="step-icon">💬</span><h3>Direct Chat</h3><p>Dealer messages farmer directly through our secure chat system in Hindi or English.</p></div>
        <div class="step-card reveal"><div class="step-num">4</div><span class="step-icon">🤝</span><h3>Confirm & Deal</h3><p>Dealer confirms purchase, crop is marked SOLD, farmer contact shared instantly.</p></div>
      </div>
    </div>
  </section>

  <!-- BENEFITS -->
  <section>
    <div class="max-w">
      <div class="text-center reveal">
        <div class="section-tag">Benefits</div>
        <h2 class="section-title">Why Choose Digital Mandi?</h2>
      </div>
      <div class="benefits-grid reveal">
        <div class="benefit-group">
          <h3>🌾 For Farmers</h3>
          <div class="benefit-item"><div class="benefit-icon bi-green">💰</div><div><h4>Better Prices</h4><p>Set your own price. No agent cuts or hidden deductions.</p></div></div>
          <div class="benefit-item"><div class="benefit-icon bi-green">📱</div><div><h4>Easy Upload</h4><p>Upload crop details and photos from your phone in minutes.</p></div></div>
          <div class="benefit-item"><div class="benefit-icon bi-green">🗺️</div><div><h4>District Reach</h4><p>Your crops visible to all dealers in your district automatically.</p></div></div>
          <div class="benefit-item"><div class="benefit-icon bi-green">🔒</div><div><h4>Secure Contact</h4><p>Your phone number shared only after deal confirmation.</p></div></div>
        </div>
        <div class="benefit-group">
          <h3>🏪 For Dealers</h3>
          <div class="benefit-item"><div class="benefit-icon bi-orange">🔍</div><div><h4>Smart Filters</h4><p>Filter by crop type, price range, quantity and district.</p></div></div>
          <div class="benefit-item"><div class="benefit-icon bi-orange">📦</div><div><h4>Bulk Buying</h4><p>Access hundreds of farmers offering minimum 100kg lots.</p></div></div>
          <div class="benefit-item"><div class="benefit-icon bi-orange">💬</div><div><h4>Direct Chat</h4><p>Negotiate prices directly with farmers. No broker involvement.</p></div></div>
          <div class="benefit-item"><div class="benefit-icon bi-orange">⚡</div><div><h4>Fast Sourcing</h4><p>Find and confirm quality crops in your district within minutes.</p></div></div>
        </div>
      </div>
    </div>
  </section>

  <!-- SUPPORTED CROPS -->
  <section style="background:white;">
    <div class="max-w">
      <div class="text-center reveal">
        <div class="section-tag">Supported Crops</div>
        <h2 class="section-title">Trade Any Crop</h2>
        <p class="section-sub">From grains to vegetables — list any agricultural produce on Digital Mandi.</p>
      </div>
      <div class="crops-grid">
        <div class="crop-card reveal" onclick="navigate('listings')"><span class="crop-emoji">🌾</span><h4>Wheat</h4><p>₹22–28/kg</p></div>
        <div class="crop-card reveal" onclick="navigate('listings')"><span class="crop-emoji">🍚</span><h4>Rice</h4><p>₹30–45/kg</p></div>
        <div class="crop-card reveal" onclick="navigate('listings')"><span class="crop-emoji">🌽</span><h4>Maize</h4><p>₹18–24/kg</p></div>
        <div class="crop-card reveal" onclick="navigate('listings')"><span class="crop-emoji">🧅</span><h4>Onion</h4><p>₹15–30/kg</p></div>
        <div class="crop-card reveal" onclick="navigate('listings')"><span class="crop-emoji">🥔</span><h4>Potato</h4><p>₹12–20/kg</p></div>
        <div class="crop-card reveal" onclick="navigate('listings')"><span class="crop-emoji">🍅</span><h4>Tomato</h4><p>₹20–40/kg</p></div>
        <div class="crop-card reveal" onclick="navigate('listings')"><span class="crop-emoji">🌶️</span><h4>Chilli</h4><p>₹80–150/kg</p></div>
        <div class="crop-card reveal" onclick="navigate('listings')"><span class="crop-emoji">🧄</span><h4>Garlic</h4><p>₹60–120/kg</p></div>
        <div class="crop-card reveal" onclick="navigate('listings')"><span class="crop-emoji">🫘</span><h4>Soybean</h4><p>₹40–55/kg</p></div>
        <div class="crop-card reveal" onclick="navigate('listings')"><span class="crop-emoji">🌻</span><h4>Sunflower</h4><p>₹50–65/kg</p></div>
        <div class="crop-card reveal" onclick="navigate('listings')"><span class="crop-emoji">🍬</span><h4>Sugarcane</h4><p>₹3–5/kg</p></div>
        <div class="crop-card reveal" onclick="navigate('listings')"><span class="crop-emoji">🥜</span><h4>Groundnut</h4><p>₹55–75/kg</p></div>
      </div>
    </div>
  </section>

  <!-- CTA -->
  <section style="background:linear-gradient(135deg,var(--g700),var(--g500));">
    <div class="max-w text-center reveal">
      <h2 style="font-size:2.2rem;font-weight:800;color:white;margin-bottom:16px;">Ready to Start Trading?</h2>
      <p style="color:rgba(255,255,255,0.8);font-size:1.05rem;margin-bottom:36px;max-width:480px;margin-left:auto;margin-right:auto;">Join thousands of farmers and dealers already using Digital Mandi for fair, direct crop trading.</p>
      <div style="display:flex;gap:16px;justify-content:center;flex-wrap:wrap;">
        <button class="btn" style="background:white;color:var(--g700);" onclick="navigate('upload')">🌾 Upload Your Crop</button>
        <button class="btn btn-outline" style="border-color:rgba(255,255,255,0.5);color:white;" onclick="navigate('listings')">Browse Crops →</button>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="footer-grid">
      <div class="footer-brand">
        <h3>🌾 Digital Mandi</h3>
        <p>Empowering Indian farmers with direct access to buyers. No middlemen, transparent pricing, fair trade.</p>
      </div>
      <div class="footer-col">
        <h4>Platform</h4>
        <a href="#" onclick="navigate('listings')">Browse Crops</a>
        <a href="#" onclick="navigate('upload')">Upload Crop</a>
        <a href="#" onclick="navigate('chat')">Chat</a>
      </div>
      <div class="footer-col">
        <h4>For Users</h4>
        <a href="#" onclick="navigate('farmer-dash')">Farmer Dashboard</a>
        <a href="#" onclick="navigate('dealer-dash')">Dealer Dashboard</a>
        <a href="#" onclick="navigate('login')">Sign Up</a>
      </div>
      <div class="footer-col">
        <h4>Support</h4>
        <a href="#">Help Center</a>
        <a href="#">Contact Us</a>
        <a href="#">Hindi Support</a>
      </div>
    </div>
    <div class="footer-bottom">
      <p>© 2024 Digital Mandi. Made for Indian Farmers 🇮🇳</p>
      <p>No commissions • No middlemen • Direct trade</p>
    </div>
  </footer>
</div>

<!-- ===================== FARMER DASHBOARD ===================== -->
<div class="page" id="page-farmer-dash">
  <div class="dashboard-layout">
    <button class="back-btn" onclick="navigate('home')"><svg viewBox="0 0 24 24"><polyline points="15 18 9 12 15 6"/></svg> Back to Home</button>
    <div class="dashboard-header">
      <div>
        <h1>🌾 Farmer Dashboard</h1>
        <p style="color:var(--muted);font-size:0.92rem;margin-top:4px;">Welcome back, Ramesh Kumar • Nashik District</p>
      </div>
      <button class="btn btn-green" onclick="navigate('upload')">+ Upload New Crop</button>
    </div>

    <div class="stats-row">
      <div class="stat-card"><div class="num">8</div><div class="label">Active Listings</div><div class="trend">↑ 2 this week</div></div>
      <div class="stat-card"><div class="num">3</div><div class="label">Sold Crops</div><div class="trend">₹1.2L earned</div></div>
      <div class="stat-card"><div class="num">12</div><div class="label">New Messages</div><div class="trend">↑ 5 today</div></div>
      <div class="stat-card"><div class="num">24</div><div class="label">Profile Views</div><div class="trend">This week</div></div>
    </div>

    <div class="tabs">
      <button class="tab-btn active" onclick="switchTab(this,'tab-my-crops')">My Crops</button>
      <button class="tab-btn" onclick="switchTab(this,'tab-messages')">Messages</button>
      <button class="tab-btn" onclick="switchTab(this,'tab-history')">Crop History</button>
    </div>

    <div class="tab-content active" id="tab-my-crops">
      <div class="cards-grid" id="farmer-crops-grid"></div>
    </div>
    <div class="tab-content" id="tab-messages">
      <div style="background:white;border-radius:16px;border:1px solid var(--border);padding:24px;">
        <h3 style="font-size:1rem;font-weight:700;margin-bottom:20px;color:var(--g700);">Recent Messages</h3>
        <div id="farmer-messages-list"></div>
      </div>
    </div>
    <div class="tab-content" id="tab-history">
      <div style="background:white;border-radius:16px;border:1px solid var(--border);padding:24px;">
        <h3 style="font-size:1rem;font-weight:700;margin-bottom:20px;color:var(--g700);">Crop History</h3>
        <div id="farmer-history-list"></div>
      </div>
    </div>
  </div>
</div>

<!-- ===================== DEALER DASHBOARD ===================== -->
<div class="page" id="page-dealer-dash">
  <div class="dashboard-layout">
    <button class="back-btn" onclick="navigate('home')"><svg viewBox="0 0 24 24"><polyline points="15 18 9 12 15 6"/></svg> Back to Home</button>
    <div class="dashboard-header">
      <div>
        <h1>🏪 Dealer Dashboard</h1>
        <p style="color:var(--muted);font-size:0.92rem;margin-top:4px;">Welcome back, Suresh Traders • Nashik District</p>
      </div>
      <button class="btn btn-orange" onclick="navigate('listings')">Browse All Crops</button>
    </div>

    <div class="stats-row">
      <div class="stat-card"><div class="num">45</div><div class="label">Crops Available</div><div class="trend">In your district</div></div>
      <div class="stat-card"><div class="num">6</div><div class="label">Purchases Made</div><div class="trend">₹4.8L spent</div></div>
      <div class="stat-card"><div class="num">8</div><div class="label">Active Chats</div><div class="trend">↑ 3 today</div></div>
      <div class="stat-card"><div class="num">18</div><div class="label">Farmers Contacted</div><div class="trend">This month</div></div>
    </div>

    <div class="tabs">
      <button class="tab-btn active" onclick="switchTab(this,'tab-browse')">Browse Crops</button>
      <button class="tab-btn" onclick="switchTab(this,'tab-my-purchases')">My Purchases</button>
      <button class="tab-btn" onclick="switchTab(this,'tab-saved')">Saved Crops</button>
    </div>

    <div class="tab-content active" id="tab-browse">
      <div class="filter-bar">
        <div class="search-wrap">
          <span class="search-icon">🔍</span>
          <input type="text" placeholder="Search crops..." id="dealer-search" oninput="filterCrops()">
        </div>
        <select id="f-crop" onchange="filterCrops()"><option value="">All Crops</option><option>Wheat</option><option>Rice</option><option>Onion</option><option>Tomato</option><option>Potato</option><option>Maize</option></select>
        <select id="f-district" onchange="filterCrops()"><option value="">All Districts</option><option>Nashik</option><option>Pune</option><option>Nagpur</option><option>Aurangabad</option><option>Solapur</option></select>
        <select id="f-price" onchange="filterCrops()"><option value="">Any Price</option><option value="low">Under ₹25/kg</option><option value="mid">₹25–50/kg</option><option value="high">Above ₹50/kg</option></select>
      </div>
      <div class="cards-grid" id="dealer-crops-grid"></div>
    </div>
    <div class="tab-content" id="tab-my-purchases">
      <div style="background:white;border-radius:16px;border:1px solid var(--border);padding:24px;">
        <h3 style="font-size:1rem;font-weight:700;margin-bottom:20px;color:var(--g700);">Purchase History</h3>
        <div id="purchase-history"></div>
      </div>
    </div>
    <div class="tab-content" id="tab-saved">
      <div class="cards-grid" id="saved-crops-grid"></div>
    </div>
  </div>
</div>

<!-- ===================== UPLOAD PAGE ===================== -->
<div class="page" id="page-upload">
  <div class="upload-layout">
    <button class="back-btn" onclick="history.length>1?navigate('farmer-dash'):navigate('home')"><svg viewBox="0 0 24 24"><polyline points="15 18 9 12 15 6"/></svg> Back</button>
    <div class="form-card">
      <h2>📸 Upload Your Crop</h2>
      <p>List your crop for dealers in your district. Fill all details accurately for better response.</p>

      <div class="form-group">
        <label>Crop Name *</label>
        <select id="crop-name">
          <option value="">Select crop type...</option>
          <option>Wheat</option><option>Rice</option><option>Maize</option><option>Onion</option>
          <option>Potato</option><option>Tomato</option><option>Chilli</option><option>Garlic</option>
          <option>Soybean</option><option>Sugarcane</option><option>Groundnut</option><option>Other</option>
        </select>
      </div>

      <div class="form-grid">
        <div class="form-group">
          <label>Quantity (kg) *</label>
          <input type="number" id="quantity" placeholder="Min. 100 kg" min="100">
        </div>
        <div class="form-group">
          <label>Expected Price (₹/kg) *</label>
          <input type="number" id="price" placeholder="e.g. 25">
        </div>
      </div>

      <div class="form-grid">
        <div class="form-group">
          <label>District *</label>
          <select id="district">
            <option value="">Select district...</option>
            <option>Nashik</option><option>Pune</option><option>Nagpur</option>
            <option>Aurangabad</option><option>Solapur</option><option>Kolhapur</option>
            <option>Ahmednagar</option><option>Jalgaon</option>
          </select>
        </div>
        <div class="form-group">
          <label>Phone Number *</label>
          <input type="tel" id="phone" placeholder="+91 XXXXX XXXXX">
        </div>
      </div>

      <div class="form-group">
        <label>Description</label>
        <textarea id="description" placeholder="Describe your crop quality, harvesting date, storage conditions, etc."></textarea>
      </div>

      <div class="form-group">
        <label>Crop Photos</label>
        <div class="upload-area" onclick="document.getElementById('img-input').click()">
          <span class="upload-icon">📷</span>
          <p><strong>Click to upload</strong> or drag & drop</p>
          <p style="margin-top:4px;font-size:0.78rem;">JPG, PNG up to 5MB each • Max 5 photos</p>
        </div>
        <input type="file" id="img-input" multiple accept="image/*" style="display:none" onchange="previewImages(event)">
        <div id="preview-imgs"></div>
      </div>

      <button class="btn btn-green" style="width:100%;justify-content:center;" onclick="submitCrop()">
        ✓ Submit Crop Listing
      </button>
    </div>
  </div>
</div>

<!-- ===================== LISTINGS PAGE ===================== -->
<div class="page" id="page-listings">
  <div class="dashboard-layout">
    <button class="back-btn" onclick="navigate('home')"><svg viewBox="0 0 24 24"><polyline points="15 18 9 12 15 6"/></svg> Back to Home</button>
    <div class="dashboard-header">
      <div>
        <h1>🌾 Browse Crops</h1>
        <p style="color:var(--muted);font-size:0.92rem;margin-top:4px;">Find quality crops directly from farmers in your district</p>
      </div>
      <button class="btn btn-green" onclick="navigate('upload')">+ List Your Crop</button>
    </div>

    <div class="filter-bar">
      <div class="search-wrap">
        <span class="search-icon">🔍</span>
        <input type="text" placeholder="Search crops, district..." id="list-search" oninput="filterListings()">
      </div>
      <select id="l-crop" onchange="filterListings()"><option value="">All Crops</option><option>Wheat</option><option>Rice</option><option>Onion</option><option>Tomato</option><option>Potato</option><option>Maize</option><option>Chilli</option></select>
      <select id="l-district" onchange="filterListings()"><option value="">All Districts</option><option>Nashik</option><option>Pune</option><option>Nagpur</option><option>Aurangabad</option></select>
      <select id="l-sort" onchange="filterListings()"><option value="">Sort By</option><option value="price-low">Price: Low to High</option><option value="price-high">Price: High to Low</option><option value="qty">Quantity</option></select>
    </div>

    <div class="cards-grid" id="listings-grid"></div>
  </div>
</div>

<!-- ===================== CHAT PAGE ===================== -->
<div class="page" id="page-chat">
  <div class="chat-layout">
    <button class="back-btn" onclick="navigate('home')"><svg viewBox="0 0 24 24"><polyline points="15 18 9 12 15 6"/></svg> Back to Home</button>
    <h1 style="font-size:1.8rem;font-weight:800;color:var(--g700);margin-bottom:24px;">💬 Messages</h1>
    <div class="chat-container" style="height:580px;">
      <div class="chat-sidebar">
        <div class="chat-sidebar-header">
          <h3>Conversations</h3>
        </div>
        <div class="chat-list" id="chat-list"></div>
      </div>
      <div class="chat-main">
        <div class="chat-header">
          <div class="chat-header-left">
            <div class="chat-avatar">👤</div>
            <div>
              <div class="chat-user-name" id="chat-with-name">Suresh Traders</div>
              <div class="chat-user-status">Online</div>
            </div>
          </div>
          <div style="display:flex;gap:8px;">
            <button class="btn-sm btn-sm-outline" onclick="showModal()">📦 Confirm Deal</button>
          </div>
        </div>
        <div class="chat-messages" id="chat-messages"></div>
        <div class="chat-input-bar">
          <select id="chat-lang" style="padding:8px 12px;border:1.5px solid var(--border);border-radius:10px;font-size:0.85rem;outline:none;">
            <option value="en">EN</option>
            <option value="hi">HI</option>
          </select>
          <input type="text" id="chat-input" placeholder="Type a message..." onkeydown="if(event.key==='Enter')sendMsg()">
          <button class="chat-send" onclick="sendMsg()">➤</button>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ===================== LOGIN/SIGNUP PAGE ===================== -->
<div class="page" id="page-login">
  <div class="auth-layout">
    <div class="auth-left">
      <h2>Join Digital Mandi Today</h2>
      <p>Connect directly with buyers and sellers. No middlemen, no hidden fees. Just fair, direct crop trading across districts.</p>
      <div class="auth-features">
        <div class="auth-feat"><div class="af-icon">🌾</div><div><h4>For Farmers</h4><p>Upload and sell your crops at your own price</p></div></div>
        <div class="auth-feat"><div class="af-icon">🏪</div><div><h4>For Dealers</h4><p>Source quality crops directly from farmers</p></div></div>
        <div class="auth-feat"><div class="af-icon">💬</div><div><h4>Direct Chat</h4><p>Hindi & English messaging support</p></div></div>
        <div class="auth-feat"><div class="af-icon">🔒</div><div><h4>Secure & Free</h4><p>Zero commission. Your data stays private.</p></div></div>
      </div>
    </div>
    <div class="auth-right">
      <div class="auth-box">
        <button class="back-btn" onclick="navigate('home')" style="margin-bottom:20px;"><svg viewBox="0 0 24 24"><polyline points="15 18 9 12 15 6"/></svg> Back to Home</button>
        <h1 id="auth-title">Welcome Back</h1>
        <p class="sub" id="auth-sub">Sign in to your Digital Mandi account</p>

        <div class="role-tabs">
          <div class="role-tab active" id="rt-farmer" onclick="selectRole('farmer')">
            <span class="rt-icon">🌾</span>
            <h4>Farmer</h4>
            <p>Upload & sell crops</p>
          </div>
          <div class="role-tab" id="rt-dealer" onclick="selectRole('dealer')">
            <span class="rt-icon">🏪</span>
            <h4>Dealer</h4>
            <p>Buy crops in bulk</p>
          </div>
        </div>

        <div id="auth-form">
          <div class="form-group"><label>Phone Number</label><input type="tel" placeholder="+91 XXXXX XXXXX" id="auth-phone"></div>
          <div class="form-group"><label>Password</label><input type="password" placeholder="Enter password" id="auth-pass"></div>
          <button class="btn btn-green" style="width:100%;justify-content:center;margin-top:8px;" onclick="doLogin()" id="auth-submit-btn">Login</button>
        </div>

        <div class="auth-switch">
          <span id="auth-switch-text">Don't have an account?</span>
          <a onclick="toggleAuthMode()" id="auth-toggle-link"> Sign up</a>
        </div>
        <div style="text-align:center;margin-top:12px;font-size:0.8rem;color:var(--muted);">
          Demo: Click Login to explore the platform
        </div>
      </div>
    </div>
  </div>
</div>

<script>
// ── STATE ──
let currentLang = 'en';
let currentRole = 'farmer';
let isLogin = true;
let chatMessages = {
  'suresh': [{s:'r',t:'Hello! I am interested in your wheat crop.',ts:'10:32 AM'},{s:'s',t:'Yes, still available. 500kg at ₹26/kg.',ts:'10:34 AM'},{s:'r',t:'Can you do ₹24/kg for bulk?',ts:'10:35 AM'},{s:'s',t:'Minimum ₹25/kg. Quality is A-grade.',ts:'10:37 AM'}],
  'mahesh': [{s:'r',t:'क्या यह टमाटर अभी उपलब्ध है?',ts:'9:15 AM'},{s:'s',t:'हाँ, 300 किलो उपलब्ध है।',ts:'9:18 AM'}],
  'rajesh': [{s:'r',t:'What is the moisture content of your rice?',ts:'Yesterday'},{s:'s',t:'Around 14%. Freshly harvested.',ts:'Yesterday'}],
};
let activeChatId = 'suresh';

const translations = {
  en: {
    badge:'Live Marketplace • 500+ Farmers',
    heroTitle:'Digital Mandi –\nDirect Farmer to\nDealer Marketplace',
    heroSub:'Sell crops directly without middlemen. Connect farmers and dealers across districts for fair, transparent bulk crop trading.',
    btnFarmer:'Farmer Login',btnDealer:'Dealer Login',howTitle:'Simple. Direct. Fair.',
    howSub:'Four easy steps to connect farmers directly with buyers — no middlemen, no hidden fees.',
    langToggle:'🌐 हिंदी',
  },
  hi: {
    badge:'लाइव बाज़ार • 500+ किसान',
    heroTitle:'डिजिटल मंडी –\nकिसान से सीधे\nव्यापारी तक',
    heroSub:'बिना दलालों के सीधे फसल बेचें। जिले भर में किसानों और व्यापारियों को जोड़ें।',
    btnFarmer:'किसान लॉगिन',btnDealer:'व्यापारी लॉगिन',howTitle:'सरल। सीधा। उचित।',
    howSub:'चार आसान कदमों में किसान सीधे खरीदारों से जुड़ें — कोई दलाल नहीं, कोई छिपा शुल्क नहीं।',
    langToggle:'🌐 English',
  }
};

// ── CROPS DATA ──
const cropsData = [
  {id:1,name:'Wheat',farmer:'Ramesh Kumar',district:'Nashik',qty:500,price:26,status:'available',icon:'🌾',phone:'9876543210',desc:'Grade A wheat, dry storage, fresh harvest.',img:'https://images.unsplash.com/photo-1574323347407-f5e1ad6d020b?w=400&h=200&fit=crop'},
  {id:2,name:'Onion',farmer:'Sudhir Patil',district:'Nashik',qty:800,price:18,status:'available',icon:'🧅',phone:'9823456789',desc:'Medium size, export quality.',img:'https://images.unsplash.com/photo-1587049352846-4a222e784d38?w=400&h=200&fit=crop'},
  {id:3,name:'Tomato',farmer:'Vijay More',district:'Pune',qty:300,price:32,status:'available',icon:'🍅',phone:'9765432109',desc:'Hybrid variety, firm and fresh.',img:'https://images.unsplash.com/photo-1592924357228-91a4daadcfea?w=400&h=200&fit=crop'},
  {id:4,name:'Rice',farmer:'Anil Yadav',district:'Nagpur',qty:1200,price:42,status:'available',icon:'🍚',phone:'9812345678',desc:'Basmati variety, premium quality.',img:'https://images.unsplash.com/photo-1586201375761-83865001e31c?w=400&h=200&fit=crop'},
  {id:5,name:'Potato',farmer:'Ganesh Shinde',district:'Pune',qty:600,price:15,status:'sold',icon:'🥔',phone:'9898765432',desc:'Good size, minimal damage.',img:'https://images.unsplash.com/photo-1518977676601-b53f82aba655?w=400&h=200&fit=crop'},
  {id:6,name:'Chilli',farmer:'Prakash Desai',district:'Aurangabad',qty:200,price:110,status:'available',icon:'🌶️',phone:'9756438291',desc:'Dried red chilli, spicy grade 1.',img:'https://images.unsplash.com/photo-1583119022894-919a68a3d0e3?w=400&h=200&fit=crop'},
  {id:7,name:'Maize',farmer:'Santosh Kale',district:'Nashik',qty:900,price:22,status:'available',icon:'🌽',phone:'9765412398',desc:'Yellow maize, 13% moisture.',img:'https://images.unsplash.com/photo-1601593346740-925612772716?w=400&h=200&fit=crop'},
  {id:8,name:'Soybean',farmer:'Mahesh Gawli',district:'Nagpur',qty:400,price:48,status:'available',icon:'🫘',phone:'9876012345',desc:'Non-GMO, food grade.',img:'https://images.unsplash.com/photo-1515543237350-b3eea1ec8082?w=400&h=200&fit=crop'},
];

const chatContacts = [
  {id:'suresh',name:'Suresh Traders',crop:'Wheat',time:'10:37 AM',unread:2},
  {id:'mahesh',name:'Mahesh & Sons',crop:'Tomato',time:'9:18 AM',unread:0},
  {id:'rajesh',name:'Rajesh Enterprises',crop:'Rice',time:'Yesterday',unread:1},
];

// ── NAVIGATION ──
function navigate(page) {
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.getElementById('page-'+page).classList.add('active');
  window.scrollTo(0,0);
  if(page==='listings'||page==='dealer-dash') renderListings();
  if(page==='farmer-dash') renderFarmerDash();
  if(page==='chat') initChat();
  if(page==='home') initReveal();
}

// ── LANGUAGE TOGGLE ──
function toggleLang() {
  currentLang = currentLang==='en'?'hi':'en';
  const t = translations[currentLang];
  document.getElementById('badge-text').textContent = t.badge;
  document.getElementById('hero-title').innerHTML = t.heroTitle.replace(/\n/g,'<br>').replace('Direct Farmer','<em>Direct Farmer</em>').replace('सीधे किसान','<em>सीधे किसान</em>');
  document.getElementById('hero-sub').textContent = t.heroSub;
  document.getElementById('btn-farmer').textContent = t.btnFarmer;
  document.getElementById('btn-dealer').textContent = t.btnDealer;
  document.getElementById('how-title').textContent = t.howTitle;
  document.getElementById('how-sub').textContent = t.howSub;
  document.getElementById('lang-toggle').textContent = t.langToggle;
}

function toggleMobile() {
  document.getElementById('mobile-menu').classList.toggle('open');
}

// ── AUTH ──
function selectRole(role) {
  currentRole = role;
  document.getElementById('rt-farmer').classList.toggle('active', role==='farmer');
  document.getElementById('rt-dealer').classList.toggle('active', role==='dealer');
}

function toggleAuthMode() {
  isLogin = !isLogin;
  if(!isLogin) {
    document.getElementById('auth-title').textContent = 'Create Account';
    document.getElementById('auth-sub').textContent = 'Join Digital Mandi for free';
    document.getElementById('auth-form').innerHTML = `
      <div class="form-group"><label>Full Name</label><input type="text" placeholder="Your name"></div>
      <div class="form-group"><label>Phone Number</label><input type="tel" placeholder="+91 XXXXX XXXXX"></div>
      <div class="form-group"><label>District</label><select><option>Select district...</option><option>Nashik</option><option>Pune</option><option>Nagpur</option><option>Aurangabad</option></select></div>
      <div class="form-group"><label>Password</label><input type="password" placeholder="Create password"></div>
      <button class="btn btn-green" style="width:100%;justify-content:center;margin-top:8px;" onclick="doLogin()">Create Account</button>`;
    document.getElementById('auth-switch-text').textContent = 'Already have an account?';
    document.getElementById('auth-toggle-link').textContent = ' Login';
  } else {
    document.getElementById('auth-title').textContent = 'Welcome Back';
    document.getElementById('auth-sub').textContent = 'Sign in to your Digital Mandi account';
    document.getElementById('auth-form').innerHTML = `
      <div class="form-group"><label>Phone Number</label><input type="tel" placeholder="+91 XXXXX XXXXX" id="auth-phone"></div>
      <div class="form-group"><label>Password</label><input type="password" placeholder="Enter password" id="auth-pass"></div>
      <button class="btn btn-green" style="width:100%;justify-content:center;margin-top:8px;" onclick="doLogin()">Login</button>`;
    document.getElementById('auth-switch-text').textContent = "Don't have an account?";
    document.getElementById('auth-toggle-link').textContent = ' Sign up';
  }
}

function doLogin() {
  showToast('Login successful! Welcome to Digital Mandi 🌾');
  setTimeout(()=>{
    if(currentRole==='farmer') navigate('farmer-dash');
    else navigate('dealer-dash');
  },800);
}

// ── RENDER CROP CARDS ──
function cropCardHTML(crop, showConfirm=false) {
  const statusBadge = crop.status==='sold'
    ?'<span class="card-badge badge-sold">SOLD</span>'
    :'<span class="card-badge badge-available">Available</span>';
  const actions = crop.status==='sold'
    ?`<button class="btn-sm btn-sm-outline" disabled style="opacity:0.5;cursor:not-allowed;">Sold Out</button>`
    :showConfirm
    ?`<button class="btn-sm btn-sm-green" onclick="showModal()">✓ Confirm Buy</button><button class="btn-sm btn-sm-outline" onclick="navigate('chat')">💬 Chat</button>`
    :`<button class="btn-sm btn-sm-green" onclick="showModal()">Contact Farmer</button><button class="btn-sm btn-sm-outline" onclick="navigate('chat')">💬 Chat</button>`;
  const imgSection = crop.img
    ? `<div class="card-img" style="padding:0;overflow:hidden;">
        <img src="${crop.img}" alt="${crop.name}" style="width:100%;height:100%;object-fit:cover;display:block;" onerror="this.parentElement.innerHTML='<span style=font-size:4rem>${crop.icon}</span>'">
        ${statusBadge}
      </div>`
    : `<div class="card-img">${crop.icon}${statusBadge}</div>`;
  return `<div class="listing-card">
    ${imgSection}
    <div class="card-body">
      <h3>${crop.icon} ${crop.name}</h3>
      <div class="card-meta">
        <span class="meta-tag">📍 ${crop.district}</span>
        <span class="meta-tag">⚖️ ${crop.qty} kg</span>
        <span class="meta-tag">👤 ${crop.farmer}</span>
      </div>
      <p style="font-size:0.82rem;color:var(--muted);margin-bottom:12px;line-height:1.55;">${crop.desc}</p>
      <div class="card-price">₹${crop.price}<span>/kg</span> <span style="font-size:0.82rem;color:var(--muted);"> • ₹${(crop.price*crop.qty).toLocaleString('en-IN')} total</span></div>
      <div class="card-actions">${actions}</div>
    </div>
  </div>`;
}

function renderListings(data) {
  const grid = document.getElementById('listings-grid');
  if(!grid) return;
  const crops = data||cropsData;
  grid.innerHTML = crops.map(c=>cropCardHTML(c,true)).join('');
}

function renderFarmerDash() {
  const grid = document.getElementById('farmer-crops-grid');
  if(grid) grid.innerHTML = cropsData.slice(0,4).map(c=>cropCardHTML(c,false)).join('');
  renderFarmerMessages();
  renderHistory();
}

function renderFarmerMessages() {
  const list = document.getElementById('farmer-messages-list');
  if(!list) return;
  const msgs = [
    {from:'Suresh Traders',msg:'Interested in your wheat, can we negotiate?',time:'10:37 AM',crop:'Wheat'},
    {from:'Mahesh & Sons',msg:'क्या यह टमाटर उपलब्ध है?',time:'9:18 AM',crop:'Tomato'},
    {from:'Rajesh Enterprises',msg:'What is delivery timeline?',time:'Yesterday',crop:'Rice'},
  ];
  list.innerHTML = msgs.map(m=>`
    <div style="display:flex;justify-content:space-between;align-items:center;padding:14px 0;border-bottom:1px solid var(--border);cursor:pointer;" onclick="navigate('chat')">
      <div style="display:flex;gap:14px;align-items:center;">
        <div style="width:44px;height:44px;background:var(--g50);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1.2rem;">👤</div>
        <div>
          <div style="font-weight:600;font-size:0.9rem;">${m.from}</div>
          <div style="font-size:0.8rem;color:var(--muted);">${m.msg}</div>
        </div>
      </div>
      <div style="text-align:right;">
        <div style="font-size:0.75rem;color:var(--muted);">${m.time}</div>
        <div style="font-size:0.75rem;background:var(--g50);color:var(--g600);padding:2px 8px;border-radius:20px;margin-top:4px;">${m.crop}</div>
      </div>
    </div>`).join('');
}

function renderHistory() {
  const list = document.getElementById('farmer-history-list');
  if(!list) return;
  const history = [
    {crop:'Wheat',qty:300,price:25,total:'₹7,500',date:'Dec 12, 2024',buyer:'Suresh Traders',status:'Sold'},
    {crop:'Onion',qty:500,price:16,total:'₹8,000',date:'Nov 28, 2024',buyer:'Amar Enterprises',status:'Sold'},
    {crop:'Rice',qty:200,price:40,total:'₹8,000',date:'Nov 10, 2024',buyer:'Mahesh & Sons',status:'Sold'},
  ];
  list.innerHTML = `<div style="overflow-x:auto;"><table style="width:100%;border-collapse:collapse;font-size:0.88rem;">
    <thead><tr style="background:var(--g50);">${['Crop','Quantity','Price','Total','Buyer','Date','Status'].map(h=>`<th style="padding:12px 16px;text-align:left;font-weight:600;color:var(--g700);">${h}</th>`).join('')}</tr></thead>
    <tbody>${history.map(h=>`<tr style="border-bottom:1px solid var(--border);">
      <td style="padding:12px 16px;font-weight:600;">${h.crop}</td>
      <td style="padding:12px 16px;">${h.qty} kg</td>
      <td style="padding:12px 16px;">₹${h.price}/kg</td>
      <td style="padding:12px 16px;font-weight:600;color:var(--g600);">${h.total}</td>
      <td style="padding:12px 16px;">${h.buyer}</td>
      <td style="padding:12px 16px;color:var(--muted);">${h.date}</td>
      <td style="padding:12px 16px;"><span style="background:#e8f5e9;color:#2e7d32;padding:3px 10px;border-radius:20px;font-size:0.78rem;font-weight:600;">${h.status}</span></td>
    </tr>`).join('')}</tbody>
  </table></div>`;
}

function filterCrops() {
  const search = (document.getElementById('dealer-search')||{value:''}).value.toLowerCase();
  const crop = (document.getElementById('f-crop')||{value:''}).value;
  const district = (document.getElementById('f-district')||{value:''}).value;
  const price = (document.getElementById('f-price')||{value:''}).value;
  let filtered = cropsData.filter(c=>{
    if(search && !c.name.toLowerCase().includes(search) && !c.district.toLowerCase().includes(search) && !c.farmer.toLowerCase().includes(search)) return false;
    if(crop && c.name!==crop) return false;
    if(district && c.district!==district) return false;
    if(price==='low' && c.price>=25) return false;
    if(price==='mid' && (c.price<25||c.price>50)) return false;
    if(price==='high' && c.price<=50) return false;
    return true;
  });
  const grid = document.getElementById('dealer-crops-grid');
  if(grid) grid.innerHTML = filtered.length?filtered.map(c=>cropCardHTML(c,true)).join(''):`<div style="text-align:center;padding:60px;color:var(--muted);grid-column:1/-1;"><span style="font-size:3rem;display:block;margin-bottom:16px;">🔍</span><h3>No crops found</h3><p>Try adjusting your filters</p></div>`;
}

function filterListings() {
  const search = (document.getElementById('list-search')||{value:''}).value.toLowerCase();
  const crop = (document.getElementById('l-crop')||{value:''}).value;
  const district = (document.getElementById('l-district')||{value:''}).value;
  const sort = (document.getElementById('l-sort')||{value:''}).value;
  let filtered = cropsData.filter(c=>{
    if(search && !c.name.toLowerCase().includes(search) && !c.district.toLowerCase().includes(search)) return false;
    if(crop && c.name!==crop) return false;
    if(district && c.district!==district) return false;
    return true;
  });
  if(sort==='price-low') filtered.sort((a,b)=>a.price-b.price);
  else if(sort==='price-high') filtered.sort((a,b)=>b.price-a.price);
  else if(sort==='qty') filtered.sort((a,b)=>b.qty-a.qty);
  const grid = document.getElementById('listings-grid');
  if(grid) grid.innerHTML = filtered.map(c=>cropCardHTML(c,true)).join('');
}

// ── CHAT ──
function initChat() {
  renderChatList();
  loadChat('suresh');
}

function renderChatList() {
  const list = document.getElementById('chat-list');
  if(!list) return;
  list.innerHTML = chatContacts.map(c=>`
    <div class="chat-item${c.id===activeChatId?' active':''}" onclick="loadChat('${c.id}')">
      <div class="chat-item-top">
        <span class="chat-item-name">${c.name}</span>
        <span class="chat-item-time">${c.time}</span>
      </div>
      <div class="chat-item-msg">Re: ${c.crop}</div>
      ${c.unread?`<span class="unread">${c.unread}</span>`:''}
    </div>`).join('');
}

function loadChat(id) {
  activeChatId = id;
  const contact = chatContacts.find(c=>c.id===id);
  document.getElementById('chat-with-name').textContent = contact.name;
  renderMessages();
  renderChatList();
  contact.unread = 0;
}

function renderMessages() {
  const container = document.getElementById('chat-messages');
  if(!container) return;
  const msgs = chatMessages[activeChatId]||[];
  container.innerHTML = msgs.map(m=>`
    <div class="msg-wrap${m.s==='s'?' sent':''}">
      <div class="msg-bubble${m.s==='s'?' msg-sent':' msg-received'}">${m.t}</div>
      <div class="msg-time" style="font-size:0.7rem;color:var(--muted);margin-top:2px;">${m.ts}</div>
    </div>`).join('');
  container.scrollTop = container.scrollHeight;
}

function sendMsg() {
  const input = document.getElementById('chat-input');
  const lang = document.getElementById('chat-lang').value;
  const text = input.value.trim();
  if(!text) return;
  const now = new Date();
  const ts = now.toLocaleTimeString('en-IN',{hour:'2-digit',minute:'2-digit'});
  if(!chatMessages[activeChatId]) chatMessages[activeChatId]=[];
  chatMessages[activeChatId].push({s:'s',t:text,ts});
  input.value = '';
  renderMessages();
  // simulate reply
  setTimeout(()=>{
    const replies = lang==='hi'
      ?['समझ गया, मैं आपसे संपर्क करूंगा।','ठीक है, बढ़िया।','क्या आप डिलीवरी दे सकते हैं?']
      :['Understood, will get back to you.','Sounds good!','Can you arrange delivery?','What is the final price?'];
    chatMessages[activeChatId].push({s:'r',t:replies[Math.floor(Math.random()*replies.length)],ts:new Date().toLocaleTimeString('en-IN',{hour:'2-digit',minute:'2-digit'})});
    renderMessages();
    showNotif(chatContacts.find(c=>c.id===activeChatId)?.name+' replied');
  },1200+Math.random()*1000);
}

// ── UPLOAD ──
function previewImages(e) {
  const files = Array.from(e.target.files).slice(0,5);
  const container = document.getElementById('preview-imgs');
  container.innerHTML = '';
  files.forEach(f=>{
    const reader = new FileReader();
    reader.onload = ev=>{
      const img = document.createElement('img');
      img.src = ev.target.result;
      container.appendChild(img);
    };
    reader.readAsDataURL(f);
  });
}

function submitCrop() {
  const name = document.getElementById('crop-name').value;
  const qty = document.getElementById('quantity').value;
  const price = document.getElementById('price').value;
  const district = document.getElementById('district').value;
  if(!name||!qty||!price||!district) {
    showToast('⚠️ Please fill all required fields');
    return;
  }
  if(parseInt(qty)<100) {
    showToast('⚠️ Minimum quantity is 100 kg');
    return;
  }
  showToast('✅ Crop listed successfully! Dealers in '+district+' can now see it.');
  setTimeout(()=>navigate('farmer-dash'),1200);
}

// ── MODAL ──
function showModal() { document.getElementById('modal').classList.add('show'); }
function closeModal() { document.getElementById('modal').classList.remove('show'); }
function confirmPurchase() {
  closeModal();
  showToast('🎉 Deal confirmed! Farmer contact shared. Check chat for details.');
  // mark sold
  cropsData[0].status = 'sold';
}

// ── TOAST & NOTIF ──
function showToast(msg) {
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.classList.add('show');
  setTimeout(()=>t.classList.remove('show'),3000);
}

function showNotif(msg) {
  const n = document.getElementById('notif');
  document.getElementById('notif-text').textContent = msg;
  n.classList.add('show');
  setTimeout(()=>n.classList.remove('show'),3500);
}

// ── TABS ──
function switchTab(btn, tabId) {
  btn.closest('.dashboard-layout').querySelectorAll('.tab-btn').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  btn.closest('.dashboard-layout').querySelectorAll('.tab-content').forEach(t=>t.classList.remove('active'));
  document.getElementById(tabId).classList.add('active');
  if(tabId==='tab-browse') filterCrops();
  if(tabId==='tab-my-purchases') renderPurchases();
  if(tabId==='tab-saved') renderSaved();
}

function renderPurchases() {
  const el = document.getElementById('purchase-history');
  if(!el) return;
  const items = [{crop:'Wheat',farmer:'Ramesh Kumar',qty:300,price:25,date:'Dec 10'},
    {crop:'Rice',farmer:'Anil Yadav',qty:200,price:40,date:'Nov 28'}];
  el.innerHTML = items.map(i=>`<div style="display:flex;justify-content:space-between;padding:16px 0;border-bottom:1px solid var(--border);align-items:center;">
    <div><strong>${i.crop}</strong> from ${i.farmer}<div style="font-size:0.8rem;color:var(--muted);margin-top:2px;">${i.qty}kg @ ₹${i.price}/kg</div></div>
    <div style="text-align:right;"><strong style="color:var(--g600);">₹${(i.qty*i.price).toLocaleString('en-IN')}</strong><div style="font-size:0.75rem;color:var(--muted);">${i.date}</div></div>
  </div>`).join('');
}

function renderSaved() {
  const grid = document.getElementById('saved-crops-grid');
  if(grid) grid.innerHTML = cropsData.slice(0,3).map(c=>cropCardHTML(c,true)).join('');
}

// ── SCROLL REVEAL ──
function initReveal() {
  const obs = new IntersectionObserver((entries)=>{
    entries.forEach(e=>{if(e.isIntersecting){e.target.classList.add('visible');}});
  },{threshold:0.1});
  document.querySelectorAll('.reveal').forEach(el=>obs.observe(el));
}

// ── INIT ──
window.addEventListener('load',()=>{
  initReveal();
  renderListings();
  renderFarmerDash();
  // simulate notification after 4s
  setTimeout(()=>showNotif('Suresh Traders is interested in your Wheat!'),4000);
});

// Close modal on overlay click
document.getElementById('modal').addEventListener('click',function(e){if(e.target===this)closeModal();});
</script>
</body>
</html>

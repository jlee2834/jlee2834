<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Jacob Lee — GitHub Hub</title>
<style>
  :root{
    --bg:#0a0a0a;
    --card:#131313;
    --card-2:#141414;
    --border:#262626;
    --border-soft:#1e1e1e;
    --text:#f2f2f2;
    --text-dim:#9a9a9a;
    --text-faint:#6b6b6b;
    --green:#3fb950;
    --chip:#1a1a1a;
  }
  *{box-sizing:border-box; margin:0; padding:0;}
  body{
    background:var(--bg);
    font-family:-apple-system, BlinkMacSystemFont, "Segoe UI", Helvetica, Arial, sans-serif;
    color:var(--text);
    width:1080px;
    padding:32px;
  }
  .wrap{ display:flex; gap:28px; align-items:flex-start; }

  /* ---------- LEFT SIDEBAR ---------- */
  .sidebar{ width:236px; flex-shrink:0; }
  .avatar{
    width:220px; height:220px; border-radius:50%;
    background: radial-gradient(circle at 30% 25%, #3a3a3a, #141414 70%);
    border:1px solid var(--border);
    display:flex; align-items:center; justify-content:center;
    font-size:64px; font-weight:700; color:#4d4d4d;
    letter-spacing:1px;
    margin-bottom:18px;
  }
  .name{ font-size:26px; font-weight:700; color:var(--text); margin-bottom:4px;}
  .handle{ font-size:15px; color:var(--text-dim); margin-bottom:16px;}
  .follow-btn{
    display:flex; align-items:center; justify-content:center; gap:8px;
    width:100%; padding:10px 14px; border-radius:8px;
    background:#1c1c1c; border:1px solid var(--border);
    color:var(--text); font-size:14px; font-weight:600;
    margin-bottom:18px;
  }
  .follow-btn svg{ width:16px; height:16px; fill:var(--text); }
  .tags{ display:flex; flex-wrap:wrap; gap:6px; margin-bottom:18px; }
  .tag{
    font-size:11.5px; color:var(--text-dim); background:var(--chip);
    border:1px solid var(--border); border-radius:20px; padding:5px 11px;
  }
  .meta-list{ display:flex; flex-direction:column; gap:10px; margin-bottom:16px; }
  .meta-row{ display:flex; align-items:center; gap:9px; font-size:13.5px; color:var(--text-dim); }
  .meta-row svg{ width:15px; height:15px; flex-shrink:0; stroke:var(--text-faint); fill:none; stroke-width:1.8; }
  .follow-count{ font-size:13.5px; color:var(--text-dim); margin-bottom:8px; }
  .follow-count b{ color:var(--text); font-weight:600; }
  .views-row{ display:flex; align-items:center; gap:9px; font-size:13.5px; color:var(--text-faint); }
  .views-row svg{ width:15px; height:15px; stroke:var(--text-faint); fill:none; stroke-width:1.8; }

  /* ---------- MAIN COLUMN ---------- */
  .main{ flex:1; display:flex; flex-direction:column; gap:16px; min-width:0; }
  .card{
    background:var(--card); border:1px solid var(--border); border-radius:14px;
    padding:20px 22px;
  }

  .banner{ display:flex; justify-content:space-between; align-items:flex-start; }
  .banner h1{ font-size:21px; font-weight:700; margin-bottom:6px; }
  .banner p{ font-size:13.5px; color:var(--text-dim); }
  .banner .powered{ font-size:12px; color:var(--text-faint); white-space:nowrap; }
  .banner .powered b{ color:var(--green); }

  .stats-row{ display:grid; grid-template-columns:repeat(4,1fr); gap:16px; }
  .stat-card{
    background:var(--card); border:1px solid var(--border); border-radius:14px;
    padding:20px 10px; display:flex; flex-direction:column; align-items:center; gap:8px;
  }
  .stat-card svg{ width:18px; height:18px; stroke:var(--text-dim); fill:none; stroke-width:1.7; }
  .stat-num{ font-size:26px; font-weight:700; color:var(--text); }
  .stat-label{ font-size:10.5px; letter-spacing:0.06em; color:var(--text-faint); text-transform:uppercase; }

  .contrib-head{ display:flex; justify-content:space-between; align-items:center; margin-bottom:14px; }
  .contrib-head h2{ font-size:15px; font-weight:700; }
  .contrib-head .total{ font-size:13px; color:var(--text-dim); }
  .contrib-head .total b{ color:var(--text); }
  .month-labels{ display:flex; font-size:11px; color:var(--text-faint); margin-bottom:6px; padding-left:2px; }
  .month-labels span{ width:56px; }
  .grid-wrap{ overflow:hidden; }
  .contrib-foot{ font-size:12px; color:var(--text-faint); margin-top:10px; }

  .two-col{ display:grid; grid-template-columns:1fr 1fr; gap:16px; }
  .section-label{ font-size:11px; letter-spacing:0.08em; color:var(--text-faint); font-weight:700; margin-bottom:14px; }
  .chip-row{ display:flex; flex-wrap:wrap; gap:8px; }
  .lang-chip{
    display:flex; align-items:center; gap:7px; font-size:12.5px; color:var(--text);
    background:var(--chip); border:1px solid var(--border); border-radius:20px; padding:6px 12px;
  }
  .dot{ width:8px; height:8px; border-radius:50%; flex-shrink:0; }

  .donut-row{ display:flex; align-items:center; gap:22px; }
  .donut-center-label{ font-size:11px; fill:var(--text-faint); }
  .legend{ display:flex; flex-direction:column; gap:11px; flex:1; }
  .legend-row{ display:flex; align-items:center; justify-content:space-between; font-size:13px; }
  .legend-left{ display:flex; align-items:center; gap:9px; color:var(--text); }
  .legend-pct{ color:var(--text-dim); font-weight:600; }
  .donut-foot{ font-size:11.5px; color:var(--text-faint); margin-top:14px; }

  .proj-head{ display:flex; justify-content:space-between; align-items:center; }
  .proj-head h2{ font-size:16px; font-weight:700; display:flex; align-items:center; gap:8px; }
  .sort-btn{
    font-size:12.5px; color:var(--text-dim); background:var(--chip); border:1px solid var(--border);
    border-radius:8px; padding:7px 12px; display:flex; align-items:center; gap:6px;
  }

  .proj-grid{ display:grid; grid-template-columns:1fr 1fr; gap:16px; }
  .proj-card{
    background:var(--card); border:1px solid var(--border); border-radius:14px; padding:18px 20px;
  }
  .proj-top{ display:flex; justify-content:space-between; align-items:flex-start; margin-bottom:8px;}
  .proj-name{ display:flex; align-items:center; gap:7px; font-size:15px; font-weight:700; color:var(--green); }
  .proj-name svg{ width:15px; height:15px; stroke:var(--green); fill:none; stroke-width:1.8; }
  .lang-pill{ font-size:11px; color:var(--text-dim); background:var(--chip); border:1px solid var(--border); border-radius:12px; padding:3px 9px; display:flex; align-items:center; gap:5px;}
  .proj-desc{ font-size:13px; color:var(--text-dim); line-height:1.5; margin-bottom:16px; min-height:38px;}
  .proj-foot{ display:flex; gap:16px; font-size:12.5px; color:var(--text-faint); }
  .proj-foot span{ display:flex; align-items:center; gap:5px; }
  .proj-foot svg{ width:13px; height:13px; stroke:var(--text-faint); fill:none; stroke-width:1.8;}

  .footer-brand{ display:flex; justify-content:flex-end; align-items:center; gap:8px; font-size:12.5px; color:var(--text-faint); margin-top:6px; }
  .footer-brand svg{ width:15px; height:15px; fill:var(--text-faint); }
</style>
</head>
<body>

<div class="wrap">

  <!-- LEFT SIDEBAR -->
  <div class="sidebar">
    <div class="avatar">JL</div>
    <div class="name">Jacob Lee</div>
    <div class="handle">@jlee2834</div>

    <div class="follow-btn">
      <svg viewBox="0 0 16 16"><path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.01 8.01 0 0 0 16 8c0-4.42-3.58-8-8-8z"/></svg>
      Follow on GitHub
    </div>

    <div class="tags">
      <div class="tag">IT Support</div>
      <div class="tag">Cybersecurity</div>
      <div class="tag">Homelab Engineer</div>
      <div class="tag">Highly Active</div>
    </div>

    <div class="meta-list">
      <div class="meta-row">
        <svg viewBox="0 0 24 24"><path d="M20 10c0 6-8 12-8 12s-8-6-8-12a8 8 0 0 1 16 0z"/><circle cx="12" cy="10" r="3"/></svg>
        United States
      </div>
      <div class="meta-row">
        <svg viewBox="0 0 24 24"><rect x="3" y="4" width="18" height="18" rx="2"/><path d="M16 2v4M8 2v4M3 10h18"/></svg>
        Joined March 2022
      </div>
    </div>

    <div class="follow-count"><b>89</b> followers &nbsp;·&nbsp; 12 following</div>
    <div class="views-row">
      <svg viewBox="0 0 24 24"><path d="M1 12s4-7 11-7 11 7 11 7-4 7-11 7-11-7-11-7z"/><circle cx="12" cy="12" r="3"/></svg>
      123 views
    </div>
  </div>

  <!-- MAIN COLUMN -->
  <div class="main">

    <div class="card banner">
      <div>
        <h1>Welcome to Jacob Lee's Hub</h1>
        <p>Explore his open source contributions and projects</p>
      </div>
      <div class="powered">GitHub Profile Dashboard</div>
    </div>

    <div class="stats-row">
      <div class="stat-card">
        <svg viewBox="0 0 24 24"><path d="M3 7a2 2 0 0 1 2-2h4l2 3h8a2 2 0 0 1 2 2v7a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V7z"/></svg>
        <div class="stat-num">18</div>
        <div class="stat-label">Total Repos</div>
      </div>
      <div class="stat-card">
        <svg viewBox="0 0 24 24"><polygon points="12 2 15 9 22 9.5 17 14.5 18.5 22 12 18 5.5 22 7 14.5 2 9.5 9 9 12 2"/></svg>
        <div class="stat-num">146</div>
        <div class="stat-label">Total Stars</div>
      </div>
      <div class="stat-card">
        <svg viewBox="0 0 24 24"><circle cx="9" cy="8" r="3.2"/><path d="M2.5 20c0-3.6 2.9-6 6.5-6s6.5 2.4 6.5 6"/><circle cx="17" cy="8" r="2.6"/><path d="M16 14.2c2.6.5 4.5 2.5 4.5 5.8"/></svg>
        <div class="stat-num">89</div>
        <div class="stat-label">Followers</div>
      </div>
      <div class="stat-card">
        <svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="9"/><path d="M12 7v5l3.5 2"/></svg>
        <div class="stat-num">3+</div>
        <div class="stat-label">Years Active</div>
      </div>
    </div>

    <div class="card">
      <div class="contrib-head">
        <h2>Contributions</h2>
        <div class="total">Total Contributions: <b>3.2k</b></div>
      </div>
      <div class="month-labels">
        <span>Jan</span><span>Feb</span><span>Mar</span><span>Apr</span><span>May</span><span>Jun</span><span>Jul</span><span>Aug</span><span>Sep</span><span>Oct</span><span>Nov</span><span>Dec</span>
      </div>
      <div class="grid-wrap">
        <svg xmlns="http://www.w3.org/2000/svg" width="728" height="98" viewBox="0 0 728 98"><rect x="0" y="0" width="11" height="11" rx="2" fill="#161b22"/><rect x="0" y="14" width="11" height="11" rx="2" fill="#161b22"/><rect x="0" y="28" width="11" height="11" rx="2" fill="#161b22"/><rect x="0" y="42" width="11" height="11" rx="2" fill="#006d32"/><rect x="0" y="56" width="11" height="11" rx="2" fill="#006d32"/><rect x="0" y="70" width="11" height="11" rx="2" fill="#26a641"/><rect x="0" y="84" width="11" height="11" rx="2" fill="#161b22"/><rect x="14" y="0" width="11" height="11" rx="2" fill="#161b22"/><rect x="14" y="14" width="11" height="11" rx="2" fill="#161b22"/><rect x="14" y="28" width="11" height="11" rx="2" fill="#0e4429"/><rect x="14" y="42" width="11" height="11" rx="2" fill="#161b22"/><rect x="14" y="56" width="11" height="11" rx="2" fill="#161b22"/><rect x="14" y="70" width="11" height="11" rx="2" fill="#0e4429"/><rect x="14" y="84" width="11" height="11" rx="2" fill="#0e4429"/><rect x="28" y="0" width="11" height="11" rx="2" fill="#0e4429"/><rect x="28" y="14" width="11" height="11" rx="2" fill="#006d32"/><rect x="28" y="28" width="11" height="11" rx="2" fill="#161b22"/><rect x="28" y="42" width="11" height="11" rx="2" fill="#006d32"/><rect x="28" y="56" width="11" height="11" rx="2" fill="#006d32"/><rect x="28" y="70" width="11" height="11" rx="2" fill="#161b22"/><rect x="28" y="84" width="11" height="11" rx="2" fill="#161b22"/><rect x="42" y="0" width="11" height="11" rx="2" fill="#161b22"/><rect x="42" y="14" width="11" height="11" rx="2" fill="#161b22"/><rect x="42" y="28" width="11" height="11" rx="2" fill="#161b22"/><rect x="42" y="42" width="11" height="11" rx="2" fill="#006d32"/><rect x="42" y="56" width="11" height="11" rx="2" fill="#0e4429"/><rect x="42" y="70" width="11" height="11" rx="2" fill="#006d32"/><rect x="42" y="84" width="11" height="11" rx="2" fill="#006d32"/><rect x="56" y="0" width="11" height="11" rx="2" fill="#39d353"/><rect x="56" y="14" width="11" height="11" rx="2" fill="#0e4429"/><rect x="56" y="28" width="11" height="11" rx="2" fill="#0e4429"/><rect x="56" y="42" width="11" height="11" rx="2" fill="#006d32"/><rect x="56" y="56" width="11" height="11" rx="2" fill="#0e4429"/><rect x="56" y="70" width="11" height="11" rx="2" fill="#26a641"/><rect x="56" y="84" width="11" height="11" rx="2" fill="#0e4429"/><rect x="70" y="0" width="11" height="11" rx="2" fill="#161b22"/><rect x="70" y="14" width="11" height="11" rx="2" fill="#161b22"/><rect x="70" y="28" width="11" height="11" rx="2" fill="#161b22"/><rect x="70" y="42" width="11" height="11" rx="2" fill="#161b22"/><rect x="70" y="56" width="11" height="11" rx="2" fill="#161b22"/><rect x="70" y="70" width="11" height="11" rx="2" fill="#161b22"/><rect x="70" y="84" width="11" height="11" rx="2" fill="#161b22"/><rect x="84" y="0" width="11" height="11" rx="2" fill="#0e4429"/><rect x="84" y="14" width="11" height="11" rx="2" fill="#0e4429"/><rect x="84" y="28" width="11" height="11" rx="2" fill="#161b22"/><rect x="84" y="42" width="11" height="11" rx="2" fill="#161b22"/><rect x="84" y="56" width="11" height="11" rx="2" fill="#26a641"/><rect x="84" y="70" width="11" height="11" rx="2" fill="#0e4429"/><rect x="84" y="84" width="11" height="11" rx="2" fill="#0e4429"/><rect x="98" y="0" width="11" height="11" rx="2" fill="#006d32"/><rect x="98" y="14" width="11" height="11" rx="2" fill="#161b22"/><rect x="98" y="28" width="11" height="11" rx="2" fill="#0e4429"/><rect x="98" y="42" width="11" height="11" rx="2" fill="#39d353"/><rect x="98" y="56" width="11" height="11" rx="2" fill="#0e4429"/><rect x="98" y="70" width="11" height="11" rx="2" fill="#0e4429"/><rect x="98" y="84" width="11" height="11" rx="2" fill="#006d32"/><rect x="112" y="0" width="11" height="11" rx="2" fill="#006d32"/><rect x="112" y="14" width="11" height="11" rx="2" fill="#161b22"/><rect x="112" y="28" width="11" height="11" rx="2" fill="#161b22"/><rect x="112" y="42" width="11" height="11" rx="2" fill="#161b22"/><rect x="112" y="56" width="11" height="11" rx="2" fill="#161b22"/><rect x="112" y="70" width="11" height="11" rx="2" fill="#161b22"/><rect x="112" y="84" width="11" height="11" rx="2" fill="#26a641"/><rect x="126" y="0" width="11" height="11" rx="2" fill="#161b22"/><rect x="126" y="14" width="11" height="11" rx="2" fill="#006d32"/><rect x="126" y="28" width="11" height="11" rx="2" fill="#0e4429"/><rect x="126" y="42" width="11" height="11" rx="2" fill="#26a641"/><rect x="126" y="56" width="11" height="11" rx="2" fill="#0e4429"/><rect x="126" y="70" width="11" height="11" rx="2" fill="#161b22"/><rect x="126" y="84" width="11" height="11" rx="2" fill="#161b22"/><rect x="140" y="0" width="11" height="11" rx="2" fill="#161b22"/><rect x="140" y="14" width="11" height="11" rx="2" fill="#0e4429"/><rect x="140" y="28" width="11" height="11" rx="2" fill="#26a641"/><rect x="140" y="42" width="11" height="11" rx="2" fill="#0e4429"/><rect x="140" y="56" width="11" height="11" rx="2" fill="#161b22"/><rect x="140" y="70" width="11" height="11" rx="2" fill="#39d353"/><rect x="140" y="84" width="11" height="11" rx="2" fill="#0e4429"/><rect x="154" y="0" width="11" height="11" rx="2" fill="#161b22"/><rect x="154" y="14" width="11" height="11" rx="2" fill="#0e4429"/><rect x="154" y="28" width="11" height="11" rx="2" fill="#26a641"/><rect x="154" y="42" width="11" height="11" rx="2" fill="#39d353"/><rect x="154" y="56" width="11" height="11" rx="2" fill="#26a641"/><rect x="154" y="70" width="11" height="11" rx="2" fill="#0e4429"/><rect x="154" y="84" width="11" height="11" rx="2" fill="#26a641"/><rect x="168" y="0" width="11" height="11" rx="2" fill="#0e4429"/><rect x="168" y="14" width="11" height="11" rx="2" fill="#39d353"/><rect x="168" y="28" width="11" height="11" rx="2" fill="#26a641"/><rect x="168" y="42" width="11" height="11" rx="2" fill="#161b22"/><rect x="168" y="56" width="11" height="11" rx="2" fill="#006d32"/><rect x="168" y="70" width="11" height="11" rx="2" fill="#006d32"/><rect x="168" y="84" width="11" height="11" rx="2" fill="#0e4429"/><rect x="182" y="0" width="11" height="11" rx="2" fill="#0e4429"/><rect x="182" y="14" width="11" height="11" rx="2" fill="#161b22"/><rect x="182" y="28" width="11" height="11" rx="2" fill="#0e4429"/><rect x="182" y="42" width="11" height="11" rx="2" fill="#0e4429"/><rect x="182" y="56" width="11" height="11" rx="2" fill="#39d353"/><rect x="182" y="70" width="11" height="11" rx="2" fill="#26a641"/><rect x="182" y="84" width="11" height="11" rx="2" fill="#161b22"/><rect x="196" y="0" width="11" height="11" rx="2" fill="#161b22"/><rect x="196" y="14" width="11" height="11" rx="2" fill="#26a641"/><rect x="196" y="28" width="11" height="11" rx="2" fill="#26a641"/><rect x="196" y="42" width="11" height="11" rx="2" fill="#161b22"/><rect x="196" y="56" width="11" height="11" rx="2" fill="#0e4429"/><rect x="196" y="70" width="11" height="11" rx="2" fill="#0e4429"/><rect x="196" y="84" width="11" height="11" rx="2" fill="#161b22"/><rect x="210" y="0" width="11" height="11" rx="2" fill="#0e4429"/><rect x="210" y="14" width="11" height="11" rx="2" fill="#006d32"/><rect x="210" y="28" width="11" height="11" rx="2" fill="#0e4429"/><rect x="210" y="42" width="11" height="11" rx="2" fill="#161b22"/><rect x="210" y="56" width="11" height="11" rx="2" fill="#161b22"/><rect x="210" y="70" width="11" height="11" rx="2" fill="#161b22"/><rect x="210" y="84" width="11" height="11" rx="2" fill="#26a641"/><rect x="224" y="0" width="11" height="11" rx="2" fill="#006d32"/><rect x="224" y="14" width="11" height="11" rx="2" fill="#161b22"/><rect x="224" y="28" width="11" height="11" rx="2" fill="#161b22"/><rect x="224" y="42" width="11" height="11" rx="2" fill="#26a641"/><rect x="224" y="56" width="11" height="11" rx="2" fill="#26a641"/><rect x="224" y="70" width="11" height="11" rx="2" fill="#161b22"/><rect x="224" y="84" width="11" height="11" rx="2" fill="#0e4429"/><rect x="238" y="0" width="11" height="11" rx="2" fill="#39d353"/><rect x="238" y="14" width="11" height="11" rx="2" fill="#39d353"/><rect x="238" y="28" width="11" height="11" rx="2" fill="#0e4429"/><rect x="238" y="42" width="11" height="11" rx="2" fill="#26a641"/><rect x="238" y="56" width="11" height="11" rx="2" fill="#26a641"/><rect x="238" y="70" width="11" height="11" rx="2" fill="#006d32"/><rect x="238" y="84" width="11" height="11" rx="2" fill="#39d353"/><rect x="252" y="0" width="11" height="11" rx="2" fill="#161b22"/><rect x="252" y="14" width="11" height="11" rx="2" fill="#0e4429"/><rect x="252" y="28" width="11" height="11" rx="2" fill="#006d32"/><rect x="252" y="42" width="11" height="11" rx="2" fill="#161b22"/><rect x="252" y="56" width="11" height="11" rx="2" fill="#161b22"/><rect x="252" y="70" width="11" height="11" rx="2" fill="#39d353"/><rect x="252" y="84" width="11" height="11" rx="2" fill="#0e4429"/><rect x="266" y="0" width="11" height="11" rx="2" fill="#0e4429"/><rect x="266" y="14" width="11" height="11" rx="2" fill="#161b22"/><rect x="266" y="28" width="11" height="11" rx="2" fill="#161b22"/><rect x="266" y="42" width="11" height="11" rx="2" fill="#161b22"/><rect x="266" y="56" width="11" height="11" rx="2" fill="#0e4429"/><rect x="266" y="70" width="11" height="11" rx="2" fill="#161b22"/><rect x="266" y="84" width="11" height="11" rx="2" fill="#161b22"/><rect x="280" y="0" width="11" height="11" rx="2" fill="#26a641"/><rect x="280" y="14" width="11" height="11" rx="2" fill="#006d32"/><rect x="280" y="28" width="11" height="11" rx="2" fill="#39d353"/><rect x="280" y="42" width="11" height="11" rx="2" fill="#39d353"/><rect x="280" y="56" width="11" height="11" rx="2" fill="#0e4429"/><rect x="280" y="70" width="11" height="11" rx="2" fill="#006d32"/><rect x="280" y="84" width="11" height="11" rx="2" fill="#39d353"/><rect x="294" y="0" width="11" height="11" rx="2" fill="#161b22"/><rect x="294" y="14" width="11" height="11" rx="2" fill="#26a641"/><rect x="294" y="28" width="11" height="11" rx="2" fill="#0e4429"/><rect x="294" y="42" width="11" height="11" rx="2" fill="#0e4429"/><rect x="294" y="56" width="11" height="11" rx="2" fill="#006d32"/><rect x="294" y="70" width="11" height="11" rx="2" fill="#006d32"/><rect x="294" y="84" width="11" height="11" rx="2" fill="#161b22"/><rect x="308" y="0" width="11" height="11" rx="2" fill="#26a641"/><rect x="308" y="14" width="11" height="11" rx="2" fill="#26a641"/><rect x="308" y="28" width="11" height="11" rx="2" fill="#26a641"/><rect x="308" y="42" width="11" height="11" rx="2" fill="#39d353"/><rect x="308" y="56" width="11" height="11" rx="2" fill="#39d353"/><rect x="308" y="70" width="11" height="11" rx="2" fill="#39d353"/><rect x="308" y="84" width="11" height="11" rx="2" fill="#0e4429"/><rect x="322" y="0" width="11" height="11" rx="2" fill="#161b22"/><rect x="322" y="14" width="11" height="11" rx="2" fill="#26a641"/><rect x="322" y="28" width="11" height="11" rx="2" fill="#161b22"/><rect x="322" y="42" width="11" height="11" rx="2" fill="#161b22"/><rect x="322" y="56" width="11" height="11" rx="2" fill="#0e4429"/><rect x="322" y="70" width="11" height="11" rx="2" fill="#0e4429"/><rect x="322" y="84" width="11" height="11" rx="2" fill="#161b22"/><rect x="336" y="0" width="11" height="11" rx="2" fill="#26a641"/><rect x="336" y="14" width="11" height="11" rx="2" fill="#0e4429"/><rect x="336" y="28" width="11" height="11" rx="2" fill="#26a641"/><rect x="336" y="42" width="11" height="11" rx="2" fill="#0e4429"/><rect x="336" y="56" width="11" height="11" rx="2" fill="#161b22"/><rect x="336" y="70" width="11" height="11" rx="2" fill="#39d353"/><rect x="336" y="84" width="11" height="11" rx="2" fill="#006d32"/><rect x="350" y="0" width="11" height="11" rx="2" fill="#26a641"/><rect x="350" y="14" width="11" height="11" rx="2" fill="#006d32"/><rect x="350" y="28" width="11" height="11" rx="2" fill="#161b22"/><rect x="350" y="42" width="11" height="11" rx="2" fill="#0e4429"/><rect x="350" y="56" width="11" height="11" rx="2" fill="#161b22"/><rect x="350" y="70" width="11" height="11" rx="2" fill="#0e4429"/><rect x="350" y="84" width="11" height="11" rx="2" fill="#161b22"/><rect x="364" y="0" width="11" height="11" rx="2" fill="#39d353"/><rect x="364" y="14" width="11" height="11" rx="2" fill="#161b22"/><rect x="364" y="28" width="11" height="11" rx="2" fill="#006d32"/><rect x="364" y="42" width="11" height="11" rx="2" fill="#0e4429"/><rect x="364" y="56" width="11" height="11" rx="2" fill="#0e4429"/><rect x="364" y="70" width="11" height="11" rx="2" fill="#39d353"/><rect x="364" y="84" width="11" height="11" rx="2" fill="#39d353"/><rect x="378" y="0" width="11" height="11" rx="2" fill="#006d32"/><rect x="378" y="14" width="11" height="11" rx="2" fill="#161b22"/><rect x="378" y="28" width="11" height="11" rx="2" fill="#161b22"/><rect x="378" y="42" width="11" height="11" rx="2" fill="#39d353"/><rect x="378" y="56" width="11" height="11" rx="2" fill="#0e4429"/><rect x="378" y="70" width="11" height="11" rx="2" fill="#0e4429"/><rect x="378" y="84" width="11" height="11" rx="2" fill="#006d32"/><rect x="392" y="0" width="11" height="11" rx="2" fill="#26a641"/><rect x="392" y="14" width="11" height="11" rx="2" fill="#26a641"/><rect x="392" y="28" width="11" height="11" rx="2" fill="#39d353"/><rect x="392" y="42" width="11" height="11" rx="2" fill="#006d32"/><rect x="392" y="56" width="11" height="11" rx="2" fill="#39d353"/><rect x="392" y="70" width="11" height="11" rx="2" fill="#0e4429"/><rect x="392" y="84" width="11" height="11" rx="2" fill="#006d32"/><rect x="406" y="0" width="11" height="11" rx="2" fill="#006d32"/><rect x="406" y="14" width="11" height="11" rx="2" fill="#161b22"/><rect x="406" y="28" width="11" height="11" rx="2" fill="#161b22"/><rect x="406" y="42" width="11" height="11" rx="2" fill="#26a641"/><rect x="406" y="56" width="11" height="11" rx="2" fill="#161b22"/><rect x="406" y="70" width="11" height="11" rx="2" fill="#0e4429"/><rect x="406" y="84" width="11" height="11" rx="2" fill="#0e4429"/><rect x="420" y="0" width="11" height="11" rx="2" fill="#0e4429"/><rect x="420" y="14" width="11" height="11" rx="2" fill="#0e4429"/><rect x="420" y="28" width="11" height="11" rx="2" fill="#26a641"/><rect x="420" y="42" width="11" height="11" rx="2" fill="#161b22"/><rect x="420" y="56" width="11" height="11" rx="2" fill="#006d32"/><rect x="420" y="70" width="11" height="11" rx="2" fill="#161b22"/><rect x="420" y="84" width="11" height="11" rx="2" fill="#0e4429"/><rect x="434" y="0" width="11" height="11" rx="2" fill="#161b22"/><rect x="434" y="14" width="11" height="11" rx="2" fill="#161b22"/><rect x="434" y="28" width="11" height="11" rx="2" fill="#006d32"/><rect x="434" y="42" width="11" height="11" rx="2" fill="#161b22"/><rect x="434" y="56" width="11" height="11" rx="2" fill="#0e4429"/><rect x="434" y="70" width="11" height="11" rx="2" fill="#39d353"/><rect x="434" y="84" width="11" height="11" rx="2" fill="#39d353"/><rect x="448" y="0" width="11" height="11" rx="2" fill="#006d32"/><rect x="448" y="14" width="11" height="11" rx="2" fill="#006d32"/><rect x="448" y="28" width="11" height="11" rx="2" fill="#39d353"/><rect x="448" y="42" width="11" height="11" rx="2" fill="#39d353"/><rect x="448" y="56" width="11" height="11" rx="2" fill="#39d353"/><rect x="448" y="70" width="11" height="11" rx="2" fill="#26a641"/><rect x="448" y="84" width="11" height="11" rx="2" fill="#006d32"/><rect x="462" y="0" width="11" height="11" rx="2" fill="#006d32"/><rect x="462" y="14" width="11" height="11" rx="2" fill="#0e4429"/><rect x="462" y="28" width="11" height="11" rx="2" fill="#39d353"/><rect x="462" y="42" width="11" height="11" rx="2" fill="#006d32"/><rect x="462" y="56" width="11" height="11" rx="2" fill="#161b22"/><rect x="462" y="70" width="11" height="11" rx="2" fill="#006d32"/><rect x="462" y="84" width="11" height="11" rx="2" fill="#161b22"/><rect x="476" y="0" width="11" height="11" rx="2" fill="#26a641"/><rect x="476" y="14" width="11" height="11" rx="2" fill="#161b22"/><rect x="476" y="28" width="11" height="11" rx="2" fill="#161b22"/><rect x="476" y="42" width="11" height="11" rx="2" fill="#161b22"/><rect x="476" y="56" width="11" height="11" rx="2" fill="#0e4429"/><rect x="476" y="70" width="11" height="11" rx="2" fill="#161b22"/><rect x="476" y="84" width="11" height="11" rx="2" fill="#0e4429"/><rect x="490" y="0" width="11" height="11" rx="2" fill="#161b22"/><rect x="490" y="14" width="11" height="11" rx="2" fill="#0e4429"/><rect x="490" y="28" width="11" height="11" rx="2" fill="#161b22"/><rect x="490" y="42" width="11" height="11" rx="2" fill="#0e4429"/><rect x="490" y="56" width="11" height="11" rx="2" fill="#26a641"/><rect x="490" y="70" width="11" height="11" rx="2" fill="#006d32"/><rect x="490" y="84" width="11" height="11" rx="2" fill="#161b22"/><rect x="504" y="0" width="11" height="11" rx="2" fill="#161b22"/><rect x="504" y="14" width="11" height="11" rx="2" fill="#161b22"/><rect x="504" y="28" width="11" height="11" rx="2" fill="#006d32"/><rect x="504" y="42" width="11" height="11" rx="2" fill="#0e4429"/><rect x="504" y="56" width="11" height="11" rx="2" fill="#161b22"/><rect x="504" y="70" width="11" height="11" rx="2" fill="#006d32"/><rect x="504" y="84" width="11" height="11" rx="2" fill="#0e4429"/><rect x="518" y="0" width="11" height="11" rx="2" fill="#161b22"/><rect x="518" y="14" width="11" height="11" rx="2" fill="#161b22"/><rect x="518" y="28" width="11" height="11" rx="2" fill="#26a641"/><rect x="518" y="42" width="11" height="11" rx="2" fill="#26a641"/><rect x="518" y="56" width="11" height="11" rx="2" fill="#0e4429"/><rect x="518" y="70" width="11" height="11" rx="2" fill="#006d32"/><rect x="518" y="84" width="11" height="11" rx="2" fill="#0e4429"/><rect x="532" y="0" width="11" height="11" rx="2" fill="#0e4429"/><rect x="532" y="14" width="11" height="11" rx="2" fill="#006d32"/><rect x="532" y="28" width="11" height="11" rx="2" fill="#39d353"/><rect x="532" y="42" width="11" height="11" rx="2" fill="#39d353"/><rect x="532" y="56" width="11" height="11" rx="2" fill="#39d353"/><rect x="532" y="70" width="11" height="11" rx="2" fill="#39d353"/><rect x="532" y="84" width="11" height="11" rx="2" fill="#006d32"/><rect x="546" y="0" width="11" height="11" rx="2" fill="#161b22"/><rect x="546" y="14" width="11" height="11" rx="2" fill="#006d32"/><rect x="546" y="28" width="11" height="11" rx="2" fill="#26a641"/><rect x="546" y="42" width="11" height="11" rx="2" fill="#0e4429"/><rect x="546" y="56" width="11" height="11" rx="2" fill="#0e4429"/><rect x="546" y="70" width="11" height="11" rx="2" fill="#161b22"/><rect x="546" y="84" width="11" height="11" rx="2" fill="#26a641"/><rect x="560" y="0" width="11" height="11" rx="2" fill="#39d353"/><rect x="560" y="14" width="11" height="11" rx="2" fill="#006d32"/><rect x="560" y="28" width="11" height="11" rx="2" fill="#26a641"/><rect x="560" y="42" width="11" height="11" rx="2" fill="#161b22"/><rect x="560" y="56" width="11" height="11" rx="2" fill="#006d32"/><rect x="560" y="70" width="11" height="11" rx="2" fill="#161b22"/><rect x="560" y="84" width="11" height="11" rx="2" fill="#26a641"/><rect x="574" y="0" width="11" height="11" rx="2" fill="#26a641"/><rect x="574" y="14" width="11" height="11" rx="2" fill="#006d32"/><rect x="574" y="28" width="11" height="11" rx="2" fill="#161b22"/><rect x="574" y="42" width="11" height="11" rx="2" fill="#006d32"/><rect x="574" y="56" width="11" height="11" rx="2" fill="#161b22"/><rect x="574" y="70" width="11" height="11" rx="2" fill="#26a641"/><rect x="574" y="84" width="11" height="11" rx="2" fill="#26a641"/><rect x="588" y="0" width="11" height="11" rx="2" fill="#006d32"/><rect x="588" y="14" width="11" height="11" rx="2" fill="#0e4429"/><rect x="588" y="28" width="11" height="11" rx="2" fill="#161b22"/><rect x="588" y="42" width="11" height="11" rx="2" fill="#006d32"/><rect x="588" y="56" width="11" height="11" rx="2" fill="#161b22"/><rect x="588" y="70" width="11" height="11" rx="2" fill="#161b22"/><rect x="588" y="84" width="11" height="11" rx="2" fill="#161b22"/><rect x="602" y="0" width="11" height="11" rx="2" fill="#26a641"/><rect x="602" y="14" width="11" height="11" rx="2" fill="#39d353"/><rect x="602" y="28" width="11" height="11" rx="2" fill="#161b22"/><rect x="602" y="42" width="11" height="11" rx="2" fill="#0e4429"/><rect x="602" y="56" width="11" height="11" rx="2" fill="#0e4429"/><rect x="602" y="70" width="11" height="11" rx="2" fill="#39d353"/><rect x="602" y="84" width="11" height="11" rx="2" fill="#0e4429"/><rect x="616" y="0" width="11" height="11" rx="2" fill="#161b22"/><rect x="616" y="14" width="11" height="11" rx="2" fill="#39d353"/><rect x="616" y="28" width="11" height="11" rx="2" fill="#161b22"/><rect x="616" y="42" width="11" height="11" rx="2" fill="#39d353"/><rect x="616" y="56" width="11" height="11" rx="2" fill="#161b22"/><rect x="616" y="70" width="11" height="11" rx="2" fill="#161b22"/><rect x="616" y="84" width="11" height="11" rx="2" fill="#0e4429"/><rect x="630" y="0" width="11" height="11" rx="2" fill="#161b22"/><rect x="630" y="14" width="11" height="11" rx="2" fill="#0e4429"/><rect x="630" y="28" width="11" height="11" rx="2" fill="#0e4429"/><rect x="630" y="42" width="11" height="11" rx="2" fill="#0e4429"/><rect x="630" y="56" width="11" height="11" rx="2" fill="#0e4429"/><rect x="630" y="70" width="11" height="11" rx="2" fill="#161b22"/><rect x="630" y="84" width="11" height="11" rx="2" fill="#006d32"/><rect x="644" y="0" width="11" height="11" rx="2" fill="#39d353"/><rect x="644" y="14" width="11" height="11" rx="2" fill="#26a641"/><rect x="644" y="28" width="11" height="11" rx="2" fill="#39d353"/><rect x="644" y="42" width="11" height="11" rx="2" fill="#39d353"/><rect x="644" y="56" width="11" height="11" rx="2" fill="#39d353"/><rect x="644" y="70" width="11" height="11" rx="2" fill="#26a641"/><rect x="644" y="84" width="11" height="11" rx="2" fill="#0e4429"/><rect x="658" y="0" width="11" height="11" rx="2" fill="#161b22"/><rect x="658" y="14" width="11" height="11" rx="2" fill="#161b22"/><rect x="658" y="28" width="11" height="11" rx="2" fill="#006d32"/><rect x="658" y="42" width="11" height="11" rx="2" fill="#006d32"/><rect x="658" y="56" width="11" height="11" rx="2" fill="#161b22"/><rect x="658" y="70" width="11" height="11" rx="2" fill="#161b22"/><rect x="658" y="84" width="11" height="11" rx="2" fill="#0e4429"/><rect x="672" y="0" width="11" height="11" rx="2" fill="#161b22"/><rect x="672" y="14" width="11" height="11" rx="2" fill="#161b22"/><rect x="672" y="28" width="11" height="11" rx="2" fill="#0e4429"/><rect x="672" y="42" width="11" height="11" rx="2" fill="#26a641"/><rect x="672" y="56" width="11" height="11" rx="2" fill="#006d32"/><rect x="672" y="70" width="11" height="11" rx="2" fill="#26a641"/><rect x="672" y="84" width="11" height="11" rx="2" fill="#0e4429"/><rect x="686" y="0" width="11" height="11" rx="2" fill="#0e4429"/><rect x="686" y="14" width="11" height="11" rx="2" fill="#161b22"/><rect x="686" y="28" width="11" height="11" rx="2" fill="#161b22"/><rect x="686" y="42" width="11" height="11" rx="2" fill="#0e4429"/><rect x="686" y="56" width="11" height="11" rx="2" fill="#0e4429"/><rect x="686" y="70" width="11" height="11" rx="2" fill="#006d32"/><rect x="686" y="84" width="11" height="11" rx="2" fill="#0e4429"/><rect x="700" y="0" width="11" height="11" rx="2" fill="#161b22"/><rect x="700" y="14" width="11" height="11" rx="2" fill="#0e4429"/><rect x="700" y="28" width="11" height="11" rx="2" fill="#26a641"/><rect x="700" y="42" width="11" height="11" rx="2" fill="#006d32"/><rect x="700" y="56" width="11" height="11" rx="2" fill="#161b22"/><rect x="700" y="70" width="11" height="11" rx="2" fill="#161b22"/><rect x="700" y="84" width="11" height="11" rx="2" fill="#0e4429"/><rect x="714" y="0" width="11" height="11" rx="2" fill="#161b22"/><rect x="714" y="14" width="11" height="11" rx="2" fill="#006d32"/><rect x="714" y="28" width="11" height="11" rx="2" fill="#006d32"/><rect x="714" y="42" width="11" height="11" rx="2" fill="#006d32"/><rect x="714" y="56" width="11" height="11" rx="2" fill="#161b22"/><rect x="714" y="70" width="11" height="11" rx="2" fill="#161b22"/><rect x="714" y="84" width="11" height="11" rx="2" fill="#161b22"/></svg>
      </div>
      <div class="contrib-foot">Last 52 weeks of activity.</div>
    </div>

    <div class="two-col">
      <div class="card">
        <div class="section-label">CORE TECHNOLOGIES</div>
        <div class="chip-row">
          <div class="lang-chip"><span class="dot" style="background:#4391ce"></span>PowerShell</div>
          <div class="lang-chip"><span class="dot" style="background:#3776ab"></span>Python</div>
          <div class="lang-chip"><span class="dot" style="background:#f0db4f"></span>JavaScript</div>
          <div class="lang-chip"><span class="dot" style="background:#e34c26"></span>HTML</div>
          <div class="lang-chip"><span class="dot" style="background:#264de4"></span>CSS</div>
          <div class="lang-chip"><span class="dot" style="background:#89e051"></span>Shell</div>
          <div class="lang-chip"><span class="dot" style="background:#68217a"></span>C#</div>
        </div>
      </div>

      <div class="card">
        <div class="section-label">LANGUAGES</div>
        <div class="donut-row">
          <svg width="120" height="120" viewBox="0 0 120 120">
            <!-- donut segments: PowerShell 42, Python 22, JavaScript 16, HTML 12, CSS 8 -->
            <circle cx="60" cy="60" r="46" fill="none" stroke="#242424" stroke-width="16"/>
            <circle cx="60" cy="60" r="46" fill="none" stroke="#4391ce" stroke-width="16"
              stroke-dasharray="121.4 289.0" stroke-dashoffset="0" transform="rotate(-90 60 60)"/>
            <circle cx="60" cy="60" r="46" fill="none" stroke="#3776ab" stroke-width="16"
              stroke-dasharray="63.6 289.0" stroke-dashoffset="-121.4" transform="rotate(-90 60 60)"/>
            <circle cx="60" cy="60" r="46" fill="none" stroke="#f0db4f" stroke-width="16"
              stroke-dasharray="46.2 289.0" stroke-dashoffset="-185.0" transform="rotate(-90 60 60)"/>
            <circle cx="60" cy="60" r="46" fill="none" stroke="#e34c26" stroke-width="16"
              stroke-dasharray="34.7 289.0" stroke-dashoffset="-231.2" transform="rotate(-90 60 60)"/>
            <circle cx="60" cy="60" r="46" fill="none" stroke="#264de4" stroke-width="16"
              stroke-dasharray="23.1 289.0" stroke-dashoffset="-265.9" transform="rotate(-90 60 60)"/>
            <text x="60" y="57" text-anchor="middle" fill="#f2f2f2" font-size="15" font-weight="700" font-family="-apple-system">5</text>
            <text x="60" y="72" text-anchor="middle" fill="#6b6b6b" font-size="10">langs</text>
          </svg>
          <div class="legend">
            <div class="legend-row"><div class="legend-left"><span class="dot" style="background:#4391ce"></span>PowerShell</div><div class="legend-pct">42%</div></div>
            <div class="legend-row"><div class="legend-left"><span class="dot" style="background:#3776ab"></span>Python</div><div class="legend-pct">22%</div></div>
            <div class="legend-row"><div class="legend-left"><span class="dot" style="background:#f0db4f"></span>JavaScript</div><div class="legend-pct">16%</div></div>
            <div class="legend-row"><div class="legend-left"><span class="dot" style="background:#e34c26"></span>HTML</div><div class="legend-pct">12%</div></div>
            <div class="legend-row"><div class="legend-left"><span class="dot" style="background:#264de4"></span>CSS</div><div class="legend-pct">8%</div></div>
          </div>
        </div>
        <div class="donut-foot">Based on top 20 repos</div>
      </div>
    </div>

    <div class="proj-head">
      <h2>🔖 Notable Projects</h2>
      <div class="sort-btn">Most Stars ⌄</div>
    </div>

    <div class="proj-grid">
      <div class="proj-card">
        <div class="proj-top">
          <div class="proj-name">
            <svg viewBox="0 0 24 24"><path d="M3 7a2 2 0 0 1 2-2h4l2 3h8a2 2 0 0 1 2 2v7a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V7z"/></svg>
            Enterprise-Homelab
          </div>
          <div class="lang-pill"><span class="dot" style="background:#4391ce"></span>PowerShell</div>
        </div>
        <div class="proj-desc">Proxmox-based lab with Windows Server, Active Directory, Microsoft Sentinel, Wazuh, Veeam, and full infrastructure monitoring.</div>
        <div class="proj-foot">
          <span><svg viewBox="0 0 24 24"><polygon points="12 2 15 9 22 9.5 17 14.5 18.5 22 12 18 5.5 22 7 14.5 2 9.5 9 9 12 2"/></svg>32</span>
          <span><svg viewBox="0 0 24 24"><circle cx="7" cy="6" r="2.2"/><circle cx="7" cy="18" r="2.2"/><circle cx="17" cy="12" r="2.2"/><path d="M7 8v8M9 6.5h4a3 3 0 0 1 3 3V11"/></svg>6</span>
        </div>
      </div>

      <div class="proj-card">
        <div class="proj-top">
          <div class="proj-name">
            <svg viewBox="0 0 24 24"><path d="M3 7a2 2 0 0 1 2-2h4l2 3h8a2 2 0 0 1 2 2v7a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V7z"/></svg>
            Action1-Automation
          </div>
          <div class="lang-pill"><span class="dot" style="background:#4391ce"></span>PowerShell</div>
        </div>
        <div class="proj-desc">PowerShell automation for endpoint patching, software deployment, and certificate management across 800+ endpoints.</div>
        <div class="proj-foot">
          <span><svg viewBox="0 0 24 24"><polygon points="12 2 15 9 22 9.5 17 14.5 18.5 22 12 18 5.5 22 7 14.5 2 9.5 9 9 12 2"/></svg>24</span>
          <span><svg viewBox="0 0 24 24"><circle cx="7" cy="6" r="2.2"/><circle cx="7" cy="18" r="2.2"/><circle cx="17" cy="12" r="2.2"/><path d="M7 8v8M9 6.5h4a3 3 0 0 1 3 3V11"/></svg>5</span>
        </div>
      </div>

      <div class="proj-card">
        <div class="proj-top">
          <div class="proj-name">
            <svg viewBox="0 0 24 24"><path d="M3 7a2 2 0 0 1 2-2h4l2 3h8a2 2 0 0 1 2 2v7a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V7z"/></svg>
            UniFi-Content-Filtering
          </div>
          <div class="lang-pill"><span class="dot" style="background:#4391ce"></span>PowerShell</div>
        </div>
        <div class="proj-desc">Automated SSL certificate deployment and DNS filtering policies for UniFi environments across multiple clients.</div>
        <div class="proj-foot">
          <span><svg viewBox="0 0 24 24"><polygon points="12 2 15 9 22 9.5 17 14.5 18.5 22 12 18 5.5 22 7 14.5 2 9.5 9 9 12 2"/></svg>15</span>
          <span><svg viewBox="0 0 24 24"><circle cx="7" cy="6" r="2.2"/><circle cx="7" cy="18" r="2.2"/><circle cx="17" cy="12" r="2.2"/><path d="M7 8v8M9 6.5h4a3 3 0 0 1 3 3V11"/></svg>3</span>
        </div>
      </div>

      <div class="proj-card">
        <div class="proj-top">
          <div class="proj-name">
            <svg viewBox="0 0 24 24"><path d="M3 7a2 2 0 0 1 2-2h4l2 3h8a2 2 0 0 1 2 2v7a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V7z"/></svg>
            Roommate-Expense-Tracker
          </div>
          <div class="lang-pill"><span class="dot" style="background:#f0db4f"></span>JavaScript</div>
        </div>
        <div class="proj-desc">Full-stack web application for tracking shared expenses, bills, balances, and payments between roommates.</div>
        <div class="proj-foot">
          <span><svg viewBox="0 0 24 24"><polygon points="12 2 15 9 22 9.5 17 14.5 18.5 22 12 18 5.5 22 7 14.5 2 9.5 9 9 12 2"/></svg>12</span>
          <span><svg viewBox="0 0 24 24"><circle cx="7" cy="6" r="2.2"/><circle cx="7" cy="18" r="2.2"/><circle cx="17" cy="12" r="2.2"/><path d="M7 8v8M9 6.5h4a3 3 0 0 1 3 3V11"/></svg>2</span>
        </div>
      </div>
    </div>

  </div>
</div>

</body>
</html>

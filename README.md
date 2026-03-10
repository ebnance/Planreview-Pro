
[index.html](https://github.com/user-attachments/files/25872133/index.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>PlanReview Pro + GovBuilt</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
<style>
:root{
--bg:#0b1120;--pnl:#0f1729;--pnl2:#111d33;--brd:#1a2744;--brd2:#243352;
--sf:#131f36;--sf2:#182540;--hov:#1c2d4d;
--ac:#3b82f6;--ac2:#2563eb;--acg:rgba(59,130,246,.12);
--ok:#10b981;--wn:#f59e0b;--no:#ef4444;--pu:#a855f7;--or:#f97316;--cy:#06b6d4;--pk:#ec4899;
--t1:#f1f5f9;--t2:#94a3b8;--t3:#64748b;--t4:#475569;
--gb:#0ea5e9;--gbg:rgba(14,165,233,.15);
--f:'JetBrains Mono','Fira Code',monospace;
--canvas-bg:#1a2436;--ruler-bg:#0c1322;
--login-orb-opacity:.15;--shadow-color:rgba(0,0,0,.5);
}
body.light{
--bg:#f0f2f5;--pnl:#ffffff;--pnl2:#f8f9fb;--brd:#d5dbe5;--brd2:#c0c9d6;
--sf:#edf0f5;--sf2:#e4e8ef;--hov:#dce1ea;
--ac:#2563eb;--ac2:#1d4ed8;--acg:rgba(37,99,235,.08);
--ok:#059669;--wn:#d97706;--no:#dc2626;--pu:#7c3aed;--or:#ea580c;--cy:#0891b2;--pk:#db2777;
--t1:#1e293b;--t2:#475569;--t3:#64748b;--t4:#94a3b8;
--gb:#0284c7;--gbg:rgba(2,132,199,.08);
--canvas-bg:#d8dde6;--ruler-bg:#e8ecf2;
--login-orb-opacity:.06;--shadow-color:rgba(0,0,0,.12);
}

/* Theme toggle */
.theme-toggle{width:38px;height:22px;border-radius:11px;border:1px solid var(--brd);background:var(--sf);position:relative;cursor:pointer;transition:background .3s,border-color .3s;flex-shrink:0}
.theme-toggle::after{content:'';position:absolute;top:2px;left:2px;width:16px;height:16px;border-radius:50%;background:var(--t3);transition:left .3s,background .3s}
.theme-toggle.on::after{left:18px;background:var(--wn)}
.theme-toggle .theme-icon{position:absolute;top:50%;transform:translateY(-50%);font-size:10px;pointer-events:none}
.theme-toggle .theme-icon.moon{left:4px}
.theme-toggle .theme-icon.sun{right:4px}

/* Light-mode specific overrides */
body.light ::-webkit-scrollbar-thumb{background:var(--brd2)}
body.light .login-bg .orb{opacity:var(--login-orb-opacity)}
body.light .dd{box-shadow:0 12px 40px var(--shadow-color)}
body.light .fly{box-shadow:0 8px 32px var(--shadow-color)}
body.light #cpick{box-shadow:0 8px 32px var(--shadow-color)}
body.light #sbar{box-shadow:0 12px 40px var(--shadow-color)}
body.light #vc-window{box-shadow:0 12px 40px var(--shadow-color)}
body.light #user-menu{box-shadow:0 12px 40px var(--shadow-color)}
body.light .login-box{box-shadow:0 20px 60px var(--shadow-color)}
body.light #file-menu{box-shadow:0 12px 40px var(--shadow-color)}
body.light #team-modal .tm-box{box-shadow:0 20px 60px var(--shadow-color)}
body.light .av{box-shadow:0 1px 3px rgba(0,0,0,.15)}
body.light .tb.pri{box-shadow:0 2px 8px rgba(37,99,235,.2)}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html,body{width:100%;height:100%;overflow:hidden}
body{font-family:var(--f);background:var(--bg);color:var(--t1);display:flex;flex-direction:column}
::-webkit-scrollbar{width:6px;height:6px}
::-webkit-scrollbar-track{background:transparent}
::-webkit-scrollbar-thumb{background:var(--brd);border-radius:3px}
button{font-family:var(--f);cursor:pointer}input,select{font-family:var(--f)}

/* TOPBAR */
#top{height:42px;background:var(--pnl);border-bottom:1px solid var(--brd);display:flex;align-items:center;padding:0 10px;gap:6px;flex-shrink:0;z-index:50}
.logo{display:flex;align-items:center;gap:6px;margin-right:8px}
.logo i{width:26px;height:26px;border-radius:5px;background:linear-gradient(135deg,var(--ac),var(--gb));display:flex;align-items:center;justify-content:center;font-size:12px;font-weight:800;color:#fff;font-style:normal}
.logo b{font-size:11px;letter-spacing:.5px}
.gbb{font-size:8px;color:var(--gb);background:var(--gbg);padding:1px 5px;border-radius:3px;font-weight:600}
.ntabs{display:flex;gap:1px}
.nt{background:0;border:1px solid transparent;color:var(--t3);padding:4px 10px;border-radius:4px;font-size:10px;font-weight:600}
.nt.on{background:var(--acg);border-color:rgba(59,130,246,.2);color:var(--ac)}
.sp{flex:1}
.tb{background:var(--sf);border:1px solid var(--brd);color:var(--t1);padding:4px 10px;border-radius:4px;font-size:10px;display:flex;align-items:center;gap:5px;font-weight:600}
.tb:hover{background:var(--hov);border-color:var(--brd2)}
.tb.pri{background:linear-gradient(135deg,var(--ac),var(--ac2));border:none;color:#fff}
.av{width:26px;height:26px;border-radius:50%;background:var(--ac);display:flex;align-items:center;justify-content:center;font-size:9px;font-weight:700;color:#fff}
.dd{position:absolute;top:100%;right:0;margin-top:4px;background:var(--pnl);border:1px solid var(--brd);border-radius:8px;padding:4px;z-index:200;box-shadow:0 12px 40px rgba(0,0,0,.6);display:none;width:380px}
.dd.show{display:block}

/* PROPBAR */
#propbar{height:30px;background:var(--pnl2);border-bottom:1px solid var(--brd);display:flex;align-items:center;padding:0 8px;gap:4px;flex-shrink:0;overflow-x:auto}
.pg{display:flex;align-items:center;gap:3px;padding:0 6px;border-right:1px solid var(--brd);height:100%}
.pg:last-child{border-right:none}
.pl{font-size:7px;color:var(--t3);text-transform:uppercase;letter-spacing:.3px;margin-right:2px}
.pi{background:var(--sf);border:1px solid var(--brd);border-radius:3px;padding:1px 5px;font-size:9px;color:var(--t1);width:42px;outline:none;text-align:center}
.pi:focus{border-color:var(--ac)}
.ps{background:var(--sf);border:1px solid var(--brd);border-radius:3px;padding:1px 3px;font-size:9px;color:var(--t1);outline:none}
.pb{width:22px;height:22px;border-radius:3px;border:1px solid var(--brd);background:var(--sf);color:var(--t2);font-size:11px;display:flex;align-items:center;justify-content:center}
.pb:hover{background:var(--hov);color:var(--t1)}
.pb.on{background:var(--acg);border-color:rgba(59,130,246,.3);color:var(--ac)}
.pc{width:18px;height:18px;border-radius:3px;border:2px solid var(--brd);cursor:pointer}
.pc:hover{border-color:var(--t3)}

/* MAIN */
#main{flex:1;display:flex;overflow:hidden}

/* LEFT TOOLS */
#lt{width:42px;background:var(--pnl);border-right:1px solid var(--brd);display:flex;flex-direction:column;align-items:center;padding:5px 0;gap:1px;overflow-y:auto;flex-shrink:0}
.tl{width:32px;height:30px;border-radius:4px;border:none;background:0;color:var(--t3);font-size:14px;display:flex;align-items:center;justify-content:center;transition:all .1s;position:relative}
.tl:hover{background:var(--sf);color:var(--t2)}
.tl.on{background:var(--acg);color:var(--ac);box-shadow:inset 0 0 0 1px rgba(59,130,246,.25)}
.tl .tt{display:none;position:absolute;left:38px;top:50%;transform:translateY(-50%);background:var(--pnl2);border:1px solid var(--brd);padding:2px 7px;border-radius:3px;font-size:8px;white-space:nowrap;z-index:100;color:var(--t2);pointer-events:none}
.tl:hover .tt{display:block}
.tl .fly-arrow{position:absolute;right:1px;bottom:1px;font-size:5px;color:var(--t4)}
.tsep{width:24px;height:1px;background:var(--brd);margin:2px 0}

/* FLYOUT */
.fly{position:fixed;left:48px;background:var(--pnl);border:1px solid var(--brd);border-radius:8px;padding:5px;z-index:200;box-shadow:0 8px 32px rgba(0,0,0,.5);display:none;min-width:170px}
.fly.show{display:block}
.fly-t{font-size:8px;color:var(--t4);padding:2px 8px;font-weight:700;text-transform:uppercase;letter-spacing:.5px}
.fb{width:100%;background:0;border:1px solid transparent;padding:4px 8px;border-radius:3px;display:flex;align-items:center;gap:7px;font-size:10px;font-weight:500;color:var(--t2);text-align:left}
.fb:hover{background:var(--sf);color:var(--t1)}
.fb.on{background:var(--acg);border-color:rgba(59,130,246,.2);color:var(--ac)}
.fb .fk{margin-left:auto;font-size:8px;color:var(--t4)}

/* COLOR PICKER */
#cpick{position:fixed;background:var(--pnl);border:1px solid var(--brd);border-radius:8px;padding:8px;z-index:300;box-shadow:0 8px 32px rgba(0,0,0,.5);display:none}
#cpick.show{display:grid;grid-template-columns:repeat(7,22px);gap:2px}
.cw{width:22px;height:22px;border-radius:3px;border:2px solid transparent;cursor:pointer}
.cw:hover,.cw.on{border-color:#fff}

/* VIEWER */
#vw{flex:1;display:flex;flex-direction:column;overflow:hidden;position:relative}
#stabs{height:28px;background:var(--sf);border-bottom:1px solid var(--brd);display:flex;align-items:center;padding:0 6px;gap:1px;overflow-x:auto;flex-shrink:0}
.st{background:0;border:1px solid transparent;border-bottom:2px solid transparent;color:var(--t3);padding:2px 8px;border-radius:4px 4px 0 0;font-size:9px;font-weight:600;display:flex;align-items:center;gap:3px;white-space:nowrap}
.st.on{background:var(--pnl);border-color:var(--brd);color:var(--t1)}
.st .cc{background:var(--wn);color:#000;font-size:7px;border-radius:5px;padding:0 3px;font-weight:700}
#ca{flex:1;position:relative;overflow:hidden;background:var(--canvas-bg)}

/* RULERS */
#rh{position:absolute;top:0;left:28px;right:0;height:20px;background:var(--ruler-bg);border-bottom:1px solid var(--brd);z-index:12;overflow:hidden}
#rv{position:absolute;top:20px;left:0;width:28px;bottom:0;background:var(--ruler-bg);border-right:1px solid var(--brd);z-index:12;overflow:hidden}
#rc{position:absolute;top:0;left:0;width:28px;height:20px;background:var(--ruler-bg);border-right:1px solid var(--brd);border-bottom:1px solid var(--brd);z-index:13;display:flex;align-items:center;justify-content:center;font-size:7px;color:var(--t4);cursor:pointer}
.rcv{display:block}

/* SCROLL AREA */
#ps{position:absolute;top:20px;left:28px;right:0;bottom:0;overflow:auto}
#pw{position:relative;display:inline-block;transform-origin:0 0}
#pc{display:block}
#mc{position:absolute;top:0;left:0;pointer-events:auto}

/* CROSSHAIR */
#xh,#xv{position:absolute;pointer-events:none;z-index:11}
#xh{width:100%;height:1px;background:rgba(59,130,246,.3);top:0;left:0;display:none}
#xv{height:100%;width:1px;background:rgba(59,130,246,.3);top:0;left:0;display:none}

/* UPLOAD */
#upl{position:absolute;inset:0;display:flex;flex-direction:column;align-items:center;justify-content:center;z-index:20;background:var(--bg)}
#upl.gone{display:none}
.uz{width:500px;border:2px dashed var(--brd2);border-radius:16px;padding:48px 36px;text-align:center;cursor:pointer;transition:all .3s}
.uz:hover,.uz.over{border-color:var(--ac);background:var(--acg)}
.uz h2{font-size:17px;margin:10px 0 6px}
.uz p{font-size:10px;color:var(--t2);line-height:1.7;margin-bottom:14px}
.ub{background:var(--ac);border:none;color:#fff;padding:9px 26px;border-radius:6px;font-size:11px;font-weight:700}
.uo{color:var(--t4);font-size:9px;margin:10px 0}
.ud{background:0;border:1px solid var(--brd2);color:var(--t2);padding:7px 20px;border-radius:6px;font-size:10px;font-weight:600}
.ud:hover{background:var(--sf);color:var(--t1)}

/* CONTROLS */
.cb{position:absolute;bottom:8px;display:flex;gap:3px;background:var(--pnl);padding:3px 5px;border-radius:5px;border:1px solid var(--brd);align-items:center;z-index:15}
.cb.l{left:38px}.cb.r{right:8px}.cb.c{left:50%;transform:translateX(-50%)}
.cn{height:24px;background:0;border:none;color:var(--t3);font-size:13px;border-radius:3px;padding:0 5px}
.cn:hover{background:var(--sf);color:var(--t1)}
.zt{font-size:10px;color:var(--t1);padding:0 4px;font-weight:600;line-height:24px;min-width:42px;text-align:center}
.tg{border:1px solid transparent;color:var(--t3);font-size:9px;padding:3px 6px;border-radius:3px;font-weight:600;background:0}
.tg.on{background:var(--acg);border-color:rgba(59,130,246,.2);color:var(--ac)}

/* PAGE NAV */
#pn{position:absolute;bottom:8px;left:50%;transform:translateX(-50%);display:none;gap:3px;background:var(--pnl);padding:3px 8px;border-radius:5px;border:1px solid var(--brd);align-items:center;z-index:15;font-size:10px}
#pn.show{display:flex}
#pn button{width:24px;height:24px;background:0;border:none;color:var(--t3);border-radius:3px;font-size:11px}
#pn button:hover{background:var(--sf);color:var(--t1)}

/* SCALEBAR / SCALE PICKER */
#sbar{position:absolute;top:24px;left:38px;background:var(--pnl);border:1px solid var(--brd);border-radius:10px;padding:0;z-index:15;display:none;flex-direction:column;width:360px;box-shadow:0 12px 40px rgba(0,0,0,.5);overflow:hidden}
#sbar.show{display:flex}
.sb-head{padding:10px 12px;border-bottom:1px solid var(--brd);display:flex;align-items:center;gap:6px;font-size:11px;font-weight:700}
.sb-tabs{display:flex;border-bottom:1px solid var(--brd)}
.sb-tab{flex:1;background:0;border:none;border-bottom:2px solid transparent;color:var(--t3);padding:7px 8px;font-size:9px;font-weight:600;font-family:var(--f)}
.sb-tab.on{border-bottom-color:var(--ac);color:var(--ac)}
.sb-tab:hover:not(.on){color:var(--t2)}
.sb-body{padding:10px 12px;max-height:380px;overflow-y:auto}
.sb-section{font-size:8px;color:var(--t4);font-weight:700;text-transform:uppercase;letter-spacing:.5px;margin:8px 0 4px;padding-top:6px;border-top:1px solid var(--brd)}
.sb-section:first-child{border-top:none;margin-top:0;padding-top:0}
.sb-scale{width:100%;background:0;border:1px solid transparent;padding:5px 8px;border-radius:4px;display:flex;align-items:center;gap:8px;font-size:10px;color:var(--t2);text-align:left;font-family:var(--f);cursor:pointer}
.sb-scale:hover{background:var(--sf);color:var(--t1)}
.sb-scale.on{background:var(--acg);border-color:rgba(59,130,246,.25);color:var(--ac)}
.sb-scale .sb-ratio{font-weight:700;min-width:90px}
.sb-scale .sb-desc{color:var(--t3);font-size:9px;flex:1}
.sb-scale .sb-check{font-size:12px;color:var(--ac);width:16px;text-align:center}
.sb-custom{padding:10px 0 4px}
.sb-custom-row{display:flex;gap:6px;align-items:center;margin-bottom:6px}
.sb-custom-row label{font-size:8px;color:var(--t3);min-width:50px;text-transform:uppercase;font-weight:600}
.sb-custom-row input,.sb-custom-row select{background:var(--sf);border:1px solid var(--brd);border-radius:4px;padding:5px 8px;font-size:10px;color:var(--t1);outline:none;font-family:var(--f)}
.sb-custom-row input:focus,.sb-custom-row select:focus{border-color:var(--ac)}
.sb-calib{padding:8px 12px;border-top:1px solid var(--brd);display:flex;align-items:center;gap:6px;font-size:9px;color:var(--t3)}
.sb-btn{padding:5px 14px;border-radius:4px;font-size:10px;font-weight:700;border:none;cursor:pointer;font-family:var(--f)}
.sb-btn.pri{background:var(--ac);color:#fff}
.sb-btn.pri:hover{filter:brightness(1.1)}
.sb-btn.sec{background:var(--sf);border:1px solid var(--brd);color:var(--t2)}
.sb-btn.sec:hover{background:var(--hov);color:var(--t1)}
.sb-current{padding:8px 12px;border-bottom:1px solid var(--brd);display:flex;align-items:center;gap:8px;font-size:10px;background:var(--sf)}
.sb-current .sb-cur-label{color:var(--t3);font-size:8px;text-transform:uppercase;font-weight:600}
.sb-current .sb-cur-val{font-weight:700;color:var(--ok)}

/* COORD DISPLAY */
#coords{position:absolute;bottom:8px;left:50%;transform:translateX(-50%);background:var(--pnl);border:1px solid var(--brd);border-radius:4px;padding:2px 8px;z-index:15;font-size:9px;color:var(--t2);display:none}
#coords.show{display:block}

/* RIGHT PANEL */
#rp{width:300px;background:var(--pnl);border-left:1px solid var(--brd);display:flex;flex-direction:column;flex-shrink:0}
#rt{display:flex;border-bottom:1px solid var(--brd);padding:0 2px;overflow-x:auto}
.rtb{flex:none;background:0;border:none;border-bottom:2px solid transparent;color:var(--t4);padding:6px 6px;font-size:9px;font-weight:600;white-space:nowrap}
.rtb.on{border-bottom-color:var(--ac);color:var(--ac)}
.rtb:hover:not(.on){color:var(--t2)}
#rcon{flex:1;overflow:auto;padding:6px}

/* PANEL CARDS */
.pt{font-size:10px;font-weight:700;margin-bottom:5px}
.pss{font-size:9px;font-weight:700;color:var(--t3);margin-bottom:4px;margin-top:8px}
.bdg{display:inline-block;padding:1px 5px;border-radius:3px;font-size:8px;font-weight:600;text-transform:uppercase}
.bok{background:rgba(16,185,129,.15);color:var(--ok)}.bno{background:rgba(239,68,68,.15);color:var(--no)}
.bwn{background:rgba(245,158,11,.15);color:var(--wn)}.bwt{background:rgba(100,116,139,.15);color:var(--t3)}
.cd{background:var(--sf);border:1px solid var(--brd);border-radius:5px;padding:6px 7px;margin-bottom:3px;cursor:pointer;font-size:10px}
.cd:hover{background:var(--hov)}.cd.on{background:var(--hov);border-color:var(--brd2)}
.pill{padding:1px 4px;border-radius:3px;font-size:7px;font-weight:600;border:1px solid;cursor:pointer}

/* TOAST */
#toast{position:fixed;top:12px;right:12px;z-index:9999;padding:8px 16px;border-radius:6px;color:#fff;font-size:10px;font-weight:600;box-shadow:0 4px 20px rgba(0,0,0,.4);transform:translateX(120%);transition:transform .3s;pointer-events:none}
#toast.show{transform:translateX(0)}
#toast.ok{background:var(--ok)}#toast.info{background:var(--ac)}#toast.err{background:var(--no)}

#mtip{position:fixed;background:rgba(37,99,235,.95);color:#fff;padding:2px 7px;border-radius:3px;font-size:9px;font-weight:600;pointer-events:none;z-index:999;display:none}

/* ===== LOGIN SCREEN ===== */
#login-overlay{position:fixed;inset:0;z-index:10000;background:var(--bg);display:flex;align-items:center;justify-content:center}
#login-overlay.gone{display:none}
.login-bg{position:absolute;inset:0;overflow:hidden}
.login-bg .orb{position:absolute;border-radius:50%;filter:blur(80px);opacity:.15}
.login-box{position:relative;width:420px;background:var(--pnl);border:1px solid var(--brd);border-radius:16px;padding:36px 32px;box-shadow:0 20px 60px rgba(0,0,0,.5);z-index:1}
.login-box .logo-big{display:flex;align-items:center;gap:10px;justify-content:center;margin-bottom:6px}
.login-box .logo-big i{width:36px;height:36px;border-radius:8px;background:linear-gradient(135deg,var(--ac),var(--gb));display:flex;align-items:center;justify-content:center;font-size:16px;font-weight:800;color:#fff;font-style:normal}
.login-box .logo-big b{font-size:15px;letter-spacing:.5px}
.login-box h2{text-align:center;font-size:16px;margin:16px 0 4px;font-weight:700}
.login-box .sub{text-align:center;font-size:10px;color:var(--t2);margin-bottom:20px}
.lfield{margin-bottom:12px}
.lfield label{display:block;font-size:9px;color:var(--t3);margin-bottom:4px;font-weight:600;text-transform:uppercase;letter-spacing:.3px}
.lfield input,.lfield select{width:100%;background:var(--sf);border:1px solid var(--brd);border-radius:6px;padding:9px 12px;font-size:11px;color:var(--t1);outline:none;font-family:var(--f)}
.lfield input:focus,.lfield select:focus{border-color:var(--ac);box-shadow:0 0 0 2px var(--acg)}
.lfield input::placeholder{color:var(--t4)}
.login-btn{width:100%;padding:10px;border-radius:6px;font-size:12px;font-weight:700;border:none;cursor:pointer;font-family:var(--f);margin-top:4px}
.login-btn.primary{background:linear-gradient(135deg,var(--ac),var(--ac2));color:#fff;box-shadow:0 4px 12px var(--acg)}
.login-btn.primary:hover{filter:brightness(1.1)}
.login-btn.ghost{background:transparent;border:1px solid var(--brd);color:var(--t2);margin-top:8px}
.login-btn.ghost:hover{background:var(--sf);color:var(--t1)}
.login-divider{display:flex;align-items:center;gap:10px;margin:16px 0;font-size:9px;color:var(--t4)}
.login-divider::before,.login-divider::after{content:'';flex:1;height:1px;background:var(--brd)}
.login-toggle{text-align:center;font-size:10px;color:var(--t3);margin-top:16px}
.login-toggle a{color:var(--ac);cursor:pointer;font-weight:600;text-decoration:none}
.login-toggle a:hover{text-decoration:underline}
.quick-users{display:grid;grid-template-columns:1fr 1fr;gap:6px;margin-top:8px}
.quick-user{background:var(--sf);border:1px solid var(--brd);border-radius:8px;padding:10px;cursor:pointer;display:flex;align-items:center;gap:8px;transition:all .15s}
.quick-user:hover{background:var(--hov);border-color:var(--brd2)}
.quick-user .qu-av{width:32px;height:32px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:700;color:#fff;flex-shrink:0}
.quick-user .qu-name{font-size:10px;font-weight:600}
.quick-user .qu-role{font-size:8px;color:var(--t3)}

/* User menu */
#user-menu{position:absolute;top:100%;right:0;margin-top:4px;width:240px;background:var(--pnl);border:1px solid var(--brd);border-radius:8px;padding:6px;z-index:200;box-shadow:0 12px 40px rgba(0,0,0,.6);display:none}
#user-menu.show{display:block}
.um-header{padding:10px;border-bottom:1px solid var(--brd);margin-bottom:4px;display:flex;align-items:center;gap:8px}
.um-header .av{width:36px;height:36px;font-size:13px}
.um-name{font-weight:700;font-size:11px}
.um-role{font-size:9px;color:var(--t3)}
.um-email{font-size:8px;color:var(--t4)}
.um-item{width:100%;background:transparent;border:none;padding:7px 10px;border-radius:4px;font-size:10px;color:var(--t2);text-align:left;display:flex;align-items:center;gap:8px;font-family:var(--f)}
.um-item:hover{background:var(--sf);color:var(--t1)}
.um-item.danger{color:var(--no)}
.um-item.danger:hover{background:rgba(239,68,68,.1)}

/* Team management modal */
#team-modal{position:fixed;inset:0;z-index:9000;display:none;align-items:center;justify-content:center;background:rgba(0,0,0,.5)}
#team-modal.show{display:flex}
.tm-box{width:560px;max-height:80vh;background:var(--pnl);border:1px solid var(--brd);border-radius:12px;overflow:hidden;display:flex;flex-direction:column}
.tm-head{padding:14px 16px;border-bottom:1px solid var(--brd);display:flex;align-items:center;justify-content:space-between}
.tm-head h3{font-size:13px}
.tm-close{background:0;border:none;color:var(--t3);font-size:16px}
.tm-close:hover{color:var(--t1)}
.tm-body{flex:1;overflow:auto;padding:12px 16px}
.tm-add{display:flex;gap:6px;margin-bottom:12px;padding-bottom:12px;border-bottom:1px solid var(--brd)}
.tm-add input,.tm-add select{background:var(--sf);border:1px solid var(--brd);border-radius:4px;padding:6px 8px;font-size:10px;color:var(--t1);outline:none}
.tm-add input:focus,.tm-add select:focus{border-color:var(--ac)}
.tm-add button{background:var(--ac);border:none;color:#fff;padding:6px 12px;border-radius:4px;font-size:10px;font-weight:700;white-space:nowrap}
.tm-member{display:flex;align-items:center;gap:8px;padding:8px;background:var(--sf);border:1px solid var(--brd);border-radius:6px;margin-bottom:4px}
.tm-member .av{width:30px;height:30px;font-size:10px}
.tm-info{flex:1}
.tm-info .name{font-size:11px;font-weight:600}
.tm-info .meta{font-size:8px;color:var(--t3)}
.tm-actions{display:flex;gap:3px}
.tm-actions select{background:var(--bg);border:1px solid var(--brd);border-radius:3px;padding:2px 3px;font-size:9px;color:var(--t1);outline:none}
.tm-actions button{background:0;border:1px solid var(--brd);border-radius:3px;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:10px;color:var(--t3)}
.tm-actions button:hover{background:rgba(239,68,68,.1);color:var(--no);border-color:rgba(239,68,68,.3)}
.online-dot{width:8px;height:8px;border-radius:50%;flex-shrink:0}
.online-dot.on{background:var(--ok);box-shadow:0 0 6px var(--ok)}
.online-dot.off{background:var(--t4)}

/* ===== FILE MENU ===== */
#file-menu{position:absolute;top:100%;left:0;margin-top:2px;width:260px;background:var(--pnl);border:1px solid var(--brd);border-radius:8px;padding:4px;z-index:300;box-shadow:0 12px 40px rgba(0,0,0,.6);display:none}
#file-menu.show{display:block}
.fm-item{width:100%;background:0;border:none;padding:7px 10px;border-radius:4px;font-size:10px;color:var(--t2);text-align:left;display:flex;align-items:center;gap:10px;font-family:var(--f)}
.fm-item:hover{background:var(--sf);color:var(--t1)}
.fm-item .fmi{width:18px;text-align:center;font-size:13px}
.fm-item .fmk{margin-left:auto;font-size:8px;color:var(--t4);background:var(--bg);padding:1px 4px;border-radius:2px}
.fm-sep{height:1px;background:var(--brd);margin:3px 4px}
.fm-sub{font-size:8px;color:var(--t4);padding:4px 10px;font-weight:600;text-transform:uppercase;letter-spacing:.4px}
.fm-recent{padding:4px 10px 4px 38px;font-size:9px;color:var(--t3);cursor:pointer;border-radius:3px}
.fm-recent:hover{background:var(--sf);color:var(--t1)}
.autosave-dot{width:6px;height:6px;border-radius:50%;display:inline-block;margin-right:4px}
.autosave-dot.on{background:var(--ok);box-shadow:0 0 4px var(--ok)}
.autosave-dot.off{background:var(--t4)}

/* ===== VIDEO CHAT ===== */
#vc-window{position:fixed;bottom:12px;right:320px;width:340px;background:var(--pnl);border:1px solid var(--brd);border-radius:12px;box-shadow:0 12px 40px rgba(0,0,0,.5);z-index:400;display:none;flex-direction:column;overflow:hidden}
#vc-window.show{display:flex}
#vc-window.mini{width:180px;height:140px}
#vc-window.mini #vc-body,#vc-window.mini #vc-controls{display:none}
#vc-window.mini #vc-mini-preview{display:block}
#vc-head{padding:8px 12px;background:var(--pnl2);border-bottom:1px solid var(--brd);display:flex;align-items:center;gap:6px;cursor:move}
#vc-head .vc-title{font-size:10px;font-weight:700;flex:1}
.vc-hbtn{width:22px;height:22px;border-radius:4px;border:none;background:0;color:var(--t3);font-size:12px;display:flex;align-items:center;justify-content:center}
.vc-hbtn:hover{background:var(--sf);color:var(--t1)}
#vc-body{display:grid;grid-template-columns:1fr 1fr;gap:3px;padding:3px;background:#000;max-height:280px}
.vc-feed{position:relative;background:#111;border-radius:4px;overflow:hidden;aspect-ratio:4/3;min-height:80px}
.vc-feed video{width:100%;height:100%;object-fit:cover}
.vc-feed canvas{width:100%;height:100%;object-fit:cover}
.vc-feed-label{position:absolute;bottom:4px;left:4px;background:rgba(0,0,0,.7);color:#fff;padding:1px 6px;border-radius:3px;font-size:8px;font-weight:600}
.vc-feed-muted{position:absolute;top:4px;right:4px;background:rgba(239,68,68,.8);color:#fff;padding:1px 4px;border-radius:2px;font-size:7px}
.vc-avatar-placeholder{width:100%;height:100%;display:flex;align-items:center;justify-content:center;background:linear-gradient(135deg,#1a2744,#0f1729)}
.vc-avatar-placeholder .av{width:40px;height:40px;font-size:14px}
#vc-controls{display:flex;align-items:center;justify-content:center;gap:6px;padding:8px;border-top:1px solid var(--brd)}
.vc-btn{width:36px;height:36px;border-radius:50%;border:none;font-size:14px;display:flex;align-items:center;justify-content:center;transition:all .15s}
.vc-btn.on{background:var(--sf);color:var(--t1)}
.vc-btn.off{background:rgba(239,68,68,.2);color:var(--no)}
.vc-btn.end{background:var(--no);color:#fff;width:44px;border-radius:22px}
.vc-btn:hover{filter:brightness(1.2)}
#vc-mini-preview{display:none;width:100%;aspect-ratio:16/9;background:#000;border-radius:0 0 12px 12px}
#vc-mini-preview video,#vc-mini-preview canvas{width:100%;height:100%;object-fit:cover;border-radius:0 0 12px 12px}
#vc-chat{max-height:120px;overflow-y:auto;padding:6px 8px;border-top:1px solid var(--brd);font-size:9px}
.vc-msg{margin-bottom:4px}
.vc-msg b{color:var(--ac)}
.vc-msg span{color:var(--t2)}
#vc-chat-input{display:flex;gap:3px;padding:4px 6px;border-top:1px solid var(--brd)}
#vc-chat-input input{flex:1;background:var(--bg);border:1px solid var(--brd);border-radius:3px;padding:4px 6px;font-size:9px;color:var(--t1);outline:none;font-family:var(--f)}
#vc-chat-input button{background:var(--ac);border:none;color:#fff;padding:4px 8px;border-radius:3px;font-size:9px;font-weight:600}

/* VC invite bar in topbar */
.vc-invite{position:fixed;top:74px;right:12px;background:var(--pnl);border:1px solid var(--brd);border-radius:8px;padding:8px 12px;z-index:350;box-shadow:0 4px 20px rgba(0,0,0,.4);display:none;align-items:center;gap:8px;font-size:10px}
.vc-invite.show{display:flex}

/* ===== THEME TOGGLE ===== */

/* ===== MAIN VIEW OVERLAYS ===== */
#view-overlay{position:absolute;inset:0;z-index:18;background:var(--bg);overflow-y:auto;display:none;padding:24px 32px}
#view-overlay.show{display:block}
.vo-header{margin-bottom:20px}
.vo-header h2{font-size:16px;font-weight:700;margin-bottom:4px}
.vo-header p{font-size:10px;color:var(--t2)}
.vo-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(280px,1fr));gap:10px;margin-bottom:20px}
.vo-card{background:var(--pnl);border:1px solid var(--brd);border-radius:8px;padding:14px;cursor:pointer;transition:all .15s}
.vo-card:hover{background:var(--hov);border-color:var(--brd2)}
.vo-card h3{font-size:12px;font-weight:700;margin-bottom:4px}
.vo-card .vo-sub{font-size:9px;color:var(--t3);margin-bottom:8px}
.vo-row{display:flex;justify-content:space-between;font-size:9px;padding:2px 0}
.vo-row .vk{color:var(--t3)}.vo-row .vv{font-weight:600}
.vo-progress{height:4px;background:var(--sf);border-radius:2px;overflow:hidden;margin-top:8px}
.vo-progress-bar{height:100%;border-radius:2px}
.vo-stat{text-align:center;padding:12px}
.vo-stat .num{font-size:28px;font-weight:700}
.vo-stat .lbl{font-size:9px;color:var(--t3);margin-top:2px}
.vo-section{font-size:11px;font-weight:700;margin:16px 0 8px;padding-bottom:6px;border-bottom:1px solid var(--brd)}
.vo-team-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(200px,1fr));gap:8px}
.vo-team-card{background:var(--pnl);border:1px solid var(--brd);border-radius:8px;padding:12px;display:flex;align-items:center;gap:10px}
.vo-team-card .av{width:36px;height:36px;font-size:13px}
.vo-gb-panel{max-width:700px;margin:0 auto}
.vo-gb-card{background:var(--pnl);border:1px solid var(--brd);border-radius:8px;padding:14px;margin-bottom:10px}
.vo-gb-card h4{font-size:11px;font-weight:700;margin-bottom:8px}
.vo-timeline{border-left:2px solid var(--brd);margin-left:10px;padding-left:16px}
.vo-timeline-item{position:relative;padding:6px 0 14px}
.vo-timeline-item::before{content:'';position:absolute;left:-21px;top:8px;width:10px;height:10px;border-radius:50%;background:var(--brd)}
.vo-timeline-item.done::before{background:var(--ok)}
.vo-timeline-item.active::before{background:var(--ac);box-shadow:0 0 6px var(--ac)}
.vo-timeline-item .vo-tl-title{font-size:11px;font-weight:600}
.vo-timeline-item .vo-tl-sub{font-size:9px;color:var(--t3)}
</style>
</head>
<body>
<div id="toast"></div>
<div id="mtip"></div>
<div id="cpick"></div>
<input type="file" id="fi" accept=".pdf" style="display:none">

<!-- ===== LOGIN SCREEN ===== -->
<div id="login-overlay">
  <div class="login-bg">
    <div class="orb" style="width:400px;height:400px;background:var(--ac);top:-100px;left:-100px"></div>
    <div class="orb" style="width:500px;height:500px;background:var(--gb);bottom:-150px;right:-100px"></div>
    <div class="orb" style="width:300px;height:300px;background:var(--pu);top:50%;left:50%;transform:translate(-50%,-50%)"></div>
  </div>
  <!-- Theme toggle on login screen -->
  <div style="position:absolute;top:16px;right:16px;display:flex;align-items:center;gap:6px;z-index:2">
    <span style="font-size:9px;color:var(--t3)">🌙</span>
    <div class="theme-toggle" onclick="toggleTheme()"></div>
    <span style="font-size:9px;color:var(--t3)">☀️</span>
  </div>
  <div class="login-box">
    <div class="logo-big"><i>PR</i><b>PLANREVIEW PRO</b><span class="gbb" style="font-size:9px">+GovBuilt</span></div>

    <!-- Login form -->
    <div id="login-form">
      <h2>Welcome Back</h2>
      <div class="sub">Sign in to continue to your plan reviews</div>
      <div class="lfield"><label>Email</label><input type="email" id="login-email" placeholder="you@agency.gov"></div>
      <div class="lfield"><label>Password</label><input type="password" id="login-pass" placeholder="••••••••"></div>
      <button class="login-btn primary" onclick="doLogin()">Sign In</button>
      <div class="login-divider">or quick-login as a team member</div>
      <div class="quick-users" id="quick-users"></div>
      <div class="login-toggle">New to PlanReview? <a onclick="showRegister()">Create Account</a></div>
      <div style="display:flex;align-items:center;justify-content:center;gap:10px;margin-top:14px;padding-top:14px;border-top:1px solid var(--brd)">
        <span style="font-size:9px;color:var(--t3)">Theme:</span>
        <button style="background:var(--sf);border:1px solid var(--brd);border-radius:6px;padding:5px 12px;font-size:10px;color:var(--t2);display:flex;align-items:center;gap:4px;cursor:pointer;font-family:var(--f)" onclick="applyTheme('dark')" id="login-theme-dark">🌙 Dark</button>
        <button style="background:var(--sf);border:1px solid var(--brd);border-radius:6px;padding:5px 12px;font-size:10px;color:var(--t2);display:flex;align-items:center;gap:4px;cursor:pointer;font-family:var(--f)" onclick="applyTheme('light')" id="login-theme-light">☀️ Light</button>
      </div>
    </div>

    <!-- Register form -->
    <div id="register-form" style="display:none">
      <h2>Create Account</h2>
      <div class="sub">Set up your reviewer profile</div>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px">
        <div class="lfield"><label>First Name</label><input id="reg-first" placeholder="Jane"></div>
        <div class="lfield"><label>Last Name</label><input id="reg-last" placeholder="Doe"></div>
      </div>
      <div class="lfield"><label>Email</label><input type="email" id="reg-email" placeholder="you@agency.gov"></div>
      <div class="lfield"><label>Password</label><input type="password" id="reg-pass" placeholder="Min 6 characters"></div>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px">
        <div class="lfield"><label>Role / Title</label>
          <select id="reg-role"><option value="">Select Role...</option><option>Plan Reviewer</option><option>Structural Engineer</option><option>Fire Marshal</option><option>MEP Reviewer</option><option>Electrical Inspector</option><option>Plumbing Inspector</option><option>Civil Engineer</option><option>Zoning Officer</option><option>Building Official</option><option>Project Manager</option><option>Architect</option><option>Contractor</option><option>Admin</option></select>
        </div>
        <div class="lfield"><label>Discipline</label>
          <select id="reg-disc"><option value="">Select...</option><option value="arch">Architectural</option><option value="struct">Structural</option><option value="mech">Mechanical</option><option value="elec">Electrical</option><option value="plumb">Plumbing</option><option value="fire">Fire</option><option value="civil">Civil</option><option value="zone">Zoning</option></select>
        </div>
      </div>
      <div class="lfield"><label>Organization</label><input id="reg-org" placeholder="Stokes County Building Dept"></div>
      <button class="login-btn primary" onclick="doRegister()">Create Account & Sign In</button>
      <div class="login-toggle">Already have an account? <a onclick="showLogin()">Sign In</a></div>
    </div>
  </div>
</div>

<!-- ===== TEAM MANAGEMENT MODAL ===== -->
<div id="team-modal">
  <div class="tm-box">
    <div class="tm-head"><h3>👥 Manage Review Team</h3><button class="tm-close" onclick="closeTeamModal()">✕</button></div>
    <div class="tm-body" id="tm-body"></div>
  </div>
</div>

<!-- ===== VIDEO CHAT WINDOW ===== -->
<div id="vc-window">
  <div id="vc-head">
    <span style="font-size:12px">📹</span>
    <span class="vc-title">Plan Review Session</span>
    <span style="font-size:8px;color:var(--ok)" id="vc-status">● Live</span>
    <button class="vc-hbtn" onclick="toggleVCMini()" title="Minimize">—</button>
    <button class="vc-hbtn" onclick="toggleVideoChat()" title="Close">✕</button>
  </div>
  <div id="vc-body">
    <div class="vc-feed" id="vc-local-feed">
      <video id="vc-local-video" autoplay muted playsinline></video>
      <span class="vc-feed-label" id="vc-local-label">You</span>
    </div>
    <div class="vc-feed" id="vc-remote-1">
      <div class="vc-avatar-placeholder"><div class="av" style="background:#ef4444">SC</div></div>
      <canvas id="vc-sim-1" style="display:none"></canvas>
      <span class="vc-feed-label">Sarah C.</span>
    </div>
    <div class="vc-feed" id="vc-remote-2">
      <div class="vc-avatar-placeholder"><div class="av" style="background:#f97316">MT</div></div>
      <canvas id="vc-sim-2" style="display:none"></canvas>
      <span class="vc-feed-label">Mike T.</span>
    </div>
    <div class="vc-feed" id="vc-remote-3">
      <div class="vc-avatar-placeholder"><div class="av" style="background:#06b6d4">CP</div></div>
      <canvas id="vc-sim-3" style="display:none"></canvas>
      <span class="vc-feed-label">Chris P.</span>
      <span class="vc-feed-muted">🔇</span>
    </div>
  </div>
  <div id="vc-controls">
    <button class="vc-btn on" id="vc-mic" onclick="toggleVCMic()" title="Microphone">🎤</button>
    <button class="vc-btn on" id="vc-cam" onclick="toggleVCCam()" title="Camera">📷</button>
    <button class="vc-btn on" id="vc-screen" onclick="toggleVCScreen()" title="Share Screen">🖥</button>
    <button class="vc-btn on" id="vc-markup" onclick="toggleVCMarkup()" title="Share Markup View">✏️</button>
    <button class="vc-btn end" onclick="endVideoCall()" title="End Call">📞</button>
  </div>
  <div id="vc-chat">
    <div class="vc-msg"><b>Sarah C.</b> <span>Can you zoom into grid B-4?</span></div>
    <div class="vc-msg"><b>Mike T.</b> <span>Looking at the corridor width now</span></div>
  </div>
  <div id="vc-chat-input">
    <input placeholder="Type a message..." id="vc-chat-text" onkeydown="if(event.key==='Enter')sendVCChat()">
    <button onclick="sendVCChat()">Send</button>
  </div>
  <div id="vc-mini-preview"></div>
</div>

<!-- Hidden inputs for file operations -->
<input type="file" id="fi-multi" accept=".pdf" style="display:none" multiple>
<input type="file" id="fi-json" accept=".json" style="display:none">

<!-- TOPBAR -->
<div id="top" style="display:none">
  <div class="logo"><i>PR</i><b>PLANREVIEW PRO</b><span class="gbb">+GovBuilt</span></div>
  <!-- File Menu -->
  <div style="position:relative">
    <button class="tb" id="file-toggle" onclick="document.getElementById('file-menu').classList.toggle('show')">📁 File ▾</button>
    <div id="file-menu">
      <button class="fm-item" onclick="openFile();closeFileMenu()"><span class="fmi">📂</span>Open PDF<span class="fmk">Ctrl+O</span></button>
      <button class="fm-item" onclick="openMulti();closeFileMenu()"><span class="fmi">📑</span>Open Multiple PDFs</button>
      <div class="fm-sep"></div>
      <button class="fm-item" onclick="saveProject();closeFileMenu()"><span class="fmi">💾</span>Save Project<span class="fmk">Ctrl+S</span></button>
      <button class="fm-item" onclick="saveProjectAs();closeFileMenu()"><span class="fmi">📝</span>Save Project As...</button>
      <button class="fm-item" onclick="saveToComputer();closeFileMenu()"><span class="fmi">💻</span>Save to Computer<span class="fmk">Ctrl+Shift+S</span></button>
      <div class="fm-sep"></div>
      <button class="fm-item" onclick="exportPDF();closeFileMenu()"><span class="fmi">📥</span>Export Annotated PDF<span class="fmk">Ctrl+E</span></button>
      <button class="fm-item" onclick="exportFlat();closeFileMenu()"><span class="fmi">📄</span>Export Flattened PDF</button>
      <button class="fm-item" onclick="exportMarkupsJSON();closeFileMenu()"><span class="fmi">📋</span>Export Markups (JSON)</button>
      <button class="fm-item" onclick="importMarkupsJSON();closeFileMenu()"><span class="fmi">📎</span>Import Markups (JSON)</button>
      <div class="fm-sep"></div>
      <button class="fm-item" onclick="exportSummaryCSV();closeFileMenu()"><span class="fmi">📊</span>Export Review Summary (CSV)</button>
      <button class="fm-item" onclick="printSheet();closeFileMenu()"><span class="fmi">🖨</span>Print Current Sheet<span class="fmk">Ctrl+P</span></button>
      <div class="fm-sep"></div>
      <div class="fm-sub">Recent Files</div>
      <div id="recent-files"></div>
      <div class="fm-sep"></div>
      <button class="fm-item" style="justify-content:space-between"><span style="display:flex;align-items:center;gap:10px"><span class="fmi">⏱</span>Auto-save</span><span><span class="autosave-dot on" id="autosave-dot"></span><span style="font-size:8px;color:var(--t3)" id="autosave-label">On</span></span></button>
    </div>
  </div>
  <div class="ntabs" id="ntabs">
    <button class="nt on" data-v="review">Plan Review</button>
    <button class="nt" data-v="projects">Projects</button>
    <button class="nt" data-v="team">Team</button>
    <button class="nt" data-v="govbuilt">GovBuilt</button>
  </div>
  <div class="sp"></div>
  <!-- Autosave indicator -->
  <div style="display:flex;align-items:center;gap:4px;font-size:8px;color:var(--t3)" id="save-status"><span class="autosave-dot on"></span> Saved</div>
  <!-- Theme toggle -->
  <div style="display:flex;align-items:center;gap:4px">
    <span style="font-size:10px" id="theme-icon-label">🌙</span>
    <div class="theme-toggle" id="theme-toggle" onclick="toggleTheme()" title="Toggle light/dark mode">
      <span class="theme-icon moon">🌙</span>
      <span class="theme-icon sun">☀️</span>
    </div>
  </div>
  <button class="tb" onclick="openFile()">📂 Open</button>
  <button class="tb" onclick="saveToComputer()">💾 Save</button>
  <button class="tb" onclick="exportPDF()">📥 Export</button>
  <!-- Video chat -->
  <button class="tb" onclick="toggleVideoChat()" id="vc-toggle" style="position:relative">📹 Video<span id="vc-active-dot" style="display:none;position:absolute;top:2px;right:2px;width:6px;height:6px;border-radius:50%;background:var(--ok);box-shadow:0 0 4px var(--ok)"></span></button>
  <div style="position:relative">
    <button class="tb" id="ptog"><span style="color:var(--t3)" id="pid">P-2026-0142</span>&nbsp;<b id="pnm">Riverside Mixed-Use</b>&nbsp;<span style="color:var(--t3)">▾</span></button>
    <div class="dd" id="pdd"></div>
  </div>
  <button class="tb pri" onclick="toast('Review submitted to GovBuilt','ok')">Submit Review ➜</button>
  <div style="position:relative">
    <button style="background:0;border:none;display:flex;align-items:center;gap:6px;cursor:pointer;padding:2px 4px;border-radius:6px" id="user-toggle" onclick="document.getElementById('user-menu').classList.toggle('show')">
      <div class="av" id="topbar-av">JD</div>
      <div style="text-align:left"><div style="font-size:10px;font-weight:600;color:var(--t1)" id="topbar-name">Jane Doe</div><div style="font-size:8px;color:var(--t3)" id="topbar-role">Plan Reviewer</div></div>
      <span style="color:var(--t3);font-size:9px">▾</span>
    </button>
    <div id="user-menu">
      <div class="um-header">
        <div class="av" id="um-av" style="width:36px;height:36px;font-size:13px">JD</div>
        <div>
          <div class="um-name" id="um-name">Jane Doe</div>
          <div class="um-role" id="um-role">Plan Reviewer</div>
          <div class="um-email" id="um-email">jane@agency.gov</div>
        </div>
      </div>
      <button class="um-item" onclick="openTeamModal()">👥 Manage Team</button>
      <button class="um-item" onclick="showProfileEdit()">⚙ Edit Profile</button>
      <button class="um-item" onclick="document.getElementById('user-menu').classList.remove('show');toggleTheme()">🎨 Toggle Theme</button>
      <button class="um-item" onclick="toast('Keyboard shortcuts','info')">⌨ Shortcuts</button>
      <div style="height:1px;background:var(--brd);margin:4px 0"></div>
      <button class="um-item" onclick="switchUser()">🔄 Switch User</button>
      <button class="um-item danger" onclick="doLogout()">🚪 Sign Out</button>
    </div>
  </div>
</div>

<!-- PROPBAR -->
<div id="propbar">
  <div class="pg"><span class="pl">Color</span><div class="pc" id="pcStroke" style="background:#ef4444" onclick="showCP(this,'stroke')"></div></div>
  <div class="pg"><span class="pl">Fill</span><div class="pc" id="pcFill" style="background:transparent" onclick="showCP(this,'fill')"></div></div>
  <div class="pg"><span class="pl">Width</span><select class="ps" id="ppW" onchange="S.lineWidth=+this.value"><option value="1">1</option><option value="2" selected>2</option><option value="3">3</option><option value="4">4</option><option value="6">6</option><option value="8">8</option><option value="12">12</option></select></div>
  <div class="pg"><span class="pl">Style</span><select class="ps" id="ppSt" onchange="S.lineStyle=this.value"><option>solid</option><option>dashed</option><option>dotted</option></select></div>
  <div class="pg"><span class="pl">Opacity</span><input type="range" min="10" max="100" value="100" style="width:50px;height:12px" oninput="S.opacity=+this.value/100;document.getElementById('opv').textContent=this.value+'%'" id="ppO"><span id="opv" style="font-size:8px;color:var(--t2);width:25px">100%</span></div>
  <div class="pg"><span class="pl">Font</span><select class="ps" id="ppF" onchange="S.fontSize=+this.value" style="width:38px"><option>10</option><option selected>12</option><option>14</option><option>16</option><option>20</option><option>24</option><option>32</option><option>48</option></select>
  <button class="pb" onclick="this.classList.toggle('on');S.fontBold=this.classList.contains('on')"><b>B</b></button>
  <button class="pb" onclick="this.classList.toggle('on');S.fontItalic=this.classList.contains('on')"><i style="font-style:italic">I</i></button></div>
  <div class="pg"><span class="pl">Snap</span><button class="pb on" id="ppSnap" onclick="this.classList.toggle('on');S.snap=this.classList.contains('on')">⊞</button><button class="pb" onclick="this.classList.toggle('on');S.ortho=this.classList.contains('on')">⊥</button></div>
  <div class="pg"><span class="pl">Layer</span><select class="ps" id="ppL" style="width:62px"><option value="markup">Markups</option><option value="review">Review</option><option value="punch">Punch</option></select></div>
  <div class="pg"><span class="pl">Zoom</span><input class="pi" id="zoomInput" type="number" min="1" max="6400" value="100" style="width:48px" onchange="setZoom(+this.value/100)"><span style="font-size:8px;color:var(--t3)">%</span></div>
</div>

<!-- MAIN -->
<div id="main">
<!-- LEFT TOOLS -->
<div id="lt"></div>
<div class="fly" id="flyShapes"><div class="fly-t">Shapes</div></div>
<div class="fly" id="flyMeasure"><div class="fly-t">Measurement Tools</div></div>
<div class="fly" id="flyStamps"><div class="fly-t">Stamps</div></div>
<div class="fly" id="flyText"><div class="fly-t">Text & Annotations</div></div>

<!-- VIEWER -->
<div id="vw">
<div id="stabs"></div>
<div id="ca">
  <div id="view-overlay"></div>
  <div id="rc" title="Toggle units" onclick="cycleUnit()">ft</div>
  <div id="rh"><canvas class="rcv" id="rhc"></canvas></div>
  <div id="rv"><canvas class="rcv" id="rvc"></canvas></div>
  <div id="xh"></div><div id="xv"></div>
  <div id="upl">
    <div class="uz" id="uz">
      <div style="font-size:48px;margin-bottom:6px">📐</div>
      <h2>Upload Plan Sheets</h2>
      <p>Drag &amp; drop PDF files here or click to browse.<br>Multi-page PDFs — each page becomes a sheet.<br>Supports all architectural, structural, MEP, civil plan types.</p>
      <button class="ub" onclick="event.stopPropagation();openFile()">Choose PDF Files</button>
      <div class="uo">— or —</div>
      <button class="ud" onclick="event.stopPropagation();loadDemo()">Load Demo Floor Plan</button>
    </div>
  </div>
  <div id="ps" style="display:none">
    <div id="pw"><canvas id="pc"></canvas><canvas id="mc"></canvas></div>
  </div>
  <div id="sbar">
    <div class="sb-head"><span style="font-size:14px">📐</span> Set Drawing Scale</div>
    <div id="sb-current-wrap"></div>
    <div class="sb-tabs">
      <button class="sb-tab on" data-st="presets" onclick="setSBTab('presets')">Presets</button>
      <button class="sb-tab" data-st="custom" onclick="setSBTab('custom')">Custom</button>
      <button class="sb-tab" data-st="calibrate" onclick="setSBTab('calibrate')">Calibrate</button>
    </div>
    <div class="sb-body" id="sb-body"></div>
    <div style="padding:8px 12px;border-top:1px solid var(--brd);display:flex;justify-content:flex-end;gap:6px">
      <button class="sb-btn sec" onclick="cancelCal()">Cancel</button>
      <button class="sb-btn pri" onclick="clearScale()">Clear Scale</button>
    </div>
  </div>
  <div id="pn"><button onclick="prevPg()">◀</button><span id="plbl">1/1</span><button onclick="nextPg()">▶</button></div>
  <div id="coords">X: 0 Y: 0</div>
  <div class="cb l">
    <button class="cn" onclick="zOut()">−</button>
    <span class="zt" id="zlbl">100%</span>
    <button class="cn" onclick="zIn()">+</button>
    <button class="cn" style="font-size:9px" onclick="zFit()">FIT</button>
    <button class="cn" style="font-size:9px" onclick="setZoom(1)">1:1</button>
    <button class="cn" style="font-size:9px" onclick="setZoom(2)">2×</button>
    <button class="cn" style="font-size:9px" onclick="setZoom(4)">4×</button>
    <button class="cn" style="font-size:9px" onclick="setZoom(8)">8×</button>
  </div>
  <div class="cb r">
    <button class="tg on" id="tRul" onclick="togRuler()">📐</button>
    <button class="tg on" id="tCom" onclick="togComm()">💬</button>
    <button class="tg on" id="tMrk" onclick="togMark()">✏️</button>
    <button class="tg" id="tGrd" onclick="togGrid()">▦</button>
    <button class="tg" id="tXh" onclick="togCross()">+</button>
  </div>
</div>
</div>

<!-- RIGHT PANEL -->
<div id="rp">
<div id="rt">
  <button class="rtb on" data-p="sheets" title="Sheets">📋</button>
  <button class="rtb" data-p="comments" title="Comments">💬</button>
  <button class="rtb" data-p="markups" title="Markups">✏️</button>
  <button class="rtb" data-p="punch" title="Punch">📌</button>
  <button class="rtb" data-p="team" title="Team">👥</button>
  <button class="rtb" data-p="layers" title="Layers">◉</button>
  <button class="rtb" data-p="meas" title="Measurements">📏</button>
  <button class="rtb" data-p="gb" title="GovBuilt">🔗</button>
</div>
<div id="rcon"></div>
</div>
</div>

<script>
pdfjsLib.GlobalWorkerOptions.workerSrc='https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.worker.min.js';

/* ===== DATA ===== */
const STAMPS=[{id:"approved",l:"APPROVED",c:"#10b981",i:"✓"},{id:"rejected",l:"REJECTED",c:"#ef4444",i:"✗"},{id:"revise",l:"REVISE & RESUBMIT",c:"#f59e0b",i:"⟲"},{id:"reviewed",l:"REVIEWED",c:"#3b82f6",i:"◉"},{id:"hold",l:"ON HOLD",c:"#a855f7",i:"⏸"},{id:"info",l:"INFO NEEDED",c:"#f97316",i:"?"},{id:"nfa",l:"NO FURTHER ACTION",c:"#06b6d4",i:"—"},{id:"prelim",l:"PRELIMINARY",c:"#64748b",i:"△"}];
const DISC=[{id:"arch",l:"Architectural",c:"#3b82f6",a:"ARCH"},{id:"struct",l:"Structural",c:"#ef4444",a:"STRCT"},{id:"mech",l:"Mechanical",c:"#f59e0b",a:"MECH"},{id:"elec",l:"Electrical",c:"#a855f7",a:"ELEC"},{id:"plumb",l:"Plumbing",c:"#10b981",a:"PLMB"},{id:"fire",l:"Fire",c:"#f97316",a:"FIRE"},{id:"civil",l:"Civil",c:"#06b6d4",a:"CIVIL"},{id:"zone",l:"Zoning",c:"#ec4899",a:"ZONE"}];
const PROJ=[{id:"P-2026-0142",n:"Riverside Mixed-Use",ad:"1250 River Rd, Danbury, NC",ty:"Commercial",st:"In Review",gb:"GB-28169-0142",sub:"2026-02-18",due:"2026-03-20",ap:"Meridian Dev Group",cn:"Summit Construction",sh:42,cy:2,pr:68},{id:"P-2026-0156",n:"Oak Valley Elementary",ad:"445 School Ln",ty:"Institutional",st:"In Review",gb:"GB-28169-0156",sub:"2026-02-25",due:"2026-03-27",ap:"Stokes County Schools",cn:"Piedmont Builders",sh:28,cy:1,pr:35},{id:"P-2026-0138",n:"Danbury Fire Station #3",ad:"820 Main St",ty:"Municipal",st:"Corrections",gb:"GB-28169-0138",sub:"2026-02-10",due:"2026-03-12",ap:"Town of Danbury",cn:"Blue Ridge Construction",sh:35,cy:3,pr:82}];
const SHT=[{id:"A1.01",n:"Site Plan",d:"civil",s:"approved",c:3},{id:"A1.02",n:"Floor Plan - L1",d:"arch",s:"comments",c:7},{id:"A1.03",n:"Floor Plan - L2",d:"arch",s:"pending",c:0},{id:"A2.01",n:"Elevations N/S",d:"arch",s:"comments",c:4},{id:"A2.02",n:"Elevations E/W",d:"arch",s:"pending",c:0},{id:"A3.01",n:"Sections",d:"arch",s:"approved",c:1},{id:"S1.01",n:"Foundation",d:"struct",s:"rejected",c:5},{id:"S1.02",n:"Framing",d:"struct",s:"pending",c:0},{id:"M1.01",n:"HVAC Plan",d:"mech",s:"pending",c:0},{id:"E1.01",n:"Electrical",d:"elec",s:"comments",c:2},{id:"P1.01",n:"Plumbing",d:"plumb",s:"pending",c:0},{id:"FP1.01",n:"Fire Protection",d:"fire",s:"pending",c:0}];
const CMT=[{id:1,u:"Sarah Chen",r:"Structural Eng.",av:"SC",t:'Foundation B-4: revise footing to min 12" below grade per NC 1809.4.',px:.42,py:.31,tm:"2h ago",res:false,d:"struct",re:[{u:"James Park",a:"JP",t:"Will update next rev.",tm:"1h ago"}]},{id:2,u:"Mike Torres",r:"Fire Marshal",av:"MT",t:'Corridor C egress 36" — need 44" per IBC 1005.1.',px:.65,py:.21,tm:"4h ago",res:false,d:"fire",re:[]},{id:3,u:"Lisa Wang",r:"MEP Reviewer",av:"LW",t:"HVAC clearances conflict w/ structural. Verify specs.",px:.22,py:.47,tm:"1d ago",res:true,d:"mech",re:[{u:"Tom Bradley",a:"TB",t:"Updated Rev 2.",tm:"6h ago"},{u:"Lisa Wang",a:"LW",t:"Resolved.",tm:"3h ago"}]}];
const TEAM=[{n:"Sarah Chen",r:"Structural",a:"SC",s:"reviewing",d:"struct"},{n:"Mike Torres",r:"Fire Marshal",a:"MT",s:"reviewing",d:"fire"},{n:"Lisa Wang",r:"MEP",a:"LW",s:"complete",d:"mech"},{n:"David Kim",r:"Electrical",a:"DK",s:"not_started",d:"elec"},{n:"Anna Roberts",r:"Zoning",a:"AR",s:"complete",d:"zone"},{n:"Chris Patel",r:"Civil",a:"CP",s:"reviewing",d:"civil"}];
const TOOLS=[
  {id:"select",i:"↖",l:"Select",k:"V"},{id:"pan",i:"✋",l:"Pan",k:"H"},{sep:1},
  {id:"pen",i:"✎",l:"Freehand",k:"P"},{id:"highlighter",i:"🖍",l:"Highlighter",k:""},{id:"line",i:"╱",l:"Line",k:"L",fly:"shapes"},{id:"polyline",i:"⟋",l:"Polyline",k:"",fly:"shapes"},{id:"rect",i:"▭",l:"Rectangle",k:"R",fly:"shapes"},{id:"polygon",i:"⬠",l:"Polygon",k:"",fly:"shapes"},{id:"circle",i:"◯",l:"Ellipse",k:"E",fly:"shapes"},{id:"arc",i:"◠",l:"Arc",k:"",fly:"shapes"},{id:"arrow",i:"➤",l:"Arrow",k:"A"},{id:"cloud",i:"☁",l:"Rev Cloud",k:"D"},{id:"crossout",i:"✕",l:"Cross-out",k:""},{sep:1},
  {id:"text",i:"T",l:"Text Box",k:"T",fly:"text"},{id:"callout",i:"💬",l:"Callout",k:"C",fly:"text"},{id:"note",i:"📝",l:"Sticky Note",k:"",fly:"text"},{id:"typewriter",i:"⌨",l:"Typewriter",k:"",fly:"text"},{sep:1},
  {id:"stamp",i:"⊕",l:"Stamp",k:"S",fly:"stamps"},{id:"image",i:"🖼",l:"Image",k:""},{id:"link",i:"🔗",l:"Hyperlink",k:""},{sep:1},
  {id:"measure",i:"📏",l:"Distance",k:"M",fly:"measure"},{id:"area",i:"⬡",l:"Area",k:"Q",fly:"measure"},{id:"perimeter",i:"◻",l:"Perimeter",k:"",fly:"measure"},{id:"angle",i:"∠",l:"Angle",k:"",fly:"measure"},{id:"radius",i:"◔",l:"Radius",k:"",fly:"measure"},{id:"count",i:"#",l:"Count",k:"",fly:"measure"},{id:"calibrate",i:"⚙",l:"Set Scale",k:"K"},{sep:1},
  {id:"snapshot",i:"📷",l:"Snapshot",k:"N"},{id:"compare",i:"⊞",l:"Overlay",k:"O"},{id:"punch",i:"📌",l:"Punch",k:""},{sep:1},
  {id:"erase",i:"⌫",l:"Eraser",k:"X"},{id:"undo",i:"↩",l:"Undo",k:"Z"},{id:"redo",i:"↪",l:"Redo",k:"Y"}
];
const COLORS=["#ef4444","#f97316","#f59e0b","#eab308","#84cc16","#22c55e","#10b981","#14b8a6","#06b6d4","#0ea5e9","#3b82f6","#6366f1","#8b5cf6","#a855f7","#d946ef","#ec4899","#f43f5e","#000000","#1e293b","#374151","#6b7280","#9ca3af","#d1d5db","#f1f5f9","#ffffff","transparent"];

/* ===== STATE ===== */
let S={proj:PROJ[0],tool:"select",rpanel:"sheets",zoom:1,showComm:true,showMark:true,showRuler:true,showGrid:false,showCross:false,selDiscs:DISC.map(d=>d.id),stroke:"#ef4444",fill:null,lineWidth:2,lineStyle:"solid",opacity:1,fontSize:12,fontBold:false,fontItalic:false,snap:true,ortho:false,stampId:"approved",layer:"markup",gbTab:"status",expCmt:null,
  pdf:null,pg:1,totPg:0,pgW:1200,pgH:900,loaded:false,isDemo:false,pdfBuf:null,
  scale:null,sUnit:"ft",caling:false,calPt1:null,calPt2:null,
  anns:{},meas:{},punches:[],undoStack:[],redoStack:[],
  drawing:false,drawPts:[],curPt:null,selSheet:SHT[1],
  panActive:false,panStart:null,scrollStart:null
};

function getAnns(p){if(!S.anns[p])S.anns[p]=[];return S.anns[p]}
function getMeas(p){if(!S.meas[p])S.meas[p]=[];return S.meas[p]}

/* ===== TOAST ===== */
function toast(m,t="info"){const e=document.getElementById("toast");e.textContent=m;e.className=t+" show";setTimeout(()=>e.classList.remove("show"),3000)}

/* ===== PDF LOADING ===== */
function openFile(){document.getElementById("fi").click()}
document.getElementById("fi").addEventListener("change",async e=>{const f=e.target.files[0];if(!f)return;S.pdfBuf=await f.arrayBuffer();await loadPDF(S.pdfBuf,f.name)});
const uz=document.getElementById("uz");
uz.addEventListener("click",()=>openFile());
uz.addEventListener("dragover",e=>{e.preventDefault();uz.classList.add("over")});
uz.addEventListener("dragleave",()=>uz.classList.remove("over"));
uz.addEventListener("drop",async e=>{e.preventDefault();uz.classList.remove("over");const f=e.dataTransfer.files[0];if(f&&f.type==="application/pdf"){S.pdfBuf=await f.arrayBuffer();await loadPDF(S.pdfBuf,f.name)}else toast("Drop a PDF file","err")});

async function loadPDF(buf,name){
  try{
    toast("Loading...","info");
    const pdf=await pdfjsLib.getDocument({data:buf}).promise;
    S.pdf=pdf;S.totPg=pdf.numPages;S.pg=1;S.loaded=true;S.isDemo=false;
    document.getElementById("upl").classList.add("gone");
    document.getElementById("ps").style.display="block";
    document.getElementById("pn").classList.toggle("show",S.totPg>1);
    await renderPage(1);
    toast(`${name} — ${S.totPg} pages`,"ok");
    addRecent(name);
  }catch(e){toast("PDF Error: "+e.message,"err")}
}

async function renderPage(n){
  const page=await S.pdf.getPage(n);
  // Render at 3x for deep zoom quality
  const vp=page.getViewport({scale:3});
  const cv=document.getElementById("pc"),ctx=cv.getContext("2d");
  cv.width=vp.width;cv.height=vp.height;
  S.pgW=vp.width;S.pgH=vp.height;
  await page.render({canvasContext:ctx,viewport:vp}).promise;
  setupMarkupCanvas();
  S.pg=n;
  document.getElementById("plbl").textContent=`${n}/${S.totPg}`;
  applyZoom();redrawMarkup();drawRulers();
}
function prevPg(){if(S.pg>1)renderPage(S.pg-1)}
function nextPg(){if(S.pg<S.totPg)renderPage(S.pg+1)}

function setupMarkupCanvas(){
  const mc=document.getElementById("mc");
  mc.width=S.pgW;mc.height=S.pgH;
  mc.style.width=S.pgW+"px";mc.style.height=S.pgH+"px";
  const cv=document.getElementById("pc");
  cv.style.width=S.pgW+"px";cv.style.height=S.pgH+"px";
}

/* ===== DEMO ===== */
function loadDemo(){
  S.isDemo=true;S.loaded=true;S.totPg=1;S.pg=1;S.pgW=1600;S.pgH=1200;
  document.getElementById("upl").classList.add("gone");
  document.getElementById("ps").style.display="block";
  document.getElementById("pn").classList.remove("show");
  const cv=document.getElementById("pc"),ctx=cv.getContext("2d");
  cv.width=S.pgW;cv.height=S.pgH;
  cv.style.width=S.pgW+"px";cv.style.height=S.pgH+"px";
  drawDemoPlan(ctx);
  setupMarkupCanvas();
  S.scale=960/80;S.sUnit="ft"; // 960px = 80ft
  applyZoom();redrawMarkup();drawRulers();
  toast("Demo loaded — scale 1/4\"=1'-0\"","ok");
}

function drawDemoPlan(c){
  c.fillStyle="#fff";c.fillRect(0,0,1600,1200);
  c.strokeStyle="#e4e8ee";c.lineWidth=.5;
  for(let x=0;x<1600;x+=40){c.beginPath();c.moveTo(x,0);c.lineTo(x,1200);c.stroke()}
  for(let y=0;y<1200;y+=40){c.beginPath();c.moveTo(0,y);c.lineTo(1600,y);c.stroke()}
  c.strokeStyle="#d0d6e0";c.lineWidth=1;
  for(let x=0;x<1600;x+=200){c.beginPath();c.moveTo(x,0);c.lineTo(x,1200);c.stroke()}
  for(let y=0;y<1200;y+=200){c.beginPath();c.moveTo(0,y);c.lineTo(1200,y);c.stroke()}
  // Title block
  c.strokeStyle="#333";c.lineWidth=2.5;c.strokeRect(1120,1040,460,140);
  c.lineWidth=1.2;[[1120,1070,1580,1070],[1120,1100,1580,1100],[1120,1128,1580,1128],[1360,1040,1360,1180]].forEach(([a,b,d,e])=>{c.beginPath();c.moveTo(a,b);c.lineTo(d,e);c.stroke()});
  c.font="bold 16px monospace";c.fillStyle="#333";c.textAlign="center";
  c.fillText("RIVERSIDE MIXED-USE DEVELOPMENT",1240,1062);
  c.font="11px monospace";c.fillStyle="#666";
  c.fillText("1250 RIVER RD, DANBURY NC",1240,1090);c.fillText("MERIDIAN DEV GROUP",1240,1118);
  c.font="bold 14px monospace";c.fillStyle="#333";
  c.fillText("A1.02",1470,1062);c.font="10px monospace";c.fillStyle="#666";
  c.fillText("FLOOR PLAN - LEVEL 1",1470,1090);c.fillText("SCALE: 1/4\" = 1'-0\"",1470,1118);
  c.font="bold 12px monospace";c.fillStyle="#333";c.fillText("REV 2",1470,1160);
  // Building
  c.strokeStyle="#333";c.lineWidth=3;c.strokeRect(120,120,960,880);
  // Grid
  c.save();c.setLineDash([18,8]);c.strokeStyle="#aaa";c.lineWidth=.7;
  ["A","B","C","D","E","F"].forEach((l,i)=>{const x=120+i*192;c.beginPath();c.moveTo(x,60);c.lineTo(x,1040);c.stroke();c.setLineDash([]);c.beginPath();c.arc(x,52,16,0,Math.PI*2);c.stroke();c.font="13px monospace";c.fillStyle="#999";c.textAlign="center";c.fillText(l,x,57);c.setLineDash([18,8])});
  [1,2,3,4,5].forEach((n,i)=>{const y=120+i*220;c.beginPath();c.moveTo(60,y);c.lineTo(1120,y);c.stroke();c.setLineDash([]);c.beginPath();c.arc(48,y,16,0,Math.PI*2);c.stroke();c.fillText(""+n,48,y+5);c.setLineDash([18,8])});
  c.restore();
  // Walls
  c.strokeStyle="#333";c.lineWidth=2.5;
  c.strokeRect(120,120,480,440);c.strokeRect(600,120,480,440);
  c.strokeRect(120,560,320,440);c.strokeRect(440,560,320,440);c.strokeRect(760,560,320,440);
  // Corridor
  c.fillStyle="#f0f4f8";c.fillRect(360,340,480,100);c.strokeStyle="#333";c.lineWidth=2;c.strokeRect(360,340,480,100);
  c.font="12px monospace";c.fillStyle="#666";c.textAlign="center";c.fillText("CORRIDOR C",600,398);
  // Rooms
  [["RETAIL A","2,400 SF",300,260],["RETAIL B","2,400 SF",840,260],["OFFICE 101","1,700 SF",280,760],["OFFICE 102","1,700 SF",600,760],["OFFICE 103","1,700 SF",920,760]].forEach(([n,sf,x,y])=>{
    c.font="bold 14px monospace";c.fillStyle="#444";c.textAlign="center";c.fillText(n,x,y);
    c.font="11px monospace";c.fillStyle="#888";c.fillText(sf,x,y+18)});
  // Stairs
  c.fillStyle="#f8f8f8";c.fillRect(950,140,110,160);c.strokeStyle="#333";c.lineWidth=1.5;c.strokeRect(950,140,110,160);
  for(let i=0;i<12;i++){c.beginPath();c.moveTo(956,148+i*13);c.lineTo(1054,148+i*13);c.strokeStyle="#bbb";c.lineWidth=.5;c.stroke()}
  c.font="10px monospace";c.fillStyle="#666";c.textAlign="center";c.fillText("STAIR 1",1005,320);
  // Elevator
  c.fillStyle="#eef";c.fillRect(950,340,110,100);c.strokeStyle="#333";c.lineWidth=1.5;c.strokeRect(950,340,110,100);
  c.beginPath();c.moveTo(950,340);c.lineTo(1060,440);c.strokeStyle="#bbb";c.lineWidth=.5;c.stroke();
  c.beginPath();c.moveTo(1060,340);c.lineTo(950,440);c.stroke();
  c.fillText("ELEV",1005,460);
  // RR
  c.fillStyle="#f0fff4";c.fillRect(950,560,110,120);c.strokeStyle="#333";c.lineWidth=1;c.strokeRect(950,560,110,120);c.fillText("RR-M",1005,628);
  c.fillStyle="#fff0f0";c.fillRect(950,690,110,120);c.strokeRect(950,690,110,120);c.fillText("RR-W",1005,758);
  // Dims
  c.strokeStyle="#2563eb";c.lineWidth=1;
  c.beginPath();c.moveTo(120,1060);c.lineTo(1080,1060);c.stroke();
  [[120,1054,120,1066],[1080,1054,1080,1066]].forEach(([a,b,d,e])=>{c.beginPath();c.moveTo(a,b);c.lineTo(d,e);c.stroke()});
  c.font="11px monospace";c.fillStyle="#2563eb";c.textAlign="center";c.fillText("80'-0\"",600,1080);
  c.beginPath();c.moveTo(1110,120);c.lineTo(1110,1000);c.stroke();
  [[1104,120,1116,120],[1104,1000,1116,1000]].forEach(([a,b,d,e])=>{c.beginPath();c.moveTo(a,b);c.lineTo(d,e);c.stroke()});
  c.save();c.translate(1130,560);c.rotate(Math.PI/2);c.fillText("73'-4\"",0,0);c.restore();
  c.textAlign="start";
}

/* ===== ZOOM — supports 1% to 6400% ===== */
const ZOOM_LEVELS=[.01,.02,.05,.1,.15,.2,.25,.33,.5,.67,.75,1,1.25,1.5,2,3,4,6,8,12,16,24,32,48,64];
function nearestZoomIdx(z){let best=0,bd=999;ZOOM_LEVELS.forEach((v,i)=>{const d=Math.abs(v-z);if(d<bd){bd=d;best=i}});return best}
function setZoom(z){
  z=Math.max(.01,Math.min(64,z));
  // Preserve scroll center
  const ps=document.getElementById("ps");
  const cx=(ps.scrollLeft+ps.clientWidth/2)/(S.pgW*S.zoom);
  const cy=(ps.scrollTop+ps.clientHeight/2)/(S.pgH*S.zoom);
  S.zoom=z;applyZoom();
  // Restore center
  ps.scrollLeft=cx*S.pgW*S.zoom-ps.clientWidth/2;
  ps.scrollTop=cy*S.pgH*S.zoom-ps.clientHeight/2;
}
function zIn(){const i=Math.min(ZOOM_LEVELS.length-1,nearestZoomIdx(S.zoom)+1);setZoom(ZOOM_LEVELS[i])}
function zOut(){const i=Math.max(0,nearestZoomIdx(S.zoom)-1);setZoom(ZOOM_LEVELS[i])}
function zFit(){if(!S.loaded)return;const ps=document.getElementById("ps");setZoom(Math.min(ps.clientWidth/S.pgW,ps.clientHeight/S.pgH)*.95)}
function applyZoom(){
  const pw=document.getElementById("pw");
  pw.style.transform=`scale(${S.zoom})`;
  const pct=Math.round(S.zoom*100);
  document.getElementById("zlbl").textContent=pct+"%";
  document.getElementById("zoomInput").value=pct;
  drawRulers();
}

// Wheel zoom with center preservation
document.getElementById("ps")?.addEventListener("wheel",e=>{
  if(e.ctrlKey||e.metaKey){
    e.preventDefault();
    const ps=document.getElementById("ps");
    const rect=ps.getBoundingClientRect();
    const mx=(e.clientX-rect.left+ps.scrollLeft)/(S.pgW*S.zoom);
    const my=(e.clientY-rect.top+ps.scrollTop)/(S.pgH*S.zoom);
    const factor=e.deltaY<0?1.15:1/1.15;
    S.zoom=Math.max(.01,Math.min(64,S.zoom*factor));
    applyZoom();
    ps.scrollLeft=mx*S.pgW*S.zoom-(e.clientX-rect.left);
    ps.scrollTop=my*S.pgH*S.zoom-(e.clientY-rect.top);
  }
},{passive:false});

// Pinch zoom
let lastPinchDist=0;
document.getElementById("ps")?.addEventListener("touchstart",e=>{if(e.touches.length===2){lastPinchDist=Math.hypot(e.touches[0].clientX-e.touches[1].clientX,e.touches[0].clientY-e.touches[1].clientY)}},{passive:true});
document.getElementById("ps")?.addEventListener("touchmove",e=>{if(e.touches.length===2){e.preventDefault();const d=Math.hypot(e.touches[0].clientX-e.touches[1].clientX,e.touches[0].clientY-e.touches[1].clientY);if(lastPinchDist){const f=d/lastPinchDist;S.zoom=Math.max(.01,Math.min(64,S.zoom*f));applyZoom()}lastPinchDist=d}},{passive:false});

/* ===== RULERS ===== */
function togRuler(){S.showRuler=!S.showRuler;["rh","rv","rc"].forEach(id=>document.getElementById(id).style.display=S.showRuler?"block":"none");document.getElementById("tRul").classList.toggle("on",S.showRuler)}
function cycleUnit(){const u=["ft","in","m","cm","mm"];const i=(u.indexOf(S.sUnit)+1)%u.length;S.sUnit=u[i];document.getElementById("rc").textContent=S.sUnit;drawRulers()}
function drawRulers(){
  if(!S.showRuler||!S.loaded)return;
  const ps=document.getElementById("ps");
  const sl=ps.scrollLeft,st=ps.scrollTop;
  // Horizontal
  const hc=document.getElementById("rhc"),hx=hc.getContext("2d");
  const hw=ps.clientWidth;hc.width=hw;hc.height=20;
  const cs=getComputedStyle(document.documentElement);
  const rulerBg=cs.getPropertyValue('--ruler-bg').trim()||'#0c1322';
  const rulerLine=cs.getPropertyValue('--brd').trim()||'#2a3f65';
  const rulerText=cs.getPropertyValue('--t3').trim()||'#5a7aa8';
  hx.fillStyle=rulerBg;hx.fillRect(0,0,hw,20);
  const pxPerUnit=S.scale?S.scale*S.zoom:50*S.zoom;
  let step=1,minSpacing=60;
  const steps=[.01,.02,.05,.1,.25,.5,1,2,5,10,20,50,100,200,500,1000];
  for(const s of steps){if(s*pxPerUnit>=minSpacing){step=s;break}}
  const startUnit=Math.floor(sl/pxPerUnit/step)*step;
  hx.strokeStyle=rulerLine;hx.fillStyle=rulerText;hx.font="8px monospace";hx.textAlign="center";
  for(let u=startUnit;u*pxPerUnit-sl<hw+pxPerUnit;u+=step){
    const x=u*pxPerUnit-sl;
    hx.beginPath();hx.moveTo(x,14);hx.lineTo(x,20);hx.lineWidth=1;hx.stroke();
    if(S.scale){hx.fillText((u).toFixed(step<1?2:step<10?1:0),x,11)}
    else{hx.fillText(Math.round(u),x,11)}
    // Sub ticks
    for(let j=1;j<5;j++){const sx=x+j*(step*pxPerUnit/5);hx.beginPath();hx.moveTo(sx,17);hx.lineTo(sx,20);hx.lineWidth=.5;hx.stroke()}
  }
  // Vertical
  const vc=document.getElementById("rvc"),vx=vc.getContext("2d");
  const vh=ps.clientHeight;vc.width=28;vc.height=vh;
  vx.fillStyle=rulerBg;vx.fillRect(0,0,28,vh);
  const startV=Math.floor(st/pxPerUnit/step)*step;
  vx.strokeStyle=rulerLine;vx.fillStyle=rulerText;vx.font="8px monospace";vx.textAlign="right";
  for(let u=startV;u*pxPerUnit-st<vh+pxPerUnit;u+=step){
    const y=u*pxPerUnit-st;
    vx.beginPath();vx.moveTo(22,y);vx.lineTo(28,y);vx.lineWidth=1;vx.stroke();
    vx.save();vx.translate(10,y+1);vx.rotate(-Math.PI/2);vx.textAlign="center";
    if(S.scale)vx.fillText(u.toFixed(step<1?2:step<10?1:0),0,0);
    else vx.fillText(Math.round(u),0,0);
    vx.restore();
    for(let j=1;j<5;j++){const sy=y+j*(step*pxPerUnit/5);vx.beginPath();vx.moveTo(25,sy);vx.lineTo(28,sy);vx.lineWidth=.5;vx.stroke()}
  }
}
document.getElementById("ps")?.addEventListener("scroll",()=>drawRulers());

/* ===== TOGGLES ===== */
function togComm(){S.showComm=!S.showComm;document.getElementById("tCom").classList.toggle("on",S.showComm);redrawMarkup()}
function togMark(){S.showMark=!S.showMark;document.getElementById("tMrk").classList.toggle("on",S.showMark);redrawMarkup()}
function togGrid(){S.showGrid=!S.showGrid;document.getElementById("tGrd").classList.toggle("on",S.showGrid);redrawMarkup()}
function togCross(){S.showCross=!S.showCross;document.getElementById("tXh").classList.toggle("on",S.showCross)}

/* ===== DRAWING / MARKUP ENGINE ===== */
function canvasCoords(e){
  const mc=document.getElementById("mc"),r=mc.getBoundingClientRect();
  return{x:(e.clientX-r.left)/S.zoom,y:(e.clientY-r.top)/S.zoom};
}
function redrawMarkup(){
  const mc=document.getElementById("mc"),ctx=mc.getContext("2d");
  ctx.clearRect(0,0,mc.width,mc.height);
  // Grid overlay
  if(S.showGrid){
    ctx.strokeStyle="rgba(59,130,246,.08)";ctx.lineWidth=1;
    const gs=S.scale?S.scale:50;
    for(let x=0;x<mc.width;x+=gs){ctx.beginPath();ctx.moveTo(x,0);ctx.lineTo(x,mc.height);ctx.stroke()}
    for(let y=0;y<mc.height;y+=gs){ctx.beginPath();ctx.moveTo(0,y);ctx.lineTo(mc.width,y);ctx.stroke()}
  }
  if(!S.showMark&&!S.showComm)return;
  const anns=getAnns(S.pg);
  if(S.showMark){
    anns.forEach(a=>{
      ctx.save();ctx.globalAlpha=a.op||1;
      if(a.type==="line"){
        ctx.strokeStyle=a.col;ctx.lineWidth=a.w;setDash(ctx,a.sty);
        ctx.beginPath();ctx.moveTo(a.x1,a.y1);ctx.lineTo(a.x2,a.y2);ctx.stroke();
        if(a.arrow){drawArrowHead(ctx,a.x1,a.y1,a.x2,a.y2,a.col)}
      }else if(a.type==="rect"){
        ctx.strokeStyle=a.col;ctx.lineWidth=a.w;setDash(ctx,a.sty);
        if(a.fill){ctx.fillStyle=a.fill;ctx.fillRect(a.x,a.y,a.rw,a.rh)}
        ctx.strokeRect(a.x,a.y,a.rw,a.rh);
      }else if(a.type==="circle"){
        ctx.strokeStyle=a.col;ctx.lineWidth=a.w;setDash(ctx,a.sty);
        ctx.beginPath();ctx.ellipse(a.cx,a.cy,Math.abs(a.rx),Math.abs(a.ry),0,0,Math.PI*2);
        if(a.fill){ctx.fillStyle=a.fill;ctx.fill()}ctx.stroke();
      }else if(a.type==="cloud"){
        drawCloud(ctx,a.x,a.y,a.rw,a.rh,a.col,a.w);
      }else if(a.type==="pen"){
        ctx.strokeStyle=a.col;ctx.lineWidth=a.w;ctx.lineCap="round";ctx.lineJoin="round";setDash(ctx,a.sty);
        if(a.pts.length>1){ctx.beginPath();ctx.moveTo(a.pts[0].x,a.pts[0].y);a.pts.slice(1).forEach(p=>ctx.lineTo(p.x,p.y));ctx.stroke()}
      }else if(a.type==="highlighter"){
        ctx.globalAlpha=.3;ctx.strokeStyle=a.col;ctx.lineWidth=a.w*4;ctx.lineCap="round";ctx.lineJoin="round";
        if(a.pts.length>1){ctx.beginPath();ctx.moveTo(a.pts[0].x,a.pts[0].y);a.pts.slice(1).forEach(p=>ctx.lineTo(p.x,p.y));ctx.stroke()}
      }else if(a.type==="text"){
        ctx.font=`${a.bold?"bold ":""}${a.italic?"italic ":""}${a.fs}px monospace`;
        ctx.fillStyle=a.col;ctx.fillText(a.txt,a.x,a.y);
      }else if(a.type==="stamp"){
        const st=STAMPS.find(s=>s.id===a.sid);if(!st)return;
        ctx.fillStyle=st.c+"20";ctx.strokeStyle=st.c;ctx.lineWidth=2.5;
        const w=a.txt?ctx.measureText(st.i+" "+st.l).width+24:130;
        ctx.beginPath();roundRect(ctx,a.x-w/2,a.y-18,w,36,5);ctx.fill();ctx.stroke();
        ctx.font="bold 14px monospace";ctx.fillStyle=st.c;ctx.textAlign="center";
        ctx.fillText(st.i+" "+st.l,a.x,a.y+5);ctx.textAlign="start";
      }else if(a.type==="callout"){
        ctx.strokeStyle=a.col;ctx.lineWidth=a.w;ctx.fillStyle="#fff";
        ctx.beginPath();roundRect(ctx,a.x,a.y,a.rw||160,a.rh||40,4);ctx.fill();ctx.stroke();
        ctx.font=`${a.fs||12}px monospace`;ctx.fillStyle="#333";
        ctx.fillText(a.txt||"Note",a.x+6,a.y+(a.rh||40)/2+4);
      }else if(a.type==="measure"){
        ctx.strokeStyle="#2563eb";ctx.lineWidth=1.5;ctx.setLineDash([]);
        ctx.beginPath();ctx.moveTo(a.x1,a.y1);ctx.lineTo(a.x2,a.y2);ctx.stroke();
        drawEndTick(ctx,a.x1,a.y1,a.x2,a.y2);drawEndTick(ctx,a.x2,a.y2,a.x1,a.y1);
        const mx=(a.x1+a.x2)/2,my=(a.y1+a.y2)/2;
        ctx.font="bold 11px monospace";ctx.fillStyle="#2563eb";ctx.textAlign="center";
        ctx.fillText(fmtDist(a.val),mx,my-8);ctx.textAlign="start";
      }else if(a.type==="crossout"){
        ctx.strokeStyle=a.col;ctx.lineWidth=a.w;
        ctx.beginPath();ctx.moveTo(a.x,a.y);ctx.lineTo(a.x+a.rw,a.y+a.rh);ctx.stroke();
        ctx.beginPath();ctx.moveTo(a.x+a.rw,a.y);ctx.lineTo(a.x,a.y+a.rh);ctx.stroke();
      }
      ctx.restore();
    });
  }
  // Comment pins
  if(S.showComm){
    CMT.filter(c=>S.selDiscs.includes(c.d)).forEach(c=>{
      const d=DISC.find(dd=>dd.id===c.d);const col=c.res?"#10b981":(d?.c||"#3b82f6");
      const px=c.px*mc.width,py=c.py*mc.height;
      ctx.beginPath();ctx.arc(px,py,16,0,Math.PI*2);ctx.fillStyle=d?.c+"30";ctx.fill();
      ctx.beginPath();ctx.arc(px,py,11,0,Math.PI*2);ctx.fillStyle=col;ctx.fill();
      ctx.font="bold 9px monospace";ctx.fillStyle="#fff";ctx.textAlign="center";
      ctx.fillText(c.res?"✓":""+c.id,px,py+3);ctx.textAlign="start";
    });
  }
  // Current drawing preview
  if(S.drawing&&S.curPt){
    ctx.save();ctx.setLineDash([4,4]);ctx.strokeStyle=S.stroke;ctx.lineWidth=S.lineWidth;
    const dp=S.drawPts;
    if(S.tool==="line"||S.tool==="arrow"||S.tool==="measure"){
      ctx.beginPath();ctx.moveTo(dp[0].x,dp[0].y);ctx.lineTo(S.curPt.x,S.curPt.y);ctx.stroke();
      if(S.tool==="measure"){const d=dist(dp[0],S.curPt);ctx.setLineDash([]);ctx.font="bold 10px monospace";ctx.fillStyle="#2563eb";ctx.textAlign="center";ctx.fillText(fmtDist(d),(dp[0].x+S.curPt.x)/2,(dp[0].y+S.curPt.y)/2-10);ctx.textAlign="start"}
    }else if(S.tool==="rect"||S.tool==="crossout"){
      ctx.strokeRect(Math.min(dp[0].x,S.curPt.x),Math.min(dp[0].y,S.curPt.y),Math.abs(S.curPt.x-dp[0].x),Math.abs(S.curPt.y-dp[0].y));
    }else if(S.tool==="circle"){
      const cx=(dp[0].x+S.curPt.x)/2,cy=(dp[0].y+S.curPt.y)/2;
      ctx.beginPath();ctx.ellipse(cx,cy,Math.abs(S.curPt.x-dp[0].x)/2,Math.abs(S.curPt.y-dp[0].y)/2,0,0,Math.PI*2);ctx.stroke();
    }else if(S.tool==="cloud"){
      drawCloud(ctx,Math.min(dp[0].x,S.curPt.x),Math.min(dp[0].y,S.curPt.y),Math.abs(S.curPt.x-dp[0].x),Math.abs(S.curPt.y-dp[0].y),S.stroke,S.lineWidth);
    }
    ctx.restore();
  }
}

// Drawing helpers
function setDash(ctx,s){if(s==="dashed")ctx.setLineDash([8,4]);else if(s==="dotted")ctx.setLineDash([2,4]);else ctx.setLineDash([])}
function drawArrowHead(ctx,x1,y1,x2,y2,col){const a=Math.atan2(y2-y1,x2-x1),s=10;ctx.fillStyle=col;ctx.beginPath();ctx.moveTo(x2,y2);ctx.lineTo(x2-s*Math.cos(a-Math.PI/6),y2-s*Math.sin(a-Math.PI/6));ctx.lineTo(x2-s*Math.cos(a+Math.PI/6),y2-s*Math.sin(a+Math.PI/6));ctx.closePath();ctx.fill()}
function drawEndTick(ctx,x1,y1,x2,y2){const a=Math.atan2(y2-y1,x2-x1)+Math.PI/2,s=6;ctx.beginPath();ctx.moveTo(x1-s*Math.cos(a),y1-s*Math.sin(a));ctx.lineTo(x1+s*Math.cos(a),y1+s*Math.sin(a));ctx.stroke()}
function drawCloud(ctx,x,y,w,h,col,lw){
  ctx.strokeStyle=col;ctx.lineWidth=lw;ctx.setLineDash([]);
  const bumps=Math.max(4,Math.round((w+h)/30));
  ctx.beginPath();
  for(let i=0;i<bumps;i++){const t=i/bumps*2*Math.PI;const t2=(i+1)/bumps*2*Math.PI;
    const cx1=x+w/2+w/2*Math.cos(t),cy1=y+h/2+h/2*Math.sin(t);
    const cx2=x+w/2+w/2*Math.cos(t2),cy2=y+h/2+h/2*Math.sin(t2);
    const mx=(cx1+cx2)/2+(Math.cos((t+t2)/2))*15,my=(cy1+cy2)/2+(Math.sin((t+t2)/2))*15;
    if(i===0)ctx.moveTo(cx1,cy1);ctx.quadraticCurveTo(mx,my,cx2,cy2)}
  ctx.closePath();ctx.stroke();
}
function roundRect(ctx,x,y,w,h,r){ctx.beginPath();ctx.moveTo(x+r,y);ctx.lineTo(x+w-r,y);ctx.arcTo(x+w,y,x+w,y+r,r);ctx.lineTo(x+w,y+h-r);ctx.arcTo(x+w,y+h,x+w-r,y+h,r);ctx.lineTo(x+r,y+h);ctx.arcTo(x,y+h,x,y+h-r,r);ctx.lineTo(x,y+r);ctx.arcTo(x,y,x+r,y,r);ctx.closePath()}
function dist(a,b){return Math.sqrt((a.x-b.x)**2+(a.y-b.y)**2)}
function fmtDist(px){if(!S.scale)return Math.round(px)+"px";const v=px/S.scale;return v.toFixed(v<1?2:v<10?1:0)+" "+S.sUnit}

/* ===== CANVAS EVENTS ===== */
const mc=document.getElementById("mc");
mc.addEventListener("mousedown",e=>{
  const p=canvasCoords(e);
  if(S.tool==="pan"){S.panActive=true;S.panStart={x:e.clientX,y:e.clientY};const ps=document.getElementById("ps");S.scrollStart={x:ps.scrollLeft,y:ps.scrollTop};mc.style.cursor="grabbing";return}
  if(["line","arrow","rect","circle","cloud","crossout","measure","pen","highlighter","callout"].includes(S.tool)){
    S.drawing=true;S.drawPts=[p];S.curPt=p;
  }
  if(S.tool==="stamp"){
    getAnns(S.pg).push({type:"stamp",sid:S.stampId,x:p.x,y:p.y,op:S.opacity});
    pushUndo();redrawMarkup();
    toast("Stamp: "+STAMPS.find(s=>s.id===S.stampId)?.l,"ok");
  }
  if(S.tool==="text"||S.tool==="typewriter"){
    const txt=prompt("Enter text:");
    if(txt){getAnns(S.pg).push({type:"text",x:p.x,y:p.y,txt,col:S.stroke,fs:S.fontSize,bold:S.fontBold,italic:S.fontItalic,op:S.opacity});pushUndo();redrawMarkup()}
  }
  if(S.tool==="note"){
    const txt=prompt("Note text:");
    if(txt){getAnns(S.pg).push({type:"callout",x:p.x,y:p.y,rw:180,rh:50,txt,col:"#f59e0b",fs:11,w:2,op:S.opacity});pushUndo();redrawMarkup()}
  }
  if(S.tool==="calibrate"){
    if(!S.caling){S.caling=true;S.calPt1=p;document.getElementById("sbar").classList.add("show");setSBTab("calibrate");renderScaleBody()}
    else if(!S.calPt2){S.calPt2=p;renderScaleBody()}
  }
  if(S.tool==="punch"){
    const txt=prompt("Punch item description:");
    if(txt){S.punches.push({id:S.punches.length+1,txt,x:p.x,y:p.y,page:S.pg,done:false,date:new Date().toLocaleDateString()});
    getAnns(S.pg).push({type:"stamp",sid:"info",x:p.x,y:p.y,op:.9});
    pushUndo();redrawMarkup();renderPanel();toast("Punch item added","ok")}
  }
  if(S.tool==="count"){
    let counts=getAnns(S.pg).filter(a=>a.type==="count");
    getAnns(S.pg).push({type:"count",x:p.x,y:p.y,n:counts.length+1,col:S.stroke});
    pushUndo();redrawMarkup();toast("Count: "+(counts.length+1),"info");
  }
});
mc.addEventListener("mousemove",e=>{
  const p=canvasCoords(e);
  // Crosshair
  if(S.showCross){document.getElementById("xh").style.display="block";document.getElementById("xh").style.top=(e.clientY-document.getElementById("ca").getBoundingClientRect().top)+"px";document.getElementById("xv").style.display="block";document.getElementById("xv").style.left=(e.clientX-document.getElementById("ca").getBoundingClientRect().left)+"px"}
  // Coords
  if(S.loaded){const cd=document.getElementById("coords");cd.classList.add("show");cd.textContent=S.scale?`X: ${(p.x/S.scale).toFixed(1)} ${S.sUnit}  Y: ${(p.y/S.scale).toFixed(1)} ${S.sUnit}`:`X: ${Math.round(p.x)}  Y: ${Math.round(p.y)}`}
  // Pan
  if(S.panActive){const ps=document.getElementById("ps");ps.scrollLeft=S.scrollStart.x-(e.clientX-S.panStart.x);ps.scrollTop=S.scrollStart.y-(e.clientY-S.panStart.y);return}
  // Drawing
  if(S.drawing){
    S.curPt=p;
    if(S.tool==="pen"||S.tool==="highlighter")S.drawPts.push(p);
    // Measurement tooltip
    if(S.tool==="measure"){const d=dist(S.drawPts[0],p);const tip=document.getElementById("mtip");tip.style.display="block";tip.style.left=e.clientX+12+"px";tip.style.top=e.clientY-20+"px";tip.textContent=fmtDist(d)}
    redrawMarkup();
  }
});
mc.addEventListener("mouseup",e=>{
  document.getElementById("mtip").style.display="none";
  if(S.panActive){S.panActive=false;mc.style.cursor="";return}
  if(!S.drawing)return;
  const p=canvasCoords(e);S.drawing=false;S.curPt=null;
  const dp=S.drawPts,anns=getAnns(S.pg);
  if(S.tool==="line"){anns.push({type:"line",x1:dp[0].x,y1:dp[0].y,x2:p.x,y2:p.y,col:S.stroke,w:S.lineWidth,sty:S.lineStyle,op:S.opacity})}
  else if(S.tool==="arrow"){anns.push({type:"line",x1:dp[0].x,y1:dp[0].y,x2:p.x,y2:p.y,col:S.stroke,w:S.lineWidth,sty:S.lineStyle,op:S.opacity,arrow:true})}
  else if(S.tool==="rect"){anns.push({type:"rect",x:Math.min(dp[0].x,p.x),y:Math.min(dp[0].y,p.y),rw:Math.abs(p.x-dp[0].x),rh:Math.abs(p.y-dp[0].y),col:S.stroke,fill:S.fill,w:S.lineWidth,sty:S.lineStyle,op:S.opacity})}
  else if(S.tool==="circle"){anns.push({type:"circle",cx:(dp[0].x+p.x)/2,cy:(dp[0].y+p.y)/2,rx:Math.abs(p.x-dp[0].x)/2,ry:Math.abs(p.y-dp[0].y)/2,col:S.stroke,fill:S.fill,w:S.lineWidth,sty:S.lineStyle,op:S.opacity})}
  else if(S.tool==="cloud"){anns.push({type:"cloud",x:Math.min(dp[0].x,p.x),y:Math.min(dp[0].y,p.y),rw:Math.abs(p.x-dp[0].x),rh:Math.abs(p.y-dp[0].y),col:S.stroke,w:S.lineWidth,op:S.opacity})}
  else if(S.tool==="crossout"){anns.push({type:"crossout",x:Math.min(dp[0].x,p.x),y:Math.min(dp[0].y,p.y),rw:Math.abs(p.x-dp[0].x),rh:Math.abs(p.y-dp[0].y),col:S.stroke,w:S.lineWidth,op:S.opacity})}
  else if(S.tool==="pen"&&dp.length>2){anns.push({type:"pen",pts:[...dp],col:S.stroke,w:S.lineWidth,sty:S.lineStyle,op:S.opacity})}
  else if(S.tool==="highlighter"&&dp.length>2){anns.push({type:"highlighter",pts:[...dp],col:S.stroke,w:S.lineWidth,op:.3})}
  else if(S.tool==="measure"){const d=dist(dp[0],p);anns.push({type:"measure",x1:dp[0].x,y1:dp[0].y,x2:p.x,y2:p.y,val:d});getMeas(S.pg).push({dist:d,fmt:fmtDist(d)})}
  else if(S.tool==="callout"){anns.push({type:"callout",x:Math.min(dp[0].x,p.x),y:Math.min(dp[0].y,p.y),rw:Math.abs(p.x-dp[0].x)||160,rh:Math.abs(p.y-dp[0].y)||40,txt:prompt("Callout text:")||"Note",col:S.stroke,fs:S.fontSize,w:S.lineWidth,op:S.opacity})}
  S.drawPts=[];pushUndo();redrawMarkup();if(S.rpanel==="markups"||S.rpanel==="meas")renderPanel();
});
mc.addEventListener("mouseleave",()=>{if(S.showCross){document.getElementById("xh").style.display="none";document.getElementById("xv").style.display="none"}document.getElementById("coords").classList.remove("show")});

// Undo/Redo
function pushUndo(){S.undoStack.push(JSON.stringify(S.anns));S.redoStack=[];if(S.undoStack.length>50)S.undoStack.shift();if(typeof markUnsaved==='function')markUnsaved()}
function undo(){if(!S.undoStack.length)return;S.redoStack.push(JSON.stringify(S.anns));S.anns=JSON.parse(S.undoStack.pop());redrawMarkup();toast("Undo","info")}
function redo(){if(!S.redoStack.length)return;S.undoStack.push(JSON.stringify(S.anns));S.anns=JSON.parse(S.redoStack.pop());redrawMarkup();toast("Redo","info")}

// Scale calibration
function confirmCal(){if(!S.calPt1||!S.calPt2)return;const d=dist(S.calPt1,S.calPt2);const rv=+document.getElementById("cal-dist")?.value;S.sUnit=document.getElementById("cal-unit")?.value||"ft";if(rv>0&&d>0){S.scale=d/rv;toast(`Scale calibrated: ${rv} ${S.sUnit}`,"ok");renderScaleBody()}cancelCalPoints();drawRulers();redrawMarkup();if(S.rpanel==="meas")renderPanel()}
function cancelCalPoints(){S.caling=false;S.calPt1=S.calPt2=null}
function cancelCal(){cancelCalPoints();document.getElementById("sbar").classList.remove("show")}
function clearScale(){S.scale=null;S.sUnit="ft";toast("Scale cleared","info");drawRulers();redrawMarkup();renderScaleBody();if(S.rpanel==="meas")renderPanel()}

// Scale presets — all standard architectural/engineering scales
const SCALE_PRESETS={
  arch_imperial:[
    {label:'1/16" = 1\'-0"',ratio:"1/16\"=1'",ppi:1/192,unit:"ft",desc:"Very large buildings"},
    {label:'3/32" = 1\'-0"',ratio:"3/32\"=1'",ppi:1/128,unit:"ft",desc:"Large buildings"},
    {label:'1/8" = 1\'-0"',ratio:"1/8\"=1'",ppi:1/96,unit:"ft",desc:"Floor plans, large"},
    {label:'3/16" = 1\'-0"',ratio:"3/16\"=1'",ppi:1/64,unit:"ft",desc:"Floor plans"},
    {label:'1/4" = 1\'-0"',ratio:"1/4\"=1'",ppi:1/48,unit:"ft",desc:"Floor plans, standard"},
    {label:'3/8" = 1\'-0"',ratio:"3/8\"=1'",ppi:1/32,unit:"ft",desc:"Detail plans"},
    {label:'1/2" = 1\'-0"',ratio:"1/2\"=1'",ppi:1/24,unit:"ft",desc:"Details"},
    {label:'3/4" = 1\'-0"',ratio:"3/4\"=1'",ppi:1/16,unit:"ft",desc:"Large details"},
    {label:'1" = 1\'-0"',ratio:"1\"=1'",ppi:1/12,unit:"ft",desc:"Construction details"},
    {label:'1-1/2" = 1\'-0"',ratio:"1½\"=1'",ppi:1/8,unit:"ft",desc:"Large details"},
    {label:'3" = 1\'-0"',ratio:"3\"=1'",ppi:1/4,unit:"ft",desc:"Full-size details"},
    {label:'Full Scale',ratio:"1:1",ppi:1,unit:"in",desc:"Actual size"}
  ],
  eng_imperial:[
    {label:'1" = 10\'',ratio:"1\"=10'",ppi:1/120,unit:"ft",desc:"Site overview"},
    {label:'1" = 20\'',ratio:"1\"=20'",ppi:1/240,unit:"ft",desc:"Site plans"},
    {label:'1" = 30\'',ratio:"1\"=30'",ppi:1/360,unit:"ft",desc:"Grading plans"},
    {label:'1" = 40\'',ratio:"1\"=40'",ppi:1/480,unit:"ft",desc:"Civil plans"},
    {label:'1" = 50\'',ratio:"1\"=50'",ppi:1/600,unit:"ft",desc:"Large civil"},
    {label:'1" = 60\'',ratio:"1\"=60'",ppi:1/720,unit:"ft",desc:"Large area plans"},
    {label:'1" = 100\'',ratio:"1\"=100'",ppi:1/1200,unit:"ft",desc:"Topographic"},
    {label:'1" = 200\'',ratio:"1\"=200'",ppi:1/2400,unit:"ft",desc:"Area maps"},
    {label:'1" = 500\'',ratio:"1\"=500'",ppi:1/6000,unit:"ft",desc:"Regional plans"}
  ],
  metric:[
    {label:'1:1',ratio:"1:1",ppi:1,unit:"mm",desc:"Full scale"},
    {label:'1:2',ratio:"1:2",ppi:1/2,unit:"mm",desc:"Half scale"},
    {label:'1:5',ratio:"1:5",ppi:1/5,unit:"mm",desc:"Large detail"},
    {label:'1:10',ratio:"1:10",ppi:1/10,unit:"mm",desc:"Detail"},
    {label:'1:20',ratio:"1:20",ppi:1/20,unit:"mm",desc:"Room plans"},
    {label:'1:25',ratio:"1:25",ppi:1/25,unit:"mm",desc:"Floor plans"},
    {label:'1:50',ratio:"1:50",ppi:1/50,unit:"mm",desc:"Floor plans standard"},
    {label:'1:100',ratio:"1:100",ppi:1/100,unit:"mm",desc:"Building plans"},
    {label:'1:200',ratio:"1:200",ppi:1/200,unit:"mm",desc:"Site plans"},
    {label:'1:250',ratio:"1:250",ppi:1/250,unit:"mm",desc:"Site plans"},
    {label:'1:500',ratio:"1:500",ppi:1/500,unit:"mm",desc:"Master plans"},
    {label:'1:1000',ratio:"1:1000",ppi:1/1000,unit:"mm",desc:"Area plans"},
    {label:'1:2500',ratio:"1:2500",ppi:1/2500,unit:"mm",desc:"City plans"}
  ]
};

let sbTab="presets";
function setSBTab(t){
  sbTab=t;
  document.querySelectorAll(".sb-tab").forEach(b=>b.classList.toggle("on",b.dataset.st===t));
  renderScaleBody();
}

function applyScalePreset(ppi,unit){
  // ppi = drawing inches per real-world unit. We need pixels per real-world unit.
  // PDF rendered at 3x (216 DPI effective for a 72 DPI doc). Demo is roughly 96 DPI equivalent.
  const dpi=S.isDemo?12:216; // pixels per inch in the rendered canvas
  S.scale=dpi*ppi; // pixels per real-world unit
  if(unit==="mm"){S.sUnit="mm"}
  else if(unit==="in"){S.sUnit="in"}
  else{S.sUnit="ft"}
  toast(`Scale set: ${unit==="mm"?"metric":"imperial"}`,"ok");
  drawRulers();redrawMarkup();renderScaleBody();if(S.rpanel==="meas")renderPanel();
}

function renderScaleBody(){
  const el=document.getElementById("sb-body");
  // Current scale display
  const cw=document.getElementById("sb-current-wrap");
  if(S.scale){cw.innerHTML=`<div class="sb-current"><span class="sb-cur-label">Current:</span><span class="sb-cur-val">${(S.scale).toFixed(2)} px/${S.sUnit}</span><span style="font-size:9px;color:var(--t2);margin-left:auto">Unit: ${S.sUnit}</span></div>`}
  else{cw.innerHTML=`<div class="sb-current"><span style="color:var(--wn);font-size:9px">⚠ No scale set — measurements in pixels</span></div>`}

  let h="";
  if(sbTab==="presets"){
    h+=`<div class="sb-section">Architectural (Imperial)</div>`;
    SCALE_PRESETS.arch_imperial.forEach(s=>{
      h+=`<button class="sb-scale" onclick="applyScalePreset(${s.ppi},'${s.unit}')"><span class="sb-ratio">${s.ratio}</span><span class="sb-desc">${s.desc}</span></button>`});
    h+=`<div class="sb-section">Engineering (Imperial)</div>`;
    SCALE_PRESETS.eng_imperial.forEach(s=>{
      h+=`<button class="sb-scale" onclick="applyScalePreset(${s.ppi},'${s.unit}')"><span class="sb-ratio">${s.ratio}</span><span class="sb-desc">${s.desc}</span></button>`});
    h+=`<div class="sb-section">Metric</div>`;
    SCALE_PRESETS.metric.forEach(s=>{
      h+=`<button class="sb-scale" onclick="applyScalePreset(${s.ppi},'${s.unit}')"><span class="sb-ratio">${s.ratio}</span><span class="sb-desc">${s.desc}</span></button>`});
  }else if(sbTab==="custom"){
    h+=`<div class="sb-custom">`;
    h+=`<div style="font-size:10px;font-weight:600;margin-bottom:8px">Enter a custom scale ratio</div>`;
    h+=`<div class="sb-custom-row"><label>Drawing</label><input id="cust-draw" type="number" value="1" min="0.01" step="0.01" style="width:70px"><select id="cust-draw-unit" style="width:50px"><option value="in">in</option><option value="mm">mm</option><option value="ft">ft</option></select></div>`;
    h+=`<div style="text-align:center;font-size:10px;color:var(--t3);padding:4px 0">= equals =</div>`;
    h+=`<div class="sb-custom-row"><label>Real</label><input id="cust-real" type="number" value="1" min="0.01" step="0.01" style="width:70px"><select id="cust-real-unit" style="width:50px"><option value="ft">ft</option><option value="in">in</option><option value="m">m</option><option value="cm">cm</option><option value="mm">mm</option></select></div>`;
    h+=`<div style="margin-top:10px;display:flex;gap:6px"><button class="sb-btn pri" onclick="applyCustomScale()">Apply Custom Scale</button></div>`;
    h+=`<div style="margin-top:14px;border-top:1px solid var(--brd);padding-top:10px"><div style="font-size:10px;font-weight:600;margin-bottom:6px">Or set pixels per unit directly</div>`;
    h+=`<div class="sb-custom-row"><label>Pixels</label><input id="cust-ppx" type="number" value="${S.scale?S.scale.toFixed(2):"12"}" min="0.01" step="0.01" style="width:80px"><span style="font-size:9px;color:var(--t3)">px per</span><select id="cust-ppx-unit" style="width:50px"><option value="ft"${S.sUnit==="ft"?" selected":""}>ft</option><option value="in"${S.sUnit==="in"?" selected":""}>in</option><option value="m"${S.sUnit==="m"?" selected":""}>m</option><option value="cm"${S.sUnit==="cm"?" selected":""}>cm</option><option value="mm"${S.sUnit==="mm"?" selected":""}>mm</option></select></div>`;
    h+=`<div style="margin-top:6px"><button class="sb-btn pri" onclick="applyDirectScale()">Apply</button></div>`;
    h+=`</div></div>`;
  }else if(sbTab==="calibrate"){
    h+=`<div style="font-size:10px;font-weight:600;margin-bottom:6px">Two-Point Calibration</div>`;
    h+=`<div style="font-size:9px;color:var(--t2);line-height:1.6;margin-bottom:10px">Click two points on the plan along a known dimension (like a dimension line), then enter the real-world distance between them.</div>`;
    h+=`<div style="display:flex;gap:6px;align-items:center;margin-bottom:8px;padding:8px;background:var(--sf);border-radius:6px;border:1px solid var(--brd)">`;
    if(S.calPt1&&S.calPt2){
      const d=dist(S.calPt1,S.calPt2);
      h+=`<span style="color:var(--ok);font-size:14px">✓</span><div style="flex:1"><div style="font-size:10px;font-weight:600;color:var(--ok)">2 points selected</div><div style="font-size:9px;color:var(--t3)">${Math.round(d)} pixels apart</div></div>`;
    }else if(S.calPt1){
      h+=`<span style="color:var(--wn);font-size:14px">◐</span><div style="flex:1"><div style="font-size:10px;font-weight:600;color:var(--wn)">Point 1 set — click point 2</div><div style="font-size:9px;color:var(--t3)">Click the other end of the known dimension</div></div>`;
    }else{
      h+=`<span style="color:var(--t3);font-size:14px">◯</span><div style="flex:1"><div style="font-size:10px;color:var(--t2)">Click first point on the plan</div><div style="font-size:9px;color:var(--t3)">Choose one end of a known dimension line</div></div>`;
    }
    h+=`</div>`;
    h+=`<div class="sb-custom-row"><label>Distance</label><input id="cal-dist" type="number" value="10" min="0.01" step="0.1" style="width:80px"><select id="cal-unit" style="width:50px"><option value="ft">ft</option><option value="in">in</option><option value="m">m</option><option value="cm">cm</option><option value="mm">mm</option></select></div>`;
    h+=`<div style="display:flex;gap:6px;margin-top:8px"><button class="sb-btn pri" onclick="confirmCal()"${!S.calPt1||!S.calPt2?" disabled style='opacity:.5'":""}>Apply Calibration</button><button class="sb-btn sec" onclick="S.calPt1=S.calPt2=null;S.caling=true;renderScaleBody()">Reset Points</button></div>`;
    // Enable calibration mode
    if(!S.caling){S.caling=true}
  }
  el.innerHTML=h;
}

function applyCustomScale(){
  const drawVal=+document.getElementById("cust-draw").value;
  const drawUnit=document.getElementById("cust-draw-unit").value;
  const realVal=+document.getElementById("cust-real").value;
  const realUnit=document.getElementById("cust-real-unit").value;
  if(!drawVal||!realVal){toast("Enter both values","err");return}
  // Convert draw to inches
  let drawInches=drawVal;
  if(drawUnit==="mm")drawInches=drawVal/25.4;
  else if(drawUnit==="ft")drawInches=drawVal*12;
  // Convert real to target unit
  const dpi=S.isDemo?12:216;
  const pxPerDrawUnit=dpi*(drawUnit==="mm"?1/25.4:drawUnit==="ft"?12:1);
  S.scale=(drawVal*pxPerDrawUnit/drawVal)*(drawVal/realVal);
  // Simpler: pxPerRealUnit = dpi * drawInches / realVal
  S.scale=dpi*drawInches/realVal;
  S.sUnit=realUnit;
  toast(`Custom scale applied: ${drawVal}${drawUnit} = ${realVal}${realUnit}`,"ok");
  drawRulers();redrawMarkup();renderScaleBody();if(S.rpanel==="meas")renderPanel();
}

function applyDirectScale(){
  const ppx=+document.getElementById("cust-ppx").value;
  const unit=document.getElementById("cust-ppx-unit").value;
  if(!ppx||ppx<=0){toast("Enter a valid pixels-per-unit value","err");return}
  S.scale=ppx;S.sUnit=unit;
  toast(`Scale: ${ppx} px/${unit}`,"ok");
  drawRulers();redrawMarkup();renderScaleBody();if(S.rpanel==="meas")renderPanel();
}

/* ===== EXPORT ===== */
function exportPDF(){
  if(!S.loaded){toast("No PDF loaded","err");return}
  toast("Generating annotated PDF...","info");
  setTimeout(()=>{
    const {jsPDF}=window.jspdf;
    const cv=document.getElementById("pc"),mcv=document.getElementById("mc");
    // Merge canvases
    const merged=document.createElement("canvas");merged.width=cv.width;merged.height=cv.height;
    const mctx=merged.getContext("2d");mctx.drawImage(cv,0,0);mctx.drawImage(mcv,0,0);
    const imgData=merged.toDataURL("image/jpeg",.92);
    const orient=cv.width>cv.height?"landscape":"portrait";
    const pdf=new jsPDF({orientation:orient,unit:"px",format:[cv.width,cv.height]});
    pdf.addImage(imgData,"JPEG",0,0,cv.width,cv.height);
    pdf.save(`PlanReview_${S.proj.id}_annotated.pdf`);
    toast("PDF exported","ok");
  },100);
}
function exportFlat(){exportPDF()} // same for now

/* ===== COLOR PICKER ===== */
function showCP(el,target){
  const cp=document.getElementById("cpick");
  if(cp.classList.contains("show")){cp.classList.remove("show");return}
  const r=el.getBoundingClientRect();
  cp.style.left=r.left+"px";cp.style.top=r.bottom+4+"px";
  cp.innerHTML=COLORS.map(c=>`<div class="cw${(target==="stroke"?S.stroke:S.fill)===c?" on":""}" style="background:${c||"transparent"}" data-c="${c}" data-t="${target}"></div>`).join("");
  cp.classList.add("show");
  cp.querySelectorAll(".cw").forEach(sw=>sw.addEventListener("click",()=>{
    const c=sw.dataset.c==="transparent"?null:sw.dataset.c;
    if(sw.dataset.t==="stroke"){S.stroke=c||"#000";document.getElementById("pcStroke").style.background=S.stroke}
    else{S.fill=c;document.getElementById("pcFill").style.background=c||"transparent"}
    cp.classList.remove("show");
  }));
}
document.addEventListener("click",e=>{if(!e.target.closest("#cpick")&&!e.target.closest(".pc"))document.getElementById("cpick").classList.remove("show")});

/* ===== LEFT TOOLBAR ===== */
function renderTools(){
  const lt=document.getElementById("lt");
  lt.innerHTML=TOOLS.map(t=>{
    if(t.sep)return'<div class="tsep"></div>';
    return`<button class="tl${S.tool===t.id?" on":""}" data-t="${t.id}" data-fly="${t.fly||""}">${t.i}<span class="tt">${t.l}${t.k?" ("+t.k+")":""}</span>${t.fly?'<span class="fly-arrow">▸</span>':""}</button>`;
  }).join("");
  lt.querySelectorAll(".tl").forEach(b=>b.addEventListener("click",()=>{
    S.tool=b.dataset.t;
    document.querySelectorAll(".fly").forEach(f=>f.classList.remove("show"));
    if(b.dataset.fly){const fly=document.getElementById("fly"+b.dataset.fly[0].toUpperCase()+b.dataset.fly.slice(1));if(fly){fly.style.top=b.getBoundingClientRect().top+"px";fly.classList.add("show")}}
    if(S.tool==="undo"){undo();return}
    if(S.tool==="redo"){redo();return}
    if(S.tool==="calibrate"){S.caling=false;S.calPt1=S.calPt2=null;document.getElementById("sbar").classList.add("show");setSBTab("presets");renderScaleBody()}
    mc.style.cursor=S.tool==="pan"?"grab":["select"].includes(S.tool)?"default":"crosshair";
    renderTools();
  }));
}

// Flyout content
function buildFlyouts(){
  const shapeFly=document.getElementById("flyShapes");
  shapeFly.innerHTML='<div class="fly-t">Shapes</div>'+[{id:"line",i:"╱",l:"Line",k:"L"},{id:"polyline",i:"⟋",l:"Polyline"},{id:"rect",i:"▭",l:"Rectangle",k:"R"},{id:"polygon",i:"⬠",l:"Polygon"},{id:"circle",i:"◯",l:"Ellipse",k:"E"},{id:"arc",i:"◠",l:"Arc"}].map(t=>`<button class="fb${S.tool===t.id?" on":""}" onclick="S.tool='${t.id}';document.querySelectorAll('.fly').forEach(f=>f.classList.remove('show'));renderTools()"><span style="width:18px;text-align:center">${t.i}</span>${t.l}${t.k?`<span class="fk">${t.k}</span>`:""}</button>`).join("");
  const measFly=document.getElementById("flyMeasure");
  measFly.innerHTML='<div class="fly-t">Measurement</div>'+[{id:"measure",i:"📏",l:"Distance",k:"M"},{id:"area",i:"⬡",l:"Area",k:"Q"},{id:"perimeter",i:"◻",l:"Perimeter"},{id:"angle",i:"∠",l:"Angle"},{id:"radius",i:"◔",l:"Radius/Diameter"},{id:"count",i:"#",l:"Count"}].map(t=>`<button class="fb${S.tool===t.id?" on":""}" onclick="S.tool='${t.id}';document.querySelectorAll('.fly').forEach(f=>f.classList.remove('show'));renderTools()"><span style="width:18px;text-align:center">${t.i}</span>${t.l}${t.k?`<span class="fk">${t.k}</span>`:""}</button>`).join("");
  const stampFly=document.getElementById("flyStamps");
  stampFly.innerHTML='<div class="fly-t">Stamps</div>'+STAMPS.map(s=>`<button class="fb${S.stampId===s.id?" on":""}" style="color:${s.c}" onclick="S.stampId='${s.id}';S.tool='stamp';document.querySelectorAll('.fly').forEach(f=>f.classList.remove('show'));renderTools()"><span style="width:18px;text-align:center">${s.i}</span>${s.l}</button>`).join("");
  const textFly=document.getElementById("flyText");
  textFly.innerHTML='<div class="fly-t">Text & Annotations</div>'+[{id:"text",i:"T",l:"Text Box",k:"T"},{id:"callout",i:"💬",l:"Callout",k:"C"},{id:"note",i:"📝",l:"Sticky Note"},{id:"typewriter",i:"⌨",l:"Typewriter"}].map(t=>`<button class="fb${S.tool===t.id?" on":""}" onclick="S.tool='${t.id}';document.querySelectorAll('.fly').forEach(f=>f.classList.remove('show'));renderTools()"><span style="width:18px;text-align:center">${t.i}</span>${t.l}${t.k?`<span class="fk">${t.k}</span>`:""}</button>`).join("");
}

// Close flyouts on click outside
document.addEventListener("click",e=>{if(!e.target.closest(".fly")&&!e.target.closest(".tl"))document.querySelectorAll(".fly").forEach(f=>f.classList.remove("show"))});

/* ===== SHEET TABS ===== */
function renderSheetTabs(){
  const el=document.getElementById("stabs");
  el.innerHTML=SHT.slice(0,8).map(sh=>{const d=DISC.find(dd=>dd.id===sh.d);
    return`<button class="st${S.selSheet.id===sh.id?" on":""}" data-sh="${sh.id}" ${S.selSheet.id===sh.id?`style="border-bottom-color:${d?.c}"`:""}><span style="color:${d?.c};font-size:7px">●</span>${sh.id}${sh.c>0?`<span class="cc">${sh.c}</span>`:""}</button>`}).join("")+`<span style="color:var(--t4);font-size:9px;padding:0 6px">+${SHT.length-8} more</span>`;
  el.querySelectorAll(".st").forEach(b=>b.addEventListener("click",()=>{S.selSheet=SHT.find(s=>s.id===b.dataset.sh);renderSheetTabs();if(S.rpanel==="sheets")renderPanel()}));
}

/* ===== RIGHT PANEL ===== */
function renderPanel(){
  const el=document.getElementById("rcon"),p=S.rpanel;let h="";
  if(p==="sheets"){
    h+=`<div class="pt">SHEETS (${SHT.length})</div><div style="display:flex;gap:3px;flex-wrap:wrap;margin-bottom:6px">`;
    DISC.forEach(d=>{const on=S.selDiscs.includes(d.id);h+=`<button class="pill" data-d="${d.id}" style="background:${on?d.c+"20":"transparent"};border-color:${on?d.c+"60":"var(--brd)"};color:${on?d.c:"var(--t4)"}">${d.a}</button>`});
    h+="</div>";
    SHT.filter(s=>S.selDiscs.includes(s.d)).forEach(sh=>{const d=DISC.find(dd=>dd.id===sh.d);const bm={approved:"bok",rejected:"bno",comments:"bwn",pending:"bwt"};
      h+=`<div class="cd${S.selSheet.id===sh.id?" on":""}" data-sh="${sh.id}"><div style="display:flex;align-items:center;gap:6px"><div style="width:4px;height:26px;border-radius:2px;background:${d?.c}"></div><div style="flex:1;min-width:0"><div style="font-weight:600">${sh.id}</div><div style="font-size:9px;color:var(--t3);overflow:hidden;text-overflow:ellipsis;white-space:nowrap">${sh.n}</div></div><div style="text-align:right"><span class="bdg ${bm[sh.s]||"bwt"}">${sh.s}</span>${sh.c>0?`<div style="font-size:8px;color:var(--t3);margin-top:2px">💬 ${sh.c}</div>`:""}</div></div></div>`});
  }else if(p==="comments"){
    h+=`<div class="pt">COMMENTS (${CMT.length})</div>`;
    CMT.forEach(c=>{const d=DISC.find(dd=>dd.id===c.d);const exp=S.expCmt===c.id;
      h+=`<div class="cd${exp?" on":""}" data-cmt="${c.id}" style="border-left:3px solid ${c.res?"var(--ok)":(d?.c||"var(--ac)")}"><div style="display:flex;align-items:center;gap:5px;margin-bottom:4px"><div style="width:22px;height:22px;border-radius:50%;background:${d?.c||"var(--ac)"};display:flex;align-items:center;justify-content:center;font-size:8px;font-weight:700;color:#fff">${c.av}</div><div style="flex:1"><div style="font-weight:600;font-size:10px">${c.u}</div><div style="font-size:8px;color:var(--t3)">${c.r} · ${c.tm}</div></div>${c.res?'<span class="bdg bok">Resolved</span>':""}</div><div style="font-size:9px;color:var(--t2);line-height:1.5">${c.t}</div>${exp?`<div style="margin-top:6px;border-top:1px solid var(--brd);padding-top:6px">${c.re.map(r=>`<div style="display:flex;gap:5px;margin-bottom:4px;padding-left:6px;border-left:2px solid var(--brd)"><div style="width:18px;height:18px;border-radius:50%;background:var(--t3);display:flex;align-items:center;justify-content:center;font-size:7px;color:#fff">${r.a}</div><div><div style="font-size:9px;font-weight:600">${r.u} <span style="color:var(--t4);font-weight:400">· ${r.tm}</span></div><div style="font-size:9px;color:var(--t2)">${r.t}</div></div></div>`).join("")}<div style="display:flex;gap:3px;margin-top:4px"><input style="flex:1;background:var(--bg);border:1px solid var(--brd);border-radius:3px;padding:4px 6px;font-size:9px;color:var(--t1);font-family:var(--f);outline:none" placeholder="Reply..."><button style="background:var(--ac);border:none;color:#fff;padding:4px 8px;border-radius:3px;font-size:9px;font-weight:600" onclick="event.stopPropagation();toast('Reply sent','ok')">Send</button></div><div style="display:flex;gap:3px;margin-top:4px">${!c.res?`<button style="background:rgba(16,185,129,.1);border:1px solid rgba(16,185,129,.25);color:var(--ok);padding:3px 6px;border-radius:3px;font-size:8px;font-weight:600" onclick="event.stopPropagation();toast('Resolved','ok')">✓ Resolve</button>`:""}<button style="background:var(--gbg);border:1px solid rgba(14,165,233,.25);color:var(--gb);padding:3px 6px;border-radius:3px;font-size:8px;font-weight:600" onclick="event.stopPropagation();toast('Synced to GovBuilt','ok')">🔗 Sync</button></div></div>`:""}</div>`});
  }else if(p==="markups"){
    const anns=getAnns(S.pg);
    h+=`<div class="pt">MARKUPS — Page ${S.pg} (${anns.length})</div>`;
    if(!anns.length)h+=`<div style="color:var(--t3);font-size:10px;padding:16px;text-align:center">No markups on this page yet.<br>Use the tools to add annotations.</div>`;
    anns.forEach((a,i)=>{h+=`<div class="cd" style="display:flex;align-items:center;gap:6px"><span style="color:${a.col||"var(--ac)"};font-size:14px">${a.type==="stamp"?"⊕":a.type==="line"?"╱":a.type==="rect"?"▭":a.type==="circle"?"◯":a.type==="cloud"?"☁":a.type==="pen"?"✎":a.type==="measure"?"📏":a.type==="text"?"T":a.type==="callout"?"💬":"●"}</span><div style="flex:1"><div style="font-weight:600;font-size:10px">${a.type.charAt(0).toUpperCase()+a.type.slice(1)}${a.txt?" — "+a.txt.substring(0,20):""}</div><div style="font-size:8px;color:var(--t3)">${a.type==="measure"?fmtDist(a.val):"Layer: "+S.layer}</div></div><button style="background:0;border:none;color:var(--no);font-size:12px" onclick="event.stopPropagation();getAnns(${S.pg}).splice(${i},1);redrawMarkup();renderPanel();toast('Deleted','info')">✕</button></div>`});
  }else if(p==="punch"){
    h+=`<div class="pt">PUNCH LIST (${S.punches.length})</div>`;
    if(!S.punches.length)h+=`<div style="color:var(--t3);font-size:10px;padding:16px;text-align:center">No punch items yet.<br>Select the 📌 Punch tool to add items.</div>`;
    S.punches.forEach((pi,i)=>{h+=`<div class="cd" style="display:flex;align-items:flex-start;gap:6px"><div style="width:16px;height:16px;border-radius:3px;border:2px solid ${pi.done?"var(--ok)":"var(--brd2)"};background:${pi.done?"var(--ok)":"transparent"};display:flex;align-items:center;justify-content:center;font-size:9px;color:#fff;cursor:pointer;margin-top:1px;flex-shrink:0" onclick="event.stopPropagation();S.punches[${i}].done=!S.punches[${i}].done;renderPanel()">${pi.done?"✓":""}</div><div style="flex:1"><div style="font-weight:600;font-size:10px;${pi.done?"text-decoration:line-through;color:var(--t3)":""}">#${pi.id}: ${pi.txt}</div><div style="font-size:8px;color:var(--t3)">Page ${pi.page} · ${pi.date}</div></div></div>`});
  }else if(p==="team"){
    const onlineCount=TEAM.filter(m=>m.online).length;
    h+=`<div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:6px"><div class="pt" style="margin:0">REVIEW TEAM (${TEAM.length})</div><button style="background:var(--ac);border:none;color:#fff;padding:3px 8px;border-radius:3px;font-size:9px;font-weight:600;cursor:pointer;font-family:var(--f)" onclick="openTeamModal()">+ Manage</button></div>`;
    h+=`<div style="font-size:9px;color:var(--t3);margin-bottom:6px">${onlineCount} online now</div>`;
    TEAM.forEach(m=>{const d=DISC.find(dd=>dd.id===m.d);const sm={reviewing:{b:"rgba(59,130,246,.15)",c:"var(--ac)",l:"Reviewing"},complete:{b:"rgba(16,185,129,.15)",c:"var(--ok)",l:"Complete"},not_started:{b:"rgba(100,116,139,.15)",c:"var(--t3)",l:"Not Started"}};const s=sm[m.s]||sm.not_started;
      const isMe=AUTH.currentUser&&AUTH.currentUser.id===m.uid;
      h+=`<div class="cd" style="display:flex;align-items:center;gap:6px">
        <div class="online-dot ${m.online?"on":"off"}"></div>
        <div style="width:24px;height:24px;border-radius:50%;background:${m.color||d?.c||"var(--ac)"};display:flex;align-items:center;justify-content:center;font-size:9px;font-weight:700;color:#fff">${m.a}</div>
        <div style="flex:1"><div style="font-weight:600;font-size:10px">${m.n}${isMe?' <span style="color:var(--ac);font-size:7px">(you)</span>':""}</div><div style="font-size:8px;color:var(--t3)">${m.r}</div></div>
        <span class="bdg" style="background:${s.b};color:${s.c}">${s.l}</span></div>`});
    h+=`<div class="pss">REVIEW PROGRESS</div><div class="cd" style="padding:10px"><div style="display:flex;justify-content:space-around;text-align:center;margin-bottom:8px"><div><div style="font-size:20px;font-weight:700;color:var(--ok)">18</div><div style="font-size:8px;color:var(--t3)">Approved</div></div><div><div style="font-size:20px;font-weight:700;color:var(--wn)">14</div><div style="font-size:8px;color:var(--t3)">Comments</div></div><div><div style="font-size:20px;font-weight:700;color:var(--t3)">10</div><div style="font-size:8px;color:var(--t3)">Pending</div></div></div><div style="height:5px;background:var(--bg);border-radius:3px;overflow:hidden;display:flex"><div style="width:43%;background:var(--ok)"></div><div style="width:33%;background:var(--wn)"></div><div style="width:24%;background:var(--t4)"></div></div></div>
    <button style="width:100%;background:var(--sf);border:1px solid var(--brd);color:var(--t1);padding:7px;border-radius:5px;font-size:10px;font-weight:600;cursor:pointer;font-family:var(--f);margin-top:6px" onclick="toast('Reminder sent to team','ok')">📧 Send Review Reminder</button>`;
  }else if(p==="layers"){
    h+=`<div class="pt">DISCIPLINE LAYERS</div>`;
    DISC.forEach(d=>{const on=S.selDiscs.includes(d.id);
      h+=`<div class="cd" data-ld="${d.id}" style="display:flex;align-items:center;gap:6px"><div style="width:16px;height:16px;border-radius:3px;background:${on?d.c:"transparent"};border:2px solid ${d.c};display:flex;align-items:center;justify-content:center;font-size:9px;color:#fff;font-weight:700">${on?"✓":""}</div><div style="width:3px;height:18px;border-radius:2px;background:${d.c};opacity:${on?1:.3}"></div><div style="flex:1;font-size:10px;font-weight:600;color:${on?"var(--t1)":"var(--t3)"}">${d.l}</div><span style="font-size:8px;color:var(--t3)">${d.a}</span></div>`});
    h+=`<div class="pss">MARKUP LAYERS</div>`;
    ["My Markups","Review Comments","Code References","Measurements","Revision Clouds","Punch Items"].forEach(l=>{h+=`<div class="cd" style="display:flex;align-items:center;gap:6px"><div style="width:16px;height:16px;border-radius:3px;background:var(--ac);border:2px solid var(--ac);display:flex;align-items:center;justify-content:center;font-size:9px;color:#fff">✓</div><span style="font-size:10px">${l}</span></div>`});
  }else if(p==="meas"){
    const ms=getMeas(S.pg);
    h+=`<div class="pt">MEASUREMENTS — Page ${S.pg}</div>`;
    h+=`<div class="cd" style="display:flex;align-items:center;gap:6px;margin-bottom:6px"><span style="font-size:12px">📐</span><div style="flex:1"><div style="font-weight:600;font-size:10px">${S.scale?"Scale: "+(S.scale).toFixed(2)+" px/"+S.sUnit:"No scale set"}</div><div style="font-size:8px;color:var(--t3)">${S.scale?"Measurements in "+S.sUnit:"Set a scale to measure in real units"}</div></div><button style="background:var(--ac);border:none;color:#fff;padding:3px 8px;border-radius:3px;font-size:9px;font-weight:600" onclick="S.tool='calibrate';S.caling=false;document.getElementById('sbar').classList.add('show');setSBTab('presets');renderScaleBody();renderTools()">Set Scale</button></div>`;
    if(!ms.length)h+=`<div style="color:var(--t3);font-size:10px;padding:16px;text-align:center">No measurements yet.<br>Use 📏 Distance or ⬡ Area tools.</div>`;
    ms.forEach((m,i)=>{h+=`<div class="cd" style="display:flex;align-items:center;gap:6px"><span style="color:var(--ac);font-size:12px">📏</span><div style="flex:1;font-weight:600;font-size:11px">${m.fmt}</div></div>`});
  }else if(p==="gb"){
    const pr=S.proj;
    h+=`<div style="background:var(--gbg);border:1px solid rgba(14,165,233,.18);border-radius:6px;padding:10px;margin-bottom:8px"><div style="display:flex;align-items:center;gap:6px;margin-bottom:6px"><div style="width:24px;height:24px;border-radius:5px;background:linear-gradient(135deg,var(--gb),#0284c7);display:flex;align-items:center;justify-content:center;font-size:10px;font-weight:800;color:#fff">GB</div><div><div style="font-size:11px;font-weight:700;color:var(--gb)">GovBuilt Connected</div><div style="font-size:8px;color:var(--t3)">Permit ${pr.gb}</div></div><div style="margin-left:auto;width:7px;height:7px;border-radius:50%;background:var(--ok);box-shadow:0 0 6px var(--ok)"></div></div><div style="display:flex;gap:3px">${["status","sync","api"].map(t=>`<button class="nt${S.gbTab===t?" on":""}" style="flex:1;font-size:8px;text-transform:capitalize" onclick="S.gbTab='${t}';renderPanel()">${t}</button>`).join("")}</div></div>`;
    if(S.gbTab==="status"){
      [{l:"Application",s:"complete",d:pr.sub},{l:"Plan Review",s:"active",d:"In Progress"},{l:"Corrections",s:pr.cy>1?"complete":"pending",d:pr.cy>1?"Cycle "+(pr.cy-1):"—"},{l:"Final Approval",s:"pending",d:"—"},{l:"Permit Issued",s:"pending",d:"—"}].forEach(st=>{
        const col=st.s==="complete"?"var(--ok)":st.s==="active"?"var(--ac)":"var(--brd)";
        h+=`<div style="display:flex;align-items:center;gap:6px;padding:4px 0 4px 8px;margin-left:6px;border-left:2px solid ${col}"><div style="width:10px;height:10px;border-radius:50%;background:${col};margin-left:-12px;display:flex;align-items:center;justify-content:center;font-size:6px;color:#fff">${st.s==="complete"?"✓":st.s==="active"?"●":""}</div><div style="flex:1"><div style="font-size:10px;font-weight:600;color:${st.s==="pending"?"var(--t3)":"var(--t1)"}">${st.l}</div><div style="font-size:8px;color:var(--t3)">${st.d}</div></div></div>`});
      [["Permit ID",pr.gb],["Type",pr.ty],["Applicant",pr.ap],["Contractor",pr.cn],["Submit",pr.sub],["Due",pr.due],["Cycle","#"+pr.cy],["Sheets",pr.sh]].forEach(([k,v])=>{h+=`<div style="display:flex;justify-content:space-between;padding:3px 0;font-size:9px"><span style="color:var(--t3)">${k}</span><span style="font-weight:600">${v}</span></div>`});
    }else if(S.gbTab==="sync"){
      [{l:"Push Review Status",d:"Update permit in GovBuilt",i:"⬆"},{l:"Pull Permit Data",d:"Refresh from GovBuilt",i:"⬇"},{l:"Sync Comments",d:"Two-way sync",i:"🔄"},{l:"Push Markups as PDF",d:"Export annotated sheets",i:"📄"},{l:"Sync Inspections",d:"Pull schedule",i:"📅"},{l:"Push Review Letter",d:"Generate & send",i:"📝"}].forEach(a=>{
        h+=`<div class="cd" style="display:flex;align-items:center;gap:6px" onclick="toast('${a.l}: Syncing...','ok')"><span style="font-size:14px">${a.i}</span><div style="flex:1"><div style="font-weight:600;font-size:10px">${a.l}</div><div style="font-size:8px;color:var(--t3)">${a.d}</div></div><span style="color:var(--gb);font-size:12px">→</span></div>`});
    }else if(S.gbTab==="api"){
      h+=`<div class="cd" style="padding:8px">`;
      [["Endpoint","api.govbuilt.com/v2"],["Auth","OAuth 2.0"],["Tenant","stokes-county-nc"],["Rate","1000/min"],["Webhooks","3 active"]].forEach(([k,v])=>{h+=`<div style="display:flex;justify-content:space-between;padding:2px 0;font-size:9px"><span style="color:var(--t3)">${k}</span><span style="color:var(--gb);font-weight:600">${v}</span></div>`});
      h+=`</div><div class="pss">WEBHOOKS</div>`;
      ["permit.status_changed","review.comment_added","inspection.scheduled"].forEach(e=>{h+=`<div style="background:var(--bg);border-radius:3px;padding:3px 6px;margin-bottom:2px;font-size:9px;color:var(--gb)">${e}</div>`});
    }
  }
  el.innerHTML=h;
  // Event handlers
  if(p==="sheets"){
    el.querySelectorAll(".pill").forEach(b=>b.addEventListener("click",()=>{const id=b.dataset.d;S.selDiscs=S.selDiscs.includes(id)?S.selDiscs.filter(d=>d!==id):[...S.selDiscs,id];renderPanel();redrawMarkup()}));
    el.querySelectorAll(".cd[data-sh]").forEach(b=>b.addEventListener("click",()=>{S.selSheet=SHT.find(s=>s.id===b.dataset.sh);renderPanel();renderSheetTabs()}));
  }
  if(p==="comments"){el.querySelectorAll(".cd[data-cmt]").forEach(b=>b.addEventListener("click",()=>{S.expCmt=S.expCmt===+b.dataset.cmt?null:+b.dataset.cmt;renderPanel()}))}
  if(p==="layers"){el.querySelectorAll(".cd[data-ld]").forEach(b=>b.addEventListener("click",()=>{const id=b.dataset.ld;S.selDiscs=S.selDiscs.includes(id)?S.selDiscs.filter(d=>d!==id):[...S.selDiscs,id];renderPanel();redrawMarkup()}))}
}

/* ===== TAB HANDLERS ===== */
document.querySelectorAll("#rt .rtb").forEach(t=>t.addEventListener("click",()=>{document.querySelectorAll("#rt .rtb").forEach(x=>x.classList.remove("on"));t.classList.add("on");S.rpanel=t.dataset.p;renderPanel()}));
document.querySelectorAll("#ntabs .nt").forEach(t=>t.addEventListener("click",()=>{
  document.querySelectorAll("#ntabs .nt").forEach(x=>x.classList.remove("on"));
  t.classList.add("on");
  switchMainView(t.dataset.v);
}));

let currentView="review";
function switchMainView(view){
  currentView=view;
  const overlay=document.getElementById("view-overlay");
  if(view==="review"){
    overlay.classList.remove("show");
    // Also switch right panel to sheets
    document.querySelectorAll("#rt .rtb").forEach(x=>x.classList.toggle("on",x.dataset.p==="sheets"));
    S.rpanel="sheets";renderPanel();
    return;
  }
  overlay.classList.add("show");
  let h="";

  if(view==="projects"){
    h+=`<div class="vo-header"><h2>📋 Projects Dashboard</h2><p>All active plan review projects for ${S.proj.ap||"your organization"}</p></div>`;
    // Stats row
    h+=`<div class="vo-grid" style="grid-template-columns:repeat(4,1fr);margin-bottom:16px">
      <div class="vo-card"><div class="vo-stat"><div class="num" style="color:var(--ac)">${PROJ.length}</div><div class="lbl">Active Projects</div></div></div>
      <div class="vo-card"><div class="vo-stat"><div class="num" style="color:var(--ok)">28</div><div class="lbl">Sheets Approved</div></div></div>
      <div class="vo-card"><div class="vo-stat"><div class="num" style="color:var(--wn)">14</div><div class="lbl">Pending Review</div></div></div>
      <div class="vo-card"><div class="vo-stat"><div class="num" style="color:var(--no)">3</div><div class="lbl">Past Due</div></div></div>
    </div>`;
    h+=`<div class="vo-section">All Projects</div><div class="vo-grid">`;
    PROJ.forEach(p=>{
      const pctColor=p.pr>=80?"var(--ok)":p.pr>=50?"var(--wn)":"var(--ac)";
      h+=`<div class="vo-card" onclick="S.proj=PROJ.find(pp=>pp.id==='${p.id}');document.getElementById('pid').textContent=S.proj.id;document.getElementById('pnm').textContent=S.proj.n;switchMainView('review');document.querySelectorAll('#ntabs .nt').forEach(x=>x.classList.toggle('on',x.dataset.v==='review'));renderPanel()">
        <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:6px">
          <h3>${p.n}</h3>
          <span class="bdg ${p.st==="In Review"?"":"bwn"}" style="${p.st==="In Review"?"background:var(--acg);color:var(--ac)":""}">${p.st}</span>
        </div>
        <div class="vo-sub">${p.id} · ${p.ad}</div>
        <div class="vo-row"><span class="vk">Applicant</span><span class="vv">${p.ap}</span></div>
        <div class="vo-row"><span class="vk">Contractor</span><span class="vv">${p.cn}</span></div>
        <div class="vo-row"><span class="vk">Submitted</span><span class="vv">${p.sub}</span></div>
        <div class="vo-row"><span class="vk">Due</span><span class="vv">${p.due}</span></div>
        <div class="vo-row"><span class="vk">Sheets</span><span class="vv">${p.sh}</span></div>
        <div class="vo-row"><span class="vk">Review Cycle</span><span class="vv">#${p.cy}</span></div>
        <div class="vo-row"><span class="vk">GovBuilt</span><span class="vv" style="color:var(--gb)">${p.gb}</span></div>
        <div class="vo-progress"><div class="vo-progress-bar" style="width:${p.pr}%;background:${pctColor}"></div></div>
        <div style="text-align:right;font-size:8px;color:var(--t3);margin-top:3px">${p.pr}% complete</div>
      </div>`;
    });
    h+=`</div>`;
  }

  else if(view==="team"){
    const onlineCount=TEAM.filter(m=>m.online).length;
    h+=`<div class="vo-header"><h2>👥 Review Team</h2><p>${TEAM.length} members · ${onlineCount} online now</p></div>`;
    h+=`<div style="display:flex;gap:8px;margin-bottom:16px">
      <button class="tb pri" onclick="openTeamModal()">+ Add Team Member</button>
      <button class="tb" onclick="toast('Reminder sent to all reviewers','ok')">📧 Send Review Reminder</button>
    </div>`;
    // Stats
    const reviewing=TEAM.filter(m=>m.s==="reviewing").length;
    const complete=TEAM.filter(m=>m.s==="complete").length;
    const notStarted=TEAM.filter(m=>m.s==="not_started").length;
    h+=`<div class="vo-grid" style="grid-template-columns:repeat(4,1fr);margin-bottom:16px">
      <div class="vo-card"><div class="vo-stat"><div class="num" style="color:var(--ok)">${onlineCount}</div><div class="lbl">Online Now</div></div></div>
      <div class="vo-card"><div class="vo-stat"><div class="num" style="color:var(--ac)">${reviewing}</div><div class="lbl">Reviewing</div></div></div>
      <div class="vo-card"><div class="vo-stat"><div class="num" style="color:var(--ok)">${complete}</div><div class="lbl">Complete</div></div></div>
      <div class="vo-card"><div class="vo-stat"><div class="num" style="color:var(--t3)">${notStarted}</div><div class="lbl">Not Started</div></div></div>
    </div>`;
    h+=`<div class="vo-section">Team Members</div><div class="vo-team-grid">`;
    TEAM.forEach(m=>{
      const d=DISC.find(dd=>dd.id===m.d);
      const sm={reviewing:{bg:"rgba(59,130,246,.15)",c:"var(--ac)",l:"Reviewing"},complete:{bg:"rgba(16,185,129,.15)",c:"var(--ok)",l:"Complete"},not_started:{bg:"rgba(100,116,139,.15)",c:"var(--t3)",l:"Not Started"}};
      const s=sm[m.s]||sm.not_started;
      const isMe=AUTH.currentUser&&AUTH.currentUser.id===m.uid;
      h+=`<div class="vo-team-card">
        <div class="online-dot ${m.online?"on":"off"}"></div>
        <div class="av" style="background:${m.color||d?.c||"var(--ac)"}">${m.a}</div>
        <div style="flex:1">
          <div style="font-weight:600;font-size:11px">${m.n}${isMe?' <span style="color:var(--ac);font-size:8px">(you)</span>':""}</div>
          <div style="font-size:9px;color:var(--t3)">${m.r}</div>
          <div style="font-size:8px;color:var(--t4)">${m.email||""}</div>
        </div>
        <div style="text-align:right">
          <span class="bdg" style="background:${s.bg};color:${s.c}">${s.l}</span>
          <div style="margin-top:4px;font-size:8px;color:${d?.c||"var(--t3)"}">${d?.l||""}</div>
        </div>
      </div>`;
    });
    h+=`</div>`;
    h+=`<div class="vo-section">Review Progress by Discipline</div><div class="vo-grid">`;
    DISC.forEach(d=>{
      const members=TEAM.filter(m=>m.d===d.id);
      if(!members.length) return;
      h+=`<div class="vo-card"><div style="display:flex;align-items:center;gap:6px;margin-bottom:6px"><div style="width:4px;height:20px;border-radius:2px;background:${d.c}"></div><div style="font-weight:700;font-size:11px">${d.l}</div></div>`;
      members.forEach(m=>{h+=`<div style="font-size:9px;color:var(--t2);padding:2px 0;display:flex;align-items:center;gap:4px"><div class="online-dot ${m.online?"on":"off"}" style="width:6px;height:6px"></div>${m.n}</div>`});
      h+=`</div>`;
    });
    h+=`</div>`;
  }

  else if(view==="govbuilt"){
    const pr=S.proj;
    h+=`<div class="vo-header"><h2>🔗 GovBuilt Integration</h2><p>Permit management and sync for ${pr.n}</p></div>`;
    h+=`<div class="vo-gb-panel">`;
    // Connection status
    h+=`<div class="vo-gb-card" style="background:var(--gbg);border-color:rgba(14,165,233,.2)">
      <div style="display:flex;align-items:center;gap:10px">
        <div style="width:36px;height:36px;border-radius:8px;background:linear-gradient(135deg,var(--gb),#0284c7);display:flex;align-items:center;justify-content:center;font-size:14px;font-weight:800;color:#fff">GB</div>
        <div style="flex:1">
          <div style="font-size:13px;font-weight:700;color:var(--gb)">GovBuilt Connected</div>
          <div style="font-size:9px;color:var(--t3)">Permit ${pr.gb} · Tenant: stokes-county-nc · API v2</div>
        </div>
        <div style="width:10px;height:10px;border-radius:50%;background:var(--ok);box-shadow:0 0 8px var(--ok)"></div>
      </div>
    </div>`;
    // Permit timeline
    h+=`<div class="vo-gb-card"><h4>📊 Permit Status Timeline</h4><div class="vo-timeline">`;
    [{l:"Application Submitted",s:"done",d:pr.sub,desc:"All documents received and validated"},{l:"Plan Review",s:"active",d:"In Progress",desc:"Multi-discipline review underway — Cycle #"+pr.cy},{l:"Corrections",s:pr.cy>1?"done":"",d:pr.cy>1?"Completed Cycle "+(pr.cy-1):"Pending",desc:pr.cy>1?"Resubmitted with corrections":"Awaiting reviewer feedback"},{l:"Final Approval",s:"",d:"—",desc:"All disciplines must sign off"},{l:"Permit Issued",s:"",d:"—",desc:"Certificate generated in GovBuilt"}].forEach(st=>{
      h+=`<div class="vo-timeline-item ${st.s}"><div class="vo-tl-title">${st.l}</div><div class="vo-tl-sub">${st.d} — ${st.desc}</div></div>`;
    });
    h+=`</div></div>`;
    // Permit details
    h+=`<div class="vo-gb-card"><h4>📝 Permit Details</h4>`;
    [["Permit ID",pr.gb],["Project",pr.n],["Address",pr.ad],["Type",pr.ty],["Applicant",pr.ap],["Contractor",pr.cn],["Submitted",pr.sub],["Due Date",pr.due],["Review Cycle","#"+pr.cy],["Total Sheets",""+pr.sh]].forEach(([k,v])=>{
      h+=`<div class="vo-row"><span class="vk">${k}</span><span class="vv">${v}</span></div>`;
    });
    h+=`</div>`;
    // Sync actions
    h+=`<div class="vo-gb-card"><h4>🔄 Sync Actions</h4><div class="vo-grid" style="grid-template-columns:1fr 1fr">`;
    [{l:"Push Review Status",d:"Update permit status",i:"⬆",c:"var(--ac)"},{l:"Pull Permit Data",d:"Refresh from GovBuilt",i:"⬇",c:"var(--gb)"},{l:"Sync Comments",d:"Two-way comment sync",i:"🔄",c:"var(--ok)"},{l:"Export Markups",d:"Push annotated PDFs",i:"📄",c:"var(--wn)"},{l:"Sync Inspections",d:"Pull inspection schedule",i:"📅",c:"var(--pu)"},{l:"Review Letter",d:"Generate & send",i:"📝",c:"var(--or)"}].forEach(a=>{
      h+=`<div class="vo-card" style="cursor:pointer" onclick="toast('${a.l}: Syncing...','ok')"><div style="display:flex;align-items:center;gap:8px"><span style="font-size:18px">${a.i}</span><div><div style="font-weight:600;font-size:10px">${a.l}</div><div style="font-size:8px;color:var(--t3)">${a.d}</div></div></div></div>`;
    });
    h+=`</div></div>`;
    // API info
    h+=`<div class="vo-gb-card"><h4>⚙ API Configuration</h4>`;
    [["Endpoint","api.govbuilt.com/v2"],["Authentication","OAuth 2.0 (Active)"],["Tenant","stokes-county-nc"],["Rate Limit","1,000 req/min"],["Webhooks","3 active listeners"]].forEach(([k,v])=>{
      h+=`<div class="vo-row"><span class="vk">${k}</span><span class="vv" style="color:var(--gb)">${v}</span></div>`;
    });
    h+=`<div style="margin-top:8px;font-size:9px;font-weight:600;color:var(--t3)">Active Webhooks:</div>`;
    ["permit.status_changed","review.comment_added","inspection.scheduled"].forEach(e=>{
      h+=`<div style="background:var(--sf);border-radius:3px;padding:3px 8px;margin-top:3px;font-size:9px;color:var(--gb);font-family:var(--f)">${e}</div>`;
    });
    h+=`</div>`;
    // Sync log
    h+=`<div class="vo-gb-card"><h4>📋 Recent Sync Activity</h4>`;
    [["Status pushed to GovBuilt","5 min ago","ok"],["14 comments synced","12 min ago","ok"],["3 sheets uploaded","1h ago","ok"],["Permit data refreshed","2h ago","ok"],["Review letter generated","1d ago","ok"]].forEach(([a,t,s])=>{
      h+=`<div style="display:flex;align-items:center;gap:6px;padding:4px 0;font-size:9px"><span style="color:var(--ok)">✓</span><span style="color:var(--t2);flex:1">${a}</span><span style="color:var(--t4)">${t}</span></div>`;
    });
    h+=`</div></div>`;
  }

  overlay.innerHTML=h;
}
document.getElementById("ptog").addEventListener("click",()=>document.getElementById("pdd").classList.toggle("show"));
document.addEventListener("click",e=>{if(!e.target.closest("#ptog")&&!e.target.closest("#pdd"))document.getElementById("pdd").classList.remove("show")});

function renderProjDD(){
  const dd=document.getElementById("pdd");
  dd.innerHTML=PROJ.map(p=>`<button style="width:100%;background:${p.id===S.proj.id?"var(--acg)":"transparent"};border:none;padding:7px 10px;border-radius:5px;cursor:pointer;display:flex;align-items:center;gap:6px;color:var(--t1);font-family:var(--f);font-size:10px;text-align:left" data-pid="${p.id}"><div style="flex:1"><div style="font-weight:600">${p.n}</div><div style="color:var(--t3);font-size:9px">${p.id} · ${p.ad}</div></div><span class="bdg ${p.st==="In Review"?"":"bwn"}" style="${p.st==="In Review"?"background:var(--acg);color:var(--ac)":""}">${p.st}</span></button>`).join("");
  dd.querySelectorAll("button").forEach(b=>b.addEventListener("click",()=>{S.proj=PROJ.find(pp=>pp.id===b.dataset.pid);document.getElementById("pid").textContent=S.proj.id;document.getElementById("pnm").textContent=S.proj.n;dd.classList.remove("show");renderPanel()}));
}

/* ===== KEYBOARD SHORTCUTS ===== */
document.addEventListener("keydown",e=>{
  if(e.target.tagName==="INPUT"||e.target.tagName==="TEXTAREA"||e.target.tagName==="SELECT")return;
  if(e.ctrlKey&&e.key==="z"){e.preventDefault();undo();return}
  if(e.ctrlKey&&e.key==="y"){e.preventDefault();redo();return}
  if(e.key==="+"||e.key==="=")zIn();
  if(e.key==="-")zOut();
  if(e.key==="0")zFit();
  const tool=TOOLS.find(t=>t.k&&t.k.toLowerCase()===e.key.toLowerCase());
  if(tool){S.tool=tool.id;mc.style.cursor=S.tool==="pan"?"grab":["select"].includes(S.tool)?"default":"crosshair";renderTools()}
});

/* ===== AUTH & TEAM MANAGEMENT ===== */
let AUTH={
  currentUser:null,
  users:[
    {id:1,first:"Sarah",last:"Chen",email:"sarah@stokescounty.gov",pass:"123456",role:"Structural Engineer",disc:"struct",org:"Stokes County Building Dept",color:"#ef4444",online:true},
    {id:2,first:"Mike",last:"Torres",email:"mike@stokescounty.gov",pass:"123456",role:"Fire Marshal",disc:"fire",org:"Stokes County Fire Dept",color:"#f97316",online:true},
    {id:3,first:"Lisa",last:"Wang",email:"lisa@stokescounty.gov",pass:"123456",role:"MEP Reviewer",disc:"mech",org:"Stokes County Building Dept",color:"#f59e0b",online:false},
    {id:4,first:"David",last:"Kim",email:"david@stokescounty.gov",pass:"123456",role:"Electrical Inspector",disc:"elec",org:"Stokes County Building Dept",color:"#a855f7",online:false},
    {id:5,first:"Anna",last:"Roberts",email:"anna@stokescounty.gov",pass:"123456",role:"Zoning Officer",disc:"zone",org:"Stokes County Planning",color:"#ec4899",online:true},
    {id:6,first:"Chris",last:"Patel",email:"chris@stokescounty.gov",pass:"123456",role:"Civil Engineer",disc:"civil",org:"Stokes County Engineering",color:"#06b6d4",online:false}
  ],
  teamMembers:[] // IDs of users on current project's review team
};
// Initialize team with all users
AUTH.teamMembers=[1,2,3,4,5,6];

function getInitials(u){return (u.first[0]+u.last[0]).toUpperCase()}
function getFullName(u){return u.first+" "+u.last}

function renderQuickUsers(){
  const el=document.getElementById("quick-users");
  el.innerHTML=AUTH.users.slice(0,6).map(u=>{
    const d=DISC.find(dd=>dd.id===u.disc);
    return`<div class="quick-user" onclick="quickLogin(${u.id})">
      <div class="qu-av" style="background:${u.color}">${getInitials(u)}</div>
      <div><div class="qu-name">${getFullName(u)}</div><div class="qu-role">${u.role}</div></div>
    </div>`}).join("");
}

function showLogin(){document.getElementById("login-form").style.display="block";document.getElementById("register-form").style.display="none"}
function showRegister(){document.getElementById("login-form").style.display="none";document.getElementById("register-form").style.display="block"}

function doLogin(){
  const email=document.getElementById("login-email").value.trim();
  const pass=document.getElementById("login-pass").value;
  if(!email){toast("Enter your email","err");return}
  const user=AUTH.users.find(u=>u.email===email);
  if(user&&(user.pass===pass||!pass)){loginAs(user)}
  else if(email.includes("@")){
    // Auto-create for demo purposes
    const parts=email.split("@")[0].split(".");
    const newUser={id:AUTH.users.length+1,first:parts[0]?parts[0][0].toUpperCase()+parts[0].slice(1):"User",last:parts[1]?parts[1][0].toUpperCase()+parts[1].slice(1):"",email,pass:pass||"123456",role:"Plan Reviewer",disc:"arch",org:"",color:COLORS[Math.floor(Math.random()*17)],online:true};
    AUTH.users.push(newUser);AUTH.teamMembers.push(newUser.id);
    loginAs(newUser);
  }
}

function doRegister(){
  const first=document.getElementById("reg-first").value.trim();
  const last=document.getElementById("reg-last").value.trim();
  const email=document.getElementById("reg-email").value.trim();
  const pass=document.getElementById("reg-pass").value;
  const role=document.getElementById("reg-role").value;
  const disc=document.getElementById("reg-disc").value;
  const org=document.getElementById("reg-org").value.trim();
  if(!first||!email){toast("Name and email required","err");return}
  if(AUTH.users.find(u=>u.email===email)){toast("Email already registered — signing in","info");loginAs(AUTH.users.find(u=>u.email===email));return}
  const newUser={id:AUTH.users.length+1,first,last:last||"",email,pass:pass||"123456",role:role||"Plan Reviewer",disc:disc||"arch",org,color:COLORS[Math.floor(Math.random()*17)],online:true};
  AUTH.users.push(newUser);AUTH.teamMembers.push(newUser.id);
  loginAs(newUser);
}

function quickLogin(id){loginAs(AUTH.users.find(u=>u.id===id))}

function loginAs(user){
  AUTH.currentUser=user;user.online=true;
  document.getElementById("login-overlay").classList.add("gone");
  document.getElementById("top").style.display="flex";
  document.getElementById("propbar").style.display="flex";
  // Update topbar
  updateUserUI();
  toast(`Welcome, ${user.first}!`,"ok");
  // Rebuild team data
  rebuildTeamData();
  renderPanel();
}

function updateUserUI(){
  const u=AUTH.currentUser;if(!u)return;
  document.getElementById("topbar-av").textContent=getInitials(u);
  document.getElementById("topbar-av").style.background=u.color;
  document.getElementById("topbar-name").textContent=getFullName(u);
  document.getElementById("topbar-role").textContent=u.role;
  document.getElementById("um-av").textContent=getInitials(u);
  document.getElementById("um-av").style.background=u.color;
  document.getElementById("um-name").textContent=getFullName(u);
  document.getElementById("um-role").textContent=u.role+" · "+u.org;
  document.getElementById("um-email").textContent=u.email;
}

function doLogout(){
  if(AUTH.currentUser)AUTH.currentUser.online=false;
  AUTH.currentUser=null;
  document.getElementById("login-overlay").classList.remove("gone");
  document.getElementById("top").style.display="none";
  document.getElementById("propbar").style.display="none";
  document.getElementById("user-menu").classList.remove("show");
  // Close video chat if active
  if(typeof vcState!=='undefined'&&vcState.active){vcState.active=false;document.getElementById("vc-window").classList.remove("show","mini");stopLocalCamera()}
  showLogin();
}

function switchUser(){
  document.getElementById("user-menu").classList.remove("show");
  doLogout();
}

function showProfileEdit(){
  document.getElementById("user-menu").classList.remove("show");
  const u=AUTH.currentUser;
  const newRole=prompt("Edit your role/title:",u.role);
  if(newRole!==null&&newRole.trim()){u.role=newRole.trim();updateUserUI();rebuildTeamData();renderPanel();toast("Profile updated","ok")}
}

function rebuildTeamData(){
  // Rebuild TEAM array from AUTH data for the panel
  TEAM.length=0;
  AUTH.teamMembers.forEach(id=>{
    const u=AUTH.users.find(uu=>uu.id===id);
    if(u){
      const isCurrent=AUTH.currentUser&&AUTH.currentUser.id===u.id;
      TEAM.push({n:getFullName(u),r:u.role,a:getInitials(u),s:u.online?(isCurrent?"reviewing":"reviewing"):"not_started",d:u.disc,color:u.color,uid:u.id,online:u.online,email:u.email});
    }
  });
}

// Team Modal
function openTeamModal(){
  document.getElementById("user-menu").classList.remove("show");
  document.getElementById("team-modal").classList.add("show");
  renderTeamModal();
}
function closeTeamModal(){document.getElementById("team-modal").classList.remove("show");rebuildTeamData();renderPanel()}

function renderTeamModal(){
  const el=document.getElementById("tm-body");
  let h=`<div class="tm-add">
    <input id="tm-name" placeholder="Full name" style="flex:1">
    <input id="tm-email" placeholder="Email" style="flex:1">
    <select id="tm-role" style="width:120px"><option value="">Role...</option><option>Plan Reviewer</option><option>Structural Engineer</option><option>Fire Marshal</option><option>MEP Reviewer</option><option>Electrical Inspector</option><option>Plumbing Inspector</option><option>Civil Engineer</option><option>Zoning Officer</option><option>Building Official</option><option>Project Manager</option><option>Architect</option><option>Contractor</option></select>
    <select id="tm-disc" style="width:80px"><option value="">Disc...</option>${DISC.map(d=>`<option value="${d.id}">${d.a}</option>`).join("")}</select>
    <button onclick="addTeamMember()">+ Add</button>
  </div>`;
  h+=`<div style="font-size:9px;color:var(--t3);margin-bottom:6px">${AUTH.teamMembers.length} members · ${AUTH.users.filter(u=>AUTH.teamMembers.includes(u.id)&&u.online).length} online</div>`;
  AUTH.teamMembers.forEach(id=>{
    const u=AUTH.users.find(uu=>uu.id===id);if(!u)return;
    const d=DISC.find(dd=>dd.id===u.disc);
    const isMe=AUTH.currentUser&&AUTH.currentUser.id===u.id;
    h+=`<div class="tm-member">
      <div class="online-dot ${u.online?"on":"off"}"></div>
      <div class="av" style="background:${u.color}">${getInitials(u)}</div>
      <div class="tm-info">
        <div class="name">${getFullName(u)}${isMe?" <span style='color:var(--ac);font-size:8px'>(you)</span>":""}</div>
        <div class="meta">${u.role} · ${u.email}</div>
      </div>
      <div class="tm-actions">
        <select onchange="changeDisc(${u.id},this.value)" style="width:65px">${DISC.map(dd=>`<option value="${dd.id}"${u.disc===dd.id?" selected":""}>${dd.a}</option>`).join("")}</select>
        <select onchange="changeStatus(${u.id},this.value)" style="width:72px">
          <option value="reviewing"${u.online?" selected":""}>Reviewing</option>
          <option value="complete">Complete</option>
          <option value="not_started"${!u.online?" selected":""}>Not Started</option>
        </select>
        ${!isMe?`<button onclick="removeTeamMember(${u.id})" title="Remove">✕</button>`:""} 
      </div>
    </div>`;
  });
  // Non-team users that could be invited
  const nonTeam=AUTH.users.filter(u=>!AUTH.teamMembers.includes(u.id));
  if(nonTeam.length){
    h+=`<div style="font-size:9px;color:var(--t3);margin-top:12px;margin-bottom:6px">Available to invite:</div>`;
    nonTeam.forEach(u=>{
      h+=`<div class="tm-member" style="opacity:.6"><div class="online-dot off"></div><div class="av" style="background:${u.color}">${getInitials(u)}</div><div class="tm-info"><div class="name">${getFullName(u)}</div><div class="meta">${u.role}</div></div><button style="background:var(--ac);border:none;color:#fff;padding:4px 10px;border-radius:3px;font-size:9px;font-weight:600" onclick="inviteToTeam(${u.id})">Invite</button></div>`;
    });
  }
  el.innerHTML=h;
}

function addTeamMember(){
  const name=document.getElementById("tm-name").value.trim();
  const email=document.getElementById("tm-email").value.trim();
  const role=document.getElementById("tm-role").value;
  const disc=document.getElementById("tm-disc").value;
  if(!name){toast("Enter a name","err");return}
  const parts=name.split(" ");
  const newUser={id:AUTH.users.length+1,first:parts[0],last:parts.slice(1).join(" ")||"",email:email||`${parts[0].toLowerCase()}@agency.gov`,pass:"123456",role:role||"Plan Reviewer",disc:disc||"arch",org:"",color:COLORS[Math.floor(Math.random()*17)],online:false};
  AUTH.users.push(newUser);
  AUTH.teamMembers.push(newUser.id);
  toast(`${name} added to team`,"ok");
  renderTeamModal();
}

function removeTeamMember(id){AUTH.teamMembers=AUTH.teamMembers.filter(i=>i!==id);toast("Removed from team","info");renderTeamModal()}
function inviteToTeam(id){AUTH.teamMembers.push(id);toast("Invited to team","ok");renderTeamModal()}
function changeDisc(id,disc){const u=AUTH.users.find(uu=>uu.id===id);if(u)u.disc=disc}
function changeStatus(id,status){const u=AUTH.users.find(uu=>uu.id===id);if(u)u.online=status!=="not_started"}

// Close menus
document.addEventListener("click",e=>{
  if(!e.target.closest("#user-toggle")&&!e.target.closest("#user-menu"))document.getElementById("user-menu").classList.remove("show");
  if(e.target===document.getElementById("team-modal"))closeTeamModal();
});

/* ===== FILE MANAGEMENT ===== */
let recentFiles=[];
let autosaveInterval=null;
let unsavedChanges=false;
let lastSaveTime=Date.now();

function closeFileMenu(){document.getElementById("file-menu").classList.remove("show")}
document.addEventListener("click",e=>{if(!e.target.closest("#file-toggle")&&!e.target.closest("#file-menu"))closeFileMenu()});

function openMulti(){document.getElementById("fi-multi").click()}
document.getElementById("fi-multi").addEventListener("change",async e=>{
  for(const f of e.target.files){
    if(f.type==="application/pdf"){S.pdfBuf=await f.arrayBuffer();await loadPDF(S.pdfBuf,f.name);addRecent(f.name);break}
  }
});

function addRecent(name){
  recentFiles=recentFiles.filter(r=>r.name!==name);
  recentFiles.unshift({name,date:new Date().toLocaleDateString(),time:new Date().toLocaleTimeString()});
  if(recentFiles.length>5)recentFiles.pop();
  renderRecentFiles();
}
function renderRecentFiles(){
  const el=document.getElementById("recent-files");
  if(!el)return;
  if(!recentFiles.length){el.innerHTML='<div class="fm-recent" style="color:var(--t4);cursor:default">No recent files</div>';return}
  el.innerHTML=recentFiles.map(r=>`<div class="fm-recent">📄 ${r.name} <span style="font-size:7px;color:var(--t4)">${r.date}</span></div>`).join("");
}

function markUnsaved(){
  unsavedChanges=true;
  document.getElementById("save-status").innerHTML='<span class="autosave-dot off"></span> Unsaved';
}
function markSaved(){
  unsavedChanges=false;lastSaveTime=Date.now();
  document.getElementById("save-status").innerHTML='<span class="autosave-dot on"></span> Saved just now';
}

// Auto-save every 30s
function startAutosave(){
  if(autosaveInterval)clearInterval(autosaveInterval);
  autosaveInterval=setInterval(()=>{
    if(unsavedChanges&&S.loaded){
      autoSaveProject();
      markSaved();
    }
  },30000);
}

function autoSaveProject(){
  try{
    const data={anns:S.anns,meas:S.meas,punches:S.punches,proj:S.proj.id,scale:S.scale,sUnit:S.sUnit,user:AUTH.currentUser?.email,ts:Date.now()};
    const key=`planreview_${S.proj.id}_autosave`;
    // In production this would go to server; here we use a downloadable approach
    console.log("Auto-saved project data",data);
  }catch(e){}
}

function saveProject(){
  markSaved();
  toast("Project saved","ok");
}

function saveProjectAs(){
  const name=prompt("Save project as:",`${S.proj.id}_review`);
  if(!name)return;
  const data=JSON.stringify({version:"1.0",name,proj:S.proj,anns:S.anns,meas:S.meas,punches:S.punches,team:AUTH.teamMembers,scale:S.scale,sUnit:S.sUnit,user:AUTH.currentUser,ts:Date.now()},null,2);
  downloadFile(data,`${name}.prp`,"application/json");
  markSaved();
  toast(`Saved: ${name}.prp`,"ok");
}

function saveToComputer(){
  if(!S.loaded){toast("No document to save","err");return}
  // Save project file with all annotations
  const data=JSON.stringify({version:"1.0",proj:S.proj,anns:S.anns,meas:S.meas,punches:S.punches,team:AUTH.teamMembers,scale:S.scale,sUnit:S.sUnit,user:AUTH.currentUser?.email,ts:Date.now()},null,2);
  downloadFile(data,`${S.proj.id}_planreview.prp`,"application/json");
  markSaved();
  toast("Project file saved to computer","ok");
}

function exportMarkupsJSON(){
  const data=JSON.stringify({anns:S.anns,meas:S.meas,punches:S.punches,scale:S.scale,sUnit:S.sUnit,exported:new Date().toISOString(),by:AUTH.currentUser?getFullName(AUTH.currentUser):"Unknown"},null,2);
  downloadFile(data,`${S.proj.id}_markups.json`,"application/json");
  toast("Markups exported as JSON","ok");
}

function importMarkupsJSON(){document.getElementById("fi-json").click()}
document.getElementById("fi-json")?.addEventListener("change",async e=>{
  const f=e.target.files[0];if(!f)return;
  try{
    const txt=await f.text();const data=JSON.parse(txt);
    if(data.anns){Object.keys(data.anns).forEach(k=>{if(!S.anns[k])S.anns[k]=[];S.anns[k]=S.anns[k].concat(data.anns[k])})}
    if(data.meas){Object.keys(data.meas).forEach(k=>{if(!S.meas[k])S.meas[k]=[];S.meas[k]=S.meas[k].concat(data.meas[k])})}
    if(data.punches)S.punches=S.punches.concat(data.punches);
    if(data.scale&&!S.scale){S.scale=data.scale;S.sUnit=data.sUnit||"ft"}
    redrawMarkup();renderPanel();
    toast(`Imported markups from ${f.name}`,"ok");
  }catch(e){toast("Invalid JSON file","err")}
});

function exportSummaryCSV(){
  let csv="Sheet,Status,Comments,Discipline,Reviewer Notes\n";
  SHT.forEach(sh=>{
    const d=DISC.find(dd=>dd.id===sh.d);
    const anns=getAnns(1);
    csv+=`"${sh.id} - ${sh.n}","${sh.s}",${sh.c},"${d?.l||""}",""\n`;
  });
  csv+="\nPunch Items\nID,Description,Page,Status,Date\n";
  S.punches.forEach(p=>{csv+=`${p.id},"${p.txt}",${p.page},${p.done?"Complete":"Open"},${p.date}\n`});
  downloadFile(csv,`${S.proj.id}_review_summary.csv`,"text/csv");
  toast("Review summary CSV exported","ok");
}

function printSheet(){
  if(!S.loaded){toast("No document loaded","err");return}
  const cv=document.getElementById("pc"),mcv=document.getElementById("mc");
  const merged=document.createElement("canvas");merged.width=cv.width;merged.height=cv.height;
  const mctx=merged.getContext("2d");mctx.drawImage(cv,0,0);mctx.drawImage(mcv,0,0);
  const win=window.open("","_blank");
  win.document.write(`<html><head><title>Print - ${S.proj.id}</title><style>body{margin:0;display:flex;justify-content:center}img{max-width:100%;height:auto}@media print{img{max-width:100%;page-break-inside:avoid}}</style></head><body><img src="${merged.toDataURL("image/png")}"></body></html>`);
  win.document.close();
  setTimeout(()=>win.print(),500);
}

function downloadFile(data,filename,type){
  const blob=new Blob([data],{type});
  const url=URL.createObjectURL(blob);
  const a=document.createElement("a");a.href=url;a.download=filename;
  document.body.appendChild(a);a.click();document.body.removeChild(a);
  URL.revokeObjectURL(url);
}

// Keyboard shortcuts for file ops
document.addEventListener("keydown",e=>{
  if((e.ctrlKey||e.metaKey)&&e.key==="o"){e.preventDefault();openFile()}
  if((e.ctrlKey||e.metaKey)&&e.key==="s"&&!e.shiftKey){e.preventDefault();saveProject()}
  if((e.ctrlKey||e.metaKey)&&e.shiftKey&&e.key==="S"){e.preventDefault();saveToComputer()}
  if((e.ctrlKey||e.metaKey)&&e.key==="e"){e.preventDefault();exportPDF()}
  if((e.ctrlKey||e.metaKey)&&e.key==="p"){e.preventDefault();printSheet()}
});

/* ===== VIDEO CHAT ===== */
let vcState={active:false,mini:false,mic:true,cam:true,screen:false,markup:false,localStream:null,messages:[]};

function toggleVideoChat(){
  vcState.active=!vcState.active;
  document.getElementById("vc-window").classList.toggle("show",vcState.active);
  document.getElementById("vc-active-dot").style.display=vcState.active?"block":"none";
  if(vcState.active){startLocalCamera();toast("Video session started","ok")}
  else{stopLocalCamera();toast("Video session ended","info")}
}

function toggleVCMini(){
  vcState.mini=!vcState.mini;
  document.getElementById("vc-window").classList.toggle("mini",vcState.mini);
  if(vcState.mini&&vcState.localStream){
    // Show mini preview
    const mp=document.getElementById("vc-mini-preview");
    let v=mp.querySelector("video");
    if(!v){v=document.createElement("video");v.autoplay=true;v.muted=true;v.playsInline=true;mp.appendChild(v)}
    v.srcObject=vcState.localStream;
  }
}

async function startLocalCamera(){
  try{
    const stream=await navigator.mediaDevices.getUserMedia({video:{width:320,height:240,facingMode:"user"},audio:true});
    vcState.localStream=stream;
    document.getElementById("vc-local-video").srcObject=stream;
    document.getElementById("vc-local-label").textContent=AUTH.currentUser?AUTH.currentUser.first:"You";
    // Simulate remote participants joining
    setTimeout(()=>simulateRemoteJoin(1,"Sarah C."),1500);
    setTimeout(()=>simulateRemoteJoin(2,"Mike T."),3000);
  }catch(e){
    console.log("Camera not available, using avatar placeholder");
    toast("Camera access not available — using avatar mode","info");
    // Still show the UI, just without live video
    document.getElementById("vc-local-video").style.display="none";
    const ph=document.createElement("div");ph.className="vc-avatar-placeholder";
    const av=document.createElement("div");av.className="av";
    av.style.background=AUTH.currentUser?.color||"var(--ac)";
    av.textContent=AUTH.currentUser?getInitials(AUTH.currentUser):"?";
    ph.appendChild(av);
    document.getElementById("vc-local-feed").insertBefore(ph,document.getElementById("vc-local-label"));
    setTimeout(()=>simulateRemoteJoin(1,"Sarah C."),1500);
  }
}

function stopLocalCamera(){
  if(vcState.localStream){vcState.localStream.getTracks().forEach(t=>t.stop());vcState.localStream=null}
  document.getElementById("vc-local-video").srcObject=null;
}

function simulateRemoteJoin(n,name){
  if(!vcState.active)return;
  // Animate remote feeds with a subtle color pattern
  const canvas=document.getElementById("vc-sim-"+n);
  if(!canvas)return;
  const parent=canvas.parentElement;
  const placeholder=parent.querySelector(".vc-avatar-placeholder");
  // Keep avatar placeholder for simulated users
  toast(`${name} joined the session`,"info");
}

function toggleVCMic(){
  vcState.mic=!vcState.mic;
  document.getElementById("vc-mic").className="vc-btn "+(vcState.mic?"on":"off");
  if(vcState.localStream){vcState.localStream.getAudioTracks().forEach(t=>t.enabled=vcState.mic)}
  toast(vcState.mic?"Mic on":"Mic muted","info");
}

function toggleVCCam(){
  vcState.cam=!vcState.cam;
  document.getElementById("vc-cam").className="vc-btn "+(vcState.cam?"on":"off");
  if(vcState.localStream){vcState.localStream.getVideoTracks().forEach(t=>t.enabled=vcState.cam)}
  toast(vcState.cam?"Camera on":"Camera off","info");
}

function toggleVCScreen(){
  vcState.screen=!vcState.screen;
  document.getElementById("vc-screen").className="vc-btn "+(vcState.screen?"on":"off");
  if(vcState.screen){
    // Request screen share
    navigator.mediaDevices.getDisplayMedia?.({video:true}).then(stream=>{
      document.getElementById("vc-local-video").srcObject=stream;
      stream.getVideoTracks()[0].onended=()=>{
        vcState.screen=false;
        document.getElementById("vc-screen").className="vc-btn on";
        if(vcState.localStream)document.getElementById("vc-local-video").srcObject=vcState.localStream;
      };
      toast("Screen sharing started","ok");
    }).catch(()=>{vcState.screen=false;document.getElementById("vc-screen").className="vc-btn on";toast("Screen share cancelled","info")});
  }else{
    if(vcState.localStream)document.getElementById("vc-local-video").srcObject=vcState.localStream;
  }
}

function toggleVCMarkup(){
  vcState.markup=!vcState.markup;
  document.getElementById("vc-markup").className="vc-btn "+(vcState.markup?"on":"off");
  toast(vcState.markup?"Sharing markup view with team":"Stopped sharing markup view","info");
}

function endVideoCall(){
  vcState.active=false;vcState.mini=false;
  document.getElementById("vc-window").classList.remove("show","mini");
  document.getElementById("vc-active-dot").style.display="none";
  stopLocalCamera();
  toast("Video session ended","info");
}

function sendVCChat(){
  const input=document.getElementById("vc-chat-text");
  const msg=input.value.trim();if(!msg)return;
  const name=AUTH.currentUser?AUTH.currentUser.first:"You";
  vcState.messages.push({user:name,text:msg});
  const chat=document.getElementById("vc-chat");
  chat.innerHTML+=`<div class="vc-msg"><b>${name}</b> <span>${msg}</span></div>`;
  chat.scrollTop=chat.scrollHeight;
  input.value="";
  // Simulate response
  if(vcState.messages.length%3===0){
    setTimeout(()=>{
      const responses=["Good catch, I see it now","Can you place a cloud markup there?","Let me check the code reference","Agreed, that needs revision","I'll update my review comments"];
      const resp=responses[Math.floor(Math.random()*responses.length)];
      chat.innerHTML+=`<div class="vc-msg"><b>Sarah C.</b> <span>${resp}</span></div>`;
      chat.scrollTop=chat.scrollHeight;
    },2000);
  }
}

// Make VC window draggable
(function(){
  const head=document.getElementById("vc-head");
  const win=document.getElementById("vc-window");
  let dragging=false,dx=0,dy=0;
  head?.addEventListener("mousedown",e=>{if(e.target.closest(".vc-hbtn"))return;dragging=true;dx=e.clientX-win.offsetLeft;dy=e.clientY-win.offsetTop;e.preventDefault()});
  document.addEventListener("mousemove",e=>{if(!dragging)return;win.style.left=(e.clientX-dx)+"px";win.style.top=(e.clientY-dy)+"px";win.style.right="auto";win.style.bottom="auto"});
  document.addEventListener("mouseup",()=>dragging=false);
})();


/* ===== THEME MANAGEMENT ===== */
let currentTheme="dark";

function toggleTheme(){
  currentTheme=currentTheme==="dark"?"light":"dark";
  applyTheme(currentTheme);
}

function applyTheme(theme){
  currentTheme=theme;
  document.body.classList.toggle("light",theme==="light");
  var tog=document.getElementById("theme-toggle");
  if(tog)tog.classList.toggle("on",theme==="light");
  var lbl=document.getElementById("theme-icon-label");
  if(lbl)lbl.textContent=theme==="light"?"☀️":"🌙";
  if(typeof S!=='undefined'&&S.loaded){drawRulers();if(S.showGrid)redrawMarkup()}
}

document.addEventListener('keydown',function(e){
  if((e.ctrlKey||e.metaKey)&&e.shiftKey&&e.key==='T'){e.preventDefault();toggleTheme()}
});

/* ===== INIT ===== */
function init(){
  renderQuickUsers();renderRecentFiles();
  renderTools();buildFlyouts();renderSheetTabs();renderPanel();renderProjDD();drawRulers();
  startAutosave();
  document.getElementById("propbar").style.display="none";
}
init();
</script>
</body>
</html>

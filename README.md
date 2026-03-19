<!DOCTYPE html>
<html lang="nl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Padel Opstelling</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:ital,wght@0,400;0,500;0,600;0,700;1,400&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  body {
    font-family: 'DM Sans', sans-serif;
    background: #f5f4f0;
    min-height: 100vh;
    padding: 1.5rem 1rem 3rem;
    color: #1a1a18;
  }
  .wrap { max-width: 720px; margin: 0 auto; }

  h1 { font-size: 22px; font-weight: 700; margin-bottom: 2px; }
  .subtext { font-size: 13px; color: #73726c; margin-bottom: 22px; }

  .section-label {
    font-size: 11px; font-weight: 700; text-transform: uppercase;
    letter-spacing: .07em; color: #73726c; margin-bottom: 8px; display: block;
  }

  /* Player grid */
  .player-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 8px;
    margin-bottom: 16px;
  }
  .player-btn {
    border: 1.5px solid #d3d1c7;
    border-radius: 9px;
    padding: 9px 11px;
    background: #fff;
    cursor: pointer;
    text-align: left;
    transition: all .12s;
    font-family: inherit;
  }
  .player-btn:hover { border-color: #b4b2a9; }
  .player-btn.sel-p200 { border: 2px solid #EF9F27; background: #FAEEDA; }
  .player-btn.sel-p100 { border: 2px solid #1D9E75; background: #E1F5EE; }
  .player-btn .pname {
    font-size: 14px; font-weight: 700; display: block; margin-bottom: 2px; color: #1a1a18;
  }
  .player-btn.sel-p200 .pname { color: #633806; }
  .player-btn.sel-p100 .pname { color: #085041; }
  .player-btn .plevel { font-size: 11px; font-weight: 500; }
  .player-btn.sel-p200 .plevel { color: #854F0B; }
  .player-btn.sel-p100 .plevel { color: #0F6E56; }
  .player-btn:not(.sel-p200):not(.sel-p100) .plevel { color: #888780; }

  /* Buttons row */
  .btn-row { display: flex; align-items: center; gap: 8px; flex-wrap: wrap; margin-bottom: 4px; }
  .btn-gen {
    padding: 10px 24px; border-radius: 9px; border: none;
    background: #1a1a18; color: #fff;
    font-size: 14px; font-weight: 700; cursor: pointer; font-family: inherit;
    transition: opacity .12s;
  }
  .btn-gen:disabled { background: #d3d1c7; color: #888780; cursor: not-allowed; }
  .btn-regen {
    padding: 10px 16px; border-radius: 9px;
    border: 1.5px solid #d3d1c7; background: transparent;
    color: #1a1a18; font-size: 13px; font-weight: 500;
    cursor: pointer; font-family: inherit;
    transition: background .12s;
  }
  .btn-regen:hover { background: #ece9e3; }
  .btn-share {
    padding: 10px 16px; border-radius: 9px;
    border: 1.5px solid #d3d1c7; background: transparent;
    color: #1a1a18; font-size: 13px; font-weight: 500;
    cursor: pointer; font-family: inherit;
    transition: background .12s;
    display: flex; align-items: center; gap: 5px;
  }
  .btn-share:hover { background: #ece9e3; }
  .needs-more { font-size: 12px; color: #A32D2D; }

  /* Error */
  .error-box {
    background: #FCEBEB; color: #A32D2D;
    border-radius: 9px; padding: 10px 14px;
    font-size: 13px; margin-top: 14px;
    border: 0.5px solid #F09595; line-height: 1.5;
  }

  /* Result */
  .result { margin-top: 20px; }
  .rot-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
    margin-bottom: 18px;
  }
  .rot-card {
    border: 0.5px solid #d3d1c7;
    border-radius: 10px;
    overflow: hidden;
    background: #fff;
  }
  .rot-head {
    background: #f0ede8;
    padding: 8px 12px;
    border-bottom: 0.5px solid #d3d1c7;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .rot-head-label {
    font-size: 10px; font-weight: 700;
    text-transform: uppercase; letter-spacing: .06em; color: #73726c;
  }
  .pts-pill {
    font-size: 11px; font-weight: 700;
    padding: 2px 8px; border-radius: 4px;
    background: #E1F5EE; color: #085041;
  }
  .rot-body { padding: 10px 12px; }
  .match-label {
    font-size: 10px; color: #aaa8a0; margin-bottom: 4px;
    font-weight: 600; text-transform: uppercase; letter-spacing: .04em;
  }
  .duo { display: flex; gap: 6px; flex-wrap: wrap; margin-bottom: 10px; }
  .duo:last-child { margin-bottom: 0; }
  .tag {
    display: inline-flex; align-items: center; gap: 3px;
    padding: 4px 10px; border-radius: 6px;
    font-size: 12px; font-weight: 700;
  }
  .tag-p200 { background: #FAEEDA; color: #633806; }
  .tag-p100 { background: #E1F5EE; color: #085041; }
  .tag-sub-p200 { background: #FAEEDA; color: #633806; border: 1.5px dashed #EF9F27; font-style: italic; }
  .tag-sub-p100 { background: #E1F5EE; color: #085041; border: 1.5px dashed #1D9E75; font-style: italic; }
  .tag .sub-arrow { opacity: .6; font-size: 10px; }

  /* Count grid */
  .count-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(80px, 1fr));
    gap: 7px;
    margin-top: 8px;
  }
  .count-card {
    border: 0.5px solid #d3d1c7;
    border-radius: 8px; padding: 8px;
    text-align: center; background: #fff;
  }
  .count-name { font-size: 12px; font-weight: 700; margin-bottom: 4px; color: #1a1a18; }
  .count-num { font-size: 26px; font-weight: 800; line-height: 1; }
  .count-num-3 { color: #1D9E75; }
  .count-num-2 { color: #185FA5; }
  .count-num-1 { color: #854F0B; }
  .count-num-0 { color: #888780; }
  .count-level { font-size: 10px; color: #aaa8a0; margin-top: 2px; }

  .legend { font-size: 11px; color: #73726c; margin-top: 10px; display: flex; align-items: center; gap: 6px; }
  .legend-tag { font-style: italic; border: 1.5px dashed #aaa; border-radius: 4px; padding: 1px 6px; }

  /* Share toast */
  .toast {
    position: fixed; bottom: 24px; left: 50%; transform: translateX(-50%);
    background: #1a1a18; color: #fff; border-radius: 20px;
    padding: 10px 20px; font-size: 13px; font-weight: 500;
    opacity: 0; transition: opacity .3s; pointer-events: none; white-space: nowrap;
    z-index: 999;
  }
  .toast.show { opacity: 1; }

  /* Share panel */
  .share-panel {
    background: #fff; border: 0.5px solid #d3d1c7; border-radius: 10px;
    padding: 14px 16px; margin-top: 14px; display: none;
  }
  .share-panel.open { display: block; }
  .share-panel h3 { font-size: 14px; font-weight: 700; margin-bottom: 8px; }
  .share-options { display: flex; gap: 8px; flex-wrap: wrap; }
  .share-opt-btn {
    padding: 8px 14px; border-radius: 8px; border: 1.5px solid #d3d1c7;
    background: #f5f4f0; cursor: pointer; font-family: inherit;
    font-size: 13px; font-weight: 600; color: #1a1a18;
    display: flex; align-items: center; gap: 5px;
    transition: background .12s;
  }
  .share-opt-btn:hover { background: #ece9e3; }

  @media (max-width: 480px) {
    .player-grid { grid-template-columns: repeat(3, 1fr); gap: 6px; }
    .rot-grid { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>
<div class="wrap">
  <h1>🎾 Padel opstelling</h1>
  <p class="subtext">Selecteer wie aanwezig is — de app genereert een geldige opstelling (max 500 pts/rotatie)</p>

  <span class="section-label" id="presence-label">Aanwezig (0)</span>
  <div class="player-grid" id="player-grid"></div>

  <div class="btn-row">
    <button class="btn-gen" id="btn-gen" disabled onclick="generate()">Genereer opstelling</button>
    <button class="btn-regen" id="btn-regen" style="display:none" onclick="generate()">↻ Andere</button>
    <button class="btn-share" id="btn-share" style="display:none" onclick="toggleShare()">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><circle cx="18" cy="5" r="3"/><circle cx="6" cy="12" r="3"/><circle cx="18" cy="19" r="3"/><line x1="8.59" y1="13.51" x2="15.42" y2="17.49"/><line x1="15.41" y1="6.51" x2="8.59" y2="10.49"/></svg>
      Delen
    </button>
    <span class="needs-more" id="needs-more"></span>
  </div>

  <div class="share-panel" id="share-panel">
    <h3>Opstelling delen</h3>
    <div class="share-options">
      <button class="share-opt-btn" onclick="shareWhatsApp()">📱 WhatsApp</button>
      <button class="share-opt-btn" onclick="copyText()">📋 Kopieer tekst</button>
      <button class="share-opt-btn" onclick="shareNative()" id="btn-native" style="display:none">🔗 Delen...</button>
    </div>
  </div>

  <div class="error-box" id="error-box" style="display:none"></div>
  <div class="result" id="result" style="display:none">
    <span class="section-label">Opstelling</span>
    <div class="rot-grid" id="rot-grid"></div>
    <span class="section-label">Matchen per speler</span>
    <div class="count-grid" id="count-grid"></div>
    <div class="legend">
      <span class="legend-tag">naam ↩</span>
      <span>= wisselspeler (start pas vanaf rotatie 2)</span>
    </div>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
const PLAYERS = [
  {id:"charles",name:"Charles",level:"P200",pts:200},
  {id:"mathis",  name:"Mathis", level:"P200",pts:200},
  {id:"berend",  name:"Berend", level:"P100",pts:100},
  {id:"paolo",   name:"Paolo",  level:"P100",pts:100},
  {id:"jorre",   name:"Jorre",  level:"P100",pts:100},
  {id:"bizzy",   name:"Bizzy",  level:"P100",pts:100},
  {id:"braet",   name:"Braet",  level:"P100",pts:100},
  {id:"buys",    name:"Buys",   level:"P100",pts:100},
  {id:"auguy",   name:"Auguy",  level:"P100",pts:100},
];

let selected = new Set();
let currentLineup = null;

function shuffle(arr){const a=[...arr];for(let i=a.length-1;i>0;i--){const j=Math.floor(Math.random()*(i+1));[a[i],a[j]]=[a[j],a[i]];}return a;}

// Build player buttons
const grid = document.getElementById("player-grid");
PLAYERS.forEach(p => {
  const btn = document.createElement("button");
  btn.className = "player-btn";
  btn.id = "pbtn-" + p.id;
  btn.innerHTML = `<span class="pname">${p.name}</span><span class="plevel">${p.level} · ${p.pts} pts</span>`;
  btn.onclick = () => toggle(p);
  grid.appendChild(btn);
});

function toggle(p) {
  selected.has(p.id) ? selected.delete(p.id) : selected.add(p.id);
  const btn = document.getElementById("pbtn-" + p.id);
  btn.className = "player-btn" + (selected.has(p.id) ? ` sel-${p.level.toLowerCase()}` : "");
  updateUI();
  document.getElementById("result").style.display = "none";
  document.getElementById("error-box").style.display = "none";
  document.getElementById("btn-regen").style.display = "none";
  document.getElementById("btn-share").style.display = "none";
  document.getElementById("share-panel").classList.remove("open");
  currentLineup = null;
}

function updateUI() {
  const n = selected.size;
  document.getElementById("presence-label").textContent = `Aanwezig (${n})`;
  const canGen = n >= 4 && n <= 8;
  document.getElementById("btn-gen").disabled = !canGen;
  document.getElementById("needs-more").textContent = (n > 0 && n < 4) ? `Nog ${4 - n} nodig` : "";
}

function computeLineup(sel) {
  const p200s = shuffle(sel.filter(p=>p.level==="P200"));
  const p100s = shuffle(sel.filter(p=>p.level==="P100"));
  if(sel.length===4 && p200s.length===2) return {error:"Met 4 spelers en 2×P200 is een geldige opstelling onmogelijk (600 pts > max 500). Voeg een extra P100 toe of laat 1 P200 thuis."};
  let base, subs;
  if(p200s.length===0){base=p100s.slice(0,4);subs=p100s.slice(4);}
  else if(p200s.length===1){base=[p200s[0],...p100s.slice(0,3)];subs=p100s.slice(3);}
  else{base=[p200s[0],...p100s.slice(0,3)];subs=[p200s[1],...p100s.slice(3)];}
  const rotPlayers=[[...base],[...base],[...base]];
  const nsr2=Math.ceil(subs.length/2);
  function insertSub(ri,sub){
    const rot=[...rotPlayers[ri]];let idx;
    if(sub.level==="P200"){idx=rot.findIndex(p=>p.level==="P200");if(idx===-1)idx=rot.length-1;}
    else{for(let i=rot.length-1;i>=0;i--){if(rot[i].level==="P100"){idx=i;break;}}if(idx===undefined)idx=rot.length-1;}
    rot[idx]=sub;rotPlayers[ri]=rot;
  }
  subs.forEach((s,i)=>insertSub(i<nsr2?1:2,s));
  const usedPairs=new Set();
  const rots=[];
  for(let r=0;r<3;r++){
    const rot=rotPlayers[r];
    const total=rot.reduce((s,p)=>s+p.pts,0);
    if(total<250||total>500) return {error:`Rotatie ${r+1}: ${total} pts buiten bereik (250–500).`};
    const [a,b,c,d]=rot;
    const opts=shuffle([[[a,b],[c,d]],[[a,c],[b,d]],[[a,d],[b,c]]]);
    let chosen=null;
    for(const o of opts){
      const k1=[o[0][0].id,o[0][1].id].sort().join("|");
      const k2=[o[1][0].id,o[1][1].id].sort().join("|");
      if(!usedPairs.has(k1)&&!usedPairs.has(k2)){chosen=o;break;}
    }
    if(!chosen)chosen=opts[0];
    usedPairs.add([chosen[0][0].id,chosen[0][1].id].sort().join("|"));
    usedPairs.add([chosen[1][0].id,chosen[1][1].id].sort().join("|"));
    const d1=chosen[0].reduce((s,p)=>s+p.pts,0);
    const d2=chosen[1].reduce((s,p)=>s+p.pts,0);
    const [m1,m2]=d1>=d2?[chosen[0],chosen[1]]:[chosen[1],chosen[0]];
    rots.push({players:rot,match1:m1,match2:m2,total,nums:[r*2+1,r*2+2]});
  }
  const counts={};sel.forEach(p=>{counts[p.id]=0;});
  rots.forEach(r=>r.players.forEach(p=>{counts[p.id]++;}));
  return{rotations:rots,counts,baseIds:new Set(base.map(p=>p.id))};
}

function generate() {
  const sel = PLAYERS.filter(p=>selected.has(p.id));
  const result = computeLineup(sel);
  currentLineup = result;

  document.getElementById("error-box").style.display = "none";
  document.getElementById("result").style.display = "none";
  document.getElementById("share-panel").classList.remove("open");

  if(result.error){
    document.getElementById("error-box").textContent = "⚠ " + result.error;
    document.getElementById("error-box").style.display = "block";
    document.getElementById("btn-regen").style.display = "none";
    document.getElementById("btn-share").style.display = "none";
    return;
  }

  // Render rotations
  const rotGrid = document.getElementById("rot-grid");
  rotGrid.innerHTML = "";
  result.rotations.forEach((rot, r) => {
    const card = document.createElement("div");
    card.className = "rot-card";
    const matchesHtml = [rot.match1, rot.match2].map((duo, mi) => {
      const tags = duo.map(p => {
        const isSub = !result.baseIds.has(p.id);
        const cls = isSub ? `tag tag-sub-${p.level.toLowerCase()}` : `tag tag-${p.level.toLowerCase()}`;
        return `<span class="${cls}">${p.name}${isSub?'<span class="sub-arrow"> ↩</span>':''}</span>`;
      }).join("");
      return `<div class="match-label">Match ${rot.nums[mi]}</div><div class="duo">${tags}</div>`;
    }).join("");
    card.innerHTML = `
      <div class="rot-head">
        <span class="rot-head-label">Rotatie ${r+1} · ${rot.nums[0]} & ${rot.nums[1]}</span>
        <span class="pts-pill">${rot.total} pts ✓</span>
      </div>
      <div class="rot-body">${matchesHtml}</div>`;
    rotGrid.appendChild(card);
  });

  // Render counts
  const countGrid = document.getElementById("count-grid");
  countGrid.innerHTML = "";
  sel.forEach(p => {
    const n = result.counts[p.id];
    const card = document.createElement("div");
    card.className = "count-card";
    card.innerHTML = `<div class="count-name">${p.name}</div><div class="count-num count-num-${n}">${n}</div><div class="count-level">${p.level}</div>`;
    countGrid.appendChild(card);
  });

  document.getElementById("result").style.display = "block";
  document.getElementById("btn-regen").style.display = "inline-flex";
  document.getElementById("btn-share").style.display = "inline-flex";
  if(navigator.share) document.getElementById("btn-native").style.display = "inline-flex";
}

function buildShareText() {
  if(!currentLineup || currentLineup.error) return "";
  const sel = PLAYERS.filter(p=>selected.has(p.id));
  let txt = `🎾 Padel opstelling — ${sel.length} spelers\n\n`;
  currentLineup.rotations.forEach((rot,r) => {
    txt += `Rotatie ${r+1} (${rot.total} pts)\n`;
    txt += `  Match ${rot.nums[0]}: ${rot.match1.map(p=>p.name).join(" & ")}\n`;
    txt += `  Match ${rot.nums[1]}: ${rot.match2.map(p=>p.name).join(" & ")}\n\n`;
  });
  txt += "Matchen per speler:\n";
  sel.forEach(p => { txt += `  ${p.name}: ${currentLineup.counts[p.id]}x\n`; });
  return txt.trim();
}

function toggleShare() {
  const panel = document.getElementById("share-panel");
  panel.classList.toggle("open");
}

function shareWhatsApp() {
  const text = buildShareText();
  window.open("https://wa.me/?text=" + encodeURIComponent(text), "_blank");
}

function copyText() {
  const text = buildShareText();
  navigator.clipboard.writeText(text).then(() => showToast("✓ Gekopieerd!")).catch(() => {
    const ta = document.createElement("textarea");
    ta.value = text; document.body.appendChild(ta); ta.select();
    document.execCommand("copy"); document.body.removeChild(ta);
    showToast("✓ Gekopieerd!");
  });
}

function shareNative() {
  const text = buildShareText();
  navigator.share({title:"Padel opstelling", text}).catch(()=>{});
}

function showToast(msg) {
  const t = document.getElementById("toast");
  t.textContent = msg; t.classList.add("show");
  setTimeout(()=>t.classList.remove("show"), 2200);
}
</script>
</body>
</html>

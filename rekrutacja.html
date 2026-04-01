// ── MAP MODULE ──
const MAP_POI = [
  { id:'base',   x:.42, y:.54, color:'#2979ff', name:'Stacja 114 — MD HQ',       desc:'Główna baza Metropolitan Division. Punkt dowodzenia i zaplecze logistyczne dla wszystkich sekcji jednostki.',                        tags:['BAZA'],             zone:'downtown' },
  { id:'swat1',  x:.45, y:.59, color:'#ff4d4d', name:'OP HARBOR LOCK',            desc:'Szturm SWAT na magazyny Elysian Island. Neutralizacja uzbrojonego gangu, zabezpieczono nielegalną broń.',                             tags:['SWAT','2026'],      zone:'elysian'  },
  { id:'air1',   x:.38, y:.37, color:'#2dd4bf', name:'Air Base — Vinewood',       desc:'Nocna baza Air Support Division podczas operacji obserwacyjnej nad Vinewood Hills.',                                                    tags:['AIR SUPPORT'],      zone:'vinewood' },
  { id:'k9a',    x:.44, y:.73, color:'#c8a84b', name:'Przeszukanie Davis Quartz', desc:'K-9 Unit zlokalizował ukryte przejście do składu narkotyków. Zatrzymano 4 osoby.',                                                     tags:['K-9','SWAT'],       zone:'davis'    },
  { id:'det1',   x:.50, y:.66, color:'#ff9a3a', name:'Punkt obserwacyjny',        desc:'Wielotygodniowa obserwacja powiązana z operacją SANDSTORM. Detective Bureau Metro.',                                                    tags:['DETECTIVE'],        zone:'davis'    },
  { id:'air2',   x:.34, y:.67, color:'#c8a84b', name:'LS International — Patrol', desc:'Punkt kontrolny przy LS International Airport. Stały patrol i zabezpieczenie przylotów VIP.',                                          tags:['PATROL'],           zone:'airport'  },
  { id:'sandy',  x:.78, y:.25, color:'#a07fff', name:'Sandy Shores — OP SANDSTORM',desc:'Rejon operacji SANDSTORM. Rozbicie siatki przemytniczej na linii Sandy Shores – Los Santos.',                                          tags:['DETECTIVE','K-9'],  zone:'sandy'    },
  { id:'port',   x:.48, y:.62, color:'#ff4d4d', name:'Port Elysian — Zabezpieczenie',desc:'8-godzinna operacja zabezpieczenia transportu VIP. SWAT i Air Support w pełnej koordynacji.',                                       tags:['SWAT','AIR'],       zone:'elysian'  },
  { id:'chase',  x:.35, y:.52, color:'#2dd4bf', name:'Pościg — Autostrada i-5',  desc:'Air Support koordynował 38-minutowy pościg przez centrum miasta. Sprawca zatrzymany bezpiecznie.',                                      tags:['AIR SUPPORT'],      zone:'downtown' },
  { id:'swat2',  x:.47, y:.48, color:'#ff4d4d', name:'CQB Training Facility',    desc:'Obiekt szkoleniowy SWAT. Regularne ćwiczenia CQB, szturmy na budynki i procedury wejścia — certyfikacja operatorów MD.',               tags:['SWAT','SZKOLENIE'], zone:'downtown' },
];

let activeZone = 'all';
let canvas, ctx;
let animFrame = 0;

function initMap() {
  canvas = document.getElementById('mapCanvas');
  if (!canvas) return;
  ctx = canvas.getContext('2d');
  resizeCanvas();
  window.addEventListener('resize', resizeCanvas);
  canvas.addEventListener('mousemove', onMapHover);
  canvas.addEventListener('click', onMapClick);
  animateMap();
}

function resizeCanvas() {
  const wrap = canvas.parentElement;
  canvas.width  = wrap.clientWidth;
  canvas.height = wrap.clientHeight;
}

function animateMap() {
  animFrame++;
  drawMap();
  requestAnimationFrame(animateMap);
}

function drawMap() {
  if (!ctx) return;
  const W = canvas.width, H = canvas.height;
  ctx.clearRect(0, 0, W, H);

  // BG
  const bg = ctx.createLinearGradient(0, 0, W, H);
  bg.addColorStop(0, '#060810');
  bg.addColorStop(1, '#0b0f18');
  ctx.fillStyle = bg;
  ctx.fillRect(0, 0, W, H);

  // Grid
  ctx.strokeStyle = 'rgba(28,32,48,0.7)';
  ctx.lineWidth = 1;
  for (let x = 0; x < W; x += 40) { ctx.beginPath(); ctx.moveTo(x,0); ctx.lineTo(x,H); ctx.stroke(); }
  for (let y = 0; y < H; y += 40) { ctx.beginPath(); ctx.moveTo(0,y); ctx.lineTo(W,y); ctx.stroke(); }

  // Districts
  drawDistrict(W, H, [[.28,.30],[.55,.28],[.60,.50],[.55,.62],[.45,.68],[.30,.65],[.22,.50]], '#1a2035', 'rgba(41,121,255,0.14)', 'DOWNTOWN LOS SANTOS', 'downtown');
  drawDistrict(W, H, [[.30,.28],[.55,.26],[.60,.14],[.38,.10],[.22,.18]],                    '#101820', 'rgba(122,255,178,0.08)', 'VINEWOOD HILLS',       'vinewood');
  drawDistrict(W, H, [[.40,.60],[.56,.60],[.60,.74],[.48,.80],[.36,.72]],                    '#181210', 'rgba(255,210,0,0.08)',   'ELYSIAN ISLAND',       'elysian');
  drawDistrict(W, H, [[.20,.55],[.38,.56],[.36,.72],[.20,.74]],                              '#12100a', 'rgba(255,154,58,0.1)',   'DAVIS / STRAWBERRY',   'davis');
  drawDistrict(W, H, [[.18,.60],[.32,.60],[.32,.78],[.18,.80]],                              '#101812', 'rgba(200,168,75,0.08)',  'LS INTERNATIONAL',     'airport');
  drawDistrict(W, H, [[.62,.08],[.90,.05],[.92,.44],[.72,.44],[.60,.28]],                    '#0e1218', 'rgba(160,127,255,0.08)', 'SANDY SHORES',         'sandy');

  // Ocean
  ctx.save();
  ctx.fillStyle = 'rgba(4,12,28,0.75)';
  ctx.beginPath();
  ctx.moveTo(W*.55,H*.62); ctx.lineTo(W*.62,H*.74); ctx.lineTo(W*.62,H); ctx.lineTo(0,H); ctx.lineTo(0,H*.62);
  ctx.closePath(); ctx.fill();
  ctx.fillStyle = 'rgba(41,121,255,0.2)';
  ctx.font = `bold ${Math.round(W*.016)}px 'Bebas Neue', sans-serif`;
  ctx.textAlign = 'left';
  ctx.fillText('PACIFIC OCEAN', W*.04, H*.92);
  ctx.restore();

  // Roads
  drawRoad(W, H, [[.42,.30],[.42,.72]], 'rgba(30,42,70,0.9)', 3);
  drawRoad(W, H, [[.22,.50],[.60,.50]], 'rgba(30,42,70,0.9)', 3);
  drawRoad(W, H, [[.30,.28],[.55,.62]], 'rgba(25,35,58,0.7)', 2);
  drawRoad(W, H, [[.55,.28],[.42,.60]], 'rgba(25,35,58,0.7)', 2);
  drawRoad(W, H, [[.42,.40],[.62,.20]], 'rgba(22,32,52,0.6)', 1.5);
  drawRoad(W, H, [[.18,.65],[.55,.65]], 'rgba(22,32,52,0.6)', 1.5);

  // POIs with animated pulse
  const pulse = Math.sin(animFrame * 0.04) * 0.4 + 0.6;
  MAP_POI.forEach(poi => {
    const px = poi.x * W, py = poi.y * H;
    const active = activeZone === 'all' || poi.zone === activeZone;
    ctx.save();
    ctx.globalAlpha = active ? 1 : 0.15;

    // outer glow
    const grd = ctx.createRadialGradient(px,py,0,px,py,26);
    grd.addColorStop(0, poi.color + '40');
    grd.addColorStop(1, 'transparent');
    ctx.fillStyle = grd;
    ctx.beginPath(); ctx.arc(px,py,26,0,Math.PI*2); ctx.fill();

    // pulse ring
    if (active) {
      ctx.strokeStyle = poi.color;
      ctx.lineWidth = 1;
      ctx.globalAlpha = (active ? 0.6 : 0.1) * pulse;
      ctx.beginPath(); ctx.arc(px,py,14 + pulse*4,0,Math.PI*2); ctx.stroke();
    }

    // dot
    ctx.globalAlpha = active ? 1 : 0.15;
    ctx.fillStyle = poi.color;
    ctx.beginPath(); ctx.arc(px,py,6,0,Math.PI*2); ctx.fill();
    ctx.strokeStyle = 'rgba(255,255,255,0.8)';
    ctx.lineWidth = 1.5;
    ctx.stroke();

    ctx.restore();
  });
}

function drawDistrict(W, H, pts, fill, stroke, label, zone) {
  const active = activeZone === 'all' || activeZone === zone;
  ctx.save();
  ctx.globalAlpha = active ? 1 : 0.35;
  ctx.beginPath();
  ctx.moveTo(pts[0][0]*W, pts[0][1]*H);
  pts.slice(1).forEach(p => ctx.lineTo(p[0]*W, p[1]*H));
  ctx.closePath();
  ctx.fillStyle = fill; ctx.fill();
  ctx.strokeStyle = stroke; ctx.lineWidth = 1.5; ctx.stroke();
  if (active) {
    const cx = pts.reduce((s,p) => s+p[0], 0) / pts.length * W;
    const cy = pts.reduce((s,p) => s+p[1], 0) / pts.length * H;
    ctx.fillStyle = 'rgba(184,191,204,0.2)';
    ctx.font = `600 ${Math.round(W*.012)}px 'Barlow Condensed', sans-serif`;
    ctx.textAlign = 'center';
    ctx.fillText(label, cx, cy);
  }
  ctx.restore();
}

function drawRoad(W, H, pts, color, w) {
  ctx.strokeStyle = color; ctx.lineWidth = w;
  ctx.beginPath();
  ctx.moveTo(pts[0][0]*W, pts[0][1]*H);
  pts.slice(1).forEach(p => ctx.lineTo(p[0]*W, p[1]*H));
  ctx.stroke();
}

function onMapHover(e) {
  const r = canvas.getBoundingClientRect();
  const mx = (e.clientX-r.left)/canvas.width, my = (e.clientY-r.top)/canvas.height;
  canvas.style.cursor = MAP_POI.some(p => Math.abs(mx-p.x)<.035 && Math.abs(my-p.y)<.035) ? 'pointer' : 'crosshair';
}

function onMapClick(e) {
  const r = canvas.getBoundingClientRect();
  const mx = (e.clientX-r.left)/canvas.width, my = (e.clientY-r.top)/canvas.height;
  const found = MAP_POI.find(p => Math.abs(mx-p.x)<.04 && Math.abs(my-p.y)<.04);
  const panel = document.getElementById('mapInfoPanel');
  if (found) {
    document.getElementById('mapInfoTitle').textContent = found.name;
    document.getElementById('mapInfoText').textContent  = found.desc;
    document.getElementById('mapInfoTags').innerHTML    = found.tags.map(t => `<span class="tag">${t}</span>`).join(' ');
    document.getElementById('sidebar-poi').innerHTML    = `<strong style="color:var(--white)">${found.name}</strong><br><br>${found.desc}`;
    panel.classList.add('show');
  } else {
    panel.classList.remove('show');
  }
}

function highlightZone(zone, btn) {
  document.querySelectorAll('.map-zone-btn').forEach(b => b.classList.remove('active'));
  btn.classList.add('active');
  activeZone = zone;
}

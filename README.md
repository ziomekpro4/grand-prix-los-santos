// ── SCROLL REVEAL ──
const revealObs = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) e.target.classList.add('visible');
  });
}, { threshold: 0.08 });

function setupReveal() {
  document.querySelectorAll('.op-card, .stat, .step, .gallery-cell, .cmdr-card, .about-row, .reveal').forEach(el => {
    el.classList.add('reveal');
    revealObs.observe(el);
  });
}

// ── OPS FILTER ──
function filterOps(cat, btn) {
  document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
  btn.classList.add('active');
  document.querySelectorAll('.op-card').forEach(c => {
    c.style.display = (cat === 'all' || c.dataset.cat.includes(cat)) ? '' : 'none';
  });
}

// ── LIGHTBOX ──
function openLightbox(src) {
  document.getElementById('lbImg').src = src;
  document.getElementById('lightbox').classList.add('show');
}
function closeLightbox() {
  document.getElementById('lightbox').classList.remove('show');
}

// ── HERO BG ZOOM ──
function initHeroZoom() {
  const bg = document.getElementById('heroBg');
  if (bg) setTimeout(() => bg.classList.add('zoomed'), 100);
}

// ── ACTIVE NAV LINK ──
function setActiveNav() {
  const page = location.pathname.split('/').pop() || 'index.html';
  document.querySelectorAll('.nav-links a').forEach(a => {
    a.classList.toggle('active', a.getAttribute('href') === page);
  });
}

// ── INIT ──
document.addEventListener('DOMContentLoaded', () => {
  setActiveNav();
  setupReveal();
  initHeroZoom();

  // Gallery lightbox
  document.querySelectorAll('.gallery-cell').forEach(cell => {
    cell.addEventListener('click', () => {
      const img = cell.querySelector('img');
      if (img) openLightbox(img.src);
    });
  });

  // Map page
  if (document.getElementById('mapCanvas')) {
    initMap();
    window.addEventListener('resize', () => {
      if (canvas) { resizeCanvas(); }
    });
  }
});

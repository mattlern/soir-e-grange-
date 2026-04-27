/* ============================================================
   LA GRANGE · main.js
   Soirée du 13 Juin 2026
   ============================================================ */

(function () {
  'use strict';

  /* ── ANIMATIONS D'ENTRÉE ───────────────────────────────────── */
  // Déclenche les animations CSS au chargement de la page
  function initEntrance() {
    const elements = document.querySelectorAll('.animate-down, .animate-up');
    // Petit délai pour que le navigateur ait le temps de peindre d'abord
    requestAnimationFrame(function () {
      elements.forEach(function (el) {
        el.classList.add('visible');
      });
    });
  }

  /* ── SCROLL CUE : MASQUER APRÈS SCROLL ─────────────────────── */
  function initScrollCue() {
    var cue = document.querySelector('.scroll-cue');
    if (!cue) return;

    var hidden = false;
    window.addEventListener('scroll', function () {
      if (!hidden && window.scrollY > 80) {
        cue.style.opacity = '0';
        cue.style.transition = 'opacity 0.5s ease';
        hidden = true;
      }
    }, { passive: true });
  }

  /* ── HOVER SPARKLE SUR LES TAGS ────────────────────────────── */
  function initTagHover() {
    var tags = document.querySelectorAll('.tag');
    tags.forEach(function (tag) {
      tag.addEventListener('mouseenter', function () {
        tag.style.setProperty('--tag-glow', '1');
      });
      tag.addEventListener('mouseleave', function () {
        tag.style.setProperty('--tag-glow', '0');
      });
    });
  }

  /* ── COMPTE À REBOURS ──────────────────────────────────────── */
  // Si tu ajoutes un élément <div id="countdown"></div> dans le HTML,
  // il affichera automatiquement le nombre de jours restants.
  function initCountdown() {
    var el = document.getElementById('countdown');
    if (!el) return;

    var target = new Date('2026-06-13T19:30:00');

    function update() {
      var now  = new Date();
      var diff = target - now;

      if (diff <= 0) {
        el.textContent = 'C'est ce soir !';
        return;
      }

      var days    = Math.floor(diff / (1000 * 60 * 60 * 24));
      var hours   = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      var minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
      var seconds = Math.floor((diff % (1000 * 60)) / 1000);

      el.innerHTML =
        '<span class="cd-num">' + days    + '</span><span class="cd-unit">j</span> ' +
        '<span class="cd-num">' + hours   + '</span><span class="cd-unit">h</span> ' +
        '<span class="cd-num">' + minutes + '</span><span class="cd-unit">min</span> ' +
        '<span class="cd-num">' + seconds + '</span><span class="cd-unit">s</span>';

      setTimeout(update, 1000);
    }

    update();
  }

  /* ── REVEAL AU SCROLL (pour les autres pages) ──────────────── */
  function initScrollReveal() {
    var reveals = document.querySelectorAll('.reveal');
    if (!reveals.length) return;

    if ('IntersectionObserver' in window) {
      var observer = new IntersectionObserver(function (entries) {
        entries.forEach(function (entry) {
          if (entry.isIntersecting) {
            entry.target.classList.add('revealed');
            observer.unobserve(entry.target);
          }
        });
      }, { threshold: 0.12 });

      reveals.forEach(function (el) {
        observer.observe(el);
      });
    } else {
      // Fallback : tout révéler d'un coup
      reveals.forEach(function (el) {
        el.classList.add('revealed');
      });
    }
  }

  /* ── NAVIGATION ACTIVE ─────────────────────────────────────── */
  function initActiveNav() {
    var currentPage = window.location.pathname.split('/').pop() || 'index.html';
    var navLinks = document.querySelectorAll('.nav-btn');
    navLinks.forEach(function (link) {
      var href = link.getAttribute('href');
      if (href === currentPage) {
        link.classList.add('nav-btn-active');
      }
    });
  }

  /* ── INIT ──────────────────────────────────────────────────── */
  document.addEventListener('DOMContentLoaded', function () {
    initEntrance();
    initScrollCue();
    initTagHover();
    initCountdown();
    initScrollReveal();
    initActiveNav();
  });

})();

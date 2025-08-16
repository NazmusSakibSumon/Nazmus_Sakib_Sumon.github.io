// Simple tab switcher for Video section
(function () {
  const buttons = document.querySelectorAll('.seg-btn');
  const panels  = {
    tools: document.getElementById('videos-tools'),
    core:  document.getElementById('videos-core')
  };

  function show(which) {
    // buttons
    buttons.forEach(b => {
      const active = b.dataset.target === which;
      b.classList.toggle('active', active);
      b.setAttribute('aria-selected', active ? 'true' : 'false');
    });
    // panels
    Object.entries(panels).forEach(([key, el]) => {
      const active = key === which;
      el.classList.toggle('active', active);
      el.hidden = !active;
    });
  }

  buttons.forEach(b => b.addEventListener('click', () => show(b.dataset.target)));
  show('tools'); // default
})();

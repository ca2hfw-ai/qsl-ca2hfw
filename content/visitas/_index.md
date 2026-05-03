---
title: "Libro de Visitas"
---

# Libro de Visitas

Deja tu saludo aquí.

<script src="https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.29.4/moment.min.js"></script>
<style>
.guestbook-form{background:var(--dark-card);padding:1.5rem;border-radius:12px;border:1px solid rgba(0,240,255,0.15);margin:1.5rem 0}
.guestbook-form h3{color:var(--primary);font-size:1.1rem;margin-bottom:1rem}
.guestbook-field{display:flex;flex-direction:column;gap:0.5rem;margin-bottom:1rem}
.guestbook-field label{color:var(--text-muted);font-size:0.85rem;letter-spacing:1px;text-transform:uppercase}
.guestbook-field input,.guestbook-field textarea{background:var(--dark-secondary);border:1px solid rgba(0,240,255,0.2);border-radius:6px;padding:0.75rem;color:var(--text);font-family:inherit;font-size:0.95rem}
.guestbook-field input:focus,.guestbook-field textarea:focus{outline:none;border-color:var(--primary);box-shadow:0 0 15px rgba(0,240,255,0.2)}
.guestbook-field textarea{min-height:100px;resize:vertical}
.guestbook-submit{background:linear-gradient(135deg,var(--primary),var(--accent));border:none;border-radius:6px;padding:0.75rem 1.5rem;color:#000;font-weight:700;cursor:pointer;text-transform:uppercase;letter-spacing:2px;transition:all 0.3s}
.guestbook-submit:hover{box-shadow:0 0 25px var(--glow-cyan);transform:translateY(-2px)}
.guestbook-msg{text-align:center;padding:0.5rem;font-size:0.9rem;min-height:1.5rem}
.guestbook-list{margin-top:2rem}
.guestbook-entry{background:var(--dark-card);padding:1.25rem;border-radius:10px;border:1px solid rgba(0,240,255,0.1);margin-bottom:1rem}
.guestbook-header{display:flex;justify-content:space-between;align-items:center;margin-bottom:0.5rem}
.guestbook-call{color:var(--primary);font-weight:700;font-family:'Orbitron',monospace;font-size:1.1rem;letter-spacing:2px}
.guestbook-name{color:var(--text-muted);font-size:0.85rem}
.guestbook-date{color:var(--text-muted);font-size:0.8rem;font-family:'Share Tech Mono',monospace}
.guestbook-text{color:var(--text);line-height:1.6}
</style>

<div class="guestbook-form">
  <h3>✦ Deja tu saludo ✦</h3>
  <div class="guestbook-field">
    <label>Indicativo / Callsign</label>
    <input type="text" id="gb-call" placeholder="TU_CALL" maxlength="12">
  </div>
  <div class="guestbook-field">
    <label>Nombre / Name</label>
    <input type="text" id="gb-name" placeholder="Tu nombre" maxlength="50">
  </div>
  <div class="guestbook-field">
    <label>Mensaje / Message</label>
    <textarea id="gb-msg" placeholder="Tu mensaje..." maxlength="500"></textarea>
  </div>
  <button class="guestbook-submit" onclick="guestbookSubmit()">Enviar Saludo</button>
  <div class="guestbook-msg" id="gb-status"></div>
</div>

<div class="guestbook-list" id="guestbook-entries">
  <div class="guestbook-entry">
    <div class="guestbook-header">
      <span class="guestbook-call">LU7DLS</span>
      <span class="guestbook-date">2026-05-03</span>
    </div>
    <div class="guestbook-name">Carlos - Argentina</div>
    <div class="guestbook-text">Excelente contacto en 40m FT8. 73 y gracias por el QSL!</div>
  </div>
  <div class="guestbook-entry">
    <div class="guestbook-header">
      <span class="guestbook-call">W9FTR</span>
      <span class="guestbook-date">2026-05-02</span>
    </div>
    <div class="guestbook-name">Tom - USA</div>
    <div class="guestbook-text">Nice contact on 10m FT8. Looking forward to work you again!</div>
  </div>
</div>

<script>
function guestbookSubmit(){
  var call = document.getElementById('gb-call').value.trim().toUpperCase();
  var name = document.getElementById('gb-name').value.trim();
  var msg = document.getElementById('gb-msg').value.trim();
  var status = document.getElementById('gb-status');
  
  if(!call || !name || !msg){
    status.style.color = '#ff6666';
    status.textContent = 'Por favor completa todos los campos';
    return;
  }
  
  status.style.color = '#00f0ff';
  status.textContent = '¡Gracias! Tu salute ha sido enviado.';
  
  document.getElementById('gb-call').value = '';
  document.getElementById('gb-name').value = '';
  document.getElementById('gb-msg').value = '';
}
</script>

---

*73 de CA2HFW - La Serena, Chile*
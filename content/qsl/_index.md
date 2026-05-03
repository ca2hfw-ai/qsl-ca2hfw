---
title: "QSL Digital"
---

<script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
<style>
*{box-sizing:border-box;margin:0;padding:0}
html,body{width:100%;min-height:100vh;background:#0f0f1a;display:flex;align-items:flex-start;justify-content:center;padding:20px 10px 40px}
#wrap{width:100%;max-width:700px}
h2{font-family:'Orbitron',sans-serif;font-size:clamp(22px,5vw,32px);letter-spacing:5px;color:#ff6347;text-align:center;text-shadow:0 0 20px #dc463280;margin-bottom:4px}
.sub{text-align:center;font-family:'Share Tech Mono',monospace;font-size:10px;letter-spacing:3px;color:#666;margin-bottom:20px;text-transform:uppercase}
.search-row{display:flex;gap:10px;margin-bottom:6px}
#qsl-input{flex:1;background:#ffffff0d;border:1px solid #dc463260;border-radius:6px;color:#fff;font-size:16px;font-weight:bold;padding:10px 14px;letter-spacing:3px;text-transform:uppercase;outline:none;font-family:'Share Tech Mono',monospace}
#qsl-input::placeholder{color:#444;font-weight:normal;letter-spacing:1px}
#qsl-input:focus{border-color:#dc4632;box-shadow:0 0 10px #dc463230}
#qsl-btn{background:#dc4632;border:none;border-radius:6px;color:#fff;font-family:'Share Tech Mono',monospace;font-size:11px;letter-spacing:2px;padding:10px 18px;cursor:pointer;text-transform:uppercase;white-space:nowrap;transition:background .2s}
#qsl-btn:hover{background:#ff5540}
#qsl-btn:disabled{background:#444;cursor:not-allowed}
#qsl-msg{font-family:'Share Tech Mono',monospace;font-size:11px;letter-spacing:1px;color:#666;text-align:center;min-height:18px;margin-bottom:10px}
#qsl-card-wrap{display:none;margin-top:4px}
#qsl-card{position:relative;width:100%;aspect-ratio:14/9;border-radius:10px;overflow:hidden;background:#1a1a2e}
.qc-bg{position:absolute;inset:0;background:linear-gradient(135deg,#1a1a2e 0%,#16213e 50%,#0f0f1a 100%)}
.qc-ov{position:absolute;inset:0;background:linear-gradient(to right,rgba(10,10,20,.92) 0%,rgba(10,10,20,.62) 45%,rgba(10,10,20,.18) 100%),linear-gradient(to top,rgba(10,10,20,.78) 0%,transparent 50%)}
.qc-topbar,.qc-botbar{position:absolute;left:0;right:0;height:5px;background:linear-gradient(to right,#dc4632,#ff7a5a,#dc4632)}
.qc-topbar{top:0}.qc-botbar{bottom:0}
.qc-corner{position:absolute;width:24px;height:24px;border:2px solid #dc4632;opacity:.7}
.qc-tl{top:10px;left:10px;border-right:none;border-bottom:none}
.qc-tr{top:10px;right:10px;border-left:none;border-bottom:none}
.qc-bl{bottom:10px;left:10px;border-right:none;border-top:none}
.qc-br{bottom:10px;right:10px;border-left:none;border-top:none}
.qc-wm{position:absolute;bottom:8px;left:50%;transform:translateX(-50%);font-family:'Orbitron',monospace;font-size:10px;letter-spacing:6px;color:#ffffff08;white-space:nowrap;pointer-events:none}
.qc-left{position:absolute;top:0;left:0;bottom:0;width:56%;padding:5% 4% 4% 6%;display:flex;flex-direction:column;justify-content:space-between}
.qc-call{font-family:'Orbitron',sans-serif;font-size:clamp(24px,4.5vw,44px);font-weight:900;color:#fff;letter-spacing:3px;line-height:1;text-shadow:0 0 20px #dc463280}
.qc-call span{color:#ff6347}
.qc-confirms{font-family:'Share Tech Mono',monospace;font-size:clamp(7px,1.2vw,9px);letter-spacing:3px;color:#ff9080;margin-top:4px;text-transform:uppercase}
.qc-to{font-family:'Orbitron',sans-serif;font-size:clamp(13px,2.2vw,20px);font-weight:700;color:#ffe0d8;letter-spacing:3px;margin-top:3px;text-shadow:0 0 10px #dc463260}
.qc-op{font-size:clamp(9px,1.6vw,13px);color:#e8d8d0;margin-top:5px;font-weight:bold;font-family:'Share Tech Mono',monospace}
.qc-qth{font-size:clamp(8px,1.3vw,11px);color:#b0a0a0;letter-spacing:2px;margin-top:2px;font-family:'Share Tech Mono',monospace}
.qc-table{border-top:1px solid #dc463260;padding-top:8px;margin-top:auto}
.qc-table table{width:100%;border-collapse:collapse;font-family:'Share Tech Mono',monospace;font-size:clamp(7px,1.2vw,10px)}
.qc-table th{color:#ff6347;text-align:left;letter-spacing:2px;padding-bottom:4px;font-weight:400;border-bottom:1px solid #dc463230}
.qc-table td{color:#ffccc0;padding:3px 4px 3px 0;border-bottom:1px solid #ffffff10;letter-spacing:1px;font-weight:bold}
.qc-rst{display:flex;gap:10px;align-items:center;margin-top:6px}
.qc-rl{font-family:'Share Tech Mono',monospace;font-size:clamp(6px,1vw,9px);color:#ff6347;letter-spacing:2px}
.qc-rv{font-family:'Orbitron',monospace;font-size:clamp(13px,2.2vw,20px);font-weight:700;color:#fff;letter-spacing:2px;text-shadow:0 0 10px #dc463260}
.qc-right{position:absolute;top:0;right:0;bottom:0;width:37%;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:10px;padding:4% 3% 4% 2%}
.qc-logo{width:min(54%,110px);aspect-ratio:1;border-radius:50%;border:3px solid #dc463299;overflow:hidden;box-shadow:0 0 20px #dc463230;background:#dc4632}
.qc-logo img{width:100%;height:100%;object-fit:cover;border-radius:50%}
.qc-grid{text-align:center}
.qc-gl{font-family:'Share Tech Mono',monospace;font-size:clamp(6px,1vw,9px);letter-spacing:3px;color:#ff9080;text-transform:uppercase}
.qc-gv{font-family:'Orbitron',monospace;font-size:clamp(13px,2.2vw,17px);font-weight:700;color:#fff;letter-spacing:3px;text-shadow:0 0 10px #dc463260}
.qc-tnx{font-family:'Share Tech Mono',monospace;font-size:clamp(6px,1vw,8px);letter-spacing:2px;color:#a09090;margin-top:2px}
#qsl-dl-row{display:flex;gap:8px;margin-top:12px}
.qsl-dl-btn{flex:1;background:none;border:1px solid #dc463260;color:#ff9080;font-family:'Share Tech Mono',monospace;font-size:10px;letter-spacing:2px;padding:9px;cursor:pointer;border-radius:5px;text-transform:uppercase;transition:all .2s}
.qsl-dl-btn:hover{background:#dc463220;color:#fff;border-color:#dc4632}
#qsl-dl-status{font-family:'Share Tech Mono',monospace;font-size:10px;letter-spacing:1px;color:#80e080;text-align:center;margin-top:6px;min-height:14px}
</style>

<div id="wrap">
  <h2>CA2HFW</h2>
  <p class="sub">✦ Descarga tu tarjeta QSL digital ✦</p>
  <div class="search-row">
    <input id="qsl-input" type="text" placeholder="Ingresa tu indicativo..." maxlength="12" autocomplete="off">
    <button id="qsl-btn" onclick="qslBuscar()" disabled="">Buscar QSO</button>
  </div>
  <p id="qsl-msg" style="color: rgb(255, 144, 128);">⚠ No se pudo cargar la base de datos.</p>

  <div id="qsl-card-wrap">
    <div id="qsl-card">
      <div class="qc-bg"></div>
      <div class="qc-ov"></div>
      <div class="qc-topbar"></div><div class="qc-botbar"></div>
      <div class="qc-corner qc-tl"></div><div class="qc-corner qc-tr"></div>
      <div class="qc-corner qc-bl"></div><div class="qc-corner qc-br"></div>
      <div class="qc-wm">CA2HFW · LA SERENA · CHILE</div>
      <div class="qc-left">
        <div>
          <div class="qc-call"><span>CA</span>2HFW</div>
          <div class="qc-confirms">▸ Confirming QSO with ▸</div>
          <div class="qc-to" id="qc-to">—</div>
          <div class="qc-op">Humberto "Moni" Fuentes</div>
          <div class="qc-qth">La Serena · Chile · FG40</div>
        </div>
        <div>
          <div class="qc-table">
            <table>
              <tbody><tr><th>DATE</th><th>UTC</th><th>BAND</th><th>MODE</th></tr>
              <tr>
                <td id="qc-date">—</td><td id="qc-utc">—</td>
                <td id="qc-band">—</td><td id="qc-mode">—</td>
              </tr>
            </tbody></table>
          </div>
          <div class="qc-rst">
            <div><div class="qc-rl">RST SENT</div><div class="qc-rv" id="qc-rs">—</div></div>
            <div style="color:#dc463240;font-size:18px;margin:0 2px">·</div>
            <div><div class="qc-rl">RST RCVD</div><div class="qc-rv" id="qc-rr">—</div></div>
          </div>
        </div>
      </div>
      <div class="qc-right">
        <div class="qc-logo"></div>
        <div class="qc-grid">
          <div class="qc-gl">Maidenhead Grid</div>
          <div class="qc-gv">FG40</div>
          <div class="qc-tnx">73 · TNX FER QSO · GL DX</div>
        </div>
      </div>
    </div>
    <div id="qsl-dl-row">
      <button class="qsl-dl-btn" onclick="qslDescargar('png')">↓ Descargar PNG</button>
      <button class="qsl-dl-btn" onclick="qslDescargar('jpg')">↓ Descargar JPG</button>
    </div>
    <div id="qsl-dl-status"></div>
  </div>
</div>

<script>
var GITHUB_URL = 'https://raw.githubusercontent.com/ca2hfw-ai/qsl-ca2hfw/main/qsos.json';
var QSO_LOG = [];

fetch(GITHUB_URL + '?t=' + Date.now())
  .then(function(r){ return r.json(); })
  .then(function(data){
    QSO_LOG = Array.isArray(data[0]) ? data[0] : data;
    var msg = document.getElementById('qsl-msg');
    msg.style.color = '#555';
    msg.textContent = 'Base de datos lista · ' + QSO_LOG.length + ' QSO(s) registrados';
    document.getElementById('qsl-btn').disabled = false;
  })
  .catch(function(){
    document.getElementById('qsl-msg').style.color = '#ff9080';
    document.getElementById('qsl-msg').textContent = '⚠ No se pudo cargar la base de datos.';
  });

function qslBuscar(){
  var call = document.getElementById('qsl-input').value.trim().toUpperCase();
  if(!call){ document.getElementById('qsl-msg').textContent='Ingresa un indicativo.'; return; }
  var found = null;
  for(var i = QSO_LOG.length-1; i >= 0; i--){
    if(QSO_LOG[i].to === call){ found = QSO_LOG[i]; break; }
  }
  var msg = document.getElementById('qsl-msg');
  var wrap = document.getElementById('qsl-card-wrap');
  if(found){
    document.getElementById('qc-to').textContent   = found.to;
    document.getElementById('qc-date').textContent = found.date || '—';
    document.getElementById('qc-utc').textContent  = found.utc  || '—';
    document.getElementById('qc-band').textContent = found.band || '—';
    document.getElementById('qc-mode').textContent = found.mode || '—';
    document.getElementById('qc-rs').textContent   = found.rstS || '59';
    document.getElementById('qc-rr').textContent   = found.rstR || '59';
    wrap.style.display = 'block';
    document.getElementById('qsl-dl-status').textContent = '';
    msg.style.color = '#80e080';
    msg.textContent = '✓ QSO confirmado — ¡' + call + ' tienes una QSL de CA2HFW!';
  } else {
    wrap.style.display = 'none';
    msg.style.color = '#ff9080';
    msg.textContent = '✗ No se encontró QSO con ' + call + '. ¡Próximamente en el aire! 73';
  }
}

document.getElementById('qsl-input').addEventListener('keydown', function(e){
  if(e.key === 'Enter') qslBuscar();
  setTimeout(function(){ document.getElementById('qsl-input').value = document.getElementById('qsl-input').value.toUpperCase(); }, 0);
});

function qslDescargar(fmt){
  var st = document.getElementById('qsl-dl-status');
  st.style.color = '#ffccc0'; st.textContent = '⏳ Generando imagen...';
  var card = document.getElementById('qsl-card');
  html2canvas(card, {scale: 1654/card.offsetWidth, useCORS:true, allowTaint:true, backgroundColor:null, logging:false})
    .then(function(canvas){
      var call = document.getElementById('qsl-input').value.trim().toUpperCase() || 'QSL';
      var a = document.createElement('a');
      a.href = canvas.toDataURL(fmt==='jpg'?'image/jpeg':'image/png', 0.95);
      a.download = 'QSL_CA2HFW_' + call + '.' + fmt;
      a.click();
      st.style.color = '#80e080';
      st.textContent = '✓ Descargada: QSL_CA2HFW_' + call + '.' + fmt;
    }).catch(function(){ st.style.color='#e06050'; st.textContent='⚠ Error. Intenta de nuevo.'; });
}
</script>
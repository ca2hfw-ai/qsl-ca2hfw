---
title: "Trabajos de Investigación"
---

# Trabajos de Investigación

Artículos técnicos y experimentos de radioaficionado.

<script>
document.addEventListener('DOMContentLoaded', function() {
  fetch('https://raw.githubusercontent.com/ca2hfw-ai/qsl-ca2hfw/main/public/posts/index.html')
    .then(r => r.text())
    .then(html => {
      var container = document.getElementById('research-list');
      if(!container) return;
    });
});
</script>

## Antenas

<div class="research-card">
<h4>🔹 Dipolo Vertical HF</h4>
<p>Diseño y construcción de antenas dipolo verticals para bandas HF. Optimización para espacio reducido.</p>
<ul>
<li>Frecuencia: 10-40m</li>
<li>SWR: &lt;1.5:1</li>
<li>Material: Aluminum 6063</li>
</ul>
</div>

<div class="research-card">
<h4>🔹 Yagi VHF</h4>
<p>Antena Yagi de 5 elementos para 2m. Ganancia medida: 7.5 dBi.</p>
<ul>
<li>Banda: 144-148 MHz</li>
<li>Frente/Espalda: &gt;15 dB</li>
<li>Conector: N hembra</li>
</ul>
</div>

## Propagación

<div class="research-card">
<h4>🌐FT8 en 10m</h4>
<p>Estudio de propagación en banda de 10m usando FT8. Los mejores horarios para DX.</p>
<ul>
<li>Mejor horario: 12:00-18:00 UTC</li>
<li>Distancia máxima: 12,000 km</li>
<li>Condición: Esporádico-E</li>
</ul>
</div>

<div class="research-card">
<h4>🌐40m Noche</h4>
<p>Propagación nocturna en 40m. Contactos a larga distancia durante la noche.</p>
<ul>
<li>Mejor horario: 00:00-05:00 UTC</li>
<li>Distancia máxima: 8,000 km</li>
<li>Modo: FT8/JS8</li>
</ul>
</div>

## Modos Digitales

<div class="research-card">
<h4>📡 FT8 - Configuración</h4>
<p>Guía de configuración óptima para WSJT-X usando FlexRadio 6600.</p>
<ul>
<li>Ancho de banda: 2.4 kHz</li>
<li>Filtro: 2700 Hz</li>
<li>Pwr: 25W</li>
</ul>
</div>

<style>
.research-card{background:var(--dark-card);padding:1.25rem;border-radius:10px;border:1px solid rgba(0,240,255,0.15);margin-bottom:1rem}
.research-card h4{color:var(--primary);font-size:1.05rem;margin-bottom:0.5rem}
.research-card p{color:var(--text-muted);margin-bottom:0.75rem}
.research-card ul{list-style:none;margin:0;padding-left:1rem}
.research-card li{color:var(--text-muted);font-size:0.9rem;margin-bottom:0.3rem}
.research-card li:before{content:"▸";color:var(--primary);margin-right:0.5rem}
</style>

---

*Próximamente más artículos técnicos...*
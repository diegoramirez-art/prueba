<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tickets Atrasados — Técnicos de Campo</title>
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;500&family=Sora:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg:        #F5F5F2;
    --surface:   #FFFFFF;
    --surface2:  #F0F0EC;
    --border:    #E2E2DC;
    --border2:   #D0D0C8;
    --text:      #1A1A18;
    --text2:     #6A6A64;
    --text3:     #9A9A94;
    --red:       #C2282A;
    --red-bg:    #FDF0F0;
    --red-mid:   #E8AAAA;
    --amber:     #9A5A08;
    --amber-bg:  #FDF6E8;
    --amber-mid: #E8C87A;
    --green:     #1A6E42;
    --green-bg:  #EDF7F2;
    --green-mid: #7ACAA0;
    --accent:    #C2282A;
    --mono:      'IBM Plex Mono', monospace;
    --sans:      'Sora', sans-serif;
  }

  html { font-size: 15px; }
  body {
    font-family: var(--sans);
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    padding: 2rem 1.5rem 3rem;
  }

  /* ── HEADER ── */
  .page-header {
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    margin-bottom: 1.75rem;
    padding-bottom: 1.25rem;
    border-bottom: 1.5px solid var(--border);
  }
  .page-header-left { display: flex; align-items: center; gap: 14px; }
  .accent-bar {
    width: 4px;
    height: 48px;
    background: var(--red);
    border-radius: 2px;
    flex-shrink: 0;
  }
  .page-title { font-size: 1.4rem; font-weight: 600; letter-spacing: -.02em; color: var(--text); }
  .page-sub { font-size: .78rem; color: var(--text2); margin-top: 4px; font-family: var(--mono); }
  .status-pill {
    display: flex; align-items: center; gap: 7px;
    background: var(--red-bg);
    border: 1px solid var(--red-mid);
    border-radius: 20px;
    padding: 6px 14px;
    font-size: .75rem;
    font-weight: 500;
    color: var(--red);
    font-family: var(--mono);
  }
  .pulse {
    width: 8px; height: 8px; border-radius: 50%;
    background: var(--red);
    animation: pulse 1.6s ease-in-out infinite;
  }
  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50%       { opacity: .4; transform: scale(.7); }
  }

  /* ── SUMMARY CARDS ── */
  .summary {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 12px;
    margin-bottom: 1.75rem;
  }
  .s-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 14px 18px;
    position: relative;
    overflow: hidden;
  }
  .s-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 3px;
  }
  .s-card.red::before   { background: var(--red); }
  .s-card.amber::before { background: var(--amber); }
  .s-card.green::before { background: var(--green); }
  .s-card.gray::before  { background: var(--text3); }
  .s-val  { font-size: 2rem; font-weight: 600; letter-spacing: -.03em; line-height: 1; margin-top: 6px; }
  .s-card.red   .s-val { color: var(--red); }
  .s-card.amber .s-val { color: var(--amber); }
  .s-card.green .s-val { color: var(--green); }
  .s-card.gray  .s-val { color: var(--text2); }
  .s-lbl { font-size: .72rem; color: var(--text3); margin-top: 5px; font-family: var(--mono); text-transform: uppercase; letter-spacing: .05em; }

  /* ── TABLE WRAPPER ── */
  .table-wrap {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    overflow: hidden;
  }

  /* ── COL HEADERS ── */
  .col-head {
    display: grid;
    grid-template-columns: 48px 220px 130px 1fr 80px;
    gap: 10px;
    align-items: center;
    padding: 10px 20px;
    background: var(--surface2);
    border-bottom: 1px solid var(--border);
    font-size: .7rem;
    font-family: var(--mono);
    color: var(--text3);
    text-transform: uppercase;
    letter-spacing: .06em;
  }
  .col-head .right { text-align: right; }

  /* ── TECH ROW ── */
  .tech-row {
    border-bottom: 1px solid var(--border);
    transition: background .12s;
  }
  .tech-row:last-child { border-bottom: none; }
  .tech-row.active { background: #FAFAF8; }

  .row-main {
    display: grid;
    grid-template-columns: 48px 220px 130px 1fr 80px;
    gap: 10px;
    align-items: center;
    padding: 13px 20px;
    cursor: pointer;
    user-select: none;
  }
  .row-main:hover { background: var(--surface2); }
  .tech-row.active .row-main { background: var(--surface2); }

  .avatar {
    width: 36px; height: 36px;
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: .7rem; font-weight: 600;
    font-family: var(--mono);
    flex-shrink: 0;
  }

  .name-wrap { display: flex; align-items: center; gap: 8px; }
  .tech-name { font-size: .9rem; font-weight: 500; color: var(--text); }
  .chevron {
    font-size: 1rem; color: var(--text3);
    transition: transform .2s ease;
    line-height: 1;
  }
  .tech-row.active .chevron { transform: rotate(90deg); }

  .badge {
    display: inline-block;
    font-size: .7rem; font-weight: 500;
    padding: 4px 10px;
    border-radius: 20px;
    font-family: var(--mono);
    white-space: nowrap;
  }
  .badge-red   { background: var(--red-bg);   color: var(--red);   border: 1px solid var(--red-mid); }
  .badge-amber { background: var(--amber-bg); color: var(--amber); border: 1px solid var(--amber-mid); }
  .badge-green { background: var(--green-bg); color: var(--green); border: 1px solid var(--green-mid); }

  .bar-track {
    height: 6px;
    background: var(--surface2);
    border-radius: 3px;
    overflow: hidden;
  }
  .bar-fill { height: 100%; border-radius: 3px; transition: width .4s ease; }

  .count-num {
    font-size: 1.3rem; font-weight: 600;
    font-family: var(--mono);
    letter-spacing: -.02em;
    text-align: right;
  }

  /* ── TICKET PANEL ── */
  .tickets-panel {
    display: none;
    padding: 0 20px 16px;
    background: #FAFAF8;
    border-top: 1px solid var(--border);
    animation: slideDown .18s ease;
  }
  .tickets-panel.open { display: block; }
  @keyframes slideDown {
    from { opacity: 0; transform: translateY(-6px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .t-table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 12px;
    font-size: .8rem;
  }
  .t-table thead tr {
    background: var(--surface2);
    border-radius: 6px;
  }
  .t-table th {
    padding: 7px 12px;
    text-align: left;
    font-size: .68rem;
    font-family: var(--mono);
    color: var(--text3);
    text-transform: uppercase;
    letter-spacing: .06em;
    font-weight: 500;
    border-bottom: 1px solid var(--border);
  }
  .t-table th:last-child { text-align: right; }
  .t-table td {
    padding: 8px 12px;
    border-bottom: 1px solid var(--border);
    vertical-align: middle;
  }
  .t-table tbody tr:last-child td { border-bottom: none; }
  .t-table tbody tr:hover td { background: rgba(0,0,0,.02); }

  .t-id {
    font-family: var(--mono);
    font-size: .75rem;
    color: var(--text2);
    white-space: nowrap;
  }
  .t-subj {
    color: var(--text);
    max-width: 340px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .t-date {
    font-family: var(--mono);
    font-size: .75rem;
    color: var(--text2);
    white-space: nowrap;
  }
  .t-days {
    font-family: var(--mono);
    font-size: .8rem;
    font-weight: 500;
    text-align: right;
    white-space: nowrap;
  }
  .t-days.red   { color: var(--red); }
  .t-days.amber { color: var(--amber); }
  .t-days.green { color: var(--green); }

  /* ── FOOTER ── */
  .footer {
    margin-top: 1.5rem;
    font-size: .72rem;
    font-family: var(--mono);
    color: var(--text3);
    text-align: center;
  }

  @media (max-width: 700px) {
    .summary { grid-template-columns: repeat(2, 1fr); }
    .col-head { display: none; }
    .row-main { grid-template-columns: 40px 1fr 60px; }
    .row-main .col-badge,
    .row-main .col-bar { display: none; }
  }
</style>
</head>
<body>

<div class="page-header">
  <div class="page-header-left">
    <div class="accent-bar"></div>
    <div>
      <div class="page-title">Tickets Atrasados — Técnicos de Campo</div>
      <div class="page-sub">Service Tasks vencidos · 05/05/2026 · Haz clic en un técnico para ver sus tickets</div>
    </div>
  </div>
  <div class="status-pill"><div class="pulse"></div>ATRASADO</div>
</div>

<div class="summary">
  <div class="s-card red">
    <div class="s-lbl">Tickets atrasados</div>
    <div class="s-val">77</div>
  </div>
  <div class="s-card amber">
    <div class="s-lbl">Técnicos afectados</div>
    <div class="s-val">9</div>
  </div>
  <div class="s-card red">
    <div class="s-lbl">Días máx. de atraso</div>
    <div class="s-val">99</div>
  </div>
  <div class="s-card green">
    <div class="s-lbl">Tickets al día</div>
    <div class="s-val">2</div>
  </div>
</div>

<div class="table-wrap">
  <div class="col-head">
    <div></div>
    <div>Técnico</div>
    <div>Atraso máx.</div>
    <div>Progreso</div>
    <div class="right">Total</div>
  </div>
  <div id="table"></div>
</div>

<div class="footer">Seguridad Toledos &nbsp;·&nbsp; Datos al 05/05/2026 &nbsp;·&nbsp; Criterio: hora fin de cita</div>

<script>
const techs = [
  { name:"Emanuel Flores",  init:"EF", color:"#185FA5", bg:"#E6F1FB", count:25, maxDays:46, tickets:[
    {id:"33490",subj:"PF PLANTA 4 AMPLIACIÓN INSTALACIÓN CCTV Y CA",date:"2026-03-20",days:46},
    {id:"34017",subj:"FF CIMB MANTENCIÓN CORRECTIVA CONTROL ACCESO",date:"2026-04-06",days:29},
    {id:"34022",subj:"PF PLANTA 4 AMPLIACIÓN INSTALACIÓN CCTV Y CA",date:"2026-04-07",days:28},
    {id:"34062",subj:"P.F COMPLEJO INDUSTRIAL Prev. Controles de acceso",date:"2026-04-07",days:28},
    {id:"34063",subj:"P.F COMPLEJO DEPORTIVO Prev. Cámaras",date:"2026-04-10",days:25},
    {id:"34064",subj:"P.F COMPLEJO DEPORTIVO Prev. Racks y suministros",date:"2026-04-10",days:25},
    {id:"34065",subj:"PF PLANTA 4 AMPLIACIÓN INSTALACIÓN CCTV Y CA",date:"2026-04-08",days:27},
    {id:"34158",subj:"PF PLANTA 4 AMPLIACIÓN INSTALACIÓN CCTV Y CA",date:"2026-04-10",days:25},
    {id:"34159",subj:"Asistencia técnica Cámaras Plantas 1 y 4",date:"2026-04-10",days:25},
    {id:"34160",subj:"Revisión y reparación de cámaras P1, P4",date:"2026-04-10",days:25},
    {id:"34235",subj:"PF CIMB Capacitación uso sistema alarmas y cámaras",date:"2026-04-13",days:22},
    {id:"34255",subj:"PF PLANTA 4 AMPLIACIÓN INSTALACIÓN CCTV Y CA",date:"2026-04-14",days:21},
    {id:"34318",subj:"PF PLANTA 4 AMPLIACIÓN INSTALACIÓN CCTV Y CA",date:"2026-04-15",days:20},
    {id:"34352",subj:"PF PLANTA 4 AMPLIACIÓN INSTALACIÓN CCTV Y CA",date:"2026-04-16",days:19},
    {id:"34447",subj:"PF PLANTA 4 AMPLIACIÓN INSTALACIÓN CCTV Y CA",date:"2026-04-20",days:15},
    {id:"34448",subj:"PF PLANTA 4 AMPLIACIÓN INSTALACIÓN CCTV Y CA",date:"2026-04-21",days:14},
    {id:"34481",subj:"PF CDT INSTALACIÓN DE CCTV Y ALARMA",date:"2026-04-10",days:25},
    {id:"34506",subj:"PF PLANTA 4 AMPLIACIÓN INSTALACIÓN CCTV Y CA",date:"2026-04-22",days:13},
    {id:"34524",subj:"PF PLANTA 4 AMPLIACIÓN INSTALACIÓN CCTV Y CA",date:"2026-04-24",days:11},
    {id:"34637",subj:"PF PLANTA 2 Sistema de alarmas planta 2 y FMP",date:"2026-04-27",days:8},
    {id:"34646",subj:"PF PLANTA 4 AMPLIACIÓN INSTALACIÓN CCTV Y CA",date:"2026-04-28",days:7},
    {id:"34694",subj:"PF PLANTA 4 AMPLIACIÓN INSTALACIÓN CCTV Y CA",date:"2026-04-29",days:6},
    {id:"34791",subj:"PF COMPLEJO INDUSTRIAL Instalación de rayos",date:"2026-04-30",days:5},
    {id:"34797",subj:"PF PLANTA 4 AMPLIACIÓN INSTALACIÓN CCTV Y CA",date:"2026-05-05",days:0},
    {id:"34798",subj:"PF PLANTA 4 AMPLIACIÓN INSTALACIÓN CCTV Y CA",date:"2026-05-04",days:1},
  ]},
  { name:"Esteban Negrete", init:"EN", color:"#993C1D", bg:"#FAECE7", count:12, maxDays:41, tickets:[
    {id:"31611",subj:"Máquinas Virtuales",date:"2026-03-31",days:35},
    {id:"31990",subj:"Cambio de máscara de subred",date:"2026-03-31",days:35},
    {id:"32964",subj:"CÁMARA AV. I.C. PINTO / 29 SUR",date:"2026-03-30",days:36},
    {id:"33731",subj:"Casino Talca, Revisar puerta",date:"2026-03-25",days:41},
    {id:"34013",subj:"Falla cámara PTZ Calle 2 Norte 21 Oriente",date:"2026-04-06",days:29},
    {id:"34097",subj:"CÁMARA 14 ORIENTE CON 5 NORTE",date:"2026-04-08",days:27},
    {id:"34098",subj:"1 NORTE CON 1 PONIENTE",date:"2026-04-08",days:27},
    {id:"34298",subj:"RV: REITERACIÓN CÁMARAS SIN IMAGEN",date:"2026-04-15",days:20},
    {id:"34321",subj:"CÁMARA 16 ORIENTE CON 9 NORTE",date:"2026-04-15",days:20},
    {id:"34322",subj:"Reubicación cámaras seguridad 26 sur Talca",date:"2026-04-15",days:20},
    {id:"34477",subj:"NS AGRO REUNIÓN EN SUCURSAL TALCA",date:"2026-04-21",days:14},
    {id:"34824",subj:"Constructora Nuevo Aires: Instalación de ANPR",date:"2026-05-05",days:0},
  ]},
  { name:"Diego Franquiz",  init:"DF", color:"#534AB7", bg:"#EEEDFE", count:9, maxDays:27, tickets:[
    {id:"34092",subj:"Revisión y reparación cámaras P1 y P4",date:"2026-04-08",days:27},
    {id:"34640",subj:"PF HUECHURABA Levantamiento CCTV",date:"2026-04-28",days:7},
    {id:"34641",subj:"Asistencia técnica Sistema VTS Huechuraba",date:"2026-04-28",days:7},
    {id:"34643",subj:"PF SAN BERNARDO Asistencia técnica CCTV",date:"2026-04-28",days:7},
    {id:"34695",subj:"Asistencia técnica Cámaras Plantas 1 y 4",date:"2026-04-29",days:6},
    {id:"34747",subj:"PF PLANTA 1 Fallo en sistema de alarma",date:"2026-05-05",days:0},
    {id:"34790",subj:"PF COMPLEJO INDUSTRIAL Instalación de rayos",date:"2026-04-30",days:5},
    {id:"34793",subj:"PF COMPLEJO INDUSTRIAL Instalación de rayos",date:"2026-05-02",days:3},
    {id:"34794",subj:"PF COMPLEJO INDUSTRIAL Instalación de rayos",date:"2026-05-05",days:0},
  ]},
  { name:"Lucas Miranda",   init:"LM", color:"#0F6E56", bg:"#E1F5EE", count:8, maxDays:46, tickets:[
    {id:"33495",subj:"TPL: Regularización de red",date:"2026-04-03",days:32},
    {id:"33525",subj:"Limpiar documentación TPL y levantamientos",date:"2026-03-20",days:46},
    {id:"34297",subj:"TOLEDOS: Instalación antena Toledos 4.0",date:"2026-04-14",days:21},
    {id:"34609",subj:"PF PLANTA 1 Controles de Acceso",date:"2026-04-27",days:8},
    {id:"34642",subj:"Asistencia técnica Sistema VTS Huechuraba",date:"2026-04-28",days:7},
    {id:"34792",subj:"PF COMPLEJO INDUSTRIAL Instalación de rayos",date:"2026-04-30",days:5},
    {id:"34796",subj:"PF COMPLEJO INDUSTRIAL Instalación de rayos",date:"2026-05-05",days:0},
    {id:"34799",subj:"PF PLANTA 4 AMPLIACIÓN INSTALACIÓN CCTV Y CA",date:"2026-05-04",days:1},
  ]},
  { name:"Juan Espinoza",   init:"JE", color:"#854F0B", bg:"#FEF3D0", count:5, maxDays:99, tickets:[
    {id:"31503",subj:"Levantamiento TPL",date:"2026-01-26",days:99},
    {id:"33494",subj:"TPL: Regularización de red",date:"2026-04-03",days:32},
    {id:"34707",subj:"Instalación Sistema Alarma AJAX",date:"2026-04-30",days:5},
    {id:"34708",subj:"Instalación Sistema Alarma AJAX",date:"2026-04-29",days:6},
    {id:"34806",subj:"Constructora Nuevo Aires: Instalación de ANPR",date:"2026-05-05",days:0},
  ]},
  { name:"José Espinoza",   init:"JS", color:"#854F0B", bg:"#FEF3D0", count:5, maxDays:5, tickets:[
    {id:"31852",subj:"Puesta en Marcha — Estandarizar Documentación",date:"2026-05-04",days:1},
    {id:"34710",subj:"Problemas control de acceso",date:"2026-05-04",days:1},
    {id:"34712",subj:"TOLEDOS: Telecomunicaciones instalación y config.",date:"2026-04-30",days:5},
    {id:"34782",subj:"TOLEDOS: Verificación de horario y reglas IVS",date:"2026-05-04",days:1},
    {id:"34809",subj:"GALILEA CENTRO: Levantamiento Buin Sala de Ventas",date:"2026-05-05",days:0},
  ]},
  { name:"Julian Casanova", init:"JC", color:"#993556", bg:"#FBEAF0", count:5, maxDays:8, tickets:[
    {id:"34630",subj:"Mall del Centro Concepción: Visita técnica",date:"2026-04-27",days:8},
    {id:"34670",subj:"AGRI CHILE: CAMARICO Control vehicular",date:"2026-05-04",days:1},
    {id:"34673",subj:"Instalación Sistema Alarma AJAX",date:"2026-04-29",days:6},
    {id:"34706",subj:"Instalación Sistema Alarma AJAX",date:"2026-04-30",days:5},
    {id:"34808",subj:"GALILEA CENTRO: Levantamiento Buin Sala de Ventas",date:"2026-05-05",days:0},
  ]},
  { name:"Dario Valdes",    init:"DV", color:"#5F5E5A", bg:"#F1EFE8", count:4, maxDays:35, tickets:[
    {id:"33493",subj:"TPL: Regularización de red",date:"2026-03-31",days:35},
    {id:"34692",subj:"RV: Cámaras fuera de línea",date:"2026-05-05",days:0},
    {id:"34803",subj:"TOLEDOS: Mantención Preventiva CCTV",date:"2026-05-05",days:0},
    {id:"34830",subj:"Mall Florida GO: Correctiva en 02 cámaras",date:"2026-05-05",days:0},
  ]},
  { name:"Esteban Moran",   init:"EM", color:"#5F5E5A", bg:"#F1EFE8", count:3, maxDays:33, tickets:[
    {id:"33763",subj:"Mall Plaza Maule: Documentación Maule Express",date:"2026-04-02",days:33},
    {id:"34533",subj:"Informe General Mall Plaza",date:"2026-04-23",days:12},
    {id:"34831",subj:"Factibilidad botón emergencia",date:"2026-05-05",days:0},
  ]},
];

const MAX = 25;

function badgeClass(d) { return d >= 30 ? 'badge-red' : d >= 7 ? 'badge-amber' : 'badge-green'; }
function daysClass(d)  { return d >= 30 ? 'red' : d >= 7 ? 'amber' : 'green'; }
function daysLabel(d)  { return d === 0 ? 'Hoy' : d === 1 ? '1 día' : d + ' días'; }

const container = document.getElementById('table');

techs.forEach((t, idx) => {
  const wrap = document.createElement('div');
  wrap.className = 'tech-row';

  const pct = Math.round(t.count / MAX * 100);

  const rowHTML = `
    <div class="row-main">
      <div class="avatar" style="background:${t.bg};color:${t.color}">${t.init}</div>
      <div class="name-wrap">
        <span class="tech-name">${t.name}</span>
        <span class="chevron">›</span>
      </div>
      <div class="col-badge">
        <span class="badge ${badgeClass(t.maxDays)}">Max ${t.maxDays} días</span>
      </div>
      <div class="col-bar">
        <div class="bar-track">
          <div class="bar-fill" style="width:${pct}%;background:${t.color}"></div>
        </div>
      </div>
      <div class="count-num" style="color:${t.color}">${t.count}</div>
    </div>
    <div class="tickets-panel" id="panel-${idx}">
      <table class="t-table">
        <thead>
          <tr>
            <th style="width:80px"># Ticket</th>
            <th>Asunto</th>
            <th style="width:110px">Fecha cita</th>
            <th style="width:90px;text-align:right">Atraso</th>
          </tr>
        </thead>
        <tbody>
          ${t.tickets.map(tk => `
            <tr>
              <td class="t-id">#${tk.id}</td>
              <td class="t-subj">${tk.subj}</td>
              <td class="t-date">${tk.date}</td>
              <td class="t-days ${daysClass(tk.days)}">${daysLabel(tk.days)}</td>
            </tr>
          `).join('')}
        </tbody>
      </table>
    </div>
  `;

  wrap.innerHTML = rowHTML;

  wrap.querySelector('.row-main').addEventListener('click', () => {
    const panel = document.getElementById('panel-' + idx);
    const isOpen = panel.classList.contains('open');
    document.querySelectorAll('.tickets-panel').forEach(p => p.classList.remove('open'));
    document.querySelectorAll('.tech-row').forEach(r => r.classList.remove('active'));
    if (!isOpen) {
      panel.classList.add('open');
      wrap.classList.add('active');
    }
  });

  container.appendChild(wrap);
});
</script>
</body>
</html>

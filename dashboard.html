<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>MT5 Auto Trader</title>
<script src="https://cdn.tailwindcss.com"></script>
<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.1/dist/chart.umd.min.js"></script>
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans+Thai:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  body{font-family:'IBM Plex Sans Thai',sans-serif;background:#0a0f14;color:#e2e8f0}
  .card{background:#111820;border:1px solid #1f2b38;border-radius:10px}
  input,textarea,select{background:#0a0f14;border:1px solid #263545;border-radius:6px;padding:6px 8px;color:#e2e8f0;width:100%}
  input:focus,textarea:focus{outline:2px solid #22d3a0;outline-offset:0}
  button:focus-visible{outline:2px solid #22d3a0}
  .num{font-variant-numeric:tabular-nums}
  #chat::-webkit-scrollbar{width:6px}#chat::-webkit-scrollbar-thumb{background:#263545;border-radius:3px}
</style>
</head>
<body class="min-h-screen p-3 lg:p-5">

<header class="card px-4 py-3 flex flex-wrap items-center gap-x-6 gap-y-2 mb-4">
  <h1 class="font-semibold text-lg mr-2">MT5 Auto Trader</h1>
  <div id="conn" class="text-sm text-amber-400">กำลังเชื่อมต่อบอท…</div>
  <div class="text-sm">บัญชี <span id="acc" class="num">-</span></div>
  <div class="text-sm">Equity <span id="eq" class="num font-semibold">-</span></div>
  <div class="text-sm">กำไร/ขาดทุนลอย <span id="pl" class="num font-semibold">-</span></div>
  <div class="ml-auto flex items-center gap-3">
    <span id="runlbl" class="text-sm text-slate-400">หยุดอยู่</span>
    <button id="toggle" class="px-4 py-2 rounded-md bg-emerald-500 text-black font-medium text-sm">เริ่มเทรดอัตโนมัติ</button>
  </div>
</header>

<div id="warnbar" class="hidden card border-amber-500 text-amber-300 px-4 py-2 mb-4 text-sm"></div>

<main class="grid grid-cols-1 lg:grid-cols-12 gap-4">

  <!-- ซ้าย: ราคา + กราฟ + ไม้ที่เปิดอยู่ -->
  <section class="lg:col-span-5 space-y-4">
    <div class="card p-4">
      <div id="symtabs" class="flex flex-wrap gap-2 mb-3"></div>
      <div class="flex items-baseline gap-3 mb-2">
        <span id="selsym" class="font-semibold text-xl">-</span>
        <span id="selpx" class="num text-2xl">-</span>
      </div>
      <div class="h-56"><canvas id="chart"></canvas></div>
    </div>
    <div class="card p-4">
      <h2 class="font-medium mb-2">ไม้ที่บอทเปิดอยู่</h2>
      <div class="overflow-x-auto">
      <table class="w-full text-sm num">
        <thead class="text-slate-400 text-left"><tr><th>สัญลักษณ์</th><th>ฝั่ง</th><th>ล็อต</th><th>ราคาเข้า</th><th>SL</th><th class="text-right">กำไร</th></tr></thead>
        <tbody id="pos"><tr><td colspan="6" class="py-3 text-slate-500">ยังไม่มีไม้ที่เปิดอยู่</td></tr></tbody>
      </table>
      </div>
    </div>
    <div class="card p-4">
      <div class="flex items-center justify-between mb-1">
        <h2 class="font-medium">ประวัติการเทรด</h2>
        <button id="tcsv" class="text-xs px-2 py-1 rounded-md bg-slate-800">ดาวน์โหลด CSV</button>
      </div>
      <div id="tsum" class="text-sm text-slate-400 mb-2 num"></div>
      <div class="overflow-x-auto max-h-80 overflow-y-auto">
      <table class="w-full text-sm num whitespace-nowrap">
        <thead class="text-slate-400 text-left"><tr><th class="pr-3">สัญลักษณ์</th><th class="pr-3">ฝั่ง</th><th class="pr-3">ล็อต</th><th class="pr-3">ราคาเข้า</th><th class="pr-3">เวลาเข้า</th><th class="pr-3">ราคาออก</th><th class="pr-3">เวลาออก</th><th class="text-right">กำไร/ขาดทุน</th></tr></thead>
        <tbody id="trades"></tbody>
      </table>
      </div>
    </div>
  </section>

  <!-- กลาง: แชต -->
  <section class="lg:col-span-4 card p-4 flex flex-col h-[34rem] lg:h-auto lg:min-h-[32rem]">
    <h2 class="font-medium mb-2">ห้องแชตกับบอท</h2>
    <div id="chat" class="flex-1 overflow-y-auto space-y-2 pr-1 text-sm"></div>
    <form id="chatform" class="flex gap-2 mt-3">
      <input id="chatin" placeholder="สถานะ / เริ่ม / หยุด / ปิดทั้งหมด" autocomplete="off">
      <button class="px-4 rounded-md bg-slate-700 text-sm shrink-0">ส่ง</button>
    </form>
  </section>

  <!-- ขวา: ตั้งค่า + ข่าว -->
  <section class="lg:col-span-3 space-y-4">
    <div class="card p-4">
      <h2 class="font-medium mb-3">ตั้งค่า</h2>
      <div class="space-y-3 text-sm">
        <label class="block">สัญลักษณ์ที่เทรด (คั่นด้วยจุลภาค)
          <input id="f_symbols" placeholder="XAUUSD,EURUSD"></label>
        <div>
          <div class="mb-1">จำนวนล็อตต่อสัญลักษณ์</div>
          <div id="lots" class="space-y-1.5"></div>
        </div>
        <div class="grid grid-cols-3 gap-2">
          <label>SL เริ่มต้น (x ATR)<input id="f_sl_atr" type="number" step="0.1"></label>
          <label>เริ่มเลื่อน SL (x ATR)<input id="f_be_atr" type="number" step="0.1"></label>
          <label>SL ตามหลัง (x ATR)<input id="f_trail_atr" type="number" step="0.1"></label>
        </div>
        <div class="grid grid-cols-2 gap-2">
          <label>ถามก่อนเมื่อมั่นใจต่ำกว่า (0-1)<input id="f_ask_below" type="number" step="0.05" min="0" max="1"></label>
          <label>เตือนก่อนข่าว (นาที)<input id="f_news_warn_min" type="number" min="1"></label>
        </div>
        <div class="grid grid-cols-2 gap-2">
          <label>Volume พุ่ง (x เฉลี่ย)<input id="f_vol_mult" type="number" step="0.1"></label>
          <label>ไม้สูงสุดพร้อมกัน<input id="f_max_positions" type="number" min="1"></label>
        </div>
        <label class="flex items-start gap-2 text-amber-300"><input id="f_allow_live" type="checkbox" class="!w-4 mt-1">
          <span>อนุญาตให้เทรดบัญชีจริง (ปิดไว้ = เทรดเฉพาะบัญชีเดโม)</span></label>
        <button id="save" class="w-full py-2 rounded-md bg-emerald-500 text-black font-medium">บันทึกการตั้งค่า</button>
      </div>
    </div>

    <div class="card p-4">
      <h2 class="font-medium mb-1">ข่าวแรง</h2>
      <p class="text-xs text-slate-400 mb-2">1 บรรทัดต่อ 1 ข่าว: <span class="num">เวลา,สกุล/สัญลักษณ์,หัวข้อ,impact</span><br>
        ตัวอย่าง: <span class="num">2026-09-30 19:30,USD,US CPI,high</span> (เวลาตามเครื่องที่รันบอท)</p>
      <textarea id="newsin" rows="4" placeholder="2026-09-30 19:30,USD,US CPI,high"></textarea>
      <div class="flex gap-2 mt-2 text-sm">
        <button id="newsadd" class="flex-1 py-1.5 rounded-md bg-slate-700">เพิ่มข่าว</button>
        <label class="flex-1 py-1.5 rounded-md bg-slate-700 text-center cursor-pointer">อัปโหลดไฟล์ .csv/.txt
          <input id="newsfile" type="file" accept=".csv,.txt" class="hidden"></label>
        <button id="newsclr" class="px-3 py-1.5 rounded-md bg-slate-800 text-rose-400">ล้าง</button>
      </div>
      <ul id="newslist" class="mt-3 space-y-1 text-sm"></ul>
    </div>
  </section>
</main>

<script>
let ws, S = null, sel = null, chart = null, formBuilt = false, lastState = null, lastTrades = null;
const $ = id => document.getElementById(id);
const fmt = (n, d = 2) => Number(n).toLocaleString(undefined, {minimumFractionDigits: d, maximumFractionDigits: d});
const cls = v => v >= 0 ? 'text-emerald-400' : 'text-rose-400';
const send = o => ws && ws.readyState === 1 && ws.send(JSON.stringify(o));

let lastMsg = 0;
const setConn = (t, c) => { $('conn').textContent = t; $('conn').className = 'text-sm ' + c; };

function connect() {
  if (location.protocol === 'file:' || !location.host) {
    setConn('เปิดไฟล์ตรง ๆ ไม่ได้ — ให้รัน python bot.py แล้วเปิดที่อยู่ http://localhost:… ที่บอทแสดง', 'text-rose-400');
    return;
  }
  const url = `${location.protocol === 'https:' ? 'wss' : 'ws'}://${location.host}/ws`;
  try { ws = new WebSocket(url); } catch (err) { setConn('สร้างการเชื่อมต่อไม่ได้: ' + err.message, 'text-rose-400'); setTimeout(connect, 2000); return; }
  ws.onopen = () => { lastMsg = Date.now(); setConn('เชื่อมต่อบอทแล้ว', 'text-emerald-400'); };
  ws.onclose = () => { setConn(`ต่อ ${url} ไม่ได้ — กำลังลองใหม่ (ตรวจว่า python bot.py ยังรันอยู่ และเปิดหน้านี้จากที่อยู่ของบอท)`, 'text-rose-400'); setTimeout(connect, 2000); };
  ws.onmessage = e => {
    lastMsg = Date.now();
    try {
      const m = JSON.parse(e.data);
      if (m.type === 'state') onState(m);
      else if (m.type === 'history') { $('chat').innerHTML = ''; m.items.forEach(addChat); }
      else if (m.type === 'chat') addChat(m);
      else if (m.type === 'trades') { lastTrades = m.items || []; renderTrades(); }
    } catch (err) { console.error(err); setConn('หน้าเว็บอ่านข้อมูลจากบอทไม่ได้: ' + err.message, 'text-rose-400'); }
  };
}
// เตือนถ้าเชื่อมต่ออยู่แต่บอทเงียบเกิน 8 วินาที (บอทค้าง / MT5 ไม่ตอบ)
setInterval(() => {
  if (ws && ws.readyState === 1 && lastMsg && Date.now() - lastMsg > 8000)
    setConn('เชื่อมต่ออยู่ แต่บอทไม่ส่งข้อมูลมา ' + Math.round((Date.now() - lastMsg) / 1000) + ' วินาที — บอทอาจค้างหรือ MT5 ไม่ตอบ', 'text-amber-400');
}, 2000);

function addChat(m) {
  const box = $('chat'), row = document.createElement('div');
  const tone = m.who === 'you' ? 'ml-8 bg-slate-700' : m.who === 'warn' ? 'bg-amber-900/40 border border-amber-600/50' : 'mr-8 bg-slate-800';
  row.className = `rounded-lg px-3 py-2 ${tone}`;
  const t = document.createElement('div'); t.textContent = m.text; row.appendChild(t);
  const ts = document.createElement('div'); ts.className = 'text-[11px] text-slate-500 mt-0.5 num'; ts.textContent = m.ts; row.appendChild(ts);
  if (m.ask) {
    const bar = document.createElement('div'); bar.className = 'flex gap-2 mt-2';
    [['เข้าเลย', true, 'bg-emerald-500 text-black'], ['ไม่เข้า', false, 'bg-slate-600']].forEach(([label, ok, c]) => {
      const b = document.createElement('button'); b.textContent = label; b.className = `px-3 py-1 rounded-md text-sm ${c}`;
      b.onclick = () => { send({type: 'answer', id: m.ask, ok}); bar.remove(); };
      bar.appendChild(b);
    });
    row.appendChild(bar);
  }
  box.appendChild(row); box.scrollTop = box.scrollHeight;
}

function onState(st) {
  lastState = st; S = st.settings = st.settings || {};
  S.symbols = S.symbols || []; S.lots = S.lots || {default: 0.01};
  st.prices = st.prices || {}; st.series = st.series || {}; st.positions = st.positions || []; st.news = st.news || [];
  if (!formBuilt) buildForm();
  if (st.trades) { lastTrades = st.trades; renderTrades(); }
  else if (lastTrades === null) renderTrades();
  if (!sel || !S.symbols.includes(sel)) sel = S.symbols[0];
  const a = st.account;
  $('acc').textContent = a ? `${a.login} · ${a.server} · ${a.demo ? 'เดโม' : 'บัญชีจริง'}` : 'ไม่พบบัญชี MT5';
  $('eq').textContent = a ? fmt(a.equity) : '-';
  $('pl').textContent = a ? fmt(a.profit) : '-'; $('pl').className = 'num font-semibold ' + (a ? cls(a.profit) : '');
  $('runlbl').textContent = S.enabled ? 'กำลังเทรดอัตโนมัติ' : 'หยุดอยู่';
  $('toggle').textContent = S.enabled ? 'หยุดเปิดไม้ใหม่' : 'เริ่มเทรดอัตโนมัติ';
  $('toggle').className = 'px-4 py-2 rounded-md font-medium text-sm ' + (S.enabled ? 'bg-rose-500 text-white' : 'bg-emerald-500 text-black');

  $('symtabs').innerHTML = '';
  S.symbols.forEach(s => {
    const b = document.createElement('button');
    b.textContent = s; b.className = 'px-3 py-1 rounded-md text-sm ' + (s === sel ? 'bg-emerald-500 text-black' : 'bg-slate-800');
    b.onclick = () => { sel = s; onState(lastState); }; $('symtabs').appendChild(b);
  });
  $('selsym').textContent = sel || '-';
  const px = st.prices[sel]; $('selpx').textContent = px ? `${px.bid} / ${px.ask}` : 'ไม่มีราคา (ตรวจชื่อสัญลักษณ์)';
  drawChart(st.series[sel] || []);

  const tb = $('pos');
  tb.innerHTML = st.positions.length ? '' : '<tr><td colspan="6" class="py-3 text-slate-500">ยังไม่มีไม้ที่เปิดอยู่</td></tr>';
  st.positions.forEach(p => {
    tb.insertAdjacentHTML('beforeend', `<tr class="border-t border-slate-800"><td class="py-1.5">${p.sym}</td>
      <td class="${p.side === 'BUY' ? 'text-emerald-400' : 'text-rose-400'}">${p.side}</td><td>${p.lot}</td><td>${p.open}</td><td>${p.sl || '-'}</td>
      <td class="text-right ${cls(p.profit)}">${fmt(p.profit)}</td></tr>`);
  });

  const nl = $('newslist'); nl.innerHTML = '';
  st.news.filter(n => n.mins > -60).forEach(n => {
    const soon = n.mins >= 0 && n.mins <= S.news_warn_min;
    nl.insertAdjacentHTML('beforeend', `<li class="flex justify-between gap-2 ${soon ? 'text-amber-300' : 'text-slate-300'}"><span>${n.t.slice(5)} ${n.sym} ${esc(n.title)}</span><span class="num shrink-0">${n.mins >= 0 ? 'อีก ' + n.mins + ' น.' : 'ผ่านมาแล้ว'}</span></li>`);
  });
  if (!nl.children.length) nl.innerHTML = '<li class="text-slate-500">ยังไม่มีข่าวที่กำลังจะมาถึง</li>';
  const soonN = st.news.filter(n => n.impact === 'high' && n.mins >= 0 && n.mins <= S.news_warn_min);
  $('warnbar').classList.toggle('hidden', !soonN.length);
  if (soonN.length) $('warnbar').textContent = '⚠️ ข่าวแรงใกล้ออก: ' + soonN.map(n => `${n.title} (${n.sym}) อีก ${n.mins} นาที`).join(' | ');

}
const esc = s => s.replace(/[&<>"]/g, c => ({'&': '&amp;', '<': '&lt;', '>': '&gt;', '"': '&quot;'}[c]));

function drawChart(data) {
  if (!chart) chart = new Chart($('chart'), {type: 'line', data: {labels: [], datasets: [{data: [], borderColor: '#22d3a0', borderWidth: 2, pointRadius: 0, tension: .25}]},
    options: {animation: false, maintainAspectRatio: false, plugins: {legend: {display: false}}, scales: {x: {display: false}, y: {ticks: {color: '#8aa0b5'}, grid: {color: '#1a2531'}}}}});
  chart.data.labels = data.map((_, i) => i); chart.data.datasets[0].data = data; chart.update();
}

function buildForm() {
  formBuilt = true;
  $('f_symbols').value = S.symbols.join(',');
  ['sl_atr', 'be_atr', 'trail_atr', 'ask_below', 'news_warn_min', 'vol_mult', 'max_positions'].forEach(k => $('f_' + k).value = S[k]);
  $('f_allow_live').checked = S.allow_live;
  buildLots();
  $('f_symbols').oninput = buildLots;
}
function buildLots() {
  const old = {}; document.querySelectorAll('#lots input').forEach(i => old[i.dataset.s] = i.value);
  const syms = ['default', ...$('f_symbols').value.split(',').map(x => x.trim()).filter(Boolean)];
  $('lots').innerHTML = '';
  syms.forEach(s => {
    const v = old[s] ?? S.lots[s] ?? S.lots.default ?? 0.01;
    $('lots').insertAdjacentHTML('beforeend', `<div class="flex items-center gap-2"><span class="w-24 text-slate-400">${s === 'default' ? 'ค่าเริ่มต้น' : esc(s)}</span><input data-s="${esc(s)}" type="number" step="0.01" min="0.01" value="${v}"></div>`);
  });
}

$('save').onclick = () => {
  const lots = {}; document.querySelectorAll('#lots input').forEach(i => lots[i.dataset.s] = parseFloat(i.value));
  const d = {symbols: $('f_symbols').value.split(',').map(x => x.trim()).filter(Boolean), lots, allow_live: $('f_allow_live').checked};
  ['sl_atr', 'be_atr', 'trail_atr', 'ask_below', 'news_warn_min', 'vol_mult', 'max_positions'].forEach(k => d[k] = parseFloat($('f_' + k).value));
  if (d.allow_live && !confirm('เปิดให้เทรดบัญชีจริง? แนะนำให้ทดสอบบนเดโมให้นานพอก่อน')) return;
  send({type: 'settings', data: d});
};
$('toggle').onclick = () => send({type: 'toggle', on: !(S && S.enabled)});
$('chatform').onsubmit = e => { e.preventDefault(); const v = $('chatin').value.trim(); if (v) send({type: 'chat', text: v}); $('chatin').value = ''; };
$('newsadd').onclick = () => { const t = $('newsin').value; if (t.trim()) { send({type: 'news', text: t}); $('newsin').value = ''; } };
$('newsclr').onclick = () => confirm('ล้างรายการข่าวทั้งหมด?') && send({type: 'news', clear: true});
$('newsfile').onchange = e => { const f = e.target.files[0]; if (!f) return; const r = new FileReader(); r.onload = () => send({type: 'news', text: r.result}); r.readAsText(f); e.target.value = ''; };
function renderTrades() {
  const tb = $('trades'), items = lastTrades || [];
  if (lastTrades === null) { tb.innerHTML = '<tr><td colspan="8" class="py-3 text-slate-500">รอข้อมูลประวัติจากบอท (ถ้าไม่ขึ้น ให้เพิ่มโค้ดส่ง trades ใน bot.py)</td></tr>'; $('tsum').textContent = ''; return; }
  if (!items.length) { tb.innerHTML = '<tr><td colspan="8" class="py-3 text-slate-500">ยังไม่มีไม้ที่ปิดแล้ว</td></tr>'; $('tsum').textContent = ''; return; }
  tb.innerHTML = '';
  items.forEach(t => tb.insertAdjacentHTML('beforeend', `<tr class="border-t border-slate-800"><td class="py-1.5 pr-3">${esc(String(t.sym))}</td>
    <td class="pr-3 ${t.side === 'BUY' ? 'text-emerald-400' : 'text-rose-400'}">${esc(String(t.side))}</td><td class="pr-3">${t.lot}</td>
    <td class="pr-3">${t.open}</td><td class="pr-3">${esc(String(t.open_time || '-'))}</td>
    <td class="pr-3">${t.close ?? '-'}</td><td class="pr-3">${esc(String(t.close_time || '-'))}</td>
    <td class="text-right font-medium ${cls(t.profit)}">${t.profit >= 0 ? '+' : ''}${fmt(t.profit)}</td></tr>`));
  const win = items.filter(t => t.profit > 0).length, sum = items.reduce((a, t) => a + Number(t.profit || 0), 0);
  $('tsum').innerHTML = `${items.length} ไม้ · ชนะ ${win} · แพ้ ${items.length - win} · รวม <span class="${cls(sum)} font-medium">${sum >= 0 ? '+' : ''}${fmt(sum)}</span>`;
}
$('tcsv').onclick = () => {
  const rows = [['symbol', 'side', 'lot', 'open_price', 'open_time', 'close_price', 'close_time', 'profit'], ...(lastTrades || []).map(t => [t.sym, t.side, t.lot, t.open, t.open_time, t.close, t.close_time, t.profit])];
  const csv = '\ufeff' + rows.map(r => r.map(v => `"${String(v ?? '').replace(/"/g, '""')}"`).join(',')).join('\n');
  const a = document.createElement('a'); a.href = URL.createObjectURL(new Blob([csv], {type: 'text/csv'})); a.download = 'trade_history.csv'; a.click();
};
renderTrades();
connect();
</script>
</body>
</html>

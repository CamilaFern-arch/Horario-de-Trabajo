<!DOCTYPE html>
<html lang="es" class="dark">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
  <title>⏰Control de Horas & Extras Mobile</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="https://unpkg.com/@phosphor-icons/web"></script>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">

  <script>
    tailwind.config = {
      darkMode: 'class',
      theme: {
        extend: {
          fontFamily: { sans: ['"Plus Jakarta Sans"', 'sans-serif'] },
          colors: {
            app: {
              bg: '#0A0A0C',
              card: '#141419',
              cardBorder: '#23232D',
              purple: '#A855F7',
              purpleGlow: '#A855F725',
              cyan: '#06B6D4',
              pink: '#EC4899',
              green: '#10B981',
              subtext: '#9CA3AF'
            }
          }
        }
      }
    }
  </script>
  <style>
    body {
      background-color: #0A0A0C;
      color: #F3F4F6;
      font-family: 'Plus Jakarta Sans', sans-serif;
      -webkit-tap-highlight-color: transparent;
      user-select: none;
    }
    input[type="time"], input[type="number"], select, input[type="text"] {
      color-scheme: dark;
    }
    .active-scale:active {
      transform: scale(0.97);
    }
    .neon-border {
      border: 1px solid rgba(168, 85, 247, 0.35);
      box-shadow: 0 0 15px rgba(168, 85, 247, 0.12);
    }
  </style>
</head>
<body class="min-h-screen pb-24 antialiased">

  <!-- Mobile Top Sticky Bar -->
  <header class="sticky top-0 z-30 bg-app-bg/90 backdrop-blur-lg border-b border-app-cardBorder px-4 py-3 flex items-center justify-between">
    <div class="flex items-center gap-2.5">
      <div class="w-9 h-9 rounded-xl bg-app-purple/20 border border-app-purple/40 flex items-center justify-center text-app-purple shadow-sm">
        <i class="ph-bold ph-clock text-xl"></i>
      </div>
      <div>
        <h1 class="text-base font-bold text-white leading-tight">Control de Horas</h1>
        <p class="text-[11px] text-app-subtext font-medium" id="headerContractLabel">Contrato: 20h / semana</p>
      </div>
    </div>

    <div class="flex items-center gap-2">
      <button onclick="openConfigModal()" class="w-9 h-9 rounded-xl bg-app-card border border-app-cardBorder text-gray-300 flex items-center justify-center active-scale">
        <i class="ph-bold ph-gear text-lg"></i>
      </button>
      <button onclick="exportData()" class="w-9 h-9 rounded-xl bg-app-card border border-app-cardBorder text-app-cyan flex items-center justify-center active-scale">
        <i class="ph-bold ph-export text-lg"></i>
      </button>
    </div>
  </header>

  <main class="px-4 pt-4 max-w-lg mx-auto space-y-4">

    <!-- Month Navigation Pill -->
    <div class="bg-app-card p-2 rounded-2xl border border-app-cardBorder flex items-center justify-between">
      <button id="prevMonthBtn" onclick="changeMonth(-1)" class="w-10 h-10 rounded-xl bg-app-bg border border-app-cardBorder flex items-center justify-center text-gray-200 active-scale">
        <i class="ph-bold ph-caret-left text-lg"></i>
      </button>

      <div class="flex items-center gap-1.5">
        <select id="monthSelect" onchange="onMonthYearChange()" class="bg-transparent text-sm font-bold text-white focus:outline-none cursor-pointer py-1">
          <option value="0">Enero</option>
          <option value="1">Febrero</option>
          <option value="2">Marzo</option>
          <option value="3">Abril</option>
          <option value="4">Mayo</option>
          <option value="5">Junio</option>
          <option value="6">Julio</option>
          <option value="7">Agosto</option>
          <option value="8">Septiembre</option>
          <option value="9">Octubre</option>
          <option value="10">Noviembre</option>
          <option value="11">Diciembre</option>
        </select>
        <select id="yearSelect" onchange="onMonthYearChange()" class="bg-transparent text-sm font-bold text-app-purple focus:outline-none cursor-pointer py-1">
          <!-- Populated from 2026 onwards -->
        </select>
      </div>

      <button id="nextMonthBtn" onclick="changeMonth(1)" class="w-10 h-10 rounded-xl bg-app-bg border border-app-cardBorder flex items-center justify-center text-gray-200 active-scale">
        <i class="ph-bold ph-caret-right text-lg"></i>
      </button>
    </div>

    <!-- Main Summary Card (KPIs) -->
    <div class="bg-gradient-to-br from-app-card via-app-card to-app-purple/10 p-4 rounded-2xl neon-border space-y-3">
      <div class="flex justify-between items-center border-b border-app-cardBorder/60 pb-2.5">
        <span class="text-xs uppercase tracking-wider font-semibold text-app-subtext">Resumen Mensual</span>
        <span class="text-xs font-semibold px-2.5 py-0.5 rounded-full bg-app-purple/20 text-app-purple border border-app-purple/30" id="monthBadge">Octubre 2026</span>
      </div>

      <div class="grid grid-cols-3 gap-2 text-center pt-1">
        <!-- Ordinary Hours -->
        <div class="bg-app-bg/60 p-2.5 rounded-xl border border-app-cardBorder">
          <p class="text-[10px] font-medium text-app-subtext uppercase">Base</p>
          <p class="text-lg font-extrabold text-app-cyan" id="kpiBaseHours">0h</p>
        </div>

        <!-- Overtime Hours -->
        <div class="bg-app-bg/60 p-2.5 rounded-xl border border-app-cardBorder">
          <p class="text-[10px] font-medium text-app-subtext uppercase">Extras</p>
          <p class="text-lg font-extrabold text-app-pink" id="kpiExtraHours">+0h</p>
        </div>

        <!-- Grand Total Hours -->
        <div class="bg-app-purple/20 p-2.5 rounded-xl border border-app-purple/40">
          <p class="text-[10px] font-medium text-app-purple uppercase">Total</p>
          <p class="text-lg font-extrabold text-white" id="kpiTotalHours">0h</p>
        </div>
      </div>

      <!-- Contract Overtime Bar -->
      <div class="space-y-1 pt-1">
        <div class="flex justify-between text-[11px] text-app-subtext">
          <span>Suma mensual trabajada</span>
          <span id="contractComparisonText">0 / 80 hrs esperadas</span>
        </div>
        <div class="w-full h-2 rounded-full bg-app-bg overflow-hidden p-0.5 border border-app-cardBorder">
          <div id="contractProgressBar" class="h-full bg-gradient-to-r from-app-cyan to-app-purple rounded-full transition-all duration-300" style="width: 0%"></div>
        </div>
      </div>
    </div>

    <!-- Quick Month Autofill Button -->
    <div class="flex gap-2">
      <button onclick="applyDefaultMonth()" class="flex-1 py-2.5 px-3 bg-app-card hover:bg-app-cardBorder border border-app-cardBorder text-xs font-semibold rounded-xl text-gray-200 flex items-center justify-center gap-1.5 active-scale">
        <i class="ph-bold ph-magic-wand text-app-purple"></i>
        <span>Llenar mes con mi horario habitual</span>
      </button>
    </div>

    <!-- Daily Cards Accordion List -->
    <div id="daysList" class="space-y-3">
      <!-- Generated via JavaScript -->
    </div>

  </main>

  <!-- Quick Edit Modal -->
  <div id="editModal" class="fixed inset-0 z-50 bg-black/80 backdrop-blur-md hidden flex items-end sm:items-center justify-center p-0 sm:p-4">
    <div class="bg-app-card border-t sm:border border-app-cardBorder rounded-t-3xl sm:rounded-2xl w-full max-w-md p-5 space-y-4 shadow-2xl animate-in slide-in-from-bottom duration-200">
      
      <div class="flex justify-between items-center pb-2 border-b border-app-cardBorder">
        <div>
          <h3 class="text-base font-bold text-white" id="modalDayTitle">Editar Día</h3>
          <p class="text-xs text-app-subtext" id="modalDaySubtitle">Lunes 26 de Octubre</p>
        </div>
        <button onclick="closeEditModal()" class="w-8 h-8 rounded-full bg-app-bg text-gray-400 flex items-center justify-center">
          <i class="ph-bold ph-x text-base"></i>
        </button>
      </div>

      <!-- Shift Type Segmented Control -->
      <div class="grid grid-cols-3 gap-1.5 p-1 bg-app-bg rounded-xl border border-app-cardBorder text-xs font-semibold">
        <button id="typeTrabajo" onclick="setModalShiftType('Trabajo')" class="py-2 rounded-lg text-center active-scale transition-all">💼 Trabajo</button>
        <button id="typeDescanso" onclick="setModalShiftType('Descanso')" class="py-2 rounded-lg text-center active-scale transition-all">☕ Descanso</button>
        <button id="typeVacaciones" onclick="setModalShiftType('Vacaciones')" class="py-2 rounded-lg text-center active-scale transition-all">🌴 Vacaciones</button>
      </div>

      <!-- Turn Fields (Visible when Trabajo) -->
      <div id="shiftTimeInputs" class="space-y-3">
        <!-- Turn 1 -->
        <div class="p-3 bg-app-bg/80 rounded-xl border border-app-cardBorder space-y-2">
          <span class="text-[11px] font-bold text-app-purple uppercase tracking-wider">Turno Mañana / Continuo</span>
          <div class="grid grid-cols-2 gap-2">
            <div>
              <label class="block text-[10px] text-app-subtext mb-1">Entrada</label>
              <input type="time" id="mStart1" class="w-full bg-app-card border border-app-cardBorder rounded-lg px-2 py-2 text-xs text-white text-center focus:border-app-purple">
            </div>
            <div>
              <label class="block text-[10px] text-app-subtext mb-1">Salida</label>
              <input type="time" id="mEnd1" class="w-full bg-app-card border border-app-cardBorder rounded-lg px-2 py-2 text-xs text-white text-center focus:border-app-purple">
            </div>
          </div>
        </div>

        <!-- Turn 2 (Partido) -->
        <div class="p-3 bg-app-bg/80 rounded-xl border border-app-cardBorder space-y-2">
          <span class="text-[11px] font-bold text-app-cyan uppercase tracking-wider">Turno Tarde / Noche (Partido)</span>
          <div class="grid grid-cols-2 gap-2">
            <div>
              <label class="block text-[10px] text-app-subtext mb-1">Entrada 2</label>
              <input type="time" id="mStart2" class="w-full bg-app-card border border-app-cardBorder rounded-lg px-2 py-2 text-xs text-white text-center focus:border-app-cyan">
            </div>
            <div>
              <label class="block text-[10px] text-app-subtext mb-1">Salida 2</label>
              <input type="time" id="mEnd2" class="w-full bg-app-card border border-app-cardBorder rounded-lg px-2 py-2 text-xs text-white text-center focus:border-app-cyan">
            </div>
          </div>
        </div>
      </div>

      <!-- Manual Overtime & Notes -->
      <div class="grid grid-cols-2 gap-2">
        <div>
          <label class="block text-[10px] font-bold text-app-pink uppercase mb-1">H. Extras Manuales</label>
          <div class="flex items-center bg-app-bg border border-app-cardBorder rounded-xl px-2 py-1.5">
            <input type="number" id="mExtra" step="0.5" min="0" max="12" placeholder="0" class="w-full bg-transparent text-sm font-bold text-app-pink text-center focus:outline-none">
            <span class="text-xs text-app-subtext pr-1">hrs</span>
          </div>
        </div>
        <div>
          <label class="block text-[10px] font-bold text-app-subtext uppercase mb-1">Nota del día</label>
          <input type="text" id="mNote" placeholder="Ej: Cubrí a Camila" class="w-full bg-app-bg border border-app-cardBorder rounded-xl px-2 py-2 text-xs text-white focus:outline-none focus:border-app-purple">
        </div>
      </div>

      <!-- Quick add buttons inside modal -->
      <div class="flex gap-2">
        <button onclick="addModalExtra(0.5)" class="flex-1 py-1.5 rounded-lg bg-app-pink/10 border border-app-pink/30 text-app-pink text-xs font-bold active-scale">+30 min extra</button>
        <button onclick="addModalExtra(1)" class="flex-1 py-1.5 rounded-lg bg-app-pink/20 border border-app-pink/40 text-app-pink text-xs font-bold active-scale">+1 hora extra</button>
      </div>

      <div class="pt-2 flex gap-2">
        <button onclick="saveModalRecord()" class="w-full py-3 rounded-xl bg-gradient-to-r from-app-purple to-app-cyan text-white text-xs font-extrabold uppercase tracking-wider active-scale">Guardar Cambios</button>
      </div>
    </div>
  </div>

  <!-- Contract Settings Modal -->
  <div id="configModal" class="fixed inset-0 z-50 bg-black/80 backdrop-blur-md hidden flex items-center justify-center p-4">
    <div class="bg-app-card border border-app-cardBorder rounded-2xl w-full max-w-sm p-5 space-y-4 shadow-2xl">
      <div class="flex justify-between items-center border-b border-app-cardBorder pb-2">
        <h3 class="text-sm font-bold text-white flex items-center gap-2">
          <i class="ph-bold ph-sliders text-app-purple"></i> Ajustes de Contrato
        </h3>
        <button onclick="closeConfigModal()" class="text-gray-400">
          <i class="ph-bold ph-x text-base"></i>
        </button>
      </div>

      <div class="space-y-3 text-xs">
        <div>
          <label class="block font-semibold text-gray-300 mb-1">Horas Base Semanales (Según Contrato)</label>
          <input type="number" id="cfgWeeklyBase" value="20" min="1" max="60" class="w-full bg-app-bg border border-app-cardBorder rounded-xl px-3 py-2 text-white font-bold text-sm focus:border-app-purple">
          <p class="text-[10px] text-app-subtext mt-1">El sistema calculará como Horas Extras lo que supere esta base por semana.</p>
        </div>

        <div class="border-t border-app-cardBorder pt-3">
          <label class="block font-semibold text-gray-300 mb-1">Turno Habitual Predeterminado</label>
          <div class="grid grid-cols-2 gap-2 mt-1">
            <div>
              <span class="text-[10px] text-app-subtext">Entrada habitual</span>
              <input type="time" id="cfgDefStart" value="19:00" class="w-full bg-app-bg border border-app-cardBorder rounded-lg p-2 text-white text-center">
            </div>
            <div>
              <span class="text-[10px] text-app-subtext">Salida habitual</span>
              <input type="time" id="cfgDefEnd" value="23:00" class="w-full bg-app-bg border border-app-cardBorder rounded-lg p-2 text-white text-center">
            </div>
          </div>
        </div>
      </div>

      <div class="pt-2 flex gap-2">
        <button onclick="saveConfig()" class="w-full py-2.5 rounded-xl bg-app-purple text-white font-bold text-xs active-scale">Guardar Configuración</button>
      </div>
    </div>
  </div>

  <script>
    // --- APP STATE ---
    const MIN_YEAR = 2026;
    const MIN_MONTH = 9; // Octubre (0-indexed)

    let currentYear = 2026;
    let currentMonth = 9;
    let activeEditingDateKey = null;

    let appConfig = {
      weeklyBase: 20,
      defStart: "19:00",
      defEnd: "23:00"
    };

    let records = {}; // Key: "YYYY-MM-DD"

    const dayNames = ['Domingo', 'Lunes', 'Martes', 'Miércoles', 'Jueves', 'Viernes', 'Sábado'];
    const monthNames = ['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio', 'Julio', 'Agosto', 'Septiembre', 'Octubre', 'Noviembre', 'Diciembre'];

    window.onload = function() {
      loadStorage();
      setupYearSelect();
      syncHeaderAndSelects();
      renderApp();
    };

    function loadStorage() {
      const cfg = localStorage.getItem('m_hours_config');
      if (cfg) { try { appConfig = JSON.parse(cfg); } catch(e){} }

      const rec = localStorage.getItem('m_hours_records');
      if (rec) { try { records = JSON.parse(rec); } catch(e){} }
    }

    function saveStorage() {
      localStorage.setItem('m_hours_config', JSON.stringify(appConfig));
      localStorage.setItem('m_hours_records', JSON.stringify(records));
    }

    function setupYearSelect() {
      const yr = document.getElementById('yearSelect');
      yr.innerHTML = '';
      for (let y = 2026; y <= 2032; y++) {
        const opt = document.createElement('option');
        opt.value = y;
        opt.textContent = y;
        yr.appendChild(opt);
      }
    }

    function syncHeaderAndSelects() {
      document.getElementById('monthSelect').value = currentMonth;
      document.getElementById('yearSelect').value = currentYear;
      document.getElementById('headerContractLabel').textContent = `Contrato: ${appConfig.weeklyBase}h / semana`;
      document.getElementById('monthBadge').textContent = `${monthNames[currentMonth]} ${currentYear}`;

      // Navigation lock (minimum Oct 2026)
      const isStart = (currentYear === MIN_YEAR && currentMonth === MIN_MONTH);
      document.getElementById('prevMonthBtn').disabled = isStart;
      document.getElementById('prevMonthBtn').style.opacity = isStart ? "0.3" : "1";
    }

    function onMonthYearChange() {
      currentMonth = parseInt(document.getElementById('monthSelect').value);
      currentYear = parseInt(document.getElementById('yearSelect').value);

      if (currentYear < MIN_YEAR || (currentYear === MIN_YEAR && currentMonth < MIN_MONTH)) {
        currentYear = MIN_YEAR;
        currentMonth = MIN_MONTH;
      }
      syncHeaderAndSelects();
      renderApp();
    }

    function changeMonth(delta) {
      let m = currentMonth + delta;
      let y = currentYear;
      if (m > 11) { m = 0; y++; }
      if (m < 0) { m = 11; y--; }

      if (y < MIN_YEAR || (y === MIN_YEAR && m < MIN_MONTH)) return;

      currentMonth = m;
      currentYear = y;
      syncHeaderAndSelects();
      renderApp();
    }

    // --- MAIN RENDER & CALCULATIONS ---
    function renderApp() {
      const daysList = document.getElementById('daysList');
      daysList.innerHTML = '';

      const totalDaysInMonth = new Date(currentYear, currentMonth + 1, 0).getDate();

      let monthTotalOrdinary = 0;
      let monthTotalExtra = 0;

      for (let d = 1; d <= totalDaysInMonth; d++) {
        const dateObj = new Date(currentYear, currentMonth, d);
        const dayIdx = dateObj.getDay();
        const dateKey = `${currentYear}-${String(currentMonth + 1).padStart(2, '0')}-${String(d).padStart(2, '0')}`;
        const isWeekend = (dayIdx === 0 || dayIdx === 6);

        let rec = records[dateKey];
        if (!rec) {
          rec = {
            type: isWeekend ? 'Descanso' : 'Trabajo',
            s1: isWeekend ? '' : appConfig.defStart,
            e1: isWeekend ? '' : appConfig.defEnd,
            s2: '',
            e2: '',
            extra: 0,
            note: ''
          };
        }

        const calc = computeDayHours(rec);
        monthTotalOrdinary += calc.ordinary;
        monthTotalExtra += calc.extra;

        // Render Card for Day
        const card = document.createElement('div');
        card.className = `bg-app-card border rounded-2xl p-3.5 space-y-2.5 transition-all ${
          rec.type === 'Descanso' ? 'border-app-cardBorder opacity-80' : 
          rec.type === 'Vacaciones' ? 'border-app-cyan/30 bg-app-cyan/5' : 'border-app-cardBorder hover:border-app-purple/40'
        }`;

        let statusBadge = `<span class="text-[10px] font-bold px-2 py-0.5 rounded-md bg-app-green/20 text-app-green border border-app-green/30">Trabajo</span>`;
        if (rec.type === 'Descanso') statusBadge = `<span class="text-[10px] font-bold px-2 py-0.5 rounded-md bg-app-purple/20 text-app-purple border border-app-purple/30">Descanso</span>`;
        if (rec.type === 'Vacaciones') statusBadge = `<span class="text-[10px] font-bold px-2 py-0.5 rounded-md bg-app-cyan/20 text-app-cyan border border-app-cyan/30">Vacaciones</span>`;

        let turnSummary = "Sin turno anotado";
        if (rec.type === 'Trabajo') {
          let t1 = (rec.s1 && rec.e1) ? `${rec.s1} - ${rec.e1}` : '';
          let t2 = (rec.s2 && rec.e2) ? ` / ${rec.s2} - ${rec.e2}` : '';
          turnSummary = t1 + t2 || "Toque para ingresar turno";
        } else turnSummary = rec.type;

        card.innerHTML = `
          <div class="flex items-center justify-between">
            <div class="flex items-center gap-2.5">
              <div class="w-10 h-10 rounded-xl bg-app-bg border border-app-cardBorder flex flex-col items-center justify-center">
                <span class="text-xs font-extrabold ${isWeekend ? 'text-app-pink' : 'text-white'}">${String(d).padStart(2,'0')}</span>
                <span class="text-[9px] font-semibold text-app-subtext uppercase">${dayNames[dayIdx].substring(0,3)}</span>
              </div>
              <div>
                <div class="flex items-center gap-1.5">
                  <span class="text-xs font-bold text-white">${dayNames[dayIdx]}</span>
                  ${statusBadge}
                </div>
                <p class="text-[11px] text-app-subtext">${turnSummary}</p>
              </div>
            </div>

            <!-- Hours Total Pill -->
            <div class="text-right">
              <span class="text-sm font-extrabold ${calc.total > 0 ? 'text-white' : 'text-app-subtext'}">${calc.total.toFixed(1)}h</span>
              ${calc.extra > 0 ? `<p class="text-[10px] font-bold text-app-pink">+${calc.extra.toFixed(1)}h extra</p>` : ''}
            </div>
          </div>

          ${rec.note ? `<div class="text-[11px] bg-app-bg/80 border border-app-cardBorder px-2.5 py-1 rounded-lg text-gray-300 italic">“${rec.note}”</div>` : ''}

          <!-- Quick Action Buttons Bar -->
          <div class="flex items-center gap-1.5 pt-1 border-t border-app-cardBorder/50">
            <button onclick="openEditModal('${dateKey}')" class="flex-1 py-1.5 rounded-lg bg-app-bg border border-app-cardBorder text-[11px] font-bold text-gray-200 flex items-center justify-center gap-1 active-scale">
              <i class="ph-bold ph-pencil text-app-purple"></i> Editar
            </button>
            <button onclick="quickAddExtra('${dateKey}', 1)" class="py-1.5 px-2.5 rounded-lg bg-app-pink/10 border border-app-pink/30 text-[11px] font-bold text-app-pink active-scale">
              +1h Extra
            </button>
            <button onclick="toggleQuickRest('${dateKey}')" class="py-1.5 px-2.5 rounded-lg bg-app-bg border border-app-cardBorder text-[11px] font-bold text-app-subtext active-scale">
              ${rec.type === 'Descanso' ? '💼' : '☕'}
            </button>
          </div>
        `;

        daysList.appendChild(card);
      }

      // Update KPI Cards
      document.getElementById('kpiBaseHours').textContent = `${monthTotalOrdinary.toFixed(1)}h`;
      document.getElementById('kpiExtraHours').textContent = `+${monthTotalExtra.toFixed(1)}h`;
      document.getElementById('kpiTotalHours').textContent = `${(monthTotalOrdinary + monthTotalExtra).toFixed(1)}h`;

      // Monthly Expected Calculation (WeeklyBase * ~4.33 weeks)
      const expectedMonthly = Math.round(appConfig.weeklyBase * 4.33);
      const grandTotal = monthTotalOrdinary + monthTotalExtra;
      document.getElementById('contractComparisonText').textContent = `${grandTotal.toFixed(1)} / ${expectedMonthly} hrs aprox.`;

      let progressPct = Math.min(100, Math.round((grandTotal / expectedMonthly) * 100));
      document.getElementById('contractProgressBar').style.width = `${progressPct}%`;
    }

    // Helper: Compute Hours for a Record
    function computeDayHours(rec) {
      if (rec.type !== 'Trabajo') return { ordinary: 0, extra: 0, total: 0 };

      let totalMins = 0;

      // Turn 1
      if (rec.s1 && rec.e1) {
        totalMins += getMinutesBetween(rec.s1, rec.e1);
      }
      // Turn 2
      if (rec.s2 && rec.e2) {
        totalMins += getMinutesBetween(rec.s2, rec.e2);
      }

      let totalWorkedHours = totalMins / 60;
      let manualExtra = parseFloat(rec.extra) || 0;

      return {
        ordinary: totalWorkedHours,
        extra: manualExtra,
        total: totalWorkedHours + manualExtra
      };
    }

    function getMinutesBetween(start, end) {
      const [sh, sm] = start.split(':').map(Number);
      const [eh, em] = end.split(':').map(Number);
      let s = sh * 60 + sm;
      let e = eh * 60 + em;
      if (e < s) e += 24 * 60; // Nocturno
      return Math.max(0, e - s);
    }

    // --- QUICK ACTIONS ---
    function quickAddExtra(dateKey, hours) {
      if (!records[dateKey]) {
        records[dateKey] = { type: 'Trabajo', s1: appConfig.defStart, e1: appConfig.defEnd, s2:'', e2:'', extra: 0, note: '' };
      }
      records[dateKey].extra = (parseFloat(records[dateKey].extra) || 0) + hours;
      saveStorage();
      renderApp();
    }

    function toggleQuickRest(dateKey) {
      if (!records[dateKey]) {
        records[dateKey] = { type: 'Descanso', s1: '', e1: '', s2:'', e2:'', extra: 0, note: '' };
      } else {
        records[dateKey].type = records[dateKey].type === 'Descanso' ? 'Trabajo' : 'Descanso';
        if (records[dateKey].type === 'Trabajo' && !records[dateKey].s1) {
          records[dateKey].s1 = appConfig.defStart;
          records[dateKey].e1 = appConfig.defEnd;
        }
      }
      saveStorage();
      renderApp();
    }

    function applyDefaultMonth() {
      if (!confirm("¿Deseas autocompletar este mes con tus turnos habituales (Lunes a Viernes)?")) return;

      const totalDays = new Date(currentYear, currentMonth + 1, 0).getDate();
      for (let d = 1; d <= totalDays; d++) {
        const dateObj = new Date(currentYear, currentMonth, d);
        const dayIdx = dateObj.getDay();
        const dateKey = `${currentYear}-${String(currentMonth + 1).padStart(2, '0')}-${String(d).padStart(2, '0')}`;
        const isWeekend = (dayIdx === 0 || dayIdx === 6);

        records[dateKey] = {
          type: isWeekend ? 'Descanso' : 'Trabajo',
          s1: isWeekend ? '' : appConfig.defStart,
          e1: isWeekend ? '' : appConfig.defEnd,
          s2: '',
          e2: '',
          extra: 0,
          note: ''
        };
      }
      saveStorage();
      renderApp();
    }

    // --- MODAL EDIT ---
    let currentModalShiftType = 'Trabajo';

    function openEditModal(dateKey) {
      activeEditingDateKey = dateKey;
      const rec = records[dateKey] || { type: 'Trabajo', s1: appConfig.defStart, e1: appConfig.defEnd, s2:'', e2:'', extra: 0, note: '' };

      const [y, m, d] = dateKey.split('-');
      const dateObj = new Date(y, parseInt(m)-1, d);
      document.getElementById('modalDayTitle').textContent = `${dayNames[dateObj.getDay()]} ${d}`;
      document.getElementById('modalDaySubtitle').textContent = `${monthNames[parseInt(m)-1]} ${y}`;

      document.getElementById('mStart1').value = rec.s1 || '';
      document.getElementById('mEnd1').value = rec.e1 || '';
      document.getElementById('mStart2').value = rec.s2 || '';
      document.getElementById('mEnd2').value = rec.e2 || '';
      document.getElementById('mExtra').value = rec.extra || '';
      document.getElementById('mNote').value = rec.note || '';

      setModalShiftType(rec.type || 'Trabajo');
      document.getElementById('editModal').classList.remove('hidden');
    }

    function closeEditModal() {
      document.getElementById('editModal').classList.add('hidden');
    }

    function setModalShiftType(type) {
      currentModalShiftType = type;
      const btnT = document.getElementById('typeTrabajo');
      const btnD = document.getElementById('typeDescanso');
      const btnV = document.getElementById('typeVacaciones');
      const inputs = document.getElementById('shiftTimeInputs');

      btnT.className = `py-2 rounded-lg text-center active-scale transition-all ${type==='Trabajo'?'bg-app-green/20 text-app-green border border-app-green/40 font-bold':'text-app-subtext'}`;
      btnD.className = `py-2 rounded-lg text-center active-scale transition-all ${type==='Descanso'?'bg-app-purple/20 text-app-purple border border-app-purple/40 font-bold':'text-app-subtext'}`;
      btnV.className = `py-2 rounded-lg text-center active-scale transition-all ${type==='Vacaciones'?'bg-app-cyan/20 text-app-cyan border border-app-cyan/40 font-bold':'text-app-subtext'}`;

      if (type === 'Trabajo') inputs.classList.remove('hidden');
      else inputs.classList.add('hidden');
    }

    function addModalExtra(hrs) {
      const input = document.getElementById('mExtra');
      let val = parseFloat(input.value) || 0;
      input.value = (val + hrs).toFixed(1);
    }

    function saveModalRecord() {
      if (!activeEditingDateKey) return;

      records[activeEditingDateKey] = {
        type: currentModalShiftType,
        s1: document.getElementById('mStart1').value,
        e1: document.getElementById('mEnd1').value,
        s2: document.getElementById('mStart2').value,
        e2: document.getElementById('mEnd2').value,
        extra: parseFloat(document.getElementById('mExtra').value) || 0,
        note: document.getElementById('mNote').value.trim()
      };

      saveStorage();
      closeEditModal();
      renderApp();
    }

    // --- CONFIG MODAL ---
    function openConfigModal() {
      document.getElementById('cfgWeeklyBase').value = appConfig.weeklyBase;
      document.getElementById('cfgDefStart').value = appConfig.defStart;
      document.getElementById('cfgDefEnd').value = appConfig.defEnd;
      document.getElementById('configModal').classList.remove('hidden');
    }

    function closeConfigModal() {
      document.getElementById('configModal').classList.add('hidden');
    }

    function saveConfig() {
      appConfig.weeklyBase = parseFloat(document.getElementById('cfgWeeklyBase').value) || 20;
      appConfig.defStart = document.getElementById('cfgDefStart').value || "19:00";
      appConfig.defEnd = document.getElementById('cfgDefEnd').value || "23:00";

      saveStorage();
      syncHeaderAndSelects();
      closeConfigModal();
      renderApp();
    }

    // --- EXPORT ---
    function exportData() {
      let csv = "Fecha,Dia,Estado,Entrada 1,Salida 1,Entrada 2,Salida 2,Horas Ordinarias,Horas Extras,Total,Nota\n";      const totalDays = new Date(currentYear, currentMonth + 1, 0).getDate();

      for (let d = 1; d <= totalDays; d++) {
        const dateObj = new Date(currentYear, currentMonth, d);
        const dateKey = `${currentYear}-${String(currentMonth + 1).padStart(2, '0')}-${String(d).padStart(2, '0')}`;
        const rec = records[dateKey] || { type: 'Descanso' };
        const calc = computeDayHours(rec);

        csv += `${dateKey},${dayNames[dateObj.getDay()]},${rec.type||'Trabajo'},${rec.s1||''},${rec.e1||''},${rec.s2||''},${rec.e2||''},${calc.ordinary.toFixed(2)},${calc.extra.toFixed(2)},${calc.total.toFixed(2)},"${(rec.note||'').replace(/"/g, '""')}"\n`;
      }

      const blob = new Blob([csv], { type: 'text/csv;charset=utf-8;' });
      const link = document.createElement("a");
      link.href = URL.createObjectURL(blob);
      link.download = `Horarios_${monthNames[currentMonth]}_${currentYear}.csv`;
      link.click();
    }
  </script>
</body>
</html>

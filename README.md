<!DOCTYPE html>
<html lang="es" class="dark">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>⏰Control de Horarios y Horas Extra</title>
  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- Phosphor Icons for elegant dark icons -->
  <script src="https://unpkg.com/@phosphor-icons/web"></script>
  <!-- Font setup -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet">
  
  <script>
    tailwind.config = {
      darkMode: 'class',
      theme: {
        extend: {
          fontFamily: {
            sans: ['"Plus Jakarta Sans"', 'sans-serif'],
          },
          colors: {
            brand: {
              bg: '#0F0F12',
              card: '#18181F',
              border: '#2A2A36',
              accent: '#8B5CF6', // Soft Violet
              accentHover: '#7C3AED',
              accentGlow: '#8B5CF620',
              plum: '#A78BFA',
              textMuted: '#9CA3AF',
              gold: '#D97706',
            }
          }
        }
      }
    }
  </script>
  <style>
    body {
      background-color: #0F0F12;
      color: #F3F4F6;
      font-family: 'Plus Jakarta Sans', sans-serif;
    }
    /* Custom Scrollbar for sleek aesthetic */
    ::-webkit-scrollbar {
      width: 6px;
      height: 6px;
    }
    ::-webkit-scrollbar-track {
      background: #18181F;
    }
    ::-webkit-scrollbar-thumb {
      background: #2A2A36;
      border-radius: 4px;
    }
    ::-webkit-scrollbar-thumb:hover {
      background: #8B5CF6;
    }
    /* Select styling override */
    select option {
      background-color: #18181F;
      color: #F3F4F6;
    }
    /* Print Styles for professional export */
    @media print {
      .no-print {
        display: none !important;
      }
      body {
        background-color: #fff !important;
        color: #000 !important;
      }
      .print-border {
        border: 1px solid #ccc !important;
      }
      .card-bg {
        background-color: #f9fafb !important;
        color: #000 !important;
        border: 1px solid #e5e7eb !important;
      }
    }
  </style>
</head>
<body class="min-h-screen pb-12 antialiased selection:bg-brand-accent selection:text-white">

  <!-- Header Banner -->
  <header class="border-b border-brand-border bg-brand-card/70 backdrop-blur-md sticky top-0 z-30 no-print">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-4 flex flex-col md:flex-row items-center justify-between gap-4">
      <div class="flex items-center gap-3">
        <div class="p-2.5 rounded-xl bg-brand-accent/10 border border-brand-accent/30 text-brand-accent shadow-lg shadow-brand-accent/5">
          <i class="ph-bold ph-clock-afternoon text-2xl"></i>
        </div>
        <div>
          <h1 class="text-xl font-bold tracking-tight text-white flex items-center gap-2">
            Gestión de Horarios <span class="text-xs font-normal px-2 py-0.5 rounded-full bg-brand-accent/20 text-brand-plum border border-brand-accent/30">v2.0</span>
          </h1>
          <p class="text-xs text-brand-textMuted">Control mensual de horas ordinarias, extras y descansos</p>
        </div>
      </div>

      <!-- Quick Actions / Top Header Bar -->
      <div class="flex flex-wrap items-center gap-2">
        <button onclick="openSettingsModal()" class="px-3.5 py-2 rounded-xl border border-brand-border bg-brand-card hover:bg-brand-border/50 text-sm font-medium transition-all flex items-center gap-2 text-gray-200 hover:text-white shadow-sm">
          <i class="ph-bold ph-gear text-brand-plum"></i>
          <span>Horario Base</span>
        </button>
        <button onclick="exportToCSV()" class="px-3.5 py-2 rounded-xl border border-brand-border bg-brand-card hover:bg-brand-border/50 text-sm font-medium transition-all flex items-center gap-2 text-gray-200 hover:text-white shadow-sm">
          <i class="ph-bold ph-file-csv text-emerald-400"></i>
          <span>Exportar CSV</span>
        </button>
        <button onclick="window.print()" class="px-3.5 py-2 rounded-xl border border-brand-border bg-brand-card hover:bg-brand-border/50 text-sm font-medium transition-all flex items-center gap-2 text-gray-200 hover:text-white shadow-sm">
          <i class="ph-bold ph-printer text-sky-400"></i>
          <span>Imprimir / PDF</span>
        </button>
      </div>
    </div>
  </header>

  <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 pt-8">

    <!-- Month Navigation Bar & Quick Controls -->
    <section class="flex flex-col md:flex-row items-center justify-between gap-4 mb-8 bg-brand-card p-4 rounded-2xl border border-brand-border shadow-xl">
      <div class="flex items-center gap-3">
        <button id="prevMonthBtn" onclick="changeMonth(-1)" class="p-2.5 rounded-xl border border-brand-border bg-brand-bg hover:bg-brand-accent/10 hover:border-brand-accent/50 text-gray-300 hover:text-brand-plum transition-all">
          <i class="ph-bold ph-caret-left text-lg"></i>
        </button>
        <div class="flex items-center gap-2">
          <select id="monthSelect" onchange="onMonthYearChange()" class="bg-brand-bg border border-brand-border text-white text-base font-semibold rounded-xl px-3 py-2 focus:outline-none focus:border-brand-accent cursor-pointer">
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
          <select id="yearSelect" onchange="onMonthYearChange()" class="bg-brand-bg border border-brand-border text-white text-base font-semibold rounded-xl px-3 py-2 focus:outline-none focus:border-brand-accent cursor-pointer">
            <!-- Dynamically populated from 2026 onwards -->
          </select>
        </div>
        <button id="nextMonthBtn" onclick="changeMonth(1)" class="p-2.5 rounded-xl border border-brand-border bg-brand-bg hover:bg-brand-accent/10 hover:border-brand-accent/50 text-gray-300 hover:text-brand-plum transition-all">
          <i class="ph-bold ph-caret-right text-lg"></i>
        </button>
      </div>

      <!-- Quick Template Actions -->
      <div class="flex flex-wrap items-center gap-2 w-full md:w-auto justify-end">
        <button onclick="applyDefaultScheduleToMonth()" class="w-full sm:w-auto px-4 py-2 rounded-xl bg-brand-accent/10 hover:bg-brand-accent/20 border border-brand-accent/30 text-brand-plum text-xs sm:text-sm font-semibold transition-all flex items-center justify-center gap-2">
          <i class="ph-bold ph-magic-wand"></i>
          <span>Autocompletar Mes (Lun-Vie)</span>
        </button>
        <button onclick="resetCurrentMonth()" class="w-full sm:w-auto px-3 py-2 rounded-xl border border-red-500/20 bg-red-500/10 hover:bg-red-500/20 text-red-400 text-xs sm:text-sm font-medium transition-all flex items-center justify-center gap-1.5" title="Reiniciar mes">
          <i class="ph-bold ph-trash"></i>
          <span>Limpiar Mes</span>
        </button>
      </div>
    </section>

    <!-- KPI Summary Dashboard -->
    <section class="grid grid-cols-2 lg:grid-cols-5 gap-3 sm:gap-4 mb-8">
      <!-- Days Worked -->
      <div class="bg-brand-card p-4 rounded-2xl border border-brand-border card-bg shadow-lg relative overflow-hidden group">
        <div class="absolute top-0 right-0 p-3 opacity-10 group-hover:opacity-20 transition-opacity text-emerald-400">
          <i class="ph-bold ph-briefcase text-4xl"></i>
        </div>
        <p class="text-xs font-medium text-brand-textMuted uppercase tracking-wider mb-1">Días Trabajados</p>
        <p id="kpiDaysWorked" class="text-2xl sm:text-3xl font-extrabold text-white">0 <span class="text-xs font-normal text-brand-textMuted">días</span></p>
      </div>

      <!-- Days Off -->
      <div class="bg-brand-card p-4 rounded-2xl border border-brand-border card-bg shadow-lg relative overflow-hidden group">
        <div class="absolute top-0 right-0 p-3 opacity-10 group-hover:opacity-20 transition-opacity text-purple-400">
          <i class="ph-bold ph-coffee text-4xl"></i>
        </div>
        <p class="text-xs font-medium text-brand-textMuted uppercase tracking-wider mb-1">Días Libres</p>
        <p id="kpiDaysOff" class="text-2xl sm:text-3xl font-extrabold text-brand-plum">0 <span class="text-xs font-normal text-brand-textMuted">días</span></p>
      </div>

      <!-- Ordinary Hours -->
      <div class="bg-brand-card p-4 rounded-2xl border border-brand-border card-bg shadow-lg relative overflow-hidden group">
        <div class="absolute top-0 right-0 p-3 opacity-10 group-hover:opacity-20 transition-opacity text-sky-400">
          <i class="ph-bold ph-clock text-4xl"></i>
        </div>
        <p class="text-xs font-medium text-brand-textMuted uppercase tracking-wider mb-1">Horas Ordinarias</p>
        <p id="kpiOrdinaryHours" class="text-2xl sm:text-3xl font-extrabold text-sky-400">0.0 <span class="text-xs font-normal text-brand-textMuted">hrs</span></p>
      </div>

      <!-- Overtime Hours -->
      <div class="bg-brand-card p-4 rounded-2xl border border-brand-border card-bg shadow-lg relative overflow-hidden group">
        <div class="absolute top-0 right-0 p-3 opacity-10 group-hover:opacity-20 transition-opacity text-amber-400">
          <i class="ph-bold ph-lightning text-4xl"></i>
        </div>
        <p class="text-xs font-medium text-brand-textMuted uppercase tracking-wider mb-1">Horas Extra</p>
        <p id="kpiExtraHours" class="text-2xl sm:text-3xl font-extrabold text-amber-400">0.0 <span class="text-xs font-normal text-brand-textMuted">hrs</span></p>
      </div>

      <!-- Grand Total Hours -->
      <div class="col-span-2 lg:col-span-1 bg-gradient-to-br from-brand-accent/20 to-brand-card p-4 rounded-2xl border border-brand-accent/40 card-bg shadow-xl relative overflow-hidden">
        <div class="absolute top-0 right-0 p-3 opacity-15 text-brand-plum">
          <i class="ph-bold ph-calculator text-4xl"></i>
        </div>
        <p class="text-xs font-medium text-brand-plum uppercase tracking-wider mb-1">Gran Total Horas</p>
        <p id="kpiTotalHours" class="text-2xl sm:text-3xl font-extrabold text-white">0.0 <span class="text-xs font-normal text-brand-plum">hrs</span></p>
      </div>
    </section>

    <!-- Spreadsheet Main Table Container -->
    <section class="bg-brand-card rounded-2xl border border-brand-border shadow-2xl overflow-hidden mb-12">
      <div class="overflow-x-auto">
        <table class="w-full text-left border-collapse min-w-[850px]">
          <thead>
            <tr class="bg-brand-bg/90 border-b border-brand-border text-xs uppercase text-brand-textMuted tracking-wider font-semibold">
              <th class="py-3.5 px-4 w-32">Día</th>
              <th class="py-3.5 px-4 w-40">Estado / Tipo</th>
              <th class="py-3.5 px-4 w-28 text-center">Entrada</th>
              <th class="py-3.5 px-4 w-28 text-center">Salida</th>
              <th class="py-3.5 px-4 w-28 text-center">Descanso (m)</th>
              <th class="py-3.5 px-4 w-28 text-center">H. Ordinarias</th>
              <th class="py-3.5 px-4 w-28 text-center">H. Extras</th>
              <th class="py-3.5 px-4 w-28 text-center">Total Día</th>
              <th class="py-3.5 px-4">Notas / Detalle</th>
            </tr>
          </thead>
          <tbody id="scheduleTableBody" class="divide-y divide-brand-border/40 text-sm">
            <!-- Dynamic Spreadsheet Rows Generated via JavaScript -->
          </tbody>
          <tfoot class="bg-brand-bg/90 font-bold border-t border-brand-border">
            <tr>
              <td colspan="5" class="py-4 px-4 text-right text-xs uppercase tracking-wider text-brand-textMuted">Totales Mensuales:</td>
              <td id="footOrdinary" class="py-4 px-4 text-center text-sky-400">0.0h</td>
              <td id="footExtra" class="py-4 px-4 text-center text-amber-400">0.0h</td>
              <td id="footTotal" class="py-4 px-4 text-center text-brand-plum text-base">0.0h</td>
              <td></td>
            </tr>
          </tfoot>
        </table>
      </div>
    </section>
  </main>

  <!-- Settings Modal (Base Schedule Config) -->
  <div id="settingsModal" class="fixed inset-0 z-50 flex items-center justify-center bg-black/70 backdrop-blur-sm hidden opacity-0 transition-opacity duration-200">
    <div class="bg-brand-card border border-brand-border rounded-2xl w-full max-w-md p-6 shadow-2xl transform scale-95 transition-transform duration-200" id="settingsModalCard">
      <div class="flex items-center justify-between pb-4 border-b border-brand-border mb-4">
        <h3 class="text-lg font-bold text-white flex items-center gap-2">
          <i class="ph-bold ph-sliders-horizontal text-brand-plum"></i>
          Configurar Horario Base
        </h3>
        <button onclick="closeSettingsModal()" class="text-brand-textMuted hover:text-white p-1 rounded-lg">
          <i class="ph-bold ph-x text-lg"></i>
        </button>
      </div>

      <p class="text-xs text-brand-textMuted mb-4">
        Define el horario predeterminado que realizas en un día laboral habitual. Este horario se usará al autocompletar el mes.
      </p>

      <div class="space-y-4">
        <div class="grid grid-cols-2 gap-3">
          <div>
            <label class="block text-xs font-semibold text-gray-300 mb-1">Hora Entrada Base</label>
            <input type="time" id="defaultStartTime" value="09:00" class="w-full bg-brand-bg border border-brand-border rounded-xl px-3 py-2 text-white focus:outline-none focus:border-brand-accent">
          </div>
          <div>
            <label class="block text-xs font-semibold text-gray-300 mb-1">Hora Salida Base</label>
            <input type="time" id="defaultEndTime" value="18:00" class="w-full bg-brand-bg border border-brand-border rounded-xl px-3 py-2 text-white focus:outline-none focus:border-brand-accent">
          </div>
        </div>

        <div>
          <label class="block text-xs font-semibold text-gray-300 mb-1">Descanso Predeterminado (Minutos)</label>
          <input type="number" id="defaultBreakMinutes" value="60" min="0" max="240" step="15" class="w-full bg-brand-bg border border-brand-border rounded-xl px-3 py-2 text-white focus:outline-none focus:border-brand-accent">
        </div>

        <div>
          <label class="block text-xs font-semibold text-gray-300 mb-1">Tope Horas Ordinarias / Día</label>
          <input type="number" id="defaultMaxOrdinary" value="8" min="1" max="24" step="0.5" class="w-full bg-brand-bg border border-brand-border rounded-xl px-3 py-2 text-white focus:outline-none focus:border-brand-accent">
          <span class="text-[10px] text-brand-textMuted mt-1 block">El exceso de horas calculadas pasará automáticamente a Horas Extras.</span>
        </div>
      </div>

      <div class="mt-6 flex items-center justify-end gap-3 pt-4 border-t border-brand-border">
        <button onclick="closeSettingsModal()" class="px-4 py-2 rounded-xl text-xs font-semibold text-brand-textMuted hover:text-white border border-brand-border">Cancelar</button>
        <button onclick="saveSettings()" class="px-4 py-2 rounded-xl bg-brand-accent hover:bg-brand-accentHover text-white text-xs font-semibold transition-all">Guardar Configuración</button>
      </div>
    </div>
  </div>

  <!-- Notification Toast -->
  <div id="toast" class="fixed bottom-5 right-5 z-50 bg-brand-card border border-brand-accent/40 text-white px-4 py-3 rounded-xl shadow-2xl flex items-center gap-3 transform translate-y-20 opacity-0 transition-all duration-300 pointer-events-none">
    <i class="ph-bold ph-check-circle text-emerald-400 text-xl" id="toastIcon"></i>
    <span id="toastMsg" class="text-xs font-medium">Configuración guardada</span>
  </div>

  <script>
    // --- Application State ---
    const START_YEAR = 2026;
    const START_MONTH = 9; // October (0-indexed)

    let currentYear = START_YEAR;
    let currentMonth = START_MONTH;

    // Config defaults stored in localStorage
    let userConfig = {
      defaultStartTime: "09:00",
      defaultEndTime: "18:00",
      defaultBreakMinutes: 60,
      defaultMaxOrdinary: 8
    };

    // Store data per date key "YYYY-MM-DD"
    let records = {};

    // Days of week Spanish labels
    const dayNames = ['Domingo', 'Lunes', 'Martes', 'Miércoles', 'Jueves', 'Viernes', 'Sábado'];
    const monthNames = ['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio', 'Julio', 'Agosto', 'Septiembre', 'Octubre', 'Noviembre', 'Diciembre'];

    // --- Core Lifecycle ---
    window.onload = function() {
      loadLocalStorage();
      initYearSelector();
      setSelectValues();
      renderTable();
    };

    function loadLocalStorage() {
      const savedConfig = localStorage.getItem('hours_tracker_config');
      if (savedConfig) {
        try { userConfig = JSON.parse(savedConfig); } catch(e){}
      }
      const savedRecords = localStorage.getItem('hours_tracker_records');
      if (savedRecords) {
        try { records = JSON.parse(savedRecords); } catch(e){}
      }
    }

    function saveToLocalStorage() {
      localStorage.setItem('hours_tracker_config', JSON.stringify(userConfig));
      localStorage.setItem('hours_tracker_records', JSON.stringify(records));
    }

    function initYearSelector() {
      const yearSelect = document.getElementById('yearSelect');
      yearSelect.innerHTML = '';
      for (let y = 2026; y <= 2035; y++) {
        const opt = document.createElement('option');
        opt.value = y;
        opt.textContent = y;
        yearSelect.appendChild(opt);
      }
    }

    function setSelectValues() {
      document.getElementById('monthSelect').value = currentMonth;
      document.getElementById('yearSelect').value = currentYear;
      updateMonthNavButtons();
    }

    function updateMonthNavButtons() {
      // Disable navigation prior to October 2026
      const isStart = (currentYear === START_YEAR && currentMonth === START_MONTH);
      document.getElementById('prevMonthBtn').disabled = isStart;
      if(isStart) {
        document.getElementById('prevMonthBtn').classList.add('opacity-30', 'cursor-not-allowed');
      } else {
        document.getElementById('prevMonthBtn').classList.remove('opacity-30', 'cursor-not-allowed');
      }
    }

    function onMonthYearChange() {
      currentMonth = parseInt(document.getElementById('monthSelect').value);
      currentYear = parseInt(document.getElementById('yearSelect').value);
      
      // Guard enforcement: minimum date Oct 2026
      if (currentYear < START_YEAR || (currentYear === START_YEAR && currentMonth < START_MONTH)) {
        currentYear = START_YEAR;
        currentMonth = START_MONTH;
        setSelectValues();
      }
      
      updateMonthNavButtons();
      renderTable();
    }

    function changeMonth(delta) {
      let newMonth = currentMonth + delta;
      let newYear = currentYear;

      if (newMonth > 11) {
        newMonth = 0;
        newYear++;
      } else if (newMonth < 0) {
        newMonth = 11;
        newYear--;
      }

      if (newYear < START_YEAR || (newYear === START_YEAR && newMonth < START_MONTH)) {
        return; // Restrict earlier than Oct 2026
      }

      currentMonth = newMonth;
      currentYear = newYear;
      setSelectValues();
      renderTable();
    }

    // --- Table Rendering & Calculations ---
    function renderTable() {
      const tbody = document.getElementById('scheduleTableBody');
      tbody.innerHTML = '';

      const daysInMonth = new Date(currentYear, currentMonth + 1, 0).getDate();

      let kpiWorked = 0;
      let kpiOff = 0;
      let totalOrdinary = 0;
      let totalExtra = 0;

      for (let d = 1; d <= daysInMonth; d++) {
        const dateObj = new Date(currentYear, currentMonth, d);
        const dayOfWeekIndex = dateObj.getDay();
        const dateKey = `${currentYear}-${String(currentMonth + 1).padStart(2, '0')}-${String(d).padStart(2, '0')}`;
        const isWeekend = (dayOfWeekIndex === 0 || dayOfWeekIndex === 6);

        // Fetch or init record
        let rec = records[dateKey];
        if (!rec) {
          rec = {
            type: isWeekend ? 'Libre' : 'Trabajo',
            startTime: isWeekend ? '' : userConfig.defaultStartTime,
            endTime: isWeekend ? '' : userConfig.defaultEndTime,
            breakMinutes: isWeekend ? 0 : userConfig.defaultBreakMinutes,
            manualExtra: 0,
            notes: ''
          };
        }

        // Calculate hours based on inputs
        const calc = calculateHours(rec);

        // Update Stats
        if (rec.type === 'Trabajo') kpiWorked++;
        if (rec.type === 'Libre') kpiOff++;
        totalOrdinary += calc.ordinary;
        totalExtra += calc.extra;

        // Build Table Row
        const tr = document.createElement('tr');
        tr.className = `transition-colors hover:bg-brand-border/20 ${isWeekend ? 'bg-brand-bg/40' : ''}`;

        // Highlight Libre/Vacaciones visually
        let typeBadgeColor = 'text-emerald-400 bg-emerald-500/10 border-emerald-500/20';
        if (rec.type === 'Libre') typeBadgeColor = 'text-purple-400 bg-purple-500/10 border-purple-500/20';
        if (rec.type === 'Vacaciones') typeBadgeColor = 'text-sky-400 bg-sky-500/10 border-sky-500/20';
        if (rec.type === 'Licencia') typeBadgeColor = 'text-amber-400 bg-amber-500/10 border-amber-500/20';

        tr.innerHTML = `
          <!-- Date / Day -->
          <td class="py-2.5 px-4 font-medium text-gray-200">
            <div class="flex items-center gap-2">
              <span class="text-base font-bold ${isWeekend ? 'text-brand-plum' : 'text-white'}">${String(d).padStart(2, '0')}</span>
              <span class="text-xs text-brand-textMuted">${dayNames[dayOfWeekIndex].substring(0,3)}</span>
            </div>
          </td>

          <!-- Type / Status Select -->
          <td class="py-2.5 px-4">
            <select onchange="updateRecord('${dateKey}', 'type', this.value)" class="w-full bg-brand-bg border border-brand-border text-xs rounded-lg px-2 py-1.5 focus:outline-none focus:border-brand-accent ${typeBadgeColor} border">
              <option value="Trabajo" ${rec.type === 'Trabajo' ? 'selected' : ''}>💼 Trabajo</option>
              <option value="Libre" ${rec.type === 'Libre' ? 'selected' : ''}>☕ Libre</option>
              <option value="Vacaciones" ${rec.type === 'Vacaciones' ? 'selected' : ''}>🌴 Vacaciones</option>
              <option value="Licencia" ${rec.type === 'Licencia' ? 'selected' : ''}>🏥 Licencia</option>
            </select>
          </td>

          <!-- Entrada -->
          <td class="py-2.5 px-4 text-center">
            <input type="time" value="${rec.startTime || ''}" ${rec.type !== 'Trabajo' ? 'disabled' : ''} onchange="updateRecord('${dateKey}', 'startTime', this.value)" class="w-full text-center bg-brand-bg border border-brand-border text-xs text-white rounded-lg px-1.5 py-1.5 focus:outline-none focus:border-brand-accent disabled:opacity-30 disabled:cursor-not-allowed">
          </td>

          <!-- Salida -->
          <td class="py-2.5 px-4 text-center">
            <input type="time" value="${rec.endTime || ''}" ${rec.type !== 'Trabajo' ? 'disabled' : ''} onchange="updateRecord('${dateKey}', 'endTime', this.value)" class="w-full text-center bg-brand-bg border border-brand-border text-xs text-white rounded-lg px-1.5 py-1.5 focus:outline-none focus:border-brand-accent disabled:opacity-30 disabled:cursor-not-allowed">
          </td>

          <!-- Descanso (Minutos) -->
          <td class="py-2.5 px-4 text-center">
            <input type="number" min="0" max="240" step="5" value="${rec.breakMinutes !== undefined ? rec.breakMinutes : 0}" ${rec.type !== 'Trabajo' ? 'disabled' : ''} onchange="updateRecord('${dateKey}', 'breakMinutes', parseFloat(this.value)||0)" class="w-20 text-center bg-brand-bg border border-brand-border text-xs text-white rounded-lg px-1.5 py-1.5 focus:outline-none focus:border-brand-accent disabled:opacity-30 disabled:cursor-not-allowed">
          </td>

          <!-- H. Ordinarias (Calculadas) -->
          <td class="py-2.5 px-4 text-center font-semibold text-sky-400">
            ${calc.ordinary.toFixed(1)}h
          </td>

          <!-- H. Extras (Ingreso numérico manual o suplementario) -->
          <td class="py-2.5 px-4 text-center">
            <input type="number" min="0" max="24" step="0.5" value="${rec.manualExtra || (calc.calculatedExtra > 0 ? calc.calculatedExtra : '')}" ${rec.type !== 'Trabajo' && rec.type !== 'Libre' ? 'disabled' : ''} placeholder="${calc.calculatedExtra > 0 ? calc.calculatedExtra.toFixed(1) : '0'}" onchange="updateRecord('${dateKey}', 'manualExtra', parseFloat(this.value)||0)" class="w-20 text-center bg-brand-bg border border-brand-border text-xs text-amber-400 font-bold rounded-lg px-1.5 py-1.5 focus:outline-none focus:border-brand-accent disabled:opacity-30 disabled:cursor-not-allowed">
          </td>

          <!-- Total Día -->
          <td class="py-2.5 px-4 text-center font-bold text-white">
            ${calc.total.toFixed(1)}h
          </td>

          <!-- Notas -->
          <td class="py-2.5 px-4">
            <input type="text" value="${rec.notes || ''}" placeholder="Escribir nota..." onchange="updateRecord('${dateKey}', 'notes', this.value)" class="w-full bg-brand-bg/50 border border-brand-border text-xs text-gray-300 rounded-lg px-2 py-1.5 focus:outline-none focus:border-brand-accent placeholder-brand-textMuted/40">
          </td>
        `;

        tbody.appendChild(tr);
      }

      // Update KPI Cards
      document.getElementById('kpiDaysWorked').innerHTML = `${kpiWorked} <span class="text-xs font-normal text-brand-textMuted">días</span>`;
      document.getElementById('kpiDaysOff').innerHTML = `${kpiOff} <span class="text-xs font-normal text-brand-textMuted">días</span>`;
      document.getElementById('kpiOrdinaryHours').innerHTML = `${totalOrdinary.toFixed(1)} <span class="text-xs font-normal text-brand-textMuted">hrs</span>`;
      document.getElementById('kpiExtraHours').innerHTML = `${totalExtra.toFixed(1)} <span class="text-xs font-normal text-brand-textMuted">hrs</span>`;
      document.getElementById('kpiTotalHours').innerHTML = `${(totalOrdinary + totalExtra).toFixed(1)} <span class="text-xs font-normal text-brand-plum">hrs</span>`;

      // Update Footer Totals
      document.getElementById('footOrdinary').textContent = `${totalOrdinary.toFixed(1)}h`;
      document.getElementById('footExtra').textContent = `${totalExtra.toFixed(1)}h`;
      document.getElementById('footTotal').textContent = `${(totalOrdinary + totalExtra).toFixed(1)}h`;
    }

    // Hours Calculation Helper
    function calculateHours(rec) {
      if (rec.type !== 'Trabajo' && rec.type !== 'Libre') {
        return { ordinary: 0, calculatedExtra: 0, extra: 0, total: 0 };
      }

      let ordinary = 0;
      let calculatedExtra = 0;

      if (rec.type === 'Trabajo' && rec.startTime && rec.endTime) {
        const [startH, startM] = rec.startTime.split(':').map(Number);
        const [endH, endM] = rec.endTime.split(':').map(Number);

        let startInMinutes = startH * 60 + startM;
        let endInMinutes = endH * 60 + endM;

        // Handle overnight shifts if end < start
        if (endInMinutes < startInMinutes) {
          endInMinutes += 24 * 60;
        }

        let totalWorkedMinutes = endInMinutes - startInMinutes - (rec.breakMinutes || 0);
        if (totalWorkedMinutes < 0) totalWorkedMinutes = 0;

        let totalWorkedHours = totalWorkedMinutes / 60;

        const maxOrd = userConfig.defaultMaxOrdinary || 8;
        if (totalWorkedHours > maxOrd) {
          ordinary = maxOrd;
          calculatedExtra = totalWorkedHours - maxOrd;
        } else {
          ordinary = totalWorkedHours;
          calculatedExtra = 0;
        }
      }

      // If user provided manual extra input, use manual extra; otherwise use calculated auto-extra
      const extra = (rec.manualExtra !== undefined && rec.manualExtra !== null && rec.manualExtra !== 0) 
        ? rec.manualExtra 
        : calculatedExtra;

      return {
        ordinary: ordinary,
        calculatedExtra: calculatedExtra,
        extra: extra,
        total: ordinary + extra
      };
    }

    function updateRecord(dateKey, field, value) {
      if (!records[dateKey]) {
        records[dateKey] = {
          type: 'Trabajo',
          startTime: userConfig.defaultStartTime,
          endTime: userConfig.defaultEndTime,
          breakMinutes: userConfig.defaultBreakMinutes,
          manualExtra: 0,
          notes: ''
        };
      }

      records[dateKey][field] = value;

      // If changing to libre/vacaciones, clear or auto adapt
      if (field === 'type' && value !== 'Trabajo') {
        if (value === 'Libre') {
          records[dateKey].startTime = '';
          records[dateKey].endTime = '';
          records[dateKey].breakMinutes = 0;
        }
      } else if (field === 'type' && value === 'Trabajo' && !records[dateKey].startTime) {
        records[dateKey].startTime = userConfig.defaultStartTime;
        records[dateKey].endTime = userConfig.defaultEndTime;
        records[dateKey].breakMinutes = userConfig.defaultBreakMinutes;
      }

      saveToLocalStorage();
      renderTable();
    }

    // --- Bulk Schedule Actions ---
    function applyDefaultScheduleToMonth() {
      const daysInMonth = new Date(currentYear, currentMonth + 1, 0).getDate();

      for (let d = 1; d <= daysInMonth; d++) {
        const dateObj = new Date(currentYear, currentMonth, d);
        const dayOfWeekIndex = dateObj.getDay();
        const dateKey = `${currentYear}-${String(currentMonth + 1).padStart(2, '0')}-${String(d).padStart(2, '0')}`;
        const isWeekend = (dayOfWeekIndex === 0 || dayOfWeekIndex === 6);

        if (!records[dateKey]) {
          records[dateKey] = {};
        }

        if (isWeekend) {
          records[dateKey].type = 'Libre';
          records[dateKey].startTime = '';
          records[dateKey].endTime = '';
          records[dateKey].breakMinutes = 0;
        } else {
          records[dateKey].type = 'Trabajo';
          records[dateKey].startTime = userConfig.defaultStartTime;
          records[dateKey].endTime = userConfig.defaultEndTime;
          records[dateKey].breakMinutes = userConfig.defaultBreakMinutes;
        }
      }

      saveToLocalStorage();
      renderTable();
      showToast('Horario base aplicado a lunes-viernes de este mes');
    }

    function resetCurrentMonth() {
      if (!confirm('¿Seguro que deseas limpiar los registros de este mes?')) return;

      const daysInMonth = new Date(currentYear, currentMonth + 1, 0).getDate();
      for (let d = 1; d <= daysInMonth; d++) {
        const dateKey = `${currentYear}-${String(currentMonth + 1).padStart(2, '0')}-${String(d).padStart(2, '0')}`;
        delete records[dateKey];
      }

      saveToLocalStorage();
      renderTable();
      showToast('Registros del mes reiniciados');
    }

    // --- Settings Modal Handlers ---
    function openSettingsModal() {
      document.getElementById('defaultStartTime').value = userConfig.defaultStartTime;
      document.getElementById('defaultEndTime').value = userConfig.defaultEndTime;
      document.getElementById('defaultBreakMinutes').value = userConfig.defaultBreakMinutes;
      document.getElementById('defaultMaxOrdinary').value = userConfig.defaultMaxOrdinary;

      const modal = document.getElementById('settingsModal');
      const card = document.getElementById('settingsModalCard');
      modal.classList.remove('hidden');
      setTimeout(() => {
        modal.classList.remove('opacity-0');
        card.classList.remove('scale-95');
      }, 10);
    }

    function closeSettingsModal() {
      const modal = document.getElementById('settingsModal');
      const card = document.getElementById('settingsModalCard');
      modal.classList.add('opacity-0');
      card.classList.add('scale-95');
      setTimeout(() => {
        modal.classList.add('hidden');
      }, 200);
    }

    function saveSettings() {
      userConfig.defaultStartTime = document.getElementById('defaultStartTime').value;
      userConfig.defaultEndTime = document.getElementById('defaultEndTime').value;
      userConfig.defaultBreakMinutes = parseFloat(document.getElementById('defaultBreakMinutes').value) || 0;
      userConfig.defaultMaxOrdinary = parseFloat(document.getElementById('defaultMaxOrdinary').value) || 8;

      saveToLocalStorage();
      closeSettingsModal();
      renderTable();
      showToast('Configuración del horario base guardada');
    }

    // --- CSV Export Functionality ---
    function exportToCSV() {
      const daysInMonth = new Date(currentYear, currentMonth + 1, 0).getDate();
      let csvContent = "data:text/csv;charset=utf-8,";
      csvContent += "Fecha,Dia,Estado,Hora Entrada,Hora Salida,Descanso (min),Horas Ordinarias,Horas Extras,Total Horas,Notas\n";

      for (let d = 1; d <= daysInMonth; d++) {
        const dateObj = new Date(currentYear, currentMonth, d);
        const dayOfWeekIndex = dateObj.getDay();
        const dateKey = `${currentYear}-${String(currentMonth + 1).padStart(2, '0')}-${String(d).padStart(2, '0')}`;
        const rec = records[dateKey] || { type: (dayOfWeekIndex===0||dayOfWeekIndex===6)?'Libre':'Trabajo' };
        const calc = calculateHours(rec);

        const row = [
          dateKey,
          dayNames[dayOfWeekIndex],
          rec.type || 'Trabajo',
          rec.startTime || '',
          rec.endTime || '',
          rec.breakMinutes || 0,
          calc.ordinary.toFixed(2),
          calc.extra.toFixed(2),
          calc.total.toFixed(2),
          `"${(rec.notes || '').replace(/"/g, '""')}"`
        ];

        csvContent += row.join(",") + "\n";
      }

      const encodedUri = encodeURI(csvContent);
      const link = document.createElement("a");
      link.setAttribute("href", encodedUri);
      link.setAttribute("download", `Horarios_${monthNames[currentMonth]}_${currentYear}.csv`);
      document.body.appendChild(link);
      link.click();
      document.body.removeChild(link);

      showToast('Archivo CSV descargado con éxito');
    }

    // --- Toast UI helper ---
    function showToast(msg) {
      const toast = document.getElementById('toast');
      document.getElementById('toastMsg').textContent = msg;
      toast.classList.remove('translate-y-20', 'opacity-0');
      setTimeout(() => {
        toast.classList.add('translate-y-20', 'opacity-0');
      }, 3000);
    }
  </script>
</body>
</html>

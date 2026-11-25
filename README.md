# RAHIL
<body>

<div class="app">

    <aside class="sidebar">
        Navigation
    </aside>

    <main class="dashboard">

        <header class="topbar">
            Search | Notifications | Profile
        </header>

        <section class="kpis">
            Revenue
            Orders
            Customers
            Profit
        </section>

        <section class="analytics">

            <div class="sales-chart"></div>

            <div class="customer-chart"></div>

        </section>

        <section class="data-grid">

            <table>
                Business Data
            </table>

        </section>

    </main>

</div>

</body>
:root{
  --bg:#0b1120;
  --panel:#111827;
  --card:#1e293b;
  --border:#334155;
  --primary:#38bdf8;
  --success:#22c55e;
  --warning:#f59e0b;
  --danger:#ef4444;
  --text:#ffffff;
  --muted:#94a3b8;
}

*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family:'Segoe UI',sans-serif;
}

body{
  background:var(--bg);
  color:var(--text);
  min-height:100vh;
}

.app{
  display:grid;
  grid-template-columns:280px 1fr;
  min-height:100vh;
}

/* SIDEBAR */

.sidebar{
  background:var(--panel);
  border-right:1px solid var(--border);
  padding:25px;
}

.logo{
  font-size:28px;
  font-weight:700;
  color:var(--primary);
  margin-bottom:40px;
}

.nav{
  display:flex;
  flex-direction:column;
  gap:10px;
}

.nav a{
  text-decoration:none;
  color:var(--muted);
  padding:14px;
  border-radius:12px;
  transition:.3s;
}

.nav a:hover{
  background:#263244;
  color:white;
}

/* MAIN */

.main{
  padding:30px;
}

.topbar{
  display:flex;
  justify-content:space-between;
  align-items:center;
  margin-bottom:25px;
}

.search{
  width:350px;
  padding:12px;
  background:#1e293b;
  border:none;
  border-radius:10px;
  color:white;
}

.profile{
  display:flex;
  align-items:center;
  gap:15px;
}

.avatar{
  width:45px;
  height:45px;
  border-radius:50%;
  background:var(--primary);
}

/* KPI CARDS */

.kpis{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(240px,1fr));
  gap:20px;
  margin-bottom:25px;
}

.card{
  background:var(--card);
  padding:20px;
  border-radius:18px;
  border:1px solid var(--border);
  transition:.3s;
}

.card:hover{
  transform:translateY(-5px);
}

.card-title{
  color:var(--muted);
  margin-bottom:10px;
}

.metric{
  font-size:35px;
  font-weight:800;
}

.growth-up{
  color:var(--success);
}

.growth-down{
  color:var(--danger);
}

/* CHART AREA */

.analytics{
  display:grid;
  grid-template-columns:2fr 1fr;
  gap:20px;
  margin-bottom:25px;
}

.chart{
  background:var(--card);
  padding:20px;
  border-radius:18px;
  border:1px solid var(--border);
  min-height:380px;
}

.widget{
  background:var(--card);
  border:1px solid var(--border);
  padding:20px;
  border-radius:18px;
  margin-bottom:20px;
}

/* TABLE */

.data-table{
  background:var(--card);
  padding:20px;
  border-radius:18px;
  border:1px solid var(--border);
  overflow:auto;
}

table{
  width:100%;
  border-collapse:collapse;
}

th{
  text-align:left;
  background:#243041;
  padding:16px;
}

td{
  padding:16px;
  border-bottom:1px solid var(--border);
}

tr:hover{
  background:#243041;
}

/* PROGRESS BARS */

.progress{
  height:10px;
  width:100%;
  background:#334155;
  border-radius:50px;
  overflow:hidden;
}

.progress-bar{
  height:100%;
  background:linear-gradient(
      90deg,
      #38bdf8,
      #22c55e
  );
}

/* GLASS EFFECT */

.glass{
  backdrop-filter
  // ========== KPI COUNTERS ==========

function animateValue(id, start, end, duration) {
    let current = start;
    const range = end - start;
    const stepTime = Math.abs(Math.floor(duration / range));

    const timer = setInterval(() => {
        current += 1;

        document.getElementById(id).innerText =
            current.toLocaleString();

        if (current >= end) {
            clearInterval(timer);
        }
    }, stepTime);
}

animateValue("revenue", 0, 12800000, 1000);
animateValue("customers", 0, 38421, 1000);
animateValue("orders", 0, 92300, 1000);
animateValue("profit", 0, 5400000, 1000);

// ========== LIVE CLOCK ==========

function updateClock() {
    const clock = document.getElementById("clock");

    if (!clock) return;

    const now = new Date();

    clock.innerHTML =
        now.toLocaleDateString() +
        " | " +
        now.toLocaleTimeString();
}

setInterval(updateClock, 1000);
updateClock();

// ========== REAL-TIME DASHBOARD DATA ==========

function updateMetrics() {

    const revenue =
        document.getElementById("revenue");

    const orders =
        document.getElementById("orders");

    if (!revenue || !orders) return;

    const currentRevenue =
        parseInt(
            revenue

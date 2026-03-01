<template>
  <div class="dashboard-wrap">
  <div class="dashboard">

    <!-- ── Hover zone: LEFT edge → Profile card floats in ── -->
    <div class="hover-zone zone-left">
      <div class="float-card prof-card">
        <div class="prof-av">R</div>
        <div class="prof-info">
          <div class="prof-sched">Scheduled on 5 Apr at 19:05</div>
          <div class="prof-name">Ramsey 🎧</div>
          <div class="prof-stats">
            <span>♡ —</span>
            <span>↺ —</span>
            <span>💬 —</span>
          </div>
        </div>
      </div>
    </div>

    <!-- ── Hover zone: RIGHT edge → Todo card floats in ── -->
    <div class="hover-zone zone-right">
      <div class="float-card todo-card">
        <div class="todo-hd">
          <div class="panel-title">To-do list</div>
          <div class="todo-date">Wednesday, 11 May</div>
          <button class="todo-x">×</button>
        </div>
        <div class="todo-list">
          <div v-for="task in todos" :key="task.id" class="todo-row">
            <div class="todo-l">
              <input type="checkbox" :checked="task.done" class="todo-chk" />
              <div>
                <div class="todo-nm" :class="{ done: task.done }">{{ task.label }}</div>
                <div v-if="task.sub" class="todo-tm">{{ task.sub }}</div>
              </div>
            </div>
            <span class="todo-tag" :class="task.tagClass">{{ task.tagLabel }}</span>
          </div>
        </div>
      </div>
    </div>

    <!-- ── Full-height Sidebar ── -->
    <div class="d-sidebar">
      <img :src="HouseLine" alt="home"     class="d-s-icon active" />
      <img :src="TrendUp"   alt="trend"    class="d-s-icon" />
      <img :src="UserThree" alt="users"    class="d-s-icon" />
      <img :src="MoneyWavy" alt="money"    class="d-s-icon" />
      <img :src="GearSix"   alt="settings" class="d-s-icon" />
      <img :src="Info"      alt="info"     class="d-s-icon" />
    </div>

    <!-- ── Right: Topbar + Body ── -->
    <div class="d-content">

      <!-- Top Bar -->
      <div class="d-topbar">
        <div class="d-topbar-l">
          <div class="d-divider"></div>
          <div>
            <div class="d-title">Welcome back, John</div>
            <div class="d-sub">Statistics overview</div>
          </div>
        </div>
        <div class="d-topbar-r">
          <div class="d-search">
            <span class="d-search-ico">⌕</span>
            <span class="d-search-ph">Search</span>
          </div>
          <div class="d-ico-row">
            <img :src="bell" class="d-ico-img" />
            <span class="d-ico">✉</span>
            <img :src="profile" class="d-avatar" />
          </div>
        </div>
      </div>

      <!-- Subheader row -->
      <div class="d-subbar">
        <div class="week-pill">This week ▾</div>
        <div class="last-updated">Last updated at 10:22 AM</div>
      </div>

      <!-- Main area -->
      <div class="d-main">

        <!-- Left Panel -->
        <div class="d-left">
          <div class="stats-grid">
            <div class="s-card">
              <div class="s-top">
                <div class="s-lbl">New subscribers</div>
                <div class="s-badge up">10% ↑</div>
              </div>
              <div class="s-val-row">
                <div class="s-val">1,324</div>
                <span class="s-unit">People</span>
                <span class="s-ico-r">👤</span>
              </div>
            </div>
            <div class="s-card">
              <div class="s-top">
                <div class="s-lbl">Total views</div>
                <div class="s-badge up">5% ↑</div>
              </div>
              <div class="s-val-row">
                <div class="s-val">12.1M</div>
                <span class="s-unit">Views</span>
                <span class="s-ico-r">👁</span>
              </div>
            </div>
            <div class="s-card">
              <div class="s-top">
                <div class="s-lbl">Engagement rate</div>
                <div class="s-badge dn">12% ↓</div>
              </div>
              <div class="s-val-row">
                <div class="s-val">56%</div>
                <span class="s-unit">percent</span>
                <span class="s-ico-r">♡</span>
              </div>
            </div>
          </div>

          <!-- Chart -->
          <div class="chart-card">
            <div class="chart-hd-row">
              <div class="chart-hd">Daily visitors</div>
              <span class="chart-more">···</span>
            </div>
            <div class="bars">
              <div
                v-for="(h, i) in barHeights"
                :key="i"
                class="bar-col"
                :class="{ hi: i === highlightIdx }"
              >
                <div class="bar" :style="{ height: h + 'px' }">
                  <div v-if="i === highlightIdx" class="bar-tt">
                    <span class="tt-val">+6637</span>
                    <span class="tt-date">Feb 7</span>
                  </div>
                </div>
              </div>
            </div>
            <div class="x-axis">
              <span>22</span>
              <span>28</span>
              <span>January</span>
              <span>2</span>
              <span>8</span>
              <span>14</span>
              <span>February</span>
              <span>March</span>
            </div>
          </div>
        </div>

        <!-- Right Panel -->
        <div class="d-right">
          <div class="integ-panel">
            <div class="panel-title">Integrations</div>
            <div class="integ-list">
              <div v-for="item in integrations" :key="item.name + item.idx" class="integ-row">
                <div class="i-ico" :style="{ background: item.color }">{{ item.symbol }}</div>
                <div class="i-info">
                  <div class="i-name">{{ item.name }}</div>
                  <div class="i-sub">12 loho.207</div>
                </div>
                <button class="i-btn" :class="item.connected ? 'on' : 'off'">
                  {{ item.connected ? 'Connected' : 'Connect' }}
                </button>
              </div>
            </div>
          </div>
        </div>

      </div>
    </div>
  </div><!-- /.dashboard -->
  </div><!-- /.dashboard-wrap -->
</template>

<script setup>
import GearSix   from '../assets/svg/GearSix.svg'
import MoneyWavy from '../assets/svg/MoneyWavy.svg'
import Info      from '../assets/svg/Info.svg'
import TrendUp   from '../assets/svg/TrendUp.svg'
import UserThree from '../assets/svg/UsersThree.svg'
import HouseLine from '../assets/svg/HouseLine.svg'
import profile from '../assets/svg/profile.svg'
import bell from '../assets/svg/Bell.svg'

const barHeights   = [14, 20, 12, 30, 18, 24, 14, 18, 26, 22, 36, 28, 70, 42, 32, 50, 26, 18, 22, 30, 16, 24, 18, 28]
const highlightIdx = 12

const integrations = [
  { idx: 1, name: 'Unsplash',  symbol: 'U',  color: '#1a1a1a', connected: true  },
  { idx: 2, name: 'Facebook',  symbol: 'f',  color: '#1877f2', connected: true  },
  { idx: 3, name: 'Instagram', symbol: '◎',  color: '#c13584', connected: true  },
  { idx: 4, name: 'Behance',   symbol: 'Bē', color: '#053eff', connected: false },
  { idx: 5, name: 'Twitter/X', symbol: '𝕏',  color: '#111111', connected: false },
  { idx: 6, name: 'Unsplash',  symbol: 'U',  color: '#1a1a1a', connected: true  },
  { idx: 7, name: 'Twitter/X', symbol: '𝕏',  color: '#111111', connected: false },
]

const todos = [
  { id: 1, label: 'Upload 3 new Car Photo...', sub: 'Completed', done: true,  tagClass: 'tag-done', tagLabel: 'Completed' },
  { id: 2, label: 'Today  10:00 PM — 11:45',  sub: '',          done: false, tagClass: 'tag-con',  tagLabel: 'Connected' },
]
</script>

<style scoped>
/* ─── Outer wrapper ─── */
.dashboard-wrap {
  position: relative;
  display: flex;
  width: 97%;
  justify-content: center;
  padding: 10px;
  border-radius: 14px;

  background: rgba(14, 11, 46, 0.85);
  backdrop-filter: blur(22px);
  -webkit-backdrop-filter: blur(22px);

  /* Inward white glow */
  box-shadow:
    inset 0 0 0 1px rgba(255,255,255,0.08),
    inset 0 0 60px rgba(255,255,255,0.06),
    inset 0 0 140px rgba(255,255,255,0.04);
}

/* ─── Shell ─── */
.dashboard {
  position: relative;
  background: rgba(14, 11, 46, 0.75);
  border-radius: 14px;
  border: 1px solid rgba(255,255,255,0.06);
  overflow: visible;
  font-size: 11px;
  font-family: var(--font-body, 'DM Sans', sans-serif);
  display: flex;
  height: 325px;

  backdrop-filter: blur(24px);
  -webkit-backdrop-filter: blur(24px);

  /* Deep inward glass glow */
  box-shadow:
    inset 0 0 0 1px rgba(255,255,255,0.08),
    inset 0 20px 60px rgba(255,255,255,0.05),
    inset 0 -20px 80px rgba(255,255,255,0.04);
}

/* ─────────────────────────────────────────
   Hover zones — invisible trigger strips
   at the vertical midpoint of each side
───────────────────────────────────────── */
.hover-zone {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 18px;          /* thin invisible strip */
  height: 50%;          /* covers the middle 50% vertically */
  z-index: 20;
}
.zone-left  { left: 0; }
.zone-right { right: 0; }

/* Floating card — hidden by default */
.float-card {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(18, 14, 50, 0.96);
  border: 1px solid rgba(139,92,246,0.28);
  border-radius: 12px;
  padding: 12px;
  width: 190px;
  backdrop-filter: blur(18px);
  box-shadow: 0 8px 32px rgba(0,0,0,0.5), 0 0 0 1px rgba(139,92,246,0.12);
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.2s ease, transform 0.2s ease;
  z-index: 30;
}

/* Profile card slides in from the LEFT — almost outside the box */
.zone-left .float-card {
  left: -160px;
  transform: translateY(-50%) translateX(-8px);
}
.zone-left:hover .float-card {
  opacity: 1;
  pointer-events: auto;
  transform: translateY(-50%) translateX(0);
}

/* Todo card slides in from the RIGHT — almost outside the box */
.zone-right .float-card {
  right: -160px;
  transform: translateY(-50%) translateX(8px);
}
.zone-right:hover .float-card {
  opacity: 1;
  pointer-events: auto;
  transform: translateY(-50%) translateX(0);
}

/* ─── Profile card contents ─── */
.prof-card { display: flex; align-items: center; gap: 10px; }
.prof-av {
  width: 32px; height: 32px; border-radius: 50%;
  background: linear-gradient(135deg, #6d28d9, #4f46e5);
  display: flex; align-items: center; justify-content: center;
  font-size: 13px; font-weight: 700; flex-shrink: 0; color: #fff;
}
.prof-sched { font-size: 7.5px; color: rgba(255,255,255,0.3); margin-bottom: 2px; }
.prof-name  { font-size: 10px; font-weight: 600; color: #fff; }
.prof-stats { display: flex; gap: 10px; font-size: 9px; color: rgba(255,255,255,0.3); margin-top: 3px; }

/* ─── Todo card contents ─── */
.panel-title {
  font-size: 11px; font-weight: 700; color: #fff;
  font-family: var(--font-display, 'Syne', sans-serif); margin-bottom: 0;
  padding: 2px;
}
.todo-hd   { display: flex; align-items: center; gap: 5px; margin-bottom: 10px; }
.todo-date { font-size: 8px; color: rgba(255,255,255,0.28); flex: 1; }
.todo-x    { background: none; border: none; color: rgba(255,255,255,0.3); font-size: 16px; cursor: pointer; line-height: 1; padding: 0; }
.todo-list { display: flex; flex-direction: column; gap: 8px; }
.todo-row  { display: flex; align-items: center; justify-content: space-between; gap: 6px; }
.todo-l    { display: flex; align-items: flex-start; gap: 6px; }
.todo-chk  { accent-color: #8b5cf6; margin-top: 1px; flex-shrink: 0; }
.todo-nm   { font-size: 9px; color: #fff; font-weight: 500; line-height: 1.3; }
.todo-nm.done { text-decoration: line-through; color: rgba(255,255,255,0.3); }
.todo-tm   { font-size: 7.5px; color: rgba(255,255,255,0.26); margin-top: 2px; }
.todo-tag  { font-size: 7.5px; border-radius: 4px; padding: 2px 7px; white-space: nowrap; flex-shrink: 0; }
.tag-done  { background: rgba(34,197,94,0.12);  color: #4ade80; }
.tag-con   { background: rgba(139,92,246,0.12); color: #a78bfa; }

/* ─── Sidebar ─── */
.d-sidebar {
  width: 46px; flex-shrink: 0;
  background: rgba(255,255,255,0.025);
  border-right: 1px solid rgba(255,255,255,0.06);
  display: flex; flex-direction: column;
  align-items: center;
  padding-top: 10px;
  gap: 2px;
}
.d-s-icon {
  width: 15px; height: 15px;
  opacity: 0.38; padding: 8px; border-radius: 8px;
  transition: opacity 0.15s, background 0.15s;
  cursor: pointer; box-sizing: content-box; display: block;
}
.d-s-icon:hover  { opacity: 0.75; background: rgba(139,92,246,0.12); }
.d-s-icon.active { opacity: 1; background: rgba(139,92,246,0.22); box-shadow: 0 0 0 1px rgba(139,92,246,0.35); }

/* ─── Content column ─── */
.d-content {
  flex: 1;
  display: flex;
  flex-direction: column;
  min-width: 0;

  background: rgba(255,255,255,0.03);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
}
/* ─── Topbar ─── */
.d-topbar {
  display: flex; align-items: center; justify-content: space-between;
  padding: 10px 14px;
  border-bottom: 1px solid rgba(255,255,255,0.06);
  flex-shrink: 0;
}
.d-topbar-l { display: flex; align-items: center; gap: 10px; }
.d-divider  { width: 2px; height: 36px; background: rgba(139,92,246,0.55); border-radius: 2px; flex-shrink: 0; }
.d-title    { font-size: 15px; font-weight: 700; color: #fff; font-family: var(--font-display, 'Syne', sans-serif); }
.d-sub      { font-size: 9px; color: rgba(255,255,255,0.36); margin-top: 1px; }
.d-topbar-r { display: flex; align-items: center; gap: 10px; }
.d-search {
  display: flex; align-items: center; gap: 6px;
  background: rgba(255,255,255,0.06); border: 1px solid rgba(255,255,255,0.08);
  border-radius: 8px; padding: 5px 12px; width: 140px;
}
.d-search-ico { color: rgba(255,255,255,0.32); font-size: 14px; }
.d-search-ph  { color: rgba(255,255,255,0.26); font-size: 10px; }
.d-ico-row  { display: flex; align-items: center; gap: 8px; }
.d-ico      { font-size: 14px; color: rgba(255,255,255,0.42); }
.d-ico-img {
  width: 15px;
  height: 15px;
  opacity: 0.42;
  filter: brightness(0) invert(1);
  cursor: pointer;
  transition: opacity 0.15s;
}
.d-ico-img:hover { opacity: 0.75; }

.d-avatar {
  width: 26px;
  height: 26px;
  border-radius: 50%;
  border: 1.5px solid rgba(139, 92, 246, 0.5);
  object-fit: cover;       /* ensures the SVG/image fills the circle cleanly */
  cursor: pointer;
  display: block;
}

/* ─── Subbar ─── */
.d-subbar {
  display: flex; align-items: center; justify-content: space-between;
  padding: 6px 14px; flex-shrink: 0;
}
.week-pill {
  display: inline-flex; align-items: center;
  background: rgba(139,92,246,0.14); border: 1px solid rgba(139,92,246,0.28);
  border-radius: 20px; padding: 3px 11px;
  font-size: 9.5px; color: #a78bfa; cursor: pointer;
}
.last-updated { font-size: 8px; color: rgba(255,255,255,0.22); }

/* ─── Main row ─── */
.d-main { display: flex; flex: 1; overflow: hidden; }

/* ─── Left panel ─── */
.d-left {
  flex: 1; padding: 10px 14px;
  border-right: 1px solid rgba(255,255,255,0.05);
  display: flex; flex-direction: column; gap: 10px;
  overflow-y: auto; min-width: 0;
   backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
}

.stats-grid { display: grid; grid-template-columns: repeat(3,1fr); gap: 8px; }
.s-card {
  background: rgba(255,255,255,0.06);
backdrop-filter: blur(12px);
-webkit-backdrop-filter: blur(12px);
  border: 1px solid rgba(255,255,255,0.07);
  border-radius: 10px; padding: 9px 10px;
}
.s-top  { display: flex; justify-content: space-between; align-items: center; margin-bottom: 5px; }
.s-lbl  { font-size: 8.5px; color: rgba(255,255,255,0.4); }
.s-badge { font-size: 8px; border-radius: 4px; padding: 1px 5px; font-weight: 600; }
.up { background: rgba(34,197,94,0.13); color: #4ade80; }
.dn { background: rgba(239,68,68,0.13); color: #f87171; }
.s-val-row { display: flex; align-items: baseline; gap: 4px; }
.s-val  { font-size: 18px; font-weight: 700; color: #fff; font-family: var(--font-display, 'Syne', sans-serif); line-height: 1; }
.s-unit { font-size: 8.5px; color: rgba(255,255,255,0.32); }
.s-ico-r { margin-left: auto; font-size: 12px; opacity: 0.3; }

/* ─── Chart ─── */
.chart-card {
  background: rgba(255,255,255,0.05);
backdrop-filter: blur(14px);
-webkit-backdrop-filter: blur(14px);
  border: 1px solid rgba(255,255,255,0.06);
  border-radius: 10px; padding: 10px;
}
.chart-hd-row { display: flex; justify-content: space-between; align-items: center; margin-bottom: 8px; }
.chart-hd   { font-size: 10px; font-weight: 600; color: #fff; font-family: var(--font-display, 'Syne', sans-serif); }
.chart-more { font-size: 14px; color: rgba(255,255,255,0.28); cursor: pointer; letter-spacing: 1px; }

.bars {
  display: flex; align-items: flex-end; gap: 2.5px;
  height: 62px; padding-bottom: 4px;
}
.bar-col { flex: 1; display: flex; flex-direction: column; align-items: center; justify-content: flex-end; position: relative; }
.bar     { width: 100%; background: rgba(139,92,246,0.18); border-radius: 2px 2px 0 0; position: relative; }
.bar-col.hi .bar { background: #8b5cf6; }

.bar-tt {
  position: absolute;
  bottom: 50%; transform: translateY(50%);
  left: calc(100% + 6px);
  background: #1e1b4b; border: 1px solid rgba(139,92,246,0.45);
  border-radius: 6px; padding: 4px 8px;
  display: flex; flex-direction: column; align-items: center;
  font-size: 8px; color: #fff; white-space: nowrap; z-index: 5; gap: 1px;
}
.tt-val  { font-weight: 700; font-size: 9px; color: #a78bfa; }
.tt-date { color: rgba(255,255,255,0.45); }

.x-axis {
  display: flex; justify-content: space-between;
  font-size: 7.5px; color: rgba(255,255,255,0.22);
  padding-top: 5px; border-top: 1px solid rgba(255,255,255,0.05);
}

/* ─── Right panel ─── */
.d-right { width: 210px; flex-shrink: 0; display: flex; flex-direction: column; overflow-y: auto; }
.integ-panel .integ-panel {
  padding: 10px 11px;
  flex: 1;
  background: rgba(255,255,255,0.04);
  backdrop-filter: blur(14px);
  -webkit-backdrop-filter: blur(14px);
}
.integ-list  { display: flex; flex-direction: column; gap: 7px; padding: 10px; }
.integ-row   { display: flex; align-items: center; gap: 7px; }
.i-ico {
  width: 22px; height: 22px; border-radius: 6px;
  display: flex; align-items: center; justify-content: center;
  font-size: 9px; font-weight: 700; flex-shrink: 0; color: #fff;
}
.i-info { flex: 1; min-width: 0; }
.i-name { font-size: 9.5px; font-weight: 600; color: #fff; }
.i-sub  { font-size: 7.5px; color: rgba(255,255,255,0.26); }
.i-btn  { font-size: 8px; border-radius: 5px; padding: 3px 8px; border: none; cursor: pointer; white-space: nowrap; font-weight: 500; }
.i-btn.on  { background: rgba(34,197,94,0.13); color: #4ade80; }
.i-btn.off { background: transparent; color: rgba(255,255,255,0.48); border: 1px solid rgba(255,255,255,0.14); }
</style>
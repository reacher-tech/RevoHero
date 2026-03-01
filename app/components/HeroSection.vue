<template>
  <section class="hero">
    <!-- Glow blobs -->
    <div class="glow glow-1" aria-hidden="true" />
    <div class="glow glow-2" aria-hidden="true" />

    <!-- Release badge -->
    <div class="badge">
      <span class="badge-dot" />
      <span>V2.0 release</span>
      <span class="badge-sep">|</span>
      <span>Integration with ChatGPT</span>
      <span class="badge-arr">→</span>
    </div>

    <!-- Headline -->
    <h1 class="headline">
      <span class="h1-plain">Revolutionize Your</span>
      <span class="h1-accent">
        Content Creation
        <span class="h1-widget" aria-hidden="true">
          <img :src="board" alt="icon" style="height: 50px; width: 50px;">
        </span>
        <span class="h1-plain">
        Process
        </span>
      </span>
    </h1>

    <!-- Dashboard -->
    <div class="dash-wrap">
      <TheDashboard />
    </div>
  </section>
</template>

<script setup>
import board from '../assets/svg/board.svg'
</script>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 100px;
  padding-bottom: 0;
  position: relative;
  overflow: hidden;
}

/* ── Glow blobs ── */
.glow {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);
  pointer-events: none;
  z-index: 0;
}
.glow-1 {
  width: 700px; height: 420px;
  background: radial-gradient(ellipse, rgba(109,40,217,0.5) 0%, transparent 68%);
  top: -60px; left: 50%; transform: translateX(-50%);
}
.glow-2 {
  width: 360px; height: 360px;
  background: radial-gradient(ellipse, rgba(76,29,149,0.35) 0%, transparent 70%);
  bottom: 100px; right: 8%;
}

/* ── Badge ── */
.badge {
  position: relative; z-index: 2;
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background: rgba(255,255,255,0.05);
  border: 1px solid rgba(255,255,255,0.11);
  border-radius: 20px;
  padding: 5px 14px;
  font-size: 12px;
  color: var(--text-sec);
  margin-bottom: 26px;
}
.badge-dot {
  width: 6px; height: 6px;
  border-radius: 50%;
  background: var(--purple-accent);
  box-shadow: 0 0 7px var(--purple-accent);
  flex-shrink: 0;
}
.badge-sep { color: rgba(255,255,255,0.2); }
.badge-arr { color: var(--purple-accent); }

/* ── Headline ── */
.headline {
  position: relative; z-index: 2;
  text-align: center;
  margin-bottom: 44px;
  line-height: 1.1;
}
.h1-plain {
  display: block;
  font-family: var(--font-display);
  font-weight: 700;
  font-size: clamp(34px, 5vw, 58px);
  color: #fff;
  margin-bottom: 2px;
}
.h1-accent {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  gap: 12px;
  font-family: var(--font-display);
  font-weight: 700;
  font-size: clamp(34px, 5vw, 58px);
  color: var(--purple-accent);
}

.h1-widget {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 50px; height: 40px;
  background: rgba(139,92,246,0.12);
  border: 1px solid rgba(139,92,246,0.3);
  border-radius: 8px;
  flex-shrink: 0;
}
.w-bars {
  display: flex;
  flex-direction: column;
  gap: 5px;
  padding: 3px;
}
.w-bar {
  display: block;
  height: 8px;
  border-radius: 3px;
  background: rgba(139,92,246,0.65);
}
.w-bars .w-bar:first-child { width: 30px; }
.w-bars .w-bar:last-child  { width: 18px; }

/* ── Dashboard wrapper ── */
.dash-wrap {
  position: relative; z-index: 2;
  width: 100%;
  max-width: 780px;
  padding: 0 20px;
  animation: riseUp 0.9s cubic-bezier(0.22, 1, 0.36, 1) 0.15s both;
}

@keyframes riseUp {
  from { opacity: 0; transform: translateY(28px); }
  to   { opacity: 1; transform: translateY(0); }
}
</style>
<template>
  <nav class="navbar">
    <div class="nav-inner">
      <div class="logo">LOOO</div>

      <ul class="nav-links">
        <li><a href="#">About</a></li>
        <li><a href="#">Features</a></li>
        <li><a href="#">Pricing</a></li>
        <li><a href="#">Blog</a></li>
        <li><a href="#">Contact</a></li>
      </ul>

      <button class="btn-cta">Get Started</button>
    </div>
  </nav>
</template>

<script setup>
// No logic needed
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0; left: 0; right: 0;
  z-index: 100;
  height: 58px;
  display: flex;
  align-items: center;
  padding: 0 48px;
  background: rgba(8, 6, 23, 0.75);
  backdrop-filter: blur(18px);
  -webkit-backdrop-filter: blur(18px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.06);
}

.nav-inner {
  max-width: 1160px;
  width: 100%;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.logo {
  font-family: var(--font-display);
  font-weight: 800;
  font-size: 22px;
  letter-spacing: 0.07em;
  color: #fff;
}

.nav-links {
  list-style: none;
  display: flex;
  gap: 30px;
}

.nav-links a {
  font-size: 13px;
  color: var(--text-sec);
  transition: color 0.2s;
}
.nav-links a:hover { color: #fff; }

.btn-cta {
  background: var(--purple-accent);
  color: #fff;
  border: none;
  border-radius: 8px;
  padding: 8px 20px;
  font-size: 13px;
  font-weight: 500;
  transition: background 0.2s, transform 0.15s;
}
.btn-cta:hover {
  background: #7c3aed;
  transform: translateY(-1px);
}
</style>
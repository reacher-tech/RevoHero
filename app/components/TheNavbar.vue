<template>
  <nav class="navbar">
    <div class="nav-inner">

      <!-- Logo -->
      <img :src="logo" alt="logo" class="logo"/>

      <!-- Centre links -->
      <ul class="nav-links">
        <li><a href="#">About</a></li>
        <li><a href="#">Features</a></li>
        <li><a href="#">Pricing</a></li>
        <li><a href="#">Blog</a></li>
        <li><a href="#">Contact</a></li>
      </ul>

      <!-- CTA -->
      <button class="btn-cta">Get Started</button>

    </div>
  </nav>
</template>

<script setup>
import logo from '../assets/svg/logo.svg'
</script>

<style scoped>
/* Shell */
.navbar {
  position: fixed;
  top: 16px;          /* ← float it down from the top edge */
  left: 50%;          /* ← start from centre */
  transform: translateX(-50%); /* ← pull back by half its own width */
  right: unset;       /* ← remove the edge-to-edge stretch */
  width: 70%; 
  border-radius: 12px; /* ← rounded since it's floating now */
  background: rgba(14, 12, 35, 0.85);
  border: 1px solid rgba(148, 146, 146, 0.1)
}

.nav-inner {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  position: relative;
  
}



.nav-links {
  list-style: none;
  display: flex;
  align-items: center;
  gap: 36px;
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  margin: 0; padding: 0;
}

.nav-links a {
  font-family: var(--font-body, 'DM Sans', sans-serif);
  font-size: 13.5px;
  font-weight: 400;
  color: rgba(255, 255, 255, 0.58);
  text-decoration: none;
  transition: color 0.2s ease;
  white-space: nowrap;
}
.nav-links a:hover { color: #fff; }

/* CTA */
.btn-cta {
  font-family: var(--font-body, 'DM Sans', sans-serif);
  font-size: 13px;
  font-weight: 500;
  color: #fff;
  background: transparent;
  border: 1px solid rgba(255, 255, 255, 0.32);
  border-radius: 8px;
  padding: 7px 18px;
  cursor: pointer;
  animation: ctaPulse 2.8s ease-in-out infinite;
  transition: background 0.2s ease, border-color 0.2s ease;
}
.btn-cta:hover {
  background: rgba(139, 92, 246, 0.14);
  border-color: rgba(139, 92, 246, 0.7);
  animation: none;
}

/* Pulse: border glow breathes purple */
@keyframes ctaPulse {
  0%, 100% {
    border-color: rgba(255, 255, 255, 0.32);
    box-shadow: 0 0 0 rgba(139, 92, 246, 0);
  }
  50% {
    border-color: rgba(139, 92, 246, 0.72);
    box-shadow: 0 0 10px rgba(139, 92, 246, 0.32), 0 0 22px rgba(139, 92, 246, 0.14);
  }
}
</style>

<template>
  <div class="carousel-section">
    <div class="carousel-track">
      <div v-for="set in 2" :key="set" class="logo-set">
        <div v-for="logo in logos" :key="logo.id + '-' + set" class="logo-it">
          <img :src="logo.image" :alt="'logo-' + logo.id" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>

import logo from '../assets/svg/logo.svg'
import logoo from '../assets/svg/logoo.svg'
import logooo from '../assets/svg/logooo.svg'
import logoooo from '../assets/svg/logoooo.svg'
import logooooo from '../assets/svg/logooooo.svg'
const logos = [
  { id: 1, image:logoo },
  { id: 2, image: logooo      },
  { id: 3, image: logo    },
  { id: 4, image: logooooo   },
  { id: 5, image: logoooo  },
]
</script>

<style scoped>
.carousel-section {
  border-top: 1px solid rgba(255,255,255,0.06);
  padding: 18px 0;
  overflow: hidden;
  background: var(--bg-deep);
  /* Fade edges */
  mask-image: linear-gradient(to right, transparent, black 12%, black 88%, transparent);
  -webkit-mask-image: linear-gradient(to right, transparent, black 12%, black 88%, transparent);
}

.carousel-track {
  display: flex;
  width: max-content;
  animation: logoSlide 22s linear infinite;
}

.logo-set {
  display: flex;
  align-items: center;
  gap: 52px;
  padding-right: 52px;
}

.logo-it {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  opacity: 0.4;
  transition: opacity 0.3s;
  cursor: default;
  user-select: none;
}
.logo-it:hover { opacity: 0.8; }

.logo-it span {
  font-family: var(--font-display);
  font-size: 15px;
  font-weight: 700;
  color: rgba(255,255,255,0.7);
  letter-spacing: 0.04em;
  white-space: nowrap;
}


.logo-it img {
  height: 22px;
  width: auto;
  filter: brightness(0) invert(1);
  opacity: 1;
}


@keyframes logoSlide {
  0%   { transform: translateX(0); }
  100% { transform: translateX(-50%); }
}
</style>
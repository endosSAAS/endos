<script setup>
import {
  ref,
  computed,
  onMounted,
  onUnmounted,
  defineAsyncComponent,
} from "vue";
import Home from "./components/Home.vue";

const Privacy = defineAsyncComponent(() => import("./components/Privacy.vue"));
const Terms = defineAsyncComponent(() => import("./components/Terms.vue"));

const path = ref(window.location.hash);
const menuOpen = ref(false);
const fEmail = ref(null);
const fPhone = ref(null);

const toggle = () => (menuOpen.value = !menuOpen.value);
const close = () => (menuOpen.value = false);

const onMove = (e) => {
  requestAnimationFrame(() => {
    const s = document.documentElement.style;
    s.setProperty("--mouse-x", `${e.clientX}px`);
    s.setProperty("--mouse-y", `${e.clientY}px`);
  });
};

const onView = computed(
  () =>
    ({
      "#privacy": Privacy,
      "#terms": Terms,
    }[path.value] || Home)
);

onMounted(() => {
  window.addEventListener("hashchange", () => {
    path.value = window.location.hash;
    window.scrollTo(0, 0);
    close();
  });

  window.addEventListener("mousemove", onMove, { passive: true });
  document.addEventListener("contextmenu", (e) => e.preventDefault());

  const [e, p] = [
    atob("ZG53c3A0MDdAZ21haWwuY29t"),
    atob("KzQ0NzgzMTMwOTczNw=="),
  ];

  if (fEmail.value) {
    fEmail.value.href = `mailto:${e}`;
    fEmail.value.innerText = e;
  }
  if (fPhone.value) {
    fPhone.value.href = `tel:${p}`;
    fPhone.value.innerText = p;
  }
});

onUnmounted(() => window.removeEventListener("mousemove", onMove));
</script>

<template>
  <div class="app-wrapper">
    <div class="bg-layer base-bg"></div>
    <div class="bg-layer mouse-spotlight"></div>
    <div class="bg-layer frost-overlay"></div>

    <div class="landing-page">
      <nav class="navbar container">
        <div class="logo">ENDOS</div>
        <div class="nav-links">
          <a href="#">Home</a>
          <a href="#services">Services</a>
          <a href="https://nano-sketch.github.io/porfv/" target="_blank"
            >Portfolio</a
          >
          <a
            href="https://maps.app.goo.gl/6teBYEfYSgPnAp9v7?g_st=ipc"
            target="_blank"
            >Contact</a
          >
        </div>
        <button class="hamburger" :class="{ active: menuOpen }" @click="toggle">
          <span></span><span></span><span></span>
        </button>
      </nav>

      <transition name="mobile-menu">
        <div v-show="menuOpen" class="mobile-menu">
          <a href="#" @click="close">Home</a>
          <a href="#services" @click="close">Services</a>
          <a
            href="https://nano-sketch.github.io/porfv/"
            target="_blank"
            @click="close"
            >Portfolio</a
          >
          <a
            href="https://maps.app.goo.gl/6teBYEfYSgPnAp9v7?g_st=ipc"
            target="_blank"
            @click="close"
            >Contact</a
          >
        </div>
      </transition>

      <component :is="onView" />

      <footer id="about" class="footer">
        <div class="container footer-content">
          <div class="footer-brand">ENDOS &copy; 2026</div>
          <div class="footer-links">
            <a href="#privacy">Privacy</a>
            <a href="#terms">Terms</a>
            <a ref="fEmail" class="secure-contact"></a>
            <a ref="fPhone" class="secure-contact"></a>
          </div>
        </div>
      </footer>
    </div>
  </div>
</template>

<style scoped>
.app-wrapper {
  position: relative;
  min-height: 100vh;
}
.bg-layer {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  pointer-events: none;
  z-index: -1;
}
.base-bg {
  background-color: var(--bg-color);
  z-index: -3;
}
.mouse-spotlight {
  z-index: -2;
  background: radial-gradient(
    600px circle at var(--mouse-x, 50%) var(--mouse-y, 50%),
    rgba(255, 255, 255, 0.07),
    transparent 40%
  );
}
.frost-overlay {
  z-index: -1;
  backdrop-filter: blur(60px);
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noiseFilter'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.65' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noiseFilter)' opacity='0.05'/%3E%3C/svg%3E");
  opacity: 0.6;
}
.landing-page {
  display: flex;
  flex-direction: column;
  gap: 3rem;
  padding-bottom: 4rem;
}
.navbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 60px;
  border-bottom: 1px solid var(--border-color);
  width: 100%;
}
.logo {
  font-size: 1.1rem;
  font-weight: 700;
  color: var(--text-primary);
  letter-spacing: -0.05em;
  text-transform: uppercase;
}
.nav-links {
  display: none;
  gap: 2rem;
}
.nav-links a {
  font-size: 0.8rem;
  color: var(--text-secondary);
  text-decoration: none;
  text-transform: uppercase;
  transition: all 0.1s;
}
.nav-links a:hover {
  text-decoration: underline;
  color: var(--text-primary);
  background-color: transparent;
}
.nav-actions {
  display: flex;
  gap: 0.5rem;
}
@media (min-width: 768px) {
  .nav-links {
    display: flex;
  }
  .hamburger {
    display: none;
  }
}
.footer {
  border-top: 1px dashed var(--border-color);
  padding-top: 1.5rem;
}
.footer-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.footer-brand {
  font-size: 0.75rem;
  color: var(--text-secondary);
}
.footer-links {
  display: flex;
  gap: 1rem;
}
.footer-links a {
  font-size: 0.75rem;
  color: var(--text-secondary);
  text-decoration: none;
  transition: color 0.15s;
}
.footer-links a:hover {
  text-decoration: underline;
  color: var(--text-primary);
}
.secure-contact {
  color: var(--text-secondary);
  text-decoration: none;
  user-select: none;
  cursor: pointer;
  font-size: 0.75rem;
  transition: color 0.15s;
}
.secure-contact:hover {
  color: var(--text-primary);
  text-decoration: underline;
}
@media (max-width: 768px) {
  .footer-content {
    flex-direction: column;
    gap: 1rem;
    text-align: center;
  }
  .footer-links {
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    gap: 1rem 1.5rem;
  }
}
.mobile-menu-enter-active,
.mobile-menu-leave-active {
  transition: all 0.3s ease;
  max-height: 300px;
  opacity: 1;
}
.mobile-menu-enter-from,
.mobile-menu-leave-to {
  max-height: 0;
  opacity: 0;
}
.mobile-menu {
  position: absolute;
  top: 60px;
  left: 0;
  width: 100%;
  background: var(--bg-color);
  border-bottom: 1px solid var(--border-color);
  display: flex;
  flex-direction: column;
  padding: 1rem 0;
  gap: 1rem;
  z-index: 50;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.5);
}
.mobile-menu a {
  padding: 0.5rem 2rem;
  font-size: 0.9rem;
  color: var(--text-secondary);
  text-decoration: none;
  text-transform: uppercase;
  transition: color 0.2s;
}
.mobile-menu a:hover {
  color: var(--text-primary);
  background: rgba(255, 255, 255, 0.05);
}
.hamburger {
  display: none;
  flex-direction: column;
  justify-content: space-between;
  width: 24px;
  height: 18px;
  cursor: pointer;
  z-index: 60;
  background: none;
  border: none;
  padding: 0;
  margin-left: auto;
}
@media (max-width: 767px) {
  .hamburger {
    display: flex;
  }
}
.hamburger span {
  display: block;
  width: 100%;
  height: 2px;
  background-color: var(--text-primary);
  transition: all 0.3s ease;
}
.hamburger.active span:nth-child(1) {
  transform: translateY(8px) rotate(45deg);
}
.hamburger.active span:nth-child(2) {
  opacity: 0;
}
.hamburger.active span:nth-child(3) {
  transform: translateY(-8px) rotate(-45deg);
}
</style>

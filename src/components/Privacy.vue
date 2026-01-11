<script setup>
import { onMounted, ref } from "vue";
const emailLink = ref(null);
const cipher = (s) => atob(s).split('').map(c => String.fromCharCode(c.charCodeAt(0) ^ 0x07)).join('');
const go = () => {
  window.location.href = 'mailto:' + cipher('Y2lwdHczNzBHYGpmbmspZGhq');
};
onMounted(() => {
  const e = cipher('Y2lwdHczNzBHYGpmbmspZGhq');
  if (emailLink.value) emailLink.value.innerText = e.split('').reverse().join('');
});
</script>

<template>
  <div class="legal-page container">
    <h1>Privacy Policy</h1>
    <p class="last-updated">Last updated: 2026-01-01</p>
    <div class="content">
      <section>
        <h2>1. Data Collection</h2>
        <p>
          We collect minimal data necessary for operation. System logs, IP
          addresses, and usage metrics are retained for detailed analysis and
          security auditing. We do not sell your data.
        </p>
      </section>
      <section>
        <h2>2. Cookies</h2>
        <p>
          We use local storage for essential session management. No third-party
          tracking cookies are employed.
        </p>
      </section>
      <section>
        <h2>4. Contact</h2>
        <p>
          For privacy concerns, contact
          <span ref="emailLink" class="secure-contact" @click="go"></span>
        </p>
      </section>
    </div>
  </div>
</template>

<style scoped>
.legal-page {
  padding-top: 4rem;
  padding-bottom: 4rem;
  max-width: 800px;
}
h1 {
  font-size: 2rem;
  font-weight: 700;
  text-transform: uppercase;
  margin-bottom: 0.5rem;
  color: var(--text-primary);
}
.last-updated {
  font-family: var(--font-mono);
  font-size: 0.8rem;
  color: var(--text-secondary);
  margin-bottom: 3rem;
  border-bottom: 1px dashed var(--border-color);
  padding-bottom: 1rem;
}
h2 {
  font-size: 1.2rem;
  margin-bottom: 1rem;
  color: var(--text-primary);
  font-family: var(--font-mono);
}
section {
  margin-bottom: 2.5rem;
}
p {
  color: var(--text-secondary);
  line-height: 1.7;
}
.secure-contact {
  color: var(--primary-color);
  text-decoration: none;
  user-select: none;
  cursor: pointer;
  unicode-bidi: bidi-override;
  direction: rtl;
}
.secure-contact:hover {
  text-decoration: underline;
}
</style>

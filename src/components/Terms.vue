<template>
  <div class="legal-page container">
    <h1>Terms of Service</h1>
    <p class="last-updated">Last updated: 2026-01-01</p>
    <div class="content">
      <section>
        <h2>1. Acceptance</h2>
        <p>
          By accessing this service, you agree to be bound by these terms. If
          you disagree with any part, you may not access the service.
        </p>
      </section>
      <section>
        <h2>2. License</h2>
        <p>
          We grant you a limited, non-exclusive, non-transferable license to use
          our services for lawful purposes only.
        </p>
      </section>
      <section>
        <h2>3. Restrictions</h2>
        <p>
          You may not reverse engineer, decompile, or attempt to extract source
          code. Unauthorized access or distribution is prohibited.
        </p>
      </section>
      <section>
        <h2>4. Termination</h2>
        <p>
          We reserve the right to terminate or suspend access immediately,
          without prior notice, for any breach of these terms.
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
</style>

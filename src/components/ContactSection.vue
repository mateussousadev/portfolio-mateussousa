<script setup>
// Links de contato.
// ⚠️ WhatsApp é placeholder — para trocar, altere apenas o número no link wa.me.
const whatsapp = 'https://wa.me/5586999457187'
const linkedin = 'https://www.linkedin.com/in/mateussousa-b9921b270'
const github = 'https://github.com/mateussousadev'
</script>

<template>
  <section id="contato" class="mx-auto max-w-5xl px-6 py-20 text-center">
    <!-- Cabeçalho -->
    <h2 class="text-3xl font-bold tracking-tight text-text">
      Vamos conversar?
    </h2>
    <p class="mx-auto mt-3 max-w-xl text-lg text-muted">
      Aberto a projetos freelance, vagas e colaborações.
    </p>

    <!-- Botões -->
    <div
      class="mt-8 flex flex-col items-stretch justify-center gap-3 sm:flex-row sm:items-center"
    >
      <!-- WhatsApp (verde, sólido) -->
      <a
        :href="whatsapp"
        target="_blank"
        rel="noopener noreferrer"
        class="inline-flex items-center justify-center gap-2 rounded-md bg-green px-5 py-2.5 text-sm font-semibold text-bg shadow-sm transition-opacity hover:opacity-90"
      >
        <span aria-hidden="true">💬</span>
        WhatsApp
      </a>

      <!-- LinkedIn (outline accent) -->
      <a
        :href="linkedin"
        target="_blank"
        rel="noopener noreferrer"
        class="inline-flex items-center justify-center rounded-md border border-accent px-5 py-2.5 text-sm font-semibold text-accent transition-colors hover:bg-accent/10"
      >
        LinkedIn
      </a>

      <!-- GitHub (outline muted) -->
      <a
        :href="github"
        target="_blank"
        rel="noopener noreferrer"
        class="inline-flex items-center justify-center rounded-md border border-border px-5 py-2.5 text-sm font-semibold text-muted transition-colors hover:border-muted hover:text-text"
      >
        GitHub
      </a>
    </div>
  </section>
</template>

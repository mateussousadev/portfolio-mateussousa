<script setup>
// FooterSection — rodapé simples e centralizado.
// Ano atual calculado em runtime (evita "2025" hardcoded).
const anoAtual = new Date().getFullYear()
</script>

<template>
  <footer class="border-t border-border">
    <div class="mx-auto max-w-5xl px-6 py-10 text-center text-sm text-muted">
      <p>© {{ anoAtual }} Mateus Sousa · Parnaíba, Piauí</p>
      <p class="mt-1">Feito com Vue 3 + Tailwind — deploy na AWS.</p>
    </div>
  </footer>
</template>

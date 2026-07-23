<script setup>
// Cards de números (destaques rápidos).
const stats = [
  { value: '2+', label: 'anos de experiência' },
  { value: '8+', label: 'projetos em produção' },
  { value: '4', label: 'estados atendidos' },
]
</script>

<template>
  <section id="sobre" class="mx-auto max-w-5xl px-6 py-20">
    <div class="grid grid-cols-1 gap-10 lg:grid-cols-3">
      <!-- Texto (2/3) -->
      <div class="lg:col-span-2">
        <h2 class="text-3xl font-bold tracking-tight text-text">Sobre</h2>

        <div class="mt-6 space-y-4 text-lg leading-relaxed text-muted">
          <p>
            Sou desenvolvedor full-stack e moro em Parnaíba, no Piauí. Desde
            2024 faço parte da Cajutec, onde ajudo a construir e manter os
            sistemas de gestão escolar que rodam em redes municipais espalhadas
            pelo Nordeste. 
          </p>
          <p>
            O que me move é resolver problema de verdade, do banco de dados ao
            deploy. Curto trabalhar em time: puxar uma discussão de arquitetura,
            dar aquela força pra quem tá começando, ajudar a montar o ambiente
            de alguém. E se aparece um processo manual e repetitivo no caminho,
            pode apostar que eu vou querer automatizar.
          </p>
        </div>
      </div>

      <!-- Cards de números (1/3) -->
      <div class="flex flex-col gap-4">
        <div
          v-for="stat in stats"
          :key="stat.label"
          class="rounded-md border border-border bg-surface px-6 py-5 shadow-sm"
        >
          <p class="font-mono text-3xl font-bold text-accent">
            {{ stat.value }}
          </p>
          <p class="mt-1 text-sm text-muted">{{ stat.label }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

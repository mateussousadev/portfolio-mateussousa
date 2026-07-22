<script setup>
// Cards de números (destaques rápidos).
const stats = [
  { value: '2+', label: 'anos de experiência' },
  { value: '4+', label: 'projetos em produção' },
  { value: '3', label: 'municípios atendidos' },
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
            Sou desenvolvedor full-stack baseado em Parnaíba, Piauí. Trabalho na
            Cajutec desde 2024, onde desenvolvo e mantenho sistemas de gestão
            escolar usados por redes municipais de ensino em todo o Nordeste.
          </p>
          <p>
            Gosto de resolver problemas reais — do banco de dados ao deploy,
            passando por decisões de arquitetura e onboarding de times. Quando
            não estou codando, estou ajudando a montar o ambiente de alguém ou
            pensando em como automatizar o próximo processo manual.
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

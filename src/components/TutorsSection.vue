<script setup>
import { ref } from 'vue'

// Pessoas que me formaram.
// foto: URL da imagem (ex: foto pública do LinkedIn). null = mostra a inicial.
const tutores = [
  {
    nome: 'Francisco Coelho',
    papel: 'Professor · Ensino Médio',
    mensagem:
      'Me deu as primeiras aulas de algoritmos e banco de dados. Plantou a semente de tudo que veio depois.',
    linkedin: 'https://www.linkedin.com/in/franciscocoelho-dev/',
    foto: null,
  },
  {
    nome: 'Dione Bastos',
    papel: 'Tech Lead · Escritha',
    mensagem:
      'Me orientou no estágio, me ensinou a trabalhar com profissionalismo e boas práticas desde cedo.',
    linkedin: 'https://www.linkedin.com/in/dione-bastos/',
    foto: null,
  },
  {
    nome: 'Bruno Oliveira',
    papel: 'Tech Lead · Primeiro emprego',
    mensagem:
      'Me ensinou o que é ser desenvolvedor de verdade — raciocínio, responsabilidade e autonomia.',
    linkedin: 'https://www.linkedin.com/in/bruno-oliveira/',
    foto: null,
  },
]

// Guarda os nomes cujas fotos falharam ao carregar (cai no fallback da inicial).
const fotosComErro = ref(new Set())
function marcarErro(nome) {
  fotosComErro.value = new Set(fotosComErro.value).add(nome)
}

// Primeira letra do nome (fallback do avatar).
function inicial(nome) {
  return nome.charAt(0).toUpperCase()
}
</script>

<template>
  <section id="tutors" class="mx-auto max-w-5xl px-6 py-20">
    <!-- Cabeçalho -->
    <h2 class="text-3xl font-bold tracking-tight text-text">Quem me formou</h2>
    <p class="mt-3 max-w-2xl text-lg text-muted">
      Três pessoas essenciais na minha trajetória como desenvolvedor.
    </p>

    <!-- Cards -->
    <div class="mt-10 grid grid-cols-1 gap-4 lg:grid-cols-3">
      <article
        v-for="tutor in tutores"
        :key="tutor.nome"
        class="flex flex-col items-center rounded-md border border-border bg-surface p-6 text-center shadow-sm"
      >
        <!-- Avatar: foto se existir/carregar, senão inicial -->
        <img
          v-if="tutor.foto && !fotosComErro.has(tutor.nome)"
          :src="tutor.foto"
          :alt="`Foto de ${tutor.nome}`"
          class="h-20 w-20 rounded-full border border-border object-cover"
          loading="lazy"
          @error="marcarErro(tutor.nome)"
        />
        <div
          v-else
          class="flex h-20 w-20 items-center justify-center rounded-full border border-border bg-bg text-2xl font-bold text-muted"
          :aria-label="`Avatar de ${tutor.nome}`"
        >
          {{ inicial(tutor.nome) }}
        </div>

        <!-- Nome e papel -->
        <h3 class="mt-4 font-bold text-text">{{ tutor.nome }}</h3>
        <p class="mt-1 text-sm text-muted">{{ tutor.papel }}</p>

        <!-- Mensagem de agradecimento -->
        <p class="mt-4 text-sm italic leading-relaxed text-muted">
          “{{ tutor.mensagem }}”
        </p>

        <!-- Link LinkedIn -->
        <a
          :href="tutor.linkedin"
          target="_blank"
          rel="noopener noreferrer"
          class="mt-5 inline-flex items-center gap-2 text-sm font-semibold text-accent transition-colors hover:text-accent-hover"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-5 w-5"
            viewBox="0 0 24 24"
            fill="currentColor"
            aria-hidden="true"
          >
            <path
              d="M20.45 20.45h-3.56v-5.57c0-1.33-.02-3.04-1.85-3.04-1.85 0-2.14 1.45-2.14 2.94v5.67H9.35V9h3.41v1.56h.05c.48-.9 1.63-1.85 3.36-1.85 3.6 0 4.27 2.37 4.27 5.45v6.29zM5.34 7.43a2.07 2.07 0 110-4.14 2.07 2.07 0 010 4.14zM7.12 20.45H3.56V9h3.56v11.45zM22.22 0H1.77C.79 0 0 .77 0 1.72v20.56C0 23.23.79 24 1.77 24h20.45c.98 0 1.78-.77 1.78-1.72V1.72C24 .77 23.2 0 22.22 0z"
            />
          </svg>
          LinkedIn
        </a>
      </article>
    </div>
  </section>
</template>

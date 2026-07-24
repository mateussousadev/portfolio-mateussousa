<script setup>
// Pessoas que me formaram.
// icone: SVG path (Heroicons outline) que representa o papel de cada um.
const tutores = [
  {
    nome: "Francisco Coelho",
    papel: "Professor · Ensino Médio",
    mensagem:
      "Me deu as primeiras aulas de algoritmos e banco de dados. O início do meu amor à programação.",
    linkedin: "https://www.linkedin.com/in/franciscocoelho-dev/",
    // Capelo de formatura — o professor.
    icone:
      "M4.26 10.147a60.438 60.438 0 0 0-.491 6.347A48.62 48.62 0 0 1 12 20.904a48.62 48.62 0 0 1 8.232-4.41 60.46 60.46 0 0 0-.491-6.347m-15.482 0a50.636 50.636 0 0 0-2.658-.813A59.906 59.906 0 0 1 12 3.493a59.903 59.903 0 0 1 10.399 5.84c-.896.248-1.783.52-2.658.814m-15.482 0A50.717 50.717 0 0 1 12 13.489a50.702 50.702 0 0 1 7.74-3.342M6.75 15a.75.75 0 1 0 0-1.5.75.75 0 0 0 0 1.5Zm0 0v-3.675A55.378 55.378 0 0 1 12 8.443m-7.007 11.55A5.981 5.981 0 0 0 6.75 15.75v-1.5",
  },
  {
    nome: "Dione Bastos",
    papel: "Tech Lead · Primeiro estágio",
    mensagem:
      "Me orientou durante todo o estágio, me ensinando a trabalhar com profissionalismo e boas práticas desde cedo.",
    linkedin: "https://www.linkedin.com/in/dione-bastos/",
    // Chaves de código — o mentor de boas práticas.
    icone:
      "M17.25 6.75 22.5 12l-5.25 5.25m-10.5 0L1.5 12l5.25-5.25m7.5-3-4.5 16.5",
  },
  {
    nome: "Bruno Oliveira",
    papel: "Tech Lead · Primeiro emprego",
    mensagem:
      "Ele me ensinou o que é ser fullstack — me instigou a ter raciocínio, responsabilidade e autonomia, e sempre me deu conselhos e dicas que sigo até hoje.",
    linkedin: "https://www.linkedin.com/in/bruno-oliveira/",
    // Foguete — o empurrão pra decolar na carreira.
    icone:
      "M15.59 14.37a6 6 0 0 1-5.84 7.38v-4.8m5.84-2.58a14.98 14.98 0 0 0 6.16-12.12A14.98 14.98 0 0 0 9.631 8.41m5.96 5.96a14.926 14.926 0 0 1-5.841 2.58m-.119-8.54a6 6 0 0 0-7.381 5.84h4.8m2.581-5.84a14.927 14.927 0 0 0-2.58 5.84m2.699 2.7c-.103.021-.207.041-.311.06a15.09 15.09 0 0 1-2.448-2.448 14.9 14.9 0 0 1 .06-.312m-2.24 2.39a4.493 4.493 0 0 0-1.757 4.306 4.493 4.493 0 0 0 4.306-1.758M16.5 9a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0Z",
  },
];
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
        <!-- Avatar: ícone que representa o papel do mentor -->
        <div
          class="flex h-20 w-20 items-center justify-center rounded-full border border-border bg-bg text-accent"
          :aria-label="`Ícone de ${tutor.nome}`"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-9 w-9"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            stroke-width="1.5"
            aria-hidden="true"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              :d="tutor.icone"
            />
          </svg>
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

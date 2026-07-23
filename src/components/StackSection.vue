<script setup>
// Stack por categoria.
// - icon: slug do Devicon (https://devicon.dev). null = renderiza pill de texto.
const categorias = [
  {
    nome: 'Backend',
    itens: [
      { nome: 'PHP 8.4', icon: 'php' },
      { nome: 'Laravel', icon: 'laravel' },
      { nome: 'NestJS', icon: 'nestjs' },
      { nome: 'Python', icon: 'python' },
      { nome: 'FastAPI', icon: null },
    ],
  },
  {
    nome: 'Frontend',
    itens: [
      { nome: 'Vue.js', icon: 'vuejs' },
      { nome: 'Vuetify', icon: 'vuetify' },
      { nome: 'Inertia.js', icon: null },
      { nome: 'JavaScript', icon: 'javascript' },
      { nome: 'Tailwind CSS', icon: 'tailwindcss' },
    ],
  },
  {
    nome: 'Banco & Cache',
    itens: [
      { nome: 'MariaDB', icon: 'mariadb' },
      { nome: 'MySQL', icon: 'mysql' },
      { nome: 'Redis', icon: 'redis' },
    ],
  },
  {
    nome: 'Infra & DevOps',
    itens: [
      { nome: 'Nginx', icon: 'nginx' },
      { nome: 'AWS EC2', icon: 'amazonwebservices' },
      { nome: 'GitHub Actions', icon: 'githubactions' },
      { nome: 'Cloudflare', icon: 'cloudflare' },
      { nome: 'Docker', icon: 'docker' },
    ],
  },
  {
    nome: 'Ferramentas',
    itens: [
      { nome: 'Git', icon: 'git' },
      { nome: 'Playwright', icon: null },
      { nome: 'Telegram Bot API', icon: null },
      { nome: 'Filament', icon: null },
    ],
  },
]

// Monta a URL do SVG do Devicon a partir do slug.
function iconUrl(icon) {
  return `https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/${icon}/${icon}-original.svg`
}
</script>

<template>
  <section id="stack" class="mx-auto max-w-5xl px-6 py-20">
    <!-- Cabeçalho -->
    <h2 class="text-3xl font-bold tracking-tight text-text">Stack</h2>
    <p class="mt-3 max-w-2xl text-lg text-muted">
      Tecnologias que uso no dia a dia em produção.
    </p>

    <!-- Categorias -->
    <div class="mt-10 space-y-10">
      <div v-for="categoria in categorias" :key="categoria.nome">
        <h3 class="mb-4 font-mono text-sm font-medium text-muted">
          {{ categoria.nome }}
        </h3>

        <ul
          class="grid grid-cols-2 gap-3 sm:grid-cols-3 lg:grid-cols-5"
        >
          <li
            v-for="item in categoria.itens"
            :key="item.nome"
            class="flex flex-col items-center justify-center gap-2 rounded-md border border-border bg-surface p-4 text-center transition-colors hover:border-accent"
          >
            <!-- Item com ícone Devicon -->
            <template v-if="item.icon">
              <img
                :src="iconUrl(item.icon)"
                :alt="item.nome"
                class="h-10 w-10"
                loading="lazy"
              />
              <span class="text-xs text-muted">{{ item.nome }}</span>
            </template>

            <!-- Item sem Devicon: pill de texto verde -->
            <template v-else>
              <span
                class="rounded bg-dark-surface px-2.5 py-1 font-mono text-xs text-green"
              >
                {{ item.nome }}
              </span>
            </template>
          </li>
        </ul>
      </div>
    </div>
  </section>
</template>

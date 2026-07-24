<script setup>
// Paths oficiais (Simple Icons) para logos que o Devicon não tem — embutidos
// inline para não depender de outro CDN além do Devicon.
const SVG_TELEGRAM =
  'M11.944 0A12 12 0 0 0 0 12a12 12 0 0 0 12 12 12 12 0 0 0 12-12A12 12 0 0 0 12 0a12 12 0 0 0-.056 0zm4.962 7.224c.1-.002.321.023.465.14a.506.506 0 0 1 .171.325c.016.093.036.306.02.472-.18 1.898-.962 6.502-1.36 8.627-.168.9-.499 1.201-.82 1.23-.696.065-1.225-.46-1.9-.902-1.056-.693-1.653-1.124-2.678-1.8-1.185-.78-.417-1.21.258-1.91.177-.184 3.247-2.977 3.307-3.23.007-.032.014-.15-.056-.212s-.174-.041-.249-.024c-.106.024-1.793 1.14-5.061 3.345-.48.33-.913.49-1.302.48-.428-.008-1.252-.241-1.865-.44-.752-.245-1.349-.374-1.297-.789.027-.216.325-.437.893-.663 3.498-1.524 5.83-2.529 6.998-3.014 3.332-1.386 4.025-1.627 4.476-1.635z'
const SVG_FILAMENT =
  'M2.074 9.603c-.404 0-.866.122-1.128.596-.086.15-.151.336-.197.558l-.084.41H.149l-.149.71h.515c-.17.812-.337 1.623-.506 2.435h.925c.172-.811.34-1.624.508-2.436h.849l.149-.71h-.888l.058-.295a.664.664 0 0 1 .18-.364c.1-.086.229-.13.36-.122.173.003.344.044.5.12l.224-.757a2.173 2.173 0 0 0-.8-.145Zm3.865.007-.944.082c-.319 1.54-.64 3.08-.962 4.62h.928c.021-.104.491-2.381.978-4.702Zm-2.046.022c-.288-.01-.605.136-.654.473-.13.663.559.652.874.481.115-.064.19-.188.227-.37.054-.21-.027-.584-.447-.584Zm19.43.347-.95.167-.213 1.02h-.5l-.15.71h.503c-.091.448-.185.895-.279 1.342-.056.267-.05.488.02.662.13.348.483.517.961.517.127-.003.473-.031.664-.151l.1-.772a.818.818 0 0 1-.46.154c-.42 0-.37-.409-.326-.617l.235-1.135h.923l.149-.71h-.925s.074-.348.248-1.187zM7.542 11.08c-.562.001-1.147.192-1.204.211l-.146.825c.2-.087.66-.264 1.077-.264a.93.93 0 0 1 .357.058.336.336 0 0 1 .217.411c-.902.148-1.15.172-1.342.238-.38.116-.665.375-.728.762-.084.389.03.726.292.918a.809.809 0 0 0 .493.147c.402.008.714-.216.9-.495h.072l-.04.42h.8c.143-.661.28-1.324.416-1.987.056-.256.047-.476-.028-.662-.197-.485-.735-.582-1.136-.582Zm3.958 0c-.142 0-.28.025-.41.076-.258.1-.482.273-.644.498h-.08l.067-.536-.783.047c-.215 1.049-.436 2.097-.655 3.145h.929l.133-.65c.095-.438.183-.878.273-1.317.301-.357.501-.406.646-.406.335 0 .34.33.278.627-.077.365-.15.731-.225 1.097-.044.217-.088.434-.134.65h.925c.77-3.66-.303 1.396.417-1.998.053-.064.117-.116.175-.174.108-.099.266-.203.447-.203.328 0 .343.317.279.628l-.36 1.746h.928c.135-.673.278-1.345.419-2.017.08-.368.054-.661-.074-.882-.128-.22-.35-.331-.668-.331-.142 0-.28.026-.412.077a1.492 1.492 0 0 0-.658.51h-.068a.708.708 0 0 0-.204-.404c-.13-.122-.31-.183-.541-.183Zm4.752 0c-.29 0-.547.063-.773.188-.633.352-.825 1.049-.878 1.324-.087.437-.114 1.182.57 1.581.25.146.56.22.932.22.428 0 .825-.103.978-.196l.124-.8c-.089.05-.186.091-.292.124-.464.144-1.192.182-1.404-.304a.706.706 0 0 1-.053-.313l.001-.012h1.9c.048-.12.073-.249.109-.373.07-.287.07-.54-.003-.756a.9.9 0 0 0-.416-.503c-.205-.12-.47-.18-.795-.18zm3.956 0c-.147 0-.288.025-.424.076a1.41 1.41 0 0 0-.654.498h-.076l.064-.536-.782.047c-.088.426-.292 1.421-.655 3.145h.928c.136-.656.273-1.311.407-1.967a2.03 2.03 0 0 1 .203-.208.95.95 0 0 1 .218-.144c.168-.08.476-.097.556.117.044.115.045.267.004.456l-.36 1.746h.928l.138-.654c.093-.455.188-.909.284-1.363.124-.59.004-1.213-.779-1.213zm-16.63.08-.453.016-.058.212a.08.08 0 0 0 .03.074l.314.219-.366.024c-.03.002-.053.026-.06.058l-.03.137a.08.08 0 0 0 .03.074l.314.218-.366.024c-.03.002-.053.026-.06.058l-.029.135a.08.08 0 0 0 .03.075l.314.218-.367.025c-.028.002-.053.025-.06.057-.011.046-.02.092-.029.138a.08.08 0 0 0 .03.073l.314.218-.366.025c-.03.002-.053.025-.06.058l-.03.137a.08.08 0 0 0 .032.073l.313.22-.367.023c-.028.002-.053.025-.06.057l-.127.504h.41l.065-.274.513-.045c.03-.002.054-.025.06-.058l.03-.136a.08.08 0 0 0-.031-.074l-.314-.219.367-.024c.029-.002.053-.026.06-.058.011-.045.019-.091.028-.136a.08.08 0 0 0-.03-.074l-.313-.219.366-.025c.03 0 .054-.025.06-.057l.03-.137a.08.08 0 0 0-.03-.074l-.315-.218.367-.025c.029-.002.053-.025.06-.057l.028-.128v-.009a.08.08 0 0 0-.03-.074l-.313-.218.367-.024c.029-.002.053-.025.06-.057l.028-.128v-.01a.08.08 0 0 0-.03-.073l-.415-.292Zm12.693.585c.168 0 .286.07.357.208a.67.67 0 0 1 .057.398l-1.122.024.01-.028c.122-.368.392-.6.698-.602zM7.728 12.75l-.105.504c-.173.256-.409.405-.633.408-.099.004-.359-.054-.305-.368a.374.374 0 0 1 .252-.286c.234-.089.519-.113.685-.196a.691.691 0 0 0 .106-.062Z'

// Stack por categoria.
// - icon: slug do Devicon. variant: variação do arquivo (padrão "original").
// - svg: path inline (para logos que o Devicon não tem). color: cor do path.
// - sem icon/svg: renderiza pill de texto.
const categorias = [
  {
    nome: 'Backend',
    itens: [
      { nome: 'PHP 8.4', icon: 'php' },
      { nome: 'Laravel', icon: 'laravel' },
      { nome: 'NestJS', icon: 'nestjs' },
      { nome: 'Python', icon: 'python' },
      { nome: 'FastAPI', icon: 'fastapi' },
    ],
  },
  {
    nome: 'Frontend',
    itens: [
      { nome: 'Vue.js', icon: 'vuejs' },
      { nome: 'Vuetify', icon: 'vuetify' },
      { nome: 'Inertia.js', icon: 'inertiajs' },
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
      // amazonwebservices só tem variantes com wordmark no Devicon.
      { nome: 'AWS EC2', icon: 'amazonwebservices', variant: 'plain-wordmark' },
      { nome: 'GitHub Actions', icon: 'githubactions' },
      { nome: 'Cloudflare', icon: 'cloudflare' },
      { nome: 'Docker', icon: 'docker' },
    ],
  },
  {
    nome: 'Ferramentas',
    itens: [
      { nome: 'Git', icon: 'git' },
      { nome: 'Playwright', icon: 'playwright' },
      { nome: 'Telegram Bot API', svg: SVG_TELEGRAM, color: '#26A5E4' },
      { nome: 'Filament', svg: SVG_FILAMENT, color: '#FFAF00' },
    ],
  },
]

// Monta a URL do SVG do Devicon a partir do slug + variante.
function iconUrl(icon, variant = 'original') {
  return `https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/${icon}/${icon}-${variant}.svg`
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

        <ul class="grid grid-cols-2 gap-3 sm:grid-cols-3 lg:grid-cols-5">
          <li
            v-for="item in categoria.itens"
            :key="item.nome"
            class="flex flex-col items-center justify-center gap-2 rounded-md border border-border bg-surface p-4 text-center transition-colors hover:border-accent"
          >
            <!-- Ícone Devicon (imagem) -->
            <template v-if="item.icon">
              <img
                :src="iconUrl(item.icon, item.variant)"
                :alt="item.nome"
                class="h-10 w-10 object-contain"
                loading="lazy"
              />
              <span class="text-xs text-muted">{{ item.nome }}</span>
            </template>

            <!-- Ícone SVG inline (logos fora do Devicon) -->
            <template v-else-if="item.svg">
              <svg
                class="h-10 w-10"
                viewBox="0 0 24 24"
                xmlns="http://www.w3.org/2000/svg"
                :style="{ color: item.color }"
                aria-hidden="true"
              >
                <path :d="item.svg" fill="currentColor" />
              </svg>
              <span class="text-xs text-muted">{{ item.nome }}</span>
            </template>

            <!-- Sem ícone: pill de texto verde -->
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

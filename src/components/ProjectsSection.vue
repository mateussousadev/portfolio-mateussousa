<script setup>
// Lista de projetos. Cada item vira um card.
// - destaque: caixa interna opcional (borda-l accent)
// - link: botão externo opcional
const projetos = [
  {
    badge: 'Cajutec · 2024–presente',
    titulo: 'e-PUBLIC — Gestão Escolar Municipal',
    descricao:
      'Plataforma de gestão escolar para redes municipais públicas. Desenvolvo e mantenho as funcionalidades que movem o dia a dia da escola — matrículas, notas, frequências, planejamentos e aulas — em municípios do Nordeste.',
    destaque:
      'Módulo de Pendências de Professor — dashboard que consolida informações de todos os módulos do sistema, permitindo que gestores acompanhem, em um único painel, os lançamentos pendentes de cada professor da rede',
    tags: ['PHP 8.4', 'Laravel', 'Vue 2', 'Vuetify', 'MariaDB', 'Redis', 'Nginx', 'Multi-tenant'],
    link: null,
  },
  {
    badge: 'Cajutec · 2024–presente',
    titulo: 'e-institucional — Gestão Escolar Privada',
    descricao:
      'A mesma base de gestão acadêmica, adaptada para escolas privadas. Mesmo núcleo do e-PUBLIC, ajustado às necessidades das instituições particulares.',
    destaque:
      'Fiz a integração do portal do aluno com a API do Sicoob para disponibilizar os boletos direto pra quem estuda — precisei aprender a integração do zero pra entregar.',
    tags: ['PHP 8.4', 'Laravel', 'Vue 2', 'Vuetify', 'MariaDB', 'Redis', 'Nginx', 'API Sicoob'],
    link: null,
  },
  {
    badge: 'Cajutec · interno',
    titulo: 'Cajuawards',
    descricao:
      'Sistema interno de premiações: cadastro de candidatos, votação pública por usuários cadastrados e uma tela de apresentação com slides e efeitos visuais pro evento ao vivo.',
    destaque: null,
    tags: ['Laravel', 'Filament', 'Vue.js'],
    link: null,
  },
  {
    badge: 'Cajutec · interno',
    titulo: 'Automações Internas',
    descricao:
      'Dois utilitários que economizam tempo do time: (1) um bot no Telegram que avisa automaticamente quando muda o status de protocolos no sistema de tickets; (2) um conversor de protocolos para Markdown via regex, pronto pra jogar direto nas IAs de programação.',
    destaque: null,
    tags: ['Laravel', 'Telegram Bot API', 'Python', 'Regex'],
    link: null,
  },
  {
    badge: 'Freelance · nov 2025 – abr 2026',
    titulo: 'Plataforma de Consulta de Dados Públicos',
    descricao:
      'SaaS multi-tenant que centraliza a consulta de dados públicos federais dos municípios — instrumentos do TransfereGov, propostas e pagamentos do FNS (Saúde) e transferências especiais — sempre atualizados direto das fontes oficiais.',
    destaque:
      'Fui eu quem construiu do zero as integrações com os portais do governo (CAUC/SICONFI, TransfeGov, FNS), usando scraping com anti-detecção avançada. Trocou um processo manual que levaria centenas de dias por consultas automáticas.',
    tags: ['Laravel 12', 'Vue 3', 'Inertia.js', 'Python', 'FastAPI', 'Playwright', 'Multi-tenant', 'Web Scraping'],
    link: null,
  },
  {
    badge: 'JM2 · 2024',
    titulo: 'Piauí Oportunidades',
    descricao:
      'Plataforma do Governo do Estado do Piauí que conecta jovens a vagas de emprego, estágios e cursos. Atuei como tech lead de um time de 3 pessoas, desenvolvendo do zero o backend em NestJS e o frontend em Vue.js, além de configurar a infraestrutura em servidor privado.',
    destaque: null,
    tags: ['NestJS', 'Vue.js', 'MySQL', 'Tech Lead', 'Governo'],
    link: {
      label: 'Acessar plataforma',
      url: 'https://piauioportunidades.pi.gov.br/',
    },
  },
  {
    badge: 'Escritha · 2023–2024',
    titulo: 'Sistema de Artigos Científicos (ABNT)',
    descricao:
      'Plataforma para estudantes e professores produzirem artigos científicos com formatação ABNT automática. O sistema compilava o trabalho completo e integrava API de IA para sugerir conteúdo, consumindo tokens do plano do usuário.',
    destaque: null,
    tags: ['Laravel', 'Angular', 'IA', 'Docker', 'Laradock'],
    link: null,
  },
]
</script>

<template>
  <section id="projetos" class="mx-auto max-w-5xl px-6 py-20">
    <!-- Cabeçalho -->
    <h2 class="text-3xl font-bold tracking-tight text-text">Projetos</h2>
    <p class="mt-3 max-w-2xl text-lg text-muted">
      Sistemas que estão em produção — alguns abertos, outros sob sigilo por
      serem de clientes.
    </p>

    <!-- Grade de cards -->
    <div class="mt-10 grid grid-cols-1 gap-4 lg:grid-cols-2">
      <article
        v-for="projeto in projetos"
        :key="projeto.titulo"
        class="flex flex-col overflow-hidden rounded-md border border-border bg-surface shadow-sm transition-colors hover:border-accent/60"
      >
        <!-- Área de imagem (placeholder) com badge sobreposto -->
        <div class="relative flex h-48 items-center justify-center bg-dark-surface">
          <span class="px-6 text-center font-mono text-sm text-muted">
            {{ projeto.titulo }}
          </span>
          <!-- Badge empresa/período (pill top-left) -->
          <span
            class="absolute left-3 top-3 rounded-full border border-border bg-bg/80 px-3 py-1 text-xs font-medium text-muted backdrop-blur"
          >
            {{ projeto.badge }}
          </span>
        </div>

        <!-- Conteúdo -->
        <div class="flex flex-1 flex-col p-6">
          <h3 class="text-lg font-bold text-text">{{ projeto.titulo }}</h3>

          <p class="mt-2 text-sm leading-relaxed text-muted">
            {{ projeto.descricao }}
          </p>

          <!-- Destaque interno (opcional) -->
          <div
            v-if="projeto.destaque"
            class="mt-4 border-l-2 border-accent bg-dark-surface px-4 py-3 text-xs leading-relaxed text-muted"
          >
            {{ projeto.destaque }}
          </div>

          <!-- Pills de tecnologia -->
          <ul class="mt-4 flex flex-wrap gap-2">
            <li
              v-for="tag in projeto.tags"
              :key="tag"
              class="rounded-full border border-border bg-bg px-2.5 py-1 font-mono text-xs text-muted"
            >
              {{ tag }}
            </li>
          </ul>

          <!-- Botão externo (opcional) — empurrado pro rodapé do card -->
          <div v-if="projeto.link" class="mt-auto pt-5">
            <a
              :href="projeto.link.url"
              target="_blank"
              rel="noopener noreferrer"
              class="inline-flex items-center gap-1 text-sm font-semibold text-accent transition-colors hover:text-accent-hover"
            >
              {{ projeto.link.label }}
              <span aria-hidden="true">→</span>
            </a>
          </div>
        </div>
      </article>
    </div>
  </section>
</template>

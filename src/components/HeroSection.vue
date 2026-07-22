<script setup>
import { ref } from 'vue'

// Detecta a foto em src/assets/img/ em tempo de build sem quebrar caso não exista.
// Quando o arquivo foto.{jpg,jpeg,png,webp} for adicionado, o glob o resolve
// automaticamente e o layout passa a exibi-lo — sem alterar código.
const fotos = import.meta.glob('../assets/img/foto.{jpg,jpeg,png,webp}', {
  eager: true,
  import: 'default',
})
const fotoUrl = Object.values(fotos)[0] || null

// Fallback extra: se a img existir mas falhar ao carregar, cai no placeholder.
const imgErro = ref(false)

// Scroll suave até a seção de projetos.
function irParaProjetos() {
  document.querySelector('#projetos')?.scrollIntoView({ behavior: 'smooth' })
}
</script>

<template>
  <!-- Grade sutil de pontos só no hero (dot grid via CSS inline) -->
  <section
    class="hero-dot-grid border-b border-border"
    style="
      background-image: radial-gradient(circle, #30363d 1px, transparent 1px);
      background-size: 24px 24px;
    "
  >
    <div
      class="mx-auto flex max-w-5xl flex-col items-center gap-10 px-6 py-20 lg:flex-row lg:items-center lg:justify-between lg:py-28"
    >
      <!-- Foto: no mobile aparece acima (order-first); no desktop vai à direita -->
      <div class="order-first lg:order-last">
        <!-- Foto real, se existir e carregar -->
        <img
          v-if="fotoUrl && !imgErro"
          :src="fotoUrl"
          alt="Foto de Mateus Sousa"
          class="h-40 w-40 rounded-full border border-border object-cover shadow-md"
          @error="imgErro = true"
        />
        <!-- Placeholder circular com ícone de pessoa -->
        <div
          v-else
          class="flex h-40 w-40 items-center justify-center rounded-full border border-border bg-dark-surface shadow-md"
          aria-label="Foto de Mateus Sousa (placeholder)"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-20 w-20 text-muted"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            stroke-width="1.5"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M15.75 6a3.75 3.75 0 11-7.5 0 3.75 3.75 0 017.5 0zM4.5 20.25a7.5 7.5 0 0115 0"
            />
          </svg>
        </div>
      </div>

      <!-- Texto -->
      <div class="max-w-2xl text-center lg:text-left">
        <!-- Eyebrow -->
        <p class="font-mono text-sm font-medium text-accent">
          Desenvolvedor Full-Stack
        </p>

        <!-- Heading -->
        <h1
          class="mt-4 text-4xl font-extrabold leading-tight tracking-tight text-text sm:text-5xl"
        >
          Transformo requisitos em sistemas reais.
        </h1>

        <!-- Subtítulo -->
        <p class="mt-6 text-lg text-muted">
          PHP · Laravel · Vue.js · Python — construindo produtos para o setor
          público e privado desde 2023.
        </p>

        <!-- Botões -->
        <div
          class="mt-8 flex flex-col items-stretch gap-3 sm:flex-row sm:items-center sm:justify-center lg:justify-start"
        >
          <!-- Primário -->
          <button
            type="button"
            class="rounded-md bg-accent px-5 py-2.5 text-sm font-semibold text-white shadow-sm transition-colors hover:bg-accent-hover"
            @click="irParaProjetos"
          >
            Ver projetos
          </button>
          <!-- Outline -->
          <a
            href="https://github.com/mateussousadev"
            target="_blank"
            rel="noopener noreferrer"
            class="inline-flex items-center justify-center gap-2 rounded-md border border-accent px-5 py-2.5 text-sm font-semibold text-accent transition-colors hover:bg-accent/10"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="h-5 w-5"
              viewBox="0 0 24 24"
              fill="currentColor"
              aria-hidden="true"
            >
              <path
                d="M12 .5C5.73.5.5 5.73.5 12a11.5 11.5 0 007.86 10.94c.58.1.79-.25.79-.56v-2c-3.2.7-3.88-1.54-3.88-1.54-.53-1.34-1.3-1.7-1.3-1.7-1.06-.72.08-.71.08-.71 1.17.08 1.79 1.2 1.79 1.2 1.04 1.79 2.73 1.27 3.4.97.1-.76.41-1.27.74-1.56-2.55-.29-5.23-1.28-5.23-5.7 0-1.26.45-2.29 1.19-3.1-.12-.29-.52-1.46.11-3.05 0 0 .97-.31 3.18 1.18a11 11 0 015.8 0c2.2-1.49 3.17-1.18 3.17-1.18.63 1.59.23 2.76.11 3.05.74.81 1.19 1.84 1.19 3.1 0 4.43-2.69 5.41-5.25 5.69.42.36.79 1.08.79 2.18v3.23c0 .31.21.67.8.56A11.5 11.5 0 0023.5 12C23.5 5.73 18.27.5 12 .5z"
              />
            </svg>
            GitHub
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from "vue";

// Detecta a foto em src/assets/img/ em tempo de build sem quebrar caso não exista.
// Quando o arquivo foto.{jpg,jpeg,png,webp} for adicionado, o glob o resolve
// automaticamente e o layout passa a exibi-lo — sem alterar código.
const fotos = import.meta.glob("../assets/img/foto.{jpg,jpeg,png,webp}", {
  eager: true,
  import: "default",
});
const fotoUrl = Object.values(fotos)[0] || null;

// Fallback extra: se a img existir mas falhar ao carregar, cai no placeholder.
const imgErro = ref(false);

// Scroll suave até a seção de projetos.
function irParaProjetos() {
  document.querySelector("#projetos")?.scrollIntoView({ behavior: "smooth" });
}

// Links sociais (mesmos do Contato). path = SVG inline da marca.
// ⚠️ WhatsApp é placeholder — para trocar, altere só o número no link wa.me.
// destaque: true → WhatsApp ganha realce em verde (melhor canal de contato).
const socials = [
  {
    nome: "WhatsApp",
    url: "https://wa.me/5586999457187",
    destaque: true,
    path: "M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413Z",
  },
  {
    nome: "GitHub",
    url: "https://github.com/mateussousadev",
    destaque: false,
    path: "M12 .5C5.73.5.5 5.73.5 12a11.5 11.5 0 007.86 10.94c.58.1.79-.25.79-.56v-2c-3.2.7-3.88-1.54-3.88-1.54-.53-1.34-1.3-1.7-1.3-1.7-1.06-.72.08-.71.08-.71 1.17.08 1.79 1.2 1.79 1.2 1.04 1.79 2.73 1.27 3.4.97.1-.76.41-1.27.74-1.56-2.55-.29-5.23-1.28-5.23-5.7 0-1.26.45-2.29 1.19-3.1-.12-.29-.52-1.46.11-3.05 0 0 .97-.31 3.18 1.18a11 11 0 015.8 0c2.2-1.49 3.17-1.18 3.17-1.18.63 1.59.23 2.76.11 3.05.74.81 1.19 1.84 1.19 3.1 0 4.43-2.69 5.41-5.25 5.69.42.36.79 1.08.79 2.18v3.23c0 .31.21.67.8.56A11.5 11.5 0 0023.5 12C23.5 5.73 18.27.5 12 .5z",
  },
  {
    nome: "LinkedIn",
    url: "https://www.linkedin.com/in/mateussousa-b9921b270",
    destaque: false,
    path: "M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z",
  },
];
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
          class="h-60 w-60 rounded-full border border-border object-cover shadow-md"
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
         Amo programar — e que bom que vivo disso.
        </h1>

        <!-- Subtítulo -->
        <p class="mt-6 text-lg text-muted">
          PHP com Laravel e Vue são meu dia a dia. Desde 2023 construindo
          produtos para setor público e no privado.
        </p>

        <!-- Botões -->
        <div
          class="mt-8 flex flex-col items-center gap-5 sm:flex-row sm:justify-center lg:justify-start"
        >
          <!-- CTA primário -->
          <button
            type="button"
            class="w-full rounded-md bg-accent px-5 py-2.5 text-sm font-semibold text-white shadow-sm transition-colors hover:bg-accent-hover sm:w-auto"
            @click="irParaProjetos"
          >
            Ver projetos
          </button>

          <!-- Sociais (mesmos do Contato): botões-ícone.
               WhatsApp tem leve destaque em verde (melhor canal de contato). -->
          <div class="flex items-center gap-3">
            <a
              v-for="social in socials"
              :key="social.nome"
              :href="social.url"
              target="_blank"
              rel="noopener noreferrer"
              :aria-label="social.nome"
              :title="social.nome"
              class="inline-flex h-11 w-11 items-center justify-center rounded-md border transition-colors"
              :class="
                social.destaque
                  ? 'border-green/60 bg-green/10 text-green hover:border-green hover:bg-green/20'
                  : 'border-border text-muted hover:border-accent hover:text-accent'
              "
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-5 w-5"
                viewBox="0 0 24 24"
                fill="currentColor"
                aria-hidden="true"
              >
                <path :d="social.path" />
              </svg>
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

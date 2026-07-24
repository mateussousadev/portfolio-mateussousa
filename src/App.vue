<script setup>
import { onMounted, onBeforeUnmount, ref } from 'vue'

import NavBar from './components/NavBar.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import StackSection from './components/StackSection.vue'
import TutorsSection from './components/TutorsSection.vue'
import ContactSection from './components/ContactSection.vue'
import FooterSection from './components/FooterSection.vue'

// Referência ao observer para conseguir desconectar no unmount.
let observer = null

// --- Parallax do fundo ---------------------------------------------------
// scrollY guarda o deslocamento atual; o template usa esse valor pra empurrar
// cada camada em velocidades diferentes. Atualizamos dentro de rAF pra não
// travar o scroll.
const scrollY = ref(0)
let ticking = false

function onScroll() {
  if (ticking) return
  ticking = true
  requestAnimationFrame(() => {
    scrollY.value = window.scrollY
    ticking = false
  })
}

onMounted(() => {
  window.addEventListener('scroll', onScroll, { passive: true })


  // Seleciona todos os elementos marcados com [data-reveal].
  // Estado inicial (definido no template via classes Tailwind):
  //   opacity-0 translate-y-4 transition-all duration-500
  // Ao entrar na viewport, adicionamos as classes de estado "visível".
  const targets = document.querySelectorAll('[data-reveal]')

  // Se o navegador não suportar IntersectionObserver, revela tudo direto.
  if (!('IntersectionObserver' in window)) {
    targets.forEach((el) => el.classList.add('opacity-100', 'translate-y-0'))
    return
  }

  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.remove('opacity-0', 'translate-y-4')
          entry.target.classList.add('opacity-100', 'translate-y-0')
          // Anima só uma vez — para de observar após revelar.
          observer.unobserve(entry.target)
        }
      })
    },
    {
      threshold: 0.12,
      // Antecipa um pouco a revelação antes de entrar totalmente na tela.
      rootMargin: '0px 0px -40px 0px',
    },
  )

  targets.forEach((el) => observer.observe(el))
})

onBeforeUnmount(() => {
  if (observer) observer.disconnect()
  window.removeEventListener('scroll', onScroll)
})
</script>

<template>
  <div class="relative min-h-screen bg-bg text-text antialiased">
    <!-- Fundo com textura + parallax: fixo atrás de todo o conteúdo.
         Cada camada se move numa velocidade pra dar profundidade. -->
    <div class="parallax-bg" aria-hidden="true">
      <div
        class="parallax-grid"
        :style="{ transform: `translate3d(0, ${scrollY * 0.12}px, 0)` }"
      ></div>
      <div
        class="parallax-glow parallax-glow--one"
        :style="{ transform: `translate3d(0, ${scrollY * 0.28}px, 0)` }"
      ></div>
      <div
        class="parallax-glow parallax-glow--two"
        :style="{ transform: `translate3d(0, ${scrollY * -0.2}px, 0)` }"
      ></div>
      <div class="parallax-noise"></div>
    </div>

    <!-- Conteúdo acima do fundo -->
    <div class="relative z-10">
      <!-- NavBar: fixa no topo, não participa do fade-in -->
      <NavBar />

    <main>
      <!-- Cada seção é envolvida por um wrapper [data-reveal] com o estado
           inicial de animação. O IntersectionObserver revela ao scroll. -->
      <HeroSection />

      <div
        data-reveal
        class="opacity-0 translate-y-4 transition-all duration-500 ease-out"
      >
        <AboutSection />
      </div>

      <div
        data-reveal
        class="opacity-0 translate-y-4 transition-all duration-500 ease-out"
      >
        <ProjectsSection />
      </div>

      <div
        data-reveal
        class="opacity-0 translate-y-4 transition-all duration-500 ease-out"
      >
        <StackSection />
      </div>

      <div
        data-reveal
        class="opacity-0 translate-y-4 transition-all duration-500 ease-out"
      >
        <TutorsSection />
      </div>

      <div
        data-reveal
        class="opacity-0 translate-y-4 transition-all duration-500 ease-out"
      >
        <ContactSection />
      </div>
      </main>

      <FooterSection />
    </div>
  </div>
</template>

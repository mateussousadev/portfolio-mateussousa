<script setup>
import { onMounted, onBeforeUnmount } from 'vue'

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

onMounted(() => {
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
})
</script>

<template>
  <div class="min-h-screen bg-bg text-text antialiased">
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
</template>

<script setup>
import { ref } from 'vue'

// Estado do menu mobile (hamburger). Sem libs externas — apenas v-show.
const menuOpen = ref(false)

// Links de navegação (âncoras das seções).
const links = [
  { label: 'Sobre', href: '#sobre' },
  { label: 'Projetos', href: '#projetos' },
  { label: 'Stack', href: '#stack' },
  { label: 'Contato', href: '#contato' },
]

// Fecha o menu ao clicar num link (mobile).
function closeMenu() {
  menuOpen.value = false
}
</script>

<template>
  <header
    class="sticky top-0 z-50 border-b border-border bg-bg/95 backdrop-blur"
  >
    <nav
      class="mx-auto flex max-w-5xl items-center justify-between px-6 py-4"
    >
      <!-- Logo -->
      <a
        href="#"
        class="font-sans text-lg font-bold text-text transition-colors hover:text-accent"
      >
        Mateus Sousa
      </a>

      <!-- Links desktop -->
      <ul class="hidden items-center gap-8 sm:flex">
        <li v-for="link in links" :key="link.href">
          <a
            :href="link.href"
            class="text-sm font-medium text-muted transition-colors hover:text-text"
          >
            {{ link.label }}
          </a>
        </li>
      </ul>

      <!-- Botão hamburger (mobile) -->
      <button
        type="button"
        class="text-muted transition-colors hover:text-text sm:hidden"
        :aria-expanded="menuOpen"
        aria-label="Abrir menu de navegação"
        @click="menuOpen = !menuOpen"
      >
        <!-- Ícone hamburger / fechar -->
        <svg
          v-if="!menuOpen"
          xmlns="http://www.w3.org/2000/svg"
          class="h-6 w-6"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          stroke-width="2"
        >
          <path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16" />
        </svg>
        <svg
          v-else
          xmlns="http://www.w3.org/2000/svg"
          class="h-6 w-6"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          stroke-width="2"
        >
          <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
        </svg>
      </button>
    </nav>

    <!-- Menu mobile expansível -->
    <div
      v-show="menuOpen"
      class="border-t border-border bg-bg sm:hidden"
    >
      <ul class="mx-auto max-w-5xl px-6 py-2">
        <li v-for="link in links" :key="link.href">
          <a
            :href="link.href"
            class="block py-3 text-sm font-medium text-muted transition-colors hover:text-text"
            @click="closeMenu"
          >
            {{ link.label }}
          </a>
        </li>
      </ul>
    </div>
  </header>
</template>

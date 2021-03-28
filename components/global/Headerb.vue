<template>
  <nav class="scrim-bg fixed z-40 top-0 inset-x-0 pt-3 px-3" aria-label="Main Menu">
    <nav class="mx-auto flex flex-wrap justify-between items-center py-8">
        <div>
          <nuxt-link v-if="theme === 'theme-light'" to="/">LOGO</nuxt-link>
          <nuxt-link v-else to="/">LOGO</nuxt-link>
        </div>
        <div class="block lg:hidden">
          <button @click="toggle" class="flex items-center px-3 py-2 border rounded border-gray-500 hover:text-gray-600 hover:border-gray-600">
            <svg class="current-color h-3 w-3" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z" fill="gray" /></svg>
          </button>
        </div>
        <ul
          class="uppercase tracking-wide font-bold w-full block flex-grow lg:space-x-8 space-y-6 lg:space-y-0 lg:flex lg:flex-initial lg:w-auto items-center mt-8 lg:mt-0"
          :class="isOpen ? 'block': 'hidden'"
        >
          <li class="mb-6 lg:mb-0">
            <!-- <search-input /> -->
          </li>
          <li>
            <a v-if="$route.path === '/'" href="/#projects" v-scroll-to="'#projects'" class="text-copy-primary hover:text-gray-600">Link</a>
            <nuxt-link v-else to="/#projects" v-scroll-to="'/#projects'" class="text-copy-primary hover:text-gray-600">Link</nuxt-link>
          </li>
          <li>
            <a v-if="$route.path === '/'" href="/#about" v-scroll-to="'#about'" class="text-copy-primary hover:text-gray-600">Link</a>
            <nuxt-link v-else to="/#about" v-scroll-to="'/#about'" class="text-copy-primary hover:text-gray-600">Link</nuxt-link>
          </li>
          <li>
            <a v-if="$route.path === '/'" href="/#contact" v-scroll-to="'#contact'" class="text-copy-primary hover:text-gray-600">Link</a>
            <nuxt-link v-else to="/#contact" v-scroll-to="'/#contact'" class="text-copy-primary hover:text-gray-600">Link</nuxt-link>
          </li>
          <li>
            <nuxt-link to="/blog" class="text-copy-primary hover:text-gray-600">Link</nuxt-link>
            <!-- <g-link to="/blog" class="text-copy-primary hover:text-gray-600">Blog</g-link> -->
          </li>
        </ul>
      </nav>
  </nav>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      isOpen: false,
      theme: '',
    }
  },
  methods: {
    toggle() {
      this.isOpen = !this.isOpen
    },
    updateTheme(theme) {
      this.theme = theme
    }
  }
}
</script>

<style lang="postcss" scoped>
.scrim-bg {
  &::before {
    content: '';
    z-index: -1;
    background-color: var(--bg);
    @apply absolute bottom-0 inset-x-0 h-12 mb-4 transition-colors duration-200 ease-in-out;
  }
  &::after {
    content: '';
    z-index: -1;
    opacity: 1;
    animation: fadeIn1 500ms ease-in-out;
    @apply pointer-events-none absolute bottom-0 inset-x-0 h-16 -mb-12;
    background: linear-gradient(to bottom, #111827, cubic-bezier(0.15, 0, 0.45, 1), transparent);
  }
}
.nuxt-link-exact-active {
  @apply text-gray-200 border-gray-400 bg-gray-800 bg-opacity-25 cursor-default;
}

.light-mode {
  & .scrim-bg {
    &::after {
      animation-name: fadeIn2;
      background: linear-gradient(to bottom, #e5e7eb, cubic-bezier(0.15, 0, 0.45, 1), transparent);
    }
  }
  & .nuxt-link-exact-active {
    @apply text-primary-700 border-gray-600 bg-gray-100;
  }
}

/* Need two because of smoother switching between color modes */
@keyframes fadeIn1 {
  from { opacity: 0; }
  to { opacity: 1; }
}
@keyframes fadeIn2 {
  from { opacity: 0; }
  to { opacity: 1; }
}
</style>

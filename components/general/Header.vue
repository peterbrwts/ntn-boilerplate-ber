<template>
<header class="py-6">
    <div class="sm:mx-auto flex flex-wrap">
      <div class="flex-1 flex justify-between items-center">
      <a href="#">
        NTN
    </a>
  </div>
      <!-- Desktop nav list -->
     <div class="hidden lg:flex lg:items-center lg:w-auto w-full" id="menu">
    <nav>
      <ul class="lg:flex items-center justify-between text-base text-gray-700 pt-4 lg:pt-0 lg:mx-5">
      <li class="flex-1 mr-2">
        <nuxt-link class="btn block lg:p-4 py-3 px-0 block border-b-2 border-transparent hover:border-indigo-400" to="/">Home</nuxt-link>
      </li>
      <li class="flex-1 mr-2">
        <nuxt-link class="btn block lg:p-4 py-3 px-0 block border-b-2 border-transparent hover:border-indigo-400" to="/blog">Blog</nuxt-link>
      </li>
      <li class="flex-1">
        <nuxt-link class="btn block lg:p-4 py-3 px-0 block border-b-2 border-transparent hover:border-indigo-400" to="/projects">Projects</nuxt-link>
      </li>
    </ul>

    </nav>

  </div>
      <!-- Toggle menu mobile icon -->
      <div class="ml-auto sm:hidden p-6" @click="menu = !menu">
        menu
      </div>
    </div>
    <!-- Mobile nav list -->
    <nav v-show="menu" class="w-full">
      <ul class="flex flex-col text-center">
        <li
          v-for="(item, index) in items"
          :key="index"
        >
          <a :href="item.href" class="hover:bg-green-500 p-6 block">{{ item.title }}</a>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<style lang="postcss" scoped>
 #menu-toggle:checked + #menu {
        display: block;
      }
.nuxt-link-exact-active {
  @apply text-accent-100 bg-accent bg-opacity-20;
  &:hover {
    @apply text-white bg-accent-600;
  }
}
.light-mode {
  & .nuxt-link-exact-active {
    @apply text-accent-600;
    &:hover {
      @apply text-white;
    }
  }
}
</style>

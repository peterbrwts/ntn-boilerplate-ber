<template>
  <header class="top topnav h-54px p-2 text-white">
    <div class="container mx-auto flex justify-left items-center">
      <div class="left self-end" v-if="!isContentPage">
        <ul class="flex lang-switch justify-around">
          <li>
            <nuxt-link
              class="text-md ml-3 font-semibold text-white hover:text-gray-400 focus:underline"
              :to="switchLocalePath('en')"
              >EN</nuxt-link
            >
          </li>

          <li>
            <nuxt-link
              class="text-md ml-3 font-semibold text-white hover:text-gray-400 focus:underline"
              :to="switchLocalePath('fr')"
              >FR</nuxt-link
            >
          </li>
          <li>
            <nuxt-link
              class="text-md ml-3 font-semibold text-white hover:text-gray-400 focus:underline"
              :to="switchLocalePath('nl')"
              >NL</nuxt-link
            >
          </li>
        </ul>
      </div>
    </div>
  </header>
</template>

<script>
const data = () => ({
  title: 'NTN Boilerplate Berwouts',
})
const computed = {
  isContentPage() {
    return this.$route.name.includes('slug')
  },
}
export default {
  name: 'Header',
  data,
  computed,
}
</script>

<style></style>
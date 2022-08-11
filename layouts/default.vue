<template>
  <div class="wrapper">
    <Header />
    <nuxt />
    
    <cookie-control />
  </div>
</template>

<script>
import cookieControl from '~/components/cookieControl/cookieControl'
export default {
  components: {
    cookieControl,
  },
}
</script>
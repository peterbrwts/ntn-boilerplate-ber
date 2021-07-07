<template>
  <div class="wrapper">
    <Header />
    <nuxt />
    <ColorModePicker />
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
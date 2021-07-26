<template>
  <main>
    <section class="self-center flex flex-col flex-1 items-center justify-center">
      <h1 class="title text-center">{{ $t('title') }}</h1>
      <h2 class="subtitle text-center">Boilerplate Berwouts</h2>
      <div class="">
        <Langswitch />
      </div>
    </section>

    <section class="mt-8">
      <h3 class="text-primary-600 dark:text-primary-400 max-w-5xl mx-auto">Latest blog post</h3>
      <posts post-type="blog" :amount="2" />
    </section>
  </main>
</template>
<script>
export default {
  components: {},
}
</script>
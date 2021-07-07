<template>
  <div class="cookie-control__footer">
    <div class="">
      <template v-if="modal">
        <button @click="$cookies.toggleModal" class="bg-green-500 text-white active:bg-green-600  font-bold  px-4 py-2 rounded shadow hover:shadow-lg outline-none focus:outline-none lg:mr-1 lg:mb-0 ml-3 mb-3 ease-linear transition-all duration-150">
          {{ cookies.text.closeCookies }}
        </button>
        <button @click="$cookies.setConsentModal({ type: 'partial' })" class="bg-green-500 text-white active:bg-green-600  font-bold  px-4 py-2 rounded shadow hover:shadow-lg outline-none focus:outline-none lg:mr-1 lg:mb-0 ml-3 mb-3 ease-linear transition-all duration-150"
        >
          {{ cookies.text.save }}
        </button>
      </template>
      <template v-else>
        <button @click="cookies.modal = true" class="bg-green-500 text-white active:bg-green-600  font-bold  px-4 py-2 rounded shadow hover:shadow-lg outline-none focus:outline-none lg:mr-1 lg:mb-0 ml-3 mb-3 ease-linear transition-all duration-150">{{
          cookies.text.manageCookies
        }}</button>
        <button @click="$cookies.setConsentModal" class="bg-green-500 text-white active:bg-green-600  font-bold  px-4 py-2 rounded shadow hover:shadow-lg outline-none focus:outline-none lg:mr-1 lg:mb-0 ml-3 mb-3 ease-linear transition-all duration-150">{{
          cookies.text.acceptAll
        }}</button>
      </template>
    </div>
  </div>
</template>
<script>

export default {
  name: 'CookieControlFooter',
  props: {
    description: {
      type: Array,
      default: () => [],
    },
    cookies: {
      type: Object,
      default: () => ({}),
    },
    modal: {
      type: Boolean,
      default: () => false,
    },
  },
}
</script>

<style lang="scss">
.cookie-control__footer {
  
  pointer-events: all;

  padding: 0.5rem 1rem 1rem 1rem;
  

  &__wrapper {
    width: 100%;

    .btn {
      width: 100%;

      &:first-child {
          padding: 1rem;
      }
    }

    .btn .btn__wrapper {
      display: block;
    }

    @media screen and (min-width: 768px) {
      display: flex;
      justify-content: flex-end;

      .btn {
        width: auto;
        &:first-child {
          padding-bottom: 0;
          margin-right: 1rem
        }
      }
    }
  }
}
</style>

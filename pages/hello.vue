<template>
  <div>
    {{ page }}
    <nuxt-content :document="page" />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  async asyncData({ $content }) {
    const page = await $content('hello').fetch()

    return {
      page,
    }
  },

  computed: {
    pageProps(): [string, any][] {
      // Bug?
      return [['text', { test: 'text' }]] // Object.entries(this.page)
    },
  },
})
</script>

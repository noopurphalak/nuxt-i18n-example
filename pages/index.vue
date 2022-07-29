<template>
  <div>
    <div>
      <nuxt-link
        v-for="locale in availableLocales"
        :key="locale.code"
        :to="switchLocalePath(locale.code)"
        >{{ locale.name }}</nuxt-link
      >
    </div>
    {{ $t('welcome') }}
  </div>
</template>

<script lang="ts">
import { LocaleObject } from '@nuxtjs/i18n'
import Vue from 'vue'

export default Vue.extend({
  name: 'IndexPage',
  computed: {
    availableLocales(): LocaleObject[] {
      return (this.$i18n.locales as any).filter(
        (i: LocaleObject) => i.code !== this.$i18n.locale
      )
    },
  },
})
</script>

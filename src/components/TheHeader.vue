<script lang="ts" setup>
import { defineOptions } from 'vue';
import { availableLocales, loadLanguageAsync } from '~/modules/i18n';

defineOptions({ name: 'the-header' })

const { t, locale } = useI18n()

async function toggleLocales() {
  // change to some real logic
  const locales = availableLocales
  const newLocale = locales[(locales.indexOf(locale.value) + 1) % locales.length]
  await loadLanguageAsync(newLocale)
  locale.value = newLocale
}
</script>

<template>
  <div class="the-header">
    <!-- -->
    <TheAlignContainer class="flex justify-between items-center h-full">
      <RouterLink to="/" :title="t('button.home')" class="mr-12">
        LOGO
      </RouterLink>
      <nav class="the-header-nav">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/hi/miemiemie">{{ t('intro.hi') }}</RouterLink>
      </nav>

      <div class="flex items-center h-full gap-4">
        <a :title="t('button.toggle_langs')" @click="toggleLocales()">
          <div i-carbon-language />
        </a>

        <a :title="t('button.toggle_dark')" @click="toggleDark()">
          <div i="carbon-sun dark:carbon-moon" />
        </a>
      </div>

    </TheAlignContainer>
  </div>
</template>

<style lang="postcss">
.the-header {
  @apply h-10 border-b border-b-black dark:border-b-white;
}


.the-header-nav {
  @apply flex-1 flex gap-4 h-full;
}

.the-header-nav a {
  @apply flex items-center cursor-pointer px-4 h-full hover:bg-black hover:text-white dark:hover:bg-white dark:hover:text-black;
}
</style>

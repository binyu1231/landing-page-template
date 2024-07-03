<template>
  <main class="page-container">
    <TheHeader />
    <div class="flex-1">
      <RouterView />
    </div>
    <TheFooter />
  </main>
</template>
<style lang="postcss">
.page-container {
  @apply gray-700 dark:gray-200 min-h-100vh flex flex-col justify-between;
}
</style>
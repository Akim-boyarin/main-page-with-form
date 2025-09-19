<script setup>
  import PageHeader from '@/components/PageHeader.vue';
  import PageFooter from '@/components/PageFooter.vue';
  import GreetingBanner from "@/components/GreetingBanner.vue";
  import GreetingInterface from "@/components/GreetingInterface.vue";
</script>

<template>
  <div class="page">
    <PageHeader class="page__header"></PageHeader>
    <main class="page__main">
      <GreetingBanner></GreetingBanner>
      <GreetingInterface></GreetingInterface>
    </main>
    <PageFooter class="page__footer"></PageFooter>
  </div>
</template>

<style lang="scss">
  @use "@/assets/style/index.scss";

  .page {
    position: relative;
    &__header {
      position: sticky;
      top: 0;            /* отступ от верха */
      z-index: 1000;
    }
  }
</style>

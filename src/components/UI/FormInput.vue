<script setup>
  defineProps({
    placeholder: String,
  });
  const value = defineModel();
</script>

<template>
  <input type="text" class="form-input" :placeholder="placeholder" v-model="value" />
</template>

<style lang="scss">
  @use "@/assets/style/index.scss" as *;

  .form-input {
    display: block;
    width: 100%;
    height: 48px;
    background-color: rgba(255, 255, 255, 0.85);
    border: 1px solid #fff;
    border-radius: 3px;
    font-family: "Lato", sans-serif;
    font-weight: 400;
    font-size: 16px;
    line-height: 110%;
    color: #272733;
    @include flex(row, flex-start, center);
    padding-left: 12px;
  }
</style>
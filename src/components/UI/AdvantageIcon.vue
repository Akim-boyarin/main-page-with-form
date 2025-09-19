<script setup>

</script>

<template>
  <div class="advantage">
    <slot></slot>
  </div>
</template>

<style lang="scss">
@use "@/assets/style/index.scss" as *;

.advantage {
  width: 100px;
  height: 100px;
  background-color: #009edb;
  border-radius: 50%;
  border: 5px solid #00688f;
  @include flex(row, center, center);
}
</style>
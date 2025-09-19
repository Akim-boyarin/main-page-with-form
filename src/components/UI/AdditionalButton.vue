<script setup>
const emit = defineEmits(['click']);

function handleClick() {
  emit('click');
}
</script>

<template>
  <button class="additional-button" type="button" @click="handleClick">
    <slot></slot>
  </button>
</template>

<style lang="scss">
@use "@/assets/style/index.scss" as *;

.additional-button {
  display: block;
  background-color: #fff;
  border: 1px solid #6F6D7B;
  border-radius: 4px;
  width: 100%;
  font-family: 'Lato', sans-serif;
  font-size: 14px;
  font-weight: 400;
  line-height: 100%;
  text-transform: uppercase;
  color: #2A2B30;
  padding: 15px 0;
}
</style>
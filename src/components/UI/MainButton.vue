<script setup>
const emit = defineEmits(['click']);

function handleClick() {
  emit('click');
}
</script>

<template>
  <button class="main-button" type="button" @click="handleClick">
    <slot></slot>
  </button>
</template>

<style lang="scss">
@use "@/assets/style/index.scss" as *;

.main-button {
  display: block;
  background-color: #3E9CDC;
  border: 1px solid #fff;
  border-radius: 4px;
  width: 100%;
  font-family: 'Lato', sans-serif;
  font-size: 14px;
  font-weight: 400;
  line-height: 100%;
  text-transform: uppercase;
  color: #fff;
  padding: 15px 0;

}
</style>
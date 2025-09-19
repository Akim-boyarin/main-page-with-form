<script setup>
import AdvantageIcon from "@/components/UI/AdvantageIcon.vue";

defineProps({
  advantage: Object,
  index: Number,
  isLast: Boolean,
});
</script>

<template>
  <div class="advantage-card">
    <div class="advantage-card__content">
      <AdvantageIcon class="advantage-card__icon">
        <img :src="advantage.img" alt="advantage icon">
      </AdvantageIcon>
      <p class="advantage-card__text">
        {{ advantage.text }}
      </p>
    </div>
    <div class="advantage-card__points" v-if="!isLast">
      <div class="advantage-card__point"></div>
      <div class="advantage-card__point"></div>
      <div class="advantage-card__point"></div>
      <div class="advantage-card__point"></div>
      <div class="advantage-card__point"></div>
    </div>
  </div>
</template>

<style lang="scss">
@use "@/assets/style/index.scss" as *;

.advantage-card {
  position: relative;
  width: 304px;
  &__content {
    @include flex(column, flex-start, center);
    width: 190px;
    gap: 20px;
    flex-grow: 0;
  }
  &__icon {
    flex-grow: 0;
    flex-shrink: 0;
  }
  &__text {
    font-family: 'Lato', sans-serif;
    font-size: 16px;
    font-weight: 400;
    line-height: 110%;
    color: #FFFFFF;
    text-align: center;
  }
  &__points {
    width: 110px;
    @include flex(row, space-between, center);
    position: absolute;
    top: 47px;
    right: -2px;
  }
  &__point {
    width: 6px;
    height: 6px;
    border-radius: 50%;
    background-color: #C4C4C4;
  }
}
</style>
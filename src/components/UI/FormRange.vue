<script setup>
  defineProps({
    min: Number,
    max: Number,
    step: Number,
    text: String,
  });
  const value = defineModel();
</script>

<template>
  <div class="form-range">
    <div class="form-range__text-content">
      <p class="form-range__text">{{ text }}</p>
      <p class="form-range__value-display">{{ value }}%</p>
    </div>
    <input type="range"
      class="form-range__field"
      :min="min"
      :max="max"
      :step="step"
      v-model="value"
    />
  </div>
</template>

<style lang="scss">
  @use "@/assets/style/index.scss" as *;

  .form-range {
    height: 48px;
    &__text-content {
      @include flex(row, space-between, center);
      font-family: 'Lato', sans-serif;
      font-size: 16px;
      line-height: 110%;
      color: #fff;
      &__text {
        flex-grow: 1;
        font-weight: 400;
      }

      &__value-display {
        flex-grow: 0;
        width: 50px;
        text-align: end;
        font-weight: 600;
        margin-left: 5px;
      }
    }

    &__field {
      display: block;
      width: 100%;
      padding: 12px 0;
      &::-webkit-slider-thumb {
        -webkit-appearance: none;
        appearance: none;
        width: 30px;
        height: 30px;
        border-radius: 50%;
        background: #009edb;
        position: relative;
        top: -4px;
      }
      &::-webkit-slider-runnable-track {
        height: 6px;
        border-radius: 3px;
        background-color: rgba(255, 255, 255, 0.85);
      }
    }
  }
</style>
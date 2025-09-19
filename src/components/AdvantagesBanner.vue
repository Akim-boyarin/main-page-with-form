<script setup>
import AdvantageCard from "@/components/UI/AdvantageCard.vue";
import {SwiperSlide} from "swiper/vue";

defineProps({
  advantages: Array,
});
</script>

<template>
  <div class="advantages-banner">
    <div class="advantages-banner__content">
      <div class="advantages-banner__card-wrapper" v-for="(advantage, advantageIndex) in advantages" :key="advantage.id" :style="{ 'z-index': (advantages.length - advantageIndex) }">
        <AdvantageCard :advantage="advantage" :index="advantageIndex" :isLast="advantageIndex === advantages.length - 1" ></AdvantageCard>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
@use "@/assets/style/index.scss" as *;

.advantages-banner {
  width: 100%;
  overflow: hidden;
  &__content {
    @include flex(row, center, center);
    position: relative;
    left: 40px;
  }
  &__card-wrapper {
    width: 300px;
    position: relative;
  }
}
</style>
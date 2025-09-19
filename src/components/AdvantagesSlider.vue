<script setup>
import { Swiper, SwiperSlide } from 'swiper/vue';
import 'swiper/css';
import AdvantageCard from "@/components/UI/AdvantageCard.vue";

defineProps({
  advantages: Array,
});
</script>

<template>
  <div class="advantages-slider">
    <Swiper
        :slides-per-view="'auto'"
    >
      <SwiperSlide v-for="(advantage, advantageIndex) in advantages" :key="advantage.id" :style="{ 'z-index': (advantages.length - advantageIndex) }">
        <AdvantageCard :advantage="advantage" :index="advantageIndex" :isLast="advantageIndex === advantages.length - 1" >
        </AdvantageCard>
      </SwiperSlide>
    </Swiper>
  </div>
</template>

<style lang="scss">
@use "@/assets/style/index.scss" as *;

.advantages-slider {
  padding-left: 16px;
  @media (min-width: 640px) {
    padding-left: 20px;
  }
  @media (min-width: 1100px) {
    padding-left: 45px;
  }
}
.advantages-slider .swiper-slide {
  position: relative;
  width: 300px;
}
</style>
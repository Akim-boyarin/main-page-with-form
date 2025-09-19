<script setup>
import bannerBackground from '@/assets/img/greeting-banner__background.png';
import MainButton from "@/components/UI/MainButton.vue";
import AdditionalButton from "@/components/UI/AdditionalButton.vue";

function buy() {
  console.log('buy');
}
function knowMore() {
  console.log('know more');
}
</script>

<template>
  <section class="hero">
    <div class="hero__background">
      <img :src="bannerBackground" alt="Background" class="hero__image" />
    </div>
    <div class="hero__content-wrapper">
      <div class="hero__content">
        <h1 class="hero__title"><span>Lorem ipsum</span> dolor sit amet
          consectetur <span>adipiscing</span></h1>
        <div class="hero__text">
          <p class="hero__paragraph">At vero eos et accusamus et iusto odio dignissimos ducimus!</p>
          <ul class="hero__list">
            <li class="hero__list-item">Totam rem aperiam eaque ipsa</li>
            <li class="hero__list-item">Sit voluptatem accusantium doloremque laudantium</li>
            <li class="hero__list-item">Sed ut perspiciatis, unde omnis iste natus error</li>
          </ul>
        </div>
        <div class="hero__buttons">
          <MainButton class="hero__button" @click="buy">Заказать</MainButton>
          <AdditionalButton class="hero__button" @click="knowMore">Подробнее</AdditionalButton>
        </div>
      </div>
    </div>
  </section>

</template>

<style lang="scss">
@use "@/assets/style/index.scss" as *;

.hero {
  position: relative;
  &__background {
    width: 100%;
    position: relative;
    z-index: 1;
    height: 600px;
    @media (min-width: 1100px) {
      height: auto;
    }
    @media (min-width: 2000px) {
      height: 1000px;
      overflow: hidden;
    }
  }
  &__image {
    display: block;
    height: 100%;
    position: absolute;
    z-index: 1;
    top: 0;
    right: 0;
    @media (min-width: 1100px) {
      position: relative;
      width: 100%;
      height: auto;
    }
    @media (min-width: 2000px) {
      width: 110%;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }
  }
  &__content-wrapper {
    position: absolute;
    top: 0;
    left: 0;
    z-index: 2;
    width: 100%;
    height: 100%;
    @include flex(column, center, center);
    @media (min-width: 1100px) {
      align-items: flex-start;
      margin-left: 25px;
    }
    @media (min-width: 1600px) {
      max-width: 1600px;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      margin-left: 0;
    }
  }
  &__content {
    width: 100%;
    backdrop-filter: blur(10px);
    padding: 20px 16px;
    max-width: 400px;
    @media (min-width: 1100px) {
      max-width: 680px;
      padding: 20px;
    }
    @media (min-width: 1430px) {
      max-width: 800px;
    }
    @media (min-width: 1600px) {
      position: relative;
      left: -20px;
    }
  }
  &__title {
    font-family: 'Lato', sans-serif;
    font-size: 24px;
    font-weight: 700;
    line-height: 120%;
    text-transform: uppercase;
    color: #000;
    margin-bottom: 32px;
    @media (min-width: 1100px) {
      font-size: 48px;
      margin-bottom: 80px;
    }
    & span {
      color: #3E9CDC;
    }
  }

  &__paragraph {
    font-family: 'Lato', sans-serif;
    font-weight: 700;
    font-size: 18px;
    line-height: 100%;
    color: #000000;
    margin-bottom: 10px;
    @media (min-width: 1100px) {
      font-size: 20px;
    }
  }

  &__list {
    @include flex(column, flex-start, flex-start);
    gap: 5px;
    margin-bottom: 24px;
    @media (min-width: 1100px) {
      margin-bottom: 80px;
    }
  }

  &__list-item {
    font-family: 'Lato', sans-serif;
    font-weight: 400;
    font-size: 18px;
    line-height: 100%;
    color: #000000;
    @media (min-width: 1100px) {
      font-size: 20px;
    }

    &::before {
      content: "-";
      margin-right: 8px;
      color: inherit;
    }
  }

  &__buttons {
    @include flex(column, flex-start, flex-start);
    gap: 10px;
    @media (min-width: 1100px) {
      gap: 30px;
      flex-direction: row;
    }
  }

  &__button {
    @media (min-width: 1100px) {
      width: 183px;
    }
  }
}

</style>
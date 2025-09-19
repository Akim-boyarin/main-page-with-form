<script setup>
import {reactive} from "vue";
import searchIcon from '@/assets/img/greeting-inerface__search-icon.svg';
import percentIcon from '@/assets/img/greeting-interface__percent-icon.svg';
import fileIcon from '@/assets/img/greeting-interface__file-icon.svg';
import messageIcon from '@/assets/img/greeting-interface__message-icon.svg';
import moneyIcon from '@/assets/img/greeting-interface__money-icon.svg';
import AdvantagesSlider from "@/components/AdvantagesSlider.vue";
import AdvantagesBanner from "@/components/AdvantagesBanner.vue";
import InterfaceForm from "@/components/InterfaceForm.vue";
import backgroundMap from '@/assets/img/greeting-interface__background-map.png';

const advantages = reactive([
  {
    id: 1,
    text: 'Lorem ipsum dolor sit amet',
    img: searchIcon,
  },
  {
    id: 2,
    text: 'Сonsecteturadipiscing elit',
    img: percentIcon,
  },
  {
    id: 3,
    text: 'Sed do eiusmod tempor',
    img: fileIcon,
  },
  {
    id: 4,
    text: 'Esse cillum dolore eu fugiat',
    img: messageIcon,
  },
  {
    id: 5,
    text: 'Excepteur sint occaecat cupidatat non proident',
    img: moneyIcon,
  },
]);
</script>

<template>
  <div class="greeting-interface">
    <div class="greeting-interface__background">
      <img :src="backgroundMap" alt="" class="greeting-interface__background-image">
    </div>
    <div class="greeting-interface__content-wrapper">
      <div class="greeting-interface__text">
        <div class="greeting-interface__text-content">
          <h2 class="greeting-interface__title">Оформление <span>Заказа</span></h2>
          <p class="greeting-interface__description">Перед заполнением формы ознакомьтесь с нашей схемой работы!</p>
        </div>
      </div>
      <div class="greeting-interface__advantages">
        <AdvantagesSlider class="greeting-interface__advantages-slider" :advantages="advantages"></AdvantagesSlider>
        <AdvantagesBanner class="greeting-interface__advantages-banner" :advantages="advantages"></AdvantagesBanner>
      </div>
      <div class="greeting-interface__form-wrapper">
        <InterfaceForm class="greeting-interface__form"></InterfaceForm>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
@use "@/assets/style/index.scss" as *;

.greeting-interface {
  position: relative;
  &__background {
    position: relative;
    z-index: 1;
    background-color: #272733;
    //background-color: white;
    width: 100%;
    height: 840px;
    overflow: hidden;
    @media (min-width: 1100px) {
      height: 920px;
    }
  }
  &__background-image {
    display: block;
    height: 100%;
    position: absolute;
    top: 50%;
    left: 60%;
    transform: translate(-50%, -50%);
    @media (min-width: 1800px) {
      width: 90%;
      height: auto;
      left: 50%;
    }
  }

  &__content-wrapper {
    position: absolute;
    top: 0;
    left: 0;
    z-index: 2;
    width: 100%;
    height: 100%;
    @include flex(column, center, stretch);
    @media (min-width: 1100px) {
      padding-top: 0px;
    }
  }

  &__text {
    @include flex(row, center, center);
    margin-bottom: 50px;
    @media (min-width: 1100px) {
      margin-bottom: 80px;
    }
  }
  &__text-content {
    @include flex(column, flex-start, center);
    padding: 0 16px;
    max-width: 400px;
    @media (min-width: 1100px) {
      max-width: 600px;
    }
  }
  &__title {
    font-family: 'Lato', sans-serif;
    font-size: 21px;
    font-weight: 700;
    line-height: 120%;
    text-transform: uppercase;
    color: #ffffff;
    text-align: center;
    margin-bottom: 18px;
    @media (min-width: 1100px) {
      font-size: 36px;
      margin-bottom: 30px;
    }
    & span {
      color: #3E9CDC;
    }
  }

  &__description {
    font-family: 'Lato', sans-serif;
    font-weight: 400;
    font-size: 16px;
    line-height: 100%;
    color: #BBBBBB;
    text-align: center;
    margin-bottom: 10px;
    @media (min-width: 1100px) {
      font-size: 18px;
    }
  }

  &__advantages {
    margin-bottom: 50px;
    @media (min-width: 1100px) {
      margin-bottom: 80px;
    }
  }

  &__advantages-slider {
    @media (min-width: 1480px) {
      display: none;
    }
  }

  &__advantages-banner {
    display: none;
    @media (min-width: 1480px) {
      display: block;
    }
  }
}
</style>
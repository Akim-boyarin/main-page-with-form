<script setup>
import logo from '@/assets/img/header__logo.svg';
import {reactive} from "vue";

const links = reactive([
  { id: 1, name: 'Бизнес', url: '/main-page-with-form/' },
  { id: 2, name: 'О нас', url: '/main-page-with-form/' },
  { id: 3, name: 'Цены', url: '/main-page-with-form/' },
  { id: 4, name: 'Оформить заказ', url: '/main-page-with-form/' }
]);
</script>

<template>
  <header class="header">
    <div class="header__content-wrapper">
      <img class="header__logo" :src="logo">
      <nav class="header__nav-menu nav-menu">
        <ul class="nav-menu__list">
          <li class="nav-menu__item" v-for="link in links" :key="link.id">
            <a :href="link.url" class="nav-menu__link">{{ link.name }}</a>
          </li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<style lang="scss">
@use "@/assets/style/index.scss" as *;

.header {
  background-color: #10101DE5;
  padding: 25px 16px;
  @include flex(row, center, center);
  @media (min-width: 640px) {
    padding: 30px 20px;
  }
  @media (min-width: 1100px) {
    padding: 32px 45px;
  }

  &__content-wrapper {
    width: 100%;
    max-width: 1600px;
    @media (min-width: 1100px) {
      @include flex(row, space-between, center);
    }
  }
  &__logo {
    display: block;
    margin-bottom: 36px;
    @media (min-width: 1100px) {
      margin-bottom: 0;
    }
  }

  &__nav-menu {
    .nav-menu {

      &__list {
        @include flex(column, flex-start, flex-start);
        @media (min-width: 640px) {
          flex-direction: row;
          justify-content: flex-start;
          gap: 28px;
        }
      }

      &__item {
        &:not(:last-child) {
          margin-bottom: 8px;
          @media (min-width: 1100px) {
            margin-bottom: 0;
          }
        }
      }

      &__link {
        color: #fff;
        font-family: 'Lato', sans-serif;
        font-weight: 600;
        line-height: 120%;
        font-size: 14px;
        text-transform: uppercase;

      }
    }
  }
}
</style>
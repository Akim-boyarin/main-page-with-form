<script setup>
  import { ref } from "vue";
  import buttonIcon from '@/assets/img/interface-form__button-icon.svg';

  const props = defineProps({
    osList: Array,
  });
  const emit = defineEmits(['send']);

  const chosenIndex = ref(0);
  const listIsOpened = ref(false);
  const displayText = ref('Выберите тип системы');

  function chooseOS(index) {
    chosenIndex.value = index;
    displayText.value = props.osList[index].name;
    sendChosenSystem(index);
    closeList();
  }
  function closeList() {
    listIsOpened.value = false;
  }
  function toggleList() {
    listIsOpened.value = !listIsOpened.value;
  }
  function sendChosenSystem(index) {
    const chosenSystemName = props.osList[index].name;
    console.log('sendChosenSystem name', chosenSystemName);
    emit('send', chosenSystemName);
  }
</script>

<template>
  <div class="dropdown-list">
    <div class="dropdown-list__display">
      <p class="dropdown-list__display-text" @click="toggleList">{{ displayText }}</p>
      <button class="dropdown-list__display-button"
        type="button"
        :class="{ 'dropdown-list__display-button_pressed': listIsOpened }"
        @click="toggleList">
        <img :src="buttonIcon" alt="" class="dropdown-list__display-button-icon">
      </button>
    </div>
    <ul class="dropdown-list__list" :class="{ 'dropdown-list__list_opened': listIsOpened }">
      <li class="dropdown-list__list-item"
          v-for="(os, osIndex) in osList"
          :key="os.id"
          @click="chooseOS(osIndex)">
        {{ os.name }}
      </li>
    </ul>
  </div>
</template>

<style lang="scss">
@use "@/assets/style/index.scss" as *;

.dropdown-list {
  width: 100%;
  position: relative;
  &__display {
    position: relative;
    width: 100%;
    z-index: 1;
    height: 48px;
    background-color: rgba(255, 255, 255, 0.85);
    border: 1px solid #fff;
    border-radius: 3px;
    overflow: hidden;
    @include flex(row, flex-start, center);
    @media (min-width: 1100px) {
      cursor: pointer;
    }
    &-text {
      flex-grow: 1;
      font-family: "Lato", sans-serif;
      font-weight: 400;
      font-size: 16px;
      line-height: 110%;
      color: #272733;
      height: 100%;
      @include flex(row, flex-start, center);
      padding-left: 12px;
    }

    &-button {
      display: block;
      width: 46px;
      height: 46px;
      background-color: rgba(255, 255, 255, 0);
      flex-grow: 0;
      @include flex(row, center, center);
      &-icon {
        transition: all 0.2s ease;
      }
      &_pressed &-icon {
        transform: rotate(-180deg);
      }
    }
  }

  &__list {
    display: none;
    position: absolute;
    z-index: 2;
    top: 47px;
    left: 0;
    width: 100%;
    border-bottom-left-radius: 3px;
    border-bottom-right-radius: 3px;
    overflow: hidden;
    background: rgba(255, 255, 255, 1);
    box-shadow: 4px 4px 8px 0px rgba(34, 60, 80, 0.2);
    &_opened {
      display: block;
    }
    &-item {
      font-family: "Lato", sans-serif;
      font-weight: 400;
      font-size: 16px;
      line-height: 110%;
      color: #272733;
      padding: 8px;
      padding-left: 12px;
      background: rgba(255, 255, 255, 1);
    }
  }
}
</style>
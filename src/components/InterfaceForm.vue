<script setup>
  import {reactive, ref} from "vue";
  import DropdownList from "@/components/UI/DropdownList.vue";
  import FormInput from "@/components/UI/FormInput.vue";
  import FormRange from "@/components/UI/FormRange.vue";
  import AdditionalButton from "@/components/UI/AdditionalButton.vue";
  import MainButton from "@/components/UI/MainButton.vue";

  const osList = reactive([
    {
      id: 1,
      name: 'Windows',
    },
    {
      id: 2,
      name: 'MacOS',
    },
    {
      id: 3,
      name: 'Linux',
    },
  ]);
  let chosenSystemName = '';

  const email = ref('');
  const name = ref('');

  const min = 0;
  const max = 100;
  const step = 1;
  const rangeValue = ref(50);

  function getChosenSystemName(incomingName) {
    chosenSystemName = incomingName;
  }
  function attachFile() {
    console.log('attachFile');
  }
  function sendData() {
    const dataToSend = {
      system: chosenSystemName,
      email: email.value,
      name: name.value,
      range: rangeValue.value,
    };

    console.log('dataToSend', dataToSend);
  }
</script>

<template>
  <div class="interface-form">
    <form class="interface-form__form" action="" method="">
      <!-- выпадающий список -->
      <DropdownList class="interface-form__dropdown-list" :osList="osList" @send="getChosenSystemName"></DropdownList>
      <!-- поля ввода -->
      <FormInput class="interface-form__mail"
        v-model="email"
        placeholder="Ваш e-mail">
      </FormInput>
      <!-- поля ввода -->
      <FormInput class="interface-form__name"
        v-model="name"
        placeholder="Ваше имя">
      </FormInput>
      <!-- ползунок -->
      <FormRange class="interface-form__range"
        text="Sed ut perspiciatis, unde omnis iste natus"
        :min="min"
        :max="max"
        :step="step"
        v-model="rangeValue"
      ></FormRange>
      <!-- кнопка  -->
      <AdditionalButton class="interface-form__file" @click="attachFile">
        <p class="interface-form__file-btn-text">
          <svg xmlns="http://www.w3.org/2000/svg" width="18" height="21" viewBox="0 0 18 21" fill="none">
            <path d="M16.8125 4.60899L13.3304 1.12685C12.9174 0.713902 12.0915 0.36792 11.5 0.36792H1.50002C0.9085 0.36792 0.428589 0.847831 0.428589 1.43935V19.2965C0.428589 19.888 0.9085 20.3679 1.50002 20.3679H16.5C17.0915 20.3679 17.5714 19.888 17.5714 19.2965V6.43935C17.5714 5.84783 17.2255 5.02194 16.8125 4.60899ZM11.8572 1.88578C12.0469 1.95274 12.2366 2.05319 12.3148 2.13131L15.8081 5.62462C15.8862 5.70274 15.9866 5.89247 16.0536 6.08221H11.8572V1.88578ZM16.1429 18.9394H1.85716V1.79649H10.4286V6.43935C10.4286 7.03087 10.9085 7.51078 11.5 7.51078H16.1429V18.9394ZM4.7143 9.29649V10.0108C4.7143 10.2117 4.87055 10.3679 5.07145 10.3679H12.9286C13.1295 10.3679 13.2857 10.2117 13.2857 10.0108V9.29649C13.2857 9.0956 13.1295 8.93935 12.9286 8.93935H5.07145C4.87055 8.93935 4.7143 9.0956 4.7143 9.29649ZM12.9286 11.7965H5.07145C4.87055 11.7965 4.7143 11.9527 4.7143 12.1536V12.8679C4.7143 13.0688 4.87055 13.2251 5.07145 13.2251H12.9286C13.1295 13.2251 13.2857 13.0688 13.2857 12.8679V12.1536C13.2857 11.9527 13.1295 11.7965 12.9286 11.7965ZM12.9286 14.6536H5.07145C4.87055 14.6536 4.7143 14.8099 4.7143 15.0108V15.7251C4.7143 15.926 4.87055 16.0822 5.07145 16.0822H12.9286C13.1295 16.0822 13.2857 15.926 13.2857 15.7251V15.0108C13.2857 14.8099 13.1295 14.6536 12.9286 14.6536Z" fill="#272733"/>
          </svg>
          <span>Прикрепить файл</span>
        </p>
      </AdditionalButton>
      <!-- кнопка  -->
      <MainButton class="interface-form__send" @click="sendData">Отправить</MainButton>
    </form>
  </div>
</template>

<style lang="scss">
@use "@/assets/style/index.scss" as *;

.interface-form {
  width: 100%;
  @include flex(row, center, center);
  &__form {
    width: 100%;
    max-width: 1600px;
    padding: 0 16px;
    display: grid;
    grid-template-columns: 1fr;
    gap: 16px;
    @media (min-width: 640px) {
      padding: 0 20px;
      grid-template-columns: 1fr 1fr;
      grid-template-rows: repeat(5, 48px);
      gap: 20px;
    }
    @media (min-width: 820px) {
      grid-template-columns: repeat(4, 1fr);
    }
    @media (min-width: 1100px) {
      grid-template-columns: repeat(3, 1fr);
      grid-template-rows: repeat(3, 48px);
      padding: 0 45px;
    }
    @media (min-width: 1600px) {
      padding: 0;
    }
  }
  &__dropdown-list {
    @media (min-width: 640px) {
      grid-column: 1 / -1;
      grid-row-start: 1;
      grid-row-end: 2;
    }
    @media (min-width: 1100px) {
      grid-column: 1 / 2;
      grid-row: 1 / 2;
    }
  }
  &__mail {
    @media (min-width: 640px) {
      grid-column-start: 1;
      grid-column-end: 2;
      grid-row-start: 2;
      grid-row-end: 3;
    }
    @media (min-width: 820px) {
      grid-column-start: 1;
      grid-column-end: 3;
    }
    @media (min-width: 1100px) {
      grid-column: 2 / 3;
      grid-row: 1 / 2;
    }
  }
  &__name {
    @media (min-width: 640px) {
      grid-column-start: 2;
      grid-column-end: 3;
      grid-row-start: 2;
      grid-row-end: 3;
    }
    @media (min-width: 820px) {
      grid-column-start: 3;
      grid-column-end: 5;
    }
    @media (min-width: 1100px) {
      grid-column: 3 / 4;
      grid-row: 1 / 2;
    }
  }
  &__range {
    @media (min-width: 640px) {
      grid-column: 1 / -1;
      grid-row-start: 3;
      grid-row-end: 4;
    }
    @media (min-width: 1100px) {
      grid-column: 1 / 3;
      grid-row: 2 / 3;
    }
  }
  &__file {
    @media (min-width: 640px) {
      grid-column: 1 / -1;
      grid-row-start: 4;
      grid-row-end: 5;
    }
    @media (min-width: 820px) {
      grid-column-start: 2;
      grid-column-end: 4;
    }
    @media (min-width: 1100px) {
      grid-column: 3 / 4;
      grid-row: 2 / 3;
    }
  }
  &__file-btn-text {
    @include flex(row, center, center);
    gap: 16px;
  }
  &__send {
    @media (min-width: 640px) {
      grid-column: 1 / -1;
      grid-row-start: 5;
      grid-row-end: 6;
    }
    @media (min-width: 820px) {
      grid-column-start: 2;
      grid-column-end: 4;
    }
    @media (min-width: 1100px) {
      grid-column: 2 / 3;
      grid-row: 3 / 4;
    }
  }
}
</style>
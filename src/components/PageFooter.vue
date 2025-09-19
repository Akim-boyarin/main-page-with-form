<script setup>
  import {reactive} from "vue";

  // payment pics
  import paymentQiwiWalletPic from '@/assets/img/footer__payment__qiwiwallet.svg';
  import paymentYandexMoneyPic from '@/assets/img/footer__payment__yandexmoney.svg';
  import paymentWebMoneyPic from '@/assets/img/footer__payment__webmoney.svg';

  // contacts pics
  import contactMailPic from '@/assets/img/footer__contacts__mail.svg';
  import contactVkPic from '@/assets/img/footer__contacts__vk.svg';


  const payments = reactive([
    { id: 1, logo: paymentQiwiWalletPic, name: 'QIWI wallet' },
    { id: 2, logo: paymentYandexMoneyPic, name: 'Yandex Money' },
    { id: 3, logo: paymentWebMoneyPic, name: 'Web Money' },
  ]);

  function usePayment(payment) {
    console.log(payment.name);
  }

  const contacts = reactive([
    { id: 1, logo: contactMailPic, name: 'info@ipsum228.com', url: 'mailto:info@ipsum228.com' },
    { id: 2, logo: contactVkPic, name: 'Мы вконтакте', url: '/' },
  ]);

</script>

<template>
  <footer class="footer">
    <div class="footer__container">
      <p class="footer__copyright">© 2018 «LoremIpsum.net» Все права защищены.</p>
      <ul class="footer__payments">
        <li class="footer__payment" v-for="payment in payments" :key="payment.id">
          <img class="footer__payment-logo" :src="payment.logo" />
          <span class="footer__payment-text">{{ payment.name }}</span>
        </li>
      </ul>
      <ul class="footer__contacts">
        <li class="footer__contact-link-wrapper" v-for="contact in contacts" :key="contact.id">
          <img class="footer__contact-logo" :src="contact.logo" />
          <a :href="contact.url" class="footer__contact-link">{{ contact.name }}</a>
        </li>
      </ul>
    </div>
  </footer>
</template>

<style lang="scss">
  @use "@/assets/style/index.scss" as *;

  .footer {
    background-color: #3c4050;
    padding: 25px 16px;
    @include flex(row, center, center);
    @media (min-width: 640px) {
      padding: 30px 20px;
    }
    @media (min-width: 1100px) {
      padding: 32px 45px;
    }
    &__container {
      width: 100%;
      max-width: 1600px;
      @media (min-width: 750px) {
        @include flex(row, space-between, flex-start);
        gap: 60px;
      }
      @media (min-width: 1300px) {
        align-items: center;
        height: 20px;
      }
    }

    &__copyright {
      font-family: "Lato", sans-serif;
      font-size: 14px;
      font-weight: 400;
      line-height: 100%;
      color: #fff;
      margin-bottom: 18px;
      @media (min-width: 750px) {
        flex: 1 0 25%;
        width: 300px;
        margin-bottom: 0;
      }
      @media (min-width: 1300px) {
        width: auto;
        border-right: 1px solid #C3C3C3;
        height: 100%;
      }
    }

    &__payments {
      margin-bottom: 14px;
      @media (min-width: 750px) {
        flex: 1 0 25%;
        margin-bottom: 0;
      }
      @media (min-width: 1300px) {
        @include flex(row, center, center);
        gap: 20px;
        flex: 2 0 25%;
      }
      @media (min-width: 1400px) {
        gap: 45px;
      }
    }

    &__payment {
      @include flex(row, flex-start, center);
      gap: 10px;
    }


    &__payment-text {
      font-family: "Lato", sans-serif;
      color: #C3C3C3;
      font-size: 14px;
      font-weight: 400;
      line-height: 100%;
    }

    &__contacts {
      @media (min-width: 750px) {
        flex: 1 0 25%;
        margin-bottom: 0;
      }
      @media (min-width: 1300px) {
        @include flex(row, flex-end, center);
        gap: 20px;
        border-left: 1px solid #C3C3C3;
      }
      @media (min-width: 1400px) {
        gap: 45px;
      }
    }

    &__contact-link-wrapper {
      @include flex(row, flex-start, center);
      gap: 10px;
    }
    &__contact-link {
      font-family: "Lato", sans-serif;
      color: #C3C3C3;
      font-size: 14px;
      font-weight: 400;
      line-height: 100%;
    }
  }
</style>
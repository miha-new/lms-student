<template>
  <footer class="base-footer">
    <div class="container">
      <div class="base-footer__section">
        <div class="h3 base-footer__h3">
          Есть вопросы? Пишите на<br>
          <a href="#" class="base-footer__mailto">sara.cruz@example.com</a>
        </div>
        <a href="#" class="base-footer__insta">
          <icon-insta/>
        </a>
      </div>
    </div>
  </footer>
</template>

<script>
import IconInsta from '@/assets/IconInsta.svg';

export default {
  components: {
    IconInsta,
  },
};
</script>

<style lang="scss">
  .base-footer {
    position: relative;
    &__section {
      position: relative;
      padding: 28px;
      margin-bottom: 28px;
      text-align: center;
      background-color: $grey;
      border-radius: 20px;
    }
    &__h3 {
      margin-top: 0;
      margin-bottom: 17px;
    }
    &__mailto {
      font-weight: 600;
      font-size: 16px;
      line-height: 24px;
      text-align: center;
      letter-spacing: 0.0038em;
      text-decoration: none;
      color: $orange;
      &:hover {
        text-decoration: underline;
      }
    }
    &__insta {
      display: block;
      width: 21px;
      height: 21px;
      margin: 0 auto;
      path {
        transition: fill $time ease-in-out;
      }
      &:hover path {
        fill: $orange;
      }
    }
  }
</style>

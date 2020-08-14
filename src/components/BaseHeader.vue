<template>
  <header class="base-header">
    <div class="container base-header__container">
      <router-link to="/" class="base-header__logo">
        <div class="base-header__logo-icon">Р</div>
        <div class="base-header__logo-text">Школа Иллюстрации</div>
      </router-link>
      <router-link to="/" class="btn btn-outline-orange ml-auto">
        Войти
      </router-link>
    </div>
  </header>
</template>

<script>
export default {

};
</script>

<style lang="scss">
  .base-header {
    position: relative;
    padding-top: 30px;
    padding-bottom: 20px;
    @media (min-width: 768px) {
      padding-bottom: 30px;
    }
    &__container {
      display: flex;
    }
    &__logo {
      display: flex;
      text-decoration: none;
    }
    &__logo:hover &__logo-icon {
      background-color: rgba($orange, 0.8);
      box-shadow: 0px 8px 16px rgba($orange, 0.3);
    }
    &__logo:hover &__logo-text {
      color: rgba($text, 0.8);
    }
    &__logo-icon {
      display: flex;
      align-items: center;
      justify-content: center;
      width: 40px;
      height: 40px;
      color: $lightGrey;
      background: $orange;
      border-radius: 10px;
      transition: background-color $time ease-in-out, box-shadow $time ease-in-out;
    }
    &__logo-text {
      display: none;
      @media (min-width: 768px) {
        display: flex;
        align-items: center;
        padding: 0px 20px;
        font-weight: 600;
        font-size: 14px;
        line-height: 110%;
        text-align: center;
        color: $text;
        transition: color $time ease-in-out;
      }
    }
  }
</style>

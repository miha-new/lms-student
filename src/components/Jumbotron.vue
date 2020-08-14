<template>
  <div class="jumbotron">
    <div class="jumbotron__col-left">
      <img :src="jumbotron.img" alt="" class="jumbotron__img">
    </div>
    <div class="jumbotron__col-right">
      <h1 class="h1 jumbotron__title">{{jumbotron.title}}</h1>
      <p class="text-3 jumbotron__text">{{jumbotron.text}}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    jumbotron: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style lang="scss">
  .jumbotron {
    position: relative;
    margin-left: -20px;
    margin-right: -20px;
    background: $white;
    box-shadow: 0px 2px 10px rgba(144, 144, 210, 0.14);
    @media (min-width: 768px) {
      display: flex;
      margin-left: 0;
      margin-right: 0;
      border-radius: 20px;
    }
    &__col-left,
    &__col-right {
      @media (min-width: 768px) {
        flex: 0 0 50%;
        max-width: 50%;
        padding-top: 20px;
        padding-bottom: 20px;
      }
    }
    &__col-right {
      padding-left: 20px;
      padding-right: 20px;
      overflow: hidden;
      @media (min-width: 768px) {
        order: 0;
      }
      @media (min-width: 992px) {
        padding-left: 70px;
        padding-right: 30px;
      }
    }
    &__col-left {
      @media (min-width: 768px) {
        padding-left: 0;
        padding-right: 20px;
        order: 1;
      }
    }
    &__title {
      margin-top: 20px;
      margin-bottom: 15px;
      @media (min-width: 1200px) {
        margin-top: 50px;
        margin-bottom: 30px;
      }
    }
    &__text {
      margin-top: 0;
      margin-bottom: 25px;
    }
    &__img {
      display: block;
      width: 100%;
      height: auto;
      border: 1px solid $grey;
      box-sizing: border-box;
      @media (min-width: 768px) {
        border-radius: 10px;
      }
    }
  }
</style>

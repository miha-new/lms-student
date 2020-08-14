<template>
  <div class="jumbotron">
    <div class="jumbotron__col-left">
      <h1 class="h1 jumbotron__title">{{jumbotron.title}}</h1>
      <p class="text-3 jumbotron__text">{{jumbotron.text}}</p>
    </div>
    <div class="jumbotron__col-right">
      <img :src="jumbotron.img" alt="" class="jumbotron__img">
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
    display: flex;
    background: $white;
    box-shadow: 0px 2px 10px rgba(144, 144, 210, 0.14);
    border-radius: 20px;
    &__col-left,
    &__col-right {
      flex: 0 0 50%;
      max-width: 50%;
      padding-top: 20px;
      padding-bottom: 20px;
    }
    &__col-left {
      padding-left: 70px;
      padding-right: 30px;
    }
    &__col-right {
      padding-left: 0;
      padding-right: 20px;
    }
    &__title {
      margin-top: 50px;
      margin-bottom: 30px;
    }
    &__text {
      margin-top: 0;
      margin-bottom: 0;
    }
    &__img {
      max-width: 100%;
      height: auto;
      border: 1px solid $grey;
      box-sizing: border-box;
      border-radius: 10px;
    }
  }
</style>

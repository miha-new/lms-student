<template>
  <div class="card">
    <div class="card__head" :style="{backgroundImage: `url(${card.img})`}"></div>
    <div class="card__body">
      <div class="h2 card__title">{{card.title}}</div>
      <div class="card__ul">
        <div v-for="(item, index) in card.list" :key="index" class="text-1 card__li">{{item}}</div>
      </div>
      <div class="h2 card__price">{{card.price}}</div>
    </div>
    <div class="card__foot">
      <button class="btn btn-orange card__btn">Купить</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    card: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style lang="scss">
  .card {
    position: relative;
    background: $white;
    border-radius: 20px;
    overflow: hidden;
    filter: drop-shadow(0px 2px 10px rgba(144, 144, 210, 0.14));
    &__head {
      height: 135px;
      background-color: $grey;
      background-repeat: no-repeat;
      background-position: 50%;
      background-size: cover;
      overflow: hidden;
    }
    &__body {
      padding: 20px 16px;
      height: 207px;
    }
    &__foot {
      padding: 0 16px 20px;
    }
    &__title {
      margin-top: 0;
      margin-bottom: 10px;
      height: 40px;
      overflow: hidden;
    }
    &__ul {
      margin-top: 0;
      margin-bottom: 10px;
      height: 87px;
    }
    &__li {
      color: $dolphin;
    }
    &__price {
      margin-top: 0;
      margin-bottom: 0;
    }
    &__btn {
      width: 100%;
    }
  }
</style>

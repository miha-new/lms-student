<template>
  <div class="home">
    <div class="container">
      <jumbotron :jumbotron="jumbotron" class="home__jumbotron"/>
      <div class="home__panel">
        <div class="home__panel-left">
          <input-search v-model="search"/>
        </div>
      </div>
      <div class="home__row">
        <div v-for="card in cards" :key="card.id" class="home__col">
          <card :card="card" class="home__card"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Jumbotron from '@/components/Jumbotron.vue';
import Card from '@/components/Card.vue';
import InputSearch from '@/components/InputSearch.vue';

export default {
  name: 'Home',
  components: {
    Jumbotron,
    Card,
    InputSearch,
  },
  data: () => ({
    jumbotron: {
      title: 'Школа иллюстрации',
      text: 'Такой расширенной программы, которая охватывает все нюансы fashion иллюстрации нет ни у одной школы. Мы проверяли ;)',
      img: 'img/jumbotron.jpg',
    },
    search: '',
    cards: [
      {
        id: 1,
        title: 'Основы иллюстрации. Вводная лекция',
        list: [
          'Старт 1 июля 2020 года',
          'Обучение на практике',
          '40+ пошаговых уроков',
          'Удобный онлайн формат',
        ],
        price: '2 000 ₽',
      },
      {
        id: 2,
        title: 'Fashion иллюстрация',
        list: [
          'Старт 1 июля 2020 года',
          'Обучение на практике',
          '40+ пошаговых уроков',
          'Удобный онлайн формат',
        ],
        price: '2 000 ₽',
      },
      {
        id: 3,
        title: 'Работа с цветом',
        list: [
          'Старт 1 июля 2020 года',
          'Обучение на практике',
          '40+ пошаговых уроков',
          'Удобный онлайн формат',
        ],
        price: '2 000 ₽',
      },
      {
        id: 4,
        title: 'Fashion иллюстрация',
        list: [
          'Старт 1 июля 2020 года',
          'Обучение на практике',
          '40+ пошаговых уроков',
          'Удобный онлайн формат',
        ],
        price: '2 000 ₽',
      },
    ],
  }),
};
</script>

<style lang="scss">
.home {
  position: relative;
  &__jumbotron {
    margin-bottom: 10px;
  }
  &__panel {
    position: relative;
    display: flex;
    padding-top: 30px;
    padding-bottom: 30px;
    margin-left: -10px;
    margin-right: -10px;
  }
  &__panel-left,
  &__panel-right {
    flex: 0 0 50%;
    max-width: 50%;
    padding-left: 10px;
    padding-right: 10px;
  }
  &__row {
    display: flex;
    flex-wrap: wrap;
    margin-left: -10px;
    margin-right: -10px;
  }
  &__col {
    flex: 0 0 25%;
    padding-left: 10px;
    padding-right: 10px;
    max-width: 25%;
  }
  &__card {
    margin-bottom: 20px;
  }
}
</style>

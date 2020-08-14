<template>
  <div class="home">
    <div class="container">
      <jumbotron :jumbotron="jumbotron" class="home__jumbotron"/>
      <div class="home__panel">
        <div class="home__panel-left">
          <input-search v-model="search"/>
        </div>
        <div class="home__panel-right">
          <single-select
            v-model="showFilterCards.selected"
            :options="showFilterCards.options"
            label="label"
          >
            <template v-slot:control>
              <button
                class="btn btn-select"
              >
                <span class="btn-select__hint">Показать:</span>
                <span class="btn-select__text">{{showFilterCards.selected.label}}</span>
                <icon-down class="btn-select__icon"/>
                <icon-settings class="btn-select__settings"/>
              </button>
            </template>
          </single-select>
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
import IconDown from '@/assets/IconDown.svg';
import IconSettings from '@/assets/IconSettings.svg';
import Jumbotron from '../components/Jumbotron.vue';
import Card from '../components/Card.vue';
import InputSearch from '../components/InputSearch.vue';
import SingleSelect from '../components/SingleSelect.vue';

export default {
  name: 'Home',
  components: {
    IconDown,
    IconSettings,
    Jumbotron,
    Card,
    InputSearch,
    SingleSelect,
  },
  data: () => ({
    jumbotron: {
      title: 'Школа иллюстрации',
      text: 'Такой расширенной программы, которая охватывает все нюансы fashion иллюстрации нет ни у одной школы. Мы проверяли ;)',
      img: 'img/jumbotron.jpg',
    },
    search: '',
    showFilterCards: {
      selected: null,
      options: [
        {
          label: 'Все',
          name: 'all',
        },
        {
          label: 'Новые',
          name: 'new',
        },
        {
          label: 'Популярные',
          name: 'popular',
        },
      ],
    },
    cards: [
      {
        id: 1,
        img: '/img/card-1.jpg',
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
        img: '/img/card-2.jpg',
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
        img: '/img/card-3.jpg',
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
        img: '/img/card-4.jpg',
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
  created() {
    const [filterFirstOption] = this.showFilterCards.options;
    this.showFilterCards.selected = filterFirstOption;
  },
};
</script>

<style lang="scss">
.home {
  position: relative;
  &__jumbotron {
    @media (min-width: 768px) {
      margin-bottom: 10px;
    }
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
    display: flex;
    padding-left: 10px;
    padding-right: 10px;
    @media (min-width: 768px) {
      display: flex;
      flex: 0 0 50%;
      max-width: 50%;
    }
  }
  &__panel-left {
    flex-grow: 1;
  }
  &__panel-right {
    flex: 0 0 auto;
    margin-left: auto;
    .btn-select {
      &__settings {
        display: none;
      }
      @media (max-width: 767px) {
        padding: 12px 13px;
        &__icon,
        &__text,
        &__hint {
          display: none;
        }
        &__settings {
          display: block;
        }
      }
    }
  }
  &__row {
    @media (min-width: 768px) {
      display: flex;
      flex-wrap: wrap;
      margin-left: -10px;
      margin-right: -10px;
    }
  }
  &__col {
    @media (min-width: 768px) {
      flex: 0 0 50%;
      padding-left: 10px;
      padding-right: 10px;
      max-width: 50%;
    }
    @media (min-width: 992px) {
      flex: 0 0 33.333%;
      max-width: 33.333%;
    }
    @media (min-width: 1200px) {
      flex: 0 0 25%;
      max-width: 25%;
    }
  }
  &__card {
    margin-bottom: 20px;
  }
}
</style>

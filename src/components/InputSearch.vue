<template>
  <div class="input-search">
    <icon-search class="input-search__icon"/>
    <input
      type="text"
      name="search"
      :value="value"
      class="input-search__control"
      autocomplete="off"
      placeholder="Найти курс..."
      @input="handleInput"
      @keydown.enter="handleSubmit"
    >
    <button
      v-if="value"
      class="btn input-search__remove"
      @click="handleRemoveValue"
    >
      <icon-remove/>
    </button>
  </div>
</template>

<script>
import IconSearch from '@/assets/IconSearch.svg';
import IconRemove from '@/assets/IconRemove.svg';

export default {
  components: {
    IconSearch,
    IconRemove,
  },
  props: {
    value: String,
  },
  methods: {
    handleInput(e) {
      this.$emit('input', e.target.value);
    },
    handleSubmit(e) {
      this.$emit('submit', e.target.value);
    },
    handleRemoveValue() {
      this.$emit('input', '');
    },
  },
};
</script>

<style lang="scss">
  .input-search {
    position: relative;
    width: 100%;
    &__icon {
      position: absolute;
      top: calc(50% - 6px);
      left: 18px;
      pointer-events: none;
    }
    &__control {
      display: block;
      width: 100%;
      height: 40px;
      padding: 9px 45px;
      font-weight: 400;
      font-size: 12px;
      line-height: 20px;
      letter-spacing: 0.0038em;
      color: $text;
      background-color: $grey;
      background-clip: padding-box;
      border: 1px solid $grey;
      border-radius: 10px;
      &:focus {
        outline: 0;
      }
      &::placeholder {
        color: $darkGrey;
      }
    }
    &__remove {
      position: absolute;
      top: calc(50% - 8px);
      right: 12px;
      path {
        transition: fill $time ease-in-out;
      }
      &:hover path {
        fill: $red;
      }
    }
  }
</style>

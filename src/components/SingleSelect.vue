<template>
  <div
    class="single-select"
    :class="{open}"
    @click="handleToggle"
  >
    <button
      v-if="!$slots.control"
      class="btn btn-select"
    >
      {{optionLabel(value)}}
      <icon-down class="btn-select__icon"/>
    </button>
    <slot
      v-else
      name="control"
    />
    <div
      v-if="open"
      class="single-select__content"
    >
      <div class="single-select__wrap">
        <div
          v-for="(option, index) in options"
          :key="index"
          class="single-select__item"
          :class="{active: isActive(option)}"
          @click="handleInput(option)"
        >
          {{optionLabel(option)}}
        </div>
      </div>
    </div>
    <slot name="content"/>
  </div>
</template>

<script>
import IconDown from '@/assets/IconDown.svg';

export default {
  components: {
    IconDown,
  },
  props: {
    value: {
      required: true,
    },
    options: {
      type: Array,
      required: true,
    },
    label: {
      type: String,
    },
    allowEmpty: {
      type: Boolean,
      default: false,
    },
  },
  data: () => ({
    open: false,
  }),
  methods: {
    isActive(value) {
      return Object.is(this.value, value);
    },
    optionLabel(value) {
      return this.label ? value.label : value;
    },
    handleInput(value) {
      let selected;
      if (this.allowEmpty) {
        selected = !this.isActive(value) ? value : null;
      } else {
        selected = value;
      }
      this.$emit('input', selected);
    },
    handleToggle() {
      if (this.open) {
        this.handleClose();
      } else {
        this.handleOpen();
      }
    },
    handleOpen() {
      this.open = true;
      window.addEventListener('click', this.watchClickOutside);
    },
    handleClose() {
      this.open = false;
      window.removeEventListener('click', this.watchClickOutside);
    },
    watchClickOutside(e) {
      if (!this.$el.contains(e.target)) {
        this.handleClose();
      } else {
        e.stopPropagation();
      }
    },
  },
};
</script>

<style lang="scss">
  .single-select {
    position: relative;
    &.open {
      .btn-select {
        &__icon {
          transition: color $time ease-in-out;
          transform: rotateX(180deg);
          path {
            stroke: $text;
          }
        }
      }
    }
    &__content {
      position: absolute;
      top: calc(100% + 18px);
      right: 0;
      background-color: $white;
      box-shadow: 0px 10px 24px rgba(144, 144, 210, 0.2);
      border-radius: 10px;
      z-index: 500;
      @media (min-width: 768px) {
        &::before {
          position: absolute;
          top: -8px;
          left: calc(50% - 8px);
          width: 16px;
          height: 16px;
          background-color: $white;
          box-shadow: 0px 10px 24px rgba(144, 144, 210, 0.2);
          transform: rotate(45deg);
          z-index: 0;
          content: '';
        }
        &::after {
          position: absolute;
          top: 0;
          left: 0;
          bottom: 0;
          right: 0;
          background-color: $white;
          border-radius: 10px;
          z-index: 0;
          content: '';
        }
      }
    }
    &__wrap {
      position: relative;
      padding-top: 12px;
      padding-bottom: 12px;
      max-height: 200px;
      z-index: 1;
      overflow: auto;
    }
    &__item {
      position: relative;
      font-size: 12px;
      line-height: 20px;
      letter-spacing: 0.0038em;
      padding: 6px 23px;
      user-select: none;
      cursor: pointer;
      transition: background-color $time ease-in-out, color $time ease-in-out;
      &:hover {
        background-color: $grey;
      }
      &.active {
        background-color: $orange;
        color: $lightGrey;
      }
    }
  }
</style>

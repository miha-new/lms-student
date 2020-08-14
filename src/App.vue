<template>
  <div id="app">
    <base-header/>
    <main class="base-main">
      <router-view/>
    </main>
    <base-footer/>
  </div>
</template>

<script>
import BaseHeader from './components/BaseHeader.vue';
import BaseFooter from './components/BaseFooter.vue';

export default {
  components: {
    BaseHeader,
    BaseFooter,
  },
};
</script>

<style lang="scss" src="./styles/common.scss" />

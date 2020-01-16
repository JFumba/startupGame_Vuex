<template>
  <div id="game">
    <Overview />
  </div>
</template>

<script>
import Overview from './components/Overview';

export default {
  name: 'app',
  components: {
    Overview
  },
  methods: {
    coding () {
      // Do Something
    },
    loop () {
      // Game Loop
      requestAnimationFrame(this.loop);
    }
  },
  created () {
    this.loop();
    window.addEventListener('keypress', this.coding);
  },
  destroyed () {
    window.removeEventListener('keypress', this.coding);
  }
}
</script>

<style lang="scss">
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  body {
    font-family:Arial, Helvetica, sans-serif;
  }
</style>

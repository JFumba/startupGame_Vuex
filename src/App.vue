<template>
  <div id="game">
    <Overview />
    <Upgrades />
  </div>
</template>

<script>
import Overview from './components/Overview';
import Upgrades from './components/Upgrades';

export default {
  name: 'app',
  components: {
    Overview,
    Upgrades
  },
  methods: {
    coding () {
      this.$store.commit('incrementBytes', this.$store.state.bpk);
    },
    loop () {
      // Game Loop
      this.levelManager();
      requestAnimationFrame(this.loop);
    },
    levelManager () {
      if (this.$store.getters.bytesUntilLevelUp <= 0) {
        this.$store.commit('levelUp');
      }      
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

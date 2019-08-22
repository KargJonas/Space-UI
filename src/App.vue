<template>
  <div id="app">
    <Terminal
      title="BOOTED MICROTECH CRD-8 COMBAT ASSAULT DECK :: LINK"
      main="LOL"
      footer="FOOTER"
      height="100px"
      width="500px"
      x="100px"
      y="50px"
      speed="100"
    />
  </div>
</template>

<script>
import Terminal from './components/Terminal.vue'
import "./global.scss";

export default {
  name: 'app',
  components: { Terminal },
}
</script>

<style lang="scss">
html {
  background-color: #0c0c0c;
}

body {
  margin: 0;
}
</style>

<template>
  <div id="app">
    <Terminal
      title="BOOTED MICROTECH CRD-8 COMBAT ASSAULT DECK :: LINK"
      v-bind:main="terminalText"
      footer="FOOTER"
      height="100px"
      width="500px"
      x="100px"
      y="50px"
      speed="1"
    />

    <Terminal title="||" width="100px" x="200px" y="500px" />
  </div>
</template>

<script>
import Terminal from './components/Terminal.vue'
import "./global.scss";

const terminalText = `SHIELDS ........ 100%
CHECKS ......... 100%
SHIELDS ........ 100%
CHECKS ......... 100%
SHIELDS ........ 100%
CHECKS ......... 100%
SHIELDS ........ 100%
CHECKS ......... 100%
SHIELDS ........ 100%
CHECKS ......... 100%
`;

export default {
  name: 'app',
  components: { Terminal },
  data: () => ({ terminalText })
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

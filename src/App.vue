<template>
  <div id="app">
    <Terminal
      title="BOOTING MICROTECH CRD-8 COMBAT ASSAULT DECK"
      v-bind:main="terminalText"
      v-bind:footer="41"
      height="100px"
      width="506px"
      x="100px"
      y="50px"
      v-bind:speed="3"
    />

    <Terminal
      title="OUTSTREAM"
      v-bind:main="terminalText2"
      v-bind:footer="23"
      height="100px"
      width="300px"
      x="350px"
      y="320px"
      speed="3"
    />

    <Terminal title="||" width="100px" x="200px" y="300px" />
  </div>
</template>

<script>
import Terminal from './components/Terminal.vue'
import "./global.scss";

const terminalText = `BOOTING

SHIELDS ..................... 73%\tDONE\t0x06
WEAPONS .....................  3%\tDONE\t0xa4
LIFE SUPPORT SYSTEMS ........ 89%\tDONE\t0x1f
REACTOR CORE ................ 81%\tDONE\t0x13`;

let terminalText2 = "";

for (let i = 0; i < 1000; i++) {
  terminalText2 += Math.random() * 10 | 0;
}

export default {
  name: 'app',
  components: { Terminal },
  data: () => ({ terminalText, terminalText2 })
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
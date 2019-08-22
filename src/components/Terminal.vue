<template>
  <div v-bind:style="{left: x, top: y, width}" class="terminal">
    <div v-if="title" class="topbar">
      <div class="topbar-text">{{title}}</div>
      <img src="../assets/warning.svg" />
    </div>
    <div v-if="main" class="main" v-bind:style="{ height }">
      <pre class="scroller" ref="scroller">{{mainText}}</pre>
    </div>
    <div v-if="footer" class="footer">{{footer}}</div>
  </div>
</template>

<script>
export default {
  name: "terminal",
  props: ["width", "height", "x", "y", "title", "footer", "main", "speed"],
  data: () => ({ mainText: "" }),
  methods: {
    async type(index = 0) {
      this.mainText += this.main[index];
      this.scroller.scrollTop = this.scroller.scrollHeight;

      index++;
      if (index >= this.main.length) return;

      setTimeout(
        () => requestAnimationFrame(() => this.type(index)),
        this.speed || 0
      );
    }
  },
  mounted() {
    if (!this.main) return;
    this.scroller = this.$refs.scroller;
    this.scroller.addEventListener("wheel", e => e.preventDefault());
    this.scroller.addEventListener("touchmove", e => e.preventDefault());
    if (this.main) this.type();
  }
};
</script>

<style scoped lang="scss">
.terminal {
  position: absolute;
  border: solid;
  opacity: 0.3;
  color: #ee386f;
  border-color: #ee386f;
  border-width: 3px;
  width: 300px;
  word-wrap: break-word;

  .main,
  .topbar,
  .footer {
    padding: 10px 20px;
  }

  .topbar-text {
    width: calc(100% - 30px);
  }

  .topbar {
    border-bottom: solid;
    position: relative;

    img {
      height: 30px;
      position: absolute;
      right: 16px;
      top: 50%;
      transform: translateY(-50%);
    }
  }

  .main {
    overflow: hidden;

    .scroller {
      overflow-y: scroll;
      padding-right: 40px;
      max-height: 100%;
      margin: 0 -100px 0 0;
      padding-right: 80px;
    }
  }

  .footer {
    border-top: solid;
  }
}
</style>
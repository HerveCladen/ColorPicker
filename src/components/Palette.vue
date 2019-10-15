<template>
  <div class="container">
      <div>
        <input class="input" id="red" type="number" v-model="red" min="0" max="255">
        <label for="red">Rouge</label>
      </div>
      <div>
        <input class="input" id="green" type="number" v-model="green" min="0" max="255">
        <label for="green">Vert</label>
      </div>
      <div>
        <input class="input" id="blue" type="number" v-model="blue" min="0" max="255">
        <label for="blue">Bleu</label>
      </div>
      <div class="canvas" v-bind:style="{ background: activeColor }"></div>
    </div>
</template>

<script>
export default {
  name: 'palette',
  data() {
    return {
      red: 0,
      green: 0,
      blue: 0,
    };
  },
  computed: {
    activeColor() {
      return `rgb(${this.red}, ${this.green}, ${this.blue})`;
    },
  },
  watch: {
    red(val) {
      if (val > 255) this.red = 255;
      if (val < 0) this.red = 0;
    },
    green(val) {
      if (val > 255) this.green = 255;
      if (val < 0) this.green = 0;
    },
    blue(val) {
      if (val > 255) this.blue = 255;
      if (val < 0) this.blue = 0;
    },
  },
};
</script>

<style scoped lang="scss">
  .container {
    padding: 5px;

    div {
      padding: 5px;
      display: flex;

      input {
        width: 200px;
      }

      label {
        margin: 5px 10px;
      }
    }

    .canvas {
      width: 100px;
      height: 100px;
      margin: 5px;
    }
  }
</style>

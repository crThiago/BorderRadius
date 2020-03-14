<template>
  <div id="app">
    <div>
      <h1>Border Radius</h1>
      <div class="grid">
        <input type="number" class="border-input grid8" min="0" max="100" v-model="leftTopVertical" placeholder="Left Top">
        <input type="number" class="border-input grid1" min="0" max="100" v-model="leftTopHorizontal" placeholder="Top Left">
        <input type="number" class="border-input grid2" min="0" max="100" v-model="rightTopHorizontal" placeholder="Top Right">
        <input type="number" class="border-input grid3" min="0" max="100" v-model="rightTopVertical" placeholder="Right Top">
        <div class="box grid9" ref="refbox" :style="borderRadius"></div>
        <input type="number" class="border-input grid7" min="0" max="100" v-model="leftBottomVertical" placeholder="Left Bottom">
        <input type="number" class="border-input grid6" min="0" max="100" v-model="leftBottomHorizontal" placeholder="Bottom Left">
        <input type="number" class="border-input grid5" min="0" max="100" v-model="rightBottomHorizontal" placeholder="Bottom Right">
        <input type="number" class="border-input grid4" min="0" max="100" v-model="rightBottomVertical" placeholder="Right Bottom">
      </div>
      <div class="result">
        <input class="result__input" ref="input" type="text" readonly :value="borderRadius">
        <button class="result__button" :class="copied ? 'result__button--copied' : ''" @click="copyInput" >{{ !copied ? 'Copy' : 'Copied' }}</button>
      </div>
    </div>
    <div class="link">
      <a  href="https://vuejs.org/">
        <img src="./assets/logo.png" alt="vue js logo">
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      leftTopHorizontal: 100,
      rightTopHorizontal: 9,
      rightBottomHorizontal: 64,
      leftBottomHorizontal: 43,

      leftTopVertical: 64,
      rightTopVertical: 9,
      rightBottomVertical: 100,
      leftBottomVertical: 43,

      copied: false
    }
  },
  methods: {
    copyInput() {
      const input = this.$refs.input
      input.select()
      document.execCommand("copy")
      
      this.copied = true

      setTimeout(() => {
        this.copied = false
      }, 2000)
    }
  },
  computed: {
    borderRadius() {
      return `border-radius: ${this.leftTopHorizontal}% ${this.rightTopHorizontal}% ${this.rightBottomHorizontal}% ${this.leftBottomHorizontal}% / ${this.leftTopVertical}% ${this.rightTopVertical}% ${this.rightBottomVertical}% ${this.leftBottomVertical}%`
    }
  }
}
</script>

<style>
body {
  background: #35495E;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
}

h1 {
  color: white;
}

.grid {
  display: grid;
  grid-template-columns: repeat(5, 100px);
  grid-template-rows: repeat(5, 100px);
  grid-column-gap: 0px;
  grid-row-gap: 0px;
  justify-content: center;
}

.border-input {
  border: none;
  border-bottom: 1px solid #41B883;
  background: transparent;
  outline: none;
  color: white;
  align-self: center;
  justify-self: center;
  text-align: center;
  line-height: 20px;
  font-weight: bold;
}

.grid1 { grid-area: 1 / 2 / 2 / 3; }
.grid2 { grid-area: 1 / 4 / 2 / 5; }
.grid3 { grid-area: 2 / 5 / 3 / 6; }
.grid4 { grid-area: 4 / 5 / 5 / 6; }
.grid5 { grid-area: 5 / 4 / 6 / 5; }
.grid6 { grid-area: 5 / 2 / 6 / 3; }
.grid7 { grid-area: 4 / 1 / 5 / 2; }
.grid8 { grid-area: 2 / 1 / 3 / 2; }
.grid9 { grid-area: 2 / 2 / 5 / 5; }

.box {
  width: 300px;
  height: 300px;
  background: #41B883;
}

.result {
  display: flex;
  justify-content: center;

  margin-top: 30px;
}
.result__input {
  width: 450px;
  text-align: center;
  background: transparent;
  color: white;
  font-size: 1em;
  padding: 15px;
  border: 3px solid #41B883;
  border-right: none;
  border-radius: 10px 0 0 10px;
  font-weight: bold;
}

.result__button {
  border: 3px solid #41B883;
  color: white;
  background: transparent;
  padding: 14px 30px;
  font-size: 1.5em;
  font-weight: 800;
  border-radius: 0 10px 10px 0;
  cursor: pointer;
  outline: none;
  transition: 300ms;
}

.result__button:hover, .result__button--copied {
  background: #41B883;
}

.link {
  background: white;
  position: fixed;
  bottom: 10px;
  right: 10px;
  border-radius: 10px;
}

.link img {
  padding: 10px;
  height: 30px;
}
</style>

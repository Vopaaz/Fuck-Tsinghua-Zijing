<template>
  <div id="app">
    <div v-if="atQrPage">
      <img class="bg-img" src="./assets/main-redmi.png" @click="toOutgoingPage" />
      <span class="time-str main" id="time-str">{{ timeStr }}</span>
    </div>
    <div v-else-if="atSidedoor">
      <img class="bg-img" src="./assets/outgoing-sidedoor-redmi.png" @click="toQrPage" />
      <span class="time-str outgoing" id="time-str" @click="switchDoor">{{ timeStr }}</span>
    </div>
    <div v-else>
      <img class="bg-img" src="./assets/outgoing-redmi.png" @click="toQrPage" />
      <span class="time-str outgoing" id="time-str" @click="switchDoor">{{ timeStr }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data: function() {
    return {
      timeStr: undefined,
      atQrPage: true,
      atSidedoor: false
    };
  },
  mounted() {
    setInterval(() => {
      const date = new Date();
      this.timeStr = `${date.getFullYear()}-${date.getMonth() +
        1}-${date.getDate()} ${
        date.getHours().toString().length === 1
          ? "0" + date.getHours().toString()
          : date.getHours().toString()
      }:${
        date.getMinutes().toString().length === 1
          ? "0" + date.getMinutes().toString()
          : date.getMinutes().toString()
      }:${
        date.getSeconds().toString().length === 1
          ? "0" + date.getSeconds().toString()
          : date.getSeconds().toString()
      }`;
    }, 1000);
  },
  methods: {
    toOutgoingPage() {
      this.atQrPage = false;
    },
    toQrPage() {
      this.atQrPage = true;
    },
    switchDoor() {
      this.atSidedoor = !this.atSidedoor;
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0px;
}

.bg-img {
  min-height: 100%;

  /* Set up proportionate scaling */
  width: 100%;
  height: auto;

  /* Set up positioning */
  position: fixed;
  top: 0;
  left: 0;
}

.time-str {
  position: absolute;
  /* iPhone X or Xiaomi */
  left: 25%;
  /* left: 26.75%; */
  color: grey;
  font-size: 22px;
}

.main {
  /* For iPhone X */
  top: 49.8%;

  /* For iPhone 11 */
  /* top: 49.5%; */

  /* For xiaomi */
  /* top: 57.5%; */
}

.outgoing {
  /* For iphone, confirmed */
  top: 49.2%;

  /* For iPhone 11 */
  /* top: 48.9%; */

  /* For xiaomi, confirmed */
  /* top: 56.7%; */
}
</style>

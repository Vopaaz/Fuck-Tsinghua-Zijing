<template>
  <div id="app">
    <div v-if="atQrPage">
      <img id="bg-img" src="./assets/qrcode-cropped.png" @click="toOutgoingPage" />
      <span id="time-str">{{ timeStr }}</span>
    </div>
    <div v-else>
      <img id="bg-img-outgoing" src="./assets/outgoing-cropped.png" @click="toQrPage" />
      <span id="time-str">{{ timeStr }}</span>
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
      atQrPage: true
    };
  },
  mounted() {
    setInterval(() => {
      const date = new Date();
      this.timeStr = `${date.getFullYear()}-${date.getMonth() +
        1}-${date.getDate()} ${date.getHours()}:${
        date.getMinutes().toString().length === 1
          ? "0" + date.getMinutes().toString()
          : date.getMinutes().toString()
      }:${
        date.getSeconds().toString().length === 1
          ? "0" + date.getSeconds().toString()
          : date.getSeconds().toString()
      }`;
    });
  },
  methods: {
    toOutgoingPage() {
      this.atQrPage = false;
    },
    toQrPage() {
      this.atQrPage = true;
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

#bg-img {
  min-height: 100%;

  /* Set up proportionate scaling */
  width: 100%;
  height: auto;

  /* Set up positioning */
  position: fixed;
  top: 0;
  left: 0;
}

#bg-img-outgoing {
  min-height: 100%;

  /* Set up proportionate scaling */
  width: 100%;
  height: auto;

  /* Set up positioning */
  position: fixed;
  top: 0;
  left: 0;
}

#time-str {
  position: absolute;
  left: 23%;
  /* For iphone, confirmed */
  /* top: 54%; */
  /* For xiaomi, confirmed */
  top: 65%;
  color: grey;
  font-size: 24px;
}
</style>

<template>
  <div id="app">
    <img id="bg-img" src="./assets/qrcode.png" />
    <span id="time-str">{{ timeStr }}</span>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data: function() {
    return {
      timeStr: undefined
    };
  },
  mounted() {
    setInterval(() => {
      const date = new Date();
      this.timeStr = `${date.getFullYear()}-${date.getMonth()}-${date.getDate()} ${date.getHours()}:${date.getMinutes()}:${date.getSeconds()}`;
    });
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
  margin-top: 0px;
}

#bg-img {
  margin: 0px;
  width: 100%;
}

#time-str{
  position: absolute;
  left: 28%;
  top: 53%;
  color: grey;
  font-size: 21px;
}
</style>

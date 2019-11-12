<template>
  <div id="app">
    <!--     <div @click="playSound">So CLICK</div>
    <div @mouseover="playSound">So 1</div>
    <p v-show="active">SONA</p> -->

    <button @click="playSound">So CLICK</button>

    <div>
      <input type="range" v-model="position" />
    </div>

    <p>{{ this.position }}</p>
  </div>
</template>

<script src="https://cdnjs.cloudflare.com/ajax/libs/howler/2.1.2/howler.spatial.min.js"></script>

<script>
// eslint-disable-next-line no-unused-vars
import { Howl, Howler } from "howler";

export default {
  name: "app",
  components: {},
  data: function() {
    return {
      position: 0
    };
  },
  methods: {
    playSound() {
      var sound = new Howl({
        src: ["http://www.largesound.com/ashborytour/sound/brobob.mp3"],
        autoplay: true
      });

      var id1 = sound.play();

      sound.rate(10, id1);
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

input {
}
</style>

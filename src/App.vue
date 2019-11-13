<template>
  <div id="app">
    <!--     <div @click="playSound">So CLICK</div>
    <div @mouseover="playSound">So 1</div>
    <p v-show="active">SONA</p> -->

    <button @click="playSound">COMENÇA</button>
    <button @click="soundLeft">LEFT</button>
    <button @click="soundRight">RIGHT</button>

    <div>
      <input
        @input="changeSound"
        type="range"
        v-model="position"
        min="-100"
        max="100"
      />
    </div>

    <p>{{ this.position / 100 }}</p>
  </div>
</template>

<script>
// eslint-disable-next-line no-unused-vars
// import { Howl, Howler } from "howler";

import Wad from "web-audio-daw";

export default {
  name: "app",
  components: {},
  data: function() {
    return {
      position: 0,
      bell: ""
    };
  },
  methods: {
    /* playSound() {
      var sound = new Howl({
        src: ["http://www.largesound.com/ashborytour/sound/brobob.mp3"],
        autoplay: true
      });

      // sound.rate(2);

      sound.volume(1, soundID);
      sound.pos(-500, 0, 1000, soundID);

      var soundID = sound.play();
    }
  } */
    playSound() {
      this.bell = new Wad({
        source:
          "https://files.freemusicarchive.org/storage-freemusicarchive-org/music/Oddio_Overplay/Christian_Bjoerklund/Skapmat/Christian_Bjoerklund_-_01_-_Hallon.mp3",
        panning: 1
      });
      this.bell.play();

      this.bell.stop();
    },
    soundLeft() {
      this.bell.setPanning(-1, 2);
    },
    soundRight() {
      this.bell.setPanning(1, 2);
    },
    changeSound() {
      this.bell.setPanning(this.position / 100, 2);
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
  width: 100%;
}
</style>

<template>
  <div class="buttons" v-bind:style="{background: bgColor}">
      <div class="button" id="record" v-on:click="onRecord">
          <p class="button-text">Record</p>
      </div>
      <div class="button" id="stop" v-on:click="onStop">
          <p class="button-text">Stop</p>
      </div>
      <div class="button" id="play" v-on:click="onPlay">
          <p class="button-text">Play</p>
      </div>
      <div class="button" id="clear" v-on:click="onClear">
          <p class="button-text">Clear</p>
      </div>
  </div>
</template>

<script>
export default {
    data() {
        return {
            bgColor: "blanchedalmond"
        }
    },
    methods: {
        onRecord(){
            console.log("🔴 Now recording... 🔴");
            this.bgColor = "#B11B1B"
        },
        onStop(){
            console.log("🛑 Recording has stopped 🛑");
            this.bgColor = "blanchedalmond"
        },
        onPlay(){
            console.log("🎧 Now playing.. 🎧");
            this.bgColor = "lightgreen"
        },
        onClear(){
            console.log("💣 Recording deleted 💣");
            this.bgColor = "blanchedalmond"
        }
    }
}
</script>

<style>

</style>
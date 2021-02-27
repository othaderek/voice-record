<template>
  <div class="buttons">
      <div class="button" id="record" v-on:click="startRecord">
          <p class="button-text">Record</p>
      </div>
      <div class="button" id="stop" v-on:click="stopRecord">
          <p class="button-text">Stop</p>
      </div>
      <div class="button" id="play" v-on:click="playRecording">
          <p class="button-text">Play</p>
      </div>
      <div class="button" id="clear" v-on:click="clearRecording">
          <p class="button-text">Clear</p>
      </div>
  </div>
</template>

<script>
export default {
    methods: {
        startRecord(){
            console.log("🔴 Now recording... 🔴");
        },
        stopRecord(){
            console.log("🛑 Recording has stopped 🛑");
        },
        playRecording(){
            console.log("🎧 Now playing.. 🎧");
        },
        clearRecording(){
            console.log("💣 Recording deleted 💣");
        }
    }
}
</script>

<style>

</style>
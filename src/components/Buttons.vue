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
            bgColor: "blanchedalmond",
            audioEle: null,
            audio: null,
            audioChunks: [],
            mediaRecorder: null
        }
    },
    mounted(){
        this.audioEle = this.$parent.$children[0].$el
        this.isPaused();
    },
    methods: {
        onRecord(){
            // Do recording shit
            this.createRecording();
            console.log("🔴 Now recording... 🔴");
            this.bgColor = "#B11B1B"
        },
        onStop(){
            try {
                this.mediaRecorder.stop();
                console.log("🛑 Recording has stopped 🛑");
                this.bgColor = "blanchedalmond";
            } catch (error) {
                console.error('Not recording, you can only press stop while recording.', error);
                alert('🎤 Not recording, you can only press stop while recording. 🎤')
            }
        },
        onPlay(){
            try {
                this.audio.play();
                console.log("🎧 Now playing.. 🎧");
                console.log(this.audio.paused);
                this.bgColor = "lightgreen"
            } catch (error) {
                console.error("🌻 No audio to play. Try recording some! 🌻", error);
                alert("🌻 No audio to play. Try recording some! 🌻");
            }
        },
        onClear(){
            if (this.audio){
                this.audio = null;
                this.audioChunks = [];
                console.log("💣 Recording deleted 💣");
                alert("💣 Recording deleted 💣");
                this.bgColor = "blanchedalmond";
                return;
            }
            console.log('🎤Try recording some audio first!🎤');
            alert('🎤Try recording some audio first!🎤');
        },
        createRecording(){
            navigator.mediaDevices.getUserMedia({audio: true})
                .then(stream =>{
                    this.mediaRecorder = new MediaRecorder(stream);
                    this.mediaRecorder.start();

                    this.mediaRecorder.addEventListener("dataavailable", event => {
                        this.audioChunks.push(event.data);
                    });
                    this.mediaRecorder.addEventListener('stop', this.createAudio);
                })
        },
        createAudio(){
            console.log(this.audioChunks);
            this.audioBlob = new Blob(this.audioChunks);
            let audioUrl = URL.createObjectURL(this.audioBlob);
            this.audio = new Audio(audioUrl);
        },
        isPaused(){
            setInterval(() => {
                if (this.bgColor === "lightgreen"){
                    this.audio.paused ? this.bgColor = "blanchedalmond" : null
                }
            }, 100)
        }
    }
}
</script>

<style>

</style>
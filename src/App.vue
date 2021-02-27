<template>
  <div id="app">
    <Buttons/>
  </div>
</template>

<script>
import Buttons from './components/Buttons.vue'

export default {
  name: 'App',
  components: {
    Buttons
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

body {
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  background: blanchedalmond;
}

#app {
  width: 100%;
  height: 100%;
}

.buttons {
  width: 100%;
  height:100%;
  display: flex;
  justify-content: center;
  position: relative;
  flex-direction: column;
  align-items: center;
}

.button {
  width: 30%;
  height: 15%;
  background: white;
  margin: 1em;
  vertical-align: middle;
  display: flex;
  justify-content: center;
  vertical-align: middle;
}

.button:hover {
  background: rgb(197, 197, 197);
}

.button-text {
  transform: translate(39%, 39%);
  margin-right: 35px;
  font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}


/* Center buttons */
/* Button styling */

</style>

<template>
  <div id="app">
    <GameHeader :colour='colour' />
    <Buttons :colour='colour' :colours='colours' :showmessage='showMessage' />
    <ColourBox v-for="(colour, i) in colours" :colour="colour" :index="i" :key="key(colour)" :colours='colours' :winner="winner" />
  </div>
</template>

<script>
  import Buttons from './components/Buttons.vue';
  import ColourBox from './components/ColourBox.vue';
  import GameHeader from './components/GameHeader.vue';

  export default {
    name: 'App',
    components: {
      Buttons,
      ColourBox,
      GameHeader
    },
    data() {
      return {
        colour: {
          r: 0,
          g: 0,
          b: 0
        },
        colours: [],
        showMessage: "Pick a Colour!"
      }
    },
    methods: {
      winner(colourBox, actual) {
        if(JSON.stringify(colourBox) === JSON.stringify(this.colour)) {
          this.showMessage = "You Picked Right!";
          for (let index = 0; index < this.colours.length; index++) {
            Object.assign(this.colours[index], colourBox);
          }
          setTimeout(() => {
            this.showMessage = "Click on New Colours to play again!"
          }, 2000);
        } else {
          this.showMessage = "Try Again!";
          this.colours[actual].r = 23;
          this.colours[actual].g = 23;
          this.colours[actual].b = 23;
        }
      },
      key(colour){
        return '' + Math.random() * 100000 + colour.r + colour.g + colour.b;
      }
    }
  }
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  body {
    background: #232323;
    margin: 0;
    font-family: "Montserrat", "Avenir";
  }
</style>

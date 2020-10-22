<template>
  <section id="navigator">
    <button id="reset" @click="restart">New colours</button>
    <span id="message"> {{ showmessage }} </span>
    <button id="easy" v-bind:class="{ selected: !difficult }" @click="easy()">easy</button>
    <button id="hard" v-bind:class="{ selected: difficult }" @click="hard()">hard</button>
  </section>
</template>

<script>
  export default  {
    name: 'buttonsheader',
    props: ['colour', 'colours', 'showmessage'],
    created() {
      this.restart();
    },
    data () {
      return {
        difficult: true,
        cant: 6
      }
    },
    methods: {
      easy() {
        if (this.difficult) {
          this.difficult = false;
          this.cant = 3;
          this.restart();
        }
      },
      hard() {
        if (!this.difficult) {
          this.difficult = true;
          this.cant = 6;
          this.restart();
        }
      },
      restart() {
        this.colours.splice(0, this.colours.length, ...this.createNewColours());
        let pickedColour = this.colours[this.pickColour()];
        this.colour.r = pickedColour.r;
        this.colour.g = pickedColour.g;
        this.colour.b = pickedColour.b;
      },
      createNewColours() {
        let arr = [];
        for (var i = 0; i < this.cant; i++) {
          arr.push(this.createRandomStringColour());
        }
        return arr;
      },
      createRandomStringColour() {
        return {
          r: this.randomInt(),
          g: this.randomInt(), 
          b: this.randomInt()
        };
      }, 
      randomInt() {
        return Math.floor(Math.random() * 256);
      },
      pickColour() {
        return Math.floor(Math.random() * this.cant);
      }
    }
  }
</script>

<style scoped lang="css">
  #navigator {
    background: #ffffff;
    height: 30px;
    text-align: center;
    margin: 0;
    margin-top: -30px;
  }
  #message {
    color: steelblue;
    display: inline-block;
    width: 20%;
  }
  .selected {
    background-color: steelblue;
    color: white;
  }
  button {
    border: none;
    background-color: white;
    font-family: "Montserrat", "Avenir";
    text-transform: uppercase;
    height: 100%;
    font-weight: 700;
    letter-spacing: 1px;
    color: steelblue;
    transition: all 0.3s;
    outline: none;
  }

  button:hover {
    color: white;
    background-color: steelblue;
  }
</style>

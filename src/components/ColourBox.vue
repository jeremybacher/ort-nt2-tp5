<template>
  <section id="container">
    <div class="square" :style="{'background-color': backgroundColor}" @click="show"></div>
  </section>
</template>

<script>
  export default  {
    name: 'colourbox',
    props: ['colour', 'index', 'winner'],
    data () {
      return {
        backgroundColor: `rgb(${this.colour.r},${this.colour.g},${this.colour.b})`
      }
    },
    methods: {
      show(){
        this.winner(this.colour, this.index);
      }
    }
  }
</script>

<style scoped lang="css">
  #container {
    margin: 20px auto;
    max-width: 600px;
  }
  .square {
    width: 30%;
    background: blue;
    padding-bottom: 30%;
    float: left;
    margin: 1.66%;
    border-radius: 10%;
    transition: background 0.8s;
    -webkit-transition: background 0.8s;
    -moz-transition: background 0.8s;
  }
</style>

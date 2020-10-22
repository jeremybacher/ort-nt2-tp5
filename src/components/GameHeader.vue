<template>
  <section id="header">
    <h1>The Great <br>
      <span id="colorDisplay">rgb({{colour.r}}, {{colour.g}}, {{colour.b}})</span>
      <br>
      Guessing Game
    </h1>
  </section>
</template>

<script>
  export default  {
    name: 'gameheader',
    props: ['colour']
  }
</script>

<style scoped lang="css">
  h1 {
    font-weight: normal;
    line-height: 1.1;
    padding: 20px 0;
  }
</style>

<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h3>Anatomy of a Vue file</h3>
    <ul>
      <li>Templates</li>
      <li>Script</li>
      <li>Style</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  /* display: inline-block; */
  margin: 10px 10px;
}
a {
  color: #42b983;
}
</style>

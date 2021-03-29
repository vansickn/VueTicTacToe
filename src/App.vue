<template>
<h1>Tic-Tac-Toe with a Twist</h1>
<p>Can pick up your last piece and move it!</p>
<div class="boardDiv">
  <Board/>
</div>


</template>

<script>
import Board from './components/Board.vue'

export default {
  name: 'App',
  components: {
    Board,
  },
  
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
h1{
  border-bottom: 2px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
.boardDiv{
  margin: auto;
}
</style>

<template>
<h1>Tic-Tac-Toe</h1>



<div class="boardDiv">
  <Board/>
</div>

<div class="legend">
  <div class="glegend">
    <h3>Open Cell</h3>
  </div>
  <div class="rlegend">
    <h3>Can't Place</h3>
  </div>
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
.glegend{
  padding: 10px;
  border: 2px solid green;
  border-radius: 10px;
  height: fit-content;
  width: fit-content;
  margin: auto;
  display: inline-block;
}
.rlegend{
  padding: 10px;
  border: 2px solid red;
  border-radius: 10px;
  height: fit-content;
  width: fit-content;
  margin: auto;
  margin-left: 10px;
  display: inline-block;
}
.legend{
  padding: 15px;
  border: 2px solid #2c3e50;
  border-radius: 10px;
  height: fit-content;
  width: fit-content;
  margin: auto;
  display: inline-block;
}
</style>

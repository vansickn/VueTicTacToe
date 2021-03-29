<template>
<div class="board">
    <div v-for="(n,i) in 3" :key="n.id">
        <div v-for="(n,j) in 3" :key="n.id">
            <Cell :value="boardData[j][i]" @mark="markPosition(i,j)" :owned="isOwned(i,j)" :openCell="isOpenCell(i,j)">
            </Cell>
        </div>
    </div>
</div>
<h3 v-if="turn">X's Turn</h3>
<h3 v-else>O's Turn</h3>
</template>



<script>
import Cell from './Cell'

// turn true for player 1, false for player 2
export default {
    data() {
        return {
            boardData: 
            [["","",""],
            ["","",""],
            ["","",""]],
            turn: true,

             
        }
    },
    components: {
        Cell,
    },
    methods: {
        markPosition(i,j) { 
            if (this.turn && this.boardData[j][i] === ''){
                this.boardData[j][i] = "X"
                this.turn = !this.turn
            }else if(!this.turn && this.boardData[j][i] === ''){
                this.boardData[j][i] = "O"
                this.turn = !this.turn
            }
            
        },
        isOwned(i,j){
            if(this.boardData[j][i] === "X" && this.turn === true){return true}
            if(this.boardData[j][i] === "O" && this.turn === false){return true}
            else{
                return false
            } 
        },
        isOpenCell(i,j){
            if(this.boardData[j][i] === ''){return true}
            else{return false}
        }
    }
}
</script>

<style>
.board {
    padding-top: 2%;
    display: inline-flex;
    flex-wrap: wrap;
}

</style>
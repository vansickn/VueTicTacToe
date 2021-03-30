<template>


<div class="board">
    <div v-for="(n,i) in 3" :key="n.id">
        <div v-for="(n,j) in 3" :key="n.id">
            <Cell :value="boardData[j][i]" @mark="markPosition(i,j)" :cantPlace="cantPlace(i,j)" :openCell="isOpenCell(i,j)">
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
            piecesPlaced: 0,
            c: 2,
            ld: "",
            rd: "",
            RB: false

             
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
                this.piecesPlaced += 1
            }else if(!this.turn && this.boardData[j][i] === ''){
                this.boardData[j][i] = "O"
                this.turn = !this.turn
                this.piecesPlaced += 1
            }
            this.winner()
            
        },
        cantPlace(i,j){
            if(this.boardData[j][i] !== ''){return true}
            else{
                return false
            } 
        },
        isOpenCell(i,j){
            if(this.boardData[j][i] === ''){return true}
            else{return false}
        },
        winner() {
            console.log(!this.turn)
            console.log(this.c)
            if(this.piecesPlaced >= 5){
                // Horizontal
                for (let i = 0; i < this.boardData.length; i++) {
                    if (this.boardData[i][0] + this.boardData[i][1] + this.boardData[i][2] === this.winningString()){
                        this.$emit('win', !this.turn)
                        this.reset()
                    } 
                }
                // Vertical
                for (let j = 0; j <this.boardData.length; j++) {
                    if (this.boardData[0][j] + this.boardData[1][j] + this.boardData[2][j] === this.winningString()){
                        this.$emit('win', !this.turn)
                        this.reset()
                    }
                }
                // Diagonal n = 3
                
                this.boardData.forEach(i => {
                    this.rd += i[this.c]
                    this.ld += i[i.length-(this.c)-1]
                    this.c -= 1
                });
                if(this.ld === this.winningString() | this.rd === this.winningString()){
                    this.$emit('win', !this.turn)
                    this.reset()
                }
                else{
                    this.c = 2
                    this.ld = ""
                    this.rd = ""
                }
            }
            
        },
        winningString() {
            // opposite of turn, because of click that changes turn back
            if(this.turn){return "OOO"}
            else{return "XXX"}
        },
        reset() {
            this.boardData = 
            [["","",""],
            ["","",""],
            ["","",""]],
            this.turn = true,
            this.piecesPlaced = 0,
            this.c = 2,
            this.ld = "",
            this.rd = ""
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
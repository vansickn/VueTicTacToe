<template>
  <div class="cell" @click="markCell" @mouseover="highlightCell" @mouseleave="deHighlightCell" :class="{highlighted,cantPlace,openCell}">
      <!-- Hacky fix to make the mouseover on the p to highlight as well but I don't know how to do it better! -->
      <p @mouseover="highlightCell"> {{value}} </p> 
  </div>
</template>

<script>
export default {
    data() {
        return {
            highlighted: false
        }
    },
    props: {
        value: String,
        cantPlace: Boolean,
        openCell: Boolean,
    },
    methods: {
        markCell() {
            this.$emit('mark')
        },
        highlightCell() {
            this.highlighted = true
        },
        deHighlightCell(){
            this.highlighted = false
        }
    }
}
</script>

<style>
.cell{
    width: 100px;
    height: 100px;
    background: grey;
    border: 3px solid black;
    font-size: 50px;
    display: flex;
    align-items: center;
    justify-content: center;
}
.highlighted{
    border-color: yellow;
}
.highlighted.cantPlace{
    border-color: red;
}
.highlighted.openCell{
    border-color: rgb(5, 206, 5);
}
p {
    user-select: none;
}
</style>
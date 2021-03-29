<template>
  <div class="cell" @click="markCell" @mouseover="highlightCell" @mouseleave="highlightCell" :class="{highlighted,owned}">
      <p> {{value}} </p>
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
        owned: Boolean,
    },
    methods: {
        markCell() {
            this.$emit('mark')
        },
        highlightCell() {
            this.highlighted = !this.highlighted
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
.highlighted.owned{
    border-color: red;
}
</style>
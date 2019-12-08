<template>
    <div class="square" @click="$emit('changeValue', this.props.id)">salam</div>    
</template>

<script>
export default {
    el: "square",
    name: "Square",
    props: {
        value: Number,
        xTurn: Boolean
    },
    data(){
        return {
            // value: this.props.xTurn == true ? "X" : "O",
        }
    }
}
</script>

<style>
    .square {
        width: 100px;
        height: 100px;
        border: 1px solid black;
    }
</style>
<template>
    <div v-on:click="$emit('clickedSquare', currentId)" class="square">
        <slot></slot>
    </div>
</template>

<script>
export default {
    name: "Square",
    props: {
        id: String,
    },
    data() {
        return {
            currentId : this.id,
        }
    }
}
</script>

<style>
    .square {
        border: 1px solid black;
        width: 100px;
        height: 100px;
        font-size: 45px;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .square:hover{
        background-color: grey;
    }
</style>
<template>
    <div id="Board">
        <Square v-on:changeValue="handleClick($event)" id="0" />
    </div>
</template>

<script>
import { Square } from './Square'
export default {
    el: "Board",
    components: {
        Square
    },
    handleClick(){
        window.alert("salam")
    }
}
</script>

<style>

</style>
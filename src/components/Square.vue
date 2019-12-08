<template>
	<div class="square" @click="emitOnClick">{{this.$props.value}}</div>    
</template>

<script>
export default {
	name: "Square",
	methods: {
		emitOnClick(){
			this.$emit("clicked", this.$props.id)
		}
	},
	props: {
		id: String,
		value: String
	},
}
</script>

<style>
	.square {
		width: 100px;
		height: 100px;
		border: 1px solid black;
		font-size: 45px;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.square:hover{
		background-color: grey;
	}
</style>
<template>
	<div id="Board">
		<div class="row">
			<Square :value="board[0]" v-on:clicked="handleClick($event)" id="0" />
			<Square :value="board[1]" v-on:clicked="handleClick($event)" id="1" />
			<Square :value="board[2]" v-on:clicked="handleClick($event)" id="2" />
		</div>
		<div class="row">
			<Square :value="board[3]" v-on:clicked="handleClick($event)" id="3" />
			<Square :value="board[4]" v-on:clicked="handleClick($event)" id="4" />
			<Square :value="board[5]" v-on:clicked="handleClick($event)" id="5" />
		</div>
		<div class="row">
			<Square :value="board[6]" v-on:clicked="handleClick($event)" id="6" />
			<Square :value="board[7]" v-on:clicked="handleClick($event)" id="7" />
			<Square :value="board[8]" v-on:clicked="handleClick($event)" id="8" />
		</div>
	</div>
</template>

<script>
import Square from './Square';
import { checkWinner } from '../assets/services/services'

export default {
	name: "Board",
	components: {
		Square
	},
	methods: {
		handleClick(id){
			let xTurn = this.$data.xTurn
			if (this.$data.board[+id]) return ;
			this.$set(this.board , id, this.$data.board[+id] = xTurn ? "X" : "O");
			this.$data.xTurn = !xTurn;
			let winner = checkWinner(this.$data.board);
			if(winner){
				(winner == "D" ? window.alert("Draw") : window.alert(`${winner} has won the game`) )
				this.$data.board = Array(9).fill(null)
			}
	}
	},
	data(){
		return {
			board: Array(9).fill(null),
			xTurn: false,
		}
	},
}
</script>

<style>
	#board {
		display: flex;
		flex-direction: column;
	}

	.row {
		display: flex;
		flex-direction: row;
	}
</style>
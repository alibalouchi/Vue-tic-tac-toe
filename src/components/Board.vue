<template>
  <div class="container">
    current Turn is : {{this.xTurn ? "X" : "O"}}
    <div class="row">
      <Square :class="this.winner[0] ? 'winner' : ''" v-on:clickedSquare="handleClick(0)" id="0">{{this.board[0]}}</Square>
      <Square :class="this.winner[1] ? 'winner' : ''" v-on:clickedSquare="handleClick(1)" id="1">{{this.board[1]}}</Square>
      <Square :class="this.winner[2] ? 'winner' : ''" v-on:clickedSquare="handleClick(2)" id="2">{{this.board[2]}}</Square>
    </div>
    <div class="row">
      <Square :class="this.winner[3] ? 'winner' : ''" v-on:clickedSquare="handleClick(3)" id="3" >{{this.board[3]}}</Square>
      <Square :class="this.winner[4] ? 'winner' : ''" v-on:clickedSquare="handleClick(4)" id="4" >{{this.board[4]}}</Square>
      <Square :class="this.winner[5] ? 'winner' : ''" v-on:clickedSquare="handleClick(5)" id="5" >{{this.board[5]}}</Square>
    </div>
    <div class="row">
      <Square :class="this.winner[6] ? 'winner' : ''" v-on:clickedSquare="handleClick(6)" id="6" >{{this.board[6]}}</Square>
      <Square :class="this.winner[7] ? 'winner' : ''" v-on:clickedSquare="handleClick(7)" id="7" >{{this.board[7]}}</Square>
      <Square :class="this.winner[8] ? 'winner' : ''" v-on:clickedSquare="handleClick(8)" id="8" >{{this.board[8]}}</Square>
    </div>
    <button v-on:click="handleReset()">Reset The Game</button>
  </div>
</template>

<script>
import {checkWinner}  from '../services/services';
import  Square  from './Square';
export default {
  name: 'Board',
  components: {Square},
  data(){
    return {
      board: Array(9).fill(null),
      xTurn: false,
      winner: Array(9).fill(false)
    }
  },
  props: {
    dimension: String
  },
  methods: {
    handleReset(){
      this.board = Array(9).fill(null)
      this.winner = Array(9).fill(false)
    },
    handleClick(id){
      if (this.board[id]) return;
      if (this.winner.find(item => item == true)) return;
      this.board[id] = this.xTurn ? "X" : "O"
      this.xTurn = !this.xTurn
      let indexes = checkWinner(this.board)
      indexes.map(item => this.winner[item] = true)
    }
  }
}
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.row {
  display: flex;
  flex-direction: row;
}

button {
  margin: 50px;
}

.winner {
  background-color: green;
}
</style>

<template>
  <div class="container">
    <h1>Malesef Bilemediniz!</h1>
    <button @click="newGame">Yeni Oyun</button>
  </div>
</template>

<script>
 import GameCards from "./GameCards";
export default {
  components:{appGameCards:GameCards},
  methods: {
    newGame() {
     this.$emit("activeComponentEvent","app-game-cards")
    }
  }
}
</script>
<style scoped>
.container {
  position: absolute;
  top: 0px;
  left: 0px;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: darkred;
}

.container h1 {
  text-align: center;
  font-size: 333%;
  color: white;
}


.container button {
  cursor:pointer;
  width:200px;
  height: 60px;
  color:darkred;
  bockground-color:#fff;
  border:  1px solid brown;
  font-size: 15px;
  outline: none;
  border-radius: 5px;
  transition: all .5s;
}

.container button:hover {
 background-color: lightgreen;
 color: #fff; 
  transition: all .5s;
}
</style>
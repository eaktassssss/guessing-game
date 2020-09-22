<template>
  <div class="container">
    <h1>Tebrikler Bildiniz :)</h1>
    <button @click="newGame">Yeni Oyun</button>
  </div>
</template>

<script>
import GameCards from "./GameCards";
export default {
 
  methods: {
    newGame() {
      this.$emit("activeComponentEvent", "app-game-cards")
    }
  },
  components: {appGameCards: GameCards},
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
}

.container h1 {
  text-align: center;
  font-size: 333%;
  color: darkgreen;
  opacity: .5;
}


.container button {
  cursor: pointer;
  width: 200px;
  height: 60px;
  color: darkred;
  bockground-color: #fff;
  border: 1px solid darkgreen;
  font-size: 15px;
  outline: none;
  border-radius: 5px;
  transition: all .5s;
}

.container button:hover {
  background-color: darkgreen;
  color: #fff;
  transition: all .5s;
}
</style>
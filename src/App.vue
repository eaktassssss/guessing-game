<template>
  <transition-group name="slideContainer" mode="out-in">
    <component :is="activeComponent" key="mainComponent" @activeComponentEvent="activeComponent=$event"></component>
    <canvas key="canvas" id="canvas" v-show="activeComponent=='app-celebrate'"></canvas>
  </transition-group>
</template>
<script>
import GameCards from "./assets/components/GameCards";
import Failure from "./assets/components/Failure";
import Celebrate from "./assets/components/Celebrate";


export default {
  components: {appGameCards: GameCards, appCelebrate: Celebrate, appFailure: Failure},
  data: function() {
    return {
      activeComponent: "app-game-cards"
    }
  },
  methods: {},

}
</script>
<style>
body {
  font-family: sans-serif;
}

.slideContainer-enter {

}

.slideContainer-enter-active {
   animation: slide-in .3s ease-out forwards;
}

.slideContainer-leave {

}

.slideContainer-leave-active {
  animation: slide-out .3s ease-out forwards;
}

@keyframes slide-in {
  from {
    transform: translateX(-1000px);
    opacity:0;
  }
  to {
    transform: translateX(0px);
    opacity: 1;
  }
}

@keyframes slide-out {
  from {
    transform: translateX(0px);
    opacity: 1;
  }
  to {
    transform: translateX(-1000px);
    opacity: 0;
  }
}
</style>
<template>
  
  <div class="game-area">
    <h1 class="title">Kedi <span>Nerede<strong>?</strong></span></h1>
    <h4 class="description">Açık kartlardan birini seçtikten sonra kapalı olan karta tıklayınız</h4>
    <div class="container">
      <transition-group name="rotate-all" class="card-container" appear>
        <app-card :key="value.id" :class="{'shadow':selectedCard==value.id}" @click.native="selectedCard=value.id"
                  v-for="value in cards"
                  :card="value"></app-card>
      </transition-group>
    </div>
   
    <div class="container">
      <transition name="rotate" mode="out-in">
        <component :card="answer" :is="activeCard" @click.native="showCard(answer)">
        </component>
      </transition>
    </div>
  </div>
</template>

<script>
import Card from './Card'
import DefaultCard from "./DefaultCard";
import Failure from "./Failure";
import Celebrate from "./Celebrate";


export default {
  data: function() {
    return {
      answer: {},
      cards: [
        {id: 1, component: "app-card", image: "src/assets/card-1.jpg"},
        {id: 2, component: "app-card", image: "src/assets/card-2.jpg"},
        {id: 3, component: "app-card", image: "src/assets/card-3.jpg"},
        {id: 4, component: "app-card", image: "src/assets/card-4.jpg"},
        {id: 5, component: "app-card", image: "src/assets/card-5.jpg"},
      ],
      selectedCard: null,
      activeCard: "app-default-card"
    }
  },
  components: {appCard: Card, appDefaultCard: DefaultCard, appFailure: Failure, appCelebrate: Celebrate},

  created() {
    const rnd=Math.ceil(Math.random() * this.cards.length);
    this.answer=this.cards[rnd - 1];
  },
  methods: {
    showCard(answer) {
      if(this.selectedCard == null)
        alert("Kart Seçimi Yapınız");
      else{
        this.activeCard=answer.component;
        setTimeout(() => {
          if(answer.id == this.selectedCard){
            this.$emit("activeComponentEvent", "app-celebrate");
          }
          else{
            this.$emit("activeComponentEvent", "app-failure");
          }
        }, 1000);

      }

    }
  }
}
</script>
<style scoped>


.container {
  display: flex;
  justify-content: center;
  margin-top: 50px;
}

.title {
  text-align: center;

  color: rosybrown;

}

.card-container {
  display: flex;
  justify-content: center;
  margin-top: 50px;
}

.title spn {
  color: mediumpurple;
}

.title strong {
  color: darkred;
}

.description {
  color: green;
  text-align: center;
}

.shadow {
  box-shadow: 0px 5px 48px #30969F !important;
  transition: box-shadow .5s;
}

.rotate-all-enter {
}

.rotate-all-enter-active {
  animation: rotate-all ease-in-out 2s forwards;
}

.rotate-all-leave {
}

.rotate-all-leave-active {
}


.rotate-enter {
}

.rotate-enter-active {
  animation: rotate-all ease-in-out 2s forwards;
}

.rotate-leave {
}

.rotate-leave-active {
}

@keyframes rotate-all {
  from {
    transform: rotateY(0);
  }
  to {
    transform: rotateY(360deg);
  }
}

@keyframes rotate-in {
  from {
    transform: rotateY(90deg);
  }
  to {
    transform: rotateY(0deg);
  }
}
</style>

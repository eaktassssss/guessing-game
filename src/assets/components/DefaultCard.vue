<template>
  <div class="card">
    <img src="src/assets/vue-js-egitim-background.jpg">
  </div>
</template>

<script>
export default {
  data: function() { 
    return {
      
    }
  }
}
</script>
<style scoped>
.card {
  width: 200px;
  heigth: 232px;
  border-radius: 5px;
  border: 1px solid #666;
}

.card:hover {
  box-shadow: 0px 5px 48px #666;
  transition: box-shadow .5s;
}

.card img {
  width: 100%;
  height: 100%;
}
</style>
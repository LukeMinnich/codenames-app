<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <GameBoard />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import GameBoard from "@/components/GameBoard.vue";

export default {
  name: "Home",
  components: {
    HelloWorld,
    GameBoard
  }
};
</script>

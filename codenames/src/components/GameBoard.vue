<template>
  <div class="game-board">
    <div class="columns" v-for="row in board">
      <div class="column" v-for="card in row">
        <Card :word="card.word" :teamColor="card.teamColor" />
      </div>
    </div>
  </div>
</template>

<script>
import Card from "@/components/Card.vue";
import { CardData, TeamColor } from "@/models";
import { chunk } from "lodash";

export default {
  name: "GameBoard",
  data() {
    return {
      boardState: [
        new CardData("elevator", TeamColor.BLUE),
        new CardData("poetry", TeamColor.BLUE),
        new CardData("ambition", TeamColor.BLUE),
        new CardData("indication", TeamColor.BLUE),
        new CardData("member", TeamColor.BLUE),
        new CardData("mud", TeamColor.BLUE),
        new CardData("assumption", TeamColor.BLUE),
        new CardData("storage", TeamColor.BLUE),
        new CardData("news", TeamColor.NONE),
        new CardData("attention", TeamColor.NONE),
        new CardData("magazine", TeamColor.NONE),
        new CardData("passion", TeamColor.NONE),
        new CardData("security", TeamColor.BLACK),
        new CardData("technology", TeamColor.NONE),
        new CardData("farmer", TeamColor.NONE),
        new CardData("government", TeamColor.NONE),
        new CardData("attitude", TeamColor.NONE),
        new CardData("inflation", TeamColor.RED),
        new CardData("anxiety", TeamColor.RED),
        new CardData("classroom", TeamColor.RED),
        new CardData("bathroom", TeamColor.RED),
        new CardData("introduction", TeamColor.RED),
        new CardData("family", TeamColor.RED),
        new CardData("desk", TeamColor.RED),
        new CardData("passenger", TeamColor.RED),
      ],
    };
  },
  components: {
    Card,
  },
  computed: {
    board() {
      console.log(chunk(this.boardState, 5));
      return chunk(this.boardState, 5);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.game-board {
  width: 90%;
  margin: 0 auto;
}
</style>

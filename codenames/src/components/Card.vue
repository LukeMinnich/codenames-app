<template>
  <div class="card" @click="flip">
    <div class="card-inner" ref="inner">
      <div class="card-front">
        <h1>{{ formattedWord }}</h1>
      </div>
      <div class="card-back" ref="back">
        <h1>{{ formattedWord }}</h1>
      </div>
    </div>
  </div>
</template>

<script>
import { TeamColor } from "@/models";

const data = {
  flipped: false,
};

export default {
  name: "Card",
  data() {
    return data;
  },
  props: {
    word: String,
    teamColor: Number,
  },
  computed: {
    formattedWord() {
      return this.word.toUpperCase();
    },
  },
  mounted() {
    // setBackSideColor();
  },
  methods: {
    flip() {
      console.log(`tried to flip ${this.formattedWord} from flipped = ${data.flipped}`);
      if (data.flipped) {
        this.$refs.inner.style.transform = "rotateX(0deg)";
      } else {
        // setBackSideColor();
        let backSideColor = "wheat";

        console.log(this.word);

        switch (this.teamColor) {
          case TeamColor.RED:
            backSideColor = "red";
            break;
          case TeamColor.BLUE:
            backSideColor = "blue";
            break;
          case TeamColor.BLACK:
            backSideColor = "black";
            break;
          case TeamColor.NONE:
            backSideColor = "wheat";
            break;
        }
        this.$refs.back.style.backgroundColor = backSideColor;

        this.$refs.inner.style.transform = "rotateX(180deg)";
      }

      data.flipped = !data.flipped;
    },
    setBackSideColor() {
      let backSideColor = "wheat";

      console.log(this.word);

      switch (this.teamColor) {
        case TeamColor.RED:
          backSideColor = "red";
          break;
        case TeamColor.BLUE:
          backSideColor = "blue";
          break;
        case TeamColor.BLACK:
          backSideColor = "black";
          break;
        case TeamColor.NONE:
          backSideColor = "wheat";
          break;
      }
      this.$refs.back.style.backgroundColor = backSideColor;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.card {
  background-color: transparent;
  height: 100px;
}

.card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}

/* .card:hover .card-inner {
  transform: rotateX(180deg);
} */

.card-front,
.card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  border-color: red;
  border-style: dashed;
  border-radius: 10px;
  -webkit-backface-visibility: hidden; /* Safari */
}

.card-front {
  background-color: rgb(216, 190, 157);
}

.card-back {
  background-color: lightblue;
  transform: rotateX(180deg);
}

h1 {
  font-family: Georgia, "Times New Roman", Times, serif;
  font-size: 20px;
  font-weight: bold;
}
</style>

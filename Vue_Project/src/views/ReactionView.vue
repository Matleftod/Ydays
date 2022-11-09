<template>
  <div class="reaction">
    <h1>Ninja Reaction Timer</h1>
    <button @click="start" :disabled="isPlaying">Play</button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
    <Result v-if="showResult" :score="score" />
  </div>
</template>

<style>

</style>

<script lang="ts">
import Block from "../components/Block.vue";
import Result from "../components/Result.vue";
export default {
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
    };
  },
  components: { Block, Result },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.showResult = false;
      this.isPlaying = true;
    },
    endGame(reactionTimer: any) {
      this.score = reactionTimer;
      this.isPlaying = false;
      this.showResult = true;
    }
  },
};
</script>

<style>
.reaction {
  text-align: center;
  margin-top: 30px;
}
button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>

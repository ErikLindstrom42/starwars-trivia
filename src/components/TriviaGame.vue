<template>
  <div>
    <h3>Star Wars Trivia</h3>
    <button @click="selectDifficulty('easy')">Easy</button>
    <button @click="selectDifficulty('medium')">Medium</button>
    <button @click="selectDifficulty('hard')">Hard</button>
    <button @click="selectDifficulty('All')">All</button>
    <button @click="hideAnswers">Hide All Answers</button>

    <div class="cards">
      <div v-for="item in filteredTrivia" :key="item.id">
        <flash-card :card="item" @toggle="handleStatusChange" />
      </div>
    </div>
  </div>
</template>
<script>
import { trivia } from "../trivia";
import FlashCard from "./FlashCard.vue";

export default {
  components: { FlashCard },
  methods: {
    handleStatusChange(item) {
      item.answerShown = !item.answerShown;
      console.log(item);
    },
    hideAnswers() {
      this.filteredTrivia.forEach((x) => (x.answerShown = false));
    },
    selectDifficulty(difficulty) {
      if (difficulty === "All") this.filteredTrivia = [...trivia];
      else {
        this.filteredTrivia = this.triviaQuestions.filter(
          (x) => x.difficulty === difficulty
        );
      }
    },
  },
  data() {
    return {
      triviaQuestions: [...trivia],
      filteredTrivia: [],
    };
  },
};
</script>
<style scoped>
.cards {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
</style>
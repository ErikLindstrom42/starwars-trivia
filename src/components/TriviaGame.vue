<template>
  <div>
    <h3>Star Wars Trivia</h3>
    <div v-for="item in triviaQuestions" :key="item.question">
      <flash-card :card="item" @toggle="handleStatusChange" />
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
  },
  data() {
    return {
      triviaQuestions: [...trivia],
    };
  },
};
</script>
<template>
  <div>
    <div v-if="!card.answerShown">
      <h2>{{ card.question }}</h2>
      <button @click="handleClick">Show Answer</button>
    </div>
    <div v-else>{{ card.answer }}</div>
  </div>
</template>
<script>
export default {
  props: ["card"],
  methods: {
    handleClick() {
      this.$emit("toggle", this.card);
    },
  },
};
</script>
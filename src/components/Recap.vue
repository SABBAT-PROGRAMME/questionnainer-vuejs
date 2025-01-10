<!-- tamplate -->
<template>
  <h1>Recap</h1>
  <p>Score : {{ score }} / {{ quiz.questions.length }}</p>
</template>

<!-- script -->
<script setup>
import { ref, computed } from "vue";

// const question = computed(() => {
//   return props.quiz.questions[props.answers.length];
// });

const props = defineProps({
  answers: Array,
  quiz: Object,
});

const score = computed(() => {
  return props.quiz.questions.reduce((acc, question, index) => {
    if (question.correct_answer === props.answers[index]) {
      return acc + 1;
    }
    return acc;
  }, 0);
});
</script>

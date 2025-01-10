<!-- tamplate -->
<template>
  <h1>{{ quiz.title }}</h1>
  <ProgressBarre :value="step" :max="quiz.questions.length - 1" />
  <Question :question="question" v-if="question" />
</template>

<!-- script -->
<script setup>
import { computed, ref } from "vue";
// importation des composants
import ProgressBarre from "./ProgressBarre.vue";
import Question from "./Question.vue";

const props = defineProps({
  quiz: Object,
});

// variables
const step = ref(0);
const question = computed(() => props.quiz.questions[step.value]);
console.log(question.value);
</script>

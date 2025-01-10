<!-- tamplate -->
<template>
  <h1>{{ quiz.title }}</h1>
  <ProgressBarre :value="step" :max="quiz.questions.length - 1" />
  <Question
    :key="question.question"
    :question="question"
    v-if="state === 'question'"
    @anwser="addAnswer"
  />

  <Recap v-if="state === 'recap'" :answers="answers" :quiz="quiz" />

  {{ answers }}
</template>

<!-- script -->
<script setup>
import { computed, ref } from "vue";
// importation des composants
import ProgressBarre from "./ProgressBarre.vue";
import Question from "./Question.vue";
import Recap from "./Recap.vue";

const props = defineProps({
  quiz: Object,
});

// variables
const state = ref("question");
const answers = ref(props.quiz.questions.map(() => null));
const step = ref(0);
const question = computed(() => props.quiz.questions[step.value]);
console.log(question.value);

// methods
const addAnswer = (answer) => {
  answers.value[step.value] = answer;
  if (step.value === props.quiz.questions.length - 1) {
    state.value = "recap";
  }
  step.value++;
};
</script>

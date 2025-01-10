<!-- tamplate -->
<template>
  <h1>{{ quiz.title }}</h1>
  <ProgressBarre :value="step" :max="quiz.questions.length" />
</template>

<!-- script -->
<script setup>
import { ref } from "vue";
// importation des composants
import ProgressBarre from "./ProgressBarre.vue";

defineProps({
  quiz: Object,
});

// variables
const step = ref(0);
</script>

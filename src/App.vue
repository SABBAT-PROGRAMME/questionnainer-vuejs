<!-- tamplate -->
<template>
  <!-- <h1>{{ quiz.title }}</h1> -->
  <div v-if="state === 'error'">
    <p>Impossible de charger quiz</p>
    <!-- {{ quiz }} -->
  </div>
  <div :aria-busy="state === 'loading... '">
    <Quiz :quiz="quiz" v-if="quiz" />
  </div>
</template>

<!-- script -->
<script setup>
import { ref, onMounted } from "vue";

// importation des composants
import Quiz from "./components/quiz.vue";

// variables
const quiz = ref(null);
const state = ref("loading... ");

// mounted
onMounted(() => {
  fetch("/quiz.json")
    .then((response) => {
      if (response.ok) {
        return response.json();
      }
      throw new Error("impossible de récupérer les données");
    })
    .then((data) => {
      quiz.value = data;
      state.value = "idle";
    })
    .catch((error) => {
      state.value = "error";
    });
});
</script>

<!-- style -->

<style>
.container {
  margin-top: 2em;
}
</style>

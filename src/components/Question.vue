<!-- tamplate -->
<template>
  <div class="question">
    <h3>{{ question.question }}</h3>
    <ul>
      <li v-for="(choice, index) in randomChoice" :key="choice">
        <label :for="`answer-${index}`">
          <input
            :id="`answer-${index}`"
            type="radio"
            name="answer"
            v-model="answer"
            :value="choice"
          />{{ choice }}</label
        >
      </li>
    </ul>
    {{ question.correct_answer }}
    <button :disabled="answer === null" @click="emit('anwser', answer)">
      Question suivante
    </button>
  </div>
</template>

<!-- script -->
<script setup>
import { shuffleArray } from "@/function/array.js/array";
import { ref, watch, computed } from "vue";

const props = defineProps({
  question: Object,
});

const emit = defineEmits(["anwser"]);
const answer = ref(null);
console.log(answer);

const randomChoice = computed(() => shuffleArray(props.question.choices));
</script>

<!-- style -->
<style>
.question {
  margin-top: 2rem;
}

.question button {
  margin-left: auto;
  display: block;
}
</style>

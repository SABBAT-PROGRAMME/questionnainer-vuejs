<!-- tamplate -->
<template>
  <div class="question">
    <h3>{{ question.question }}</h3>
    <ul>
      <li v-for="(choice, index) in question.choices" :key="choice">
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
    {{ answer }}
    <button :disabled="answer === null" @click="emit('anwser', answer)">
      Question suivante
    </button>
  </div>
</template>

<!-- script -->
<script setup>
import { ref } from "vue";

const propos = defineProps({
  question: Object,
});

const emit = defineEmits(["anwser"]);
const answer = ref(null);
console.log(answer);
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

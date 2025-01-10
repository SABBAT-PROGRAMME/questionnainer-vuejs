<!-- tamplate -->
<template>
  <div class="question">
    <h3>{{ question.question }}</h3>
    <ul>
      <li v-for="(choice, index) in question.choices" :key="choice">
        <label :for="`answer-${index}`">
          <input :id="`answer-${index}`" type="radio" name="answer" />{{
            choice
          }}</label
        >
      </li>
    </ul>
    <button>Question suivante</button>
  </div>
</template>

<!-- script -->
<script setup>
const propos = defineProps({
  question: Object,
});
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

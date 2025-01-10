<!-- tamplate -->
<template>
  <div class="question">
    <h3>{{ question.question }}</h3>
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
</style>

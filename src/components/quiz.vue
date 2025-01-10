<!-- tamplate -->
<template>
  <h1>{{ quiz.title }}</h1>
</template>

<!-- script -->
<script setup>
defineProps({
  quiz: Object,
});
</script>

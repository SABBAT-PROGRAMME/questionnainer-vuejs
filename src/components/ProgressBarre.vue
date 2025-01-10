<!-- tamplate -->
<template>
  <div>
    <!-- <progress :value="value" :max="max"></progress> -->

    Etape {{ value }} / {{ max }}
  </div>
</template>

<!-- script -->
<script setup>
defineProps({
  value: Number,
  max: Number,
});
</script>

<script setup>
import { RouterLink } from 'vue-router'
import { defineProps } from 'vue'
const { quizQuestionLength, numberOfCorrectAnswer } = defineProps( [ 'quizQuestionLength', 'numberOfCorrectAnswer' ] );

</script>
<template>
  <div class="results">
    <p>Your results...</p>
    <h1>{{ numberOfCorrectAnswer  + '/' + quizQuestionLength }}</h1>
    <RouterLink to="/">Go to Back</RouterLink>
  </div>
</template>

<style scoped>
  .results {
    text-align: center;
    padding: 100px 0;
  }
  p {
    font-size: 25px;
  }
  h1 {
    font-size: 80px;
  }
</style>
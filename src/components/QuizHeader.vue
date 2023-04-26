<script setup>
import { defineProps } from 'vue';

const {
  questionStatus,
  barPrecent
  } = defineProps( [
    'questionStatus',
    'barPrecent'
  ] );
</script>
<template>
  <header>
    <h4>Question {{ questionStatus }}</h4>
    <div class="bar">
      <div class="complition" :style="{width: barPrecent }">
      </div>
    </div>
  </header>
</template>

<style scoped>
header  {
  margin-top: 20px;

  }
  header h4 {
    font-size: 30px;
  }
  .bar {
    width: 300px;
    height: 50px;
    border: 3px solid bisque;
  }
  .complition {
    height: 100%;
    width: 0%;
    background-color: bisque;
  }
</style>
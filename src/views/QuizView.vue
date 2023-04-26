<script setup>
import Question from '../components/Question.vue';
import QuizHeader from '../components/QuizHeader.vue';
import Result from '../components/Result.vue';
import { useRoute } from 'vue-router';
import { ref, computed} from 'vue';
import quizes from '../data/quizes.json';

const route = useRoute();
const quizId = parseInt( route.params.id );
const quiz = quizes.find( q => q.id === quizId );
const currentQuestionIndex = ref( 0 );
const numberOfCorrectAnswer = ref( 0 );
const questionStatus = computed( () => `${ currentQuestionIndex.value } / ${ quiz.questions.length }` );
const barPrecent = computed( () => `${ currentQuestionIndex.value / quiz.questions.length * 100 }%` );
const showResult = ref(false)

const onOptionSelected = (isCorrect) =>
{
  if ( isCorrect )
  {
    numberOfCorrectAnswer.value++
  }
  if ( quiz.questions.length - 1 === currentQuestionIndex.value )
  {
    showResult.value = true
  }
  currentQuestionIndex.value++
}
</script>

<template>
  <div>
    <QuizHeader 
      :questionStatus="questionStatus"
      :barPrecent="barPrecent"
    />
    <div>
      <Question 
        v-if="!showResult"
        :question="quiz.questions[currentQuestionIndex]"
        @selectOption="onOptionSelected"
      />
      <Result 
        :quizQuestionLength="quiz.questions.length"
        :numberOfCorrectAnswer="numberOfCorrectAnswer"
        v-else
      />
    </div>
  </div>
</template>
<template>
  <v-main>
    <v-container
      :class="isdark ? 'container-dark': ''"
      max-width="1200px"
    >
        <h2
          :class="['mb-2', isdark ? 'white--text' : 'black--text']"
        >Frage: {{question_index + 1}}</h2>
        <Question
          v-if="question_index < questions.length"
          @next="question_index++"
          :question="currentQuestion"
          :isdark="isdark"
        >
        </Question>
        <v-sheet
          v-if="question_index >= questions.length"
          align="center"
          justify-center
          :class="isdark ? 'container-dark': ''"
        >
        <div :class="['text-h2 mb-4', isdark ? 'white--text' : '']">
          No questions left
        </div>
        <br>
        <v-btn @click="question_index=0">
          Start Over
        </v-btn>
        </v-sheet>
      </v-container>
  </v-main>
</template>
<style scoped>
.container-dark {
  background-color: rgb(20, 20, 20);
}
.container {
  max-width: 1200px;
}
</style>
<script>
import questions from '../assets/questions.js'
import Question from './Question.vue'
  export default {
    name: 'HelloWorld',
    components: {
      Question
    },
    props: ['isdark'],

    data: () => ({
     question_index: 0,
    }),
    computed: {
      questions () {
        return questions.questions
      },
      currentQuestion () {
        return this.questions[this.question_index]
      },
    },
    methods: {
      q () {
        console.log(questions)
      }
    }
  }
</script>


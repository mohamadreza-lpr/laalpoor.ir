<template class="bg-secondary">
      <div>
            <b-jumbotron class="m-2 bg-dark">
                  <template #header><h2 class="text-secondary">Questions</h2></template>

                  <template #lead>
                        <p class="text-white">
                              {{ QuestionList.question }}
                        </p>
                  </template>

                  <hr class="my-4" />
                  <b-list-group>
                        <b-list-group-item
                              id="bg-list"
                              v-for="(answer, index) in answers"
                              :key="answer.index"
                              @click="answerIndex(index)"
                        >
                              {{ answer }}
                        </b-list-group-item>
                  </b-list-group>
                  <b-button href="#">Submit</b-button>
                  <b-button href="#" @click="next">NEXT</b-button>
            </b-jumbotron>
      </div>
</template>

<script>
import _ from "lodash";
export default {
      props: {
            QuestionList: Object,
            next: Function,
            correctAnswer:false,
      },
      data() {
            return {
                  allAnswers: undefined,
            };
      },
      methods:{
            answerIndex(index){
                  let correctAnswer = this.answers.indexOf(correctAnswer);
                  if (correctAnswer === index) {
                        this.correctAnswer = true
                  };
                  console.log();
            }
      },
      computed: {
            answers() {
                  let Answers = [...this.QuestionList.incorrect_answers];
                  Answers.push(this.QuestionList.correct_answer);
                  return _.shuffle(Answers);
            },
            
      },
};
</script>

<style>
.btn {
      margin: 10px 2px;
      color: rgb(255, 217, 205);
}
#bg-list {
      background-color: rgb(255, 68, 0);
      font-weight: 500;
      color: rgb(31, 31, 31);
}
#bg-list:hover {
      background-color: rgb(118, 118, 118);
      color: blanchedalmond;
      font-weight: 700;
      cursor: pointer;
}
</style>

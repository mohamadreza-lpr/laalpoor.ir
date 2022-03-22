<template>
      <div>
            <Header :index="this.headerIndex" />
            <b-row>
                  <b-col cols="6" offset="3">
                        <Content :QuestionList="this.questionList[this.index]" :next="next" />
                  </b-col>
            </b-row>
      </div>
</template>

<script>
import LaalHeader from "./components/LaalHeader.vue";
import LaalContent from "./components/LaalContent.vue";
import axios from "axios";
export default {
      name: "App",
      components: {
            Header: LaalHeader,
            Content: LaalContent,
      },
      data() {
            return {
                  questionList: undefined,
                  index: 0,
            };
      },
      mounted() {
            this.getQuestions();
      },
      computed: {
            headerIndex() {
                  let headerIndex = this.index+1;
                  return headerIndex;
            },
      },
      methods: {
            next() {
                  if (this.index < 10) {
                        this.index++;
                  }
            },
            getQuestions() {
                  axios.get("https://opentdb.com/api.php?amount=10&category=21&type=multiple").then((response) => {
                        (this.questionList = response.data.results), console.log(this.questionList[this.index]);
                  });
            },
      },
};
</script>

<style></style>

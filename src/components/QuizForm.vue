<template>
  <form-wizard
    @on-complete="onComplete"
    shape="square"
    color="#3498db"
    @on-change="onChange"
  >
    <tab-content title="" v-for="(item, index) in test.test" :key="index">
      <AnswerBox @sendData="saveAnswer" :content="item" :number="index + 1" />
    </tab-content>
    Answers: {{ answers }}
  </form-wizard>
</template>

<script>
import AnswerBox from "./AnswerBox.vue";
import { FormWizard, TabContent } from "vue-form-wizard";
import "vue-form-wizard/dist/vue-form-wizard.min.css";
import text from "../assets/content.json";

export default {
  name: "QuizForm",
  components: { FormWizard, TabContent, AnswerBox },
  data() {
    return {
      test: text,
      total: 0,
      answers: [],
    };
  },
  props: {
    title: {
      type: String,
      default: "Awesome Wizard Test",
    },
    subtitle: {
      type: String,
      default: "",
    },
    nextButtonText: {
      type: String,
      default: "Next",
    },
    backButtonText: {
      type: String,
      default: "Back",
    },
    finishButtonText: {
      type: String,
      default: "Finish",
    },
  },
  methods: {
    onComplete: function () {
      //alert("Done!");
      console.log(this.answers.length);
    },
    onChange(prevIndex, nextIndex) {
      console.log(prevIndex, nextIndex);
    },
    saveAnswer(answer) {
      let itemIndex = this.answers.findIndex((el) => el.num === answer.num);
      if (itemIndex >= 0) {
        console.log("already exists", this.answers[itemIndex]);
        this.answers[itemIndex] = {
          ...this.answers[itemIndex],
          ...{ points: answer.points },
        };
      } else {
        console.log("new answer, push");
        this.answers.push(answer);
      }
      //let newArray = [...this.answers];
      //newArray[itemIndex] = { ...newArray[itemIndex], points: answer.num };
      //this.answers.push(answer);

      console.log(
        "answer.id",
        answer.num,
        answer.points,
        itemIndex,
        this.answers
      );
    },
  },
};
</script>

<style >
</style>

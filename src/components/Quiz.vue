<template>
  <div>
    <h2>How digitally mature is your Pension Administration?</h2>
    <button @click="start = true" v-if="!start">Start quiz</button>
    <template v-if="start">
      <QuizForm @completeQuiz="getAnswer" />
    </template>
    <template v-if="!start && answerText">
      <QuizResult :score="score" :text="answerText" />
    </template>
  </div>
</template>

<script>
import QuizForm from "./QuizForm";
import QuizResult from "./QuizResult";
import text from "../assets/content.json";

const content = text;
export default {
  name: "Quiz",
  components: { QuizForm, QuizResult },
  data() {
    return {
      test: content,
      total: 0,
      answerText: null,
      score: 0,
      start: false,
    };
  },
  validateOnBack: true,
  methods: {
    getAnswer: function (value) {
      let answer = "";
      const expr = value;
      switch (true) {
        case expr <= 100:
          answer = "Red alert!";
          break;
        case expr > 100 && expr <= 200:
          answer = "Lot of room to improve!";
          break;
        case expr > 200 && expr <= 300:
          answer = "Still work to do!";
          break;
        case expr > 301 && expr <= 400:
          answer = "Almost there!";
          break;
        default:
          console.log(expr);
          answer = "default";
      }
      this.answerText = answer;
      this.score = value;
      this.start = false;
    },
  },
};
</script>

<style >
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding-left: 0;
}
</style>

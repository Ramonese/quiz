<template>
  <div>
    <div>Score {{ total }}</div>
    <QuizForm @completeQuiz="getAnswer" />
    Score: {{ score }} Answer: {{ answerText }}
  </div>
</template>

<script>
import QuizForm from "./QuizForm";

import text from "../assets/content.json";

const content = text;
export default {
  name: "Quiz",
  components: { QuizForm },
  data() {
    return {
      test: content,
      total: 0,
      answerText: null,
      score: 0,
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

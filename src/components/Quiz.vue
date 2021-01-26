<template>
  <div>
    <div>
      <!-- <div v-for="(item, index) in test.test" :key="index">
        <AnswerBox @sendData="saveAnswer" :content="item" :number="index + 1" />
      </div> -->
      Score {{ total }}
    </div>
    <QuizForm />
  </div>
</template>

<script>
import QuizForm from "./QuizForm";
import AnswerBox from "./AnswerBox.vue";
import text from "../assets/content.json";
const content = text;
export default {
  name: "Quiz",
  components: { AnswerBox, QuizForm },
  data() {
    return {
      test: content,
      total: 0,
    };
  },
  validateOnBack: true,
  methods: {},
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

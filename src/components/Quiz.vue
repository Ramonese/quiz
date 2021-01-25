<template>
  <div>
    <div>
      <div v-for="(item, index) in test.test" :key="index">
        <AnswerBox @sendData="saveAnswer" :content="item" :number="index + 1" />
      </div>
      <!-- <div v-for="(item, index) in test.test" :key="index">
        <p>{{ item.question }}</p>
        <ul>
          <li v-for="answer in item.answer" :key="answer.label">
            {{ answer.label }}, {{ answer.value }}
          </li>
        </ul>
      </div> -->
    </div>
  </div>
</template>

<script>
import { FormWizard, TabContent } from "vue-form-wizard";
import "vue-form-wizard/dist/vue-form-wizard.min.css";
import AnswerBox from "./AnswerBox.vue";
import text from "../assets/content.json";
const content = text;
export default {
  name: "Quiz",
  components: { AnswerBox },
  data() {
    return {
      test: content,
    };
  },
  methods: {
    saveAnswer(answer) {
      console.log(answer);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style >
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: upper-latin;
}
</style>

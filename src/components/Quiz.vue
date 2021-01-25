<template>
  <div>
    <div>
      <div v-for="(item, index) in test.test" :key="index">
        <AnswerBox @sendData="saveAnswer" :content="item" :number="index + 1" />
      </div>
      Score {{ total }}
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
      total: 0,
    };
  },
  methods: {
    saveAnswer(answer) {
      console.log(answer);
      this.total = this.total + answer;
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
  list-style-type: none;
  padding-left: 0;
}
</style>

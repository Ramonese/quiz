<template>
  <form-wizard
    @on-complete="onComplete"
    shape="tab"
    color="#007ACA"
    title=""
    subtitle=""
    @on-change="onChange"
  >
    <tab-content title="" v-for="(item, index) in test.test" :key="index">
      <AnswerBox @sendData="saveAnswer" :content="item" :number="index + 1" />
    </tab-content>
    <template slot="footer" scope="props">
      <wizard-button
        v-if="props.activeTabIndex > 0"
        :style="{ background: '#6D6D6D', color: '#fff' }"
        @click.native="props.prevTab()"
        >Back</wizard-button
      >

      <wizard-button
        v-if="!props.isLastStep"
        @click.native="props.nextTab()"
        class="wizard-footer-right"
        :style="props.fillButtonStyle"
        >Next</wizard-button
      >

      <wizard-button
        v-else
        @click.native="onComplete"
        class="wizard-footer-right finish-button"
        :style="props.fillButtonStyle"
        >{{ props.isLastStep ? "Finish" : "Next" }}</wizard-button
      >
    </template>
  </form-wizard>
</template>



<script>
import AnswerBox from "./AnswerBox.vue";
import { FormWizard, TabContent, WizardButton } from "vue-form-wizard";
import "vue-form-wizard/dist/vue-form-wizard.min.css";
import text from "../assets/content.json";

export default {
  name: "QuizForm",
  components: { FormWizard, TabContent, AnswerBox, WizardButton },
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
      let count = 0;
      this.answers.forEach((el) => {
        count = count + el.points;
      });
      this.total = count;
      console.log("total", this.total);
      this.$emit("completeQuiz", this.total);
    },
    onChange(prevIndex, nextIndex) {
      console.log(prevIndex, nextIndex);
    },
    saveAnswer(answer) {
      let itemIndex = this.answers.findIndex((el) => el.num === answer.num);
      if (itemIndex >= 0) {
        console.log("already exists", this.answers[itemIndex]);
        this.answers[itemIndex].points = answer.points;
      } else {
        console.log("new answer, push");
        this.answers.push(answer);
      }
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
.wizard-icon {
  font-style: normal;
}
.wizard-card-footer {
  display: flex;
  align-items: center;
  justify-content: center;
  column-gap: 1em;
}
</style>

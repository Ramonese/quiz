<template>
  <div>
    <div>Score {{ total }}</div>
    <QuizForm />
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

<template>
  <div id="app">
    <Quiz msg="Hello Vue in CodeSandbox!" />
    <!-- v-if show result:  -->
    <QuizResult :score="100" text="red alert" />
  </div>
</template>

<script>
import Quiz from "./components/Quiz";
import QuizResult from "./components/QuizResult";

export default {
  name: "App",
  components: {
    Quiz,
    QuizResult,
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
.blue {
  color: #007ACA;
}
</style>

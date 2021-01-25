<template>
  <div class="quiz-text">
    <header class="quiz--heading">
      <span class="quiz--heading-number">{{ number }}</span>
      <h3 class="quiz--heading-text">{{ content.question }}</h3>
    </header>
    <form @change.prevent="sendAnswer" class="quiz--text">
      <ul>
        <li
          v-for="(answer, index) in content.answer"
          :key="answer.label"
          class="quiz--text-item"
        >
          <div>
            <input
              class="quiz--text-input -sr-only"
              type="radio"
              :id="index"
              :value="answer.value"
              v-model="checked"
            />
            <label :for="index" class="quiz--text-label">{{
              answer.label
            }}</label>
          </div>
        </li>
      </ul>
      {{ checked }}
    </form>
  </div>
</template>

<script>
export default {
  name: "AnswerBox",
  props: {
    content: {
      type: Object,
    },
    number: {},
  },
  data() {
    return {
      checked: "",
    };
  },
  methods: {
    sendAnswer() {
      this.$emit("sendData", this.checked);
    },
  },
};
</script>
<style>
.sr-only {
  clip: rect(0 0 0 0);
  clip-path: inset(100%);
  height: 1px;
  overflow: hidden;
  position: absolute;
  white-space: nowrap;
  width: 1px;
}
.quiz--heading {
  color: #007ACA;
  display: grid;
  border: 1px solid red;
  grid-column-gap: 1em;
  grid-template-columns: max-content 1fr;
  align-items: center;
  margin-bottom: 40px;
}
.quiz--heading-text {
  margin: 0;
}
/* for desktop 140px; */
.quiz--heading-number {
  font-size: 60px;
}
.quiz--text-label {
  color: #6D6D6D;
}
.quiz--text-item {
  margin-bottom: 36px;
}
.quiz--text-input:checked + label {
  color: #007ACA;
}
.quiz--text-input:focus-visible + label {
  outline: 2px solid black;
  outline-offset: 2px;
}
</style>
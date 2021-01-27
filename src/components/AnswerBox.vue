<template>
  <div class="quiz--content">
    <span class="quiz--heading-number blue">{{ number }}</span>
    <h3 class="quiz--heading-text blue">{{ content.question }}</h3>
    <form @change.prevent="sendAnswer" class="quiz--text">
      <ul>
        <li
          v-for="(answer, index) in content.answer"
          :key="answer.label"
          class="quiz--text-item"
        >
          <div>
            <input
              class="quiz--text-input sr-only"
              type="radio"
              :id="index + answer.label"
              :value="answer.value"
              v-model="checked"
            />

            <label :for="index + answer.label" class="quiz--text-label"
              ><span
                v-for="(i, index) in letter[index]"
                class="quiz--label-number"
                :key="i + index"
              >
                {{ i }}</span
              ><span>{{ answer.label }}</span></label
            >
          </div>
        </li>
      </ul>
      {{ checked }}
    </form>
  </div>
</template>

<script>
const letters = ["A", "B", "C", "D"];
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
      letter: letters,
      isChecked: false,
    };
  },
  methods: {
    sendAnswer() {
      let answer = {
        num: this.number,
        points: this.checked,
      };
      this.isChecked = true;
      this.$emit("sendData", answer);
      //this.$emit("isSelected", this.isChecked);
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
.quiz--content {
  display: grid;
  grid-column-gap: 1em;
  grid-template-columns: max-content 1fr;
}

.quiz--text {
  grid-column-start: 2;
}
.quiz--heading-text {
  margin: 0;
  align-self: center;
}
/* for desktop 140px; */
.quiz--heading-number {
  font-size: 60px;
}
.quiz--text {
  padding: 40px 0;
}
.quiz--text-label {
  color: #6D6D6D;
}
.quiz--label-number {
  margin-right: 20px;
}
.quiz--text-item {
  margin-bottom: 36px;
}
.quiz--text-input:checked + .quiz--text-label {
  color: #007ACA;
}
.quiz--text-input:focus-visible + label {
  outline: 2px solid black;
  outline-offset: 2px;
}
</style>
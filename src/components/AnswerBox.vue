<template>
  <div>
    <h3>{{ content.question }}</h3>
    <form @change.prevent="sendAnswer">
      <ul>
        <li v-for="(answer, index) in content.answer" :key="answer.label">
          <div>
            <input
              type="radio"
              :id="index"
              :value="answer.value"
              v-model="checked"
            />
            <label :for="index">{{ answer.label }}</label>
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
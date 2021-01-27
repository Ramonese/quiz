<template>
  <section>
    <h3>Result</h3>
    <p>
      <span>Score: </span><span class="blue">{{ score }}</span
      ><span class="blue"> {{ text }}</span>
    </p>
    <p>Thank you for answering questions! We’ve prepared for you.</p>
  </section>
</template>

<script>
export default {
  name: "QuizResult",
  props: {
    score: {
      type: String,
    },
    text: {
      type: String,
    },
  },
};
</script>
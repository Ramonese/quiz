<template>
  <wizard-step
    slot-scope="props"
    slot="step"
    :tab="props.tab"
    :transition="props.transition"
    :index="props.index"
  >
  </wizard-step>
</template>
<script>
export default {
  name: "Step",
};
</script>
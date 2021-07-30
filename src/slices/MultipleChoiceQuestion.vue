<template>
  <div>
    <prismic-rich-text :field="slice.primary.question_prompt" />
    <div v-for="item in slice.items" :key="item.choice[0].text">
      <input type="checkbox" />
      {{ item.choice[0].text }}
      <!-- {{ item.correct ? "(Correct)" : "" }} -->
    </div>
    <button>Submit</button>
  </div>
</template>

<script>
export default {
  name: "MultipleChoiceQuestion",
  props: {
    slice: Object,
  },
};
</script>

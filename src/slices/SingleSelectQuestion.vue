<template>
  <div>
    <prismic-rich-text :field="slice.primary.question_prompt" />
    <div v-for="item in slice.items" :key="item.choice[0].text">
      <input
        type="radio"
        :id="item.choice[0].text"
        name="singleSelect"
        :value="item.choice[0].text"
      />
      <label :for="item.choice[0].text">{{ item.choice[0].text }}</label>
      <!-- {{ item.correct ? "(Correct)" : "" }} -->
    </div>

    <button>Submit</button>
  </div>
</template>

<script>
export default {
  name: "SingleSelectQuestion",
  props: {
    slice: Object,
  },
};
</script>

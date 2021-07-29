<template>
  <div>
    <prismic-rich-text :field="slice.primary.question_prompt" />
    <input type="text" />
    <button>Submit</button>
  </div>
</template>

<script>
export default {
  name: "TextResponseQuestion",
  props: {
    slice: Object,
  },
};
</script>

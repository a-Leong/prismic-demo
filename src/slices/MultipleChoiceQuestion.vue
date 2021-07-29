<template>
  <div>
    <prismic-rich-text :field="slice.primary.rich_text_field" />
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

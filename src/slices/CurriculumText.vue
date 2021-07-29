<template>
  <prismic-rich-text :field="slice.primary.text" />
</template>

<script>
export default {
  name: "CurriculumText",
  props: {
    slice: Object,
  },
};
</script>

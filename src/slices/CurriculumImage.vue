<template>
  <div class="image-container">
    <prismic-image :field="slice.primary.curriculum_image" />
  </div>
</template>

<script>
export default {
  name: "CurriculumImage",
  props: {
    slice: Object,
  },
};
</script>

<style scoped>
.image-container {
  display: flex;
  justify-content: center;
}
</style>

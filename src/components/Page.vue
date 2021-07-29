<script>
import SliceZone from "vue-slicezone";

import CurriculumText from "@/slices/CurriculumText";
import CurriculumImage from "@/slices/CurriculumImage";
import MultipleChoiceQuestion from "@/slices/MultipleChoiceQuestion";
import TextResponseQuestion from "@/slices/TextResponseQuestion";

export default {
  components: {
    SliceZone,
  },
  props: {
    data: Object,
  },
  data() {
    return {
      slices: {
        CurriculumText,
        CurriculumImage,
        MultipleChoiceQuestion,
        TextResponseQuestion,
      },
    };
  },
};
</script>

<template>
  <div class="page">
    <SliceZone
      :slices="data.body"
      :resolver="({ sliceName }) => slices[sliceName]"
    />
  </div>
</template>

<style scoped>
.page {
  display: flex;
  justify-content: center;
}
</style>

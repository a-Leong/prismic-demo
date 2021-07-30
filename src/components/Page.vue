<script>
import SliceZone from "vue-slicezone";

import CurriculumText from "@/slices/CurriculumText";
import CurriculumImage from "@/slices/CurriculumImage";
import CurriculumQuestion from "@/slices/MultipleChoiceQuestion";
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
        CurriculumQuestion,
        TextResponseQuestion,
      },
    };
  },
};
</script>

<template>
  <SliceZone
    :slices="data.body"
    :resolver="({ sliceName }) => slices[sliceName]"
  />
</template>

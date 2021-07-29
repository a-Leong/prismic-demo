<script>
import Page from "@/components/Page";

export default {
  components: {
    Page,
  },
  props: {
    pages: Array,
  },
  computed: {
    totalPages: function() {
      return this.pages.length;
    },
  },
  data() {
    return {
      currentPageIdx: 0,
    };
  },
  methods: {
    handlePageBack() {
      if (this.currentPageIdx > 0) {
        this.currentPageIdx--;
      }
    },
    handlePageForward() {
      if (this.currentPageIdx < this.totalPages - 1) {
        this.currentPageIdx++;
      }
    },
  },
};
</script>

<template>
  <div v-if="totalPages > 0">
    <Page :data="pages[currentPageIdx].data" />
    <nav>
      Page {{ currentPageIdx + 1 }} of {{ totalPages }}
      <button @click="handlePageBack">Back</button>
      <button @click="handlePageForward">Forward</button>
    </nav>
  </div>
</template>

<style scoped></style>

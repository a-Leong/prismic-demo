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
  <div v-if="totalPages > 0" class="page-list">
    <Page :data="pages[currentPageIdx].data" />
    <nav>
      <button @click="handlePageBack">Back</button>
      <p>Page {{ currentPageIdx + 1 }} of {{ totalPages }}</p>
      <button @click="handlePageForward">Forward</button>
    </nav>
  </div>
</template>

<style scoped>
.page-list {
  max-width: 576px;
  margin: auto;
}

nav {
  position: fixed;
  left: 50%;
  transform: translateX(-50%);
  bottom: 0;
  display: flex;
  justify-content: center;
}
</style>

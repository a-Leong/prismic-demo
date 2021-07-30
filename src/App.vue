<script>
import PageList from "@/components/PageList";

export default {
  name: "App",
  components: {
    PageList,
  },
  data() {
    return {
      // Initialize "response"
      viewing: "homepage",
      homepage: null,
      pages: null,
    };
  },
  methods: {
    viewHomepage() {
      this.viewing = "homepage";
    },
    viewPages() {
      this.viewing = "pages";
    },
    async getContent() {
      this.homepage = await this.$prismic.client.getSingle("homepage");
      this.pages = await this.$prismic.client.query(
        this.$prismic.Predicates.at("document.type", "curriculum_pag")
      );
    },
  },
  created() {
    // Call the API query method
    this.getContent();
  },
};
</script>

<template>
  <div id="app">
    <nav>
      Nav
      <button @click="viewHomepage">Homepage</button>
      <button @click="viewPages">Pages</button>
    </nav>
    <button @click="getContent">Refresh content from Prismic API</button>
    <div
      v-if="homepage != null && viewing === 'homepage'"
      class="homepage"
      :style="{
        'background-color': homepage
          ? homepage.data.homepage_background_color
          : 'unset',
      }"
    >
      <div class="homepage-content">
        <prismic-image :field="homepage.data.banner" />
        <prismic-rich-text :field="homepage.data.main_title" />
      </div>
    </div>
    <div v-if="pages != null && viewing === 'pages'">
      <page-list :pages="pages.results" />
    </div>
  </div>
</template>

<style>
.homepage {
  display: flex;
  flex-direction: row;
  justify-content: center;
}

.homepage-content {
  text-align: center;
  max-width: 576px;
}

button {
  margin: 8px;
}
</style>

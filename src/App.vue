<template>
  <navbar
    :pages="pages"
    :active-page="activePage"
    :nav-link-click="(index) => (activePage = index)"
  ></navbar>
  <create-page :page-created="pageCreated">

  </create-page>
  <!-- <page-viewer v-if="pages.length > 0" :page="pages[activePage]"></page-viewer> -->
</template>

<script>
import PageViewer from "./components/PageViewer.vue";
import Navbar from "./components/Navbar.vue";
import CreatePage from "./components/CreatePage.vue";
export default {
  components: {
    PageViewer,
    Navbar,
    CreatePage
  },
  created() {
    this.getPages();
  },
  data() {
    return {
      activePage: 0,
      theme: "light",
      useDarkNavbar: false,
      pages: [],
    };
  },
  methods: {
    async getPages() {
      let res = await fetch("pages.json");
      let data = await res.json();
      this.pages = data;
    },
    pageCreated(pgObj){
      this.pages.push(pgObj)
    }
  },
};
</script>

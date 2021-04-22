<template>
  <div>
    <blogSearchForm @btn-click="searchRoute($event)"></blogSearchForm>
    <blogListTable :posts="posts"></blogListTable>
  </div>
</template>
<script>
import blogSearchForm from "../../components/Blog/BlogSearchForm.vue";
import blogListTable from "../../components/Blog/BlogListTable.vue";

export default {
  data() {
    return {
      searchText: "",
      posts: [],
    };
  },
  methods: {
    searchRoute(strSearch) {
      if (strSearch.trim() != "") {
        this.searchWhere(strSearch.trim());
      } else {
        this.searchAll();
      }
    },
    async searchAll() {
      const response = await this.$axios.$get("http://localhost:3000/blogs");
      this.posts = response;
    },
    async searchWhere(strValue) {
      let url = "http://localhost:3000/blogs?title_like=" + strValue.trim();
      const response = await this.$axios.$get(url);
      this.posts = response;
    },
  },
  components: {
    blogSearchForm,
    blogListTable,
  },
  mounted() {
    this.searchAll();
  },
};
</script>

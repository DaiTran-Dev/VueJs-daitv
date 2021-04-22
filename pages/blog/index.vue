<template>
  <blogListTable :posts="this.posts"></blogListTable>
</template>
<script>
import blogListTable from "../../components/Blog/BlogListTable.vue";

export default {
  data() {
    return {
      posts: [],
    };
  },
  components: {
    blogListTable,
  },
  methods: {
    async getAllBlog() {
      const response = await this.$axios.$get("http://localhost:3000/blogs");
      this.posts = response;
    },
  },
  mounted(){
    this.getAllBlog();
  }
};
</script>

<template>
  <blogEdit :title="title" :post="post" :edit="edit"></blogEdit>
</template>
<script>
import blogEdit from "../../components/Blog/BlogEdit.vue";
export default {
  data() {
    return {
      title: "Edit Blog",
      post: {},
      edit:true,
    };
  },
  components: {
    blogEdit,
  },
  methods: {
    async fetchSomething(id) {
      let url = "http://localhost:3000/blogs/" + id;
      const response = await this.$axios.$get(url);
      this.post = response;
    },
  },
  mounted() {
    var id = this.$route.params.edit;
    if (id != undefined) {
      this.fetchSomething(id);
    }
  },
};
</script>

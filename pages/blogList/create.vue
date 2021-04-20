<template>
  <blogEdit :title="title" :post="post" :edit="edit"></blogEdit>
</template>
<script>
import blogEdit from "../../components/Blog/BlogEdit.vue";
export default {
  data() {
    return {
      title: "New Blogs",
      post: {
        title: "",
        des: "",
        detail: "",
        image: "",
        category: "",
        position: [],
        public: true,
        data_pubblic: "",
      },
      edit:false,
    };
  },
  components: {
    blogEdit,
  },
};
</script>

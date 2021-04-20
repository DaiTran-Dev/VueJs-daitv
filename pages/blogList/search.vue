<template>
  <div>
    <blogSearchForm></blogSearchForm>
    <blogListTable></blogListTable>
  </div>
</template>
<script>
import blogSearchForm from "../../components/Blog/BlogSearchForm.vue";
import blogListTable from "../../components/Blog/BlogListTable.vue";

export default {
  data() {
    return {};
  },
  components: {
    blogSearchForm,
    blogListTable,
  },
};
</script>

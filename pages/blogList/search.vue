<template>
  <div>
    <blogSearchForm @btn-click="searchText = $event"></blogSearchForm>
    <blogListTable :posts="posts"></blogListTable>
  </div>
</template>
<script>
import blogSearchForm from "../../components/Blog/BlogSearchForm.vue";
import blogListTable from "../../components/Blog/BlogListTable.vue";

export default {
  data() {
    return {
      searchText:'',
      posts:[],
    };
  },
  methods: {
    async searchAll() {
      const response = await this.$axios.$get("http://localhost:3000/blogs");
      this.posts = response;
    },
    async searchWhere(strValue) {
      const response = await this.$axios.$get("http://localhost:3000/blogs");
      var listData = new Array(response)[0];
      this.posts = listData.filter(function(value){
        var str = value.title;
        if(str.indexOf(strValue)!=-1){
          return true;
        }
        return false;
      });
    },
  },
  components: {
    blogSearchForm,
    blogListTable,
  },
  watch:{
    searchText:function(val){
      if(val.trim()!=""){
        this.searchWhere(val.trim())
      }else{
        this.searchAll();
      }
    }
  },
  mounted(){
    this.searchAll();
  }
};
</script>

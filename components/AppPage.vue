<template>
  <div class="container mt-5">
    <!-- Start header  -->
    <AppHeader :title="title"></AppHeader>
    <!-- End header  -->
    <div class="row">
      <!-- Start menu left  -->
      <div class="col-md-3">
        <AppMenu></AppMenu>
      </div>
      <!-- End menu left  -->
      <!-- Start content page  -->
      <div class="col-md-9">
        <BlogList :searchStatus="searchStatus"></BlogList>
      </div>
      <!-- End content page  -->
    </div>
  </div>
</template>

<script>
import AppMenu from "../components/AppMenu.vue";
import AppHeader from "../components/AppHeader.vue";
import BlogCreateEdit from "../components/BlogCreateEdit.vue";
import BlogList from "../components/BlogList.vue";
export default {
  data() {
    return {
      title: "Đây là trang chủ",
      titleAction: "Sửa",
      searchStatus: true,
    };
  },
  components: {
    AppMenu,
    AppHeader,
    BlogCreateEdit,
    BlogList
  },
  methods: {
    test: function () {
      console.log(this.blog.title);
    },
  },
};
</script>

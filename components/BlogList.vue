<template>
  <div class="container-fluid">
    <div class="card" v-if="searchStatus">
      <div class="card-header">Search Blogs</div>
      <div class="card-body">
        <form class="form-inline" action="" method="">
          <div class="form-group">
            <label for="inputPassword6">Tiêu Đề</label>
            <input
              type="password"
              id="inputPassword6"
              class="form-control mx-sm-3"
              placeholder="Tiêu Đề"
            />
          </div>
          <div class="form-group">
            <button type="button" class="btn btn-primary">Search</button>
          </div>
        </form>
      </div>
    </div>
    <div class="card" id="dataTable">
      <div class="card-header">List Blogs</div>
      <div class="card-body">
        <table class="table table-bordered">
          <thead>
            <tr>
              <th scope="col">ID</th>
              <th scope="col">Tin</th>
              <th scope="col">Loại</th>
              <th scope="col">Trạng Thái</th>
              <th scope="col">Vị Trí</th>
              <th scope="col">Ngày Public</th>
              <th scope="col">Edit</th>
              <th scope="col">Delete</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="item in posts" :key="item.id">
              <th scope="row">{{ item.id }}</th>
              <td>{{ item.title }}</td>
              <td>{{ item.title }}</td>
              <td>{{ item.title }}</td>
              <td>{{ item.title }}</td>
              <td>{{ item.title }}</td>
              <td><a href="">Edit</a></td>
              <td><a href="">Delete</a></td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      posts: [],
    };
  },
  props: ["searchStatus"],
  methods: {
    async fetchSomething() {
      const response = await this.$axios.$get("http://localhost:3000/blogs");
      console.log(response);
      this.posts = response;
    },
  }
};
</script>

<template>
  <div class="container-fluid">
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
              <td>{{ convertCategory(item.category) }}</td>
              <td>{{ convertStatus(item.public) }}</td>
              <td>{{ convertPosition(item.position) }}</td>
              <td>{{ item.data_pubblic }}</td>
              <td>
                <NuxtLink :to="linkEdit(item.id)" class="nav-link"
                  >Edit</NuxtLink
                >
              </td>
              <td>
                <button
                  type="button"
                  class="btn-delete"
                  @click="deleteBlog(item.id)"
                >
                  Delete
                </button>
              </td>
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
      categories: [
        { id: 0, name: "Tin Vắn" },
        { id: 1, name: "Thời sự" },
      ],
      position: [
        { id: 0, name: "Việt Nam" },
        { id: 1, name: "Châu Á" },
        { id: 2, name: "Châu Âu" },
        { id: 3, name: "Châu Mỹ" },
      ],
    };
  },
  props: ["posts"],
  methods: {
    convertStatus(status) {
      if (status) {
        return "Hiện";
      }
      return "Ẩn";
    },
    convertPosition(position) {
      position = new Array(position);
      if(position.length==0){
        return;
      }
      position= position[0];
      var positionName = "";
      for (let index = 0; index < this.position.length; index++) {
        let element = this.position[index];
        if(position.find(x=>x==element.id)){
          positionName+=element.name+",";
        }
      }
      return positionName;
    },
    convertCategory(categoryId) {
      var category = this.categories.find(x=>x.id == categoryId);
      if(category){
        return category.name;
      }
      return "";
    },
    linkEdit(id) {
      return "/blog/" + id;
    },
    async getAllBlog() {
      const response = await this.$axios.$get("http://localhost:3000/blogs");
      this.posts = response;
    },
    async deleteBlog(id) {
      var url = "http://localhost:3000/blogs/" + id;
      await this.$axios.$delete(url).then((response) => {
        this.getAllBlog();
      });
    },
  },
};
</script>
<style>
#dataTable {
  padding: 0;
  border: none;
}
#dataTable .card-header {
  padding-left: 0;
  background: none;
  border: none;
  font-weight: bold;
  font-size: 1.3rem;
}
#dataTable .card-body {
  padding: 0;
}
.btn-delete {
  padding: 2px;
  display: inline-block;
  border: 1px solid red;
  color: red;
  border-radius: 10%;
}
</style>

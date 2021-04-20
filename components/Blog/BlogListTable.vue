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
              <td>{{ item.category }}</td>
              <td>{{ convertBoolean(item.public) }}</td>
              <td>{{ convertLocation(item.position) }}</td>
              <td>{{ item.data_pubblic }}</td>
              <td>
                <NuxtLink :to="linkEdit(item.id)" class="nav-link"
                  >Edit</NuxtLink
                >
              </td>
              <td>
                <NuxtLink :to="linkDelete(item.id)" class="nav-link"
                  >Delete</NuxtLink
                >
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
    return {};
  },
  props: ["posts"],
  methods: {
    convertBoolean(value) {
      if (value) {
        return "Hiện";
      }
      return "Ẩn";
    },
    convertLocation(value) {
      var location = "";
      for (let index = 0; index < value.length; index++) {
        const element = value[index];
        if (element == 1) {
          location += " Việt Nam";
        } else if (element == 2) {
          location += " Châu Á";
        } else if (element == 3) {
          location += " Châu Âu";
        } else if (element == 4) {
          location += " Châu Mỹ";
        }
      }
      return location;
    },
    convertCate(value) {
      if (value == 1) {
        return "Thời Sự";
      }
      return "Tin Tức";
    },
    linkEdit(value) {
      return "/blogList/" + value;
    },
    linkDelete(value) {
      return "delele";
    },
  },
};
</script>

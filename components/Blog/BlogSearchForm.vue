<template>
  <div class="card">
    <div class="card-header">Search Blogs</div>
    <div class="card-body">
      <form class="form-inline" action="" method="">
        <div class="form-group">
          <label for="inputPassword6">Tiêu Đề</label>
          <input
            type="text"
            id="inputPassword6"
            class="form-control mx-sm-3"
            placeholder="Tiêu Đề"
            v-model="searchText"
          />
        </div>
        <div class="form-group">
          <button type="button" class="btn btn-primary" @click="$emit('btn-click',searchText)">Search</button>
        </div>
      </form>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      searchText: "",
    };
  },
};
</script>

<template>
  <div class="card" id="f-search">
    <div class="card-header p-0">Search Blogs</div>
    <div class="card-body pl-0 pb-0">
      <form action="" method="">
        <div class="form-group row">
          <label class="col-sm-2 col-form-label">Tiêu Đề</label>
          <div class="col-sm-10">
            <input
              type="text"
              class="mx-sm-3 form-control"
              placeholder="Tiêu Đề"
              v-model="searchText"
            />
          </div>
        </div>
        <div class="form-group row mt-4">
          <div class="col-md-3">
            <button
              type="button"
              class="btn btn-primary btn-search"
              @click="$emit('btn-click', searchText)"
            >
              Search
            </button>
          </div>
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
<style>
#f-search {
  background: none;
  border: none;
  padding-left: 15px;
  padding-top: 20px;
}
#f-search .card-header {
  border: none;
  background: none;
  font-weight: bold;
  font-size: 1.3rem;
}
#f-search .btn-search {
  background: #28a745;
  font-size: 0.8em;
  border-color: #28a745;
}
</style>

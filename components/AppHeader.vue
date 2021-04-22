<template>
  <div class="row">
    <div class="col-md-3">
      <a href="" class="logo">
        <img src="../assets/devfast-logo.png" alt="" class="img-fluid" />
      </a>
    </div>
    <div class="col-md-9">
      <h1 class="title-header">{{ title }}</h1>
    </div>
  </div>
</template>
<script>
export default {
  props: ["title"],
};
</script>
<style scoped>
.logo img {
  width: 150px;
}
.title-header{
  text-transform: capitalize;
  color: black;
  font-weight: bold;
}
</style>>

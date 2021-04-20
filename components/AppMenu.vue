<template>
  <nav class="navbar d-block p-0" id="menu">
    <!-- Links -->
    <ul class="navbar-nav">
      <li class="nav-item active">
        <NuxtLink to="/blogList/" class="nav-link">List</NuxtLink>
      </li>
      <li class="nav-item">
        <NuxtLink to="/blogList/create" class="nav-link">New</NuxtLink>
      </li>
      <li class="nav-item">
        <NuxtLink to="/blogList/search" class="nav-link">Search</NuxtLink>
      </li>
    </ul>
  </nav>
</template>
<script>
export default {
  data() {
    return {
      status: true,
    };
  },
};
</script>
<style scoped>
#menu {
  border: 1px solid #e8e6e6;
  margin-top: 2rem;
}
#menu .nav-item .nav-link {
  border-bottom: 1px solid #e8e6e6;
  color: #000;
  text-align: center;
}
a.nuxt-link-active {
  font-weight: bold;
}
a.nuxt-link-exact-active {
  color: #00c58e;
}
</style>

<template>
  <nav class="navbar d-block p-0" id="menu">
    <!-- Links -->
    <ul class="navbar-nav">
      <li class="nav-item">
        <NuxtLink to="/blog/" class="nav-link">List</NuxtLink>
      </li>
      <li class="nav-item">
        <NuxtLink to="/blog/create" class="nav-link">New</NuxtLink>
      </li>
      <li class="nav-item">
        <NuxtLink to="/blog/search" class="nav-link">Search</NuxtLink>
      </li>
    </ul>
  </nav>
</template>
<script>
export default {};
</script>
<style scoped>
#menu {
  border: 1px solid #e8e6e6;
  margin-top: 14px;
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

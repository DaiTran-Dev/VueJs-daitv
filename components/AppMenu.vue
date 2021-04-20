<template>
  <nav class="navbar d-block p-0" id="menu">
    <!-- Links -->
    <ul class="navbar-nav">
      <li class="nav-item active">
        <a class="nav-link" href="#">List</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">New</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">Search</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">Edit</a>
      </li>
    </ul>
  </nav>
</template>
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
</style>
<script>
export default {};
</script>

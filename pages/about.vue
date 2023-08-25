<template>
  <div class="container">
    <ul class="menu">
      <li><router-link to="/">Home</router-link></li>
      <li><router-link to="/about">About</router-link></li>
      <li><router-link to="/contact">Contact</router-link></li>
    </ul>
    <section>
      <p>Halo Semua</p>
    </section>
  </div>
</template>

<style>
.container {
  width: 75%;
  margin: 100px auto;
  text-align: center;
}
.menu {
  list-style: none;
  margin-bottom: 20px;
}
.menu li {
  display: inline;
}
.menu li a {
  padding: 20px;
  text-decoration: none;
}
</style>

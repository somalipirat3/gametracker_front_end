<template>
<aside>
  <div class="navbar-icon-list">
      <router-link to="/">
        <div class="icon"></div>
      </router-link>
      <router-link to="/about">
        <div class="icon"></div>
      </router-link>
  </div>
</aside>

</template>

<script>
export default {
  name: 'Sidebar',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
aside {
  height: 100%; /* Full-height: remove this if you want "auto" height */
  width: 60px; /* Set the width of the sidebar */
  position: fixed; /* Fixed Sidebar (stay in place on scroll) */
  z-index: 1; /* Stay on top */
  top: 0; /* Stay at the top */
  left: 0;
  background-color: #5666f3; /* Black */
  overflow-x: hidden; /* Disable horizontal scroll */
  padding-top: 20px;
  padding-left: 10px;
  color: white;
  text-align: center;
}

.navbar-icon-list > a >.icon {
  width: 40px;
  height: 40px;
  background-color: #3f4483;
  margin-top: 20px;
  margin-bottom: 20px;
  border-radius: 50%;
}

@media screen and (max-height: 450px) {
  .sidenav {padding-top: 15px;}
  .sidenav a {font-size: 18px;}
}
</style>

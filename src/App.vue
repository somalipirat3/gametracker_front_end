<template>
  <div id="app">
    <Sidebar />
    <router-view class="main" />

    <div class="color_palets">
      <div>Color Palete </div>
      <div style="backgroundColor: #272730"> #272730 </div>
      <div style="backgroundColor: #303038"> #303038</div>
      <div style="backgroundColor: #51536B"> #51536B </div>
      <div style="backgroundColor: #3f4483"> #3f4483 </div>
      <div style="backgroundColor: #5666f3"> #5666f3 </div>
      
      <div style="backgroundColor: #ffb428"> #ffb428 </div>
      <div style="backgroundColor: #50d890"> #50d890 </div>
      <div style="backgroundColor: #ff6b7a"> #ff6b7a </div>
    </div>


  </div>
</template>
<script>
import Sidebar from "@/components/navigation/Sidebar";
export default {
  components: {
    Sidebar
  }
}
</script>
<style>
body {
  background: #272730;
  width: 100%;
  height: 100%;
  /* overflow: hidden; */
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  padding: 0;
  margin: 0;
}
.main {
  margin-left: 60px;
  margin-top: 0;
  color: white;
}
/* #nav a.router-link-exact-active {
  color: #42b983;
} */

input:-webkit-autofill,
input:-webkit-autofill:hover, 
input:-webkit-autofill:focus,
textarea:-webkit-autofill,
textarea:-webkit-autofill:hover,
textarea:-webkit-autofill:focus,
select:-webkit-autofill,
select:-webkit-autofill:hover,
select:-webkit-autofill:focus {
  border: 1px solid #5666f3;
  -webkit-text-fill-color: #f1f1f1;
  -webkit-box-shadow: 0 0 0px 1000px #303038 inset;
  transition: background-color 5000s ease-in-out 0s;
}

  .color_palets > div {
      display: inline-block;
      padding: 12px;
      color: white;
      font-weight: 500;
  }

  .color_palets > div:first-child {
      display: inline-block;
      padding: 12px;
      border-radius: 12px;
  }

  .color_palets {
    position: fixed;
    bottom: 0;
    right: 0;
  }
</style>

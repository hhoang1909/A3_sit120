<template>
  <div class="header">
    <div class="header--left">
      <img class="logo" src="../assets/images/default.png" alt="" srcset="" />
    </div>
    <div class="header--right">
      <ul class="menu">
        <li class="menu-item"><router-link to="/">Home</router-link></li>
        <li class="menu-item"><router-link to="/hot-deals">Hot deals</router-link></li>
        <li class="menu-item"><router-link to="/service">Service</router-link></li>
        <li class="menu-item"><router-link to="/login">Login</router-link></li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.header {
  background-color: #0dc4fe;
  height: auto;
  display: flex;
  justify-content: space-between;
}
.header .header--left {
  display: block;
  height: auto;
  margin: 10px 10px 10px 20px;
}
.header .header--left .logo {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  object-fit: cover;
}

.header .header--right {
  display: flex;
  align-items: center;
  margin-right: 10px;
}

.header .header--right .menu {
  display: block;
  text-align: center;
}
.header .header--right .menu .menu-item {
  display: inline;
  margin-right: 70px;
  font-size: 28px;
}
</style>
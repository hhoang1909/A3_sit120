<template>
  <Layout>
    <div class="container">
      <h1 class="title">Welcome to HA Gear Gaming deals</h1>
    </div>
    <ListProduct />
  </Layout>
</template>

<script>
/**Import component */
import Layout from "../components/Layout.vue";
import ListProduct from "../components/home/ListProduct.vue";

export default {
  /**khai báo component sẽ sử dụng */
  components: {
    Layout,
    ListProduct,
  },
};
</script>

<style scoped>
.title {
  align-self: start;
  margin-top: 40px;
  font-size: 50px;
}
</style>
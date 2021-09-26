<template>
  <Layout>
    <div class="container">
      <h1 class="title">Hot Deals</h1>
    </div>
  </Layout>
</template>

<script>
import Layout from "../components/Layout.vue";

export default {
  components: {
    Layout,
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
<template>
  <div class="layout">
    <Header />
    <slot></slot>
    <Footer />
  </div>
</template>

<script>
import Header from "./Header.vue";
import Footer from "./Footer.vue";
export default {
  components: {
    Header,
    Footer,
  },
};
</script>

<style>
.layout {
  background-color: #c4c4c4;
  min-height: 100vh;
  padding-bottom: 100px;
}
</style>
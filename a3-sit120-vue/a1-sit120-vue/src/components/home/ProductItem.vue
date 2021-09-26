<template>
  <div class="product-item">
    <div class="wapper">
      <img :src="dataProduct.src" />
      <div class="info">
        <div class="title">{{ dataProduct.name }}</div>
        <div class="description">
          {{ dataProduct.description }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  // data which component used 
  props: {
    dataProduct: {
      type: Object,
      default: () => {},
    },
  },
};
</script>

<style scoped>
.product-item {
  display: inline-block;
  /* background: blue; */
  margin: 10px 0 0 2%;
  flex-grow: 1;
  height: auto;
  width: calc(100% * (1 / 4) - 10px - 1px);
}
.wapper {
  display: flex;
}
.wapper img {
  width: 120px;
  height: auto;
  margin-right: 10px;
  object-fit: cover;
}
.wapper .info .title {
  font-weight: bold;
  font-size: 20px;
  margin-bottom: 5px;
}
.wapper .info .description {
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 6; /* number of lines to show */
  -webkit-box-orient: vertical;
}
</style>
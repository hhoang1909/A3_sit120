<template>
  <div class="container">
    <div class="search">
      <label for="searchProduct">Search product:</label>
      <input
        type="text"
        name="searchProduct"
        placeholder="product name"
        v-model="option.productname"
      />
    </div>
    <div class="filters">
      <label for="brand">Brand</label>
      <select name="brand" v-model="option.brand">
        <!-- LOOP data brands -> render ra html option-->
        <!-- v-for="brand in brands" :key="brand.value" -->
        <option v-for="brand in brands" :key="brand.value" :value="brand.value">
          {{ brand.text }}
        </option>
      </select>
      <label for="product">Product</label>
      <select name="product" v-model="option.type">
        <option v-for="type in types" :key="type.value" :value="type.value">
          {{ type.text }}
        </option>
      </select>
    </div>
    <div class="show-product">
      <!-- showProduct || listProduct-->
      <ProductItem
        v-for="product in showProduct"
        :key="product.id"
        :dataProduct="product"
      />
    </div>
  </div>
</template>

<script>
import ProductItem from "./ProductItem.vue";
export default {
  components: {
    ProductItem,
  },
  data() {
    return {
      // Biên để hứng giá trị trong form
      option: {
        productname: "", // all

        brand: 0, // all
        type: 0, // all
      },
      // BEGIN: data dropdown
      brands: [
        { value: 0, text: "All" },
        { value: 1, text: "Razer" },
        { value: 2, text: "Logitech" },
        { value: 3, text: "Alienware" },
        { value: 4, text: "Steelseries" },
      ],
      types: [
        { value: 0, text: "All" },
        { value: 1, text: "Mouse" },
        { value: 2, text: "Keyboard" },
        { value: 4, text: "Headphone" },
      ],
      // END.
      listProduct: [
        {
          id: 1,
          src: require("../../assets/images/m510.jpg"),
          brand: 3,
          type: 1,
          name: "Alienware M510 Gaming Mouse - 1",
          description:
            "Gaming mouse with 10 fully programmable buttons and custom adjustable scroll wheel for performance that dominates in any arena.",
        },
        {
          id: 2,
          src: require("../../assets/images/m510.jpg"),
          brand: 3,
          type: 1,
          name: "Alienware M510 Gaming Mouse - 2",
          description:
            "Gaming mouse with 10 fully programmable buttons and custom adjustable scroll wheel for performance that dominates in any arena.",
        },
        {
          id: 3,
          src: require("../../assets/images/m510.jpg"),
          brand: 3,
          type: 1,
          name: "Alienware M510 Gaming Mouse - 3",
          description:
            "Gaming mouse with 10 fully programmable buttons and custom adjustable scroll wheel for performance that dominates in any arena.",
        },
        {
          id: 4,
          src: require("../../assets/images/510H.jpg"),
          brand: 3,
          type: 4,
          name: "Alienware 510H 7.1Gaming Headset (Lunar Light) - 1",
          description:
            "Get absorbed in your games on the Alienware 7.1 Gaming Headset, showcasing 7.1 surround sound with Alienware Immersive Audio technology.",
        },
        {
          id: 5,
          src: require("../../assets/images/510H.jpg"),
          brand: 3,
          type: 4,
          name: "Alienware 510H 7.1Gaming Headset (Lunar Light) - 2",
          description:
            "Get absorbed in your games on the Alienware 7.1 Gaming Headset, showcasing 7.1 surround sound with Alienware Immersive Audio technology.",
        },
        {
          id: 6,
          src: require("../../assets/images/510H.jpg"),
          brand: 3,
          type: 4,
          name: "Alienware 510H 7.1Gaming Headset (Lunar Light) - 3",
          description:
            "Get absorbed in your games on the Alienware 7.1 Gaming Headset, showcasing 7.1 surround sound with Alienware Immersive Audio technology.",
        },
      ],
    };
  },
  computed: {
    showProduct() {
      // dưa vào biến option sẽ chọn data product nào được show trong listProduct

      // filter chọn data nào thỏa điều kiên // lên google search, nó là function của es6
      // chức năng gàn giống for, vẫn dọc từng phần thử và chỉ trả về phần tử vào thỏa điểu kiện
      return this.listProduct.filter((product) => {
        // search theo tên không? => check Brand & type
        if (this.option.productname) {
          return (
            product.name
              .toLowerCase() // chuyển chữ inh thành chữ thường, search() -> tìm ký tự trong chuỗi chữ
              .search(this.option.productname.toLowerCase()) > -1 &&
            this.checkOption(this.option, product)
          );
        } else {
          // không search theo tên? => check Brand & type
          return this.checkOption(this.option, product);
        }
      });
    },
  },
  methods: {
    // check Brand & type
    checkOption(option, product) {
      // brand: all and typp: all
      if (option.brand === 0 && option.type === 0) return product;
      // brand: expt all and typp: khác all
      if (option.brand !== 0 && option.type !== 0)
        return product.brand === option.brand && product.type === option.type;
      // brand: expt all and type: all
      if (option.brand !== 0 || option.type === 0)
        return product.brand === option.brand;
      // brand: expt and type: khác all
      if (option.brand === 0 || option.type !== 0)
        return product.type === option.type;
    },
  },
};
</script>

<style scoped>
label {
  align-self: start;
  padding-left: 40px;
  font-size: 20px;
}

input,
select {
  margin-left: 5px;
}

.show-product {
  display: flex;
  flex-wrap: wrap;
  margin: 20px 0;
}
</style>
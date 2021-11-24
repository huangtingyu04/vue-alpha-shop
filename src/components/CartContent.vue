<template>
  <div class="cart-box">
    <div class="title">購物籃</div>
    <div id="product-container">
      <div class="product-item" v-for="item in products" :key="item.id">
        <div class="product-img">
          <div
            class="img"
            :style="{ backgroundImage: 'url(' + item.image + ')' }"
          ></div>
        </div>
        <div class="product-detail">
          <div class="product-des">
            <div class="product-title">{{ item.name }}</div>
            <div class="product-num-box">
              <button class="minus-btn btn" @click="minusCount(item.id)">
                -
              </button>
              <span class="product-num">{{ item.count }}</span>
              <button class="add-btn btn" @click="addCount(item.id)">+</button>
            </div>
          </div>
          <div class="fee">{{ item.price }}</div>
        </div>
      </div>
    </div>
    <div class="delivery-fee">
      <span>運費</span>
      <span>{{
        initialShippingCost === 0 ? "免費" : initialShippingCost
      }}</span>
    </div>
    <div class="total">
      <span>小計</span>
      <span class="price">{{ sum }}</span>
    </div>
  </div>
</template>

<script>
const dummyData = [
  {
    id: 1,
    name: "破壞補丁修身牛仔褲",
    count: 1,
    price: 3999,
    image:
      "https://github.com/huangtingyu04/alpha_shop/blob/master/image/product01.png?raw=true",
  },
  {
    id: 2,
    name: "刷色直筒牛仔褲",
    count: 1,
    price: 1299,
    image:
      "https://github.com/huangtingyu04/alpha_shop/blob/master/image/product02.png?raw=true",
  },
];
export default {
  props: {
    initialShippingCost: {
      type: Number,
      required: true,
    },
  },
  data() {
    return {
      products: [],
      sum: 0,
    };
  },
  methods: {
    fetchProductItems() {
      this.products = [...dummyData].map((product) => {
        return { ...product, pricecached: product.price };
      });
    },
    addCount(id) {
      this.products = this.products.map((product) => {
        if (product.id === id) {
          return { ...product, count: product.count + 1 };
        } else {
          return product;
        }
      });
      this.caculateTotalPrice();
    },
    minusCount(id) {
      this.products = this.products.map((product) => {
        if (product.id === id && product.count !== 0) {
          return { ...product, count: product.count - 1 };
        } else {
          return product;
        }
      });
      this.caculateTotalPrice();
    },
    caculateTotalPrice() {
      let tempSum = 0;
      this.products = this.products.map((product) => {
        return { ...product, price: product.count * product.pricecached };
      });
      for (let i = 0; i < this.products.length; i++) {
        tempSum += this.products[i].price;
      }
      this.sum = tempSum + this.initialShippingCost;
    },
  },
  created() {
    this.fetchProductItems();
    this.caculateTotalPrice();
  },
  watch: {
    initialShippingCost() {
      this.caculateTotalPrice();
    },
  },
};
</script>
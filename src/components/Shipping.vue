<template>
  <div class="form-box">
    <form>
      <div class="col-1 d-flex wrap">
        <div class="w-7 delivery-box">
          <input
            type="radio"
            id="standard"
            name="delivery"
            checked
            @click="getShippingCost(0)"
          />
          <label class="delivery" for="standard">
            <div class="box">
              <div class="title">標準運送</div>
              <div class="des">約 3~7 個工作天</div>
            </div>
            <div class="fee">免費</div>
          </label>
        </div>
      </div>
      <div class="col-1 d-flex wrap">
        <div class="w-7 delivery-box">
          <input
            type="radio"
            id="dhl"
            name="delivery"
            @click="getShippingCost(500)"
          />
          <label class="delivery" for="dhl">
            <div class="box">
              <div class="title">DHL 貨運</div>
              <div class="des">48 小時內送達</div>
            </div>
            <div class="fee">$500</div>
          </label>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  props: {
    initialShippingCost: {
      type: Number,
      required: true,
    },
  },
  data() {
    return {
      payment: 0,
    };
  },
  methods: {
    getShippingCost(fee) {
      this.payment = fee;
      this.$emit("updated-fee", this.payment);
    },
    fetchShippingCost() {
      this.payment = this.initialShippingCost;
    },
  },
  created() {
    this.fetchShippingCost();
  },
};
</script>
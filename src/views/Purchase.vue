<template>
  <div class="card-shop">
    <h2 class="main-title">結帳</h2>
    <div class="shop-box">
      <div class="info-box">
        <div>
          <ol class="steps">
            <!-- step-active step-finished -->
            <li
              class="step step-active"
              :class="[{ 'step-finished': step !== 0 }]"
            >
              <span class="order"><small>1</small></span>
              <span class="step-des">寄送地址</span>
            </li>
            <li
              class="step"
              :class="[
                { 'step-active': step !== 1 },
                { 'step-finished': step === 2 },
              ]"
            >
              <span class="order"><small>2</small></span>
              <span class="step-des">運送方式</span>
            </li>
            <li class="step" :class="[{ 'step-active': step === 2 }]">
              <span class="order"><small>3</small></span>
              <span class="step-des">付款資訊</span>
            </li>
          </ol>
          <div class="form-outbox">
            <div class="form-title">寄送地址</div>
            <div id="form-container">
              <Address v-show="step === 0" />
              <Shipping
                v-show="step === 1"
                :initialShippingCost="shippingCost"
                @updated-fee="updateCost"
              />
              <Payment v-show="step === 2" />
            </div>
          </div>
        </div>
        <div class="form-btn">
          <button class="step-btn prev" v-show="step != 0" @click="prevStep()">
            ← 上一步
          </button>
          <button class="step-btn next right" @click="nextStep()">
            {{ step === 2 ? "確認送出" : "下一步 →" }}
          </button>
        </div>
      </div>
      <CartContent :initialShippingCost="shippingCost" />
    </div>
  </div>
</template>

<script>
import Address from "./../components/Address";
import Shipping from "./../components/Shipping";
import Payment from "./../components/Payment";
import CartContent from "./../components/CartContent";

export default {
  components: {
    Address,
    Shipping,
    Payment,
    CartContent,
  },
  data() {
    return {
      step: 0,
      shippingCost: 0,
    };
  },
  methods: {
    nextStep() {
      if (this.step < 2) {
        this.step += 1;
      }
    },
    prevStep() {
      this.step -= 1;
    },
    updateCost(fee) {
      this.shippingCost = fee;
    },
  },
};
</script>
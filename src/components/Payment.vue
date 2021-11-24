<template>
  <div class="form-box">
    <form>
      <div class="col-1 d-flex wrap">
        <div class="w-7">
          <label for="ownerName" class="title">持卡人姓名</label>
          <input id="ownerName" type="text" placeholder="John Doe" />
        </div>
      </div>
      <div class="col-1 d-flex wrap">
        <div class="w-7">
          <label for="cardNumber" class="title">卡號</label>
          <input
            id="cardNumber"
            type="text"
            placeholder="1111 2222 3333 4444"
          />
        </div>
      </div>
      <div class="col-1 d-flex">
        <div class="w-5 m-R-12">
          <label for="date" class="title">有效期限</label>
          <input id="date" type="text" placeholder="MM/YY" />
        </div>
        <div class="w-5">
          <label for="CVC" class="title">CVC / CCV </label>
          <input id="CVC" type="text" placeholder="123" />
        </div>
      </div>
    </form>
  </div>
</template>
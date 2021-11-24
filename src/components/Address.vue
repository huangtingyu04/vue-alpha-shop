<template>
  <div class="form-box">
    <form>
      <div class="col-1 d-flex">
        <div class="w-3 m-R-12">
          <label for="sex-mode" class="title">稱謂</label>
          <div class="select-wrapper">
            <select name="sex-mode" id="sex-mode">
              <option value="先生">先生</option>
              <option value="小姐">小姐</option>
            </select>
          </div>
        </div>
        <div class="w-7">
          <label for="name" class="title">姓名</label>
          <input id="name" type="text" placeholder="請輸入姓名" />
        </div>
      </div>
      <div class="col-1 d-flex wrap">
        <div class="w-5 m-R-12">
          <label for="phone" class="title">電話</label>
          <input id="phone" type="text" placeholder="請輸入行動電話" />
        </div>
        <div class="w-5">
          <label for="e-mail" class="title">Email</label>
          <input id="e-mail" type="text" placeholder="請輸入電子郵件" />
        </div>
      </div>
      <div class="col-1 d-flex wrap">
        <div class="w-5 m-R-12">
          <label for="country" class="title">縣市</label>
          <div class="select-wrapper">
            <select id="country" name="sex-mode">
              <option value="">請選擇縣市</option>
              <option value="先生">先生</option>
              <option value="小姐">小姐</option>
            </select>
          </div>
        </div>
        <div class="w-5">
          <label for="address" class="title">地址</label>
          <input id="address" type="text" placeholder="請輸入地址" />
        </div>
      </div>
    </form>
  </div>
</template>
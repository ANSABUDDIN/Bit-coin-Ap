<template>
  <div>
    <div class="container text-center my-5">
      <h1 class="my-5 fw-bolder heading">Bit-Coin Api With Axios</h1>
      <div class="mx-auto mt-5 fw-bold" v-for="item in list" :key="item">
        <div class="">
          <div class="">
            <div class="px-5 bit-logo">
              {{ item.FROMSYMBOL }}
            </div>
            <div class="px-5 mt-3 fw-bolder d-flex justify-content-between">
              <h5 class="fw-bolder">OPENDAY</h5>
              {{ item.OPENDAY }}
            </div>
            <div class="px-5 fw-bolder mt-3 d-flex justify-content-between">
              <h5 class="fw-bolder">Curent Price of Bit-Coin</h5>
              {{ item.PRICE }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "IndexPage",
  data() {
    return {
      list: [],
    };
  },
  async mounted() {
    let result = await axios.get(
      "https://min-api.cryptocompare.com/data/pricemultifull?fsyms=BTC,ETH&tsyms=USD,EUR,PKR,INR"
    );
    // let result = await axios.get("https://reqres.in/api/users?page=2");
    console.log("api data", result.data.DISPLAY.BTC);
    this.list = result.data.DISPLAY.BTC;
  },
};
</script>

<style scoped>
.bit-logo {
  display: flex;
  justify-content: center;
  font-size: 50px;
  background: #41b883 !important;
  border-radius: 50px;
}
.heading {
  color: #41b883 !important;
  font-size: 40px !important;
}
</style>
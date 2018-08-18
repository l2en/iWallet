<style>
*{
  box-sizing: border-box
}
.walletWrapper{
  border-radius: 5px;
  overflow: hidden;
}
.walletTop{
  height: calc(40vh - 80px);
  background: linear-gradient(to bottom, #1FB7FC 0%,#7087F8 100%);
  color: #fff;
  text-align: center;
  padding-top:80px
}
.moneyNum{
  font-size: 30px;
  font-weight: 600;
}
.walletMid{
  height: 20vh;
  display: flex;
  justify-content: center;

}
.wallet-slider{
  width:85%;
  height: 100%;
  box-shadow: 0 0 7px #98999C;
  position: relative;
  top: -60px;
  border-radius: 5px;
  overflow: hidden;
  z-index: 2;
  display: flex;
  flex-direction:row;
  background-color: #fff;
}
.wallet-slider-leftLists{
  width: 70vw;
  display: flex;
  flex-direction: column;
  padding-left: 20px;
  padding-top:20px;
}
.wallet-slider-leftLists-top{
  color: #909090;
  font-size: 15px;
}
.wallet-slider-leftLists-bottom{
    font-size: 30px;
    font-weight: 600;
    color:#4CA2E0;
}
.wallet-slider-maxPayment{
  width: 30vw;
  display: flex;
  flex-direction: column;
  padding-top:20px;
}
.wallet-slider-maxPaymentName{
  color: #4CA2E0;
  font-weight: 500;
  font-size: 1.1em;
  padding-right:20px;
  overflow: hidden;
  text-overflow:ellipsis;
  white-space: nowrap;
}
</style>
<template>
  <div class="walletWrapper">
      <div class="walletTop">
            <p class="moneyType">还款</p>
            <p class="moneyNum">8,466.88</p>
        </div>
      <div class="walletMid">
        <div class="wallet-slider">
          <div class="wallet-slider-leftLists">
              <p class="wallet-slider-leftLists-top"><span style="color:#4CA2E0;font-size:20px">5</span>项还款</p>
              <p class="wallet-slider-leftLists-bottom">2,000.00</p>
          </div>
          <div class="wallet-slider-maxPayment">
            <p class="wallet-slider-maxPaymentName">蜡笔分期</p>
          </div>
        </div>
      </div>
  </div>
</template>

<script>
// Use Vuex
import store from "./store";

export default {
  computed: {
    counter() {
      return store.state.count
    }
  },
  created(){

},

  methods: {
    increment() {
      store.commit("increment")
    },
    decrement() {
      store.commit("decrement")
    }
  }
};
</script>


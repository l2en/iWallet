<template>
    <image :src='imgSrc' mode="widthFix" class="index" @click="finger"/>
</template>

<script>
const imgSrc = require('./finger.png')
export default {
  data() {
    return {
      imgSrc: ''
    };
  },
  components: {

  },
  created(){
    this.finger()
  },
  mounted(){
    this.imgSrc = imgSrc
  },
  methods: {
     getUserInfo() {
      // 调用登录接口
      wx.login({
        success: () => {
          wx.getUserInfo({
            success: res => {
              console.log("user info:", res);
              this.userInfo = res.userInfo;
            }
          })
        }
      })
    },
    finger() {
      wx.checkIsSupportSoterAuthentication({
        success(res) {
          wx.checkIsSoterEnrolledInDevice({
            checkAuthMode: "fingerPrint",
            success(res) {
              if (!res.isEnrolled) return;
                wx.startSoterAuthentication({
                  requestAuthModes: ['fingerPrint'],
                  challenge: "123456",
                  // authContent: "请用指纹解锁",
                  success(resp) {
                    console.log("指纹解锁成功", resp)
                    // this.getUserInfo()
                    const url = "../walletMain/main"
                    wx.navigateTo({ url })
                      
                  },
                  fail(err) {
                    console.log("指纹解锁失败", err)
                  }
                })
            }
          })
        }
      })
    },
    scanCode() {
      wx.scanCode({
        success: res => {
          console.log("scan result", res);
        }
      });
    }
  }
}
</script>

<style scoped>
.index{
  width: 100%
}
</style>

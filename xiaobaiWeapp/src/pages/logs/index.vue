<template>
  <div>
    <div class="maxbox">
      <div class="box">
        <img class="touxiang" src="/static/images/touxiang.png" />
        <span>用户名：{{ username }}</span>
      </div>
      <div class="bg">
        <img src="/static/images/bg.png" alt="" />
      </div>
    </div>
    <div class="list">
      <span>微信版本号</span>
      <span>7.0.0</span>
    </div>
    <div class="listTwo">
      <span>操作系统</span>
      <span>ios10.0.1</span>
    </div>
    <div class="con">
      <van-button
        class="btn"
        slot="button"
        round
        block
        color="#3d7ef9"
        @click="btn"
        >退出登录</van-button
      >
    </div>
    <van-toast id="van-toast" />
  </div>
</template>

<script>
import Toast from "vant-weapp/dist/toast/toast";

export default {
  components: {},

  data() {
    return {
      username: "是一只羊",
    };
  },
  methods: {
    btn() {
      Toast.success("退出成功");
      //500ms后跳转到首页
      wx.navigateTo({
        url:"/pages/login/main"
      })
    },
  },
  beforeMount() {
    var that = this;
    console.log(1111)
    wx.getStorage({
      key: "user",
      success(res) {
        console.log(res.data)
        that.username = res.data.username;
      },
      fail(res) {
        Toast.fail("用户名查找失败");
      },
    });
  },
};
</script>

<style>
.btn {
  float: right;
  width: 35%;
  height: 44px;
  background-color: #3d7ef9;
  border-radius: 22px;
  color: #fff;
}
.con {
  width: 80%;
  margin: 70px auto;
}

.list {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 80%;
  height: 30px;
  background-color: #3d7ef9;
  margin: 70px auto;
  border-radius: 15px;
}
.listTwo {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 80%;
  height: 30px;
  background-color: #3d7ef9;
  margin: -30px auto;
  border-radius: 15px;
}
.listTwo span:nth-child(1) {
  margin-left: 20px;
  width: 28%;
  color: #fff;
}
.listTwo span:nth-child(2) {
  color: #fff;
  width: 30%;
}

.list span:nth-child(1) {
  margin-left: 20px;
  width: 28%;
  color: #fff;
}
.list span:nth-child(2) {
  color: #fff;
  width: 20%;
}
.touxiang {
  width: 75px;
  height: 75px;
  border-radius: 50%;
}
.box {
  width: 70%;
  display: flex;
  align-items: center;
  /* justify-content: space-between; */
  margin: 30px auto;
}
.box span {
  margin-left: 10px;
  color: #000;
}
.bg img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 150px;
  opacity: 0.5;
  z-index: -1;
}
</style>

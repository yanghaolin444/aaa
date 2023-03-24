<template>
  <div>
    <div class="nav">注 意 事 项</div>
    <div class="box">
      <ul class="inner-box">
        <li v-for="(item, index) in data" :key="index" @click="onClose(index)">
          <div class="hover">{{ index + 1 }}、{{ item.title }}</div>
          <div class="title">
            {{ item.list }}
          </div>
          <img :src="item.img" alt="" />
          <div class="boot">
            <span>发布人:{{ item.pubName }}</span>
            <span>发布时间:{{ item.time }}</span>
          </div>
        </li>
      </ul>
    </div>
    <van-popup :show="show" @click="onCloseTwo" position="right">
      <div class="nav-div">
        <div>{{ popup.id }}、{{ popup.title }}。</div>
        <img :src="popup.img" alt="" />
        <p class="p">&nbsp;&nbsp;{{popup.list}}</p>
      </div>
      <div class="boot2">
            <span>发布人:{{ popup.pubName }}</span>
            <span>发布时间:{{ popup.time }}</span>
          </div>
    </van-popup>
  </div>
</template>

<script>
import Toast from "vant-weapp/dist/toast/toast";
// import Popup from "vant-weapp/dist/popup/index";

export default {
  components: {},
  data() {
    return {
      data: [
        {
          id: 1,
          pubName: "秋耹",
          img: "./images/1.png",
          time: "2023-3-15",
          title: "确定智能家居的类型,是有线系统还是无线系统",
          list: "有线的智能家居优点是比较稳定，不过安装施工需要和装修一起进行，基本上所有的功能都需要一步到位，后期的结构调整和功能的增减成本比较大，所以如果想要安装有线智能家居系统，需要在前期就有专业的人员介入，从设计到施工，再到验收。  反而无线智能家居就相对要简单的多，施工比较方便、灵活性比较强，在使用的过程中能够随时扩展功能、调整结构、整体的使用成本比较低，不过不是很稳定，穿透性差。",
        },
        {
          id: 2,
          pubName: "大罗皮仙",
          time: "2023-2-23",
          title: "布线注意事项",
          img: "./images/2.png",
          list: "很多的智能产品供电方式是零火线供电，不过一般的装修水电工都是默认的单火线供电，所以在前期走线过程当中，预留零线是非常重要的。不然后期重新布线的成本比较大，而且会破坏装修。  装修过程当中，尽可能的多预留插座，相当一部分的智能家居组件都是需要电源的，如果没有在前期布置好插座，很容易导致后期设备无法安装，不然走明线会非常难看。例如智能马桶、智能窗帘、投影幕布、摄像头等等，都是需要预留插座的。",
        },
        {
          id: 3,
          pubName: "落羽成尘",
          time: "2023-2-16",
          title: "智能灯光注意事项",
          img: "./images/3.png",
          list: "可以使用网络摄像头来进行查看家中事物和老人情况。同时，摄像头还具备监听功能，可以在办公室随时监听家中情况。还可以给老人配上一个一键紧急按钮，万一遇到突发性事件，只需要按动手中遥控器的按键，主机便会自动打电话或发短信给子女进行通告。",
        },
        {
          id: 4,
          pubName: "ArthurPandragon",
          time: "2023-1-25",
          title:
            "我家里有老人在家，因为老人一个人在家，有时候有点不放心，有什么功能和办法可以帮我做一下监测?",
          img: "./images/4.png",
          list: "首先应该确认哪些区域需要使用智能灯具，需要使用什么类型的灯具，是否需要冷暖调色；例如射灯和筒灯的开孔尺寸是需要提前就进行确认的；灯带和线条灯都需要预留凹槽。LED灯具有自身的电源驱动，需提前注意安装环境，预留适当的安装空间。智能灯光总之，在装修的时候是需要将智能家居的安装考虑进来来同步进行，这样是非常省时省力的，而且随着智能家居产品技术的成熟，即便是老房子新装智能家居也不必打动干戈，找个专业的智能团队，能够给您提供不同的智能家居场景以及全屋的智能家居方案。",
        }
      ],
      show: false,
      popup: {},
    };
  },
  methods: {
    onClose(index) {
      this.show = !this.show;
      this.popup = this.data[index]
    },
    onCloseTwo() {
      this.show = !this.show;
    }
  },
  beforeMount() {},
};
</script>

<style>
.nav-div div:nth-child(1){
  margin: 10px 0 10px 0;

}
.p{
  line-height: 30px;
}
.nav-div{
  width: 90%;
  margin: 0 auto;
}
.nav-div img{
  width: 100%;
}
.nav {
  position: fixed;
  top: 0px;
  left: 0px;
  width: 100%;
  color: #fff;
  padding: 0 0 10px 0;
  background-color: #3d7ef9;
  text-align: center;
  z-index: 100;
}
.box {
  width: 90%;
  margin: 0 auto;
}
.inner-box li:nth-child(1) {
  margin-top: 40px;
}
.inner-box li {
  position: relative;
  padding: 10px;
  width: 95%;
  margin: 10px auto;
  height: 160px;
  /* border: 1px solid #3d7ef9; */
  border-radius: 5px;
  background-color: #e6e6e6;
}
.inner-box li div:nth-child(1) {
  width: 120px;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}
.inner-box li div:nth-child(2) {
  width: 180px;
  -webkit-line-clamp: 4;
  display: -webkit-box;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
}
.inner-box li img {
  position: absolute;
  top: 10px;
  right: 10px;
  width: 40%;
  height: 50%;
  border-radius: 5px;
}
.boot {
  margin-top: 50px;
  display: flex;
  justify-content: space-between;
}
.boot span {
  font-size: 12px;
}
.boot span:nth-child(1) {
  color: #3d7ef9;
}
.boot span:nth-child(2) {
  color: #b73df9;
}
.title {
  margin-top: 10px;
  font-size: 12px;
}
.hover:hover {
  color: red;
}
.boot2{
  margin: 40px auto;
  width: 90%;
  display: flex;
  justify-content: space-between;
}
.boot2 span:nth-child(1) {
  font-size: 12px;
  color: #3d7ef9;
}
.boot2 span:nth-child(2) {
  font-size: 12px;
  color: #b73df9;
}
</style>

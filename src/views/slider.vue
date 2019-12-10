<template>
  <div class="slide" @mouseenter="stop" @mouseleave="begin">
    <div class="slideItem">
      <ul>
        <li v-for="(item, index) in imgUrl" v-show="mark === index" :key="index">
          <img :src="item" alt />
        </li>
      </ul>
    </div>
    <div class="btn">
      <span class="leftBtn" @click="leftClick()">&gt</span>
      <span class="rightBtn" @click="rightClick()">&lt</span>
    </div>
    <div class="bar">
      <span
        v-for="(item, index) in imgUrl.length"
        @click="change(index)"
        :class="{'active': index === mark}"
        :key="index"
      ></span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      mark: 0,
      timer: null,
      isActive: false,
      // btnActive:'',
      imgUrl: [
        require("../assets/img/slide1.jpg"),
        require("../assets/img/slide2.jpg"),
        require("../assets/img/slide3.jpg"),
        require("../assets/img/slide4.jpg"),
        require("../assets/img/slide5.jpg")
      ]
    };
  },
  methods: {
    autoplay() {
      this.mark++;
      if (this.mark === this.imgUrl.length) {
        this.mark = 0;
      }
    },
    play() {
      clearInterval(this.timer);
      this.timer = setInterval(this.autoplay, 3000);
    },
    leftClick() {
      if (this.mark === 0) {
        this.mark = this.imgUrl.length - 1;
      } else {
        this.mark--;
      }
    },
    rightClick() {
      if (this.mark === this.imgUrl.length - 1) {
        this.mark = 0;
      } else {
        this.mark++;
      }
    },
    change(index) {
      this.mark = index;
    },
    stop() {
      clearInterval(this.timer);
    },
    begin() {
      this.play();
    }
  },
  created() {
    this.play();
  }
}
</script>

<style>
.slide {
  width: 100%;
  height: 700px;
  position: relative;
  overflow: hidden;
}
.slideItem {
  width: 1920px;
  height: 700px;
}
.btn {
  width: 100%;
  position: absolute;
  top: 50%;
}
.btn span {
  width: 50px;
  height: 50px;
  line-height: 50px;
  text-align: center;
  font-size: 30px;
  display: block;
  background: #fff;
  opacity: 0.5;
  
}
.btn .leftBtn{
  margin-left: 50px;
  float: left;

}

.btn .rightBtn {
  float: right;
  margin-right: 50px;
}
.btn span:hover {
  background: #f30;
  color: #fff;
  transition: all 1s ease;
}
.bar {
  width: 100%;
  position: absolute;
  bottom: 20px;
  text-align: center;
  clear: both;
}

.bar span {
  width: 25px;
  height: 25px;
  background: #fff;
  border-radius: 50%;
  margin: 0 5px;
  display: inline-block;
}
.bar .active {
  background: #f30;
  transition: all 1s ease;
}
</style>
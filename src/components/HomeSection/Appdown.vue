<template>
  <div class="appdown">
    <div
      class="leftWrap"
      :class="{
        animationIn: nowIndex === activeIndex,
        animationOut: nowIndex !== activeIndex,
      }"
    ></div>
    <div
      class="rightWrap"
      :class="{
        animationIn: nowIndex === activeIndex,
        animationOut: nowIndex !== activeIndex,
      }"
    >
      <div class="show_app_img_wrap">
        <div class="img_box appgame">
          <img :src="imgInfo.q1" alt="" />
          <img :src="imgInfo.t12" alt="" />
        </div>
        <div class="img_box appgame">
          <img :src="imgInfo.yinzi" alt="" />
        </div>
        <div class="img_box appgame">
          <img :src="imgInfo.q2" alt="" />
          <img :src="imgInfo.t22" alt="" />
        </div>
        <div class="img_box appgame">
          <img :src="imgInfo.yinzi02" alt="" />
        </div>
        <div class="img_box appgame">
          <img :src="imgInfo.q3" alt="" />
          <img :src="imgInfo.q32" alt="" />
        </div>
        <div class="img_box appgame">
          <img :src="imgInfo.yinzi03" alt="" />
        </div>
        <div class="img_box appgame">
          <img :src="imgInfo.q4" alt="" />
        </div>
      </div>
      <div class="base_img_wrap">
        <img :src="imgInfo.dizuo" alt="" />
        <img :src="imgInfo.qfooter" alt="" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    type: {
      type: String,
      default: "",
    },
    nowIndex: {
      type: Number,
      default: 0,
    },
    activeIndex: {
      type: Number,
      default: 0,
    },
  },
  data() {
    return {
      imgInfo: {},
      allImg: {
        q1: require("@/assets/images/home/q-1@2x.png"),
        q2: require("@/assets/images/home/q-2@2x.png"),
        t12: require("@/assets/images/home/t-1-2@2x.png"),
        yinzi: require("@/assets/images/home/yinzi-01_2@2x.png"),
        t22: require("@/assets/images/home/t-2-2@2x.png"),
        yinzi02: require("@/assets/images/home/yinzi-02_2@2x.png"),
        q3: require("@/assets/images/home/q-3@2x.png"),
        q32: require("@/assets/images/home/q-3-2@2x.png"),
        yinzi03: require("@/assets/images/home/yinzi-03_2@2x.png"),
        q4: require("@/assets/images/home/q-4@2x.png"),
        dizuo: require("@/assets/images/home/dizuo_2@2x.png"),
        qfooter: require("@/assets/images/home/q-footer.png"),
      },
      sportImg: {
        q1: require("@/assets/images/home/q-2@2x.png"),
        q2: require("@/assets/images/home/q-1@2x.png"),
        t12: require("@/assets/images/home/t-1-2@2x.png"),
        yinzi: require("@/assets/images/home/yinzi-01_2@2x.png"),
        t22: require("@/assets/images/home/t-2-2@2x.png"),
        yinzi02: require("@/assets/images/home/yinzi-02_2@2x.png"),
        q3: require("@/assets/images/home/q-3@2x.png"),
        q32: require("@/assets/images/home/q-3-2@2x.png"),
        yinzi03: require("@/assets/images/home/yinzi-03_2@2x.png"),
        q4: require("@/assets/images/home/q-4@2x.png"),
        dizuo: require("@/assets/images/home/dizuo_2@2x.png"),
        qfooter: require("@/assets/images/home/q-footer.png"),
      },
    };
  },
  mounted() {
    // 根据不同的类型，展示不同的图片
    if (this.type === "all") {
      this.imgInfo = this.allImg;
    } else if (this.type === "sport") {
      this.imgInfo = this.sportImg;
    }
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/css/animation.scss";

.appdown {
  position: absolute;
  width: 100%;
  top: 0;
  display: flex;
  height: 660px;
  .leftWrap {
    width: 490px;
    min-width: 490px;
    position: relative;
    left: 0;
    margin-top: 60px;
    font-family: MicrosoftYaHei;
    background-color: #999;

    &.animationOut {
      @include animation_left_out;
    }

    &.animationIn {
      @include animation_left_in;
    }
  }
  .rightWrap {
    flex: 1;
    position: relative;
    z-index: 4;

    &.animationOut {
      @include animation_right_out;
    }

    &.animationIn {
      position: relative;
      z-index: 1;
      @include animation_right_in;

      $cardTime: 1.5s;
      .img_box {
        &:nth-child(1) {
          animation: cardIn1 $cardTime ease-out both;
        }
        &:nth-child(2) {
          animation: cardIn1 $cardTime ease-out both;
        }
        &:nth-child(3) {
          animation: cardIn2 $cardTime ease-out both;
        }
        &:nth-child(4) {
          animation: cardIn2 $cardTime ease-out both;
        }
        &:nth-child(5) {
          animation: cardIn3 $cardTime ease-out both;
          img {
            &:nth-child(2) {
              animation: cardInshadow3 $cardTime ease-out both;
            }
          }
        }
        &:nth-child(6) {
          animation: cardIn3 $cardTime ease-out both;
        }
        &:nth-child(7) {
          animation: cardIn4 $cardTime ease-out both;
        }
      }
    }
    .show_app_img_wrap {
      .img_box {
        position: absolute;
        z-index: 3;
        top: 0;
        img {
          width: 100%;
        }
        &:nth-child(1) {
          width: 264px;
          left: 42px;
          top: 60px;
          z-index: 10;

          img {
            &:nth-child(1) {
              position: relative;
              z-index: 1;
            }
            &:nth-child(2) {
              width: 218px;
              position: absolute;
              right: -46px;
              top: 15px;
            }
          }
        }
        &:nth-child(2) {
          width: 515px;
          height: 105px;
          position: absolute;
          left: 52px;
          top: 395px;
        }
        &:nth-child(3) {
          width: 323px;
          left: 126px;
          z-index: 8;
          top: 32px;
          img {
            &:nth-child(1) {
              position: relative;
              z-index: 1;
            }
            &:nth-child(2) {
              width: 215px;
              position: absolute;
              right: -40px;
              top: 17px;
            }
            &:nth-child(3) {
              width: 591px;
              position: absolute;
              left: -22px;
              bottom: -32px;
            }
          }
        }
        &:nth-child(4) {
          width: 591px;
          height: 105px;
          position: absolute;
          left: 102px;
          top: 398px;
        }
        &:nth-child(5) {
          width: 325px;
          left: 274px;
          top: 38px;
          z-index: 6;
          img {
            &:nth-child(1) {
              position: relative;
              z-index: 1;
            }
            &:nth-child(2) {
              width: 194px;
              position: absolute;
              right: -32px;
              top: 79px;
            }
          }
        }
        &:nth-child(6) {
          width: 505px;
          height: 106px;
          position: absolute;
          left: 250px;
          top: 406px;
        }
      }
      .appgame {
        &:last-child {
          width: 242px;
          left: 450px;
          top: 121px;
        }
      }
      .sport {
        &:nth-child(5) {
          img {
            &:nth-child(2) {
              width: 168px;
              position: absolute;
              right: -16px;
              top: 105px;
            }
          }
        }
        &:last-child {
          width: 256px;
          left: 450px;
          top: 145px;
        }
      }
    }

    .base_img_wrap {
      position: absolute;
      bottom: 0;
      img {
        &:nth-child(1) {
          width: 723px;
          z-index: 1;
        }
        &:nth-child(2) {
          width: 294px;
          position: absolute;
          right: 0;
          bottom: 0;
          z-index: 10;
        }
      }
    }
  }

  // 卡片进入动画
  @keyframes cardIn1 {
    0% {
      opacity: 0;
      transform: translate3d(438px, 0, 0);
    }

    80% {
      opacity: 1;
      transform: translate3d(-30px, 0, 0);
    }

    100% {
      opacity: 1;
      transform: translate3d(0, 0, 0);
    }
  }
  @keyframes cardIn2 {
    0% {
      opacity: 0;
      transform: translate3d(320px, 0, 0);
    }

    80% {
      opacity: 1;
      transform: translate3d(-20px, 0, 0);
    }

    100% {
      opacity: 1;
      transform: translate3d(0, 0, 0);
    }
  }
  @keyframes cardIn3 {
    0% {
      opacity: 0;
      transform: translate3d(185px, 0, 0);
    }

    80% {
      opacity: 1;
      transform: translate3d(-10px, 0, 0);
    }

    100% {
      opacity: 1;
      transform: translate3d(0, 0, 0);
    }
  }
  @keyframes cardInshadow3 {
    0% {
      opacity: 0;
      transform: translate3d(185px, 0, 0);
    }

    80% {
      opacity: 0;
      transform: translate3d(-10px, 0, 0);
    }

    100% {
      opacity: 1;
      transform: translate3d(0, 0, 0);
    }
  }

  @keyframes cardIn4 {
    0% {
      opacity: 1;
      transform: translate3d(30px, 0, 0);
    }

    80% {
      opacity: 1;
      transform: translate3d(-5px, 0, 0);
    }

    100% {
      opacity: 1;
      transform: translate3d(0, 0, 0);
    }
  }
}
</style>

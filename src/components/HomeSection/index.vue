<template>
  <div>
    <div class="wrap">
      <div class="header">
        <img v-if="titleImg" :src="titleImg" alt="" />
        <h2>
          {{ title }}
        </h2>
        <p>
          {{ titleMsg }}
        </p>
      </div>
      <div class="tab">
        <ul :class="direction">
          <li
            @click="seletIndex(index)"
            :class="{ active: nowIndex === index }"
            v-for="(item, index) in tabLlist"
            :key="index"
          >
            <div :class="{ activeWrap: nowIndex === index, iconWrap: true }">
              <img class="icon" :src="item.icon" alt="" />
              <img class="activeIcon" :src="item.activeIcon" alt="" />
            </div>
            <span>{{ item.title }}</span>
          </li>
        </ul>
      </div>
      <div :style="{ height: height + 'px' }" class="content">
        <slot></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    // 当前选择的类型
    nowIndex: {
      type: Number,
      default: 0,
    },
    // 内容的高度
    height: {
      type: Number,
      default: 520,
    },
    // 标题
    title: {
      type: String,
      default: "",
    },
    // 标题上面的图片
    titleImg: {
      type: String,
      default: "",
    },
    // 标题下面的描述
    titleMsg: {
      type: String,
      default: "",
    },
    // tab列表
    tabLlist: {
      type: Array,
      default: () => [],
    },
    // tab列表排列方向
    direction: {
      type: String,
      default: "",
    },
  },
  methods: {
    seletIndex(i) {
      this.$emit("selectIndex", i);
    },
  },
};
</script>

<style scoped lang="scss">
.right {
  justify-content: flex-end;
}
.center {
  justify-content: center;
}

.wrap {
  width: 1200px;
  margin: 0 auto;
  margin-top: 20px;

  .header {
    text-align: center;
    img {
      height: 28px;
      vertical-align: top;
      position: relative;
      top: -10px;
    }
    h2 {
      width: 240px;
      margin: 0 auto;
      font-size: 40px;
      font-weight: 700;
      position: relative;
      color: #6a7391;

      &::before {
        content: "";
        display: block;
        position: absolute;
        width: 480px;
        height: 21px;
        background: url("./images/titleset-left.png") no-repeat center center;
        background-size: contain;
        left: -480px;
        top: 10px;
      }
      &::after {
        content: "";
        display: block;
        position: absolute;
        width: 480px;
        height: 21px;
        background: url("./images/titleset-right.png") no-repeat center center;
        background-size: contain;
        right: -480px;
        top: 10px;
      }
    }
    p {
      margin-top: 10px;
      color: #6a7391;
      font-size: 14px;
      font-family: MicrosoftYaHei;
    }
  }

  .tab {
    ul {
      display: flex;
      margin-top: 26px;
      li {
        position: relative;
        display: flex;
        justify-content: center;
        align-items: center;
        width: 160px;
        height: 50px;
        line-height: 50px;
        margin-left: 12px;
        text-align: center;
        border-radius: 0 0 14px 14px;
        box-shadow: 0 6px 10px 0 rgb(184 208 255 / 30%);
        cursor: pointer;
        background-image: url("./images/primary-medium-txt-normal@2x.png");
        background-size: cover;

        &.active,
        &:hover {
          background-image: none;
          color: #fff;
          &::before {
            content: "";
            top: 0;
            z-index: -1;
            display: block;
            width: 180px;
            height: 66px;
            position: absolute;
            left: 50%;
            transform: translate3d(-50%, 0, 0);
            background-image: url("./images/primary-medium-new-selected.png");
            background-repeat: no-repeat;
            background-size: 100% 100%;
          }

          .activeWrap {
            @keyframes zoom {
              0% {
                transform: scale(1);
              }
              50% {
                opacity: 1;
                transform: scale(1.1);
              }
              100% {
                opacity: 1;
                transform: scale(1);
              }
            }
            animation: zoom 0.5s ease-in forwards;
          }
        }
        // 默认图标
        .iconWrap {
          width: 28px;
          height: 28px;
          margin-right: 14px;
          .activeIcon {
            display: none;
          }
          .icon {
            display: block;
          }
          img {
            width: 100%;
            height: 100%;
          }
        }
        // 选中图标
        .activeWrap {
          width: 44px;
          height: 44px;
          margin-right: 4px;
          .icon {
            display: none;
          }
          .activeIcon {
            display: block;
          }
        }
      }
    }
  }

  .content {
    position: relative;
    min-height: 520px;
  }
}
</style>

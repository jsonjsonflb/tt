<template>
  <div class="wrap">
    <div class="innerWrap">
      <div class="topbar">占位</div>
      <div class="navbar-wrap">
        <ul class="navbar">
          <li
            @mouseenter="moveIn(i)"
            @mouseleave="moveOut()"
            v-for="i in 11"
            :key="i"
            class="navbar-item"
          >
            <span>{{ i }}</span>
          </li>
        </ul>
      </div>

      <div
        @mouseenter="moveIn(i)"
        @mouseleave="moveOut()"
        v-for="i in 11"
        :key="i"
        :style="{ backgroundColor: `#${i}${i}${i}` }"
        :class="`item-wrap ${nowIndex === i ? 'active' : ''}`"
      >
        <component :is="list[i]"></component>
      </div>
    </div>
  </div>
</template>

<script>
import Item from "./Item";
export default {
  name: "HelloWorld",
  data() {
    return {
      nowIndex: -1,
      list: [Item, Item, Item, Item, Item, Item, Item, Item, Item, Item, Item],
    };
  },
  methods: {
    moveIn(i) {
      this.nowIndex = i;
    },
    moveOut() {
      this.nowIndex = -1;
    },
  },
  mounted() {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.wrap {
  height: 106px;
  background-color: #fff;
}
.innerWrap {
  background-color: #fff;
  position: fixed;
  top: 0;
  width: 100%;
  z-index: 999;
}

.topbar {
  height: 22px;
  background-color: aqua;
}

.navbar-wrap {
  box-shadow: 0 3px 9px 0 rgb(0 0 0 / 8%);
  .navbar {
    width: 1200px;
    display: flex;
    padding: 0;
    margin: 0 auto;
    position: relative;

    .navbar-item {
      margin: 0;
      list-style: none;
      min-width: 57px;
      height: 100%;
      line-height: 84px;
      color: #444c64;
      cursor: pointer;
      transition: all 0.2s ease;
      &:hover {
        background-color: #999;
      }
    }
  }
}

.item-wrap {
  position: fixed;
  top: 106px;
  width: 100%;
  // height: 375px;
  height: 0;
  overflow: hidden;
  left: 0;
  transition: all 0.3s linear;

  &.active {
    height: 375px;
  }
}
</style>

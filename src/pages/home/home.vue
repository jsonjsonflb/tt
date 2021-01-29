<template>
  <div class="wrap">
    <HomeSection
      :title="appDown.title"
      :titleImg="appDown.titleImg"
      :titleMsg="appDown.titleMsg"
      :tabLlist="appDown.tabLlist"
      :direction="appDown.direction"
      :nowIndex="appdwonIndex"
      @selectIndex="setAppdownIndex"
      :height="660"
    >
      <Appdown type="all" :activeIndex="0" :nowIndex="appdwonIndex" />
      <Appdown type="sport" :activeIndex="1" :nowIndex="appdwonIndex" />
    </HomeSection>
    <HomeSection
      :title="hotgame.title"
      :titleImg="hotgame.titleImg"
      :titleMsg="hotgame.titleMsg"
      :tabLlist="hotgame.tabLlist"
      :direction="hotgame.direction"
      :nowIndex="hotgameIndex"
      @selectIndex="setHotgameIndex"
      :height="450"
    >
      <!-- 动画组件 传左右两边内容，可以是组件或者dom -->
      <Transform :leftWidth="600" :activeIndex="0" :nowIndex="hotgameIndex">
        <!-- 左边的内容 -->
        <template v-slot:left>
          <div>
            <h1>1111</h1>
            <h1>1111</h1>
          </div>
        </template>
        <!-- 右边的内容 -->
        <template v-slot:right>
          <div>
            <h1>2222</h1>
            <h1>2222</h1>
          </div>
        </template>
      </Transform>

      <!-- 动画组件 -->
      <Transform :leftWidth="600" :activeIndex="1" :nowIndex="hotgameIndex">
        <template v-slot:left>
          <Appdown type="all" :activeIndex="0" :nowIndex="0" />
        </template>
        <template v-slot:right>
          <Appdown type="all" :activeIndex="1" :nowIndex="1" />
        </template>
      </Transform>
    </HomeSection>
  </div>
</template>

<script>
import HomeSection from "@/components/HomeSection";
import Appdown from "@/components/HomeSection/Appdown";
import Transform from "@/components/Transform";
import appDownload from "@/assets/images/home/app-download.png";
import topGame from "@/assets/images/home/top-games@2x.png";
import allIcon from "@/assets/images/home/icon.png";
import allIconActive from "@/assets/images/home/icon.png";
import sportIcon from "@/assets/images/home/activeIcon.png";
import sportIconActive from "@/assets/images/home/activeIcon.png";

export default {
  data() {
    return {
      appdwonIndex: 0,
      appDown: {
        title: "APP下载",
        titleImg: appDownload,
        titleMsg: "独家原生APP支持全部移动端",
        tabLlist: [
          {
            title: "全站APP",
            icon: allIcon,
            activeIcon: allIconActive,
          },
          {
            title: "体育APP",
            icon: sportIcon,
            activeIcon: sportIconActive,
          },
        ],
        direction: "right",
      },
      hotgameIndex: 0,
      hotgame: {
        title: "热门游戏",
        titleImg: topGame,
        titleMsg: "您想要的亚博都有，带给您丰富的游戏体验",
        tabLlist: [
          {
            title: "体育",
            icon: allIcon,
            activeIcon: allIconActive,
          },
          {
            title: "真人",
            icon: sportIcon,
            activeIcon: sportIconActive,
          },
        ],
        direction: "center",
      },
    };
  },
  methods: {
    setAppdownIndex(i) {
      // 控制切换
      this.appdwonIndex = i;
    },
    setHotgameIndex(i) {
      // 控制切换
      this.hotgameIndex = i;
    },
  },
  components: {
    HomeSection,
    Appdown,
    Transform,
  },
};
</script>

<style lang="scss" scoped>
.wrap {
  overflow: hidden;
}
</style>

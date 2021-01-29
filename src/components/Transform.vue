<template>
  <div class="wrap">
    <div
      class="leftWrap"
      :class="{
        animationIn: nowIndex === activeIndex,
        animationOut: nowIndex !== activeIndex,
      }"
      :style="{
        width: (leftWidth ? leftWidth : 490) + 'px',
        animationDuration: duration + 's',
      }"
    >
      <slot name="left"></slot>
    </div>
    <div
      class="rightWrap"
      :class="{
        animationIn: nowIndex === activeIndex,
        animationOut: nowIndex !== activeIndex,
      }"
      :style="{ animationDuration: duration + 's' }"
    >
      <slot name="right"></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    nowIndex: {
      type: Number,
      default: 0,
    },
    activeIndex: {
      type: Number,
      default: 0,
    },
    leftWidth: {
      type: Number,
      default: 0,
    },
    // 动画执行时间，默认0.5s
    duration: {
      type: Number,
      default: 0.5,
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/css/animation.scss";

.wrap {
  position: absolute;
  top: 0;
  display: flex;
  height: 100%;
}
.leftWrap {
  width: 490px;
  height: 100%;
  position: relative;
  font-family: MicrosoftYaHei;

  &.animationOut {
    z-index: 0;
    @include animation_left_out;
  }

  &.animationIn {
    z-index: 1;
    @include animation_left_in;
  }
}
.rightWrap {
  flex: 1;
  position: relative;

  &.animationOut {
    z-index: 0;
    @include animation_right_out;
  }

  &.animationIn {
    position: relative;
    z-index: 1;
    @include animation_right_in;
  }
}
</style>

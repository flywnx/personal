<template>
  <div
    id='portraitList'
    ref="portraitList"
    @mousewheel="handleScroll"
    @mouseover="startScroll"
  >
    <slot></slot>
  </div>
</template>
<script lang='ts'>
// 竖屏首页 展示轮播组件
import { Prop, Component, Vue } from "vue-property-decorator";
@Component
export default class PortraitList extends Vue {
  @Prop({
    type: String,
    default: "1"
  })
  listLength: string;

  mounted() {
    console.log(this.listLength);
  }
  destroyed() {}

  methods: {};
  public onScrolls(): void {
    // let e = arguments[0];
    console.log(arguments[0].target.scrollTop);
  }
  public handleScroll(): void {
    console.log(arguments[0]);
  }
  public startScroll(): void {}
}
</script>
<style lang="scss" scoped>
#portraitList {
  width: 100%;
  height: 100vh;
  overflow: hidden;
}
</style>
<template>
  <div id="portraitList"
       ref="portraitList"
       @mousewheel="handleScroll"
       @mouseover="startScroll"
       @mouseout="endScroll">
    <div class="conent"
         :style="{top:(sceollNum*100)+'vh'}">
      <slot></slot>
    </div>
  </div>
</template>
<script lang='ts'>
// 竖屏首页 展示轮播组件
import { Prop, Component, Vue } from "vue-property-decorator";
import utils from "../utils";
@Component
export default class PortraitList extends Vue {
  @Prop({
    type: String
  })
  public listLength: string = "1";
  public scrollType: boolean = false;
  public sceollNum: number = 0;
  public debouncetype: boolean = false;
  public startScroll() {
    this.scrollType = true;
  }

  public endScroll() {
    this.scrollType = false;
  }
  public handleScroll(): void {
    if (!utils.debounce(this, "debouncetype")) {
      // 防抖
      return;
    }
    if (arguments[0].wheelDelta > 0) {
      if (this.sceollNum > -Number(this.listLength) + 1) {
        this.sceollNum -= 1;
      }
    } else {
      if (this.sceollNum < 0) {
        this.sceollNum += 1;
      }
    }
  }
}
</script>
<style lang="scss" scoped>
#portraitList {
  width: 100%;
  height: 100vh;
  overflow: hidden;
}
.conent {
  position: relative;
  transition: top 0.3s;
}
</style>
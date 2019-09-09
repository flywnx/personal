<template>
  <div class="home">
    <h1
      ref="title"
      :class="{'titleClass':titleClass}"
    >FishKing</h1>
    <ul
      ref="tips"
      class="tips"
    >
      <li
        v-for="(item,index) in tips"
        :key="index"
        :class="[tipsClass>index?'ani':'']"
      >{{item}}</li>
    </ul>
    <ul :class="[isShowNav?'navBox showNav':'navBox hideNav']">
      <li
        class="navBtn"
        @click="onShowNav"
      ></li>
      <li
        v-for="(item,index) in navList"
        :key="index"
      >{{item}}</li>
    </ul>

  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component
export default class Home extends Vue {
  public titleClass: boolean = false;
  public tipsClass: number = 0;
  public navList: Array<string> = [
    "首页",
    "技术分享",
    "视听分享",
    "游戏分享",
    "自我介绍"
  ];
  public tips: string = "咸鱼王的世界";

  public isShowNav: boolean = false;

  private mounted() {
    let _this = this,
      count = 0;
    _this.$refs.tips["childNodes"].forEach(el => {
      setTimeout(() => {
        _this.titleClass = true;
        _this.tipsClass += 1;
      }, count * 300);
      count += 1;
    });
  }

  public onShowNav(): void {
    this.isShowNav = !this.isShowNav;
  }
}
</script>

<style lang="scss" scoped>
.home {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  height: 100vh;
  width: 100vw;
  h1 {
    font-size: 0px;
    color: $titleColor;
    text-shadow: -1px 1px 0 $titleShadow, -2px 2px 0 $titleShadow,
      -3px 3px 0 $titleShadow, -4px 4px 0 $titleShadow, -5px 5px 0 $titleShadow,
      -6px 6px 0 $titleShadow, -7px 7px 0 $titleShadow, -8px 8px 0 $titleShadow;
    transition: font-size 0.6s cubic-bezier(0.18, 0.89, 0.32, 1.28);
  }
  h1.titleClass {
    font-size: $fontsize * 16;
  }
  .tips {
    position: relative;
    top: -16 * $fontsize;
    display: flex;
    justify-content: center;
    flex-direction: row;
    width: 100vw;
    height: $fontsize * 8;
    font-weight: bold;
    // color: $tipsColor;
    li {
      font-size: $fontsize * 6;
      line-height: $fontsize * 8;
      opacity: 0;
      position: relative;
      top: 0;
      transition: top 0.3s cubic-bezier(0.18, 0.89, 1, 1.97),
        opacity 0.3s cubic-bezier(0.18, 0.89, 0.32, 1.28);
    }
    li.ani {
      top: -6 * $fontsize;
      opacity: 1;
    }
  }
  .navBox {
    padding-top: 5 * $fontsize;
    display: flex;
    flex-direction: column;
    height: 100vh;
    width: 10 * $fontsize;
    position: fixed;
    top: 0;
    right: -10 * $fontsize;
    background-color: $homeBG;
    color: $navColor;
    transition: right 0.3s cubic-bezier(0.18, 0.89, 0.32, 1.28);
    li {
      height: 4 * $fontsize;
      font-size: 2 * $fontsize;
      text-align: center;
      line-height: 4 * $fontsize;
    }
    .navBtn {
      width: 4 * $fontsize;
      position: absolute;
      top: 0;
      left: -4 * $fontsize;
      color: #000;
    }

    .navBtn::before {
      content: "×";
    }
  }
  .showNav {
    right: 0;
  }
  .hideNav {
    right: -10 * $fontsize;
  }
}
</style>
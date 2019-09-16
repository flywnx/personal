<template>
  <div id="app">

    <!-- <router-view /> -->
    <PortraitList listLength='5'>
      <div class='slot'>1235</div>
      <div class='slot'>1234</div>
      <div class='slot'>1233</div>
      <div class='slot'>1232</div>
      <Home></Home>
    </PortraitList>
  </div>
</template>
<script lang='ts'>
import { Component, Vue } from "vue-property-decorator";

import PortraitList from "@/components/PortraitList.vue";
import Home from "@/views/Home.vue";
@Component({
  components: {
    PortraitList,
    Home
  }
})
export default class App extends Vue {}
</script>
<style>
.slot {
  width: 100%;
  height: 100vh;
}
</style>

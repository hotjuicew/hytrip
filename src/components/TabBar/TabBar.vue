<template>
    <div class="tab-bar" >
      <div class="tab-bar-item" v-for="(item,index) in tabbarData">
        <img :src="getAssetURL(item.image)" alt="">
        <span class="text">{{ item.text }}</span>
      </div>
    </div>
</template>

<script setup>
import tabbarData from "@/assets/localData/tabbar.js"
import {getAssetURL} from "@/utils/load_assets";

</script>

<style lang="less" scoped>
.tab-bar{
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  height: 50px;
  display: flex;

  border-top: 1px solid #f3f3f3;
  .tab-bar-item{
    flex: 1;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    img {
      width: 36px;
    }

    .text {
      font-size: 12px;
      margin-top: 2px;
    }
  }
}
</style>
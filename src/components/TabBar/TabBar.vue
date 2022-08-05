<template>
  <van-tabbar v-model="currentIndex" active-color="#ff9854">
    <template v-for="(item,index) in tabbarData" :class="{active:index===currentIndex}">
      <van-tabbar-item :to="item.path">
        <span>{{ item.text }}</span>
        <template #icon>
          <img v-if="index===currentIndex" :src="getAssetURL(item.imageActive)" alt="">
          <img v-else :src="getAssetURL(item.image)" alt="">
        </template>
      </van-tabbar-item>
    </template>
  </van-tabbar>

  <!--  <div class="tab-bar">
      <div class="tab-bar-item" v-for="(item,index) in tabbarData" :class="{active:index===currentIndex}"
           @click="itemClick(index,item)">
        <img v-if="index===currentIndex" :src="getAssetURL(item.imageActive)" alt="">
        <img v-else :src="getAssetURL(item.image)" alt="">
        <span class="text">{{ item.text }}</span>
      </div>
    </div>-->
</template>

<script setup>
import tabbarData from "@/assets/localData/tabbar.js"
import {getAssetURL} from "@/utils/load_assets";
import {ref} from "vue";


const currentIndex = ref(0)

</script>

<style lang="less" scoped>
.tab-bar {
  //重写样式
  img {
    height: 28px;
  }
  // 找到类, 对类中的CSS属性重写
  // :deep(.class)找到子组件的类, 让子组件的类也可以生效
  :deep(.van-tabbar-item__icon) {
    font-size: 50px;
  }
}
</style>

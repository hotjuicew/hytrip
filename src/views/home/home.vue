<template>
  <home-nav-bar></home-nav-bar>
  <div class="banner">
    <img src="@/assets/img/home/banner.webp" alt="">
  </div>
<home-search-box></home-search-box>
  <home-categories></home-categories>
</template>

<script setup>
import HomeNavBar from '@/views/home/cpns/HomeNavBar.vue'
import HomeSearchBox from '@/views/home/cpns/HomeSearchBox.vue'
import useHomeStore from "@/stores/modules/home";
import HomeCategories from '@/views/home/cpns/HomeCategories.vue'
// 发送网络请求
const homeStore = useHomeStore()
homeStore.fetchHotSuggestData()
homeStore.fetchCategoriesData()
homeStore.fetchHouselistData()
</script>

<style lang="less" scoped>
.banner{
  img{
    width: 100%;
  }
}

</style>

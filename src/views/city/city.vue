<template>
  <div class="city top-page">
    <div class="top">
      <!--   搜索框-->
      <form action="/">
        <van-search shape="round"
                    v-model="value"
                    show-action
                    placeholder="城市/区域/位置"
                    @search="searchClick"
                    @cancel="cancelClick"
        />
      </form>
      <!-- tab的切换 -->
      <van-tabs v-model:active="tabActive" color="#ff9854" line-height="3">
        <template v-for="(value, key, index) in allCities" :key="key">
          <van-tab :title="value.title" :name="key"></van-tab>
        </template>
      </van-tabs>
    </div>
    <div class="content">
      <template v-for="(group,index) in currentGroup?.cities" :key="index">
       <div class="group-item">
         <h2>标题：{{group.group}}</h2>
         <div class="list">
           <template v-for="city in group.cities">
            <div class="city">
              {{city.cityName}}
            </div>
           </template>
         </div>
       </div>
      </template>
    </div>

  </div>
</template>

<script setup>
import {computed, ref} from "vue";
import router from "@/router";
import useCityStore from "@/stores/modules/city";
import {storeToRefs} from 'pinia';

//搜索框功能
const value = ref('');
const searchClirck = (val) => {
};
const cancelClick = () => {
  router.back()
};
//tab的切换
const tabActive = ref()

//从store标签中获取数据
const cityStore = useCityStore()
cityStore.fetchAllCitiesData()
const {allCities} = storeToRefs(cityStore)

// 目的: 获取选中标签后的数据
// 1.获取正确的key: 将tabs中绑定的tabAction正确绑定
// 2.根据key从allCities获取数据, 默认直接获取的数据不是响应式的, 所以必须包裹computed
const currentGroup = computed(() => allCities.value[tabActive.value])
</script>

<style lang="less" scoped>
.city {
  --van-tab-line-height: 30px;

  .content {
    height: calc(100vh - 98px);
    overflow-y: auto;
  }
}
</style>

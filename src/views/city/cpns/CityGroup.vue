<template>
  <div class="city-group">
    <van-index-bar highlight-color="#ff9854">
      <van-index-anchor index="热门" />
      <div class="list">
        <template v-for="(city, index) in groupData.hotCities">
          <div class="city" @click="cityClick(city)">{{ city.cityName }}</div>
        </template>
      </div>

      <template v-for="(group,index) in groupData.cities" :key="index">
        <van-index-anchor :index="group.group" />
        <template v-for="(city,index) in group.cities" :key="index">
          <van-cell :title="city.cityName" />
        </template>
      </template>
    </van-index-bar>
  </div>
</template>

<script setup>
// 定义props
const props = defineProps({
  groupData: {
    type: Object,
    default: () => ({})
  }
})
</script>

<style lang="less" scoped>

.list {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  padding: 10px;
  padding-right: 25px;

  .city {
    width: 70px;
    height: 28px;
    border-radius: 14px;
    font-size: 12px;
    color: #000;
    text-align: center;
    line-height: 28px;
    background-color: #fff4ec;
    margin: 6px 0;
  }
}

</style>

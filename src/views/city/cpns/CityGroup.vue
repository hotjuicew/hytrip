<template>
  <div class="city-group">
    <van-index-bar highlight-color="#ff9854">
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

</style>

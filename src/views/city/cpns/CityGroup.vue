<template>
  <div class="city-group">

    <template v-for="(group,index) in groupData.cities" :key="index">
      <div class="group-item">
        <h2>标题：{{group.group}}</h2>
        <div class="list">
          <template v-for="(city,index) in group.cities" :key="index">
            <div class="city">
              {{city.cityName}}
            </div>
          </template>
        </div>
      </div>
    </template>
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
把content部分抽取成独立的CityGroup
<template>
<h2>App</h2>
  <router-view></router-view>
  <router-link to="/home">首页</router-link>
  <router-link to="/favor">收藏</router-link>
  <router-link to="/order">订单</router-link>
  <router-link to="/message">消息</router-link>
  <tab-bar></tab-bar>
</template>

<script setup>
import TabBar from "@/components/TabBar/TabBar.vue";

</script>

<style scoped>

</style>

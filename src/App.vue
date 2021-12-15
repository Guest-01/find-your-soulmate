<template>
  <TheHeader />
  <router-view></router-view>
</template>

<script>
import TheHeader from "./components/TheHeader.vue"
export default {
  name: "App",
  components: { TheHeader },
  setup() {
    //
  },
}
</script>

<style>
@import "@/assets/base.css";
@import url('https://cdn.jsdelivr.net/gh/orioncactus/pretendard/dist/web/static/pretendard-dynamic-subset.css');
</style>
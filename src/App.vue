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
</style>
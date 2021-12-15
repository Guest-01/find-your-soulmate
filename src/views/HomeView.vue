<template>
  <main class="h-screen bg-gray-50 px-4 py-3 space-y-6">
    <div class="flex flex-col items-center space-y-2">
      <TheInput @inputClick="getMate" />
      <MateInfo v-if="mate" :mate="mate" />
    </div>
    <div v-if="mate" class="h-1/2 border-2 rounded bg-gradient-to-r from-indigo-400 to-violet-400">
      <div class="text-center text-white">단짝의 현재 위치</div>
      <TheMap :mate="mate" />
    </div>
  </main>
</template>

<script>
import TheInput from "../components/TheInput.vue";
import TheMap from "../components/TheMap.vue";
import MateInfo from "../components/MateInfo.vue";
import { ref } from "@vue/reactivity";

export default {
  components: {
    TheInput,
    TheMap,
    MateInfo
  },
  setup() {
    const mate = ref(null);

    const getMate = async (userInput) => {
      try {
        const res = await fetch('https://randomuser.me/api')
        const data = await res.json();
        mate.value = data.results[0]
        console.log(mate.value);
      } catch (error) {
        alert(error.message);
      }
    }

    return { mate, getMate }
  }
}
</script>
<template>
  <div class="flex flex-col items-center">
    <input
      :class="{ ring: invalid, 'ring-red-500': invalid }"
      class="w-56 p-2 text-center border-2 rounded-lg"
      type="text"
      name="name"
      id="name"
      placeholder="당신의 이름을 입력해주세요"
      v-model="userInput"
    />
    <button
      @click="validateAndEmit"
      class="p-2 bg-yellow-300 rounded-full text-center mt-6 shadow animate-bounce hover:animate-none hover:-translate-y-2 active:bg-yellow-400"
    >
      <svg
        xmlns="http://www.w3.org/2000/svg"
        class="h-6 w-6 inline text-indigo-500 ml-1"
        fill="none"
        viewBox="0 0 24 24"
        stroke="currentColor"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M19 14l-7 7m0 0l-7-7m7 7V3"
        />
      </svg>
      <span v-if="userInput" class="text-gray-800 ml-1 mr-2">{{ userInput }}님의 단짝은... (클릭)</span>
      <span v-else class="text-gray-800 ml-1 mr-2">내 단짝 찾기 (클릭)</span>
    </button>
  </div>
</template>

<script>import { ref } from "@vue/reactivity"

export default {
  name: "TheInput",
  setup(_, ctx) {
    const userInput = ref("")
    const invalid = ref(false)

    const validateAndEmit = () => {
      if (!userInput.value) {
        invalid.value = true;
      } else {
        invalid.value = false;
        ctx.emit('inputClick', userInput.value)
      }
    }

    return { userInput, invalid, validateAndEmit }
  }
}
</script>
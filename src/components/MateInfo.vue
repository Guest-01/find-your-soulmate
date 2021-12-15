<template>
  <div
    :class="{ 'bg-blue-100': isMale, 'bg-pink-100': !isMale }"
    class="flex border-2 shadow-lg px-3 py-2 rounded-lg"
  >
    <img :src="mate.picture.large" alt="Portrait" class="border-2 rounded-full" />
    <div class="flex flex-col justify-center ml-2">
      <span class="font-bold text-xl">{{ fullName }}</span>
      <span>{{ dob }} ({{mate.dob.age}}살)</span>
      <span class="text-sm underline">{{ mate.email }}</span>
      <span>{{ mate.location.country }}</span>
    </div>
  </div>
</template>

<script>
import moment from 'moment/min/moment-with-locales';

export default {
  name: "MateInfo",
  props: {
    mate: Object
  },
  computed: {
    fullName() {
      const { _, first, last } = this.mate.name
      return `${first} ${last}`
    },
    isMale() {
      return this.mate.gender === "male"
    },
    dob() {
      moment.locale("ko");
      return moment(this.mate.dob.date).format("ll")
    }
  }
}
</script>
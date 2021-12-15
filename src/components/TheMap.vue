<template>
  <div id="map" class="h-full"></div>
</template>

<script>
import L from "leaflet"

export default {
  name: "TheMap",
  props: {
    mate: Object
  },
  data() {
    return {
      myMap: null
    }
  },
  mounted() {
    console.log('Mounted!')
    this.myMap = L.map('map').setView([34, 127], 6);

    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
    }).addTo(this.myMap);
  },
  updated() {
    console.log('Updated!')
    const coord = [
      parseFloat(this.mate.location.coordinates.latitude),
      parseFloat(this.mate.location.coordinates.longitude),
    ]
    console.log(coord)

    L.marker(coord).addTo(this.myMap);
    this.myMap.setView(coord, 4);
  }
}

</script>
<template>
  <div>
    <div id="map"></div>
  </div>
</template>

<script>
import L from "leaflet";
export default {
  name: "MapComponent",
  data: () => ({
    map: null,
    tileLayer: null,
    layers: [
      {
        id: 0,
        name: "Restaurante",
        active: false,
        features: [],
      },
    ],
  }),
  mounted() {
    this.initMap();
    // this.initLayers();
  },
  methods: {
    initMap() {
      this.map = L.map("map").setView([-25.46033726712044, -49.29804536309487], 13);
      this.tileLayer = L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {
        maxZoom: 18,
        attribution:
          '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>, &copy; <a href="https://carto.com/attribution">CARTO</a>',
      });
      this.tileLayer.addTo(this.map);
    },
  },
};
</script>

<style scoped>
#map {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
}
</style>

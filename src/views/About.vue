<template>
  <div class="about">
    <h1>This is an about page</h1>
    <div id="map"></div>
  </div>
</template>
<style>
body {
  margin: 0;
  padding: 0;
}
#map {
  height: 300px;
  width: auto;
}
</style>
<script>
/* global mapboxgl */
export default {
  mounted: function () {
    this.setUpMap();
  },
  methods: {
    setUpMap: function () {
      mapboxgl.accessToken = process.env.VUE_APP_MY_API_KEY;
      const map = new mapboxgl.Map({
        container: "map", // container ID
        style: "mapbox://styles/mapbox/streets-v11", // style URL
        center: [-82.6963, 40.3045], // starting position [lng, lat]
        zoom: 9, // starting zoom
      });
      const popup = new mapboxgl.Popup({ offset: 25 }).setText(
        "The geographical center of Ohio. We have a rock! -Everyone Who Has Ever Lived There"
      );

      const marker1 = new mapboxgl.Marker().setLngLat([-82.6963, 40.3045]).setPopup(popup).addTo(map);
      console.log(map, marker1, popup);
    },
  },
};
</script>

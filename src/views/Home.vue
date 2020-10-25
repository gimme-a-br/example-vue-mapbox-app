<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h2>Here's my map</h2>
    <div id="mymap"></div>
  </div>
</template>

<style>
#mymap {
  height: 300px;
}
</style>

<script>
/* global mapboxgl */

export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
    };
  },
  created: function () {},
  mounted: function () {
    mapboxgl.accessToken = process.env.VUE_APP_MAPBOX_ACCESS_TOKEN;
    var map = new mapboxgl.Map({
      container: "mymap", // container id
      style: "mapbox://styles/mapbox/streets-v11", // style URL
      center: [-74.5, 40], // starting position [lng, lat]
      zoom: 9, // starting zoom
    });

    var popup = new mapboxgl.Popup({ offset: 25 }).setText("Construction on the Washington Monument began in 1848.");
    var marker = new mapboxgl.Marker().setLngLat([-74.5, 40]).setPopup(popup).addTo(map);
  },
  methods: {},
};
</script>

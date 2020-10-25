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
      places: [],
    };
  },
  mounted: function () {
    mapboxgl.accessToken = process.env.VUE_APP_MAPBOX_ACCESS_TOKEN;
    var map = new mapboxgl.Map({
      container: "mymap", // container id
      style: "mapbox://styles/mapbox/streets-v11", // style URL
      center: [131.044, -25.363], // starting position [lng, lat]
      zoom: 3, // starting zoom
    });

    this.places = [
      { lat: -25.363, lng: 131.044, description: "A place in Australia" },
      { lat: -33.8675, lng: 151.207, description: "The main city!" },
    ];
    this.places.forEach((place) => {
      var popup = new mapboxgl.Popup({ offset: 25 }).setText(place.description);
      var marker = new mapboxgl.Marker().setLngLat([place.lng, place.lat]).setPopup(popup).addTo(map);
    });
  },
  methods: {},
};
</script>

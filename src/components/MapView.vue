<template>
	<div id="map"></div>
</template>

<script>
import L from 'leaflet';
const DEFAULT_LOCATION = [22.3511148, 78.6677428]

export default {
	name: 'MapView',

	props: {
		coords: {
			type: Array
		}
	},

	mounted() {
		// 1. Initialize the map
		this.map = L.map('map').setView(DEFAULT_LOCATION, 4);
		L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
			attribution: '&copy; OpenStreetMap contributors'
		}).addTo(this.map);
	},

	watch: {
		// 3. Watch for new location update
		coords(newCoords) {
			if (newCoords) {
				this.map.setView(newCoords, 13);
				L.marker(newCoords).addTo(this.map);
			}
		}
	}
}
</script>

<style scoped>
@import url("https://unpkg.com/leaflet@1.9.4/dist/leaflet.css");

#map { 
	height: 100vh;
	width: 100%;
	margin-top: 10px;
}
</style>

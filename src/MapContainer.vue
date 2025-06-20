<template>
	<div class="map-container">
		<LoadingSpinner v-if="loading" />
		<SearchBar @searchLocation="onSearch" />
		<MapView :coords="coords"/>
	</div>
</template>

<script>
import MapView from '@/components/MapView';
import SearchBar from '@/components/SearchBar';
import LoadingSpinner from '@/components/LoadingSpinner';

export default {
	name: 'MapContainer',

	data() {
		return {
			// Send new location to map
			coords: null,
			loading: false
		}
	},

	components: {
		MapView,
		SearchBar,
		LoadingSpinner
	},

	methods: {
		// Trigger location search
		async onSearch(location) {
			this.loading = true;
			// https://nominatim.openstreetmap.org/search?format=json&q=kolkata
			const url = `https://nominatim.openstreetmap.org/search?format=json&q=${encodeURIComponent(location)}`;
			const res = await fetch(url);
			const results = await res.json();
			if (results.length) {
				const { lat, lon } = results[0];
				this.coords = [parseFloat(lat), parseFloat(lon)];
				this.loading = false;
			} else {
				alert('Location not found');
				this.loading = false;
			}
		}
	}
}
</script>

<style>
* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
}
.map-container {
	height: 100vh;
	margin: 10px 20px;
}
</style>

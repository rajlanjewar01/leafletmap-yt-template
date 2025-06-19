<template>
    <SearchBar @searchLocation="onSearch" />
    <MapView :coords="coords"/>
</template>

<script>
import MapView from '@/components/MapView';
import SearchBar from '@/components/SearchBar';

export default {
    name: 'MapContainer',

    data() {
        return {
            // Send new location to map
            coords: null
        }
    },

    components: {
        MapView,
        SearchBar
    },

    methods: {
        // Trigger location search
        async onSearch(location) {
            // https://nominatim.openstreetmap.org/search?format=json&q=kolkata
            const url = `https://nominatim.openstreetmap.org/search?format=json&q=${encodeURIComponent(location)}`;
            const res = await fetch(url);
            const results = await res.json();
            if (results.length) {
                const { lat, lon } = results[0];
                this.coords = [parseFloat(lat), parseFloat(lon)];
            } else {
                alert('Location not found');
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
</style>

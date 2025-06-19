<template>
	<form @submit.prevent="emitSearch">
		<input
			v-model="query"
			type="text"
		>
		<button type="submit">Search</button>
	</form>
</template>

<script>
export default {
	name: 'SearchBar',

	emits: ['searchLocation'],

	data() {
		return {
			query: ''
		}
	},

	methods: {
		// 2. Search location
		emitSearch() {
			if( this.query.trim()) {
				this.$emit('searchLocation', this.query.trim());
			}
		}
	}
}
</script>

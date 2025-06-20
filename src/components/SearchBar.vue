<template>
	<div class="search-bar">
		<form @submit.prevent="emitSearch">
			<input
				v-model="query"
				type="text"
				placeholder="Search for a location"
			>
			<button type="submit">Search</button>
		</form>
	</div>
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
			if(this.query.trim()) {
				this.$emit('searchLocation', this.query.trim());
			}
		}
	}
}
</script>
<style scoped>
.search-bar {
	display: flex;
	justify-content: center;
	margin: 20px 0;
}
.search-bar input {
	width: 300px;
	padding: 10px;
	border: 1px solid #ccc;
	border-radius: 5px;
	font-size: 16px;
}
.search-bar button {
	padding: 10px 15px;
	margin-left: 10px;
	background-color: #667eea;
	color: white;
	border: none;
	border-radius: 5px;
	cursor: pointer;
	font-size: 16px;
}
</style>

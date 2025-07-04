<template>
	<div class="search-bar">
		<form @submit.prevent="emitSearch">
			<input
				v-model.trim="query"
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
			this.$emit('searchLocation', this.query);
		}
	}
}
</script>
<style scoped>
.search-bar {
	display: flex;
	justify-content: center;
	align-items: center;
	position: fixed;
	top: 10%;
	left: 50%;
	transform: translate(-50%, -50%);
	background: rgba(255, 255, 255, 0.09);
	backdrop-filter: blur(3px);
	-webkit-backdrop-filter: blur(3px);
	border-radius: 10px;
	border: 1px solid rgba(255, 255, 255, 0.3);
	box-shadow: 
	0 8px 32px rgba(0, 0, 0, 0.1),
	inset 0 1px 0 rgba(255, 255, 255, 0.5),
	inset 0 -1px 0 rgba(255, 255, 255, 0.1),
	inset 0 0 6px 3px rgba(255, 255, 255, 0.3);
	padding: 8px 10px;
	z-index: 999;
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

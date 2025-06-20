<template>
	<div class="spinner">
		<img src="@/assets/loader.gif" alt="Loading..." />
	</div>
</template>

<script>
	export default {
		name: 'LoadingSpinner'
	}
</script>

<style scoped>
.spinner {
	position: fixed;
	top: 0;
	left: 0;	
	right: 0;
	bottom: 0;
	z-index: 999;
	background-color: rgba(167, 224, 247, 0.2);
	display: flex;
	justify-content: center;
	align-items: center;
	transition: 2ms ease-in;
}
.spinner img {
	width: 100px;
	height: 100px;
}
</style>

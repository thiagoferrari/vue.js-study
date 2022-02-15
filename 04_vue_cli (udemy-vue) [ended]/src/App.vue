<template>
	<div id="app" >
		<h1>Contadores</h1>
		<Contador v-for="c in 3" :key='c'/>
	</div>
</template>

<script>
	import Contador from './components/Contador.vue'

	export default {
		components: {
			Contador
		}
	}
</script>

<style>

</style>
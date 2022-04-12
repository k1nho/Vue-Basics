<script>
import {reactive} from 'vue'
export default {
	setup() {
		const state = reactive({count : 0});

		return{
			state,
		}
	}
}
</script>

<template>
	<div>
		<button>Click {{state.count}}</button>		
	</div>	
</template>

<style>
	
</style>
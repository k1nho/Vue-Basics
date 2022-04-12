<script>
import {reactive} from 'vue'
export default {
	setup() {
		const state = reactive({count : 0});

		// state mutation
		const incrementCount = function(){
			state.count++;
		}

		return{
			state,
			incrementCount
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
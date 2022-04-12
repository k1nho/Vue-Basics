<script setup>
import {reactive} from 'vue'

const  state = reactive({
	counterState : {count : 0},
	fruits : ["banana", "apple", "lime"]
	});

function incrementCount(){
	state.counterState.count++;
	// DOM UPDATE does not happen synchronously but it is buffered until the next tick in the cycle update
	// we can use nextTick(()=>{}) to access the updated dom 

	state.fruits.push("newFruit" + state.counterState.count); //testing deep reactivity
}

// NOTE : the reactive object is not the same as the proxy. ex) state === {} will be false
// However calling reactive on the object will be the same as proxy. ex) reactive({}) === state will be true

</script>

<template>
	<div>
		<button @click="incrementCount">Click {{state.counterState.count}}</button>		
		<li v-for="fruit in state.fruits" :key="fruit">
			<ul>
				{{fruit}}
			</ul>
		</li>
	</div>	
</template>

<style>
	
</style>
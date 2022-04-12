<script setup>
import {reactive, ref} from 'vue'

const  state = reactive({
	counterState : {count : 0},
	fruits : ["banana", "apple", "lime"]
	});

// An alternative to use primitive types is to use ref, but more importantly it allows us to create a value which we can pass and not lose reactivity
// which is not the case with reactive
const num = ref(0);


function incrementCount(){
	state.counterState.count++;
	// DOM UPDATE does not happen synchronously but it is buffered until the next tick in the cycle update
	// we can use nextTick(()=>{}) to access the updated dom 

	state.fruits.push("newFruit" + state.counterState.count); //testing deep reactivity
}

// NOTE : the reactive object is not the same as the proxy. ex) state === {} will be false
// However calling reactive on the object will be the same as proxy. ex) reactive({}) === state will be true

// NOTE : Similar as with the options API, we must return an object which means that state can only be object based and cannot be primitive based.
</script>

<template>
	<div>
		<button @click="incrementCount">Click {{state.counterState.count}}</button>
		<button @click="num++">Click ref: {{num}}</button>		
		<li v-for="fruit in state.fruits" :key="fruit">
			<ul>
				{{fruit}}
			</ul>
		</li>
	</div>	
</template>

<style>
	
</style>
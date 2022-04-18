<script setup>
import { computed, reactive, ref } from 'vue';

const  state = reactive({
	counterState : {count : 0},
	fruits : []
	});

const personInfo  = reactive({
	name : "Kin",
	pet : "Rabbit",
	food : "Shrimp",
	age : 1000,
	band : "Ellegarden"
})

// NOTE : the reactive object is not the same as the proxy. ex) state === {} will be false
// However calling reactive on the object will be the same as proxy. ex) reactive({}) === state will be true

// NOTE : Similar as with the options API, we must return an object which means that state can only be object based and cannot be primitive based.

// An alternative to use primitive types is to use ref, but more importantly it allows us to create a value which we can pass and not lose reactivity
// which is not the case with reactive
const num = ref(0);
const bgColor = ref("blue")

function incrementCount(){
	state.counterState.count++;
	// DOM UPDATE does not happen synchronously but it is buffered until the next tick in the cycle update
	// we can use nextTick(()=>{}) to access the updated dom 

	state.fruits.push("newFruit" + state.counterState.count); //testing deep reactivity
}
function decrementCount(){
	if(state.counterState.count > 0){ state.counterState.count--; state.fruits.pop();}
	
}

// Computed properties using the Composition API as follows (useful when we want to cache results based on reactivity as opposed to methods which will re-render)
const fruitsMessage = computed(() =>{
	return state.fruits.length > 0 ? "The fruit market has been replenished" : "No fruits available"
})

// Style binding
const decrementButtonStyle = reactive({
	color: 'white',
	backgroundColor : 'red'
})

</script>

<template>
	<div>
		<button @click="incrementCount" :style="{backgroundColor : bgColor, color: 'white'}"> Add more fruits</button>
		<button @click="decrementCount" :style ="decrementButtonStyle"> Remove fruit</button>
		<button @click="num++">Click ref: {{num}}</button>		
		<p>{{fruitsMessage}} : {{state.fruits.length}}</p>
		<!--List rendering example -->
		<li v-for="fruit in state.fruits" :key="fruit">
			<ul>
				{{fruit}}
			</ul>
		</li>
		<h1>Rendering objects fields</h1>
		<!-- List rendering for objects--> 
		<li v-for="(value, key) in personInfo" :key="value.name">
			<ul>
				{{key}} : {{value}}	
			</ul>
		</li>
	</div>	
</template>

<style>
.incrementButton{
	background-color: "blue"
}	
.decrementButton{
	background-color: "red"
}	
</style>